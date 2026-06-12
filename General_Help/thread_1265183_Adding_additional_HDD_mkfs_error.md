---
title: "Adding additional HDD mkfs error"
date: 2009-09-13
forum: General Help
---

### Post by dbrine on 2009-09-13
I have the strangest error and I have no idea what the problem is. I have Ubunutu 9.04 server. I added a second HDD, when I run fdisk -l, /dev/sdb is displayed. No problem because I didn't fdisk yet. So I run fdisk /dev/sdb and create a single partition and use "w" to write the table. I then reboot the system

I then run fdisk -l again and get /dev/sdb1. Looks good. I run mkfs.ext3 /dev/sdb1 and I get

Could not stat /dev/sdb1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

---

