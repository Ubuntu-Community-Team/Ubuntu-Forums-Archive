---
title: "Error when creating startup disk"
date: 2010-09-30
forum: General Help
---

### Post by lamb123 on 2010-09-30
org.freedesktop.UDisks.Error.Failed: Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdb, start=0, size=1032978432, type=0x0c
Entering MS-DOS parser (offset=0, size=1032978432)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed


This is on ubuntu 10.10 but also i get error on 10.04. Also when I enter USB stick ubuntu doesnt create desktop icon for it. I dont know where i can browse the folder.

This problem came after I tried creating startup desk before and elected to Erase disk. Then it gave me some error and since then it doesnt seem to be working.

Thanks!

---

### Post by searchfgold6789 on 2010-09-30
It looks like it is overflowing a partition.
Have you checked to see if your thumb drive has enough space for the disk you're trying to create?

---

### Post by lamb123 on 2010-09-30
> **searchfgold6789 said:**
> It looks like it is overflowing a partition.
Have you checked to see if your thumb drive has enough space for the disk you're trying to create?

this error happens when I choose "Erase Disk".

[IMG]http://ubuntuone.com/p/I5k/[/IMG]

---

### Post by C.S.Cameron on 2010-09-30
It does not look like you have selected an iso or CD to install the O/S from.

---

### Post by lamb123 on 2010-09-30
> **C.S.Cameron said:**
> It does not look like you have selected an iso or CD to install the O/S from.

I am aware of that (download in progress now) but I dont think it affects Erase Disk option?

Edit: tried now with ISO and still same error.

---

### Post by lamb123 on 2010-10-01
got help from this thread.

[http://ubuntuforums.org/showthread.php?t=534502](http://ubuntuforums.org/showthread.php?t=534502)

Yay!

---

