---
title: "make cannot find head files in build-essentials"
date: 2010-06-07
forum: General Help
---

### Post by yilin on 2010-06-07
I installed build-essentials and tested with some simple c/cpp codes but when build gnustep modules, I got this

checking sys/inttypes.h usability... no
checking sys/inttypes.h presence... no


Any idea how to fix this? Thanks a lot

---

### Post by ba_saish on 2010-06-09
run the command locate inttypes,h and see if you can find the file. Then modify the make file accordingly

---

### Post by quinnten83 on 2010-06-09
does it also need the Linux kernel headers, perhaps?
That can be installed from the repo's.

---

