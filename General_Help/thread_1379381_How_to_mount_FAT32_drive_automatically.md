---
title: "How to mount FAT32 drive automatically?"
date: 2010-01-12
forum: General Help
---

### Post by adrian-g on 2010-01-12
Hi,
I am setting up a home server and have two hard drives. One is the main HD for system files and the other will be for personal files.

The personal HD is /dev/sdb.

I know I have to edit fstab in order to get it to mount automatically at boot, but I am having trouble with the commands.

I would like for it to mount at boot and have full read-write access from any user.

---

### Post by drs305 on 2010-01-12
This is a very good link for setting up your fstab file:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

This would work, you would have to make the mountpoint (sudo mkdir /media/mountpoint) and then add this to fstab:
> 
UUID= XXX-XXXXXXXXXXx /media/mountpoint vfat user,auto,uid=1000,umask=000,utf8 0 0

Of course, change *mountpoint* to whatever name you want to use, and substitute the correct UUID. You can get the UUID when the device is mounted by running:  sudo blkid
It also assumes you are user 1000 (the first user on the machine).

---

### Post by colobix on 2010-01-12
Here's what you do

First, make disk folder

Code:

sudo mkdir /media/ntfs /media/fat32

Backup and open fstab for editing

Code:

sudo cp /etc/fstab /etc/fstab.2909
gksudo gedit /etc/fstab

And add this line to the end of the file

Code:

/dev/sdc1 /media/fat32 vfat defaults,user,dmask=027,fmask=137 0 0

Should do it for you.

---

### Post by adrian-g on 2010-01-12
Thank you!

---

