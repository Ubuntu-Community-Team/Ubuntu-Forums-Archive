---
title: "NTFS partition resize error in Gparted"
date: 2011-08-15
forum: General Help
---

### Post by editheraven on 2011-08-15
I am trying to make all ntfs partitions ext4. So i'm moving data from ntfs to other locations and shrink ntfs to free space, create in unallocated space ext4, move more data, shrink etc. But, after the first data move, i can't shrink the ntfs partition to create freespace on partition table.

Here is the log

```

GParted 0.7.0 --enable-libparted-dmraid
 Libparted 2.3
    **Shrink /dev/sdb5 from 288.83 GiB to 200.19 GiB**  00:02:59    ( ERROR )             calibrate /dev/sdb5  00:00:00    ( SUCCESS )             [I]path: /dev/sdb5
start: 16128
end: 605746889
size: 605730762 (288.83 GiB)[/I]          check file system on /dev/sdb5 for errors and (if possible) fix them  00:00:03    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sdb5***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 310134149632 bytes (310135 MB)
Current device size: 310134150144 bytes (310135 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 214955 MB (69.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    286628 MB             0
Multi-Record       :    308365 MB         44118
$MFTMirr           :         1 MB             1
Sparse             :    256380 MB          2681
Ordinary           :    308036 MB         49605
You might resize at 214954790912 bytes or 214955 MB (freeing 95180 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             shrink file system  00:02:52    ( ERROR )             run simulation  00:02:52    ( ERROR )             ***ntfsresize -P --force /dev/sdb5 -s 214955065343 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 310134149632 bytes (310135 MB)
Current device size: 310134150144 bytes (310135 MB)
New volume size    : 214955057664 bytes (214956 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 214955 MB (69.3%)
Collecting resizing constraints ...
Needed relocations : 13644118 (55887 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1472 > 1024), not yet supported!
Please try to free less space.
[/I]                check file system on /dev/sdb5 for errors and (if possible) fix them  00:00:03    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sdb5***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 310134149632 bytes (310135 MB)
Current device size: 310134150144 bytes (310135 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 214955 MB (69.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    286628 MB             0
Multi-Record       :    308365 MB         44118
$MFTMirr           :         1 MB             1
Sparse             :    256380 MB          2681
Ordinary           :    308036 MB         49605
You might resize at 214954790912 bytes or 214955 MB (freeing 95180 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             grow file system to fill the partition  00:00:01    ( SUCCESS )             run simulation  00:00:01    ( SUCCESS )             ***ntfsresize -P --force /dev/sdb5 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 310134149632 bytes (310135 MB)
Current device size: 310134150144 bytes (310135 MB)
New volume size    : 310134145536 bytes (310135 MB)
Nothing to do: NTFS volume size is already OK.
[/I]             real resize  00:00:00    ( SUCCESS )             ***ntfsresize -P --force /dev/sdb5***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sdb5
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 310134149632 bytes (310135 MB)
Current device size: 310134150144 bytes (310135 MB)
New volume size    : 310134145536 bytes (310135 MB)
Nothing to do: NTFS volume size is already OK.
[/I]                ========================================
```

---

### Post by TeoBigusGeekus on 2011-08-15
Can you post us a screenshot of the partitions in gparted, as well as the name of the partition you want to shrink?

---

### Post by editheraven on 2011-08-15
Here is the screenshot

[http://imageshack.us/photo/my-images/692/screenshotbss.png/](http://imageshack.us/photo/my-images/692/screenshotbss.png/)

In windows, the partition is called "Muzica"

---

### Post by TeoBigusGeekus on 2011-08-15
Try this: before resizing sdb5 (Muzica), move it after sdb7 and before your last unallocated space.

---

### Post by editheraven on 2011-08-15
I guess moving sdb5 involves moving sdb6 data also. But i can't move it (even gparted doesn't let me) because there is no freespace on partition table to move sdb6 on.

---

### Post by TeoBigusGeekus on 2011-08-15
Hmm...
What about copying all data from sdb7 to sdb5 and deleting sdb7?
Would that give gparted some space to operate on?
(Assuming of course that you want sdb7 deleted.)

---

### Post by editheraven on 2011-08-15
Well i don't have enough space anyware for that but :D You gave me an idea so i selected shrinking to leave some free space on sdb5 (not shrinking to all free space) and now it's working. Thanks. I'm selecting [solved] for this thread. Have a nice day.

---

### Post by TeoBigusGeekus on 2011-08-15
Cool. Glad you've sorted it out.

---

