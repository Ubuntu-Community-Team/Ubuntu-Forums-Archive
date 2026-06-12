---
title: "terminal command for printing partions info"
date: 2012-04-21
forum: General Help
---

### Post by Metul Burr on 2012-04-21
I can't find the command to print the partitions in the terminal. I normally use gparted to review the numbers and names, but that takes awhile to open up.

---

### Post by zombifier25 on 2012-04-21
Try
```
sudo fdisk -l
```
It will list the current partitions, along with their type, size, ...

---

