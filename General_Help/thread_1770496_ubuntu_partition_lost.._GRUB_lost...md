---
title: "ubuntu partition lost.. GRUB lost.."
date: 2011-05-29
forum: General Help
---

### Post by finalni on 2011-05-29
the only thing I get when restarting my computer is
```

MBR
_

```Here is how it came to be:
chkdsk on win7 checked one of my partitions and brilliantly concluded that it should be empty. I tried to save the files from it with testdisk but instead of it I wrote the new partition table to MBR. after restarting I got 
```
error: no partition found
grub rescue>

```then I tried to restore GRUB from rescatux, and realized that partition with ubuntu is gone. so I went to grub rescue and tried to boot at least into win7 by using some old advice on this forum
("set root=(hd0, 0)", then "makeactive" but this was not recognized). Now I tried to restore windows MBR from rescatux and.. well, look at the beginning of this post. Maybeee I could restore GRUB (rescue) from rescatux but decided to stop trying to "fix" anything for now..


I'm on rescatux now, here is the output of 
```
$ sudo fdisk -l

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        **3053**    24523191    7  HPFS/NTFS
/dev/sda2            **4009**        9964    47841570    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832    b  W95 FAT32
```I would like to be able to boot ubuntu and/or win7, the lost files on that partition /dev/sda2 are not crucial..

---

### Post by zealibib slaughter on 2011-05-29
if the partition holding ubuntu was formatted why dont you reinstall ubuntu to it and that will reinstall grub as well.

---

### Post by finalni on 2011-05-29
I don't think it's actually formatted, merely the partition table "forgot" about it, and I'm looking for a faster solution..

Perhaps I could use fdisk from here and restore the old partition table, but I'm not familiar with fdisk..


I found some (one month old) data about my previous partition table on sda, it was sth like this:
```

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd576590b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         789     6336513    f  W95 Ext'd (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1476        4008    20346322+   7  HPFS/NTFS
/dev/sda3            4009        9964    47841570    7  HPFS/NTFS
/dev/sda5               1         749     6008832   83  Linux
/dev/sda6             749         789      326656   82  Linux swap / Solaris
```i.e. (in sectors)

```
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046    12,675,071    12,673,026   f W95 Ext d (LBA)
/dev/sda5               2,048    12,019,711    12,017,664  83 Linux
/dev/sda6          12,021,760    12,675,071       653,312  82 Linux swap / Solaris
/dev/sda2    *     23,695,875    64,388,519    40,692,645   7 HPFS/NTFS
/dev/sda3          64,388,520   160,071,659    95,683,140   7 HPFS/NTFS

```

---

### Post by zealibib slaughter on 2011-05-29
well you can boot from a live cd mount the partition that contains grub and run grub-install.  Googling: recovering grub after windows install will give you alot of help on this.  Edit here is a link to the ubuntu help section on recovering grub [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by finalni on 2011-05-29
phew I somehow managed to restore my partition table - at least *partially* :redface: and managed to restore GRUB using rescatux and got ubuntu back :) 
unfortunately I cannot load win7 (drive is inaccessible blah blah), ubuntu cannot see one partition (which is expected since sfdisk said that it's size exceeds max allowable - even though the partition table at the moment had the partition with same start and size :confused: ), i.e.
there's a mess in a partition table, from ubuntu's terminal, the output of fdisk -l is
```
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         789     6336513    f  W95 Ext'd (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2               1         749     6008832   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3             749         789      326656   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda4            1476        4008    20346322+   7  HPFS/NTFS
/dev/sda5               1        1434    11517581   83  Linux
/dev/sda6            1435        1475      329301   82  Linux swap / Solaris
```

at the moment I need ubuntu, so I'm about to leave it as is (for few days at least), and if someone could help me clear this mess, I'd be grateful.

I'm going to change the thread title and category now..

zealibib slaughter, thanks for trying to help, but I don't have that live CD and couldn't burn it from rescatux (at least I think that's not possible).

---

