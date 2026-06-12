---
title: "&quot;Alt&quot; key combos broken since 9.10 upgrade"
date: 2009-12-01
forum: General Help
---

### Post by FrostDust on 2009-12-01
The title pretty much explains the problem. I upgraded to 9.10 through the Update Manager, rebooted, and any commands involving the "Alt" key doesn't work. Most obviously, Alt+Tab doesn't work for switching between windows. Alt+F2 for the program-launcher thingy, Alt+Ctrl+[Left/Right] for switching desktops, and so on, also don't work.

It's not just modifier keys in general. Shift works for capitalizing stuff, and Ctrl works, since I can Ctrl+tab between web browser tabs.

Interestingly enough, the Alt key is still detected by Ubuntu. I can go into the Keyboard Shortcuts preferences and assign new keyboard shortcuts. If I assign a key combo involving Alt, it will register as "Alt+[button]". It seems like the button isn't broken, there's just something wrong with whatever translates the button presses into commands.

Please help, my only other options seem to be reinstalling 8.04 and never upgrading, or switching to another distro altogether.

---

### Post by FrostDust on 2009-12-08
I finally figured out the problem.

It turns out I had Compiz installed, and I had not enabled these button combinations in the respective categories (Gnome Compatibility, for example).

---

