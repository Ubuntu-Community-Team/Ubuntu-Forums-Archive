---
title: "Overwrote partition while removing Linux"
date: 2010-11-25
forum: General Help
---

### Post by jimmy299 on 2010-11-25
So the other day I decided to remove Linux from XP. I was running a multi boot setup, with Ubuntu, XP and Win7 on one disk, and XP on a second. I wanted to just use the second disk with XP, so I did some searching here and elsewhere, and I read that all I had to do was boot the recovery console from my XP install disc and run FIXMBR and FIXBOOT and this should get XP to boot again. I attempted this, but I was giiven an error saying that I had to run CHKDSK /r first. I did this, which took a while for it to finish (1.5T disk). I went back and did FIXBOOT and FIXMBR. Still not working. I went and hooked up the drive with Ubuntu on it, booted it and mounted/browsed the XP drive. Now it says "New Volume". I assume that CHKDSK must have somehow overwritten the partition on the disk. Not good. 

I did some more searching and ended up hooking up an old backup of the XP disk and booted into Windows. I installed a program (trial version) that recovers deleted files and lost partitions. I ran it for a few minutes and it did find find some of the files and folders on the drive, even showed the original volume label. So I know the drive wasn't completely formatted/wiped.

I don't know where to go from here. I figured I'd buy two new drives, make a clone of the original onto one (so i don't mess up the original), and recover the files onto the second. I only tried that one trial program, but most of the good file recovery programs I've found aren't free. Any good Linux programs that could do the same? I did try TESTDISK but it didn't find any files or the old partition.

Jimmy

---

### Post by Mark Phelps on 2010-11-25
> **jimmy299 said:**
> I assume that CHKDSK must have somehow overwritten the partition on the disk. Not good. 

NO ... chkdsk does NOT do that.  It only repairs an existing filesystem in an existing partition.

>  So I know the drive wasn't completely formatted/wiped.
Right ... your files are still there ... but if the filesystem was corrupted, chkdsk might not have been able to fix many of them.

> I only tried that one trial program, but most of the good file recovery programs I've found aren't free. 
So, you get what you pay for.  

> Any good Linux programs that could do the same? I did try TESTDISK but it didn't find any files or the old partition.
EXACTLY the experience I have had attempting to use a Linux file utility to recover files from an MS Windows partition -- complete failure.

If you want your files back, and chkdsk didn't fix them, you'll have to cough up the money for that "trial" utility that actually DOES find them.

---

