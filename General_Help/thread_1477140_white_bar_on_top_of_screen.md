---
title: "white bar on top of screen"
date: 2010-05-08
forum: General Help
---

### Post by BelgianCubbie on 2010-05-08
After logging in, all I get is the purple background with a white bar sitting on top of the screen (where the top panel) should be.
Any idea how and why, and most importantly, how to get rid of it and get Ubuntu back in working order

---

### Post by dino99 on 2010-05-08
if you can open a console: (ctrl+alt+F2)

sudo dpkg --configure -a
sudo dpkg-reconfigure plymouth
sudo apt-get install -f

if you cant , reboot into recovery mode, edit the boot line and remove "splash" then boot.
If you dont see grub menu, at the end of bios process, hold "shift" key down

---

### Post by BelgianCubbie on 2010-05-08
did it all, no avail....
still the same screen

---

