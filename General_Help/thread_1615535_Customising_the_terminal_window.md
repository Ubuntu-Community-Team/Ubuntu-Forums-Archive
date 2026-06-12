---
title: "Customising the terminal window"
date: 2010-11-07
forum: General Help
---

### Post by EchoBeach on 2010-11-07
Hi
Apologies if this in the wrong category - I can't see one to fit it in.
I use PuTTY at work, from my Win XP Pro desktop PC to access a number of Linux servers.
When connected, the PuTTY session allows me to tab-complete file and directory names, and to select text straight into the copy buffer and right-click to paste from the copy buffer.
How can I achieve the same functionality with my Lucid terminal sessions, here at home, please?
Regards
Echo

---

### Post by Brandon Williams on 2010-11-07
Both of those functionalities (tab-complete and highlight+click to copy/paste) should be working by default in a standard lucid installation. The only difference is that X uses middle-click to paste instead of right-click.

If these things don't appear to be working for you, it would be helpful to know which terminal emulator you use when you log in directly to the box.

---

### Post by EchoBeach on 2010-11-08
Thanks for your reply, Brandon.
I'm using the Terminal window to navigate locally - on my machine.  I'm not connecting to any other boxes.
Where do I find the configuration settings for the terminal window?
Echo

---

### Post by Brandon Williams on 2010-11-12
I'm guessing that by "Terminal" you mean gnome-terminal. There should be a menu bar at the top of the window. Select Help -> About to verify this. If there is no menu bar, try using a right-click in the window to get a pop-up menu. The pop-up menu should have an item called "Show Menubar" (or something similar). Both the pop-up menu and the menu bar's Edit menu should have a "Preferences" item that will bring up a configuration dialog.

---

