---
title: "NFTS Defragmentation Tool"
date: 2009-09-16
forum: General Help
---

### Post by dawbomb on 2009-09-16
Hi,

I'm currently dual booting Ubuntu 9.04 AMD64 and Windows 7 RC.  I've got an internal SATA2 drive, an internal PATA drive, and my external hard drive is SATA (connected via USB).  The external and internal PATA drives have one partition each, formatted in NTFS, and the SATA2 drive has 2 NTFS partitions.  The reason I've used NTFS for most of my storage is that when I boot in Windows, I can't access them if they're ext3.  And a driver that I found for windows doesnt work with Windows 7.

So, now that I'm using NTFS drives, I need to be able to defragment them.  Which at the moment means that I need to start up windows, and defragment them there.  Which is a pain seeing as ubuntu is my primary OS.

I've searched the repositories and softpedia, does anyone know of any tools that I can use to defragment NTFS drives from within ubuntu?

Thanks

---

### Post by earthpigg on 2009-09-16
simple answer: no, not at present. super duper FOSS hobbyist programmers generally dont have a great deal of NTFS/FAT32 hard drives, ergo would have no use for such a tool, and thus not many will help develop it on their own without pay (these guys usually work on stuff *that interests _them_*), and (apparently) the corporate/commercial demand for such a tool is so minimal that no one is willing to pay anyone to develop it. the project does exist, however, in theory. see: [http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

complex answer: would you be interested in a windows driver that will allow windows to be able to read linux filesystems?

---

### Post by dawbomb on 2009-09-16
Thanks!

> **earthpigg said:**
> complex answer: would you be interested in a windows driver that will allow windows to be able to read linux filesystems?

Thanks, I've already got one, [http://www.fs-driver.org/]("http://www.fs-driver.org/"), but it doesn't seem to work in Windows 7!  Some people claim it does, but I cant seem to get it to work...

---

