---
title: "Where are my 46gb? (not under the couch)"
date: 2009-08-05
forum: General Help
---

### Post by soapBAR2 on 2009-08-05
There seems to be some inconsistency on my linux software raid:

```

$ /mnt/Media# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             293G  184G   94G  67% /
tmpfs                 490M     0  490M   0% /lib/init/rw
udev                   10M  128K  9.9M   2% /dev
tmpfs                 490M     0  490M   0% /dev/shm
**/dev/md0              _917G  869G  2.2G 100%_ /mnt/Media**
```

Where are the extra 46gb? I have scoured it for hidden files (there are no hidden folders, and the hidden files are only a few kb in total each), and the operating system files are on a separate disk.

Additional information;

```
$ /mnt/Media# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sda1[0] hdc1[4] hdd1[3] hdb1[2] sdb1[1]
      976783616 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
```

```
$ /mnt/Media# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Oct 13 19:18:12 2007
     Raid Level : raid5
     Array Size : 976783616 (931.53 GiB 1000.23 GB)
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Aug  5 19:35:08 2009
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e8697837:ae6e1e3c:4e59fab5:74f46c19
         Events : 0.15574

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       3       65        2      active sync   /dev/hdb1
       3      22       65        3      active sync   /dev/hdd1
       4      22        1        4      active sync   /dev/hdc1
```

---

### Post by barnex on 2009-08-05
I don't think it's an inconsistency. I have something similar on my (non-raid) home drive. I guess the typical 10% or so disk space that gets automatically reserved for root is not added to the "available" space.

---

### Post by Cheesemill on 2009-08-05
By default 5% of an ext3 volume is reserverd for the use of root only.
This makes it possible to recover your system if the partition gets completely filled.

---

### Post by soapBAR2 on 2009-08-05
> **barnex said:**
> I don't think it's an inconsistency. I have something similar on my (non-raid) home drive. I guess the typical 10% or so disk space that gets automatically reserved for root is not added to the "available" space.

> **Cheesemill said:**
> By default 5% of an ext3 volume is reserverd for the use of root only.
This makes it possible to recover your system if the partition gets completely filled.

Thanks for this. Is there any way to alter or disable this? I don't mind bricking the drives (I have plenty of spares and the data is backed up twice over) - the only thing I'm short of is ports to plug them into, so using as much of the drive as possible makes sense for me.

---

### Post by mcduck on 2009-08-05
> **soapBAR2 said:**
> Thanks for this. Is there any way to alter or disable this? I don't mind bricking the drives (I have plenty of spares and the data is backed up twice over) - the only thing I'm short of is ports to plug them into, so using as much of the drive as possible makes sense for me.

It's possible to change the amount of reserved space, but you really don't want to set it too low on your root partition.

There are several reasons for the reserved space, but simplified the thing is tat Linux really doesn't work too well when it's running out of disk space. And if you fill the drive completely, you won't be able to boot any more. The 5% reserved to root user prevents normal users and their programs from filling the drive to that point.

Also while Linux filesystems suffer less from fragmentation than Windows filesystems do, they still fragment if there's not enough free space on the drive.

So, knowing that hard disk space is very cheap, I would recommend just getting a new drive instead and reducing the reserved space only if you really, really can't get a new drive.

(For any other than root partitition you can safely set the reserved space to 0, but the fragmentation will still be an issue so you'll want to make sure you don't fill the drive to 100%)

---

