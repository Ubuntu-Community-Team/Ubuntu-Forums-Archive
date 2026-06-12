---
title: "Partition table trouble after hackint0sh install"
date: 2010-11-27
forum: General Help
---

### Post by thomasfinch on 2010-11-27
Hi, this is my fist post so please be patient with me ;)

I recently installed ideneb 1.3 on my netbook (hp mini 110), and got everything working perfectly. I have a triple boot setup with ubuntu 10.10, windows xp, and ideneb.

However, my partition table was showing up as unallocated in gparted, and I wanted to add a new partition, so I used testdisk to re-write the partition table. 

Bad idea! Now it still shows up as unallocated, but I can't boot into my ideneb install, since the partition isn't recognized anymore. I can still access my ubuntu and windows just fine, but not ideneb. 

Can anyone help me fix my partition table so I can boot OS X?

Here's the output of "sudo fdisk -l":

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00220021

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9659    77585880+   7  HPFS/NTFS
/dev/sda2            9660       16187    52428288   83  Linux
/dev/sda3           16187       16447     2096120   82  Linux swap / Solaris
/dev/sda4           16447       19458    24186057    f  W95 Ext'd (LBA)
/dev/sda5           16447       19458    24179712   af  HFS / HFS+

```

---

