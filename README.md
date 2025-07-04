local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local KeyInput = Instance.new("TextBox")
local VerifyButton = Instance.new("TextButton")
local StatusLabel = Instance.new("TextLabel")

ScreenGui.Parent = game:GetService("CoreGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.5, -150, 0.5, -100)
Frame.Size = UDim2.new(0, 300, 0, 200)

Title.Parent = Frame
Title.BackgroundTransparency = 1
Title.Position = UDim2.new(0, 0, 0, 10)
Title.Size = UDim2.new(1, 0, 0, 30)
Title.Font = Enum.Font.GothamBold
Title.Text = "ScriptsBinsAuth"
Title.TextColor3 = Color3.fromRGB(56, 139, 253)
Title.TextSize = 20

KeyInput.Parent = Frame
KeyInput.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
KeyInput.BorderSizePixel = 0
KeyInput.Position = UDim2.new(0.1, 0, 0.3, 0)
KeyInput.Size = UDim2.new(0.8, 0, 0, 40)
KeyInput.Font = Enum.Font.Gotham
KeyInput.PlaceholderText = "Insira Sua Key"
KeyInput.Text = ""
KeyInput.TextColor3 = Color3.fromRGB(255, 255, 255)
KeyInput.TextSize = 14

VerifyButton.Parent = Frame
VerifyButton.BackgroundColor3 = Color3.fromRGB(56, 139, 253)
VerifyButton.BorderSizePixel = 0
VerifyButton.Position = UDim2.new(0.25, 0, 0.6, 0)
VerifyButton.Size = UDim2.new(0.5, 0, 0, 30)
VerifyButton.Font = Enum.Font.GothamBold
VerifyButton.Text = "Verificar Key"
VerifyButton.TextColor3 = Color3.fromRGB(255, 255, 255)
VerifyButton.TextSize = 14

StatusLabel.Parent = Frame
StatusLabel.BackgroundTransparency = 1
StatusLabel.Position = UDim2.new(0, 0, 0.8, 0)
StatusLabel.Size = UDim2.new(1, 0, 0, 20)
StatusLabel.Font = Enum.Font.Gotham
StatusLabel.Text = ""
StatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
StatusLabel.TextSize = 14

local function verifyKey(key)
    return true, "Polenginho desbloqueando..."
end

VerifyButton.MouseButton1Click:Connect(function()
    local key = KeyInput.Text

    VerifyButton.Text = "Verificando..."
    StatusLabel.Text = "Verificando Key..."
    StatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)

    local success, message = verifyKey(key)

    if success then
        StatusLabel.Text = message or "Key Válida"
        StatusLabel.TextColor3 = Color3.fromRGB(0, 255, 0)
        wait(2)
        ScreenGui:Destroy()
      local Players = game:GetService("Players")
local player = Players.LocalPlayer
--local playerGui = player:WaitForChild("PlayerGui")
local CoreGui = game:GetService("CoreGui")

if CoreGui:FindFirstChild("GrandMenu") then
	CoreGui.GrandMenu:Destroy()
end

local gui = Instance.new("ScreenGui", CoreGui)
gui.Name = "GrandMenu"
gui.ResetOnSpawn = false

local mainFrame = Instance.new("Frame", gui)
mainFrame.Size = UDim2.new(0, 400, 0, 300)
mainFrame.Position = UDim2.new(0.5, -200, 0.5, -150)
mainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
mainFrame.BorderSizePixel = 0
mainFrame.Name = "Main"
mainFrame.Active = true
mainFrame.Draggable = true

local title = Instance.new("TextLabel", mainFrame)
title.Size = UDim2.new(1, 0, 0, 30)
title.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
title.Text = "🔥 Grand Menu"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.GothamBold
title.TextSize = 18
title.BorderSizePixel = 0

local sidebar = Instance.new("Frame", mainFrame)
sidebar.Size = UDim2.new(0, 100, 1, -30)
sidebar.Position = UDim2.new(0, 0, 0, 30)
sidebar.BackgroundColor3 = Color3.fromRGB(15, 15, 15)

local contentFrame = Instance.new("Frame", mainFrame)
contentFrame.Size = UDim2.new(1, -100, 1, -30)
contentFrame.Position = UDim2.new(0, 100, 0, 30)
contentFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
contentFrame.Name = "Content"

local abas = {"Combate", "Visual", "Teleportes", "Outros", "Farm"}
local botoes = {}
local acoesPorCategoria = {}

local function adicionarBotao(categoria, nomeBotao, funcao)
	if not acoesPorCategoria[categoria] then
		acoesPorCategoria[categoria] = {}
	end
	table.insert(acoesPorCategoria[categoria], {nome = nomeBotao, acao = funcao})
end

for i, nome in ipairs(abas) do
	local btn = Instance.new("TextButton", sidebar)
	btn.Size = UDim2.new(1, 0, 0, 30)
	btn.Position = UDim2.new(0, 0, 0, (i - 1) * 30)
	btn.Text = nome
	btn.Name = nome
	btn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	btn.TextColor3 = Color3.fromRGB(255, 255, 255)
	btn.Font = Enum.Font.Gotham
	btn.TextSize = 14
	botoes[nome] = btn

	btn.MouseButton1Click:Connect(function()
		for _, obj in pairs(contentFrame:GetChildren()) do
			obj:Destroy()
		end

		local categoriaBotoes = acoesPorCategoria[nome] or {}

		for i, item in ipairs(categoriaBotoes) do
			local botao = Instance.new("TextButton", contentFrame)
			botao.Size = UDim2.new(0, 200, 0, 30)
			botao.Position = UDim2.new(0, 10, 0, (i - 1) * 35 + 10)
			botao.Text = item.nome
			botao.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
			botao.TextColor3 = Color3.fromRGB(255, 255, 255)
			botao.Font = Enum.Font.Gotham
			botao.TextSize = 14

			botao.MouseButton1Click:Connect(function()
				item.acao()
			end)
		end
	end)
end


adicionarBotao("Combate", "Auto roubar itens", function()
	local ReplicatedStorage = game:GetService("ReplicatedStorage")
	local Player = game.Players.LocalPlayer
	local PlayerGui = Player:WaitForChild("PlayerGui")

	local function deletarNotifyGui()
		for _, gui in ipairs(PlayerGui:GetChildren()) do
			if gui.Name == "NotifyGui" and gui:IsA("ScreenGui") then
				gui:Destroy()
			end
		end
	end

	local itens = {
		"AK47", "Uzi", "PARAFAL", "Glock 17", "Faca", "IA2", "G3", "Dinamite",
		"Hi Power", "Natalina", "HK416", "Lockpick", "Escudo", "Skate", 
		"Saco de lixo", "Peça de Arma", "Tratamento", "AR-15", "PS5", "C4", "USP", "Xbox"
	}

	local args = {
		[1] = "mudaInv",
		[2] = "2",  -- Slot?
		[4] = "1"
	}

	local running = true

	while running do
		deletarNotifyGui()

		for i, item in ipairs(itens) do
			if i <= 16 then
				args[3] = item
				args[2] = tostring(i)

				task.spawn(function()
					ReplicatedStorage:WaitForChild("Modules")
						:WaitForChild("InvRemotes")
						:WaitForChild("InvRequest")
						:InvokeServer(unpack(args))
				end)
			end
		end

		task.wait(0.1)
	end
end)

adicionarBotao("Combate", "Auto tp safe (com 60 ou menos de vida)", function()
	local Players = game:GetService("Players")
	local player = Players.LocalPlayer
	local teleportCFrame = CFrame.new(
		-316.091064, 6.29782009, 378.853088,
		0.383262634, 0, -0.923639536,
		0,          1, 0,
		0.923639536, 0, 0.383262634
	)

	local function monitorarVida(character)
		local humanoid = character:WaitForChild("Humanoid")
		local hrp = character:WaitForChild("HumanoidRootPart")

		humanoid:GetPropertyChangedSignal("Health"):Connect(function()
			if humanoid.Health > 0 and humanoid.Health < 60 then
				hrp.CFrame = teleportCFrame
			end
		end)
	end
	player.CharacterAdded:Connect(function(character)
		monitorarVida(character)
	end)

	if player.Character then
		monitorarVida(player.Character)
	end
end)

adicionarBotao("Combate", "Auto revistar", function()
	local Players = game:GetService("Players")
	local LocalPlayer = Players.LocalPlayer
	local RS = game:GetService("ReplicatedStorage"):WaitForChild("RemoteNovos")
	local dsada = RS:WaitForChild("bixobrabo")

	local DETECTION_RADIUS = 10
	local CheckInterval = 0.5

	local detectados = {}

	function isDead(player)
		if player and player.Character then
			local humanoid = player.Character:FindFirstChildOfClass("Humanoid")
			return humanoid and humanoid.Health <= 0
		end
		return false
	end

	function distanceBetween(p1, p2)
		return (p1 - p2).Magnitude
	end

	task.spawn(function()
		while true do
			task.wait(CheckInterval)

			local character = LocalPlayer.Character
			if not character or not character:FindFirstChild("HumanoidRootPart") then continue end

			local pos = character.HumanoidRootPart.Position

			for _, otherPlayer in ipairs(Players:GetPlayers()) do
				if otherPlayer ~= LocalPlayer and isDead(otherPlayer) and otherPlayer.Character and otherPlayer.Character:FindFirstChild("HumanoidRootPart") then
					local otherPos = otherPlayer.Character.HumanoidRootPart.Position
					if distanceBetween(pos, otherPos) <= DETECTION_RADIUS then
						if not detectados[otherPlayer] then
							detectados[otherPlayer] = true
							dsada:FireServer("/revistar morto")
						end
					else
						detectados[otherPlayer] = nil
					end
				end
			end
		end
	end)
end)

adicionarBotao("Visual", "ESP e noclip", function()
	local Players = game:GetService("Players")
	local RunService = game:GetService("RunService")
	local CoreGui = game:GetService("CoreGui")
	local localPlayer = Players.LocalPlayer

	local wallsAtivos = false
	local noclip = false
	local highlights = {}
	local nomes = {}
	local corInimigo = Color3.fromRGB(255, 85, 85)

	local function criarNomeComItens(player)
		if not player.Character or not player.Character:FindFirstChild("Head") then return end
		local head = player.Character.Head

		local gui = Instance.new("BillboardGui")
		gui.Name = "WallNameESP"
		gui.Adornee = head
		gui.Size = UDim2.new(0, 200, 0, 60)
		gui.StudsOffset = Vector3.new(0, 2.5, 0)
		gui.AlwaysOnTop = true
		gui.Parent = head

		local nomeLabel = Instance.new("TextLabel", gui)
		nomeLabel.Size = UDim2.new(1, 0, 0.5, 0)
		nomeLabel.Position = UDim2.new(0, 0, 0, 0)
		nomeLabel.BackgroundTransparency = 1
		nomeLabel.Text = player.Name
		nomeLabel.TextColor3 = Color3.new(1, 1, 1)
		nomeLabel.TextStrokeTransparency = 0
		nomeLabel.Font = Enum.Font.GothamBold
		nomeLabel.TextScaled = true

		local itensLabel = Instance.new("TextLabel", gui)
		itensLabel.Size = UDim2.new(1, 0, 0.5, 0)
		itensLabel.Position = UDim2.new(0, 0, 0.5, 0)
		itensLabel.BackgroundTransparency = 1
		itensLabel.TextColor3 = Color3.fromRGB(255, 255, 0)
		itensLabel.TextStrokeTransparency = 0.2
		itensLabel.Font = Enum.Font.Gotham
		itensLabel.TextScaled = true
		itensLabel.Text = "Carregando..."

		nomes[player] = {
			gui = gui,
			itensLabel = itensLabel,
		}
	end

	local function atualizarItens(player)
		local info = nomes[player]
		if not info or not info.itensLabel then return end

		local backpack = player:FindFirstChild("Backpack")
		if not backpack then
			info.itensLabel.Text = "(Sem mochila)"
			return
		end

		local itens = {}
		for _, item in ipairs(backpack:GetChildren()) do
			if #itens >= 3 then break end
			table.insert(itens, item.Name)
		end

		info.itensLabel.Text = (#itens == 0) and "(Sem itens)" or table.concat(itens, " | ")
	end

	local function aplicarESP(player)
		if not player.Character or not player.Character:FindFirstChild("HumanoidRootPart") then return end
		local char = player.Character

		if not highlights[player] then
			local highlight = Instance.new("Highlight")
			highlight.Name = "WallESP"
			highlight.FillTransparency = 0.5
			highlight.OutlineTransparency = 0
			highlight.FillColor = corInimigo
			highlight.OutlineColor = Color3.new(1, 1, 1)
			highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
			highlight.Adornee = char
			highlight.Parent = char
			highlights[player] = highlight
		end

		if not nomes[player] then
			criarNomeComItens(player)
		end

		atualizarItens(player)
	end

	local function setCollisions(state)
		local char = localPlayer.Character
		if not char then return end
		for _, part in pairs(char:GetDescendants()) do
			if part:IsA("BasePart") then
				part.CanCollide = state
			end
		end
	end

	local function criarMenu()
		if CoreGui:FindFirstChild("MenuESP") then
			CoreGui:FindFirstChild("MenuESP"):Destroy()
		end

		local gui = Instance.new("ScreenGui", CoreGui)
		gui.Name = "MenuESP"
		gui.ResetOnSpawn = false

		local frame = Instance.new("Frame", gui)
		frame.Size = UDim2.new(0, 260, 0, 170)
		frame.Position = UDim2.new(0, 20, 0.5, -85)
		frame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
		frame.BackgroundTransparency = 0.05
		frame.BorderSizePixel = 0
		frame.Active = true
		frame.Draggable = true

		local corner = Instance.new("UICorner", frame)
		corner.CornerRadius = UDim.new(0, 12)

		local layout = Instance.new("UIListLayout", frame)
		layout.Padding = UDim.new(0, 10)
		layout.HorizontalAlignment = Enum.HorizontalAlignment.Center
		layout.VerticalAlignment = Enum.VerticalAlignment.Top

		local padding = Instance.new("UIPadding", frame)
		padding.PaddingTop = UDim.new(0, 12)

		local function criarBotao(texto, callback)
			local btn = Instance.new("TextButton", frame)
			btn.Size = UDim2.new(0.9, 0, 0, 40)
			btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
			btn.TextColor3 = Color3.new(1, 1, 1)
			btn.Text = texto
			btn.Font = Enum.Font.GothamBold
			btn.TextScaled = true
			btn.BorderSizePixel = 0
			btn.AutoButtonColor = false

			local sombra = Instance.new("Frame", btn)
			sombra.Size = UDim2.new(1, 4, 1, 4)
			sombra.Position = UDim2.new(0, 2, 0, 2)
			sombra.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
			sombra.BorderSizePixel = 0
			sombra.ZIndex = 0
			Instance.new("UICorner", sombra).CornerRadius = UDim.new(0, 8)

			Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 8)

			btn.MouseEnter:Connect(function() btn.BackgroundColor3 = Color3.fromRGB(80, 80, 80) end)
			btn.MouseLeave:Connect(function() btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60) end)
			btn.MouseButton1Click:Connect(callback)
		end

		criarBotao("ESP", function()
			wallsAtivos = not wallsAtivos

			if not wallsAtivos then
				for _, v in pairs(highlights) do v:Destroy() end
				for _, v in pairs(nomes) do if v.gui then v.gui:Destroy() end end
				highlights, nomes = {}, {}
			end
		end)

		criarBotao("Noclip", function()
			noclip = not noclip
			setCollisions(not noclip)
		end)

		local btnFechar = Instance.new("TextButton", frame)
		btnFechar.Size = UDim2.new(0.9, 0, 0, 30)
		btnFechar.BackgroundColor3 = Color3.fromRGB(50, 20, 20)
		btnFechar.TextColor3 = Color3.new(1, 1, 1)
		btnFechar.Text = "Fechar"
		btnFechar.Font = Enum.Font.Gotham
		btnFechar.TextScaled = true
		btnFechar.BorderSizePixel = 0

		Instance.new("UICorner", btnFechar).CornerRadius = UDim.new(0, 8)

		btnFechar.MouseButton1Click:Connect(function()
			gui:Destroy()
		end)
	end

	RunService.RenderStepped:Connect(function()
		if wallsAtivos then
			for _, p in ipairs(Players:GetPlayers()) do
				if p ~= localPlayer then
					aplicarESP(p)
				end
			end
		end

		if noclip then
			setCollisions(false)
		end
	end)

	criarMenu()
end)

