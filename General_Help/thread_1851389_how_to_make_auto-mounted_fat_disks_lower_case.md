---
title: "how to make auto-mounted fat disks lower case?"
date: 2011-09-28
forum: General Help
---

### Post by akos.maroy on 2011-09-28
I wonder how can one change the mount options for auto-mounted filesystems in ubuntu?

what I want to solve is to have auto-mounted fat filesystems (memory sticks / cards in general) to have the shortname=lower flag, instead of shortname=mixed.

is there a setting somewhere to change the default behaviour?

---

### Post by linux2001 on 2011-09-28
You add new line in /etc/fstab 
For example :

/dev/sdb1	/media/usb    vfat    defaults        0       2

---

