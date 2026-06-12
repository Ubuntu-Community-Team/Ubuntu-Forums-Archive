---
title: "ext3 root FS is read-olny"
date: 2009-10-05
forum: General Help
---

### Post by Zafrusteria on 2009-10-05
I have managed to get my root file system, ext3, set as read-only. So when I boot I get all sorts or errors and warning and managed to get an unusable system.

I know I can use the remount option to mount it rw but I really would like to just boot up without all that :).

I have tried booting with the desktop CD and running 

fsck -t ext3 /dev/sda1

This comes back saying the fs is clean.

---

