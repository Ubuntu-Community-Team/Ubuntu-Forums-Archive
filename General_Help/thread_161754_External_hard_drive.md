---
title: "External hard drive"
date: 2006-04-17
forum: General Help
---

### Post by styven on 2006-04-17
Hi all,

I have purchased a Maxtore 100gb external had drive to back up data.

I can write to it in windows, I can retrieve from it in linux.

What i can't do is write to it from linux.

I am told i do not have permission. and in properties I cannot change permissions as i am not the owner.

Also, i think this may be an issue, it is formatted as NTFS.

Any ideas what i do next?

Steve.

---

### Post by _linux_ on 2006-04-17
I've heard about a program called ntfs-fuse, which lets you write to NTFS disks. But I'm not sure if it's 100% safe to use. Some people say it is, other people say it isn't. I guess you just have to try it and see.

---

### Post by teet on 2006-04-17
I would just reformat the drive as fat32 (called vfat in linux).

That way you can read/write from linux or windows.  That's the easiest option.  I think you can format the drive directly from windows (that's the way I did mine...just right-clicked on the drive in my computer and left-clicked on format).

However, my drive was completely empty when I did this (not even a partition).  

-teet

---

