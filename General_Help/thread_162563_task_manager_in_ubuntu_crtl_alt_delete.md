---
title: "task manager in ubuntu? crtl alt delete"
date: 2006-04-19
forum: General Help
---

### Post by cosmoshell on 2006-04-19
is there an easy way to accsess task manager in ubuntu and how do you install it cus i got rid of it a wile back.

---

### Post by Ramses de Norre on 2006-04-19
sudo apt-get install gnome-system-monitor
It should be in applications > system tools (if not: killall gnome-panel)
To acces it through alt+ctrl+del: gconf-editor /apps/metacity: define a keybinding in global_keybindings (<Control><Alt>Delete) and define a command for it in keybinding_commands (gnome-system-monitor &)

---

### Post by cosmoshell on 2006-04-19
[QUOTE=Ramses de Norre]sudo apt-get install gnome-system-monitor
It should be in applications > system tools (if not: killall gnome-panel)
To acces it through alt+ctrl+del: gconf-editor /apps/metacity: define a keybinding in global_keybindings (<Control><Alt>Delete) and define a command for it in keybinding_commands (gnome-system-monitor &)[/QUOTE]

cool thanks

---

### Post by antiemptyv on 2006-04-20
you can also run "top" from a terminal

---

