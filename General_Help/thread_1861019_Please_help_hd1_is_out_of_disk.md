---
title: "Please help: hd1 is out of disk"
date: 2011-10-15
forum: General Help
---

### Post by wizi on 2011-10-15
Hi everyone, 

I am new to Ubuntu. I just bought a new HDD (1T) and installed Ubuntu on there along with Window 7. 

When I start Ubuntu, my computer usually says "hd1 out of disk" but it still allows me log into Ubuntu. Sometimes it takes a long time to boot. Does anyone know how to fix this? Thank you. 


when I type "sudo fdisk -l" in the terminal, I got the following message. 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b96f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      119028   956090368   83  Linux
/dev/sda2          119029      121602    20669441    5  Extended
/dev/sda5          120072      121602    12285952   82  Linux swap / Solaris
/dev/sda6          119550      120072     4191232   82  Linux swap / Solaris
/dev/sda7          119029      119550     4191232   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaa0e45fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       12749   102297600    7  HPFS/NTFS
/dev/sdb3           12749       30402   141796352    7  HPFS/NTFS


If you need more information, please let me know.

---

### Post by oldos2er on 2011-10-15
Why do you have three swap partitions? Can you post the output of **df -h** ?

---

