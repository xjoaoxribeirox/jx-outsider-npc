# NPC Management and Trading System

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Configuration Example](#configuration-example)
- [Usage](#usage)
- [Troubleshooting](#troubleshooting)
- [Version](#version)
- [License](#license)

## Overview
📖 This script, built for the [RSG Framework](https://github.com/Rexshack-RedM), enables **RedM servers** to manage **Non-Playable Characters (NPCs)** for *travel* and *illegal activities*, alongside robust item trading mechanics. It’s perfect for **roleplay servers**, offering immersive interactions and a dynamic economy driven by a unique "blood money" system.

## Features
- 🚀 **NPC Spawning**: Generates two types of NPCs:
  - **Travel NPCs**: Facilitate mechanics like teleportation or missions.
  - **Illegal NPCs**: Engage in illicit activities, such as item trading or handling "blood money."
- 🔄 **Automatic NPC Reset**: Optionally repositions NPCs at set intervals to keep gameplay fresh.
- 💰 **Item Trading**: Players can sell predefined items to illegal NPCs for profit.
- 🩸 **Blood Money System**: Requires "blood money" (a special currency earned through server-specific activities) for travel interactions.
- 🌐 **Localization**: Supports Portuguese (`pt`) and English (`en`).

## Prerequisites
Before installing, ensure you have:
- A **RedM server** running the [RSG Framework](https://github.com/Rexshack-RedM).
- [Ox Lib](https://github.com/overextended/ox_lib) (version 2.0 or higher).
- [RSG Target](https://github.com/Rexshack-RedM/rsg-target) (version 1.0 or higher).
- Basic knowledge of server configuration and Lua scripting.
- (Optional) A compatible economy system for "blood money" integration.

  ## Installation
🛠️ New to RedM? Follow these simple steps to get the script running:
1. Download the script and extract it to your server’s `resources` folder (e.g., `server-data/resources/`).
2. Open `config.lua` and adjust settings as needed (see [Configuration](#configuration)).
3. Add the script to your `server.cfg` by including: `ensure jx-outsider-npc`.
4. Restart your server or reload resources using `refresh` followed by `start jx-outsider-npc` in the server console.

## Configuration
📋 The script is configured via the `Config` table in `config.lua`. Below are the key settings:

### System Configuration
- **Locale**: Sets the language (`pt` for Portuguese, `en` for English).
- **EnableAutoReset**: Enables/disables automatic NPC repositioning (`true`/`false`, default: `false`).
- **ResetInterval**: Interval for NPC reset in milliseconds (default: 60 minutes = `60 * 60000` ms).
- **RequiredBloodMoney**: Amount of "blood money" needed for travel (default: `50`).
- **NPCQuantity**:
  - `Travel`: Number of travel NPCs to spawn (default: `1`).
  - `Illegal`: Number of illegal NPCs to spawn (default: `4`).

### Illegal NPCs
- **coordsIllegalNPC**: List of spawn coordinates (e.g., New Hanover, Annesburg, Saint Denis).
- **ModelIllegalNPC**: Available models (e.g., `g_m_m_unimountainmen_01`, `a_m_m_asbminer_01`).

### Travel NPCs
- **coordsTravelNPC**: List of spawn coordinates (e.g., BlackWater, Rhodes, Swamp).
- **ModelTravelNPC**: Available models (e.g., `cs_exconfedsleader_01`, `u_m_o_oldcajun_01`).

### Purchasable Items
Items players can sell to illegal NPCs:
- `cacos_vidro`: $1/unit
- `brinco_rubi`, `brinco_circular`: $2/unit
- `colar`, `anel_rose`: $3/unit
- `anel_azulado`, `anel_comum`: $4/unit
- `paper`: $1/unit
- `sucata`: $3/unit

### Blood Money System
💰 "Blood money" is a special currency used for travel interactions with NPCs. It’s typically earned through illegal activities or server-specific mechanics. Adjust `RequiredBloodMoney` to control the cost of travel.

## Configuration Example
💡 Here’s a sample configuration for `config.lua`:

```lua
Config = {}
Config.Locale = 'en' -- Set language to English
Config.EnableAutoReset = true -- Enable automatic NPC repositioning
Config.ResetInterval = 30 * 60000 -- Reset every 30 minutes
Config.RequiredBloodMoney = 100 -- Require 100 blood money for travel
Config.NPCQuantity = {
    Travel = 2, -- Spawn 2 travel NPCs
    Illegal = 6 -- Spawn 6 illegal NPCs
}
Config.coordsIllegalNPC = {
    vector4(579.37, 1673.29, 187.79, 132.38), -- New Hanover
    vector4(2966.17, 1434.53, 44.73, 217.86), -- Annesburg
    vector4(2930.72, 1268.30, 44.66, 330.87), -- Annesburg Station
}
Config.ModelIllegalNPC = {
    "g_m_m_unimountainmen_01",
    "a_m_m_asbminer_04",
    "a_m_m_asbminer_01",
}
Config.coordsTravelNPC = {
    vector4(-715.78, -1305.91, 41.42, 217.04), -- BlackWater
    vector4(794.33, -1246.84, 45.83, 27.86),   -- Rhodes
    vector4(2167.32, -623.82, 42.85, 318.14),  -- Swamp
}
Config.ModelTravelNPC = {
    "cs_exconfedsleader_01",
    "cs_mp_oldman_jones",
    "u_m_o_oldcajun_01"
}
Config.PurchasableItems = {
    ['cacos_vidro'] = 1,      -- $1 per unity
    ['brinco_rubi'] = 2,      -- $2 per unity
    ['brinco_circular'] = 2,  -- $2 per unity
?

```

## Usage
🎮 **In-Game**:
- Interact with **Travel NPCs** to perform travel-related actions (requires "blood money").
- Sell items listed in `PurchasableItems` to **Illegal NPCs** for profit.
- NPCs will reposition automatically if `EnableAutoReset` is enabled, preventing repetitive farming.

**Customization**:
- Edit `config.lua` to tweak NPC spawn locations, quantities, item prices, or blood money requirements.
- Enable `EnableAutoReset` for dynamic gameplay or adjust `ResetInterval` for frequency.

## Troubleshooting
🛠️ Common issues and solutions:
- **NPCs not spawning**: Ensure coordinates in `coordsIllegalNPC` and `coordsTravelNPC` are valid and not obstructed. Verify that dependencies are installed.
- **Error loading script**: Check if `Ox Lib` and `RSG Target` are up-to-date and properly configured in `server.cfg`.
- **Blood money not working**: Confirm that your server has a compatible economy system integrated with the script.
- **Localization issues**: Ensure `Locale` is set to a supported language (`pt` or `en`).

## Version
Current version: **v1.0.0** (Released April 2025)

### Changelog
- **v1.0.0**: Initial release with NPC spawning, item trading, and blood money mechanics.

## License
⚖️ This script is provided as-is for use in RedM servers. Modify and distribute as needed, but ensure compliance with your server’s licensing terms.
