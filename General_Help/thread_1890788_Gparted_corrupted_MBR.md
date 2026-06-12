---
title: "Gparted corrupted MBR"
date: 2011-12-04
forum: General Help
---

### Post by ashwinrao on 2011-12-04
I was in the process of resizing the partition on my 500 GB /sda which consists of Win7 and Ubuntu 10.04. In the process whole /sda became 'unallocated'. Please help! Can I retrieve my Ubuntu and NTFS data? Please guide me in this process. I'm using Ubuntu 11.10 live CD now. Please give me the steps by step advice to retrieve my data.:(

---

### Post by ashwinrao on 2011-12-04
Here is my analysis:
```

``` sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2c62

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 8012 MB, 8012169216 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15648768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00031862

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15635593     7817766    c  W95 FAT32 (LBA)
```

```

/dev/sdb is Live USB with Ubuntu. I'm currently searching the luck with fixparts.

---

### Post by oldfred on 2011-12-04
Gparted does have a repair function also. I have not used it but some have posted that it does work.

I have used testdisk and it finds old partitions. If you have several versions of old partitions it will show all, but you have to choose which to restore and they cannot overlap.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links

---

### Post by ashwinrao on 2011-12-05
Thank you for your reply. It turned out to be a faulty HDD. Now, it doesn't even getting recognized. I have suffered two Seagate crashes. Planning to send HDD for warranty. It was only one year old 500 GB. Time to look for WD alternative now. Thanks for Ubuntu. It still working from my USB and I can still use my machine.

---

