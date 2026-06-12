---
title: "Can't Find Ubuntu 10.04 Partition"
date: 2011-03-21
forum: General Help
---

### Post by Zirgzar on 2011-03-21
Hey. I've got a problem with my Ubuntu partition- it can't be found.

I installed it awhile back for a class, so I only gave it about 5 gigs. However, I've fallen in love with it and want to expand (or delete and re-install with a lot more room) the partition only to find out that nothing will find it.

I tried Gparted and it showed the two partitions I had already. fdisk -l gives this:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f27bf22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        7308    58605120    7  HPFS/NTFS (where I gave it room)
/dev/sda3            7309       14594    58517976    7  HPFS/NTFS


I'm not sure what happened. I didn't know much about it when I downloaded it and I'm pretty sure the install partitioned it on it's own. Also, in case it matters, I'm dual booting Windows 7 and Ubuntu 10.04. 

If anyone could help me I would greatly appreciate it.

---

### Post by idoitprone on 2011-03-21
wubi install?

---

### Post by garvinrick4 on 2011-03-21
Look in C; drive right next to Users and see if there is an UBuntu folder.
It must be a WUBI install as previous post says.

---

