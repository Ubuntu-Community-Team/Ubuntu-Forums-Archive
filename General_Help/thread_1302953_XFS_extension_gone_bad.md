---
title: "XFS extension gone bad"
date: 2009-10-27
forum: General Help
---

### Post by J0ris on 2009-10-27
Hi,

I just used Gparted to extend an existing XFS partition. I know, not something one is advised to try without a backup but since I didn't have anything big enough to back it up to... In short, it did not end well. Something went wrong and gparted tried to roll it back to the original partition. From the log file I saved it would appear that it succeeded. However, Gparted does not recognise any valid filesystem on that partition let alone any of my files on it. 
Can anyone point me in the right direction as to how to recover this volume, if at all? Below the saved log and a screen shot.

much obliged

```

GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Delete Logical Partition (xfs, 80.00 GiB) from /dev/sdc  00:00:02    ( SUCCESS )
     	
calibrate /dev/sdc5  00:00:01    ( SUCCESS )
     	
path: /dev/sdc5
start: 16771923
end: 184538654
size: 167766732 (80.00 GiB)
delete partition  00:00:01    ( SUCCESS )

========================================
Move /dev/sdc5 to the left and grow it from 763.52 GiB to 843.52 GiB  01:45:11    ( ERROR )
     	
calibrate /dev/sdc5  00:00:00    ( SUCCESS )
     	
path: /dev/sdc5
start: 184538718
end: 1785753269
size: 1601214552 (763.52 GiB)
calculate new size and position of /dev/sdc5  00:00:00    ( SUCCESS )
     	
requested start: 16771923
requested end: 1785753269
requested size: 1768981347 (843.52 GiB)
new start: 16771923
new end: 1785753269
new size: 1768981347 (843.52 GiB)
check file system on /dev/sdc5 for errors and (if possible) fix them  00:00:12    ( SUCCESS )
     	
xfs_repair -v /dev/sdc5
     	
Phase 1 - find and verify superblock...
- block cache size set to 337784 entries
Phase 2 - using internal log
- zero log...
zero_log: head block 75575 tail block 75575
- scan filesystem freespace and inode maps...
zeroing unused portion of secondary superblock (AG #34)
zeroing unused portion of secondary superblock (AG #35)
- found root inode chunk
Phase 3 - for each AG...
- scan and clear agi unlinked lists...
- process known inodes and perform inode discovery...
- agno = 0
- agno = 1
- agno = 2
- agno = 3
- agno = 4
- agno = 5
- agno = 6
- agno = 7
- agno = 8
- agno = 9
- agno = 10
- agno = 11
- agno = 12
- agno = 13
- agno = 14
- agno = 15
- agno = 16
- agno = 17
- agno = 18
- agno = 19
- agno = 20
- agno = 21
- agno = 22
- agno = 23
- agno = 24
- agno = 25
- agno = 26
- agno = 27
- agno = 28
- agno = 29
- agno = 30
- agno = 31
- agno = 32
- agno = 33
- agno = 34
- agno = 35
- process newly discovered inodes...
Phase 4 - check for duplicate blocks...
- setting up duplicate extent list...
- check for inodes claiming duplicate blocks...
- agno = 0
- agno = 1
- agno = 2
- agno = 3
- agno = 4
- agno = 5
- agno = 6
- agno = 7
- agno = 8
- agno = 9
- agno = 10
- agno = 11
- agno = 12
- agno = 13
- agno = 14
- agno = 15
- agno = 16
- agno = 17
- agno = 18
- agno = 19
- agno = 20
- agno = 21
- agno = 22
- agno = 23
- agno = 24
- agno = 25
- agno = 26
- agno = 27
- agno = 28
- agno = 29
- agno = 30
- agno = 31
- agno = 32
- agno = 33
- agno = 34
- agno = 35
Phase 5 - rebuild AG headers and trees...
- agno = 0
- agno = 1
- agno = 2
- agno = 3
- agno = 4
- agno = 5
- agno = 6
- agno = 7
- agno = 8
- agno = 9
- agno = 10
- agno = 11
- agno = 12
- agno = 13
- agno = 14
- agno = 15
- agno = 16
- agno = 17
- agno = 18
- agno = 19
- agno = 20
- agno = 21
- agno = 22
- agno = 23
- agno = 24
- agno = 25
- agno = 26
- agno = 27
- agno = 28
- agno = 29
- agno = 30
- agno = 31
- agno = 32
- agno = 33
- agno = 34
- agno = 35
- reset superblock...
Phase 6 - check inode connectivity...
- resetting contents of realtime bitmap and summary inodes
- traversing filesystem ...
- agno = 0
- agno = 1
- agno = 2
- agno = 3
- agno = 4
- agno = 5
- agno = 6
- agno = 7
- agno = 8
- agno = 9
- agno = 10
- agno = 11
- agno = 12
- agno = 13
- agno = 14
- agno = 15
- agno = 16
- agno = 17
- agno = 18
- agno = 19
- agno = 20
- agno = 21
- agno = 22
- agno = 23
- agno = 24
- agno = 25
- agno = 26
- agno = 27
- agno = 28
- agno = 29
- agno = 30
- agno = 31
- agno = 32
- agno = 33
- agno = 34
- agno = 35
- traversal finished ...
- moving disconnected inodes to lost+found ...
Phase 7 - verify and correct link counts...

XFS_REPAIR Summary Tue Oct 27 18:46:41 2009

Phase Start End Duration
Phase 1: 10/27 18:46:29 10/27 18:46:29
Phase 2: 10/27 18:46:29 10/27 18:46:32 3 seconds
Phase 3: 10/27 18:46:32 10/27 18:46:39 7 seconds
Phase 4: 10/27 18:46:39 10/27 18:46:40 1 second
Phase 5: 10/27 18:46:40 10/27 18:46:41 1 second
Phase 6: 10/27 18:46:41 10/27 18:46:41
Phase 7: 10/27 18:46:41 10/27 18:46:41

Total run time: 12 seconds
done
move partition to the left  00:00:02    ( SUCCESS )
     	
old start: 184538718
old end: 1785753269
old size: 1601214552 (763.52 GiB)
new start: 16771923
new end: 1617986474
new size: 1601214552 (763.52 GiB)
move file system to the left  01:44:55    ( ERROR )
     	
perform read-only test  01:44:55    ( ERROR )
     	
using internal algorithm
read 1601214552 sectors
finding optimal blocksize
     	
read 65536 sectors using a blocksize of 128 sectors  00:00:00    ( SUCCESS )
     	
65536 of 65536 read
0.421743 seconds
read 65536 sectors using a blocksize of 256 sectors  00:00:00    ( SUCCESS )
     	
65536 of 65536 read
0.408294 seconds
read 65536 sectors using a blocksize of 512 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
0.340518 seconds
read 65536 sectors using a blocksize of 1024 sectors  00:00:00    ( SUCCESS )
     	
65536 of 65536 read
0.497178 seconds
read 65536 sectors using a blocksize of 2048 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
0.569191 seconds
read 65536 sectors using a blocksize of 4096 sectors  00:00:00    ( SUCCESS )
     	
65536 of 65536 read
0.519395 seconds
read 65536 sectors using a blocksize of 8192 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
1.02717 seconds
read 65536 sectors using a blocksize of 16384 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
1.01799 seconds
read 65536 sectors using a blocksize of 32768 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
0.663972 seconds
read 65536 sectors using a blocksize of 65536 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
0.628717 seconds
optimal blocksize is 512 sectors (256.00 KiB)
read 1600559192 sectors using a blocksize of 512 sectors  01:44:49    ( ERROR )
     	
1015081560 of 1600559192 read
Error while reading block at sector 1200275638
1015736920 sectors read    ( ERROR )
rollback last change to the partition table  00:00:02    ( SUCCESS )
     	
move partition to the right  00:00:02    ( SUCCESS )
     	
old start: 16771923
old end: 1617986474
old size: 1601214552 (763.52 GiB)
new start: 184538655
new end: 1785753269
new size: 1601214615 (763.52 GiB)
libparted messages    ( INFO )
     	
Input/output error during read on /dev/sdc

========================================
```

