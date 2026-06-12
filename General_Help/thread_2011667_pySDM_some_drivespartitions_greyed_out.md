---
title: "pySDM some drives/partitions greyed out"
date: 2012-06-27
forum: General Help
---

### Post by rocketscove on 2012-06-27
new install of 12.04>>gksudo pysdm>>sda8,9,10,11,12 are greyed out. Sda5,6,7 are accessable. I understand sda8=swap and sda12=root not being accessed, but do not understand the others.

I merely want to mount at boot sda10, vfat for email storage etc....

pysdm and fstab screen shot attached...help appreciated....just point me to a google or ???

---

### Post by rocketscove on 2012-06-27
Gave up on pysdm.!!! I know I used it on another install, but it just don't work for me on this one.

Used>  /usr/bin/udisks --mount /dev/disk/by-uuid/****ur**uuidfrom here: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

