---
title: "Dual boot with xp."
date: 2010-06-07
forum: General Help
---

### Post by Mudsplash on 2010-06-07
I want to install Ubuntu 10.04 on a second HDD than my windows xp installation. The second drive is on the same ide ribbon as the primary HDD (xp) and is set to slave. When i installed ubuntu on the second HDD it corrupted my primary drives MBR. It was an easy fix but every attempt i make ends in the same result. I also have another HDD that is sata and the sata controller is a via pci expansion card. Installation of ubuntu to this drive as well also corrupts my primary HDD MBR. But when I install to the same HDD the dual boot works fine.

I was thinking of unplugging the power cable from the primary HDD, then installing ubuntu to one of the separate HDDs. Would i still be able to dual boot. And which drive would be optimal for a dual boot installation in this configuration.

---

### Post by xoomer.ap on 2010-06-07
Try configuring GRUB.
- unplug drive with XP and correct MBR.
- install Ubuntu to other drive.
- add to GRUB configuration file* rows like this:
```
     title Windows XP
     root (hdx,y)
     chainloader +1
```
probably, if you connect drive with WinXP to primary slave, second string will be: "root (hd1,0)"
* -I'm not exactly know where is GRUB conf. file in Ubuntu, because now I'm boot up openSUSE Linux - in this OS that file is there: /boot/grub/menu.lst

Note, I'm not 100% sure in my words, make that things at your own risk. I just write how I would be do. :)

Respectfully, xoomer.ap.

---

### Post by oldfred on 2010-06-07
Computers with IDE and MBR boot to the primary master. If you want to boot Ubuntu you have to install grub to the primary master drive. Not sure if your BIOS is new enough to choose boot drives. Newer BIOS with SATA allow you to choose boot drive (mine still calls it primary master) even when you have more than the four allowed with IDE.


What was the issue you had with grub. It works for most.

---

