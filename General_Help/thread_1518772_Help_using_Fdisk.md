---
title: "Help using Fdisk"
date: 2010-06-27
forum: General Help
---

### Post by ypestis on 2010-06-27
Dear Forum members,

Im stuck with a messed up partition after a failed Gparted action and got the following steps from the Gparted forum:

> 1)  Confirm that the sdb1 partition still shows the original sector values of
     63 - start sector of /dev/sdb1
     976768064 - end sector of /dev/sdb1
     using the command:

fdisk -l -u /dev/sdb
     Where one of the options is a lower case "L" and not the number one.
2)  Copy the end portion of the partition back to the original position before the move operation.
     Starting end portion to copy to = (976768064 - (1060290 - 63)) - 199548543 = 776159294
     Starting end portion to copy from = 976768064 - 199548543 = 777219521

dd if=/dev/sdb bs=512 skip=777219521 count=199548543 | dd of=/dev/sdb bs=512 seek=776159294


Using Fdisk I get the following information.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   975707837   487853887+   7  HPFS/NTFS


Before using the DD command I need to set the end sector to 976768064 with Fdisk..


I've been looking in the fdisk manual and internet but can't seem to figure out how I can do this.
If somebody could help me out, it would be greatly appreciated!


Thank you alot in advance,


Ype

---

### Post by efflandt on 2010-06-27
With a live/install CD, you could use **sudo fdisk** to remove the partition and recreate it with corrected start and end points.  That does not remove any data, it just sets things in the partition table.  But once you format it or start moving data around on it (dd) all bets are off if you make a mistake.

I hesitate to tell you anything specific because you did not say what is not working, what you attempted to do with gparted, what error you got, or whether it actually changed anything or gave up before doing anything due to some problem.

It always helps to record the output of **sudo fdisk -l** (and back up anything you do not want to lose) "before" first tampering with anything.  You have a snapshot of the partition table now.  But what was it before you ran gparted?

In a terminal type: **man fdisk**

---

### Post by ypestis on 2010-06-27
Hi efflandt,

Thanks for your reply, I really appreciate it cause I lost alot of data.

