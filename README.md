Hyprland Workspace HUD (Dunst + Matugen)
A clean, minimalist way to track your active workspaces in Hyprland without using a taskbar (like Waybar or Polybar). This setup uses Dunst to pop up a small, temporary notification whenever you switch workspaces, and Matugen to ensure the notification matches your wallpaper colors.

📺 Video Tutorial
Watch the full setup and demonstration here: Never Get Lost: Custom Hyprland Workspace HUD 🖥️

✨ Features
Minimalist Design: No permanent bars; workspace info only appears when you need it.

Dynamic Theming: Uses Matugen to sync notification colors with your current wallpaper.

Drop-in Configuration: Uses the .d folder structure for clean configuration management.

🛠️ Installation
First, install Dunst using your favorite AUR helper (e.g., yay):

Bash

yay -S dunst
⚙️ Configuration
1. Dunst Setup
Create your local Dunst configuration directory and copy the default config:

Bash

mkdir -p ~/.config/dunst
cp /etc/dunst/dunstrc ~/.config/dunst/dunstrc
2. Workspace HUD Script
In your hyprland.conf, add a bind that triggers a Dunst notification when switching workspaces. For example:

Plaintext

bind = $mainMod, 1, workspace, 1
bind = $mainMod, 1, exec, notify-send -u low -t 1000 "1"
(Repeat for all your workspaces)

3. Matugen Integration (.d folder)
To apply dynamic colors, we use a "drop-in" file in a dunstrc.d folder. This allows Matugen to overwrite specific color settings without touching your main dunstrc.

Create the folder: mkdir -p ~/.config/dunst/dunstrc.d

Matugen Template: Create a template in your Matugen config that generates a file like 99-matugen.conf inside that folder.

The Result: When Dunst starts, it reads the main config and then "drops in" the Matugen colors from the .d directory.

4. Matugen config.toml
Ensure your Matugen configuration includes the Dunst template and a post-processing command to restart Dunst:

Ini, TOML

[[templates]]
input = "path/to/dunst_template.conf"
output = "~/.config/dunst/dunstrc.d/99-matugen.conf"

[post_process]
command = "pkill dunst && dunst &"
🚀 Usage
Simply switch workspaces using your defined keybinds (e.g., Super + 1). A small notification box will appear at your specified location (e.g., top-center) displaying the workspace number in a color scheme matching your wallpaper.

Created by Peter Tech. Like and subscribe if this helped your Hyprland workflow!

Watch Youtube video here
https://youtu.be/xriCJrnciqA
