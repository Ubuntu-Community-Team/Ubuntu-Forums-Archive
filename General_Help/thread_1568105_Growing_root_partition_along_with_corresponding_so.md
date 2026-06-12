---
title: "Growing root partition along with corresponding softRAID array"
date: 2010-09-04
forum: General Help
---

### Post by 1321423200 on 2010-09-04
So, I recently installed a server with several software RAID partitions over three drives. After installation, I pulled out the CD-ROM and added a fourth drive.

I believe I successfully grew all the arrays (RAID1 for /boot, RAID5 for /, and RAID1 for swap), but I'm not seeing that growth in my filesystem.


The root partition is no larger than it previously was, even though the specific array that is mounted to it has grown to the proper size.


$ df -h
```
Filesystem            Size  Used Avail Use% Mounted on
**/dev/md2              292G  6.8G  271G   3% /**
none                  118M  292K  118M   1% /dev
none                  123M     0  123M   0% /dev/shm
none                  123M  472K  122M   1% /var/run
none                  123M     0  123M   0% /var/lock
none                  123M     0  123M   0% /lib/init/rw
/dev/md0              138M   36M   96M  27% /boot
/dev/md3              166G  157G  516K 100% /raid0
```



$ sudo mdadm --detail /dev/md2
```
/dev/md2:
        Version : 00.90
  Creation Time : Mon Aug 23 23:26:06 2010
     Raid Level : raid5
     **Array Size : 466114368 (444.52 GiB 477.30 GB)**
  Used Dev Size : 155371456 (148.17 GiB 159.10 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sat Sep  4 17:44:05 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 82dc6060:7279efd4:f62956d9:98a26853
         Events : 0.18594

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       8       51        2      active sync   /dev/sdd3
       3       8       35        3      active sync   /dev/sdc3
```



I'm sure I'm missing something quite simple here, but how can I resize my root partition to the full size of /dev/md2?

I should note that even though I ripped out the CD-ROM in favor of an additional HDD, I can probably run a live session from a USB stick (although I've been unable to thus far- any solution that can avoid doing so is preferable).

---

### Post by 1321423200 on 2010-09-07
Still haven't been able to solve this one... Any advice?

---

### Post by 1321423200 on 2010-09-15
(bump- it's been quite a while now...)

---