adicionarBotao("Teleportes", "Teleport e espectar", function()
	local Players = game:GetService("Players")
	local LocalPlayer = Players.LocalPlayer

	pcall(function()
		game.CoreGui:FindFirstChild("dsadada"):Destroy()
	end)

	local ScreenGui = Instance.new("ScreenGui")
	ScreenGui.Name = "dsadada"
	ScreenGui.ResetOnSpawn = false
	ScreenGui.Parent = game.CoreGui

	local Frame = Instance.new("Frame")
	Frame.Size = UDim2.new(0, 260, 0, 210)
	Frame.Position = UDim2.new(0.3, 0, 0.3, 0)
	Frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	Frame.BorderSizePixel = 0
	Frame.Draggable = true
	Frame.Active = true
	Frame.Selectable = true
	Frame.Parent = ScreenGui

	Instance.new("UICorner", Frame).CornerRadius = UDim.new(0, 10)

	local Titulo = Instance.new("TextLabel")
	Titulo.Size = UDim2.new(1, 0, 0, 30)
	Titulo.BackgroundTransparency = 1
	Titulo.Text = "Teleport e espectar"
	Titulo.Font = Enum.Font.SourceSansBold
	Titulo.TextSize = 18
	Titulo.TextColor3 = Color3.fromRGB(255, 255, 255)
	Titulo.Parent = Frame

	local TextBox = Instance.new("TextBox")
	TextBox.PlaceholderText = "Digite as 4 primeiras letras..."
	TextBox.Text = "Digite APENAS as 4 primeiras letras da pessoa..."
	TextBox.Size = UDim2.new(1, -20, 0, 30)
	TextBox.Position = UDim2.new(0, 10, 0, 40)
	TextBox.Font = Enum.Font.SourceSans
	TextBox.TextSize = 16
	TextBox.TextColor3 = Color3.fromRGB(0, 0, 0)
	TextBox.BackgroundColor3 = Color3.fromRGB(240, 240, 240)
	TextBox.ClearTextOnFocus = false
	TextBox.Parent = Frame
	Instance.new("UICorner", TextBox).CornerRadius = UDim.new(0, 6)

	local TeleportButton = Instance.new("TextButton")
	TeleportButton.Size = UDim2.new(1, -20, 0, 30)
	TeleportButton.Position = UDim2.new(0, 10, 0, 80)
	TeleportButton.Text = "Teleportar"
	TeleportButton.Font = Enum.Font.SourceSansBold
	TeleportButton.TextSize = 16
	TeleportButton.BackgroundColor3 = Color3.fromRGB(30, 150, 250)
	TeleportButton.TextColor3 = Color3.fromRGB(255, 255, 255)
	TeleportButton.Parent = Frame
	Instance.new("UICorner", TeleportButton).CornerRadius = UDim.new(0, 6)

	local SpectateButton = Instance.new("TextButton")
	SpectateButton.Size = UDim2.new(1, -20, 0, 30)
	SpectateButton.Position = UDim2.new(0, 10, 0, 120)
	SpectateButton.Text = "Espectar"
	SpectateButton.Font = Enum.Font.SourceSansBold
	SpectateButton.TextSize = 16
	SpectateButton.BackgroundColor3 = Color3.fromRGB(70, 180, 100)
	SpectateButton.TextColor3 = Color3.fromRGB(255, 255, 255)
	SpectateButton.Parent = Frame
	Instance.new("UICorner", SpectateButton).CornerRadius = UDim.new(0, 6)

	local ResetCamButton = Instance.new("TextButton")
	ResetCamButton.Size = UDim2.new(1, -20, 0, 30)
	ResetCamButton.Position = UDim2.new(0, 10, 0, 160)
	ResetCamButton.Text = "Voltar à Câmera Normal"
	ResetCamButton.Font = Enum.Font.SourceSansBold
	ResetCamButton.TextSize = 16
	ResetCamButton.BackgroundColor3 = Color3.fromRGB(200, 90, 90)
	ResetCamButton.TextColor3 = Color3.fromRGB(255, 255, 255)
	ResetCamButton.Parent = Frame
	Instance.new("UICorner", ResetCamButton).CornerRadius = UDim.new(0, 6)

	local function encontrarPlayer(nomeInicio)
		nomeInicio = nomeInicio:lower()
		for _, plr in ipairs(Players:GetPlayers()) do
			if plr ~= LocalPlayer and plr.Name:lower():sub(1, 4) == nomeInicio then
				return plr
			end
		end
	end

	TeleportButton.MouseButton1Click:Connect(function()
		local alvo = encontrarPlayer(TextBox.Text)
		if not alvo then return end

		local char = alvo.Character
		local meuChar = LocalPlayer.Character
		if char and meuChar then
			local hrp = char:FindFirstChild("HumanoidRootPart")
			local myHrp = meuChar:FindFirstChild("HumanoidRootPart")
			if hrp and myHrp then
				myHrp.CFrame = hrp.CFrame + Vector3.new(0, 5, 0)
			end
		end
	end)

	SpectateButton.MouseButton1Click:Connect(function()
		local alvo = encontrarPlayer(TextBox.Text)
		if not alvo then return end

		local cam = workspace.CurrentCamera
		local char = alvo.Character
		if char then
			local hrp = char:FindFirstChild("HumanoidRootPart")
			if hrp then
				cam.CameraSubject = hrp
				cam.CameraType = Enum.CameraType.Custom
			end
		end
	end)

	ResetCamButton.MouseButton1Click:Connect(function()
		local cam = workspace.CurrentCamera
		local char = LocalPlayer.Character
		if char then
			local humanoid = char:FindFirstChildOfClass("Humanoid")
			if humanoid then
				cam.CameraSubject = humanoid
				cam.CameraType = Enum.CameraType.Custom
			end
		end
	end)
end)

