---
title: "partimage problem."
date: 2010-10-06
forum: General Help
---

### Post by apix on 2010-10-06
At first, i created a full back up of my usb stick partition (2GB) using no compression backup with partimage. Then i created a usb boot stick with ubuntu, booted, did my job (HD partition resize) and then i tried to restore my stick.

Now i get a size error

```
The partition is to small to
 be restored:
Original partition
size:........2097119232 bytes
Destination partition 
size:.....2089188864 bytes 

```

I tried resizing the partition, deleting it and creating a new one, change type, etc but i still get the same error.

Any ideas ?

Cheers :)

---

### Post by psusi on 2010-10-06
Did you back up the entire disk, or only the partition?  It sounds like you backed up the partition, and then shrank the size of the partition a bit before you went to restore.  What does sudo fdisk -lu show?

---

### Post by apix on 2010-10-06
```
fdisk -lu /dev/sdb

Disk /dev/sdb: 2097 MB, 2097151488 bytes
255 heads, 63 sectors/track, 254 cylinders, total 4095999 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000480c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     4080509     2040223+   b  W95 FAT32

```

I backed up only the partition, not the entire stick.

---

### Post by psusi on 2010-10-06
Yep, that partition is smaller than it was before.  Run sudo fdisk -u /dev/sdb, delete the partition, and recreate it with the correct end sector ( 4095998 ).

---

### Post by apix on 2010-10-06
```
$ fdisk -lu /dev/sdb

Disk /dev/sdb: 2097 MB, 2097151488 bytes
246 heads, 54 sectors/track, 308 cylinders, total 4095999 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000480c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     4095998     2047968    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 10)
Partition 1 has different physical/logical endings:
     phys=(254, 245, 54) logical=(308, 83, 45)

```

I did what you said, but i get the same error. Above you can see the output of fdisk. The end block is correct, but the error is still there.

EDIT: the procedure that i followed after getting into fdisk was: (a) delete the partition, (b) create a new one with the correct end sector, (c) set the type to fat32 (d) write the changes and exit.

---

### Post by psusi on 2010-10-06
Did you get the warning that the changes did not take effect yet and you need to reboot when you saved?  If so, reboot ( or eject the usb stick and reinsert it ).

---

### Post by apix on 2010-10-06
Cheers, that was it. I didnt noticed that i had to eject the drive and re-plug it.

After all the problem was that gparted and cfdisk did not set the correct ending sector. Or rather i didnt tell them how to do it :p


Many thanks for the fast replys !

---

