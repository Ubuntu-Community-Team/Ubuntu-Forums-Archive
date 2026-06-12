---
title: "Mount to fstab Entry"
date: 2009-11-16
forum: General Help
---

### Post by culdesac on 2009-11-16
How do you convert:

/dev/sdb1 on /media/Media type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

to a fstab entry?

Currently, I have to manually access the drive to mount.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Try pysdm. It's a GUI for making fstab changes. ```
sudo apt-get install pysdm
``` will install it and ```
sudo pysdm
``` will run it. You can also learn the fstab [here]("http://help.ubuntu.com/community/Fstab")

---

### Post by culdesac on 2009-11-16
That was the trick, thanks.

---

