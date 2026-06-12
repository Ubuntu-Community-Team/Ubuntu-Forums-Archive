---
title: "partition dev  ext removal disk"
date: 2009-08-23
forum: General Help
---

### Post by hockeyshifter on 2009-08-23
i need to know how to identifiy what is on a peticular partition or dev 

i have run out of disk space and need to delete a dev/sda. 
i am using 9.04. i had a failed upgrade from 8.10 (do like the update though)so i did a livecd upgrade.
i did let linux install were it thought would be the best. 

here is the fdisk -l output shell

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00044d70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1033     8289540   83  Linux
/dev/sda2            1034        2432    11237467+   5  Extended
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris
/dev/sda6            1034        1197     1317267   83  Linux
/dev/sda7            2265        2325      489951   82  Linux swap / Solaris
/dev/sda8            1198        2212     8152956   83  Linux
/dev/sda9            2213        2264      417658+  82  Linux swap / Solaris

---

### Post by VMC on 2009-08-23
For starters you can delete two of the three swap partitions. You only need one. It would be nice to see the output of "/boot/grub/menu.lst" . but since you don't know which one, then on boot try to id the UUID strings. Then issue a "sudo blkid" and you can relate that info to the boot menu.

If you can boot up using one of your linux then issue df, that will tell you which one you just booted from.

---

