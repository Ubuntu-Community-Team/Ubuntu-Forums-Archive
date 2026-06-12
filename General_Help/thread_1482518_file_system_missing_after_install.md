---
title: "file system missing after install"
date: 2010-05-13
forum: General Help
---

### Post by iggy.lax on 2010-05-13
Just installed xubuntu 9.10 
I always tend to have no more than two partitions: one for my operating system and the other for my music and other documents. After the install my music partition appears to be missing, I can usually find it in File System - media - chromo0 but now this file appears to be empty :S 
[http://http://i44.tinypic.com/18zz1c.png]("http://http//i44.tinypic.com/18zz1c.png")

GParted says that it is still there - dev/sda1 : 
[http://i39.tinypic.com/15555r5.png](http://i39.tinypic.com/15555r5.png)

this is what I have tried: 
[http://i43.tinypic.com/2q21so1.png](http://i43.tinypic.com/2q21so1.png)

I have no access to my files:confused:
Any help would be greatly appreciated,
thanks

---

### Post by blazemore on 2010-05-13
If you want to mount it, select it from the Places menu.

If you want to automount it on every startup, do this:

Open a terminal
Run the following commands:

Become root
```
sudo su
```Make the directory you want to mount the partition at (change the name to whatever you want):
```
sudo mkdir **/destination**
```Set the permissions on this directory:
```
chmod 777 **/destination**
```back up, and add the required line to /etc/fstab:
```
cp /etc/fstab /etc/fstab.old
echo "/dev/sda1 **/destination** ext3 defaults 0 1" >> /etc/fstab
```Mount it:
```
mount -a
```Stop being root (IMPORTANT)
```
exit
```

---

