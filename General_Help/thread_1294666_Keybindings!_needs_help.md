---
title: "Keybindings! needs help"
date: 2009-10-18
forum: General Help
---

### Post by artheus on 2009-10-18
Hi!

I would want to bind specific key-combinations to specific actions/events in Ubuntu. How can I do this?

eg.

Super+E = open Nautilus window, in specific folder
Super+L = lock screen

I've tried to change the shortcut for lock screen to Super+L in the System > Preferences > Keyboard Shortcuts, but it just won't work.

Cheers,
Artheus

---

### Post by VCoolio on 2009-10-18
To make sure you can use the winkey in the keybindings settings window, check System > Preferences > Keyboard > Layouts > Layout options expand "Alt/Win keys behavior" and check "super is mapped to the win-keys"

Now add a keybinding for the command "nautilus /path/to/your/folder" and for lockscreen the command is already there (you can use "gnome-screensaver-command --lock" ).

---

