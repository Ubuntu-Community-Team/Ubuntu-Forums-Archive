---
title: "k3b doesn't see blank CDs"
date: 2011-06-02
forum: General Help
---

### Post by Lockheed on 2011-06-02
Right now it can't even though written cds are automounting fine.
```
/dev/cdroms/cdrom0     /media/dvd   auto   ro,user,noauto,unhide   0      0
```
or
```
/dev/sr0     /media/dvd   auto   ro,user,noauto,unhide   0      0
```
Neither works for k3b.

This is what I get when I insert blank CD:
```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged
```
I am member of optical.

What can I do to make k3b see blank cds?

---

