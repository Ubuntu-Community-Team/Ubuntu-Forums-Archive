---
title: "resizing a disk problems"
date: 2012-02-04
forum: General Help
---

### Post by nslegacy163 on 2012-02-04
Hey gang, 

 I don't know what I was thinking, but I partitioned my external like this (see attached screen grab). I want to resize the largest partition to take up the entire space of the disk. I'm doing something wrong and can't get gparted to give me the option to over take those unwanted spaces. I deleted the partitions and tried, made them the say format and tried...what am I missing? It's been one of those weeks...

Thanks ahead of time.

---

### Post by lechien73 on 2012-02-04
You also need to delete the extended partition /dev/sdc2 as well. You can't expand a primary partition into extended partition space.

---

### Post by kherring7383 on 2012-02-04
You'll need to delete the extended partition (sdc2) and then apply. Once you have removed the extended, you need to unmount the partition you want to resize. After that you should now be able to resize it and apply the changes.

Good Luck.

---

### Post by nslegacy163 on 2012-02-04
Thanks guys, that'll work! Thanks for jogging the ol' noggin.

---

### Post by nslegacy163 on 2012-02-04
Oh, and also...

 I have files on there that I can't back up this instant (I can later). The warning says it "may have the potential for data loss..." and I could do this later but would like to do it while I have the time now. If I have to wait and back up the files it's not a big deal though...

so, odds of losing my files?

---

