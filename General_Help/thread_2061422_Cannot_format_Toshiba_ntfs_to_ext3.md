---
title: "Cannot format Toshiba ntfs to ext3"
date: 2012-09-22
forum: General Help
---

### Post by z5um on 2012-09-22
Hi,

i want to format this Toshiba 500GB usb external drive to ext3. When i click partition all sub selections but unmount, manage flags and information are disabled. How can i format this drive? What do the keys mean?

[[img]http://www.freeimagehosting.net/t/ya7co.jpg[/img]](http://www.freeimagehosting.net/ya7co)

---

### Post by Cheesemill on 2012-09-22
You need to unmount the partition before you can make any changes to it, the key means the partition is locked (mounted).

---

### Post by z5um on 2012-09-22
ok thx, i managed to achieve it via sudo mkfs.ext3 /dev/sdb1

---