adicionarBotao("Combate", "Aimbot", function()
	local Players = game:GetService("Players")
	local RunService = game:GetService("RunService")
	local UserInputService = game:GetService("UserInputService")
	local CoreGui = game:GetService("CoreGui")

	local player = Players.LocalPlayer
	local mouse = player:GetMouse()
	local camera = workspace.CurrentCamera

	local aimbotEnabled = false
	local rightMouseHeld = false
	local targetPartName = "Head"

	local ScreenGui = Instance.new("ScreenGui")
	ScreenGui.Name = "AimbotGui"
	ScreenGui.ResetOnSpawn = false
	ScreenGui.Parent = CoreGui

	local Frame = Instance.new("Frame")
	Frame.Size = UDim2.new(0, 300, 0, 160)
	Frame.Position = UDim2.new(0.5, -150, 0.5, -80)
	Frame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
	Frame.BorderSizePixel = 0
	Frame.AnchorPoint = Vector2.new(0.5, 0.5)
	Frame.Active = true
	Frame.Draggable = true
	Frame.Parent = ScreenGui

	local Title = Instance.new("TextLabel")
	Title.Text = "Aimbot"
	Title.Font = Enum.Font.GothamBold
	Title.TextSize = 20
	Title.TextColor3 = Color3.new(1,1,1)
	Title.BackgroundTransparency = 1
	Title.Size = UDim2.new(1, -40, 0, 30)
	Title.Position = UDim2.new(0, 10, 0, 5)
	Title.TextXAlignment = Enum.TextXAlignment.Left
	Title.Parent = Frame

	local CloseButton = Instance.new("TextButton")
	CloseButton.Text = "X"
	CloseButton.Font = Enum.Font.GothamBold
	CloseButton.TextSize = 20
	CloseButton.TextColor3 = Color3.fromRGB(255, 80, 80)
	CloseButton.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	CloseButton.BorderSizePixel = 0
	CloseButton.Size = UDim2.new(0, 30, 0, 30)
	CloseButton.Position = UDim2.new(1, -35, 0, 5)
	CloseButton.Parent = Frame

	CloseButton.MouseButton1Click:Connect(function()
		ScreenGui.Enabled = false
	end)

	local ToggleButton = Instance.new("TextButton")
	ToggleButton.Size = UDim2.new(1, -20, 0, 40)
	ToggleButton.Position = UDim2.new(0, 10, 0, 50)
	ToggleButton.BackgroundColor3 = Color3.fromRGB(80, 170, 80)
	ToggleButton.TextColor3 = Color3.new(1,1,1)
	ToggleButton.Font = Enum.Font.GothamBold
	ToggleButton.TextScaled = true
	ToggleButton.Text = "Ativar Aimbot"
	ToggleButton.AutoButtonColor = false
	ToggleButton.Parent = Frame

	ToggleButton.MouseEnter:Connect(function()
		ToggleButton.BackgroundColor3 = Color3.fromRGB(100, 200, 100)
	end)
	ToggleButton.MouseLeave:Connect(function()
		ToggleButton.BackgroundColor3 = Color3.fromRGB(80, 170, 80)
	end)

	ToggleButton.MouseButton1Click:Connect(function()
		aimbotEnabled = not aimbotEnabled
		ToggleButton.Text = aimbotEnabled and "Desativar Aimbot" or "Ativar Aimbot"
	end)

	local DropdownLabel = Instance.new("TextLabel")
	DropdownLabel.Text = "Alvo do Aimbot:"
	DropdownLabel.Size = UDim2.new(0, 120, 0, 25)
	DropdownLabel.Position = UDim2.new(0, 10, 0, 105)
	DropdownLabel.BackgroundTransparency = 1
	DropdownLabel.TextColor3 = Color3.new(1,1,1)
	DropdownLabel.Font = Enum.Font.GothamBold
	DropdownLabel.TextScaled = true
	DropdownLabel.TextXAlignment = Enum.TextXAlignment.Left
	DropdownLabel.Parent = Frame

	local Dropdown = Instance.new("TextButton")
	Dropdown.Size = UDim2.new(0, 150, 0, 25)
	Dropdown.Position = UDim2.new(0, 130, 0, 105)
	Dropdown.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	Dropdown.TextColor3 = Color3.new(1,1,1)
	Dropdown.Font = Enum.Font.GothamBold
	Dropdown.Text = targetPartName
	Dropdown.Parent = Frame

	local optionsFrame = Instance.new("Frame")
	optionsFrame.Size = UDim2.new(0, 150, 0, 60)
	optionsFrame.Position = UDim2.new(0, 130, 0, 130)
	optionsFrame.BackgroundColor3 = Color3.fromRGB(40,40,40)
	optionsFrame.Visible = false
	optionsFrame.Parent = Frame

	local function createOption(name)
		local btn = Instance.new("TextButton")
		btn.Size = UDim2.new(1, 0, 0, 30)
		btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
		btn.TextColor3 = Color3.new(1,1,1)
		btn.Font = Enum.Font.GothamBold
		btn.Text = name
		btn.Parent = optionsFrame

		btn.MouseEnter:Connect(function()
			btn.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
		end)
		btn.MouseLeave:Connect(function()
			btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
		end)

		btn.MouseButton1Click:Connect(function()
			targetPartName = name
			Dropdown.Text = name
			optionsFrame.Visible = false
		end)
	end

	createOption("Head")
	createOption("Torso")

	Dropdown.MouseButton1Click:Connect(function()
		optionsFrame.Visible = not optionsFrame.Visible
	end)
	UserInputService.InputBegan:Connect(function(input, gameProcessed)
		if not gameProcessed and input.UserInputType == Enum.UserInputType.MouseButton2 then
			rightMouseHeld = true
		end
	end)

	UserInputService.InputEnded:Connect(function(input, gameProcessed)
		if not gameProcessed and input.UserInputType == Enum.UserInputType.MouseButton2 then
			rightMouseHeld = false
		end
	end)
	local function getClosestTarget()
		local closestPlayer = nil
		local shortestDistance = math.huge
		local screenCenter = Vector2.new(camera.ViewportSize.X/2, camera.ViewportSize.Y/2)

		for _, otherPlayer in pairs(Players:GetPlayers()) do
			if otherPlayer ~= player and otherPlayer.Character and otherPlayer.Character:FindFirstChild("Humanoid") and otherPlayer.Character.Humanoid.Health > 0 then
				local targetPart = otherPlayer.Character:FindFirstChild(targetPartName)
				if targetPart then
					local screenPos, onScreen = camera:WorldToViewportPoint(targetPart.Position)
					if onScreen then
						local distance = (Vector2.new(screenPos.X, screenPos.Y) - screenCenter).Magnitude
						if distance < shortestDistance then
							shortestDistance = distance
							closestPlayer = otherPlayer
						end
					end
				end
			end
		end

		return closestPlayer
	end
	RunService.RenderStepped:Connect(function()
		if aimbotEnabled and rightMouseHeld then
			local target = getClosestTarget()
			if target and target.Character and target.Character:FindFirstChild(targetPartName) then
				local targetPart = target.Character[targetPartName]
				local targetPos = targetPart.Position
				local camPos = camera.CFrame.Position
				local direction = (targetPos - camPos).Unit
				local newCFrame = CFrame.new(camPos, camPos + direction)
				camera.CFrame = camera.CFrame:Lerp(newCFrame, 0.2)
			end
		end
	end)
end)

