---
title: "disk data recovery help"
date: 2010-11-01
forum: General Help
---

### Post by nerdy_kid on 2010-11-01
This should be real easy for one of you experts out there ;)

I accidentally formatted a 2TB drive of mine (big oops), but have recovered 2 of the 3 partitions using testdisk.  My third partition is a LUKS encrypted partition.  testdisk managed to recover a piece of it, but it won't mount as most of it is unallocated.

The partition originally occupied all space from sector 2,930,272,065 to the end of the disk -- sector 3,907,024,064.  That is about 473 GBs.

Currently, the partition only uses space from sector 2,930,272,065 to 2,930,288,129, about 7.84 MB.  The rest of the space is unallocated.  Now what I need to do, is to expand the partition so that it occupies all the space that it used to.  How would I do this?  I can not resize the partition, cause it would try to recreate the filesystem AFAIK and I don't want that, as it will fry my data.  My data is not terribly important, but I would rather have it then not :P

I attached a screenie of kpartitionmanager.  The partition in question is /dev/sdb2.

Thanks!

---

### Post by nerdy_kid on 2010-11-02
bump

---

### Post by coffeecat on 2010-11-02
I recently used the link below to edit the partition table when I encountered a problem as described in the link, the partition table showing the last sector of an extended partition beyond the physical end of the disk. I know this is not your problem - in fact yours is the opposite - but the link describes how to manually edit the partition table, which is all you would need to do I guess. Your filesystem is there. It's just the partition table that is giving the wrong size.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Good luck.

---

### Post by nerdy_kid on 2010-11-02
Excellent, thank you very much for that.  Haven't got a chance to try it yet, but it looks like exactly what I need. Thanks!

---

### Post by nerdy_kid on 2010-11-03
yup, that fixed it perfectly.  Thanks!

---

