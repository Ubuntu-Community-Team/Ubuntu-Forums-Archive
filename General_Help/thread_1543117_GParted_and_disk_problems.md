---
title: "GParted and disk problems"
date: 2010-07-31
forum: General Help
---

### Post by collaredsiren on 2010-07-31
GParted tells me my hard drive is not partitioned and has an unrecognised partition table, but I know it has because i'm using it now to write this on here, and fdisk shows the following:

> craig@craig-desktop:~$ sudo fdisk -l /dev/sda
omitting empty partition (7)

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc4d3c4d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8518    68417671+   6  FAT16
/dev/sda2            8518       14946    51635186    5  Extended
/dev/sda5           14686       14946     2096451   82  Linux swap / Solaris
/dev/sda6            8518        9530     8124416   83  Linux

Partition table entries are not in disk order
craig@craig-desktop:~$ 


anyone know of anyreason GParted may not be working or can offer an alternative to create a partition?

---

### Post by collaredsiren on 2010-07-31
Ooops should of included the ERROR GParted throws at me:

> Error: Invalid partition table on /dev/sda -- wrong signature 0.

---

### Post by Rubi1200 on 2010-07-31
What do you use sda1 for? Fdisk indicates that the boot flag is here, but I have personally never seen a boot partition that is formatted to FAT16.

---

### Post by collaredsiren on 2010-08-01
boot is via GRUB in the MBR, not sure why the boot flag is there because there are no boot files on that partition 



Think what I am going to do to get rid of this error msg is just backup any files I want to sdb and start the drive afresh

---

