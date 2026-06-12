---
title: "Help! Drive with important data won't mount after hibernation"
date: 2011-02-18
forum: General Help
---

### Post by inverser on 2011-02-18
Hey guys, I have a expresscard that I use for saving a lot of my important documents, and my laptop went into hibernation today and now the drive no longer mounts. 

How do I fix this?

Please help!

---

### Post by ajgreeny on 2011-02-18
Can we see the output from ```
sudo fdisk -l
```lower case L at end, with the card attached.

---

### Post by inverser on 2011-02-18
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc03b8938

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3460    27784192    7  HPFS/NTFS
/dev/sda2            5844        9730    31216641    5  Extended
/dev/sda3            3460        5843    19147776   83  Linux
/dev/sda5            5844        9564    29884416   83  Linux
/dev/sda6            9564        9730     1331200   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by inverser on 2011-02-18
```
sudo gpart /dev/sdb

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
```

---

### Post by inverser on 2011-02-18
What's weird about my fdisk -l output is that the ExpressCard is 96GB, not 4GB. 

There has to be someone that's recovered a drive having similar problem..... anyone?

---

