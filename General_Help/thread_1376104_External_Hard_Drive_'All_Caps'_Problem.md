---
title: "External Hard Drive 'All Caps' Problem"
date: 2010-01-08
forum: General Help
---

### Post by joelandsonja on 2010-01-08
I realize this may sound strange to some of you, but I am trying to figure out how to rename my External Harddrive so that the title will show without using 'All Caps'. At the moment, my harddrive displays as 'LOCAL DISK' while all of my other external harddrives display 'Local Disk'. I tried using GParted to fix the problem, but when I type in 'Local Disk' it reverts back to 'LOCAL DISK' when I try to save it. 

Any thoughts?

---

### Post by Leppie on 2010-01-08
to what fs is it formatted? i believe i had this with fat filesystems (fat32,fat16, etc.).

---

### Post by joelandsonja on 2010-01-09
I believe it is in Fat format, but how do I change this without losing my information?

If it is possible to change it, is there a step by step guide on how to do it?

---

### Post by Leppie on 2010-01-09
there's the microsoft technet page: [http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx)

---

### Post by joelandsonja on 2010-01-09
Will I lose my information when I change it?

---

### Post by Jackzor on 2010-01-09
> **joelandsonja said:**
> Will I lose my information when I change it?

If you read some of the page you would have seen


The Setup program makes it easy to convert your partition to the new version of NTFS, even if it used FAT or FAT32 before. This kind of conversion keeps your files intact (unlike formatting a partition).

---

### Post by Leppie on 2010-01-09
exactly, converting from fat to ntfs should be lossless. vice versa normally isn't.

---

