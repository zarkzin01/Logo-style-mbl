print("[LZINN LOGO] iniciando...")

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local player = Players.LocalPlayer

local ASSET_ID = 121036642893138

-- parent pro Delta
local parent = nil
pcall(function()
	parent = gethui()
end)
if not parent then
	pcall(function()
		parent = game:GetService("CoreGui")
	end)
end
if not parent then
	parent = player:WaitForChild("PlayerGui")
end

print("[LZINN LOGO] parent =", parent.Name)

-- limpa antigo
pcall(function()
	local old = parent:FindFirstChild("LZINN_LogoUI")
	if old then old:Destroy() end
end)

local sg = Instance.new("ScreenGui")
sg.Name = "LZINN_LogoUI"
sg.ResetOnSpawn = false
sg.IgnoreGuiInset = true
sg.DisplayOrder = 999
sg.Parent = parent

pcall(function()
	if syn and syn.protect_gui then
		syn.protect_gui(sg)
	end
end)

-- LOGO
local logo = Instance.new("ImageLabel")
logo.BackgroundTransparency = 1
logo.Size = UDim2.new(0, 120, 0, 120)
logo.AnchorPoint = Vector2.new(0.5, 0)
logo.Position = UDim2.new(0.5, 0, 0, 30)
logo.Image = "rbxassetid://" .. tostring(ASSET_ID)
logo.ScaleType = Enum.ScaleType.Fit
logo.Parent = sg

-- se nao carregar, tenta thumb
task.spawn(function()
	task.wait(1)
	if not logo.IsLoaded then
		logo.Image = "rbxthumb://type=Asset&id=" .. tostring(ASSET_ID) .. "&w=420&h=420"
	end
end)

-- BOTAO ABRIR
local btn = Instance.new("TextButton")
btn.Name = "OpenBtn"
btn.Size = UDim2.new(0, 60, 0, 60)
btn.AnchorPoint = Vector2.new(1, 0)
btn.Position = UDim2.new(1, -16, 0, 20)
btn.BackgroundColor3 = Color3.fromRGB(255, 170, 30)
btn.Text = "LOGO"
btn.TextColor3 = Color3.fromRGB(30, 20, 0)
btn.TextSize = 12
btn.Font = Enum.Font.SourceSansBold
btn.Parent = sg

local c1 = Instance.new("UICorner")
c1.CornerRadius = UDim.new(0, 12)
c1.Parent = btn

-- PAINEL SIMPLES
local panel = Instance.new("Frame")
panel.Size = UDim2.new(0, 240, 0, 180)
panel.AnchorPoint = Vector2.new(1, 0)
panel.Position = UDim2.new(1, -16, 0, 90)
panel.BackgroundColor3 = Color3.fromRGB(30, 30, 36)
panel.Visible = false
panel.Parent = sg

local c2 = Instance.new("UICorner")
c2.CornerRadius = UDim.new(0, 12)
c2.Parent = panel

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 36)
title.BackgroundColor3 = Color3.fromRGB(40, 40, 48)
title.BorderSizePixel = 0
title.Text = "LOGO UI"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 16
title.Parent = panel

local c3 = Instance.new("UICorner")
c3.CornerRadius = UDim.new(0, 12)
c3.Parent = title

-- tamanho +
local plus = Instance.new("TextButton")
plus.Size = UDim2.new(0, 100, 0, 36)
plus.Position = UDim2.new(0, 16, 0, 50)
plus.BackgroundColor3 = Color3.fromRGB(60, 120, 220)
plus.Text = "TAMANHO +"
plus.TextColor3 = Color3.new(1, 1, 1)
plus.Font = Enum.Font.SourceSansBold
plus.TextSize = 14
plus.Parent = panel

local c4 = Instance.new("UICorner")
c4.CornerRadius = UDim.new(0, 8)
c4.Parent = plus

-- tamanho -
local minus = Instance.new("TextButton")
minus.Size = UDim2.new(0, 100, 0, 36)
minus.Position = UDim2.new(0, 124, 0, 50)
minus.BackgroundColor3 = Color3.fromRGB(60, 120, 220)
minus.Text = "TAMANHO -"
minus.TextColor3 = Color3.new(1, 1, 1)
minus.Font = Enum.Font.SourceSansBold
minus.TextSize = 14
minus.Parent = panel

local c5 = Instance.new("UICorner")
c5.CornerRadius = UDim.new(0, 8)
c5.Parent = minus

-- transparencia
local moreClear = Instance.new("TextButton")
moreClear.Size = UDim2.new(0, 100, 0, 36)
moreClear.Position = UDim2.new(0, 16, 0, 96)
moreClear.BackgroundColor3 = Color3.fromRGB(80, 80, 100)
moreClear.Text = "MAIS CLARO"
moreClear.TextColor3 = Color3.new(1, 1, 1)
moreClear.Font = Enum.Font.SourceSansBold
moreClear.TextSize = 13
moreClear.Parent = panel

local c6 = Instance.new("UICorner")
c6.CornerRadius = UDim.new(0, 8)
c6.Parent = moreClear

local moreDark = Instance.new("TextButton")
moreDark.Size = UDim2.new(0, 100, 0, 36)
moreDark.Position = UDim2.new(0, 124, 0, 96)
moreDark.BackgroundColor3 = Color3.fromRGB(80, 80, 100)
moreDark.Text = "MAIS FORTE"
moreDark.TextColor3 = Color3.new(1, 1, 1)
moreDark.Font = Enum.Font.SourceSansBold
moreDark.TextSize = 13
moreDark.Parent = panel

local c7 = Instance.new("UICorner")
c7.CornerRadius = UDim.new(0, 8)
c7.Parent = moreDark

local hide = Instance.new("TextButton")
hide.Size = UDim2.new(1, -32, 0, 32)
hide.Position = UDim2.new(0, 16, 0, 140)
hide.BackgroundColor3 = Color3.fromRGB(180, 60, 60)
hide.Text = "OCULTAR / MOSTRAR"
hide.TextColor3 = Color3.new(1, 1, 1)
hide.Font = Enum.Font.SourceSansBold
hide.TextSize = 13
hide.Parent = panel

local c8 = Instance.new("UICorner")
c8.CornerRadius = UDim.new(0, 8)
c8.Parent = hide

local sizeNow = 120
local transp = 0.1

plus.MouseButton1Click:Connect(function()
	sizeNow = math.clamp(sizeNow + 20, 60, 400)
	logo.Size = UDim2.new(0, sizeNow, 0, sizeNow)
end)

minus.MouseButton1Click:Connect(function()
	sizeNow = math.clamp(sizeNow - 20, 60, 400)
	logo.Size = UDim2.new(0, sizeNow, 0, sizeNow)
end)

moreClear.MouseButton1Click:Connect(function()
	transp = math.clamp(transp + 0.1, 0, 0.9)
	logo.ImageTransparency = transp
end)

moreDark.MouseButton1Click:Connect(function()
	transp = math.clamp(transp - 0.1, 0, 0.9)
	logo.ImageTransparency = transp
end)

hide.MouseButton1Click:Connect(function()
	logo.Visible = not logo.Visible
end)

btn.MouseButton1Click:Connect(function()
	panel.Visible = not panel.Visible
end)

print("[LZINN LOGO] OK - botao amarelo no canto superior direito")