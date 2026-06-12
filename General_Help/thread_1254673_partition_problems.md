---
title: "partition problems"
date: 2009-08-31
forum: General Help
---

### Post by thundaraptor on 2009-08-31
I have  a 1 TB hdd.  About a month ago I partitioned it out to 975 and 25 gb with different versions of ubuntu on each partition and was booting to whichever i wanted via the grub.  Eventually I deleted our the "randr" in the ubuntu that was on the 975 partition and that pretty much destroyed that system.  I copied out all the relevant data from the 975 partition and reformatted it and have been using the jaunty 64 setup on the 25 gb partition.  now, i want to use the 975 as my main data sink thereby separating the OS partition from my media library.  The 975 gb partition has some issues. 

(1) I can't write to it from inside the ubuntu on the 25 partition.  
(2) It has a directory called "lost and found" that I don't understand 
(3) It is listed as 963gb but a properties click shows that it has only 836gb free and 45gb used, which clearly does not add to the 963gb that it should be closer to.  

Any ideas?

---

### Post by tgeer43 on 2009-08-31
> (1) I can't write to it from inside the ubuntu on the 25 partition.You may need to take ownership of the 975GB partition. Let's assume that the partition is /sda1 and your username is poindexter. The correct command would be:
```
sudo chown poindexter /dev/sda1
```> (2) It has a directory called "lost and found" that I don't understandWhen the File System Checker (fsck) runs, if it detects problems on the drive it will put corrupted and recovered files in this directory. Unless it's got a bunch of stuff in it, you can disregard it.
> (3) It is listed as 963gb but a properties click shows that it has only 836gb free and 45gb used, which clearly does not add to the 963gb that it should be closer to.Another one not to worry too much about. Programs and utilities use different methods for calculating MB and GB and there is also system overhead that some apps report and others ignore.

**_NOTE_:** Before you change the ownership of the drive, post the contents of your /etc/fstab file here so we can make sure that it is currently being mounted properly (not read-only).

tgeer

---

### Post by earthpigg on 2009-08-31
a solution that is much easier and may work just as well as the solution above:

boot from a live cd.

run gparted.

delete the 975gig partition.

create a new 975 gig partition.

---

### Post by tgeer43 on 2009-08-31
> **earthpigg said:**
> a solution that is much easier and may work just as well as the solution above:

boot from a live cd.

run gparted.

delete the 975gig partition.

create a new 975 gig partition.

I'm sure that will work as well but as far as booting the Live CD and performing gparted operations being easier than entering a single command in the console... I disagree.

tgeer

---

### Post by thundaraptor on 2009-08-31
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=60d23ba3-e0a7-4f9a-9043-5ec954d2c5be /               ext2    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=822ea3c2-e13c-48ad-a8e5-5211de908d07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Is the fstab output.  I am comfortable with the terminal or gparted but not an ubuntu master or anything.

---

### Post by tgeer43 on 2009-08-31
fstab looks ok.

tgeer

---

### Post by thundaraptor on 2009-09-01
I deleted the partition and created a new one.  Still not working but did notice in the properties dialogue window that the system says I don't own the volume so I can't write to it.  Any ideas?

---

### Post by tgeer43 on 2009-09-01
I already answered that in post #2.
Go back and re-read it.

tgeer

---

### Post by thundaraptor on 2009-09-01
Yes I did that but still cannot use the drive.  If I try to copy any random pdf into the large partition error message says I don't have permission.  is this a chmod thing?  Could this be related to residual interference from the other ubuntu sleeves that I have installed?  browsing through my terminal I can see that there is still some file structures for a hardy heron install that I have.  could this be resolved via the grub?  thanks for your posts however.  TR

---

### Post by plucky on 2009-09-01
> **thundaraptor said:**
> Yes I did that but still cannot use the drive.  If I try to copy any random pdf into the large partition error message says I don't have permission.  is this a chmod thing?  Could this be related to residual interference from the other ubuntu sleeves that I have installed?  browsing through my terminal I can see that there is still some file structures for a hardy heron install that I have.  could this be resolved via the grub?  thanks for your posts however.  TR

See this link for [Mounting a linux partition](http://www.psychocats.net/ubuntu/mountlinux) 
Adapt to your requirements...

How did you actually mount the partition as it is not in your fstab file?

Please post output of ```
sudo fdisk -l
``` that is lowercase L not a 1


Good Luck

---

### Post by thundaraptor on 2009-09-01
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e7930

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3368      120238   938766307+  83  Linux
/dev/sda2          120239      121601    10948297+   5  Extended
/dev/sda3               1        3367    27045396   83  Linux
/dev/sda5          120239      121601    10948266   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    c  W95 FAT32 (LBA)

```

---

