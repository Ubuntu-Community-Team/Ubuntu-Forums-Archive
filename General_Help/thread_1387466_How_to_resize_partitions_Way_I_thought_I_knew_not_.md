---
title: "How to resize partitions? Way I thought I knew not working..."
date: 2010-01-21
forum: General Help
---

### Post by Eoghanalbar on 2010-01-21
My ubuntu partition is tiny (~9 GB, ~5 free) and my vista partition is big (~100 GB, ~60 free). I need to reverse this (so I can move all my documents and music (~40 GB) over to the ubuntu portion from the external HD they're on now).

I'm using karmic. I installed gparted, but I couldn't figure out how to make it let me access the resize option. 

So I booted with the karmic live CD and used gparted there. It let me set up the shrink on the vista partition, but gave me an error in actual running (I'll post the error details at the bottom).

The error details seem to be saying that I should try shrinking it less? But I was already leaving more than 10 GB free space there, no?

Does anyone know how to help me past this sticking point here? This is one of the vital steps for me in switching over to using ubuntu as my main OS, and hopefully leaving vista behind.


Details:

GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Shrink /dev/sda2 from 101.37 GiB to 50.78 GiB  00:00:53    ( ERROR )
     	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
     	
path: /dev/sda2
start: 3074048
end: 215669811
size: 212595764 (101.37 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:14    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 108849025536 bytes (108850 MB)
Current device size: 108849031168 bytes (108850 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 44813 MB (41.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 59230 MB 0
Multi-Record : 98242 MB 9
$MFTMirr : 59230 MB 1
Compressed : 98244 MB 30429
Sparse : 86696 MB 50434
Ordinary : 103832 MB 1768
You might resize at 44812529664 bytes or 44813 MB (freeing 64037 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:00:25    ( ERROR )
     	
run simulation  00:00:25    ( ERROR )
     	
ntfsresize -P --force /dev/sda2 -s 54522497023 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 108849025536 bytes (108850 MB)
Current device size: 108849031168 bytes (108850 MB)
New volume size : 54522491392 bytes (54523 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 44813 MB (41.2%)
Collecting resizing constraints ...
Needed relocations : 2223754 (9109 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1096 > 1024), not yet supported!
Please try to free less space.
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:14    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 108849025536 bytes (108850 MB)
Current device size: 108849031168 bytes (108850 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 44813 MB (41.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 59230 MB 0
Multi-Record : 98242 MB 9
$MFTMirr : 59230 MB 1
Compressed : 98244 MB 30429
Sparse : 86696 MB 50434
Ordinary : 103832 MB 1768
You might resize at 44812529664 bytes or 44813 MB (freeing 64037 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:00    ( SUCCESS )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda2 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 108849025536 bytes (108850 MB)
Current device size: 108849031168 bytes (108850 MB)
New volume size : 108849025536 bytes (108850 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 108849025536 bytes (108850 MB)
Current device size: 108849031168 bytes (108850 MB)
New volume size : 108849025536 bytes (108850 MB)
Nothing to do: NTFS volume size is already OK.

========================================

---

### Post by plucky on 2010-01-22
Don't use Gparted to shrink the Vista partition as it could break Vista.Use Vista Disk management to shrink the Vista partition.Also defragment the Vista partition before shrinking.

When using the Live Cd to increase the size of the Linux partition,if it is inside the extended partition,you have to turn off swap before you can increase the size of the extended partition.

Remember you can only resize the rear end of a partition,so if the free space is at the front of a partition,you have to move the partition into the free space with all the data on the partition and the resize the rear of the partition.

Moving the start of a partition can take a long time depending on how much data has to be moved.

Good Luck

---

