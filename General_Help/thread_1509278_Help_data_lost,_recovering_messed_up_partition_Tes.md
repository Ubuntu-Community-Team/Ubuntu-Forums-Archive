---
title: "Help data lost, recovering messed up partition Testdisk Gparted"
date: 2010-06-14
forum: General Help
---

### Post by ypestis on 2010-06-14
Dear forum,


When running Gparted I had a power problem and during a move operation I had to cancel it.
 It was done on a western digital external 2.5" 500gb harddisk and approximately 80gb was moved.

 

 I would like to ask what is the most smartest thing to do now to get my data back?
I have Linux running and installed testdisk but im not sure how to use this in the optimal way and perhap you have better suggestions.


 I tried testdisk to see if it could do something with it.
After analyse and deeper search this was found.
  Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start                  End     Size in sectors
* HPFS - NTFS              0   1  1 60735 254 63  975723777 [Portable]
  

  My partition that is lost was called Portable. If I press P to list the files though only the $RECYCLE.BIN dir is showed (Windows trash?)
Does this mean my files are lost or do I need to do something else?

When I run Photorec it does find files but I can't get the directory and file name structures back will this change if I run testdisk on a succesfull way?

  

 

 Any help is more then welcome!
Thank you very much.
 

 

 Here's a paste of my Gparted log:
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

### Post by coldraven on 2010-06-14
If your data is very valuable you should clone your drive first (using dd maybe) and then play with Testdisk.
Testdisk is very powerful but it helps if you have used it before, so practicing on your valuable data is not a good idea.
I once used it to recover my XP partitions but I was sweating while I did it!
Good luck.

---

### Post by ypestis on 2010-06-14
Hi thanks for the reply.
Well im travelling and all my photo's video's reports etc of my travel are gone...
I need to find a new HD so I can backup the messed up one now..

I was thinking Partimage might be the best way to do a complety backup including partition information..

Anyone else can answer the above questions concerning testdisk and photorec..
Especially want to know if the P option doesn't show the files does it mean for sure the file and folder names/structures are lost??

Cause if that's the case I will just start photorec and try to rename as much as possible.. (LOT OF WORK arggh)

---

### Post by ronnielsen1 on 2010-06-14
> If your data is very valuable you should clone your drive first (using  dd maybe) and then play with Testdisk.
Testdisk is very powerful but it helps if you have used it before, so  practicing on your valuable data is not a good idea.
I once used it to recover my XP partitions but I was sweating while I  did it!
Same here but testdisk worked great. The best cd's that I've seen are puppy unlimited and hirens bootcd for testdisk

---