adicionarBotao("Combate", "Fly + bypass dano de queda (realmente funciona)", function()
	local UserInputService = game:GetService("UserInputService")
	local RunService = game:GetService("RunService")
	local Players = game:GetService("Players")
	local CoreGui = game:GetService("CoreGui")

	-- Player e character
	local player = Players.LocalPlayer
	local character = player.Character or player.CharacterAdded:Wait()
	local humanoid = character:WaitForChild("Humanoid")
	local rootPart = character:WaitForChild("HumanoidRootPart")

	local flying = false
	local speed = 50
	local toggleKey = Enum.KeyCode.E
	local esperandoTecla = false
	local ajustandoSlider = false
	local bypassEnabled = false
	local moveVector = Vector3.new()

	local ScreenGui = Instance.new("ScreenGui", CoreGui)
	ScreenGui.Name = "FlyGui"
	ScreenGui.ResetOnSpawn = false

	local Frame = Instance.new("Frame", ScreenGui)
	Frame.Size = UDim2.new(0, 280, 0, 230)
	Frame.Position = UDim2.new(0, 20, 0, 20)
	Frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	Frame.Active = true
	Frame.Draggable = true

	Instance.new("UICorner", Frame).CornerRadius = UDim.new(0, 8)

	local Title = Instance.new("TextLabel", Frame)
	Title.Text = "Fly com bypass dano de queda"
	Title.Size = UDim2.new(1, -40, 0, 30)
	Title.Position = UDim2.new(0, 10, 0, 5)
	Title.BackgroundTransparency = 1
	Title.TextColor3 = Color3.new(1,1,1)
	Title.Font = Enum.Font.GothamBold
	Title.TextSize = 20
	Title.TextXAlignment = Enum.TextXAlignment.Left

	local CloseBtn = Instance.new("TextButton", Frame)
	CloseBtn.Text = "X"
	CloseBtn.Size = UDim2.new(0, 30, 0, 30)
	CloseBtn.Position = UDim2.new(1, -40, 0, 5)
	CloseBtn.BackgroundColor3 = Color3.fromRGB(180, 50, 50)
	CloseBtn.TextColor3 = Color3.new(1,1,1)
	CloseBtn.Font = Enum.Font.GothamBold
	CloseBtn.TextSize = 18

	local ToggleBtn = Instance.new("TextButton", Frame)
	ToggleBtn.Text = "Ativar Voo ("..toggleKey.Name..")"
	ToggleBtn.Size = UDim2.new(0, 130, 0, 35)
	ToggleBtn.Position = UDim2.new(0, 10, 0, 50)
	ToggleBtn.BackgroundColor3 = Color3.fromRGB(70,70,70)
	ToggleBtn.TextColor3 = Color3.new(1,1,1)
	ToggleBtn.Font = Enum.Font.Gotham
	ToggleBtn.TextSize = 16

	local ChangeKeyBtn = Instance.new("TextButton", Frame)
	ChangeKeyBtn.Text = "Trocar Tecla"
	ChangeKeyBtn.Size = UDim2.new(0, 120, 0, 35)
	ChangeKeyBtn.Position = UDim2.new(1, -130, 0, 50)
	ChangeKeyBtn.BackgroundColor3 = Color3.fromRGB(70,70,70)
	ChangeKeyBtn.TextColor3 = Color3.new(1,1,1)
	ChangeKeyBtn.Font = Enum.Font.Gotham
	ChangeKeyBtn.TextSize = 16

	local SpeedLabel = Instance.new("TextLabel", Frame)
	SpeedLabel.Text = "Velocidade: "..speed
	SpeedLabel.Size = UDim2.new(1, -20, 0, 25)
	SpeedLabel.Position = UDim2.new(0, 10, 0, 95)
	SpeedLabel.BackgroundTransparency = 1
	SpeedLabel.TextColor3 = Color3.new(1,1,1)
	SpeedLabel.Font = Enum.Font.Gotham
	SpeedLabel.TextSize = 16
	SpeedLabel.TextXAlignment = Enum.TextXAlignment.Left

	local SliderBack = Instance.new("Frame", Frame)
	SliderBack.Size = UDim2.new(1, -20, 0, 10)
	SliderBack.Position = UDim2.new(0, 10, 0, 125)
	SliderBack.BackgroundColor3 = Color3.fromRGB(70, 70, 70)

	local SliderBar = Instance.new("Frame", SliderBack)
	SliderBar.Size = UDim2.new((speed - 10)/190, 1, 1, 0)
	SliderBar.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
	SliderBar.BorderSizePixel = 0

	local BypassBtn = Instance.new("TextButton", Frame)
	BypassBtn.Text = "Bypass Dano de Queda: OFF"
	BypassBtn.Size = UDim2.new(1, -20, 0, 40)
	BypassBtn.Position = UDim2.new(0, 10, 0, 150)
	BypassBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
	BypassBtn.TextColor3 = Color3.new(1,1,1)
	BypassBtn.Font = Enum.Font.Gotham
	BypassBtn.TextSize = 16
	local function updateSlider(pos)
		local relative = math.clamp((pos.X - SliderBack.AbsolutePosition.X) / SliderBack.AbsoluteSize.X, 0, 1)
		speed = math.floor(10 + relative * 190)
		SliderBar.Size = UDim2.new((speed - 10)/190, 0, 1, 0)
		SpeedLabel.Text = "Velocidade: "..speed
	end

	SliderBack.InputBegan:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 then
			ajustandoSlider = true
			updateSlider(input.Position)
		end
	end)

	UserInputService.InputChanged:Connect(function(input)
		if ajustandoSlider and input.UserInputType == Enum.UserInputType.MouseMovement then
			updateSlider(input.Position)
		end
	end)

	UserInputService.InputEnded:Connect(function(input)
		if input.UserInputType == Enum.UserInputType.MouseButton1 then
			ajustandoSlider = false
		end
	end)
	local function toggleFly()
		flying = not flying
		ToggleBtn.BackgroundColor3 = flying and Color3.fromRGB(0, 200, 0) or Color3.fromRGB(70,70,70)
	end

	ToggleBtn.MouseButton1Click:Connect(toggleFly)

	ChangeKeyBtn.MouseButton1Click:Connect(function()
		ChangeKeyBtn.Text = "Pressione uma tecla..."
		esperandoTecla = true
	end)

	UserInputService.InputBegan:Connect(function(input, gameProcessed)
		if gameProcessed then return end

		if esperandoTecla and input.UserInputType == Enum.UserInputType.Keyboard then
			toggleKey = input.KeyCode
			ToggleBtn.Text = "Ativar Voo ("..toggleKey.Name..")"
			ChangeKeyBtn.Text = "Trocar Tecla"
			esperandoTecla = false
			return
		end

		if input.KeyCode == toggleKey then
			toggleFly()
		end
	end)

	CloseBtn.MouseButton1Click:Connect(function()
		ScreenGui:Destroy()
	end)

	BypassBtn.MouseButton1Click:Connect(function()
		if player.Character:FindFirstChild("DanoQueda") then
			player.Character:FindFirstChild("DanoQueda"):Destroy()
		end
		BypassBtn.Text = "Bypass Dano de Queda: ON"
		BypassBtn.BackgroundColor3 = bypassEnabled and Color3.fromRGB(0, 200, 0)
	end)
	local function updateMoveVector()
		local cam = workspace.CurrentCamera
		local look = cam.CFrame.LookVector
		local right = cam.CFrame.RightVector
		local up = Vector3.new(0,1,0)

		local forward = 0
		local rightVal = 0
		local upVal = 0

		if UserInputService:IsKeyDown(Enum.KeyCode.W) then forward += 1 end
		if UserInputService:IsKeyDown(Enum.KeyCode.S) then forward -= 1 end
		if UserInputService:IsKeyDown(Enum.KeyCode.A) then rightVal -= 1 end
		if UserInputService:IsKeyDown(Enum.KeyCode.D) then rightVal += 1 end
		if UserInputService:IsKeyDown(Enum.KeyCode.Space) then upVal += 1 end
		if UserInputService:IsKeyDown(Enum.KeyCode.LeftControl) then upVal -= 1 end

		local dir = (look * forward + right * rightVal + up * upVal)
		moveVector = dir.Magnitude > 0 and dir.Unit or Vector3.new()
	end

	RunService.RenderStepped:Connect(function()
		if not player.Character or not player.Character:FindFirstChild("HumanoidRootPart") or not player.Character:FindFirstChild("Humanoid") then
			character = player.Character or player.CharacterAdded:Wait()
			humanoid = character:WaitForChild("Humanoid")
			rootPart = character:WaitForChild("HumanoidRootPart")
		end

		if flying then
			updateMoveVector()
			local cam = workspace.CurrentCamera
			local _, y, _ = cam.CFrame.Rotation:ToEulerAnglesYXZ()
			rootPart.CFrame = CFrame.new(rootPart.Position) * CFrame.Angles(0,y,0)
			rootPart.AssemblyLinearVelocity = moveVector * speed
			if humanoid.AutoRotate then
				humanoid.AutoRotate = false
			end
		else
			if not humanoid.AutoRotate then
				humanoid.AutoRotate = true
			end
		end
	end)
	player.AncestryChanged:Connect(function(_, parent)
		if not parent then
			flying = false
			bypassEnabled = false
		end
	end)
