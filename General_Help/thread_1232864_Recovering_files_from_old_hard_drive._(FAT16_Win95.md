---
title: "Recovering files from old hard drive. (FAT16 Win95)"
date: 2009-08-06
forum: General Help
---

### Post by CuzItsThaThrilla on 2009-08-06
Hello, I would like some help on this issue.

This computer I'm working on is about ten years old. There are no USB ports, theres nothing really easy or convenient about getting data off of it besides a floppy disk... But those only hold about 3MB at a time and I have around 500MB of stuff on this :|

So I figured I would take out the hard drive, put it in a faster computer, and get Ubuntu Live running on it to pull the files. Usually devices are detected, and from there I can just put in something like a USB stick to grab information.

Well, thats not so much the case here. Using GParted, the app can see the hard drive, and even says it's mounted... But I cannot retrieve any data.

The hard drive is FAT16, and runs Windows 95 on it. There are no admin passwords or anything like that really on it... How else would I go about this?

---

### Post by CuzItsThaThrilla on 2009-08-06
Oops, forgot to post this as well:

```
ubuntu@ubuntu:~$ sudo /sbin/sfdisk -l /dev/hda

Disk /dev/hda: 14475 cylinders, 15 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 14475/15/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+    260     261-   2096451    6  FAT16
/dev/hda2        261     849     589    4731142+   5  Extended
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5        261+    521     261-   2096451    6  FAT16
/dev/hda6        522+    782     261-   2096451    6  FAT16
/dev/hda7        783+    849      67-    538146    6  FAT16

```

---

### Post by Chrus on 2009-08-06
Linux and FAT dont play well together.

I think your on the right track with putting the drive into a newer machine, but your gonna have to use windows. [BartPE]("http://www.nu2.nu/pebuilder/") is a windows live cd. Burn that do disk, boot it up, and you should be able to access your HDD from there and copy stuff to a USB drive.

---

### Post by CuzItsThaThrilla on 2009-08-06
Oh man, this guide worked AMAZING WONDERS for me! Google found this somewhere:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

For anyone else interested.

---

### Post by prshah on 2009-08-06
> **CuzItsThaThrilla said:**
> 
Disk /dev/hda: 14475 cylinders, 15 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 14475/15/63).


You disk geometry is being reported differently from what it was when it was setup. Usually, that means that you either were not using LBA then, or are not using it now.

Changing LBA (Logical Block Addressing) settings will require you to fiddle with your BIOS. Also, I'm not sure how it will affect your existing hard drives.

You can [manually pass the geometry as a boot parameter]("http://ubuntuforums.org/showpost.php?p=1397855&postcount=3") but again I'm not sure how it will work out.

In your place, I'd probably use a USB HDD enclosure (if you have easy access to one). 

FAT in all it's forms works great with Linux, so there's no beef there.

---

### Post by CuzItsThaThrilla on 2009-08-06
Yea, the guy who made this for me (before I knew all I know today, which probably isn't a whole lot... But still!) set up a few partitions and had the BIOS going his own way, for "my own security" as he put. I was only having trouble with that particular tower... I even tried putting in a cd writer to make things not so hectic, but then it couldn't see the hard drive. Thats why I put it in a different computer than that. Plus, Linux really does give you that admin edge.

I have files copying now, though, through that guide. I'll just be mounting the partitions as needed, and when I'm all done just switch out the drives again and be on my merry way. :)

---

