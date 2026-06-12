---
title: "Recovering from lost partition."
date: 2009-12-15
forum: General Help
---

### Post by drakan on 2009-12-15
In brief, I tried to fix my non-booting windows partition with ms-sys and borked it in the process due to misleading directions. I backed up the partition but the file system seems to be damaged so recovery will be less than easy.
I have good news though.

Here is my TestDisk output:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30394 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
D HPFS - NTFS              5   0  1 29999 254 63  481869675
D HPFS - NTFS              5   0  9 24781 254 63  398042497
D Linux                24782   1  1 29036 254 63   68356512
D Linux Swap           29037   1  1 30000 254 63   15486597
P FAT32 LBA            30001   0  1 30392 254 63    6297480 [DellRestore]
```

Here is my issue:

```
D HPFS - NTFS              5   0  9 24781 254 63  398042497


```
---This is the correct size partition but the filesystem is damaged. I can see this in Gparted

```
D HPFS - NTFS              5   0  1 29999 254 63  481869675

```
---This partition obviously overlaps both my linux partitions but the files are accessible through testdisk. I cannot see this in Gparted.


I'm afraid to recover the second one due to its inaccurate size.  Aside from manually,what is the best way to transfer every file from it (or restore it)? I'm not sure which application could discover the inaccurate second one and be able to back up files.

---

### Post by lidex on 2009-12-15
TestDisk should do it all for you. Have you read the wiki?
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

Rescue CDs using TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Livecd]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

---

