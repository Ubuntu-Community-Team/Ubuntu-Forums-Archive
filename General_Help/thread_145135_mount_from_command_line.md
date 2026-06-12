---
title: "mount from command line"
date: 2006-03-15
forum: General Help
---

### Post by evaristegalois on 2006-03-15
I like not using the gnome-terminal (I am actually tryingto use ratpoison which works pretty well) but then I have to mount my usb drive manually from the command line. The command

sudo mount -t nfs -o uid=myname,gid=users /dev/sda /home/myname/usb-disk

should do the trick but I get the error message

mount: directory to mount not in host:dir format

Inspite of much googling couldn't figure out how to fix this.

--evaristegalois

---

### Post by mlind on 2006-03-15
is that file system type **ntfs** instead of nfs?

for mounting network fileshares, you need to specify host aswell.

if you're going to do that mounting often, you can define it as
an entry in to /etc/fstab.

---

### Post by Sutekh on 2006-03-15
Yes check that its ntfs not nfs.

Also you should specify the partition you want to mount (/dev/sda1, /dev/sda2, /dev/sda6, etc) not just the device (/dev/sda)

What partition on /dev/sda are you trying to mount.

Check with ```
sudo fdisk -l
```
and change the mount command as needed.

---

### Post by Prospero2006 on 2006-03-15
You can find out what device (sda1, sdb1, etc.) by typing this:

dmesg | grep sda
dmesg | grep sdb
dmesg | grep hd

That will show you what devices are registered.

Pros

---

### Post by evaristegalois on 2006-03-16
Thanks for the quick replies. I will try it out and post the solution once I've got it down.
--evaristegalois

---

### Post by evaristegalois on 2006-03-16
<b>Solution:</b>

mount -t vfat -o uid=myname,gid=users /dev/sda1 /home/myname/usb-disk

Comments: found out that it was sda1 by using ``fdisk -l'' (thanks!); I had used the filesystem type ``vfat'' before and when it didn't work switched to ntfs (yes, the ``t'' is important -- thanks again!) -- turns out, though, that most usb drives are vfat and this is one of them. --evaristegalois

---

