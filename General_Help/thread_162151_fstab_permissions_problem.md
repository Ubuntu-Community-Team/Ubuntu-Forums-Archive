---
title: "fstab permissions problem"
date: 2006-04-18
forum: General Help
---

### Post by stairwayoflight on 2006-04-18
hi,

i have a small problem, i have a 200g drive just for media. its mounted and i can read/write to it ok. the problem is i can't write to files i had created under a previous installation of linux.

i asked about this on another forum about a bash script or something that would go through the tree and change permissions so my user can read/write (i don't want to sudo everything). i was told

1. chmod can change permissions for whole sections of the filesystem at a time so i don't need a script
2. the right fstab line will do it so i don't need to use chmod even

here is the fstab line i used to mount the drive (hdb1, the drive is all one ext3 partition):

/dev/hdb1       /media/bigboy   ext3    rw,user,auto    0       0

i want my user to have full permissions to read, write & execute all files on the drive, but not other users. i want to delete/move files from the gui (nautilus, etc.).
If anyone can help me with the correct fstab line, i would appreciate it thanks.

---

### Post by Ramses de Norre on 2006-04-18
Mount it like this: (change device and mountpoint)
```
/dev/hda4       /home               ext3    nodev,nosuid 0       2

```
Then if necessary run sudo chown -R user_name mountpoint

---

### Post by aysiu on 2006-04-18
Just open a terminal and type ```
sudo chown -R stairwayoflight:stairwayoflight /media/bigboy
sudo chmod -R 755 /media/bigboy
``` That's it.

---

