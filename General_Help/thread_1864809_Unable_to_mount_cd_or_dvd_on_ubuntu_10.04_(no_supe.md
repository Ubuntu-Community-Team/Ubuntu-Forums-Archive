---
title: "Unable to mount cd or dvd on ubuntu 10.04 (no superuser)"
date: 2011-10-19
forum: General Help
---

### Post by MS6 on 2011-10-19
I have following problem, the desktop computer is a part of a local network, where the non-root users are managed by a ldap database (to which i have no root access), because all home folders of normal users are located on a fileserver. I am the guy with local superuser rights, i.e. I can do anything with the desktop pcs which is necessary. If log in as local superuser (who have a local home directory) I can mount directly any cd/dvd by simply clicking Places==> or "mount /dev/sr0" (without sudo) on the terminal. But it seems not to be possible for the normal users, because ubuntu refuses with ridiculous "no-superuser"-messages.

My fstab looks like:
######################################################
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=576f39ff-ab25-4459-9134-988c9478ed41 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9b41f5f2-59eb-46b9-89b2-eaf795228034 none            swap    sw              0       0
/dev/sr0    /media/cdrom0     auto user,noauto,exec,utf8 0 0
134.19.21.16:/data/home    /home       nfs rsize=32768,wsize=32768,hard,intr,tcp
134.19.21.16:/data/department    /exchange       nfs  rsize=32768,wsize=32768,hard,
########################################################

I have also tried to change filesystem type in the /dev/sr0 line to iso9660 or udf.
I am sure that /dev/sr0 is the right location and I know my cd/dvd drive is properly working. 

does anyone have a idea whats going wrong?

Any help will be gratefully appreciated  

MS

---

### Post by MS6 on 2011-10-20
I found a solution for the described problem

simply switch from "user" to "users" in the /dev/sr0 line

---

