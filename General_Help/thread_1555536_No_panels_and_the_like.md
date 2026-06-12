---
title: "No panels and the like"
date: 2010-08-18
forum: General Help
---

### Post by FallenUnia on 2010-08-18
Hello all,

I've just done a fresh install of Ubuntu 10.04 x86_64 on my laptop (Acer Aspire 5740G). Afterwards I let it update and install the correct video driver; everything worked. When this all was done, I edited the menus. (right click and then edit menus or something)

But when I booted up this morning, I only get to see my wallpaper and a shortcut to my usb, which is plugged in. I get no panels; so no menu, no system tray or whatsoever. I do however, can right click my desktop. I then made a new launcher for Firefox and this is how I got here. 

Is there someway I can reset the menus? Thanks in advance

---

### Post by Smart Viking on 2010-08-18
You can make a launcher just like you made the firefox launcher, but with this command:

```
gnome-panel
```
:)

---

### Post by FallenUnia on 2010-08-18
Yes, but I guess they still won't show upon boot. I've just reset the menus using the same menu editor I used to edit them, I'll reboot now to see whether this helped.

---

### Post by FallenUnia on 2010-08-18
Nope, they do not show up on reboot. How to fix this?

---

### Post by FallenUnia on 2010-08-18
Anyone? Guess I'll do a fresh install then

---

### Post by Zorgoth on 2010-08-18
You don't need a fresh install!

a) if you create a new user, they should not have this problem

b) if all else fails, you can put gnome-panel --replace in "System > Preferences > Startup Applications"

---

### Post by FallenUnia on 2010-08-18
Thanks, that did the trick. Solved

---

