---
title: "USB drive no longer automounts"
date: 2011-09-24
forum: General Help
---

### Post by DrScum on 2011-09-24
USB drives no longer automount on my laptop, while they work fine on my desktop, both machines run up to date ubuntu 10.04.

When I insert the USB drive I get the following error message:

Unable to mount <8 GB file system>
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/sdb1

How can I diagnose/fix this?

---

### Post by TeoBigusGeekus on 2011-09-24
Try changing the ownership of the mount point
```
sudo chown -R yourusername /media/sdb1
```
If it complains that the folder doesn't exist, create it
```
sudo mkdir /media/sdb1
```
and repeat the first command.

---

### Post by DrScum on 2011-09-24
Thx that worked for me. I can't explain, however, why this happened in the first place.

---

### Post by TeoBigusGeekus on 2011-09-24
I don't know. For some reason root took over the ownership of the mount point. 
Don't worry too much about it.

---

