---
title: "How do i remove write protect on another disk partition?"
date: 2009-12-24
forum: General Help
---

### Post by Niclikesfilming on 2009-12-24
How do i remove a write protect on a disk partition, the second disk partition is Mac OSX Extended, and the partition running Ubuntu is FAT32, i need to write on the other hard drive to save my operating system but i cant write onto it succesfuly.

Any help would be appreciated!

Thanks, Nic

Thanks guys, SOLVED!

---

### Post by cariboo on 2009-12-24
You can change it to world read/write by opening a terminal and typing:

```
sudo chmod -R 777 /mountpoint
```

where mountpoint = where you have the apple partition mounted.

---

### Post by Mahngiel on 2009-12-24
you can also:

sudo gedit /etc/fstab

and change the permissions in the file to 

utf8,umask=007,uid=1000,gid=46

---

