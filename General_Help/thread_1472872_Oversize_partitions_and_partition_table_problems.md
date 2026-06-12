---
title: "Oversize partitions and partition table problems"
date: 2010-05-04
forum: General Help
---

### Post by wstrinz on 2010-05-04
Hello helpful ubuntu friends,

I decided a few days ago it was time to reinstall ubuntu since Lucid looked fun and interesting. Everything went really well (my table functions even worked with no configuration!) until I decided I wanted to resize my linux partition so I could install a win 7 virtual machine. I had some issues getting gparted to let me expand my partitions into free space, so I started dinking around with various settings commands, and I managed to screw up my partition table badly enough that I needed to boot with the live cd.

After a few hours in panicked trouble shooting mode, I finally got grub reinstalled and managed to boot things regularly. But now Gparted is completely nonfunctional; it shows the entire HD as unallocated and says "can't have partition outside of disk". Apparently one of my partitions is oversized. I read [this thread]("http://ubuntuforums.org/showthread.php?t=1038943"), which makes me think this should be simple to fix, but I don't what numbers to put into the command that was posted.

Any help from someone more experienced would be greatly appreciated.

Here's my output of fdisk -lu and sfdisk -d:

sudo fdisk -lu
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c5ef856

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    23406704    11703321    7  HPFS/NTFS
/dev/sda2        23406705   317271408   146932352    7  HPFS/NTFS
/dev/sda3       317283750   351727109    17221680   83  Linux
/dev/sda4       351727110   488407125    68340008    f  W95 Ext'd (LBA)
/dev/sda5       351731712   382052351    15160320   83  Linux
/dev/sda6       383477760   484116471    50319356    7  HPFS/NTFS

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders, total 1984000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             249     1983743      991747+   6  FAT16

```

sudo sfdisk -d
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 23406642, Id= 7, bootable
/dev/sda2 : start= 23406705, size=293864704, Id= 7
/dev/sda3 : start=317283750, size= 34443360, Id=83
/dev/sda4 : start=351727110, size=136680016, Id= f
/dev/sda5 : start=351731712, size= 30320640, Id=83
/dev/sda6 : start=383477760, size=100638712, Id= 7
# partition table of /dev/mmcblk0
unit: sectors

/dev/mmcblk0p1 : start=      249, size=  1983495, Id= 6
/dev/mmcblk0p2 : start=        0, size=        0, Id= 0
/dev/mmcblk0p3 : start=        0, size=        0, Id= 0
/dev/mmcblk0p4 : start=        0, size=        0, Id= 0

```

Thanks a lot!

---

### Post by srs5694 on 2010-05-04
Your extended partition is too big. Here's a modified file you can feed back into sfdisk to fix things:

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 23406642, Id= 7, bootable
/dev/sda2 : start= 23406705, size=293864704, Id= 7
/dev/sda3 : start=317283750, size= 34443360, Id=83
/dev/sda4 : start=351727110, size=136670058, Id= f
/dev/sda5 : start=351731712, size= 30320640, Id=83
/dev/sda6 : start=383477760, size=100638712, Id= 7

```

I've only changed the "size" entry for /dev/sda4; everything else is identical to the /dev/sda output you've provided. To use this, cut-and-past it into a text file (say, sda-parts.txt) and then pass it to sfdisk:

```

sudo sfdisk /dev/sda < sda-parts.txt

```

It's possible that sfdisk will complain that it doesn't like the partitions. If so, double-check the numbers and then add the "--force" option between "sfdisk" and "/dev/sda".

---

### Post by wstrinz on 2010-05-06
Thanks! Looks like that fixed it, gparted now functions properly. Still not sure how my windows partition and my linux one got placed under the same extended partition, but at least I can resize them now.

---

### Post by srs5694 on 2010-05-06
There's absolutely nothing wrong with having two (or more!) OSes share an extended partition. In fact, most sources say that a disk should not have more than one extended partition (although nothing about the data structures themselves prevents it), and most partitioning tools refuse to create a disk with more than one extended partition. Between these facts, limitations on the number of primary partitions, and the needs for number of partitions in some installations, it's often necessary to have logical partitions used by different OSes in a single extended partition.

The biggest non-optimal aspect of your configuration is that /dev/sda6, presumably a Windows partition, lies at the end of the disk, with your Linux partitions between it and the other Windows partitions. This means that head seeks will take longer to complete when Windows accesses /dev/sda6 than they would if /dev/sda6 were placed closer to the other Windows partitions, thus degrading performance. IMHO, it's not worth the effort or risk to juggle your partitions around to improve this, but you might keep it in mind for future installations: Try to keep all the partitions for a given OS contiguous on a disk. Shared partitions should go between the partitions used by the two shared OSes. (If you've got three or more OSes that share a single partition, this last rule may be impossible to satisfy for all OSes, of course.)

---

