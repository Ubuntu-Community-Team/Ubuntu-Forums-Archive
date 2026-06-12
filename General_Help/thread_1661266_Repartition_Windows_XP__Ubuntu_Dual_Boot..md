---
title: "Repartition Windows XP / Ubuntu Dual Boot."
date: 2011-01-06
forum: General Help
---

### Post by Dyffo on 2011-01-06
I am running a dual boot with XP and Ubuntu - what I want to do is increase the partition size of Ubuntu and reduce XP. When I run   " G Parted" it shows both partitions with Xp being NTFS. I guess the boot loader is Grub because Ubuntu takes priority at Boot . I cannot persuade G Parted to allow me to resize the two different partitions. I am using the G Parted Live CD. Any advice please

---

### Post by Rubi1200 on 2011-01-06
Hi,
from the CD, post the output of the following commands please:

```
sudo parted -l

sudo fdisk -lu
```

Wrap the output with the # tag when posting back.

Thanks.

---

