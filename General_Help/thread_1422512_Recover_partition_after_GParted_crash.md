---
title: "Recover partition after GParted crash"
date: 2010-03-05
forum: General Help
---

### Post by eduardosd on 2010-03-05
Hello all,

In order to make room for Ubuntu in my friend's laptop, we had to move a Windows Vista NTFS partition to the left. The problem is, while GParted (from the 9.10 live CD) was moving the partition, the computer froze (I think it might be because of the wireless driver, but that's not the matter now). Then, after rebooting, I opened GParted again, and it reported an "unknown" filesystem at the new location I was going to move the partition to.

I figure this should be complicated because, although the data itself might be intact, the filesystem has a "hole" in it; but is there any hope on recovering the filesystem? (It seems PhotoRec can recover most of the files, but is there any chance we could have the filesystem structure back?)

Cheers,
Eduardo

---

### Post by CongoJim on 2010-03-05
Yes, testdisk has saved me from the same problem. I like to keep alive ubuntu on a flash for this and other purposes.

---

