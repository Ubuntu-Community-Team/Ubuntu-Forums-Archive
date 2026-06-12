---
title: "Grub2 Can't detect Windows XP! Also cant mount C"
date: 2010-01-17
forum: General Help
---

### Post by idodos on 2010-01-17
As the Title states, "update-grub" does not detect the windows xp partition on /media/sda1. And, when I attempt to mount it from teminal nothing happens, and from nautilus I receive the following error: "Error mounting: mount exited with exit code 2:
mount: only root can mount /dev/sda1 on /media/sda1" I am root.

Help! :(

---

### Post by Leppie on 2010-01-17
which vesion of grub are you using? you can find the version number like this:
```
sudo grub-install -v
```how did you become root? the root account is disabled by default in ubuntu, instead the sudo command is used.

---

### Post by idodos on 2010-01-17
> **Leppie said:**
> which vesion of grub are you using? you can find the version number like this:
```
sudo grub-install -v
```how did you become root? the root account is disabled by default in ubuntu, instead the sudo command is used.

(GNU GRUB 1.97~beta4)
However, The problem is probably related to the fact I can't mount the /dev/sda1 partition where windows is installed..

Thanks for replying!

---

### Post by Leppie on 2010-01-17
could you post the your fstab?
```
cat /etc/fstab
```

---

### Post by idodos on 2010-01-17
> **Leppie said:**
> could you post the your fstab?
```
cat /etc/fstab
```

```
root@Raisin-Desktop:/boot/grub# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sdb2 during installation
UUID=41c45202-1a94-4bb9-b154-67e987dfbf79  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sdb5 during installation
UUID=6513d48c-d00b-484e-ab55-205010a3f715  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0 
```

---

### Post by Leppie on 2010-01-17
try mounting from the cli:
```
# mkdir /media/sda1
# mount -t ntfs /dev/sda1 /media/sda1
```

---

### Post by idodos on 2010-01-17
> **Leppie said:**
> try mounting from the cli:
```
# mkdir /media/sda1
# mount -t ntfs /dev/sda1 /media/sda1
```

No go..
I booted the computer using Bart PE which is basically a stripped down version of windows that boots from a cd. It can't open that partition.. I guess it just died..

Thanks for the help anyways

---

### Post by Leppie on 2010-01-17
check the partition for errors with chkdsk or something similar. you can find such applications on images like [Ultimate Boot CD]("http://www.ubcd4win.com/downloads.htm")
alternatively you may want to check [testdisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by idodos on 2010-01-17
> **Leppie said:**
> check the partition for errors with chkdsk or something similar. you can find such applications on images like [Ultimate Boot CD]("http://www.ubcd4win.com/downloads.htm")
alternatively you may want to check [testdisk]("http://www.cgsecurity.org/wiki/TestDisk")

Yeah I'm downloading that Ultimate Boot CD right now. Thanks!

---

### Post by Leppie on 2010-01-17
> **idodos said:**
> Yeah I'm downloading that Ultimate Boot CD right now. Thanks!
you're welcome, let us know if it worked ;)

---

