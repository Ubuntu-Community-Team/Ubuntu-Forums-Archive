---
title: "CDROM doesn't automount"
date: 2009-08-17
forum: General Help
---

### Post by hillsa on 2009-08-17
It appears that my CDROM is no longer automounting.  I've done some research and none of the options seem to work.  First, I'm running Jaunty and my /etc/fstab looks like the following:

proc            /proc           proc    defaults        0       0
UUID=26512a53-2095-413b-b58f-d8c55e77edfa /               ext3    defaults 0    1
UUID=A776-AC80  /media/archive  vfat    defaults,utf8,umask=001,gid=100 0       1
UUID=543f6cf2-568e-45f7-aaea-c7a1c5168260 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I can change the "noauto" to "auto" and manually mount the CDROM. When the option is left as "noauto", then I don't get any icon on the desktop and when I go to /media/cdrom0 I find an empty directory (as expected if the drive doesn't automount).  At this point, I'm looking for a little guidance.  Thanks.

---

### Post by 4leite on 2009-08-26
any luck with this? I seem to be having the same problem

---

