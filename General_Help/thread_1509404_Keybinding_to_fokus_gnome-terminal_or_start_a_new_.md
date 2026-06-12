---
title: "Keybinding to fokus gnome-terminal or start a new one."
date: 2010-06-14
forum: General Help
---

### Post by t.rei on 2010-06-14
Hi

I was just wondering if this was possible without using guake or yakuake or the like:

I have a shortcut  (alt+shift+c) to open a gnome-terminal window. (done via compiz keyboard commands)

However, what if I wanted it to fokus a gnome-terminal (specific?) if one(it) exists and only start a new terminal, if it isn't already running?

I looked up and down the compiz settings, not seeing anything to help me focus a specific window. :(

Thanks for help.

Timo

---

### Post by Zorgoth on 2010-08-11
<reanimate>
Braaaaaaaaaaaaaaains...
</reanimate>

Use the command wmctrl -l, and learn about parsing the output with bash.  wmctrl also has a command to raise and focus a window.

Then write a script and post it for others to use :)

---

