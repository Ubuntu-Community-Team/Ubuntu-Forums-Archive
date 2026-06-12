---
title: "usb clamav r/o usb drive"
date: 2010-02-08
forum: General Help
---

### Post by jocatoth on 2010-02-08
i have a virus infected 30g hard drive now in a USB external enclosure. i want to remove several nasty viruses by using clamav run on a ubuntu 8.10 box. that seemed to work fine. however, the 15 or so quarenteened and "deleted" are not deleted. 

here is the mount information
/dev/sdh1 on /media/HP_PAVILION type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

so i tried chown 777 to change the permissions as well as going from gksudo nautilus. but i still could not get r/w access.

i would appreciate any help or suggestions and thank you in advance

---

### Post by dcstar on 2010-02-09
> **jocatoth said:**
> i have a virus infected 30g hard drive now in a USB external enclosure. i want to remove several nasty viruses by using clamav run on a ubuntu 8.10 box. that seemed to work fine. however, the 15 or so quarenteened and "deleted" are not deleted. 

here is the mount information
/dev/sdh1 on /media/HP_PAVILION type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

so i tried chown 777 to change the permissions as well as going from gksudo nautilus. but i still could not get r/w access.

i would appreciate any help or suggestions and thank you in advance

Do a fsck on the partition.

---

### Post by jocatoth on 2010-02-09
thanks for the tip. i ended up using dosfsck (see vfat fschk). this did the trick.

---

