---
title: "Arrange boot"
date: 2010-08-13
forum: General Help
---

### Post by dek8 on 2010-08-13
I have 2 windows 7 installations on 2 different disks, during the installation of ubuntu i marked the wrong one as windows and grub made an option to boot it on the grub load menu.

Is it hard to reassign another windows loader to grub after installation?


the disk i want to use looks like this;

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       21271    15345664   83  Linux
/dev/sda2           21272       67703    33500670+   f  W95 Ext'd (LBA)
/dev/sda5           21272       67703    33500669+   7  HPFS/NTFS

Its a 50gb solid drive, linux on the first partion and windows 7 which i want to use on the second partition.

grub got one instance of windows 7 (loader) on another disk which im not using.

(Before all of this i had XP where linux is now and installed windows 7 after XP for dual booting, then installed linux over XP which im on now)

---

