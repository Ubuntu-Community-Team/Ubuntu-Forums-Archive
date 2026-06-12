---
title: "File Transfer issue"
date: 2009-09-09
forum: General Help
---

### Post by mbaybarsk on 2009-09-09
I'm trying to transfer a file which has a size of 7.4 gb's from my laptop to a flash disk (8gb). 
 
The transfer stops (i get an error) in the middle of the process, and i see that the transfer stops when the file on the flash disk reaches 4 gb's.
 
What could be the problem?

---

### Post by howefield on 2009-09-09
> **mbaybarsk said:**
> What could be the problem?

What file system do you have on your flash disk, as some have a limit on the file size.

Second table down in this article..

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by 3rdalbum on 2009-09-09
> **mbaybarsk said:**
> I'm trying to transfer a file which has a size of 7.4 gb's from my laptop to a flash disk (8gb). 
 
The transfer stops (i get an error) in the middle of the process, and i see that the transfer stops when the file on the flash disk reaches 4 gb's.
 
What could be the problem?

Your flash drive is formatted as fat32/vfat. That filesystem can only handle files up to 4 gibibytes. If you will be using the flash drive with Linux PCs, then format it as ext3 and transfer the file across. If you're going to be using the flash drive with Windows, then format it as ntfs (you need the ntfsprogs package) but note that Linux is slow to write files to NTFS filesystems.

---

### Post by chandru155 on 2009-09-09
My  perndrive is farmated as FAT 32. I want to use it windows also. So i use FAT 32. But copying files from PC to pendrive is very slow just 3MB per Second. But in Windows it goes upto 10MB. Should i format is as Ext3 to get fast speed?

---

### Post by t0p on 2009-09-09
> **chandru155 said:**
> My  perndrive is farmated as FAT 32. I want to use it windows also. So i use FAT 32. But copying files from PC to pendrive is very slow just 3MB per Second. But in Windows it goes upto 10MB. Should i format is as Ext3 to get fast speed?

If you want to use the drive with Windows, do *not* format it ext3.  Windows doesn't do ext3.  (Actually, I might be wrong on that - there may be a way to get Windows OSes to read/write ext3.  But I don't know it.)

A better solution may be to format the drive as ntfs, as both Linux and Windows can deal with it.

---

### Post by mbaybarsk on 2009-09-09
I totally thought ubuntu was the source of the problems, i didn't even think about the disk :) 
 
Thanks

---

