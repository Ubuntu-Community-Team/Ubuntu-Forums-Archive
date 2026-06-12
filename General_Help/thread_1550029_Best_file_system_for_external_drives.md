---
title: "Best file system for external drives"
date: 2010-08-10
forum: General Help
---

### Post by jonathonblake on 2010-08-10
I'm going to reformat my external drives to get rid of the crud that I've built up.   (Crud being incremental backups, windows software, and similar things.)(I also want to get rid of the FAT32 file system that they use.)

These are USB 1TB drives. The theory is that data is written to it once, but read back a number of times. (I also burn that data to DVD. If there was software that could organize 5TB of data on DVDs, I'd be using them.)

I"m trying to decide whether to use ReiserFS, Ext4, or another file system. Basically, I want something that:
* Won't get corrupted when the power fails;
* Can handle files that are 4+GB in size;
* Uses extends --- preferably without user intervention;

jonathon

---

### Post by dabl on 2010-08-10
Reiserfs has not been actively maintained for years now -- it has no future.

Otherwise:  [http://ubuntuforums.org/showthread.php?p=9702877#post9702877](http://ubuntuforums.org/showthread.php?p=9702877#post9702877)

---

### Post by mister_playboy on 2010-08-10
ext4 gets my vote.

---

### Post by -kg- on 2010-08-10
Depends on what OSes you access them (or anticipate accessing them) with.  If you use (and only anticipate using) only Linux with them, then ext4 is probably the way to go.

If you use Windows, you will want NTFS or ext2/3 (there are drivers for Windows that will allow it to access these formats).  As of yet, there are no drivers available that will read a partition formatted to ext4.

> Reiserfs has not been actively maintained for years now -- it has no future.

Lord have Mercy...[I had no idea on the story behind that]("http://arstechnica.com/old/content/2008/07/reiserfs-fading-into-obscurity-as-maker-leads-cops-to-corpse.ars")!

---

