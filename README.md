local x4 = game:GetService("Players")
local x12 = game:GetService("UserInputService")
local x5 = x4.LocalPlayer
local x15 = Instance.new("ScreenGui")
x15.Parent = game:GetService("CoreGui")
local x11 = Instance.new("TextBox")
x11.Size = UDim2.new(0, 200, 0, 40)
x11.Position = UDim2.new(0.5, -100, 0.5, -20)
x11.Text = ""
x11.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
x11.BackgroundTransparency = 0.2
x11.BorderSizePixel = 0
x11.TextColor3 = Color3.fromRGB(255, 0, 0)
x11.Font = Enum.Font.GothamBold
x11.PlaceholderText = "unji"
x11.TextXAlignment = Enum.TextXAlignment.Center
x11.TextYAlignment = Enum.TextYAlignment.Center
x11.Parent = x15

local function x6(x14)
    for _, x7 in pairs(x4:GetPlayers()) do
        pcall(function()
            local x8 = x7.Character
            if x8 then
                local x10 = x8:FindFirstChild("UpdateSign", true)
                if x10 then
                    x10:FireServer(x14)
                end
            end
        end)
    end
end

local x13 = ""
local x9

local function x3()
    if x9 then x9:Disconnect() end
    x9 = game:GetService("RunService").Heartbeat:Connect(function()
        if x13 ~= "" then
            x6(x13)
        end
    end)
end

x11:GetPropertyChangedSignal("Text"):Connect(function()
    local x2 = x11.Text
    if x2 ~= x13 then
        x13 = x2
        local x1 = Instance.new("Sound")
        x1.SoundId = "rbxassetid://7293306821"
        x1.Parent = x11.Parent
        x1:Play()
        x1.Ended:Connect(function()
            x1:Destroy()
        end)
        x3()
    end
end)
