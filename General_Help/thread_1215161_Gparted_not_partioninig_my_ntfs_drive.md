---
title: "Gparted not partioninig my ntfs drive"
date: 2009-07-16
forum: General Help
---

### Post by mishnogramjo on 2009-07-16
Hello,

I am running XP home and Ubuntu 9.04 on dual boot but of course, when I was installing ubuntu, I set aside way too littlle room, now I am out of room on my ubuntu partition.  I used gparted to try to expand my partition, used live CD and everything, unmounted all drives, freed up space on my ntfs drive and expanded my ubuntu partion, it checks it as alright but when going to perform the actual partioning and resizing, it stops and gives an error message instead.:confused:

I am including the saved error file.  Any help on how to get around this would be greatly appreciated.  As it stands, I cant do anything.  BTW, I am using a Dell Inspiron 1300 with XP home on the ntfs drive.

GParted 0.4.3
 Libparted 1.8.8
    **Shrink /dev/sda2 from 68.98 GiB to 58.22 GiB**  00:00:26    ( ERROR )             calibrate /dev/sda2  00:00:00    ( SUCCESS )             [I]path: /dev/sda2
start: 96390
end: 144761714
size: 144665325 (68.98 GiB)[/I]          calculate new size and position of /dev/sda2  00:00:00    ( SUCCESS )             [I]requested start: 96390
requested end: 122190389
requested size: 122094000 (58.22 GiB)[/I]       [I]new start: 96390
new end: 122190389
new size: 122094000 (58.22 GiB)[/I]          check file system on /dev/sda2 for errors and (if possible) fix them  00:00:06    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda2***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 74068640256 bytes (74069 MB)
Current device size: 74068646400 bytes (74069 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 46084 MB (62.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :     11843 MB             0
Multi-Record       :     73071 MB         96216
$MFTMirr           :     16780 MB             1
Compressed         :     72944 MB         75415
Ordinary           :     73050 MB         23157
You might resize at 46083694592 bytes or 46084 MB (freeing 27985 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             shrink file system  00:00:12    ( ERROR )             run simulation  00:00:12    ( ERROR )             ***ntfsresize -P --force /dev/sda2 -s 62512127999 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 74068640256 bytes (74069 MB)
Current device size: 74068646400 bytes (74069 MB)
New volume size    : 62512120320 bytes (62513 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 46084 MB (62.2%)
Collecting resizing constraints ...
Needed relocations : 1025267 (4200 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1048 > 1024), not yet supported!
Please try to free less space.
[/I]                check file system on /dev/sda2 for errors and (if possible) fix them  00:00:07    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda2***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 74068640256 bytes (74069 MB)
Current device size: 74068646400 bytes (74069 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 46084 MB (62.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :     11843 MB             0
Multi-Record       :     73071 MB         96216
$MFTMirr           :     16780 MB             1
Compressed         :     72944 MB         75415
Ordinary           :     73050 MB         23157
You might resize at 46083694592 bytes or 46084 MB (freeing 27985 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             grow file system to fill the partition  00:00:01    ( SUCCESS )             run simulation  00:00:01    ( SUCCESS )             ***ntfsresize -P --force /dev/sda2 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 74068640256 bytes (74069 MB)
Current device size: 74068646400 bytes (74069 MB)
New volume size    : 74068640256 bytes (74069 MB)
Nothing to do: NTFS volume size is already OK.
[/I]             real resize  00:00:00    ( SUCCESS )             ***ntfsresize -P --force /dev/sda2***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 74068640256 bytes (74069 MB)
Current device size: 74068646400 bytes (74069 MB)
New volume size    : 74068640256 bytes (74069 MB)
Nothing to do: NTFS volume size is already OK.
[/I]                ========================================
    **Move /dev/sda4 to the left and grow it from 2.50 GiB to 13.26 GiB**    ========================================
    **Move /dev/sda5 to the left and grow it from 2.33 GiB to 4.95 GiB**    ========================================
    **Grow /dev/sda5 from 4.95 GiB to 13.09 GiB**    ========================================

---

### Post by merlinus on 2009-07-16
Post a screenshot.

---

### Post by c0mput3r_n3rD on 2009-07-16
One of the horrible things about winblows is that it doesn't keep track of it files on the disk.  Therefore, you can not take away space of it's partition with out losing information, therefore you can't resize the partition (I'm pretty sure).  I would suggest deleting the Ubuntu partition, running a disk defragmenter (a few times cause winblows REALLY sucks at managing it's file) and then reinstalling Ubuntu.

** MAKE SURE YOU RUN DISK DEFRAGMENTER A FEW TIMES!!!   IT REALLY FRICKIN SUCKS AT MANAGING IT'S FILES!!!! ***

---

### Post by mishnogramjo on 2009-07-16
> **c0mput3r_n3rD said:**
> One of the horrible things about winblows is that it doesn't keep track of it files on the disk.  Therefore, you can not take away space of it's partition with out losing information, therefore you can't resize the partition (I'm pretty sure).  I would suggest deleting the Ubuntu partition, running a disk defragmenter (a few times cause winblows REALLY sucks at managing it's file) and then reinstalling Ubuntu.

** MAKE SURE YOU RUN DISK DEFRAGMENTER A FEW TIMES!!!   IT REALLY FRICKIN SUCKS AT MANAGING IT'S FILES!!!! ***

That did the trick.  Oh so tempted to just remove xp from this machine.  If I didn't like Adobe CS3 so much, I would make the switch.

Thanks for the help.

---

