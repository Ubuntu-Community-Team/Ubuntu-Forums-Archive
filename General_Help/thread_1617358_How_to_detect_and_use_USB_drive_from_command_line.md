---
title: "How to detect and use USB drive from command line?"
date: 2010-11-09
forum: General Help
---

### Post by MMAMail on 2010-11-09
For some reason my GUI no longer starts up :(

So I need to write something to a usb stick from my hard drive, from the terminal.

1. How can I check if my usb drive is detected and usable?

2. What path do I copy files to for them to appear on my usb stick?

Many thanks,

---

### Post by ki4jgt on 2010-11-09
To detect it:
lsusb you'll see a list of your USB ports and whats on them

To surf it:
cd /media/
and then ls the media directory. it will have a alphanumeric folder for all external media

---

### Post by MMAMail on 2010-11-09
lsusb works and I get:

```
Bus 002 Device 002: ID 0781:5567 SanDisk Corp. 
```

but when I go to /media/ 
there's only an entry for cdrom there :(

Is there some mounting or ??? I need to do before it appears there?

---

### Post by ki4jgt on 2010-11-09
Create your mount point:
> 
sudo mkdir /media/foldername

Mount your drive:
> 
if the device is FAT:

sudo mount -t vfat /dev/sdb1 /media/foldername -o uid=1000,gid=100,utf8,dmask=027,fmask=137

Be sure to change /dev/sdb1 to what ever the usb device is usually sdb1

If it is NTFS:

sudo mount -t ntfs-3g /dev/sdb1 /media/foldername

To unmount:

> sudo umount /dev/sdb1
--or--
sudo umount /media/foldername

---

