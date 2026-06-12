---
title: "If I have to format the WXP partition, will I loose Ubuntu?"
date: 2010-03-26
forum: General Help
---

### Post by rva1945 on 2010-03-26
I have the disk partitioned, Windows XP and Ubuntu.

In Ubuntu the audio works fine, so no hardware problems here.

Some time ago I started to have big troubles with the audio drivers in Windows XP, no way, WXP detects the audio hardware (onboard Intel AC97) but it doesn't install the drivers, no matter where I download them from or whateter I do. It started not immediately after installing Ubuntu, so I guess it doesn't have anything to do with it.

Chances are I'll have to reinstall Windows. The question is: if I have to format the WXP partition, once I boot in DOS mode, what will FORMAT C: do? Will it simply work on the 50GB partition leaving the Ubuntu 25GB untouched?

How will I skip the Ubuntu boot manager?

Thanks

---

### Post by Anderson Brasil on 2010-03-26
If I recall correctly, windows xp overwrite the MBR after an installation, so you will lose your grub (and therefore your ability to log into your ubuntu instalation). But your files you will still be there, untouched, all you need to do is to redo the grub config. I can't help you with that, as I am not very familiar with grub (I was once in a similar situation, but using lilo instead of grub). You will probably need to research it a little more. But I can assure you that there are ways to recover your ubuntu instalation after windows xp overwrites MBR. 

Cheers,

Anderson Brasil.

---

### Post by john newbuntu on 2010-03-27
Format C: will only clear the data in "C" partition of your disk(Windows).

Yes, as Anderson mentioned, re-installation of XP (if required) will overwrite the MBR and therefore you will lose that part of GRUB information (presuming you have loaded GRUB in the MBR).  Do you think just repairing your WinXP using the recovery console will fix your problem?

Also, as Anderson mentioned, your Ubuntu data will still be safe after formatting your windows partition. You can always use the Ubuntu liveCD to re-install GRUB to the MBR.  

Alternatively, you could backup the current relevant sections of MBR using the "dd" command to a backup file
```
dd if=/dev/sda of=/home/john/boot.mbr bs=446 count=1
```
and restore it once your WinXP installation is complete. (After booting from liveCD and mounting your partition)
```
dd if=/home/john/boot.mbr of=/dev/sda bs=446 count=1
```

 Just to be safe, always backup your Ubuntu data (especially home directories) and the list of installed software.

---

