---
title: "Can't mount writable filesystem"
date: 2006-05-18
forum: General Help
---

### Post by Calle on 2006-05-18
Hi!
Getting strange error when trying to mount my /dev/hda5 to /home. 
> calle@concrete:/$ mount
/dev/hdb1 on / type ext3 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda5 on /home type ext3 (ro)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

> calle@concrete:/$ sudo mount -t ext3 -o rw,remount /dev/hda5 /home
mount: block device /dev/hda5 is write-protected, mounting read-only
What the hell is this? I don't see why I cant remount this partition.

Thanks in advance

---

### Post by jon_z on 2006-05-18
this is happening on my other hard drive with the / mountpoint heh.. says its only readable.

---

### Post by bullgr on 2006-05-18
Because in don't know what you already done, i go from the begining...

1. First of all make a mount point. Open a terminal and type...
> sudo mkdir /media/d
(or anythere else you want, like /mnt/d)

2. In a terminal again type...
> sudo gedit /etc/fstab
Here will you give the parameters to auto mount the disk everytime you boot
> /dev/hda5  /media/d  ext3  defaults  0 0

3. And for sure that you have full read-write permitions, in a terminal again type...
> sudo chmod 777 /media/d

That's all, hope that i help

---

### Post by Calle on 2006-05-18
Thanks a lot!

---

