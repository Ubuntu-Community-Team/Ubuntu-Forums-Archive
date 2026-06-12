---
title: "How to make a new/increase size of an NTFS partition by shrinking an EXT4?"
date: 2010-09-08
forum: General Help
---

### Post by Edgewalker_001 on 2010-09-08
I have nearly 200GB of space free on the HD with my linux main EXT4 partition, and I'm wondering if I can convert a large part of this to a new NTFS partition that I can use for my windows XP paralell install?

Basically, what do I have to do to resize and create the new partition and how do I get windows to recognize it?

---

### Post by surfer on 2010-09-08
you can easily resize the partition with [gparted live]("http://gparted.sourceforge.net/livecd.php"). backup your data before you do!

i don't know how you get windows to recognize it...

---

### Post by Edgewalker_001 on 2010-09-08
> **surfer said:**
> you can easily resize the partition with [gparted live]("http://gparted.sourceforge.net/livecd.php"). backup your data before you do!

i don't know how you get windows to recognize it...

My problem here is that gparted can't do much of anything with partitions that are mounted... And it's my boot partition for Ubuntu that I want to change.

EDIT: I got it, thanks for the help. That's at least one problem out of the way.

---

### Post by dcstar on 2010-09-08
> **Edgewalker_001 said:**
> My problem here is that gparted can't do much of anything with partitions that are mounted.


Before you shrink any NTFS/FAT partition it is a good idea to defrag it with Windows.

Gparted will try and move any data itself, but I trust the native Windows tools more in this regard.

---

### Post by Edgewalker_001 on 2010-09-08
> **dcstar said:**
> Before you shrink any NTFS/FAT partition it is a good idea to defrag it with Windows.

Gparted will try and move any data itself, but I trust the native Windows tools more in this regard.

I want to grow an NTFS partition at the expense of an EXT4 one, not the other way... XD

---

### Post by surfer on 2010-09-09
defrag before resizing may be a good thing in any case. and make sure you shut down windows (instead of hibernating) before you start. and - sorry, again - backup your data before you do.

---

