---
title: "200 GB HD seen as 66 GB"
date: 2009-08-05
forum: General Help
---

### Post by LeboyX on 2009-08-05
I've recently taken a freshly installed, 200GB Maxtor (internal) hard drive and formatted it as an NTFS drive on a Windows XP machine. However, when I take the drive and put it into my other computer - running Ubuntu 9.04 - it registers as only 66 GB, and will not mount at all. 

"fdisk -l" gives the following details. sda and sdc aren't my concern: they're displaying exactly what they should, and mount properly. It's sdb that's the main problem. 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28c3fa2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         669     5373711   83  Linux
/dev/sda2             670        9729    72774450    5  Extended
/dev/sda5             670        9486    70822521   83  Linux
/dev/sda6            9487        9729     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 66.4 GB, 66489155584 bytes
239 heads, 63 sectors/track, 8624 cylinders
Units = cylinders of 15057 * 512 = 7709184 bytes
Disk identifier: 0x05f46da0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8624    64921932+   7  HPFS/NTFS

Disk /dev/sdc: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b6b0466

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1         

```

When I try to mount with "sudo mount /dev/sdb1 [some directory]", I receive the following

```

$MFT LCN (786432) or $MFTMirr LCN (24888617) is greater than the number of clusters (16230483).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

When I try to just mount sdb, with the flag "-t ntfs", I receive this: 

```

NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

---

### Post by michy99 on 2009-08-05
Did it show up as 200 GB on the Windows system? Do you have any data on the disk?

---

### Post by LeboyX on 2009-08-05
Yes, it works fine in Windows. It's formatted size is reported as 189 GB in Windows. However, I have not actually put any data on it yet. 

Is there any particular reason why Linux won't recognize the drive's size?

---

### Post by michy99 on 2009-08-06
Since you haven't put any data on it yet, try re-formating it with gparted.

---

### Post by martinbaselier on 2009-08-06
Have you already formatted the hdd or did you only create a partition? It looks like it has not been formatted yet.

---

### Post by harry2006 on 2009-08-06
seems some issue with partitioning in winbows, as linux is not able to see those and hence not able to mount the same. repartitioning might help if have no data on the disk, though.

---

### Post by LeboyX on 2009-08-06
I'd tried all those things, but to no avail. 

Regardless, I've figured the problem and feel pretty dumb. I had two hard drives slaved on the same cable, so the hardware didn't know what to do with both drives. I've since moved the jumpers on the drives, and everything's working now.

---