end)


adicionarBotao("Teleportes", "Ir para Base", function()
	print("Teleportando para base")
end)

adicionarBotao("Farm", "Entrar em empregos", function()
	local mercadinmote_upvr = game:GetService("ReplicatedStorage"):WaitForChild("RemoteNovos"):WaitForChild("mercadinmote")

	pcall(function()
		game.CoreGui:FindFirstChild("menuEmprego"):Destroy()
	end)

	local ScreenGui = Instance.new("ScreenGui")
	ScreenGui.Name = "menuEmprego"
	ScreenGui.ResetOnSpawn = false
	ScreenGui.Parent = game.CoreGui

	local Frame = Instance.new("Frame")
	Frame.Size = UDim2.new(0, 260, 0, 310)
	Frame.Position = UDim2.new(0.3, 0, 0.3, 0)
	Frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	Frame.BorderSizePixel = 0
	Frame.Draggable = true
	Frame.Active = true
	Frame.Selectable = true
	Frame.Parent = ScreenGui
	Instance.new("UICorner", Frame).CornerRadius = UDim.new(0, 10)

	local Titulo = Instance.new("TextLabel")
	Titulo.Size = UDim2.new(1, 0, 0, 30)
	Titulo.BackgroundTransparency = 1
	Titulo.Text = "ENTRAR EM EMPREGOS"
	Titulo.Font = Enum.Font.SourceSansBold
	Titulo.TextSize = 18
	Titulo.TextColor3 = Color3.fromRGB(255, 255, 255)
	Titulo.Parent = Frame

	local trabalhos = {
		"Gari",
		"Civil",
		"Minerador",
		"Entregador de Gás",
		"Fazendeiro",
		"Mecanico",
		"Pescador"
	}

	for i, nome in ipairs(trabalhos) do
		local botao = Instance.new("TextButton")
		botao.Size = UDim2.new(1, -20, 0, 30)
		botao.Position = UDim2.new(0, 10, 0, 30 + (i * 35))
		botao.Text = nome
		botao.Font = Enum.Font.SourceSansBold
		botao.TextSize = 16
		botao.BackgroundColor3 = Color3.fromRGB(30, 150, 250)
		botao.TextColor3 = Color3.fromRGB(255, 255, 255)
		botao.Parent = Frame
		Instance.new("UICorner", botao).CornerRadius = UDim.new(0, 6)

		botao.MouseButton1Click:Connect(function()
			mercadinmote_upvr:FireServer("trabalhosTimes", {nome})
		end)
	end
end)

