---
title: "to mount iso  get diffrent files"
date: 2012-06-13
forum: General Help
---

### Post by luofeiyu on 2012-06-13
root@debian:/home/tiger# mkdir  /tmp/test

root@debian:/home/tiger# mount -o  loop   /home/tiger/debian.iso  /tmp/test


root@debian:/home/tiger# mount -o  loop   /home/tiger/debian.iso  /tmp/test

the files in the  /tmp/test  is smaller than  files in  debian.iso

.disk [BOOT] is  in  the  debian.iso  ,
.disk [BOOT] is  not in the /tmp/test

there is a file named debian in the /tmp/test (it is a link file too),but not in debian.iso.

what's the reason?

---

### Post by maverickaddicted on 2012-06-13
> **luofeiyu said:**
> root@debian:/home/tiger# mkdir  /tmp/test

root@debian:/home/tiger# mount -o  loop   /home/tiger/debian.iso  /tmp/test


root@debian:/home/tiger# mount -o  loop   /home/tiger/debian.iso  /tmp/test

the files in the  /tmp/test  is smaller than  files in  debian.iso

.disk [BOOT] is  in  the  debian.iso  ,
.disk [BOOT] is  not in the /tmp/test

there is a file named debian in the /tmp/test (it is a link file too),but not in debian.iso.

what's the reason?

Any folders with prefix "." are hidden, so may be try show all hidden folders in the /tmp/test/ folder.

---

