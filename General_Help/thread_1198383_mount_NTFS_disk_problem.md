---
title: "mount NTFS disk problem"
date: 2009-06-27
forum: General Help
---

### Post by 4l1da on 2009-06-27
I have xubuntu on my PC ( because very old and slow computer).
The problem here is that my new  Xubuntu (9.04) can't detect the NTFS disk.

david@DD:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3048    23042848+   5  Extended
/dev/sda2   *        3049        5167    16019608+   7  HPFS/NTFS
/dev/sda5               1         161     1217097   82  Linux swap / Solaris
/dev/sda6             162        1711    11717968+  83  Linux
/dev/sda7            1712        3048    10107688+  83  Linux
david@DD:~$ 

I have some data on /dev/sda2 NTFS. 
I try this, but its not work for me.
[http://ubuntuforums.org/showthread.php?t=785263&highlight=sudo+fdisk](http://ubuntuforums.org/showthread.php?t=785263&highlight=sudo+fdisk)  

So, Linux-gurus... how do i solve this problem?

---

### Post by ~sHyLoCk~ on 2009-06-27
```
sudo apt-get install ntfs-3g
sudo mkdir /windows
sudo gedit /etc/fstab
```
Add an entry ```
/dev/sda2  /windows  ntfs-3g    defaults,noatime,rw 0  0 
```
See if this works

---

### Post by 4l1da on 2009-06-27
> **~sHyLoCk~ said:**
> ```
sudo apt-get install ntfs-3g
sudo mkdir /windows
sudo gedit /etc/fstab
```
Add an entry ```
/dev/sda2  /windows  ntfs-3g    defaults,noatime,rw 0  0 
```
See if this works

Yes it works, this  method mount my NTFS drive like folder. 

Thanks.

---

### Post by 4l1da on 2009-06-27
P.S. Just one difference 

With xubuntu we have to use 

sudo mousepad /etc/fstab

---

### Post by ~sHyLoCk~ on 2009-06-27
> **4l1da said:**
> P.S. Just one difference 

With xubuntu we have to use 

sudo mousepad /etc/fstab

oops didnt know xfce's editor..u could always use nano/vi for simplicity anywhere :)
Glad that worked!

---

