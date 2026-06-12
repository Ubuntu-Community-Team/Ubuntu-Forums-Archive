---
title: "Beginner. Cannot boot into XP, comes back t GRUB menu."
date: 2012-05-16
forum: General Help
---

### Post by moxin on 2012-05-16
I installed Ubuntu after windows XP. i manually made partitions for Ubuntu. and installed grub in the windows partition cause it was the 'active partition'. As it boots Windows when i install the grub in any other partition.
Ubuntu boots successfully and Grub has the entry for XP. But when i select it, it comes back to grub menu.
Please help.

BTW here is my fdisk info. the NTFS partitions are mountable.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee790441

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51196319    25598128+   7  HPFS/NTFS/exFAT
/dev/sda2        51196381   156280319    52541969+   f  W95 Ext'd (LBA)
/dev/sda5        51196383    78012789    13408203+  83  Linux
/dev/sda6        81920223   156280319    37180048+   7  HPFS/NTFS/exFAT
/dev/sda7        78014464    81915903     1950720   82  Linux swap / Solaris
```

---

