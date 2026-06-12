---
title: "ntfs disk partitioning"
date: 2006-06-04
forum: General Help
---

### Post by teia on 2006-06-04
Hi

I have a 300 gb ntfs disk with something like 180 gb of musik files on it. Totally there is some 60 gb free space on the disk.

I have no means of backing up the disk exept in portions and was wondering if there is possible to make a ext3 partition on the 60 gb space, copy some data into it and the partition up some more space?
The problems I have to day is that I can't do enything to my music files other than playing them, and it would be nice to be able to add/delete some of them too if you know what I meen.
:confused: :confused: 
How can I get around this??

Teia

---

### Post by gerbman on 2006-06-04
> **teia]is possible to make a ext3 partition on the 60 gb space, copy some data into it and the partition up some more space?[/QUOTE]If the 60 gb space is unallocated, you can use GParted to create an EXT3 partition in that space said:**
> The problems I have to day is that I can't do enything to my music files other than playing them, and it would be nice to be able to add/delete some of them too if you know what I meen.As long as the music files remain on the NTFS partition you won't be able to add/delete them. Read/write support for NTFS isn't very good right now. I'd suggest moving the files over to an EXT3 or FAT32 partition and doing away with the NTFS partition.

---

### Post by eqisow on 2006-06-04
> (I) was wondering if there is possible to make a ext3 partition on the 60 gb space, copy some data into it and the partition up some more space?

That should work, just be sure to defrag the NTFS partition each time before you shrink it. It moves all the files to the beginning of the partition and reduces the risk of corrupting your files.

---

### Post by teia on 2006-06-04
Thanx

Yeah I figured this would be the right way to do it. The whole disk is in one partition and I'd probably be best off borrowing an external disk and use it for backup while I partition up an reformat the 300 g disk.

thanx again for your answer

Teia

---

