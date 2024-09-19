local player = game.Players.LocalPlayer
local userInputService = game:GetService("UserInputService")
local screenGui = Instance.new("ScreenGui")
local menuFrame = Instance.new("Frame")

-- Заставка
local splashScreen = Instance.new("Frame")
splashScreen.Size = UDim2.new(1, 0, 1, 0) -- Занимает весь экран
splashScreen.BackgroundColor3 = Color3.fromRGB(0, 0, 0) -- Черный фон
splashScreen.Parent = screenGui

local splashText = Instance.new("TextLabel")
splashText.Size = UDim2.new(1, 0, 1, 0)
splashText.Position = UDim2.new(0, 0, 0, 0)
splashText.Text = "Tabyretka script"
splashText.TextColor3 = Color3.fromRGB(128, 0, 128) -- Фиолетовый цвет
splashText.TextScaled = true
splashText.BackgroundTransparency = 1 -- Прозрачный фон для текста
splashText.Parent = splashScreen

-- Настройки меню
menuFrame.Size = UDim2.new(0, 400, 0, 400)
menuFrame.Position = UDim2.new(0.5, -200, 0.5, -200)
menuFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
menuFrame.Visible = false
menuFrame.Parent = screenGui

-- Вкладки
local tabSetting = Instance.new("TextButton")
tabSetting.Size = UDim2.new(0, 100, 0, 50)
tabSetting.Position = UDim2.new(0, 0, 0, 0)
tabSetting.Text = "Setting"
tabSetting.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
tabSetting.Parent = menuFrame

local tabVisual = Instance.new("TextButton")
tabVisual.Size = UDim2.new(0, 100, 0, 50)
tabVisual.Position = UDim2.new(0, 0, 0, 50)
tabVisual.Text = "Visual"
tabVisual.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
tabVisual.Parent = menuFrame

-- Панель функций
local functionFrame = Instance.new("Frame")
functionFrame.Size = UDim2.new(1, 0, 1, 0)
functionFrame.Position = UDim2.new(0, 100, 0, 0)
functionFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
functionFrame.Parent = menuFrame

-- Вкладка Setting
local fontDropdown, colorDropdown, backgroundColorDropdown, sizeButton, colorIndicator = nil, nil, nil, nil, nil

local function createSettingControls()  
    fontDropdown = Instance.new("TextButton")
    fontDropdown.Size = UDim2.new(1, 0, 0, 50)
    fontDropdown.Position = UDim2.new(0, 0, 0, 0)
    fontDropdown.Text = "Font: Default"
    fontDropdown.Parent = functionFrame

    colorDropdown = Instance.new("TextButton")
    colorDropdown.Size = UDim2.new(1, 0, 0, 50)
    colorDropdown.Position = UDim2.new(0, 0, 0, 50)
    colorDropdown.Text = "Text Color: White"
    colorDropdown.Parent = functionFrame

    backgroundColorDropdown = Instance.new("TextButton")
    backgroundColorDropdown.Size = UDim2.new(1, 0, 0, 50)
    backgroundColorDropdown.Position = UDim2.new(0, 0, 0, 100)
    backgroundColorDropdown.Text = "Menu Color: Grey"
    backgroundColorDropdown.Parent = functionFrame

    sizeButton = Instance.new("TextButton")
    sizeButton.Size = UDim2.new(1, 0, 0, 50)
    sizeButton.Position = UDim2.new(0, 0, 0, 150)
    sizeButton.Text = "Increase Menu Size"
    sizeButton.Parent = functionFrame
    
    -- Индикатор цвета
    colorIndicator = Instance.new("TextLabel")
    colorIndicator.Size = UDim2.new(1, 0, 0, 30)
    colorIndicator.Position = UDim2.new(0, 0, 0, 200)
    colorIndicator.Text = "Text Indicator: OFF"
    colorIndicator.BackgroundTransparency = 1
    colorIndicator.TextColor3 = Color3.fromRGB(255, 255, 255) -- Начальный цвет
    colorIndicator.Parent = functionFrame
end

-- Вкладка Visual
local espItemButton, espPlayerButton = nil, nil

local function createVisualControls()  
    espItemButton = Instance.new("TextButton")
    espItemButton.Size = UDim2.new(1, 0, 0, 50)
    espItemButton.Position = UDim2.new(0, 0, 0, 0)
    espItemButton.Text = "Toggle Item ESP"
    espItemButton.Parent = functionFrame

    espPlayerButton = Instance.new("TextButton")
    espPlayerButton.Size = UDim2.new(1, 0, 0, 50)
    espPlayerButton.Position = UDim2.new(0, 0, 0, 50)
    espPlayerButton.Text = "Toggle Player ESP"
    espPlayerButton.Parent = functionFrame
