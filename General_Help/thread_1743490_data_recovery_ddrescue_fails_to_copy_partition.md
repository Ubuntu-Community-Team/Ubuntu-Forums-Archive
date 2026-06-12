---
title: "data recovery ddrescue fails to copy partition"
date: 2011-04-29
forum: General Help
---

### Post by wizodd0 on 2011-04-29
I'm copying a disk partition to a new HD using Gnu ddrescue. 
OS is Win XP x64 on AMD Athlon 2 x2 cpu
Working from Ubuntu 10.4 CD
 
The old partition is 112GB (of 200GB) the new one 566GB (of 640GB)
the old partition has 95GB of data. 
When copying, ddrescue gets to about 1/3 through the data and err's out...it doesn't copy anything after that. Nor does it report any errors....

I've tried changing blocksize & retry count, but it always fails the same way in the same place.

Diskutility reports that the filesystem is intact.

Any assistance would be greatly appreciated....:confused:
 
**log:** 
 
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 200.0 GB, 200049647616 bytes 
255 heads, 63 sectors/track, 24321 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x0d6aa52a 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       14537   116768421    7  HPFS/NTFS 
/dev/sda2           14538       24321    78589980    7  HPFS/NTFS 
 
Disk /dev/sdb: 640.1 GB, 640135028736 bytes 
255 heads, 63 sectors/track, 77825 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x0d6aa52a 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       73940   593921024    7  HPFS/NTFS 
/dev/sdb2           73941       77826    31208449    5  Extended 
/dev/sdb5           77588       77826     1910784   82  Linux swap / Solaris 
/dev/sdb6           73941       77588    29296640   83  Linux 
 
Partition table entries are not in disk order 
 
ubuntu@ubuntu:~$ sudo ddrescue -n -v /dev/sda1 /dev/sdb1 rescue.log 
 
About to copy 119570 MBytes from /dev/sda1 to /dev/sdb1 
    Starting positions: infile = 0 B,  outfile = 0 B 
    Copy block size: 128 hard blocks 
Hard block size: 512  bytes 
Max_retries: 0     
Direct: no    Sparse: no    Split: no    Truncate: no 
 
Press Ctrl-C to interrupt 
Initial status (read from logfile) 
rescued:         0 B,  errsize:       0 B,  errors:       0 
Current status 
rescued:    34287 MB,  errsize:       0 B,  current rate:     287 kB/s 
   ipos:    34287 MB,   errors:       0,    average rate:   44820 kB/s 
   opos:    34287 MB,     time from last successful read:       0 s 
Copying non-tried blocks... 
ddrescue: write error: Input/output error 
 
**rescue.log** 
 
# Rescue Logfile. Created by GNU ddrescue version 1.11 
# current_pos  current_status 
0x7FBB30200     ? 
#      pos        size  status 
0x00000000  0x7FBB30200  + 
0x7FBB30200  0x13DB479200  ?

---

