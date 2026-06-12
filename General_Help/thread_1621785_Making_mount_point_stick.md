---
title: "Making mount point stick"
date: 2010-11-14
forum: General Help
---

### Post by edzell on 2010-11-14
Ubuntu 10.04 (actually Mint 9)

I've created a separate partition labeled Data and mounted it at /home/myname/Data; but when I close & reboot the computer, the mount point reverts to /Data. How can I make my preferred mount point permanent?

---

### Post by Verbeck on 2010-11-14
you could add the drive to your fstab, (it'll mount at start up)
so run 
```
gksudo gedit /etc/fstab
```and add a new line for that data partition
```
UUID=**0C2A39615EAFB871** /home/myname/Data **filesystem** defaults 0 0
```to check the uuid and file system of the partition, run *sudo blkid* from a terminal while the device is connected

---

### Post by oldfred on 2010-11-14
You will want to mount it as part of the boot process with fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I prefer to do it manually as sometimes the auto version does not use correct settings:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Also after any changes to fstab run this to confirm that it is correct. if it just returns it has remounted everything without error.
sudo mount -a

---

