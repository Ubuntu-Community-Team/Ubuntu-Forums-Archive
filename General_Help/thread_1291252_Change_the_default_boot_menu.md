---
title: "Change the default boot menu"
date: 2009-10-14
forum: General Help
---

### Post by praveenthivari on 2009-10-14
I hv dual booted win7 and ubuntu. Grub has taken up the dual boot options and ubuntu loads as default.
But my system is used by others and they prefer using windows as default.
So, how do I change the default OS now?

---

### Post by jeremyswalker on 2009-10-14
Probably the easiest way is to install the package "startupmanager". Open a terminal (Applications > Accessories > Terminal). Enter the following:
```
sudo aptitude install startupmanager
```
The program should then be located at System > Administration > Startup Manager.

Alternatively, you could edit the file "/boot/grub/menu.lst". You will want to be editing the line "default 0". You would replace "0" with the number of the Windows entry in the boot menu (start counting at 0).

---

### Post by praveenthivari on 2009-10-15
Thanks

---

