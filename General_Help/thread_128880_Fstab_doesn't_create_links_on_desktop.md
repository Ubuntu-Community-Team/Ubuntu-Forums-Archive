---
title: "Fstab doesn't create links on desktop"
date: 2006-02-12
forum: General Help
---

### Post by sammydee on 2006-02-12
Hi. I recently messed around a lot with my ubuntu system, including copying all files from one drive to another and swapping round some hard disks. I had to change the fstab for it all to work, and everything ets mounted ok, but the drives are no longer displayed on the desktop or as an option with filesystem and home (know what I mean?)

Why is this?

Sam

---

### Post by Protex on 2006-02-12
In order for that to happen the drives have to have a mount point under /media.

Your CDROM mount point is /media/cdrom. That is why it shows up on the desktop.

---

### Post by sammydee on 2006-02-12
Aaaaah! That explains a lot! Can I have two mount points for each drive? How would I set this out in fstab?

Thanks!

Sam

---

### Post by sammydee on 2006-02-12
Don't worry, two seconds of research and I've sorted it. Thansks for your help!

sam

---

### Post by Protex on 2006-02-12
Well I just tried and it told me that the line was bad.

There really isn't a reason though, if you have it mounted at lets say /media/hdb1, and you also want it to be in /home/user/multimedia, then just create a shortcut...

=D

---

### Post by xfran on 2008-01-12
Hi there,

I have just updated feisty to gutsy and ...

I have the same problem, the drives are no longer displayed on the desktop, and I cant add the icons on the desktop. The units are properly mounted, in /media, and they have the 'user' option, so none of those things solved my issue.

my fstab in case st can be changed there for Kde to show the icons in the desktop ...


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=abc625bf-c016-44d4-b308-f7d47b035a34 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7ECC869F11F839F9 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=05d15c1f-5dfd-478c-8b2b-2afa0474036e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=46DB-3B18 /media/data vfat user,rw,uid=1000,gid=1000 0 2

```

Please help !
Cheers!

---

