---
title: "RAID Array missing space."
date: 2011-04-18
forum: General Help
---

### Post by HeWhoWas on 2011-04-18
Hey guys,

I have had and used a working array of 3 x 2tb drives - unfortunately it became full over the weekend, fortunately I had a few spare 2tb drives waiting for this purpose, and I chucked one in, started the grow, and walked away for 20 hours or.

Once I came back to it, I went to grow the partition using gparted, but ran into errors. Mainly the fact that e2fsck kept bitching that md/0p1 was not a valid device. Whenever i work with it, I need to reference it as /dev/md0p1 so that didn't surprise me.

I backed up my somewhat broken partition table using gdisk, just in case (Which turned out to be a good idea) and then deleted the partition table using parted. I then recreated the partition with the same start point, but extending the end point to the end of the drive.

Now gparted see's the drive as a 5.4tb ext4 partition, which is great. But when using the drive, the system still sees it as a 3.6tb :-(

What outputs do you need, and what on earth have I done?

Thanks :-)

Edit, outputs:

mdadm --detail /dev/md0
```
tv@tv-P55A-UD3:/$ sudo mdadm --detail /dev/md0
[sudo] password for tv:
/dev/md0:
        Version : 01.02
  Creation Time : Thu Dec 23 15:22:01 2010
     Raid Level : raid5
     Array Size : 5860539648 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907026432 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Apr 18 16:20:41 2011
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 256K

           Name : tv-desktop:0
           UUID : 44bbc826:36f150e7:996cdf30:1049b0dc
         Events : 42798

    Number   Major   Minor   RaidDevice State
       3       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       4       8       80        3      active sync   /dev/sdf

       5       8       48        -      spare   /dev/sdd
```
gdisk:```
Disk /dev/md0: 11721079296 sectors, 5.5 TiB
Disk identifier (GUID): 162E5CB3-29BC-4354-B477-CDC48F7B63E1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3131144670
Total free space is 479 sectors (239.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34      3131144191   5.5 TiB     0700  primary

```
sudo fdisk -l:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/md0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/md0: 6001.2 GB, 6001192599552 bytes
255 heads, 63 sectors/track, 729603 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 262144 bytes / 786432 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      267350  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.
```parted:
```
Model: Linux Software RAID Array (md)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  6001GB  6001GB  ext4         primary
```df -h:
```
tv@tv-P55A-UD3:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sde5             184G   70G  105G  40% /
none                  2.0G  328K  2.0G   1% /dev
none                  2.0G  100K  2.0G   1% /dev/shm
none                  2.0G  396K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sr0              4.3G  4.3G     0 100% /media/FLACb33tz
/dev/md0p1            3.6T  3.4T  227M 100% /media/test
```

---

### Post by srs5694 on 2011-04-18
```

sudo resize2fs /dev/md0p1

```

---

### Post by HeWhoWas on 2011-04-18
The man is a genius. It worked!

---

