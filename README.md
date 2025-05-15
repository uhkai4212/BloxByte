# BloxByte UI Library Documentation

## Overview

BloxByte UI Library is a lightweight, customizable user interface framework for Roblox games. It provides an elegant, modern UI solution inspired by popular script hubs with features like toggles, buttons, sections, and a draggable interface.

![BloxByte UI Preview](https://example.com/bloxbyte-preview.png)

## Features

- **Sleek, Modern Design**: Dark theme with rounded corners and smooth animations
- **Draggable Interface**: Move the UI anywhere on screen
- **Collapsible Window**: Minimize/maximize to save screen space
- **Toggle Switches**: Animated toggle buttons with callbacks
- **Regular Buttons**: Clickable buttons with hover effects
- **Sections**: Organize your UI with labeled sections
- **Scrolling Support**: For UIs with many elements

## Getting Started

### Installation

Add the BloxByte UI Library to your script by using `loadstring`:

```lua
local BloxByte = loadstring(game:HttpGet("https://raw.githubusercontent.com/uhkai4212/test2/refs/heads/main/1.4"))()
```

### Basic Usage

Create a window and add some UI elements:

```lua
-- Create a new window
local ui = BloxByte.new("My Window")

-- Add a toggle button
local autoFarm = ui:AddToggle("Auto Farm", false, function(state)
    print("Auto Farm is now:", state)
    -- Your code here
end)

-- Add a regular button
ui:AddButton("Click Me", function()
    print("Button clicked!")
    -- Your code here
end)
```

## API Reference

### Creating a Window

```lua
local ui = BloxByte.new(title)
```

- **title** (string): The title displayed at the top of the window
- **Returns**: UI instance

### Adding a Toggle

```lua
local toggle = ui:AddToggle(name, defaultState, callback)
```

- **name** (string): Text displayed next to the toggle
- **defaultState** (boolean): Initial state of the toggle (true = on, false = off)
- **callback** (function): Function called when toggle state changes, receives state as parameter
- **Returns**: Toggle controller with GetState() and SetState() methods

### Adding a Button

```lua
local button = ui:AddButton(name, callback)
```

- **name** (string): Text displayed on the button
- **callback** (function): Function called when button is clicked
- **Returns**: Button instance

### Adding a Section

```lua
local section = ui:AddSection(name)
```

- **name** (string): Text displayed for the section header
- **Returns**: Section label instance

### Controlling Toggles

```lua
-- Set toggle state programmatically
toggle.SetState(true)  -- Turn on
toggle.SetState(false) -- Turn off

-- Get current toggle state
local isOn = toggle.GetState()
```

### Destroying the UI

```lua
ui:Destroy()
```

Removes the UI from the screen completely.

## Advanced Usage

### Complete Example

```lua
local BloxByte = loadstring(game:HttpGet("https://raw.githubusercontent.com/YourUsername/BloxByte/main/BloxByteUI.lua"))()

-- Create a new window with title "My Game GUI"
local ui = BloxByte.new("My Game GUI")

-- Add a section for farm settings
ui:AddSection("Farming")

-- Add toggle buttons with callbacks
local autoFarm = ui:AddToggle("Auto Farm", true, function(state)
    print("Auto Farm is now:", state)
    -- Implement auto farm functionality
end)

local autoSell = ui:AddToggle("Auto Sell", false, function(state)
    print("Auto Sell is now:", state)
    -- Implement auto sell functionality
end)

-- Add a section for visual settings
ui:AddSection("Visual Settings")

local espToggle = ui:AddToggle("ESP", false, function(state)
    print("ESP is now:", state)
    -- Implement ESP functionality
end)

-- Add a button for a one-time action
ui:AddButton("Collect All", function()
    print("Collecting all items...")
    -- Implement collection functionality
end)

-- Control toggle programmatically after 5 seconds
task.wait(5)
autoFarm.SetState(false)
```

### Creating Multiple Windows

You can create multiple UI windows if needed:

```lua
local mainUI = BloxByte.new("Main Menu")
local settingsUI = BloxByte.new("Settings")

-- Add elements to each window
mainUI:AddToggle("Feature 1", false, function() end)
settingsUI:AddToggle("Sound", true, function() end)
```

## Customization

The BloxByte UI uses several color constants defined at the top of the library. You can modify these before loading to change the appearance:

```lua
-- After loading the library:
local BloxByte = loadstring(game:HttpGet("https://raw.githubusercontent.com/YourUsername/BloxByte/main/BloxByteUI.lua"))()

-- Customize colors (modify these to your preference)
BloxByte.TOGGLE_COLOR_ON = Color3.fromRGB(0, 255, 0)  -- Bright Green
BloxByte.TOGGLE_COLOR_OFF = Color3.fromRGB(255, 255, 255)  -- White
BloxByte.BACKGROUND_COLOR = Color3.fromRGB(30, 30, 30)  -- Dark Gray
BloxByte.TEXT_COLOR = Color3.fromRGB(255, 255, 255)  -- White
BloxByte.BUTTON_COLOR = Color3.fromRGB(45, 45, 45)  -- Slightly lighter gray

-- Then create your UI
local ui = BloxByte.new("Custom UI")
```

## Best Practices

1. **Organization**: Use sections to group related toggles and buttons
2. **Naming**: Use clear, concise names for toggles and buttons
3. **Callbacks**: Keep callback functions small and focused
4. **Error Handling**: Wrap callback code in pcall() to prevent script errors
5. **Cleanup**: Call ui:Destroy() when you no longer need the UI

## Troubleshooting

### UI Not Appearing
- Check if the script is running with the right permissions
- Ensure the ScreenGui is properly parented

### Toggles Not Working
- Verify your callback functions don't have errors
- Check if you're using SetState correctly

### UI Position Reset
- Make sure ResetOnSpawn is set to false
- Use a persistent storage solution for position if needed

## Compatibility

BloxByte UI Library is designed to work with modern Roblox clients and supports various exploit environments. The library automatically detects and uses the appropriate methods for different executors.

## Limitations

- Works best on PC/desktop Roblox clients
- May need additional adjustments for mobile devices
- Limited custom styling options in the current version

## Credits

Created by [kureo11 on discord]

## License

This library is provided as-is for personal and educational use.
