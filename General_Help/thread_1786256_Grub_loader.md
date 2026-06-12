---
title: "Grub loader"
date: 2011-06-19
forum: General Help
---

### Post by tatuncho on 2011-06-19
I use Ubuntu on his edition 8.10 and have always been very pleased, until 11:04 last version. Actually used a dual boot for constant use of certain programs that only work on windows. By installing the latest version, everything is as before except that I can not see the initial grub, show me out of range. My boot loader resolution is 640x480 and still I can not see the grub at startup. Any ideas

---

### Post by Quackers on 2011-06-19
Welcome to UF.
If Ubuntu is booting directly try running ```
sudo update-grub
``` in the terminal and watch to see if the Windows Loader is recognised as grub.cfg is run. If it is, reboot and you should then see a grub menu.

---