end

-- Параметры задержки трансформации
local transitionDelay = 2.5 -- Время задержки перед переходом

-- Переключение вкладок
local function showTab(tab)
    functionFrame.Visible = true
    if tab == "Setting" then
        createSettingControls()
        colorIndicator.Text = "Text Indicator: OFF" -- Сброс статуса индикатора
        espItemButton.Visible = false
        espPlayerButton.Visible = false
    else
        functionFrame:ClearAllChildren() -- Очищаем предыдущие элементы
        createVisualControls()
        espItemButton.Visible = true
        espPlayerButton.Visible = true
    end
end

tabSetting.MouseButton1Click:Connect(function()
    showTab("Setting")
end)

tabVisual.MouseButton1Click:Connect(function()
    showTab("Visual")
end)

-- Механизм заставки с плавным переходом
splashScreen.Parent = screenGui
wait(transitionDelay) -- Задержка перед переходом

-- Плавный переход в меню
for i = 1, 10 do
    splashScreen.BackgroundTransparency = i * 0.1
    menuFrame.BackgroundTransparency = 1 - (i * 0.1)
    wait(0.1) -- Настроить скорость плавного перехода
end

splashScreen:Destroy() -- Удаляем заставку после задержки
menuFrame.Visible = true -- Показываем меню

-- Обработчики для кнопок в Setting
local fontIndex = 1
local function changeFont()
    local fonts = {
        Enum.Font.SourceSans,
        Enum.Font.SourceSansBold,
        Enum.Font.SourceSansItalic,
        Enum.Font.SourceSerif,
        Enum.Font.SourceSansCondensed
    }
    fontIndex = (fontIndex % #fonts) + 1
    fontDropdown.Font = fonts[fontIndex]
    fontDropdown.Text = "Font: " .. fonts[fontIndex].Name
end

fontDropdown.MouseButton1Click:Connect(function()
    changeFont()
end)

local textColorIndex = 1
local function changeTextColor()
    local textColors = {
        Color3.fromRGB(255, 255, 255), -- White
        Color3.fromRGB(0, 0, 0), -- Black
        Color3.fromRGB(0, 0, 255), -- Blue
        Color3.fromRGB(255, 0, 0), -- Red
        Color3.fromRGB(128, 0, 128) -- Purple
    }
    textColorIndex = (textColorIndex % #textColors) + 1
    colorIndicator.TextColor3 = textColors[textColorIndex]
    colorDropdown.TextColor3 = textColors[textColorIndex]
    colorIndicator.Text = "Text Indicator: ON" -- Активируем индикатор
end

colorDropdown.MouseButton1Click:Connect(function()
    changeTextColor()
end)

local backgroundColorIndex = 1
local function changeMenuColor()
    local backgroundColors = {
        Color3.fromRGB(50, 50, 50), -- Grey
        Color3.fromRGB(255, 255, 255), -- White
        Color3.fromRGB(0, 0, 0), -- Black
        Color3.fromRGB(0, 0, 255), -- Blue
        Color3.fromRGB(255, 0, 0), -- Red
        Color3.fromRGB(128, 0, 128) -- Purple
    }
    backgroundColorIndex = (backgroundColorIndex % #backgroundColors) + 1
    menuFrame.BackgroundColor3 = backgroundColors[backgroundColorIndex]
    backgroundColorDropdown.Text = "Menu Color: " .. (backgroundColorIndex == 1 and "Grey" or "Color Not Displayed")
end

backgroundColorDropdown.MouseButton1Click:Connect(function()
    changeMenuColor()
end)

sizeButton.MouseButton1Click:Connect(function()
    menuFrame.Size = UDim2.new(0, menuFrame.Size.X.Offset + 50, 0, menuFrame.Size.Y.Offset + 50) -- Увеличиваем размер меню
end)

-- Обработчики для кнопок в Visual
espItemButton.MouseButton1Click:Connect(function()
    -- Логика переключения Item ESP здесь
    print("Toggle Item ESP clicked") -- Замените это реальной логикой
end)

espPlayerButton.MouseButton1Click:Connect(function()
    -- Логика переключения Player ESP здесь
    print("Toggle Player ESP clicked") -- Замените это реальной логикой
end)
