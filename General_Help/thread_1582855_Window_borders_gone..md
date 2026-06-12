---
title: "Window borders gone."
date: 2010-09-27
forum: General Help
---

### Post by dvlchd3 on 2010-09-27
I'm not sure what happened here, but recently everytime I log into Ubuntu and open a window (of any kind), the border is gone.  There is no close, minimize, maximize buttons, the window is placed over top the menus (upper-left corner) and cannot be moved.  Also, none of the windows are listed in the bottom panel.

If I go into Appearance preferences, and change the visual effects back to "Extra", everything goes back to normal.  However, this change does not appear to remain consistent through a restart. (It is always set at "None" when I log in).

Another random setting that occasionally seems to change itself is the accessibility feature that forces the number pad to control the mouse.  (This has been happening since the install of 10.04)

I have absolutely no idea how to even begin to troubleshoot either of these items.  Any help is greatly appreciated!

---

### Post by VCoolio on 2010-09-27
For the first, a workaround may be to install fusion-icon and add that to startup applications. It's a systray icon. When rightclicked, it will give the option to choose window manager (in this case, compiz) and window decorator. It should remember that for the next login.
For the numpad-mouse conversion: the keybinding for that is ctrl+shift+numlock to toggle on/off. Maybe there is an accessability thing in startup apps; remove it from there if you don't need it and see if it solves anything.

---

### Post by dvlchd3 on 2010-09-27
Thank you for your quick reply.  fusion-icon works, although I'm still curious as to why the Ubuntu setting doesn't remain consistent...

---

### Post by J&#7885;hn on 2010-09-27
I had this when upgrading to Lucid from Karmic. The only way I could get it consistent was to add 

/usr/bin/compiz 

to startup applications.

---