---

### Post by J0ris on 2009-10-28
Anybody?

---

### Post by jward3010 on 2009-10-28
Do an:
```
sudo fdisk -l
```
And post what you get

---

### Post by jward3010 on 2009-10-28
This MIGHT help, installing xfsprogs and doing a restart:
```
sudo apt-get install xfsprogs
```

---

### Post by J0ris on 2009-10-29
Thanks jward3010,

This is the output of fdisk -l:

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d2f9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1044     8385898+  83  Linux
/dev/sdc2            1045      121601   968374102+   5  Extended
/dev/sdc5           11488      111158   800607307+  83  Linux
/dev/sdc6          111159      121601    83883366   83  Linux
```

The problem partition is sdc5

xfs-progs was already present on my system. To no avail. Right now, I have already been running xfs_repair for over an hour. It appears to be looking for a 'secondary superblock' candidate which, whatever else that does, logically, means that the primary is screwed, right? Can anybody draw further conclusions from this? Or is the srewedness of things pretty much irrevocable here?

Thanks

---

### Post by jward3010 on 2009-10-30
I'm gonna have to relinquish my minor XFS abilities here, in other words I have no clue, and let some XFS brainbox in to help.

Have you tried the command...
```
fsck
```

---

### Post by J0ris on 2009-11-06
Thanks for your help jward3010. I just ended up reformatting it. It would seem that all the superblock metadata was gone and therefore the data it described irretrievable. Oh well.

---

### Post by jward3010 on 2009-11-06
Sorry I couldn't help, hope none of it was majorally important like a cure for cancer or Mark Shuttleworth's bank details?

---

### Post by J0ris on 2009-11-09
Nothing major, indeed...

---

