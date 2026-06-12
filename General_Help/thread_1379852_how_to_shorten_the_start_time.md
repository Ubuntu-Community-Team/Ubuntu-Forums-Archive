---
title: "how to shorten the start time?"
date: 2010-01-13
forum: General Help
---

### Post by ChipWolf on 2010-01-13
i installed xubuntu8.04 on my laptop(no other system),but when i started the system,there came out a grub and showed 
"press ESC to enter the menu"
 i think this is a waste of time
since i have only xubuntu on my lap, why do not just get in directly? why need a grub?i do not need 
so can i do something to shorten the start time?
( i know the menu is revovery option)
by the way i can not mount my usb hard disk, the error shows 
"mount: only root can mount /dev/sdb1 on /media/usbdrive."
ouyes@xubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f7bed15b-18a9-4d7f-9aa8-ba73b7a5f263 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9e952db5-47dc-416a-adf0-bbe424054ef5 /home           ext3    relatime        0       2
# /dev/sda5
UUID=a991fe46-d134-403a-ad94-872b5ee916c9 none            swap    sw              0       0
/dev/sdb1       /media/usbdrive  ntfs defaults,exec,umask=022 0 0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
what's wrong?how can fix it?

---

### Post by kerry_s on 2010-01-13
version 8.04 sucked, try the latest 9.10 where they actually worked on speeding things up.

---

