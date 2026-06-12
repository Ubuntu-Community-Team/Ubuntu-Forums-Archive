---
title: "Ubuntu 9.10 / Windows 7 Dual Boot"
date: 2009-12-07
forum: General Help
---

### Post by themoodude on 2009-12-07
Hi,

Basically I had Windows 7 (x64) installed on hd0,1 (hd0,0 is used by Windows 7 for a hidden "backup" partition). I then installed Ubuntu 9.10 on an extended partition that contained hd0,3-Linux and hd0,4 for swap.

Primarily I found that although GRUB worked in booting both Ubuntu and Windows, the default selection was Linux and it had several items that I didn't want in the boot menu. I couldn't find a way of customizing it as the file "grub.cfg" was both read-only and recreated automatically by the system.

Because of this I restored the BCD bootloader using easy bcd under Windows. The only problem now is that because I originally had GRUB installed (by default during Ubuntu installation) to the main mbr which has now been replaced by the bcd, GRUB is surely no longer installed. Because of this adding NeoGrub / Linux boot to the BCD using Easy BCD doesn't work.

How do I go about recreating a dual boot bootloader? Preferably I would like to use the BCD as it can be edited easily, but if need be i will use GRUB (although advice on removing unused kernels and memtest, and also changing the default would be appreciated).

Please note that from various google searches I have been instructed to edit /boot/grub/menu.lst although this doesn't exist. The same article advised that in that case to edit /boot/grub/grub.cfg, although even when opening it from terminal with sudo I still cannot save the file.

NB: at the moment I can't boot into Linux, but I do have the disc around, so I could easily boot into Live CD. Also I'm not all that clued up on Linux. I know some basics, but please keep any help simple.

Would be greatly appreciated.

Cheers,
Dean

---

### Post by audiomick on 2009-12-07
Hallo Dean.
Getting grub re-installed is, as far as I know, not difficult. It also seems to not be difficult to edit. From a fresh install from 9.10, you will have (had...) grub2, not grub.

Have look through these:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by themoodude on 2009-12-07
The first link there was incredibly helpful in restoring / reinstalling the grub bootloader; which I have now upgraded to Grub2 (1.97 beta), thank you for that. Now to read on and attempt to remove unused kernels / memtest from the menu, and to rename and change defaults.

Thank you for your help so far. Do you perhaps know of any GUI-based Grub2 configuration apps?

---

### Post by themoodude on 2009-12-07
Right so I've used Synaptic to remove the unrequired kernels, and after updating grub they no longer appear. I've also managed to remove the memtest; all good good. I've used SUM to change the default to Windows. My only query now is how can I rename the current menu items?

---

### Post by pqwoerituytrueiwoq on 2009-12-07
```
sudo gedit /boot/grub/grub.cfg
```
note file was not meant to be edited but just editing a tile will not mess anything up that i know of

---

### Post by themoodude on 2009-12-08
From my experience grub.cfg can't be edited without actually logging in as root. Even if you run a text editor with sudo it will still not save. Also; it's automatically overwritten whenever update-grub is run.

---

### Post by themoodude on 2009-12-15
OK I pretty much figured out how editing each file and updating grub2 can sort it and make it very customizable. Cheers for the help!

---

