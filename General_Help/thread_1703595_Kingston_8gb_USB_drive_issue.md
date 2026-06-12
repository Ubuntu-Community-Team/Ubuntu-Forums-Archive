---
title: "Kingston 8gb USB drive issue"
date: 2011-03-09
forum: General Help
---

### Post by chee on 2011-03-09
I have a Kingston 8gb Datatraveler that has been giving me troubles lately.  For some reason after I delete files from it it still shows up as full and the files are shown in the hidden trash files.

How do I get rid of these files?  I can't delete them as they just show back up.

Also,  I tried to format the drive with gparted and it won't unmount.  When I right click and select information,  at the bottom it says:
Unable to find mount point.
Unable to read the contents of the file system.
Because of this,  some operations may be unavailable.

Any help with this would be greatly appreciated.
Thank you.

---

### Post by TeoBigusGeekus on 2011-03-09
Try wiping it up completely with dd
```
dd if=/dev/zero of=/dev/whatever
```
Then use gparted or fdisk+mkfs to create new partitions and format them.

---