I will tell you what I did.
I wanted to split my USB 500gb WD passport into a 512mb partition (for rescuecd boot) and started Gparted. Unfortunately I made this partition on the left instead of the right so the whole moving procedure took so long that eventually I had to cancel it (cause im travelling and I couldn't wait any longer)..
After that I couldn't see any files anymore. A few days later I plugged my disk in again and suddenly the files and folders are back so I thought it was oke.
After checking I found out everything is mixed up. Some things are missing when I open a mp3 a different song is playing then the mp3 says, some files not opening at all..

Here is a thread on the gparted forum: [http://gparted-forum.surf4.info/viewtopic.php?id=14151](http://gparted-forum.surf4.info/viewtopic.php?id=14151)

Here's a paste of my Gparted log right after I cancelled it.

GParted 0.4.5
Libparted 1.8.8.1.159-1e0e
Move /dev/sdb1 to the right and shrink it from 465.76 GiB to 465.25 GiB  08:09:15    ( ERROR )
         
calibrate /dev/sdb1  00:00:04    ( SUCCESS )
         
path: /dev/sdb1
start: 63
end: 976768064
size: 976768002 (465.76 GiB)
calculate new size and position of /dev/sdb1  00:00:00    ( SUCCESS )
         
requested start: 1060290
requested end: 976768064
requested size: 975707775 (465.25 GiB)
new start: 1060290
new end: 976768064
new size: 975707775 (465.25 GiB)
check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:07    ( SUCCESS )
         
ntfsresize -P -i -f -v /dev/sdb1
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 500105216512 bytes (500106 MB)
Current device size: 500105217024 bytes (500106 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 409046 MB (81.8%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 430232 MB 0
Multi-Record : 500106 MB 51834
$MFTMirr : 250053 MB 1
Compressed : 61791 MB 52926
Sparse : 303778 MB 74196
Ordinary : 500105 MB 51810
You might resize at 409045397504 bytes or 409046 MB (freeing 91060 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:01:22    ( SUCCESS )
         
run simulation  00:00:11    ( SUCCESS )
         
ntfsresize -P --force /dev/sdb1 -s 499562380799 --no-action
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 500105216512 bytes (500106 MB)
Current device size: 500105217024 bytes (500106 MB)
New volume size : 499562373632 bytes (499563 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 409046 MB (81.8%)
Collecting resizing constraints ...
Needed relocations : 132530 (543 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
real resize  00:01:11    ( SUCCESS )
         
ntfsresize -P --force /dev/sdb1 -s 499562380799
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 500105216512 bytes (500106 MB)
Current device size: 500105217024 bytes (500106 MB)
New volume size : 499562373632 bytes (499563 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 409046 MB (81.8%)
Collecting resizing constraints ...
Needed relocations : 132530 (543 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sdb1'.
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
1) create it at the same disk sector (use sector as the unit!)
2) create it with the same partition type (usually 7, HPFS/NTFS)
3) do not make it smaller than the new NTFS filesystem size
4) set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode.
shrink partition from 465.76 GiB to 465.25 GiB  00:00:00    ( SUCCESS )
         
old start: 63
old end: 976768064
old size: 976768002 (465.76 GiB)
new start: 63
new end: 975707837
new size: 975707775 (465.25 GiB)
check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:08    ( SUCCESS )
         
ntfsresize -P -i -f -v /dev/sdb1
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 499562373632 bytes (499563 MB)
Current device size: 499562380800 bytes (499563 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 409046 MB (81.9%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 430232 MB 0
Multi-Record : 497432 MB 82273
$MFTMirr : 250053 MB 1
Compressed : 61791 MB 52926
Sparse : 303778 MB 74196
Ordinary : 499563 MB 51709
You might resize at 409045381120 bytes or 409046 MB (freeing 90517 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:02    ( SUCCESS )
         
run simulation  00:00:01    ( SUCCESS )
         
ntfsresize -P --force /dev/sdb1 --no-action
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 499562373632 bytes (499563 MB)
Current device size: 499562380800 bytes (499563 MB)
New volume size : 499562373632 bytes (499563 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:01    ( SUCCESS )
         
ntfsresize -P --force /dev/sdb1
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 499562373632 bytes (499563 MB)
Current device size: 499562380800 bytes (499563 MB)
New volume size : 499562373632 bytes (499563 MB)
Nothing to do: NTFS volume size is already OK.
calculate new size and position of /dev/sdb1  00:00:00    ( SUCCESS )
         
requested start: 1060290
requested end: 976768064
requested size: 975707775 (465.25 GiB)
new start: 1060290
new end: 976768064
new size: 975707775 (465.25 GiB)
check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:08    ( SUCCESS )
         
ntfsresize -P -i -f -v /dev/sdb1
         
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 499562373632 bytes (499563 MB)
Current device size: 499562380800 bytes (499563 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 409046 MB (81.9%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 430232 MB 0
Multi-Record : 497432 MB 82273
$MFTMirr : 250053 MB 1
Compressed : 61791 MB 52926
Sparse : 303778 MB 74196
Ordinary : 499563 MB 51709
You might resize at 409045381120 bytes or 409046 MB (freeing 90517 MB).
Please make a test run using both the -n and -s options before real resizing!
move file system to the right    ( EXECUTING )
         
perform read-only test  05:41:49    ( SUCCESS )
         
using internal algorithm
read 975707775 sectors
finding optimal blocksize
         
read 65536 sectors using a blocksize of 128 sectors  00:00:04    ( SUCCESS )
         
65536 of 65536 read
3.76034 seconds
read 65536 sectors using a blocksize of 256 sectors  00:00:02    ( SUCCESS )
         
65536 of 65536 read
2.83994 seconds
read 65536 sectors using a blocksize of 512 sectors  00:00:03    ( SUCCESS )
         
65536 of 65536 read
2.87743 seconds
read 65536 sectors using a blocksize of 1024 sectors  00:00:04    ( SUCCESS )
         
65536 of 65536 read
3.52367 seconds
read 65536 sectors using a blocksize of 2048 sectors  00:00:02    ( SUCCESS )
         
65536 of 65536 read
2.39114 seconds
read 65536 sectors using a blocksize of 4096 sectors  00:00:02    ( SUCCESS )
         
65536 of 65536 read
1.96052 seconds
read 65536 sectors using a blocksize of 8192 sectors  00:00:02    ( SUCCESS )
         
65536 of 65536 read
1.78882 seconds
read 65536 sectors using a blocksize of 16384 sectors  00:00:02    ( SUCCESS )
         
65536 of 65536 read
1.6872 seconds
read 65536 sectors using a blocksize of 32768 sectors  00:00:02    ( SUCCESS )
         
65536 of 65536 read
1.87736 seconds
read 65536 sectors using a blocksize of 65536 sectors  00:00:01    ( SUCCESS )
         
65536 of 65536 read
1.86731 seconds
optimal blocksize is 16384 sectors (8.00 MiB)    ( ERROR )
read 975052415 sectors using a blocksize of 16384 sectors  05:41:25    ( SUCCESS )
         
975052415 of 975052415 read
975707775 sectors read
perform real move    ( EXECUTING )
         
using internal algorithm
copy 975707775 sectors
finding optimal blocksize
         
copy 65536 sectors using a blocksize of 64 sectors  00:00:10    ( SUCCESS )
         
65536 of 65536 copied
10.3361 seconds
copy 65536 sectors using a blocksize of 128 sectors  00:00:09    ( SUCCESS )
         
65536 of 65536 copied
8.28801 seconds
copy 65536 sectors using a blocksize of 256 sectors  00:00:07    ( SUCCESS )
         
65536 of 65536 copied
6.9064 seconds
copy 65536 sectors using a blocksize of 512 sectors  00:00:05    ( SUCCESS )
         
65536 of 65536 copied
5.52724 seconds
copy 65536 sectors using a blocksize of 1024 sectors  00:00:05    ( SUCCESS )
         
65536 of 65536 copied
4.68153 seconds
copy 65536 sectors using a blocksize of 2048 sectors  00:00:04    ( SUCCESS )
         
65536 of 65536 copied
3.68164 seconds
copy 65536 sectors using a blocksize of 4096 sectors  00:00:03    ( SUCCESS )
         
65536 of 65536 copied
3.45419 seconds
copy 65536 sectors using a blocksize of 8192 sectors  00:00:03    ( SUCCESS )
         
65536 of 65536 copied
3.35351 seconds
copy 65536 sectors using a blocksize of 16384 sectors  00:00:04    ( SUCCESS )
         
65536 of 65536 copied
3.18693 seconds
copy 65536 sectors using a blocksize of 32768 sectors  00:00:03    ( SUCCESS )
         
65536 of 65536 copied
3.32705 seconds
copy 65536 sectors using a blocksize of 65536 sectors  00:00:03    ( SUCCESS )
         
65536 of 65536 copied
3.40771 seconds
optimal blocksize is 16384 sectors (8.00 MiB)
copy 974986879 sectors using a blocksize of 16384 sectors    ( EXECUTING )
         
199548543 of 974986879 copied
========================================
Create Primary Partition #1 (ntfs, 517.72 MiB) on /dev/sdb
========================================

---

### Post by dragos240 on 2010-06-27
You may be able to recover some data using testdisk, it's worth a shot.

---

### Post by ypestis on 2010-06-27
Yeah I used testdisk to recover some pictures but I dont have enough space to recover all data :(

---

### Post by ypestis on 2010-07-05
Anybody out there who can help me out with the Fdisk command?

---

### Post by ypestis on 2010-07-26
Still looking for someone to help me with the FDISK command. 
Thanks alot!

---

