---
title: "Hard Drive mounting problem"
date: 2010-05-03
forum: General Help
---

### Post by M6bud on 2010-05-03
: Could someone help me with a HD mount problem I keep getting this error Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed

I have reformated the drive and have checked / to see if it was indeed mounted. Works fine in windows with zero problems. Any ideas?

---

### Post by M6bud on 2010-05-03
Forgot to add im on 10.04

---

### Post by psmouty on 2010-06-06
+1 on this if I try and go in via disk utility in system/admin then i get:-

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed

---

### Post by davidyblood on 2010-06-15
I have the same problem. My laptop has 2 hard drives and it was trying to mount both of them at the same location so i created a directory called /media/disk1 and mounted the 2nd hard drive there. it works fine. give it a try and let me know if it works.

---

### Post by linux-hack on 2010-06-15
ok you rely need to give more infos then that .. your hdd partitions, which one you want to mount, where you want to mount 'it, the commands you used, may be terminal out put, screenshots, this way we can help you with the exact commands you need to put in ...

---

