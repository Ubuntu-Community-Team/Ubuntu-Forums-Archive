---
title: "Find NTFS signature on hard drive?"
date: 2009-08-21
forum: General Help
---

### Post by Yossi Gil on 2009-08-21
Is there a utility that will look for the NTFS signature on my hard drive? I suspect that for some reason, the partition boundary has changed, and now, I cannot access my NTFS partition. Booting a Windows XP does not help either...

The reason I suspect this is that the partition used to be 62 GB, and is now only 59GB.

Here is some background:

I do not seem to be able to use both Ubuntu and Windows on the same machine.
After re-installing windows, I lost the Ubuntu boot. I used a live CD to recover Ubuntu
fixing the Grub boot sequence, but now, I cannot access my NTFS file system.
upon [FONT=Courier New]sudo mount -t ntfs /dev/sda1 /media/test[/FONT]
I get
[FONT=Courier New]Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/FONT]

trying mounting with ntfs-3g does not help either, that is,[FONT=Courier New] sudo mount -t ntfs-3g /dev/sda1 /media/test[/FONT] gives: 

[FONT=Courier New]Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/FONT]


checking my file system using fdisk I get:

[FONT=Courier New]Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa7fb66ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             917        9044    61440000    7  HPFS/NTFS
/dev/sda2   *        9045       12379    25212600   83  Linux
/dev/sda3           12380       12921     4097520   82  Linux swap / Solaris
[/FONT]

---

### Post by vinnywright on 2009-08-21
can you boot windows?

VINNY

---

### Post by Yossi Gil on 2009-08-21
No. I cannot boot Windows.
If I use a Windows XP boot disk, it does not see my windows partition.

Yes, I know I should not be using windows. I just want my files and forget about Windows...

---

### Post by vinnywright on 2009-08-21
O hell I keep XP on my box to....................I think sence it all seams new I'd just back up as mutch as I could get and then start from scratch.

use a gparted live cd and remove all the partitions so you have one big unalocated space.

then make a NTFS partition first at the begining of the drive.

then a ext3 of about 10-15Gig for ubuntu (or more if you have the space.)
then some linux swap

then split up the rest for /home (ext3) and some Vfat storage that windows can get to :)

now install XP first then ubuntu and you should be good.

hears some guides
[Top 20 Kubuntu FAQs & Answers]("http://kubuntuforums.net/forums/index.php?topic=3099811.0") 

#4 and #5 and #3 

if thats not an option wate for mor replys :)

VINNY

---

### Post by BitJunkie on 2009-08-21
Take look at Testdisk from cgsecurity.org. I've used it to recover partitions before.

---

### Post by Yossi Gil on 2009-08-22
Yes, testdisk seems to be able to see something, but not everything.
The problem as I see it boils down to the number of heads, which is 240
according to the partition table, but 255 on the disk.

Any idea why Ubunut messed up that value?

---

### Post by Yossi Gil on 2009-08-22
The problem seems to be related to the geometry problem reported here:

[http://ubuntuforums.org/showthread.php?t=879932](http://ubuntuforums.org/showthread.php?t=879932)

but, then, why did my NTFS partition disappear?

---

