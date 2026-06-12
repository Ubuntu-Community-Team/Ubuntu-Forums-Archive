---
title: "USB device entries in fstab in Ubuntu 10.10"
date: 2010-12-11
forum: General Help
---

### Post by cscj01 on 2010-12-11
I have UUID entries for USB devices in fstab in my Ubuntu 10.10.  I assume this is because I have upgraded my Ubuntu's since 8.04.  Each time I boot, I get a message saying it cannot mount the devices even though they are present.  I have to skip mounting in order to complete the boot process.  I also have two filesystems mounted at Root ( /).  See later post in this thread.

My question is, can I safely remove these entries from fstab and have Ubuntu automount the devices?  If I do so, will this get rid of the messages at boot time?  Thanks.

---

### Post by cscj01 on 2010-12-13
bump

---

### Post by cscj01 on 2010-12-18
Okay, no one has responded as of today, and I have some more information.

I have a 500 GB fixed drive partitioned with XP, Ubuntu 10.10 x64, and Swap.  I also have a 500 GB USB drive that I use to clone the fixed drive using Clonezilla for a backup.  I labeled the first two USB partitions as Win_XP and Ubuntu respectively.  I suppose the correct terminology is that I labeled the respective filesystems as shown.  There are no partition labels.

If I check the mount points using gparted or Disk Utility, I see that the Win_XP partition on the USB drive is mounted at /media/Win_XP, and the Ubuntu partition on the USB drive is mounted at /.  So, the Ubuntu partition on the USB drive is being auto-mounted at / rather than at /media/Ubuntu, which is where I understand auto-mounted USB partitions should be mounted.  The fixed disk partitions are being mounted at /media/sda1 and at / respectively.  So, I have two file systems mounted at /.

I tried to unmount the USB Ubuntu partition using GParted, but I get an error message that says

> Could not unmount /dev/sdc2

The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

How do I correct this?  I tried "sudo /dev/sdc2" but got the message "umount: /dev/sdc2: not mounted".

Here is my fstab for further information:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdc2 :
UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=709849C898498E12	/media/Data	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=C48C88E98C88D6F8	/media/sda1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sdd1	/media/C48C88E98C88D6F8__	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177	0	0
UUID=17A5-7B95	/media/C48C88E98C88D6F8	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
#Entry for /dev/sdc3 :
UUID=5b3c361f-14a1-45fa-bd52-49cfae3f331b	none	swap	sw	0	0
#Entry for /dev/sdc3 :
UUID=5b3c361f-14a1-45fa-bd52-49cfae3f331b	none	swap	sw	0	0
//cp2/g	/mnt/cp2	smbfs	iocharset=utf8,uid=1000	0	0

/dev/sdd1 is a USB stick that is not present, and the mount points assosiated with it are the ones for which I get the messages at boot.  Could this be part of my problem for which I initially posted?

---

### Post by cscj01 on 2010-12-18
I marked this as solved because I found the answer in another post.

---

