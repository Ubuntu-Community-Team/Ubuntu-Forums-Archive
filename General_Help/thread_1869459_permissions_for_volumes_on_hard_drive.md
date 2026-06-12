---
title: "permissions for volumes on hard drive"
date: 2011-10-25
forum: General Help
---

### Post by sidewalkcynic on 2011-10-25
Ubuntu 11.10 won't allow me to change permissions of volumes that I had designated mount points for at install. The volumes show up in the Nautilus sidebar as volumes and the mount points they were assigned ( /media/name ), and I can access the volumes, but I cannot change any of the folders.

I have changed all of the permissions as root, and applied it to all folders and sub-folders - as I have .done in the past when installing an upgrade system.

When I access the volumes the lock icons are on all the folders

---

### Post by hhh on 2011-10-25
I think you can change permissions all day long and it won't let you alter files and folders there, since the drive is still mounted under /media. To make changes, you'll have to access them the way you would any system files, Alt+F2 and then...```
gksu nautilus
```

---

### Post by garvinrick4 on 2011-10-25
are they EXT or NTFS

If EXT
sudo chown -R rick:rick /media/name
Directory in /media/name/:
sudo chown -R rick:rick /media/name/Data

---

### Post by WorMzy on 2011-10-25
To extend on what Gavinrick4 said, if they're NTFS (or FAT) partitions, then see if the following tutorial sees you right: [HOWTO: Mount NTFS partitions with specific ownership/permissions]("http://ubuntuforums.org/showthread.php?t=1604251").

---

### Post by hhh on 2011-10-25
Thanks for the back-up replies, always something to learn.

---

### Post by sidewalkcynic on 2011-10-26
They were formatted ext4.

I am wondering if I did something as root when I set up the folders and files from  zip files on the volumes; anyway, I was wrong in my description; the volumes will let me add and delete new files, as user. So, I can delete the files as root and just replenish the files from my archive, as a user, and that should be the solution.

Thanks for help

---

