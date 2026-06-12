---
title: "resizing usb xfs drive"
date: 2010-07-01
forum: General Help
---

### Post by kadafi69 on 2010-07-01
I have an external 1tb usb drive. It has 1 partition which is in the XFS format. I want to resize the drive to make it smaller, but I cant seem to find a way to do it without losing my data, I have tried using Gparted but the resize option is always greyed out and im not sure how else to go about it. Any ideas?

---

### Post by andrewc6l on 2010-07-01
I don't think there's a way to shrink an existing xfs partition... so you'll have to:
 - back up the contents of the drive to somewhere else (preserving file permissions)
 - make sure the contents really are backed up :-)
 - delete the partition on the drive
 - create a new, smaller partition on the drive
 - create a new xfs file system (or some other file system) on the new partition
 - copy the data back from where you backed it up

---

### Post by warfacegod on 2010-07-01
Sounds like you need xfs support. Open a Terminal and enter:

```
sudo apt-get install xfsprogs
```

---

