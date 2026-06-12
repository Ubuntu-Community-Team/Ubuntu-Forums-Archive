---
title: "Ubuntu 10.04 server can not boot up correctly any more"
date: 2010-10-04
forum: General Help
---

### Post by seastone on 2010-10-04
Here were what I did last Friday:
1) "sudo fdisk /dev/sda" to create a a new partition (dev/sda4)
2) "sudo partprobe" to sync the partition. got an error to complain about /dev/sr1
3) "sudo mkfs -t ext3 /dev/sda4" to format the partition
4) "sudo tune2fs -l /dev/sda4 to find out UUID
5) "sudo vi /etc/fstab" to creat a new entry to add the UUID above
6) "sudo mkdir /mnt/unify"
7) "sudo mount /dev/sda4 /mnt/unify"

now the fstab file looks like
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ca8f9b51-547a-42be-9d91-ea346cfc3b39 /               ext3    defaults,error
s=remount-ro,relatime 0       1
# /dev/sda5
UUID=a049e8e1-c769-436a-95df-a1d011cf68e3 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/sda3
UUID=e5e1be7b-9bcc-4852-8a23-d0c43ebc6525 /               ext3    defaults.error
s=remount-ro,relatime 0       1
# /dev/sda4
UUID=fdc3e8cd-4092-4352-bb79-837d7652d319 /               ext3    defaults.error
s=remount-ro,relatime 0       1

Reboot the server, the I got the following error:
"**An error occurred while mounting /**" "**press S to skip or M to manual fix** **the problem**"

How can I get rid of this problem ? I am using Ubuntu 10.04. Which command caused this issue ?

Here is the fstab file.
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3890    31246393+  83  Linux
/dev/sda2            3891        4984     8787555    5  Extended
/dev/sda3            4985       18039   104864287+  83  Linux
/dev/sda4           18040       26000    63946732+  83  Linux
/dev/sda5            3891        4984     8787523+  82  Linux swap / Solaris

I have run "fsck", /dev/sda1 and /dev/sda3 are all clean. no error. But the entire file system is in "read only" mode. I can not do anything. only SSH and FTP service are activated (if I choose the S in the error screen above). 

Thanks a lot

---

### Post by dtfinch on 2010-10-04
Three of your fstab entries say to mount to "/". Only one of them should. The others need to be mounted to subfolders.

---

### Post by seastone on 2010-10-04
thanks.

how to modify the fstab file now ? Each time, when I modify the fstab file, the system says it is read only. 

It looks like the entire file system is locked to "read only". How to get rid of this ? Using rescue CD ?

---

### Post by dtfinch on 2010-10-04
It looks like "mount -n -o remount,rw /" should do it, but I've always resorted to boot cds or usb instead, partly because I couldn't remember the command. The "-n" tells it to not try to write to /etc/mtab, which it can't do when / is read only.

---

### Post by seastone on 2010-10-04
Yes, the command works.

Thanks a lot.

I own you a couple of beers.

---

