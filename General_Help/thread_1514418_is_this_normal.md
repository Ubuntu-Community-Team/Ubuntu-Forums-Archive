---
title: "is this normal?"
date: 2010-06-21
forum: General Help
---

### Post by Zombeast on 2010-06-21
this part isnt i know:
when trying to install ubuntu i get the nice black screen, but i fixed that by installing windows XP, then using WUBI demo install, using gparted to delete the partition, so on a 500GB hard drive, 465GB is used by XP and im demo booted. I delete the 465GB partition so its empty, and i install ubuntu on it

well instead of getting 465GB of space it says

TOTAL FILESYSTEM CAPACITY: 462.9GB
USED: 3.1GB
Available: 459.8GB..

Open gparted on full install:
---------------------------------

Unallocated: 1MB... (thats normal)
/dev/sda1/        file system: ext4       mount point: /      size: 454.34GB     used: 9.44GB    unused: 444.99GB

that part seems normal for a 10GB install of ubuntu 10.04

below that is:


-/dev/sda2/  file system: extended
  /dev/sda3/ file system: linux-swap    size: 11.33GB

so i had 11 and a half gigabytes *stolen* my size is usually 465 GB/

the used space and unused space adds to 463.78GB total, which means the swap holds 11.33GB, but it says used ----

so, is this all normal?

---

### Post by S.R on 2010-06-21
Yes it is correct. Best explanation I found was [http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)

---

