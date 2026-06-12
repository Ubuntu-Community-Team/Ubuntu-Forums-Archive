---
title: "Problem Cloning NTFS Volume"
date: 2012-07-23
forum: General Help
---

### Post by teasplurt on 2012-07-23
Hi everybody,
I've been trying to clone a 300GiB windows volume onto a 750GiB hard drive because I'm running out of storage space.  The image is(ideally) going from a 500GiB hard disk with another 200GiB ext4 volume onto a completely blank 750GiB hard drive.  I've been trying to use GParted, while booted into the previously mentioned 200GiB partition, to copy the entire filesystem, but after a while it says that it's hit a bad sector, the disk is faulty, and that I should try using some kind of --rescue option.  For which program, I really don't know.  When I boot into the windows volume, there are no problems, no read errors, and all of my programs work.  All of the system utilities and third party utilities that I use(except for GParted) say that all of my disks are healthy.  I'm really confused.  Any additional information on what may be going on is greatly appreciated.  At this point I don't know for sure whether my hard drive is healthy or failing.  I'd really like to try this --rescue thing, but I don't know what command(s) to append that to.  Thanks for the help.  Here's the full log file:

GParted 0.7.0 --enable-libparted-dmraid

Libparted 2.3

Copy /dev/sda2 to /dev/sdd (start at 1.00 MiB)  00:35:46    ( ERROR )
    	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
    	
path: /dev/sda2
start: 206848
end: 586144347
size: 585937500 (279.40 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:08    ( SUCCESS )
    	
ntfsresize -P -i -f -v /dev/sda2
    	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 299999994368 bytes (300000 MB)
Current device size: 300000000000 bytes (300000 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 276158 MB (92.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 145153 MB 0
Multi-Record : 300000 MB 324041
$MFTMirr : 1 MB 1
Compressed : 288569 MB 86115
Sparse : 295209 MB 57534
Ordinary : 300000 MB 116070
You might resize at 276157108224 bytes or 276158 MB (freeing 23842 MB).
Please make a test run using both the -n and -s options before real resizing!
create empty partition  00:00:01    ( SUCCESS )
    	
path: /dev/sdd1
start: 2048
end: 1465147391
size: 1465145344 (698.64 GiB)
set partition type on /dev/sdd1  00:00:00    ( SUCCESS )
    	
new partition type: ntfs
copy file system of /dev/sda2 to /dev/sdd1  00:35:37    ( ERROR )
    	
ntfsclone -f --overwrite /dev/sdd1 /dev/sda2
    	
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 299999993856 bytes (300000 MB)
Current device size: 300000000000 bytes (300000 MB)
Scanning volume ...
100.00 percent completed
Accounting clusters ...
Space in use : 276158 MB (92.1%) 
Cloning NTFS ...
*************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the *
* disk surface caused by deterioration, manufacturing faults or other *
* reason. The reliability of the disk may stay stable or degrade fast. *
* Use the --rescue option to efficiently save as much data as possible! *
*************************************************************************
ERROR: Disk is faulty, can't make full backup!
ntfsclone v2.0.0 (libntfs 10:0:0)
========================================

---

### Post by Paddy Landau on 2012-07-23
Try [Clonezilla]("http://clonezilla.org/"). Normally used for backups, it can also clone one drive to another. It's not the most user-friendly system, but it works.

Once the drive has been cloned, you can use GParted to move and resize the ext4 partition, and Windows to resize the NTFS one.

---

