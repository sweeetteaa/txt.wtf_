# txt.wtf - Roblox UI Library

A modern, lightweight, and feature-rich UI library for Roblox exploiting.

## Features

- 🎨 **Two Built-in Themes** - Dark and Light modes
- 🖱️ **Draggable Windows** - Smooth dragging with tweening
- 📑 **Tab System** - Organize your UI with multiple tabs
- 🎯 **Multiple Element Types** - Buttons, Toggles, Sliders, Dropdowns, Inputs, Labels, Sections, Keybinds
- 🔔 **Notification System** - Built-in notifications
- ✨ **Smooth Animations** - TweenService-powered transitions
- 🎪 **Clean API** - Simple and intuitive to use

## Installation

```lua
local Library = loadstring(game:HttpGet("https://github.com/sweeetteaa/ahehienanjiwi/blob/main/library.lua"))()
```

## Quick Start

```lua
-- Load the library
local Library = loadstring(game:HttpGet("https://github.com/sweeetteaa/ahehienanjiwi/blob/main/library.lua"))()

-- Create a window
local Window = Library:CreateWindow({
    Title = "My Script",
    Theme = "Dark", -- "Dark" or "Light"
    Size = UDim2.new(0, 500, 0, 400) -- Optional
})

-- Create a tab
local Tab = Window:CreateTab("Main")

-- Add elements
Tab:CreateButton({
    Name = "Click Me",
    Callback = function()
        print("Button clicked!")
    end
})
```

## API Documentation

### Library

#### `Library:CreateWindow(config)`
Creates a new window.

**Parameters:**
- `config` (table)
  - `Title` (string) - Window title (default: "txt.wtf")
  - `Theme` (string) - "Dark" or "Light" (default: "Dark")
  - `Size` (UDim2) - Window size (default: UDim2.new(0, 500, 0, 400))

**Returns:** Window object

#### `Library:Notify(config)`
Displays a notification.

**Parameters:**
- `config` (table)
  - `Title` (string) - Notification title
  - `Content` (string) - Notification content
  - `Duration` (number) - Duration in seconds (default: 3)

### Window

#### `Window:CreateTab(name)`
Creates a new tab.

**Parameters:**
- `name` (string) - Tab name

**Returns:** Tab object

### Tab Elements

#### `Tab:CreateButton(config)`
Creates a clickable button.

**Parameters:**
- `config` (table)
  - `Name` (string) - Button text
  - `Callback` (function) - Function to call when clicked

**Example:**
```lua
Tab:CreateButton({
    Name = "Reset Character",
    Callback = function()
        game.Players.LocalPlayer.Character.Humanoid.Health = 0
    end
})
```

#### `Tab:CreateToggle(config)`
Creates a toggle switch.

**Parameters:**
- `config` (table)
  - `Name` (string) - Toggle label
  - `Default` (boolean) - Initial state (default: false)
  - `Callback` (function) - Called with new state (true/false)

**Returns:** Object with `SetValue(value)` method

**Example:**
```lua
local Toggle = Tab:CreateToggle({
    Name = "Auto Farm",
    Default = false,
    Callback = function(state)
        print("Auto Farm is now:", state)
    end
})

-- Update programmatically
Toggle:SetValue(true)
```

#### `Tab:CreateSlider(config)`
Creates a value slider.

**Parameters:**
- `config` (table)
  - `Name` (string) - Slider label
  - `Min` (number) - Minimum value (default: 0)
  - `Max` (number) - Maximum value (default: 100)
  - `Default` (number) - Initial value (default: Min)
  - `Increment` (number) - Step size (default: 1)
  - `Callback` (function) - Called with new value

**Returns:** Object with `SetValue(value)` method

**Example:**
```lua
local Slider = Tab:CreateSlider({
    Name = "Walkspeed",
    Min = 16,
    Max = 200,
    Default = 16,
    Increment = 1,
    Callback = function(value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
    end
})

-- Update programmatically
Slider:SetValue(100)
```

#### `Tab:CreateDropdown(config)`
Creates a dropdown menu.

**Parameters:**
- `config` (table)
  - `Name` (string) - Dropdown label
  - `Options` (table) - Array of option strings
  - `Default` (string) - Initially selected option
  - `Callback` (function) - Called with selected option

**Returns:** Object with `SetValue(value)` method

**Example:**
```lua
local Dropdown = Tab:CreateDropdown({
    Name = "Select Weapon",
    Options = {"Sword", "Bow", "Staff", "Axe"},
    Default = "Sword",
    Callback = function(option)
        print("Selected:", option)
    end
})

-- Update programmatically
Dropdown:SetValue("Bow")
```

#### `Tab:CreateInput(config)`
Creates a text input field.

**Parameters:**
- `config` (table)
  - `Name` (string) - Input label (unused in current implementation)
  - `Placeholder` (string) - Placeholder text
  - `Default` (string) - Initial text
  - `Callback` (function) - Called with text when Enter is pressed

**Returns:** Object with `SetValue(value)` method

**Example:**
```lua
local Input = Tab:CreateInput({
    Placeholder = "Enter player name...",
    Default = "",
    Callback = function(text)
        print("Input:", text)
    end
})

-- Update programmatically
Input:SetValue("NewText")
```

#### `Tab:CreateLabel(text)`
Creates a text label.

**Parameters:**
- `text` (string) - Label text

**Returns:** Object with `SetText(text)` method

**Example:**
```lua
local Label = Tab:CreateLabel("Version 1.0.0")

-- Update text
Label:SetText("Version 1.0.1")
```

#### `Tab:CreateSection(name)`
Creates a section divider with title.

**Parameters:**
- `name` (string) - Section title

**Example:**
```lua
Tab:CreateSection("Player Settings")
```

#### `Tab:CreateKeybind(config)`
Creates a keybind that triggers a callback.

**Parameters:**
- `config` (table)
  - `Name` (string) - Keybind label
  - `Default` (Enum.KeyCode) - Initial key
  - `Callback` (function) - Function to call when key is pressed

**Returns:** Object with `SetKey(keycode)` method

**Example:**
```lua
local Keybind = Tab:CreateKeybind({
    Name = "Toggle Flight",
    Default = Enum.KeyCode.F,
    Callback = function()
        print("F key pressed!")
    end
})

-- Update key
Keybind:SetKey(Enum.KeyCode.G)
```

## Theme Colors

### Dark Theme
- Background: RGB(20, 20, 25)
- Secondary: RGB(30, 30, 35)
- Tertiary: RGB(40, 40, 45)
- Accent: RGB(138, 43, 226) - Purple
- Text: RGB(255, 255, 255)
- SubText: RGB(180, 180, 180)
- Border: RGB(60, 60, 65)

### Light Theme
- Background: RGB(240, 240, 245)
- Secondary: RGB(250, 250, 255)
- Tertiary: RGB(235, 235, 240)
- Accent: RGB(138, 43, 226) - Purple
- Text: RGB(20, 20, 25)
- SubText: RGB(100, 100, 110)
- Border: RGB(200, 200, 210)

## Full Example

See `example_usage.lua` for a comprehensive example with all element types.

## License

Free to use and modify. Credit appreciated but not required.

## Created By

txt.wtf - A modern Roblox UI library
