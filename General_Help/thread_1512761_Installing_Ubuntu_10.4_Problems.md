---
title: "Installing Ubuntu 10.4 Problems"
date: 2010-06-18
forum: General Help
---

### Post by TommyfoarRoshie on 2010-06-18
I have made a bootable pen drive (2gb) and have a 30gb partition on my hard drive for unbuntu

Im trying to try the OS by USB at the start into The BIOS If ya gets what i mean
It successfully loads The Options menu where you pick a choice like run from usb

So i run from usb and and it Loads Ubuntu just the purple background and the beans underneath it loading forever

in the Logs this comes up

/init:line7:cant open /dev/sr0 :No medium

It will keep going like that anyone know whats wrong?

Im using Windows 7 Build 7100*
with a computer i built a year ago
Intel e8400,6gb Ram, Asus P5Q SE Pro,and 100gb left on hard drive (30 Excluding cause i partitioned it =P)

em how do i remove the Floppy drive out of BIOS? i have it at the boot up priority at the last 1st is my hard drive then USB then CD Drive

---

### Post by irv on 2010-06-18
> **TommyfoarRoshie said:**
> I have made a bootable pen drive (2gb) and have a 30gb partition on my hard drive for unbuntu

Im trying to try the OS by USB at the start into The BIOS If ya gets what i mean
It successfully loads The Options menu where you pick a choice like run from usb

So i run from usb and and it Loads Ubuntu just the purple background and the beans underneath it loading forever

in the Logs this comes up

/init:line7:cant open /dev/sr0 :No medium

It will keep going like that anyone know whats wrong?

Im using Windows 7 Build 7100*
with a computer i built a year ago
Intel e8400,6gb Ram, Asus P5Q SE Pro,and 100gb left on hard drive (30 Excluding cause i partitioned it =P)

em how do i remove the Floppy drive out of BIOS? i have it at the boot up priority at the last 1st is my hard drive then USB then CD Drive

To boot from the USB first, set it first in your BIOS. Next set the CD and then the HD. This way it will check your USB, CD then HD for boot media. Next when your boot starts from the USB you can hit the F6 key to get some more boot options. You might have to try some to see if you can get it to boot into the Live OS on the USB. If you can then check to make sure you Internet is connected etc. If it all look good then you can do the install. If you want to run a dual boot with windows then select run side by side. I never set my partitions up before hand. I just let the install do it for me. If you know what you are doing then you can manually install wherever you want.

---

### Post by TommyfoarRoshie on 2010-06-18
hehe got on i used unetbootin to boot up instead

well i got these error's
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet"
All associated with gnome panel and when i put down firefiox it will dissapear i cant find it anywhere..

what should i do? (sorry im a first time ubuntu user)

---

### Post by irv on 2010-06-18
If you are talking about minimizing Firefox. Right mouse click on the panel and add "Windows list" and that should fix this.
See screen shot:
[ATTACH]160870[/ATTACH]

---

