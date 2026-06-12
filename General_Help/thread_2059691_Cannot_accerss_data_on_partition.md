---
title: "Cannot accerss data on partition"
date: 2012-09-18
forum: General Help
---

### Post by sfourie on 2012-09-18
Hello.
I am not sure if my data are still on my hdd and how I can access it. I copied os onto 2nd hdd and now I cannot access the data that was on the disk prior to copy of os. Is it wiped, overwritten?
If I use disk utility, it seems that the hdd is partioned in two partitions.
How can I access data?

---

### Post by Wim Sturkenboom on 2012-09-18
So you have two HDs? Or one HD with 2 partitions? And how did you move the OS?

Please provide the output of _sudo fdisk -l_ (that is lowercase L at the end) and _df -h_

fdisk for a system with 3 harddisks and multiple partitions on each; please remove removable media before running the command
```

wim@i3-2120:~$ **[COLOR="Blue"]sudo fdisk -l[/COLOR]**
[sudo] password for wim: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd2efff31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   511999999   255896576    7  HPFS/NTFS/exFAT
/dev/sda3       512000000   528001023     8000512   82  Linux swap / Solaris
/dev/sda4       528003070  1953523711   712760321    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       528003072   820969471   146483200   83  Linux
/dev/sda6       820971520  1953523711   566276096   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e192e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    52436159    26218048+   7  HPFS/NTFS/exFAT
/dev/sdb2        52436221   472655871   210109825+   f  W95 Ext'd (LBA)
/dev/sdb5        52436223   115346699    31455238+   7  HPFS/NTFS/exFAT
/dev/sdb6       115346763   167782859    26218048+   b  W95 FAT32
/dev/sdb7       167782923   220219019    26218048+  83  Linux
/dev/sdb8       220219392   228579327     4179968   82  Linux swap / Solaris
/dev/sdb9       228581376   472655871   122037248   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c8c2717

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001   83  Linux
wim@i3-2120:~$ 

```

df -h
```

wim@i3-2120:~$ **[COLOR="Blue"]df -h[/COLOR]**
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       138G  3,5G  128G   3% /
udev            3,7G  4,0K  3,7G   1% /dev
tmpfs           1,5G  848K  1,5G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,7G  224K  3,7G   1% /run/shm
/dev/sda6       532G   27G  478G   6% /home
/dev/sdc1       925G  210G  706G  23% /mnt/photos
wim@i3-2120:~$ 

```

---

### Post by oldfred on 2012-09-18
Please do not create duplicate threads on same topic.

[http://ubuntuforums.org/showthread.php?t=2059241](http://ubuntuforums.org/showthread.php?t=2059241)

Thread closed.

---

