---
title: "Mounting type fuseblk"
date: 2010-08-22
forum: General Help
---

### Post by Kungen7 on 2010-08-22
Im trying to add my WD Elements external disk to my fstab file so it mounts on boot and keeps it that way. Now i have to use thunar (using Awesome WM) to mount it which i simply dont like.

Adding the disk to fstab wouldnt be too dificult  if it wasnt for the filesystem being fuseblk. Just making fuseblk the type dosnt work too well, i imagine you have to specify the blksize or something but cant get the hang of it.

When i mount it in thunar it comes up like the following with the mount command:
```
/dev/sdc1 on /media/Elements type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```


Anyone know how?

Thanks,
Kungen

---

