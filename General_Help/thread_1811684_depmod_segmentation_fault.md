---
title: "depmod segmentation fault"
date: 2011-07-25
forum: General Help
---

### Post by luigione61 on 2011-07-25
hi guy
i have this problem:after profiling tymesis kernel 2.6.29 i run make and all seems OK (vmlinux image was correctly generated). iif i run make clean and make the following
 error occurs:
[COLOR=Red]Segmentation fault      /sbin/depmod -ae -F System.map -b <directory>[/COLOR]
if i delete vmlinux,System.map and i run make again the same error occurs.

do you have any ideas?

bye

---

