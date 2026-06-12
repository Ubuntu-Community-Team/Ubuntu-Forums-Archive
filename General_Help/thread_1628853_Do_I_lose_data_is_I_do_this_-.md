---
title: "Do I lose data is I do this -"
date: 2010-11-23
forum: General Help
---

### Post by listerdl on 2010-11-23
I have an external 1TB Hard Drive which is all formatted in either NFATS or NTFS (I forget which) - in any event it is configured to work with a windows machine to store data.

I would like to make an image of my ubuntu partition/boot.

If I pull out a copy of GParted and create a ext4 partition on that 1TB drive, will I enter a world of pain and lose all that data?

Thanks!

---

### Post by lmarmisa on 2010-11-23
Consider to use [Clonezilla Live]("http://www.clonezilla.org/"). Clonezilla allows you both to clone your partition or make a backup of it (image). I recommend the second option storing the image files in a NTFS filesystem.

---

### Post by listerdl on 2010-11-23
ok thanks for that - but what about actually creating a partition to accommodate for ext4?

---

### Post by lmarmisa on 2010-11-23
Gparted is a very useful tool. No problem if you shrink the NTFS (ot FAT) partition and then you define a second partition of type EXT4 using the unused space.

---

### Post by TeoBigusGeekus on 2010-11-23
I haven't tried it, but why not?
Make sure you defragment the drive 3 or 4 times from windows before you create the partition.
Make also sure that you don't interrupt gparted for any reason once it's started. I pressed cancel once while it was running and I lost half a terra of data.

---

### Post by listerdl on 2010-11-23
> **TeoBigusGeekus said:**
> 
Make sure you defragment the drive 3 or 4 times from windows before you create the partition.

That is v good advice thanks

---

### Post by psavva on 2010-11-23
> **listerdl said:**
> I have an external 1TB Hard Drive which is all formatted in either NFATS or NTFS (I forget which) - in any event it is configured to work with a windows machine to store data.

I would like to make an image of my ubuntu partition/boot.

If I pull out a copy of GParted and create a ext4 partition on that 1TB drive, will I enter a world of pain and lose all that data?

Thanks!

Seriously, Backup your data first!!!!

I would rather spend an extra 100 Euro on a new 2 TB hard Drive, and backup my work, rather than risk loosing data.

---

### Post by QLee on 2010-11-23
[QUOTE=listerdl]I have an external 1TB Hard Drive which is all formatted in either NFATS or NTFS (I forget which) - in any event it is configured to work with a windows machine to store data.
...
If I pull out a copy of GParted and create a ext4 partition on that 1TB drive, will I enter a world of pain and lose all that data?
...[/QUOTE]
If I was going to attempt this on my system, I believe I would choose Windows to shrink the native Windows volume (partition) but of course the choice is yours to make. With a good backup all you risk is time required to restore. "World of pain" or opportunity to learn, might be a matter of opinion and, if you make a mistake, we can all learn from it, faster than searching the forum for relevant threads.

---

### Post by nolag on 2010-11-23
> **QLee said:**
> If I was going to attempt this on my system, I believe I would choose Windows to shrink the native Windows volume (partition) but of course the choice is yours to make. With a good backup all you risk is time required to restore. "World of pain" or opportunity to learn, might be a matter of opinion and, if you make a mistake, we can all learn from it, faster than searching the forum for relevant threads.
 
To be hounest the only time I have seen a difference is when the partition is bootable.  If not then any resizing tool should work.  I have one suggestion, don't backup with a disk image.  I used to do it but it takes a LOT of space and time for no reason.  Also it does not support incremental backups.  The only advantage it can have is it can be bootable.

---

### Post by QLee on 2010-11-23
[QUOTE=nolag]To be hounest the only time I have seen a difference is when the partition is bootable. ...[/QUOTE]
Ever seen a Windows "dynamic disk".

---

