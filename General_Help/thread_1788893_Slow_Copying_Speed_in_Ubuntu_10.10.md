---
title: "Slow Copying Speed in Ubuntu 10.10"
date: 2011-06-23
forum: General Help
---

### Post by community on 2011-06-23
I am using Ubuntu 10.10.It is very tiresome for me to copy large files between different drives.Can anyone help?

---

### Post by dandnsmith on 2011-06-23
- put them where you want them initially?
- use links so you don't have to copy them to access?

---

### Post by mistyautom on 2011-06-23
I have noticed this too, when I am copying large amounts of data from an external drive that I have plugged into a usb drive.  For some reason if I restart the computer 1 or 2 times with the drive plugged in, the copying speed will increase to a much more anticipated speed.  So anyway, my advice would be to restart your computer 1 or 2 times with the drive plugged in, to increase the copying speed.

------------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages

---

### Post by haqking on 2011-06-23
what are the filesystems between the drives ?

are they all the same, i know there can be a lag if one is NTFS, hopefully they are all  ext2, 3 or 4 ?

---

### Post by Gyokuro on 2011-06-23
Depends on the drive too - however copying files over USB is in general slow (for my taste ;) ) as copying depends on the read speed of the drive and not much data can be cached but when data gets written, the systems use at first it's buffer and swap out later the files to the receiver (USB driver,...) and here drive can make use of it's on buffer cache too. I can only suggest that you use two identical filesystems for data sharing (linux box ext3/4 /  USB ext3/ext4) and before you start a big copy action you can sync the system in terminal via the sync command.

HTH

---

### Post by community on 2011-07-17
It takes a lot of time for me to copy files from hdd to hdd.All the drives are of ntfs file systems.But copying is fast in the case of transfering files from usb to hdd/hdd to usb.What may be the reason???

---

