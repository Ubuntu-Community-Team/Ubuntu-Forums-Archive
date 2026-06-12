---
title: "Flash drive corrupt"
date: 2010-04-18
forum: General Help
---

### Post by FreezWay on 2010-04-18
I had important files on my flash drive that are not backed up anywhere. I went into the live USB creator, misclicked and trashed my drive.
Now when I plug it in, it doesn't have any files, but its formatting remains. I can right click and see the properties and it appears as though it says the same amount is used.
Currently I tryed using GParted to sort it out and upon selecting the device it starts searching for /dev/sdb partitions. It has been doing that for the last hour. Conky shows that 2 processes of dosfsck are running. Its a new drive and I dont know if it has an activity light.
Please help. Hours of work depend on it.

---

### Post by PRC09 on 2010-04-18
If the drive will still mount you can try cntrl h and see if anything is there.It will show any hidden files.....

---

### Post by FreezWay on 2010-04-18
tried it already.... I managed to copy the drive to my home with gddrescue and mmls gives me:
```
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Size    Description
00:  -----   0000000000   0000000000   0000000001   0512B   Primary Table (#0)
01:  -----   0000000001   0000000061   0000000061   0030K   Unallocated
02:  00:00   0000000062   0016031091   0016031030   0007G   Win95 FAT32 (0x0C)
03:  -----   0016031092   0016035839   0000004748   0002M   Unallocated

```

I found sleuthkit to help, but when I run it I get errors...

```
Invalid magic value (Error: sector size (36352) is not a multiple of device size (512)
Do you have a disk image instead of a partition image?)

```

---

### Post by FreezWay on 2010-04-18
sorry for the bump, but I realllllly need these files!

---

### Post by Kai Summers on 2010-04-18
Try [this thread]("http://ubuntuforums.org/showthread.php?t=417761") for data recovery software compatible with Ubuntu.

---

### Post by FreezWay on 2010-04-18
lol, the shirt I wore yesterday had the RPSLS from ur avatar!

anyway, testdisk tells me 

```
Warning: Incorrect number of heads/cylinder 253 (FAT) != 255 (HD)
Warning: Incorrect number of sectors per track 62 (FAT) != 63 (HD)

```

and
```
No file found, filesystem seems damaged.

```

EDIT: I got it!!! you saved the day!

---

