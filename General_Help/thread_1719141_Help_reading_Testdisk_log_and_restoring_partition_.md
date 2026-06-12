---
title: "Help reading Testdisk log and restoring partition table"
date: 2011-04-01
forum: General Help
---

### Post by CrusaderAD on 2011-04-01
I ran testdick on a apple hard drive to find the tables. It looks like it found it, here's the log:

> Tue Mar 29 12:02:56 2011
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.32-30-generic (#59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011)
Compiler: GCC 4.4 - Jun 23 2009 17:11:34
ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       488281250 sectors
/dev/sda: user_max   488281250 sectors
/dev/sda: native_max 488281250 sectors
/dev/sda: dco        488397168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30394 255 63, sector size=512 - ATA SAMSUNG HD251HJ
Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - Generic External

Partition table type (auto): Intel
Disk /dev/sdd - 1000 GB / 931 GiB - Generic External
Partition table type: Mac

Analyse Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
Bad MAC partition, invalid block0 signature
read_part_mac: bad DPME signature

search_part()
Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121601 255 63
check_FAT: Bad jump in FAT partition

HFS+ magic value at 121553/57/9
part_size 313992
     HFS                   1952752544 1953066535     313992
     HFS+, 160 MB / 153 MiB

Results
   P HFS                   1952752544 1953066535     313992
     HFS+, 160 MB / 153 MiB

interface_write()
   P HFS                   1952752544 1953066535     313992
Function write_part_mac not implemented

TestDisk exited normally.


How do I restore the table using fdisk? Gparted doesn't let me check the drive. It just says unallocated space, create a table and erase all data.

---

### Post by coldraven on 2011-04-01
I'm not sure what you want, I have never had a Mac but maybe reading this would help:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")
He is the author of testdisk.

---

### Post by CrusaderAD on 2011-04-01
Thanks, I read that. I didn't see anything in there explaining what the values in the log means. I just e-mailed Christophe. Hopefully he'll respond.

---

### Post by coldraven on 2011-04-02
I sent Cristophe some money after Testdisk recovered my Windows partitions that I had accidentally removed. I was so overjoyed to get get them back with all my data intact.
Testdisk is really very powerful but use it with care. It would be better to experiment on an old disk to get the hang of it before trying on your valuable stuff.
Another way is to clone the drive as it is, then try to recover from the clone.
Then if you mess up you can repeat the process with no anxiety.

---