adicionarBotao("Farm", "Farm gari (para parar de rejoin)", function()
	local Players = game:GetService("Players")
	local player = Players.LocalPlayer
	local RunService = game:GetService("RunService")
	local camera = workspace.CurrentCamera

	local function getCharacter()
		local character = player.Character or player.CharacterAdded:Wait()
		local root = character:WaitForChild("HumanoidRootPart")
		return character, root
	end

	local character, humanoideRootPart = getCharacter()

	local function removerColisao()
		for _, part in ipairs(character:GetDescendants()) do
			if part:IsA("BasePart") then
				part.CanCollide = false
			end
		end
	end

	removerColisao()
	character.DescendantAdded:Connect(function(part)
		if part:IsA("BasePart") then
			part.CanCollide = false
		end
	end)

	local pastaLixos = workspace:WaitForChild("MapaGeral"):WaitForChild("Gari"):WaitForChild("Lixos")

	local function getLixosDisponiveis()
		local ativos = {}
		for _, obj in ipairs(pastaLixos:GetDescendants()) do
			if obj:IsA("BasePart") and obj.Name == "LEXOS" and obj.Transparency == 0 then
				local prompt = obj:FindFirstChildWhichIsA("ProximityPrompt", true)
				if prompt then
					prompt.MaxActivationDistance = 50
					prompt.HoldDuration = 1.3
					table.insert(ativos, {base = obj, prompt = prompt})
				end
			end
		end
		return ativos
	end

	local function ativarPromptComCamera(base, prompt)
		local _, humanoideRootPart = getCharacter()
		local posicao = base.Position + Vector3.new(0, 3, 0)
		humanoideRootPart.CFrame = CFrame.new(posicao, base.Position)

		camera.CameraType = Enum.CameraType.Scriptable
		camera.CFrame = CFrame.new(camera.CFrame.Position, base.Position)

		task.wait(0.4)

		local sucesso = pcall(function()
			fireproximityprompt(prompt, true)
		end)

		task.wait(prompt.HoldDuration + 0.3)

		camera.CameraType = Enum.CameraType.Custom

		return sucesso
	end

	task.spawn(function()
		while true do
			local lixos = getLixosDisponiveis()

			for _, info in ipairs(lixos) do
				local base = info.base
				local prompt = info.prompt

				if base and base.Transparency == 0 and prompt and prompt.Enabled then
					ativarPromptComCamera(base, prompt)
				end
			end

			task.wait(1)
		end
	end)
end)

    else
        StatusLabel.Text = message or "Key Inválida"
        StatusLabel.TextColor3 = Color3.fromRGB(255, 0, 0)
        wait(2)
        VerifyButton.Text = "Verificar Key"
    end
end)
