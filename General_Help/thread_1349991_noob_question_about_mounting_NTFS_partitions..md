---
title: "noob question about mounting NTFS partitions."
date: 2009-12-08
forum: General Help
---

### Post by paranj on 2009-12-08
Hey guys, my first post :).

Anyways, so I am enjoying the 9.10 live CD right now and thought of installing it so was wondering that how can I mount my NTFS data partitions during installation so that I can use them in Ubuntu as well ?

---

### Post by TheOnlyMrK on 2009-12-08
> **paranj said:**
> Hey guys, my first post :).

Anyways, so I am enjoying the 9.10 live CD right now and thought of installing it so was wondering that how can I mount my NTFS data partitions during installation so that I can use them in Ubuntu as well ?

Do you mean you want to install Ubuntu IN the NTFS partitions or just need to access them for some files in them? Because I believe Ubuntu can't be installed on NTFS, or any Windows file system really.

---

### Post by paranj on 2009-12-08
> **TheOnlyMrK said:**
> Do you mean you want to install Ubuntu IN the NTFS partitions or just need to access them for some files in them? Because I believe Ubuntu can't be installed on NTFS, or any Windows file system really.

Nope, I just want read/write access to them. Ofcourse Ubuntu can't be installed on a NTFS part.

---

### Post by fluffman86 on 2009-12-08
Check your Places menu, near the top left of the monitor.  Things are labeled differently in Ubuntu: here they will be "200 GB Media" or maybe "HP Pavillion" or something similar, other places they will be seen as "sda1" or "sdb4" or similar, with the "a1" representing the first hard drive, first partition and "b4" representing the second drive, 4th partition, and so on.  You will never see things labeled as your C: drive or E: drive or whatever.

If you click on them and get an error, read it carefully and it will tell you what to do.  You may see something like "do 'mount /dev/sda2 /media/sda2 -t ntfs-3g -o force'"

If so, open a terminal from Applications > Accessories, and enter the following:
```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2 -t ntfs-3g -o force
```
replacing the "a2" in each command with the information given in the error.

---

### Post by paranj on 2009-12-08
> **fluffman86 said:**
> Check your Places menu, near the top left of the monitor.  Things are labeled differently in Ubuntu: here they will be "200 GB Media" or maybe "HP Pavillion" or something similar, other places they will be seen as "sda1" or "sdb4" or similar, with the "a1" representing the first hard drive, first partition and "b4" representing the second drive, 4th partition, and so on.  You will never see things labeled as your C: drive or E: drive or whatever.

If you click on them and get an error, read it carefully and it will tell you what to do.  You may see something like "do 'mount /dev/sda2 /media/sda2 -t ntfs-3g -o force'"

If so, open a terminal from Applications > Accessories, and enter the following:
```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2 -t ntfs-3g -o force
```replacing the "a2" in each command with the information given in the error.

Cool! Thanks! Will try it... installation just started.

---

### Post by Ginsu543 on 2009-12-09
You should be able to mount NTFS drives/partitions by simply clicking on them in "Places" or in Nautilus. You may have to enter your password to gain access, but you only have to do this once per session.

---

### Post by iMisspell on 2009-12-09
If you want to mount drives/shares from other machines on your local network look into, 'fstab'
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

```
sudo gedit /etc/fstab
```


)

---

### Post by Leppie on 2009-12-09
If you install ntfs-config and enable the user accounts that need ntfs access to use fuse, you don't need to edit your fstab.
Only thing is that thunar does not show the not yet mounted ntfs partitions.

---

