---
title: "How to boot Ubuntu"
date: 2009-07-30
forum: General Help
---

### Post by ktechkio on 2009-07-30
I have Kubuntu karmic installed.I want windows bootloader tobe in mbr. I have not had success booting Kubuntu with easybcd. Grub is installed to /dev/sdb5

I know how to restore grub to mbr but I can't because another user of the computer in question doesn't want me to do so. I have made Easy BCD do the trick before but seem to have forgotten how. Selecting the partion and adding in EasyBCD doesn't work (doesn't boot) neither does choosing Grub isn't installed to the boot sector.

---

### Post by DeMus on 2009-07-30
> **ktechkio said:**
> I have Kubuntu karmic installed.I want windows bootloader tobe in mbr. I have not had success booting Kubuntu with easybcd. Grub is installed to /dev/sdb5

I know how to restore grub to mbr but I can't because another user of the computer in question doesn't want me to do so. I have made Easy BCD do the trick before but seem to have forgotten how. Selecting the partion and adding in EasyBCD doesn't work (doesn't boot) neither does choosing Grub isn't installed to the boot sector.

Okay, so the other user doesn't want Grub. How about you do install it, through the menu.lst file in /boot/grub you set the Windows OS as primary choice and the delay to 3 seconds or so.
Whenever (s)he boots, Windows will start after 3 seconds. When you boot, you have 3 seconds to push a key to stop the timer, select the right Ubuntu and boot it.

---

### Post by ktechkio on 2009-07-30
That's not a solution! Windows vista now 7 have issues when Grub is in MBR. Mainly some updates. I need to use Win7 bootloader.

---

### Post by DeMus on 2009-07-30
> **ktechkio said:**
> That's not a solution! Windows vista now 7 have issues when Grub is in MBR. Mainly some updates. I need to use Win7 bootloader.

Is MS really that terrible that it looks in MBR to see if it is the first OS before an update is allowed? And you want to use that OS? Erase it and use your valuable hard disk for something way better and nicer: Ubuntu Linux.

---

### Post by ktechkio on 2009-07-30
Not me Using it. But, I do use it on another pc. Once every month for Gaming.

Ms once released update KB**** for update KB**** (Not Joking):KS

---

