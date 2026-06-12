---
title: "NTFS partition won't resize, recieving &quot;Nothing to do&quot;  error"
date: 2009-12-23
forum: General Help
---

### Post by theyain on 2009-12-23
I'm trying to resize an ntfs partition (through gparted) for my grandfather so that Ubuntu has more room, however I keep getting an error.


Here is a log of one of the runs.  The error is near the bottom, highlighted in bold.
```

GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Shrink /dev/sda2 from 94.03 GiB to 76.35 GiB  00:00:56    ( ERROR )
     	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
     	
path: /dev/sda2
start: 63
end: 197197874
size: 197197812 (94.03 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:16    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 100965274112 bytes (100966 MB)
Current device size: 100965279744 bytes (100966 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 59193 MB (58.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 19217 MB 0
Multi-Record : 100962 MB 121376
$MFTMirr : 19217 MB 1
Compressed : 100901 MB 12809
Sparse : 99634 MB 38515
Ordinary : 100963 MB 110530
You might resize at 59192967168 bytes or 59193 MB (freeing 41773 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:00:25    ( ERROR )
     	
run simulation  00:00:25    ( ERROR )
     	
ntfsresize -P --force /dev/sda2 -s 81981333503 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 100965274112 bytes (100966 MB)
Current device size: 100965279744 bytes (100966 MB)
New volume size : 81981325824 bytes (81982 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 59193 MB (58.6%)
Collecting resizing constraints ...
Needed relocations : 1334919 (5468 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1432 > 1024), not yet supported!
Please try to free less space.
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:14    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 100965274112 bytes (100966 MB)
Current device size: 100965279744 bytes (100966 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 59193 MB (58.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 19217 MB 0
Multi-Record : 100962 MB 121376
$MFTMirr : 19217 MB 1
Compressed : 100901 MB 12809
Sparse : 99634 MB 38515
Ordinary : 100963 MB 110530
You might resize at 59192967168 bytes or 59193 MB (freeing 41773 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:01    ( SUCCESS )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda2 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 100965274112 bytes (100966 MB)
Current device size: 100965279744 bytes (100966 MB)
New volume size : 100965274112 bytes (100966 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:01    ( SUCCESS )
     	
[b]ntfsresize -P --force /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 100965274112 bytes (100966 MB)
Current device size: 100965279744 bytes (100966 MB)
New volume size : 100965274112 bytes (100966 MB)
Nothing to do: NTFS volume size is already OK.
[/b]
```

Anyone got an idea of what to do?

---

### Post by houseworkshy on 2009-12-23
If it's a windows partition it may be easier to use the disc manager from windows.

---

### Post by theyain on 2009-12-23
Resizing the partition while its mounted is a horrible idea, as that can and will (from personal experience) cause fs damage.

---

### Post by houseworkshy on 2009-12-23
Trust the above post as I am not expert and may have been fortunate when I followed this guide [http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

---

### Post by houseworkshy on 2010-01-02
Will you please tell me what happend.  It has been niggling at me all through Christmas.  If I've passed bad advice along please tell me.  I am a novice who discovered to his suprise that he could answer some of the very basic questions and was delighted at the opportunity to give back a little.  If I'm blowing up peoples machines or something then I'll just hold back untill I know more.

Also sorry about missing the fact that the post I told you to trust before mine was in fact from you.  I'd been online too long I think.  Well at least I know that you won't have taken my advise and destroyed your system, which is a releif.  The advice I passed on was from a video blog which is now weekly and a fair % of my limited knowlage comes from it.  If it's not sound I would like to know.  Probably others would too as it increasing popular.

Happy new year.

---

