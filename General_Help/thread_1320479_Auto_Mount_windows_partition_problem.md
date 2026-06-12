---
title: "Auto Mount windows partition problem"
date: 2009-11-09
forum: General Help
---

### Post by n.hinton on 2009-11-09
While using Jaunty I added:
/dev/sda1 /media/disk-1 vfat iocharset=utf8,umask=000 0
to the end of fstab to auto mount my windows partition, all worked fine. Upgraded to Karmic the auto mount still worked fine until today, for no apparent reason auto mount failed, had a look in File System Media and noticed disk-1 is no longer called disk-1 but 2D27-07EE.

Changed the fstab line from:
/dev/sda1 /media/disk-1 vfat iocharset=utf8,umask=000 0
to
/dev/sda1 /media/2D27-07EE vfat iocharset=utf8,umask=000 0
and the partition auto mounts again.

I would like to be able to restore the disk-1 naming but don't know how, any suggestions much appreciated.

---

### Post by n.hinton on 2009-11-10
Resolved re thread:
[http://ubuntuforums.org/showthread.php?p=8288248](http://ubuntuforums.org/showthread.php?p=8288248)

---

