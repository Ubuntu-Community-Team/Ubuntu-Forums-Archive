---
title: "How to fix corrupted ubuntu system-load files ?"
date: 2011-07-10
forum: General Help
---

### Post by EmreCFT on 2011-07-10
While xubuntu was starting (loading) i had an electricity  cut-off. then when i restarted again xubuntu didnt work and dropped to  busybox screen without any error.

How to fix that problem ?

Thanks.

---

### Post by EmreCFT on 2011-07-20
no idea yet ?

---

### Post by oldfred on 2011-07-20
I would think you would have to run this, but there may be other problems even hardware issues.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

