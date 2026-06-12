---
title: "Hard disk space"
date: 2011-04-16
forum: General Help
---

### Post by chadonline on 2011-04-16
I am running out of space and looking to save HD space for docs, music..etc (do not want to get an external drive yet)

I have a dual boot Lifebook T4020D (windows xp and unbuntu)

are any of these partitions can be used?




sudo fdisk -l


Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b263b25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1452    11657483+   c  W95 FAT32 (LBA)
/dev/sda2            2792        4864    16644096   83  Linux
/dev/sda3            1452        2792    10767361    5  Extended
/dev/sda5            1452        2729    10261504   83  Linux
/dev/sda6            2730        2792      504832   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Hedgehog1 on 2011-04-17
40 gigs is not a lot of room for two OSs, but it can be made to work.

_How much free space is available in these partitions:_

[B]/dev/sda1 * 1 1452 11657483+ c W95 FAT32 (LBA)
/dev/sda2 2792 4864 16644096 83 Linux
/dev/sda5 1452 2729 10261504 83 Linux[/B]

Based on which partitions have space left, some shrinking and expanding of partitions may be possible...

***The Hedge***

:KS

---

### Post by chadonline on 2011-04-18
/dev/sda1
Filesystem            Size  Used Avail Use% Mounted on
none                  491M  272K  491M   1% /dev

/dev/sda2
Filesystem            Size  Used Avail Use% Mounted on
none                  491M  272K  491M   1% /dev



/dev/sda5
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.7G  5.9G  3.3G  65% /


thx

---

### Post by Hedgehog1 on 2011-04-18
> **chadonline said:**
> [B][COLOR="Red"]/dev/sda1
Filesystem            Size  Used Avail Use% Mounted on
none                  491M  272K  491M   1% /dev

/dev/sda2
Filesystem            Size  Used Avail Use% Mounted on
none                  491M  272K  491M   1% /dev[/COLOR][/B]

/dev/sda5
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.7G  5.9G  3.3G  65% /

chadonline - I think the data for /dev/sda1 and /dev/sda2 are repeats.

Would you please double check those figures?

Thanks,

***The Hedge***

:KS

---

