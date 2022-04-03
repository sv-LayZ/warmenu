<h1 align='center'>Fork By sv-LayZ</a></h1>

# WarMenu
Inspired by [Dear ImGui](https://github.com/ocornut/imgui) and GTA V menu system

## How to Install
1. Place it to `/resources` folder
2. Add `ensure warmenu` to your `server.cfg`
3. Add `client_script '@warmenu/warmenu.lua'` to your `fxmanifest.lua`


## Features
* Backward compatibility
* GTA V-like look'n'feel
* Rich menu style customization
* Lots of built-in controls
* Demo menu

## Demo menu
You can read its source code to understand how framework works   
To run it, just add `client_script @warmenu/warmenu_demo.lua` to any of your resources which are using WarMenu

## API
```lua
--- add this to the top of your resources
local WarMenu = exports['warmenu']

--- * - optional parameters
WarMenu:CreateMenu(id, title, subTitle*, style*)
WarMenu:CreateSubMenu(id, parent, subTitle*, style*)

WarMenu:CurrentMenu() -- id

WarMenu:OpenMenu(id)
WarMenu:Begin(id)
WarMenu:IsAnyMenuOpened()
WarMenu:CloseMenu()

-- Controls
WarMenu:Button(text, subText*)
WarMenu:InputButton(text, windowTitleEntry*, defaultText*, maxLength*, subText*)
WarMenu:SpriteButton(text, dict, name, r*, g*, b*, a*)
WarMenu:MenuButton(text, id, subText*)
WarMenu:CheckBox(text, checked)
WarMenu:ComboBox(text, items, currentIndex)
WarMenu:ToolTip(text, width*, flipHorizontal*)
-- Use them in loop to draw
-- They return true if were selected OR you can use functions below for more granual control
WarMenu:IsItemHovered()
WarMenu:IsItemSelected()
-- See Usage section for more details

WarMenu:End() -- Processing key events and menu logic, use it in loop


-- Customizable options
--- Menu
WarMenu:SetMenuTitle(id, title)
WarMenu:SetMenuSubTitle(id, text) -- it will uppercase automatically

--- Style
--- Property name can be extracted from setter signature, i. e. 'SetMenuTitleColor' -> 'titleColor'
--- Example: local style = { titleColor = { 255, 255, 255 }, maxOptionCountOnScreen = 7, buttonPressedSound = { name = 'name', set = 'set' } }
WarMenu:SetMenuStyle(id, style)

WarMenu:SetMenuX(id, x) -- [0.0..1.0] top left corner
WarMenu:SetMenuY(id, y) -- [0.0..1.0] top
WarMenu:SetMenuWidth(id, width) -- [0.0..1.0]
WarMenu:SetMenuMaxOptionCountOnScreen(id, count) -- 10 by default

WarMenu:SetMenuTitleColor(id, r, g, b, a*)
WarMenu:SetMenuSubTitleColor(id, r, g, b, a*)

WarMenu:SetMenuTitleBackgroundColor(id, r, g, b, a*)
-- or
WarMenu:SetMenuTitleBackgroundSprite(id, dict, name)

WarMenu:SetMenuBackgroundColor(id, r, g, b, a*)
WarMenu:SetMenuTextColor(id, r, g, b, a*)
WarMenu:SetMenuSubTextColor(id, r, g, b, a*)
WarMenu:SetMenuFocusColor(id, r, g, b, a*)
WarMenu:SetMenuFocusTextColor(id, r, g, b, a*)
WarMenu:SetMenuButtonPressedSound(id, name, set) -- https://pastebin.com/0neZdsZ5
```


## Changelog
### 1.6
* Changing all functions for exports
* Delete deprecated functions
