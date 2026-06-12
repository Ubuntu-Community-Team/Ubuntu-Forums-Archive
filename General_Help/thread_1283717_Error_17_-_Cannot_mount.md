---
title: "Error 17 - Cannot mount"
date: 2009-10-05
forum: General Help
---

### Post by Mowk on 2009-10-05
Hey, when i get into grub and hit ubuntu im getting an error 17.. Im booting from a USB stick and im not sure what to change the (hd0,0) thing to.. 
here is my sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ff80c2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1561    12538701    7  HPFS/NTFS
/dev/sda2   *        1562       30402   231657472    7  HPFS/NTFS

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         459     3686886   83  Linux
/dev/sdb2             460         487      224910    5  yExtended
/dev/sdb5             460         487      224878+  82  Linux swap / Solaris

any ideas? Thanks a lot.

---

### Post by utnubuuser on 2009-10-06
You'll want to set up grub on (sdb). Just google "reinstall grub from liveCD ubuntu"

Be careful not to mess up the MBR on your HDD though.  You might even want to disconnect the HDD while you do it (if possible).

I'm kinda guessing you've got another install of ubuntu on the hdd?
You can also select your boot device by pressing F12 at boot.(this only works if it's enabled BIOS), and on some machines it's F8 or F10 or even a combination of buttons.  Check in your BIOS setup.

---

