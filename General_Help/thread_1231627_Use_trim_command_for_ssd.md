---
title: "Use trim command for ssd?"
date: 2009-08-04
forum: General Help
---

### Post by josephellengar on 2009-08-04
I just got a new computer with an awesome 160 gb Intel x-25m ssd.  Is there any way to get Ubuntu to use the "trim" command, so that files are permanently deleted upon deletion and the drive does not slow down over time?  Thanks!

---

### Post by josephellengar on 2009-08-04
bump

---

### Post by tgalati4 on 2009-08-04
Current file deletion simply changes the name of the file to be hidden (through a move to a .trash file)  When you empty the trashcan then the files in .trash get deleted freeing up those sectors to be written over.

This can help ssd's because it reduces the wear by forcing new data to be written to virgin areas of the disk.  By deleting files in the trash can after a few months, you are forcing the drive to write to new areas--thus leveling the wear.

I'm not familar with the trim command.  You can always remove files using the rm command.  This deletes files instantly.

I'm not convinced of the longevity of ssd's over hard disks.  Read performance is hard to beat, but write speed is dependent on several factors--all are beyond your control.  If the ssd controller has a hiccup and has a write error, it can trash the entire disk, making data recovery nearly impossible.

Do the following:
sudo hdparm -tT /dev/sda

Let us know how fast your new ssd is.

---

### Post by josephellengar on 2009-08-04
> **tgalati4 said:**
> Current file deletion simply changes the name of the file to be hidden (through a move to a .trash file)  When you empty the trashcan then the files in .trash get deleted freeing up those sectors to be written over.

This can help ssd's because it reduces the wear by forcing new data to be written to virgin areas of the disk.  By deleting files in the trash can after a few months, you are forcing the drive to write to new areas--thus leveling the wear.

I'm not familar with the trim command.  You can always remove files using the rm command.  This deletes files instantly.

I'm not convinced of the longevity of ssd's over hard disks.  Read performance is hard to beat, but write speed is dependent on several factors--all are beyond your control.  If the ssd controller has a hiccup and has a write error, it can trash the entire disk, making data recovery nearly impossible.

Do the following:
sudo hdparm -tT /dev/sda

Let us know how fast your new ssd is.

Haven't gotten it yet.  I expect it to arrive in the next couple of days.  Anyway, the files aren't deleted even when you empty the trash.  The sectors are still full and have to be removed when they are going to be written over.  The trim command deletes the full sectors that are marked as free using spare CPU cycles.

---

### Post by tgalati4 on 2009-08-05
True, erasing NAND flash is what takes a long time.  Each SSD controller has sophisticated algorithms for tracking bad blocks, wear-leveling, and improving throughput.  I'm not sure any user-space activity would improve what is already happening at a low level.

The real test is to use it for a year.  Run your hdparm tests at every 6 months and keep track of the speeds.  That would telling.  One test is worth a thousand expert opinions.

NAND flash will slow down over time as the bad block list fills up, as the disk becomes fragmented (not the files but the block wear patterns), and more work to find virgin blocks as the disk fills up.  How noticeable is this?  Who knows?  The current SSD's in use are using older flash media and older controllers.  It's a quickly moving technology.  Since you are on the bleeding edge, you will inform us as to how big a problem it is.

In Windows, the slowness of the flash disk would probably not be noticed.

---

### Post by josephellengar on 2009-08-05
> **tgalati4 said:**
> True, erasing NAND flash is what takes a long time.  Each SSD controller has sophisticated algorithms for tracking bad blocks, wear-leveling, and improving throughput.  I'm not sure any user-space activity would improve what is already happening at a low level.

The real test is to use it for a year.  Run your hdparm tests at every 6 months and keep track of the speeds.  That would telling.  One test is worth a thousand expert opinions.

NAND flash will slow down over time as the bad block list fills up, as the disk becomes fragmented (not the files but the block wear patterns), and more work to find virgin blocks as the disk fills up.  How noticeable is this?  Who knows?  The current SSD's in use are using older flash media and older controllers.  It's a quickly moving technology.  Since you are on the bleeding edge, you will inform us as to how big a problem it is.

In Windows, the slowness of the flash disk would probably not be noticed.

Good point(s)!  Thanks!

---

### Post by Kismet on 2009-10-08
I came across this post looking to see if Ubuntu utilizes the TRIM command also. 

The previous posters seem unaware of exactly what TRIM allows. TRIM is VERY important for maintaining SSD speeds.

> The root cause of the issue is that SSD drives do not know which blocks are truly in use and which are free. While the file system on the SSD will maintain an in-use list, SSDs don't understand file systems, and cannot access this list. This causes trouble in two places:

    * SSDs can write 4KB blocks at a time, but only delete 512KB blocks. Since the drive does not know which 4k blocks are still in use if they have been written to previously, each write requires a 512KB read-erase-modify-write cycle.

    * Wear levelling allows a drive to rearrange its data so the writes are not confined to one corner of the flash chip. Flash cells tolerate only a limited number of writes before they fail, so some SSDs will move data around to exercise all of the blocks in the drive more evenly. Since the drive does not know which blocks are truly in use by its file system, each block of data written to the drive requires an additional write due to the moved block.


TRIM allows the wear-leveling low level controller of the SSD to more effectively manage all the free blocks.


[http://en.wikipedia.org/wiki/TRIM_%28SSD_command%29](http://en.wikipedia.org/wiki/TRIM_%28SSD_command%29)

> true, erasing NAND flash is what takes a long time. Each SSD controller has sophisticated algorithms for tracking bad blocks, wear-leveling, and improving throughput. I'm not sure any user-space activity would improve what is already happening at a low level.

This statement is false because without TRIM in the user-space, the "sophisticated algorithms" will not be able to use all the actual free space.

> The TRIM command allows an operating system to tell a solid-state drive (or "SSD") which data blocks are no longer in use, such as those left by deleted files. An OS operation such as delete generally only means the data blocks involved are flagged as not in use. TRIM allows the OS to pass this information on down to the SSD controller, which otherwise would not know it could trash those blocks.

---

### Post by Kismet on 2009-10-08
TRIM is implemented in the 2.6.28 Kernels, so It would appear Ubuntu should be making use of this. Maybe someone with more knowledge on the matter can verify this.

---

### Post by josephellengar on 2009-10-08
> **Kismet said:**
> TRIM is implemented in the 2.6.28 Kernels, so It would appear Ubuntu should be making use of this. Maybe someone with more knowledge on the matter can verify this.

It uses the 2.6.31 kernel in koala, I just looked at the tech specs,but I thought it needed to be implemented on the OS level.  Am I wrong?

---

### Post by falconindy on 2009-10-08
Just because the kernel supports it doesn't mean the OS does. It **does** need to be supported by the OS, as well as the filesystem on the drive and of course, the drive's firmware. 1st generation SSDs don't support trim, and some 2nd gen don't have full support. Karmic won't have support for trim out of the box, but it looks as though SSD performance is improved somewhat regardless.

[Source](http://ubuntuforums.org/showthread.php?t=1272893)

---

