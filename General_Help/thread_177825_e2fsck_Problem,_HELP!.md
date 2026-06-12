---
title: "e2fsck Problem, HELP!"
date: 2006-05-16
forum: General Help
---

### Post by redcyborg on 2006-05-16
Hi. Recently i tried to add in some a RAID PCI card to increase more drive space. That didnt work out so i put everything back the way it was but when i booted it up i got a error

/home contains a file system with errors, check forced.

it does a check progress bar then says

e2fsck failed. Repair manually.

It allows me to press Ctrl-D  and ubuntu will still load properly but how do i fix this error from coming up at all? 

Maybe it has something to do with my fstab file? This is it if its needed anyway

proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /home           ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Some help will be greatly appretiated.

---

