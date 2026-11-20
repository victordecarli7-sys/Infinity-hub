--[[
    INFINITY HU
    Purple Edition
    LocalScript | Roblox Studio
]]

local Players = game:GetService("Players")
local player = Players.LocalPlayer

local IMAGE_ID = "rbxassetid://SEU_ID_DA_IMAGEM"

local Purple = Color3.fromRGB(125, 0, 255)
local DarkPurple = Color3.fromRGB(45, 0, 90)
local Black = Color3.fromRGB(8, 5, 12)
local White = Color3.fromRGB(255, 255, 255)

local gui = Instance.new("ScreenGui")
gui.Name = "InfinityHub"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

-- BOTÃO DA CAVEIRA
local Toggle = Instance.new("ImageButton")
Toggle.Name = "SkullToggle"
Toggle.Size = UDim2.fromOffset(75, 75)
Toggle.Position = UDim2.new(0, 15, 0.4, 0)
Toggle.Image = IMAGE_ID
Toggle.BackgroundColor3 = Black
Toggle.BorderSizePixel = 0
Toggle.Parent = gui

Instance.new("UICorner", Toggle).CornerRadius = UDim.new(1, 0)

local ToggleStroke = Instance.new("UIStroke")
ToggleStroke.Color = Purple
ToggleStroke.Thickness = 3
ToggleStroke.Parent = Toggle

-- PAINEL
local Main = Instance.new("Frame")
Main.Name = "MainHub"
Main.Size = UDim2.fromOffset(330, 350)
Main.Position = UDim2.new(0.5, -165, 0.5, -175)
Main.BackgroundColor3 = Black
Main.BorderSizePixel = 0
Main.Visible = false
Main.Parent = gui

Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 14)

local MainStroke = Instance.new("UIStroke")
MainStroke.Color = Purple
MainStroke.Thickness = 2
MainStroke.Parent = Main

-- CAPA
local Cover = Instance.new("ImageLabel")
Cover.Name = "HubCover"
Cover.Size = UDim2.new(1, 0, 0, 115)
Cover.BackgroundColor3 = Black
Cover.Image = IMAGE_ID
Cover.ScaleType = Enum.ScaleType.Crop
Cover.Parent = Main

Instance.new("UICorner", Cover).CornerRadius = UDim.new(0, 12)

-- TÍTULO
local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, -20, 0, 40)
Title.Position = UDim2.new(0, 10, 0, 115)
Title.BackgroundTransparency = 1
Title.Text = "INFINITY HUB"
Title.TextColor3 = White
Title.TextSize = 22
Title.Font = Enum.Font.GothamBold
Title.Parent = Main

-- SUBTÍTULO
local Subtitle = Instance.new("TextLabel")
Subtitle.Size = UDim2.new(1, 0, 0, 20)
Subtitle.Position = UDim2.new(0, 0, 0, 150)
Subtitle.BackgroundTransparency = 1
Subtitle.Text = "PURPLE EDITION"
Subtitle.TextColor3 = Purple
Subtitle.TextSize = 12
Subtitle.Font = Enum.Font.GothamBold
Subtitle.Parent = Main

-- BOTÕES
local function createButton(name, y)
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0, 280, 0, 43)
    button.Position = UDim2.new(0, 25, 0, y)
    button.BackgroundColor3 = DarkPurple
    button.BorderSizePixel = 0
    button.TextColor3 = White
    button.TextSize = 15
    button.Font = Enum.Font.GothamBold
    button.Text = name .. " [OFF]"
    button.Parent = Main

    Instance.new("UICorner", button).CornerRadius = UDim.new(0, 8)

    local stroke = Instance.new("UIStroke")
    stroke.Color = Purple
    stroke.Thickness = 1
    stroke.Parent = button

    local enabled = false

    button.MouseButton1Click:Connect(function()
        enabled = not enabled
        button.Text = name .. (enabled and " [ON]" or " [OFF]")
        button.BackgroundColor3 = enabled and Purple or DarkPurple
    end)

    return button
end

createButton("Farm Level", 185)
createButton("Sea Event", 237)
createButton("Halloween Event", 289)

-- FECHAR
local Close = Instance.new("TextButton")
Close.Size = UDim2.fromOffset(35, 35)
Close.Position = UDim2.new(1, -40, 0, 120)
Close.Text = "X"
Close.TextColor3 = White
Close.TextSize = 18
Close.Font = Enum.Font.GothamBold
Close.BackgroundColor3 = Purple
Close.BorderSizePixel = 0
Close.Parent = Main

Instance.new("UICorner", Close).CornerRadius = UDim.new(0, 8)

-- ABRIR E FECHAR PAINEL
Toggle.MouseButton1Click:Connect(function()
    Main.Visible = not Main.Visible
end)

Close.MouseButton1Click:Connect(function()
    Main.Visible = false
end)

print("INFINITY HUB PURPLE EDITION carregado!")
