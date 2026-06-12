---
title: "Installing geexbox,dual boot"
date: 2009-11-10
forum: General Help
---

### Post by sandy8925 on 2009-11-10
I want to install Geexbox on a separate ext2 partition. Currently my setup is as follows :

/dev/sda1 - FAT - boot partition
/dev/sda2 - Linux swap - 1 GB
/dev/sda3 - ext4 (Ubuntu) - ~38 GB
/dev/sda4 - LBA(extended partition)
      /dev/sda5 - NTFS (Windows XP) - ~37 GB 

I want to resize the swap partition and create 2 new partitions on which I want to install DSL and Geexbox. To sum  up I want to convert the 1 GB swap partition into 3 partitions - swap,ext2,ext2 .

The problem I have is that there already 4 primary partitions and I can't create any more (who made that stupid limit anyway?). I've already created an extended partition for the Windows XP install.So what do I do ?

---

### Post by sandy8925 on 2009-11-10
The output for "fdisk -lu" is:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb25db25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       96389       48163+   7  HPFS/NTFS
/dev/sda2           96390     2200904     1052257+  82  Linux swap / Solaris
/dev/sda3         2200905    79264709    38531902+  83  Linux
/dev/sda4        79264710   156280319    38507805    f  W95 Ext'd (LBA)
/dev/sda5        79264773   156280319    38507773+   7  HPFS/NTFS

```

---

