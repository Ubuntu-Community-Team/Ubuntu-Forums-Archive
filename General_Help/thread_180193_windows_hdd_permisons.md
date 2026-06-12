---
title: "windows hdd permisons"
date: 2006-05-21
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-21
hey all i just mouted my windows hdd and i am unable to write to the drive i cant chage the permisions because it says im not the onwer ( wierd eh in same comp but i dont own it) neway does ne1 know how to make it so i can write to it or change permisions etc?

---

### Post by aysiu on 2006-05-21
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bullgr on 2006-05-22
I supposed you have mount the disk correctly (see [http://ubuntuguide.org/)](http://ubuntuguide.org/)).

If the disk is formated in ntfs filesystem, then forget it, ntfs is read-only in linux (for now).

If it's formated in fat, then try to change the permissions for read-write to all user's. Open a terminal and type...
> sudo chmod 777 /media/c
...and give your root password.

Note that you must already give a mount-point to auto mount the disk. Put your's mount-point instead of "/media/c" in the command (mine is for example /mnt/c).

Hope i help.

---

