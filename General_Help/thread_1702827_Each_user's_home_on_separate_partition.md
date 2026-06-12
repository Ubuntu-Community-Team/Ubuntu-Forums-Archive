---
title: "Each user's home on separate partition"
date: 2011-03-08
forum: General Help
---

### Post by edib0y on 2011-03-08
Hi. I would like to know how would I go about having each user's home folder (\home\username\) on a separate partition/logical volume. Is that possible? If so, how? Could I mount each user's partition directly to each user's home folder?

Thanks!

---

### Post by Chronon on 2011-03-08
Yes, you can mount any partition to any location using fstab:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by edib0y on 2011-03-08
So I take it that there would be no conflict of any kind? 

Also, which free disk space would Ubuntu return for the folder? I presume for the partition?

---

### Post by Chronon on 2011-03-08
The fstab gets read during boot and partitions are mounted accordingly.  Provided each partition is associated with a unique mount point there will be no conflict.

---

