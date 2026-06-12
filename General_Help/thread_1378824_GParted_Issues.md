---
title: "GParted Issues"
date: 2010-01-11
forum: General Help
---

### Post by DeMartini on 2010-01-11
I deleted Win7 from my dual boot but I cannot seem to merge the 160 gig's of free space into my ubuntu partition, ran the live gparted but it will not let me expand the ubuntu partition! Frustrating stuff:(

---

### Post by vinnywright on 2010-01-11
resizing partitions can be dangerus.....los of data and the sutch 

why not just reformat it to ext3 and use as storage.

but if you must delet the windows partition first then expand the other into the free space.

the space isent realey free wile it's still a partition.

VINNY

---

### Post by lswb on 2010-01-11
To combine the partitions they must be physically contiguous on the disk, and both either primary partitions or both in an extended partition. There may be other constraints as well but these come to mind. Post the results of the command "sudo fdisk -l" and maybe someone will have an idea.

---

### Post by DeMartini on 2010-01-11
> **vinnywright said:**
> resizing partitions can be dangerus.....los of data and the sutch 

why not just reformat it to ext3 and use as storage.

but if you must delet the windows partition first then expand the other into the free space.

the space isent realey free wile it's still a partition.

VINNYI'll go ahead and take the ext3 route for storage, thanks for the help:D It's just a head scratcher because I did delete the partition and I still couldn't expand the ubuntu partition? Oh well...

---

### Post by lindsay7 on 2010-01-12
Post a screen shot of how Gparted is looking and this may help us see what is going on.

---

