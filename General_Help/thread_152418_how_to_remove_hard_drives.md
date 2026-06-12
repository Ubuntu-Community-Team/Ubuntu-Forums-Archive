---
title: "how to remove hard drives"
date: 2006-03-29
forum: General Help
---

### Post by R Audano on 2006-03-29
Hello I am currently running a web server with Ubuntu 5.04. The machine has two 2 SATA hard drives and 2 IDE drives. I wish to remove the two IDE drives because of reliability concerns...
The IDE drives are /Home, and /Home/2

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda8       /bob            ext3    defaults        0       2
/dev/sda1       /boot           ext3    defaults        0       2
/dev/hda5       /home           ext3    defaults        0       2
/dev/hdb5       /home/2         ext3    defaults        0       2
/dev/sda7       /tmp            ext3    defaults        0       2
/dev/sda6       /usr            ext3    defaults        0       2
/dev/sdb5       /var            ext3    defaults        0       2
/dev/sda5       /var/mail       ext3    defaults        0       2
/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Can someone please advise me how to perform this without completing a reload? I have someone who can remove the drives in my absence. I am currently stationed away from the server, and am unable to reload software etc...

V/R
Robert

---

### Post by aysiu on 2006-03-29
Wouldn't you just do this? ```
sudo umount /dev/hda5
sudo umount /dev/hdb5
sudo nano /etc/fstab
``` Delete those two lines and save. Remove the drives.

---

### Post by R Audano on 2006-03-29
so, 
as root

umount /dev/hda5
umount /dev/hdb5
nano /etc/fstab

what about my /home  user data will it be needed by the kernel? The desktop is broken anyway, so can I assume that that data is no longer needed?

---

### Post by aysiu on 2006-03-29
[QUOTE=R Audano]
what about my /home  user data will it be needed by the kernel? The desktop is broken anyway, so can I assume that that data is no longer needed?[/QUOTE] Hm. Good point. You need a home. What you should do is copy the configuration files only (not data files) to a new /home folder on your / partition and then unmount and remove the /home folder from the /etc/fstab.

If there's no /home mount point in /etc/fstab, Ubuntu will assume that /home is a regular folder on the / partition.

---

### Post by R Audano on 2006-03-29
Thanks for the assistance...

 I created a new "home" folder in the /root directory copied the contents over to the new folder. Then commented out the 2 ide hard drive entries in the /etc/fstab. I crossed my fingers and commanded a reboot... 
Now all I have to do is get the two Maxtors disconnected during the next shutdown..
The machine rebooted and is up and running! :D 


Would it be possible to move everything to sda1, then use sda2 for raid 1 backup?

---

### Post by aysiu on 2006-03-29
[QUOTE=R Audano]
Would it be possible to move everything to sda1, then use sda2 for raid 1 backup?[/QUOTE] Yeah, but you might need to use a live CD for that...

---

### Post by R Audano on 2006-03-30
after trying to disconnect hard drives the system is getting an grub error 17.
How can we edit my grub boot loader?

---

