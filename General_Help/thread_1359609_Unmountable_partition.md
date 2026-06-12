---
title: "Unmountable partition"
date: 2009-12-19
forum: General Help
---

### Post by Ankhwatcher on 2009-12-19
rory@ZUBUNT:/mnt$ sudo umount /dev/md0p1
umount: /dev/md0p1: not mounted
rory@ZUBUNT:/mnt$ sudo mount /dev/md0p1
mount: /dev/md0p1 already mounted or /media_library busy

Am I loosing my mind?
This partition of a 1000 GB raid1 drive is refusing to mount. The raid is perfectly healthy. It won't mount anywhere else either.

---

### Post by serpantman on 2009-12-19
fuser -m /dev/deviceyouwanttomount

you'll get a PID# then either

kill PID#  <--- to free it

or

ps -e | grep PID#  <---- to see whats using it

This works for me when i get that error. Hope I helped.

---

### Post by Ankhwatcher on 2009-12-20
It worked! Or it fixed itself during the night... I'm not really sure.

```
rory@ZUBUNT:/$ sudo fuser -m /dev/md0p1
[sudo] password for rory:
/dev/md0p1:           8379m
rory@ZUBUNT:/$ sudo kill 8379
rory@ZUBUNT:/$ sudo mount /dev/md0p1
mount: /dev/md0p1 already mounted or /media_library busy
mount: according to mtab, /dev/md0p1 is already mounted on /media_library
```

---

