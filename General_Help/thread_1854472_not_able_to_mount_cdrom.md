---
title: "not able to mount cdrom"
date: 2011-10-04
forum: General Help
---

### Post by 2ez2build on 2011-10-04
I have ubuntu 11.04 installed it works great except I can not mount the cdrom no record of the cdrom in fstab I have been searching for the past 2 days how to create a mount point but i have not found one so here I am hoping some one can help me! 




thanks in advance

---

### Post by pr3zident on 2011-10-04
try this [https://answers.launchpad.net/ubuntu/+question/14278](https://answers.launchpad.net/ubuntu/+question/14278)

---

### Post by seawolf167 on 2011-10-04
Here is the [Mount how-to]("https://help.ubuntu.com/community/Mount").

In general:

```
sudo mkdir /path/to/mount-point-name
sudo mount -t cd9660 /dev/cdrom /path/to/mount-point/name
```

note that /path/to/mount-point-name is usually /mnt/cdrom for cd drives, but edit as needed.

---

