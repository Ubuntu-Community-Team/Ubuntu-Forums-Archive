---
title: "What should i format My Backup Drive"
date: 2010-06-14
forum: General Help
---

### Post by Ravernomina on 2010-06-14
Hello all. I Just got a Removable Hard drive! YAY!!! Now i need to format it because i need it to hold more then 4 GB file sizes. What format should i used. Ill only need compatibility with Other LINUX computers. So should i use NTFS, BTRFS, or EXT4? Thanks!

PS How would i take ownership of the backup drivers file system and not ROOTS permissions

---

### Post by Ravernomina on 2010-06-14
Bump

---

### Post by Joe of loath on 2010-06-14
I'd format as NTFS, as the permissions can screw up when you stick your data back onto a fresh install. You just have to remember to chmod the right files when they're copied back over.

---

### Post by TheForumTroll on 2010-06-14
Sadly I don't know much about the different file systems but personally I would go for something very robust as it is a backup drive. I know NTFS support has matured a lot in Linux over that last years but if it was my files and there is no need to access them from Windows I would go with something like Ext3 maybe even with data=journal or something.


It depends on how important the data is and what is the worst thing that can happen to the drive. Fx. the power getting cut. Cutting the power could be bad if the data isn't written to the disk yet.

[Here's some stuff]("http://www.ibm.com/developerworks/library/l-fs8.html") about the mount option i mentioned.

---

### Post by scouser73 on 2010-06-14
> **Ravernomina said:**
> Hello all. I Just got a Removable Hard drive! YAY!!! Now i need to format it because i need it to hold more then 4 GB file sizes. What format should i used. Ill only need compatibility with Other LINUX computers. So should i use NTFS, BTRFS, or EXT4? Thanks!

PS How would i take ownership of the backup drivers file system and not ROOTS permissions

Going by what Wikiepedia says, I'd recommend you format it to Ext4.
> **Large file system**
The ext4 filesystem can support volumes with sizes up to 1 exabyte and files with sizes up to 16 terabytes. The current e2fsprogs can only handle a filesystem of 16 TB, but support for larger drives is under development.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by Manyette on 2010-06-14
Personally I use ext3, bacause I use Clonezilla for backup, and it doesn't (as yet) support ext4.  Just one thought.

---

