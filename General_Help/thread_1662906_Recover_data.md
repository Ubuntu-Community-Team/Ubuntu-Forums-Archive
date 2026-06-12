---
title: "Recover data"
date: 2011-01-08
forum: General Help
---

### Post by Howy on 2011-01-08
I was just messing with a Windows XP installation disk when i think it wiped my whole SDA disk!
It shows up as unallocated from a Live DVD, and with an error sign.
Is there any way to recover it? PLEASE HELP!!!!
Its where i store all my files!

---

### Post by jeicrash on 2011-01-08
Please define "messing around" if you initiated the install process and it got to the partition / format section (Which does warn you before proceeding) Your going to need to do some foot work to get back your data. 

First and most important DO NOT do anything more with the drive, disconnect if it needed. This will ensure nothing is changed.

I'll assume you have access to another machine since your posting here. So next try to download a live-cd with recovery software. There are a lot of them. F.C.C.U, Katana, etc.

You will need another drive of equal or larger size to recover data to as well.

I will check back to see if you have posted back before continuing further.

---

### Post by Howy on 2011-01-09
I do have access to a different computer, but i dont have a drive as large as my main one.
I only have a 232Gb one, but i could acquire a larger one somehow.
I did get to a part where it asked whether i wanted to delete my existing windows installation or not, but i didnt do anything. (I was trying to repair my installation.)
Drive is untouched. I won't do anything with it. And, does a live DVD for Lucid help any or do i need one of those you suggested?

---

### Post by halj32 on 2011-01-09
you need to use something like SystemRescueCD 
goodluck

---

### Post by Howy on 2011-01-09
So, the Lucid-disc is useless for this, but i need one of those?

I read about something called ddrescue. It says that it will image the whole harddrive s long as you specify the location of the device. The same site mentioned PhotoRec, which i have tried before, and it recovered all i wanted from my phone once.

The windows installation attempted to write MBR to a NTFS partition that i put on the beginning, but it wasnt sda1 when doing so. Could this be the culprit?

Im ready to get some instructions.(What to download, etc)

OK, THIS IS F'N SICK! MY PARTITIONS ARE BACK FROM THE DEAD!!!
They just appeared on my LiveDVD, and i have no friggin' idea what made them appear. Possibly some temporary disable or something.
But the partition table seems broken. It doesn't show the partitions correctly in GParted. (Shows as unallocated) But the files are 100% there, as if nothing happened.
So, is there any way to rebuild the partition table?

---

### Post by jerrrys on 2011-01-09
if you need to recover a partition then testdisk has worked fast and painless for me

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Howy on 2011-01-09
Ok, i need some help fixing the partition table. The drive shows up with more storage than it has. Its mainly at 1Tb, but it shows an additional partition that is corrupted.
Also, my system is gone. But no worries, i backed it up some hours before the accident, with all system files included.
So, how do i fix the partition table?
I remember that i had sda1, which was for backup. Its there. But now it shows my other partitions outside the Extended that i made above them. (GParted warns about that overlapping partitions arent supported.)
Im worried that i mght have to repartition it all. But all the data i want fits onto the harddrivd that i have :)
Ill have to do that if no other way is possible. But I'll know that my files are safe.

If it helps, here is the partition table at the moment:
```
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000599b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5120000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             638       30728   241693696   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           30728      121602   729946113    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           60801      120994   483497984   83  Linux
Partition 4 does not end on cylinder boundary.
/dev/sda5   *       30728       59577   231734272   83  Linux
/dev/sda6           59577       60801     9825280   82  Linux swap / Solaris
/dev/sda7          120994      121602     4881408    7  HPFS/NTFS


```This one shows up correctly. The one in Disk Utility shows up completely out of order with corruption.
But, i see that those errors need to be fixed somehow, and i want to destroy those NTFS-partitions for good. (I hate them... :evil: ) But i cant do it from GParted or Disk Utility, it shows up with this error:
```
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=1048576
Entering MS-DOS parser (offset=0, size=1000204886016)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 5242880000, type 0x07)
new part entry
looking at part 1 (offset 5243928576, size 247494344704, type 0x83)
new part entry
looking at part 2 (offset 252739320832, size 747464819712, type 0x05)
Entering MS-DOS extended parser (offset=252739320832, size=747464819712)
readfrom = 252739320832
MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 3 (offset 500102594560, size 495101935616, type 0x83)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
Error: Can't have overlapping partitions.
ped_disk_new() failed

```Does this mean a full reformat?
Just a question... is it possible to boot from a system where i have backed up all folders except /sys and /dev? That's what i did because i know they contain block devices and not just files. Would i be able to put them on a partition, fix the MBR and get it to boot normally?
If i can't, i'll have a great amount of installations and modifications to do.

---

### Post by jeicrash on 2011-01-09
As mentioned above Testdisk is a very useful tool and can restore those corrupted partitions. On Testdisk website you will find a link of live cd's that include testdisk.

Since the drive is 1tb and you have nowhere to back it up to dd and ddrescue will be of very little use to you. However if say you are only using 200gb or so you could use something like clonezilla to backup only the used data. There are command line only tools but for simplicity sake a gui with menu's can sometimes save lots of headache which is why I am recommending clonezilla.

Check Testdisk's website and read through it first. Post back if you get stuck, also let us know if it was successful. Here is a step by step guide from CGSecurity (Whos hosts testdisk).
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

