---
title: "root/permission issues on 9.04"
date: 2009-09-10
forum: General Help
---

### Post by notoriousmic24 on 2009-09-10
I'm trying to delete/add files on an external hard drive, but I'm not aloud to because I'm not root. I get this error for other things as well. Please help asap.

---

### Post by NightwishFan on 2009-09-10
You can use the command line to edit the permissions on the drive.

For example:

```
sudo chown -R 777 /media/diskmountpoint
```
OR
```
sudo chown -R yourusername /disk/mount/point
```
I think 777 means all users can access, if it is an ext3 or ext4 filesystem. If it is NTFS, I would not do this.

Please wait for conformation before doing so.

---

### Post by notoriousmic24 on 2009-09-10
Got it...thanks =-)

---

### Post by NightwishFan on 2009-09-10
For short term, you can press alt+f2, type this, and then push enter:
```
gksudo nautilus
```
With that nautilus window, you will be able to delete any files on the system, so I do not recommend it!

To find the mount point, go to the folder /media. It should be in there perhaps called /media/disk. If it is the correct one, open a terminal window (Applications -> Accessories -> Terminal) and type:
```
sudo chown -R *yourusername* /media/disk
```
Replace yourusername with your user, and /media/disk with the mount point of the external drive.

---

