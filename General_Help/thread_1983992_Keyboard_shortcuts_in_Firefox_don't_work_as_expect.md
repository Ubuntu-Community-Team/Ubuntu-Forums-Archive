---
title: "Keyboard shortcuts in Firefox don't work as expected"
date: 2012-05-21
forum: General Help
---

### Post by blazemore on 2012-05-21
Previously, on Ubuntu and other systems, the following shortcuts in Firefox would work:

[LIST]
[*]Ctrl + Tab - Switches between tabs
[*]Ctrl + F4   - Closes current tab
[/LIST]
Since installing the Mate desktop (Gnome 2), the shortcuts do the following:

[LIST]
[*]Ctrl + Tab - Does nothing
[*]Ctrl + F4   - Closes Firefox
[/LIST]
I've checked in the "Keyboard Shortcuts" section in Mate, but neither of these are being overridden. Compiz isn't installed.


This is rather annoying.

---

### Post by blazemore on 2012-05-21
****SOLVED:**** The Firefox extension "FoxTab 1.4.5" was responsible for breaking these shortcuts. Disabling it restores the desired functionality.

---

