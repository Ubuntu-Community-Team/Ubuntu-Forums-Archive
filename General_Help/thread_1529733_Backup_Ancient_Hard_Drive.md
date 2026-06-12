---
title: "Backup Ancient Hard Drive"
date: 2010-07-12
forum: General Help
---

### Post by Donner87 on 2010-07-12
I have a very old HD:
SEAGATE ST1144A 130MB 3.5"/HH IDE/AT drive
It's from a 386 machine, and I wanted to pull all the files off of it. Naturally I hooked it up to my Ubuntu box, but so far I have not been able to mount it, or even dd it. Mount wants to know the filesystem. When I try vfat, it says it can't read the boot sector. When I try to make an ISO using dd, dd says it copies 0 bytes.

Any ideas how I can read data off this bad boy? If I put the drive back into the 386 it boots just fine, so I know the HD is working. hdparams gives info on the drive, so the OS at least sees it.

EDIT: Oh yeah, the drive has MS-DOS 4.01 installed on it, in case that gives clues as to its filesystem/partition table.

---

### Post by louieb on 2010-07-12
Just wondering did you run** fdisk -l **when it was plugged in? Does it show any partitions? It may or may not have any. 

It is possible that it is formatted like a giant floppy disk.

Please  post the dd command you used? and the mount command too?

A good start would be to plug it in and post the output of 

```
sudo fdisk -l
``` lower case L at the end

---

### Post by Donner87 on 2010-07-13
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020a07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60052   482361344   83  Linux
/dev/sda2           60052       60802     6023169    5  Extended
/dev/sda5           60052       60802     6023168   82  Linux swap / Solaris
```
Obviously that's just my primary drive. It doesn't list anything for /dev/sdb, which is the ancient drive.

And here's the part of syslog pertaining to sdb:
```
Jul 13 17:14:52 ubuntu-slave kernel: [    1.842783] sd 6:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
Jul 13 17:14:52 ubuntu-slave kernel: [    1.842832] sd 6:0:0:0: [sdb] Write Protect is off
Jul 13 17:14:52 ubuntu-slave kernel: [    1.842835] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jul 13 17:14:52 ubuntu-slave kernel: [    1.842859] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jul 13 17:14:52 ubuntu-slave kernel: [    1.843096] sd 6:0:0:0: [sdb] Attached SCSI disk
```

---

### Post by oldfred on 2010-07-13
What do you see in BIOS? BIOS may be trying to make it LBA and those old drives you had to manually set cylinders, heads, sectors from the label on the hard drive.

---

### Post by Donner87 on 2010-07-13
The BIOS has everything set to AUTO for that drive. The HD has no label on it except for the model number (ST1144A). I'm not familiar with the various modes for hard drives. What mode should this Hard Drive be in and such? [Here is a link with specs]("http://stason.org/TULARC/pc/hard-drives-hdd/seagate/ST1144A-32-130MB-3-5-HH-IDE-AT.html")

---

### Post by Schrute Farms on 2010-07-13
The specs show your info in the upper corner:  Cylinders: 1024, Heads: 14, Sec/Track: 17.  Anything else you need to know should be there.

Also, this drive is old enough that you need to manually set the drive as the slave.  On the end of the drive, by the data plugin  (opposite side of the power plug), you should see some little jumpers.  There are 2 sets of pins controling master/slave.  The pins furthest away from the data connector are #1 & 2.  The next two rows are what you want to look at.  Pull any jumpers off of 3/4 and 5/6 and you should be set to slave.

Hope that helps.

---

### Post by Donner87 on 2010-07-13
Thank you for the reply.

I've tried various settings with CHS, but all of them make the drive disappear from Linux completely (it's not listed in /dev). If I put it back on LBA or AUTO then it shows up, albeit back to being useless.

The primary drive is on SATA, so I have this ancient one set to master on its own IDE cable.

---

### Post by CharlesA on 2010-07-13
Suggestion would be to throw it in a machine that has a IDE drive as the main drive and hook it up as a slave and see what happens.

---

### Post by louieb on 2010-07-14
Sounds like you have done most of the things i would try.

Look at the BIOS setting on the PC in which it works. Do they match what you are using on the other PC? 

 I did find the drive on the Seagate site. lol - it was copyrighted almost 20 years ago. 

Even Seagate is not sure
> 
[FONT=Letter Gothic Line, MS LineDraw][SIZE=-1]ALSO, CHECK TO SEE IF YOUR CMOS SETUP HAS A "CUSTOM" OR "USER DEFINABLE" DRIVE TYPE AVAILABLE. (see below)

Possible translation:  1001 cyl, 15 heads, 17 sectors = 130,690,560
Possible translation:  1024 cyl, 14 heads, 17 sectors = 124,780,544
[/SIZE][/FONT]
Look at the [Tech specs tab here]("http://www.seagate.com/ww/v/index.jsp?name=Legacy&vgnextoid=ef83c6ea20fbd010VgnVCM100000dd04090aRCRD&locale=en-US&reqPage=Legacy#")

The drive is old enough - it probably does not have LBA - the the mode probably should be set to CHS or Auto.

---

