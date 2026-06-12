---
title: "help mounting hd"
date: 2010-07-20
forum: General Help
---

### Post by alexe5 on 2010-07-20
Hey i ran this command. but how can i undo it? i did it to mount my hd in the startup but id didnt work, so i want to undo it, and if somebody can tell how to make my hd to be mounted since the startup i would really appreciate it
 	Code:
 	sudo apt-get install ntfs-3g 
Then, create the mount point for that device:

 	Code:
 	sudo mkdir /media/musicdrive 
Open /etc/fstab file for editing:

 	Code:
 	gksudo gedit /etc/fstab 
and add the line of code below to the last part of the file:

 	Quote:
 	 	 		 			 				/dev/sdb1 /media/musicdrive ntfs-3g defaults 0 0 			 		  	 	 
Save and Close the File: Drop to your terminal and issue the  command:

 	Code:
 	sudo mount -a

---

### Post by djyoung4 on 2010-07-20
> **alexe5 said:**
> Hey i ran this command. but how can i undo it? i did it to mount my hd in the startup but id didnt work, so i want to undo it, and if somebody can tell how to make my hd to be mounted since the startup i would really appreciate it
 	Code:
 	sudo apt-get install ntfs-3g 
Then, create the mount point for that device:

 	Code:
 	sudo mkdir /media/musicdrive 
Open /etc/fstab file for editing:

 	Code:
 	gksudo gedit /etc/fstab 
and add the line of code below to the last part of the file:

 	Quote:
 	 	 		 			 				/dev/sdb1 /media/musicdrive ntfs-3g defaults 0 0 			 		  	 	 
Save and Close the File: Drop to your terminal and issue the  command:

 	Code:
 	sudo mount -a
post your fstab file for us
```
gksudo gedit /etc/fstab
```
post what is in the file

---

### Post by alexe5 on 2010-07-20
that is what appeared in the fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=df95b09c-5450-4e5a-bfff-d5a738c283ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f3623eba-3bab-4d29-8f63-dc6c1c708018 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/musicdrive ntfs-3g defaults 0 0 
```

---

### Post by alexe5 on 2010-07-20
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=df95b09c-5450-4e5a-bfff-d5a738c283ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f3623eba-3bab-4d29-8f63-dc6c1c708018 none            swap    
sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/musicdrive ntfs-3g defaults 0 0


here's an image of my fstab 
[IMG]http://img824.imageshack.us/img824/6845/screenshot11f.png[/IMG]

---

### Post by djyoung4 on 2010-07-20
Get rid of the line in red and save it
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=df95b09c-5450-4e5a-bfff-d5a738c283ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f3623eba-3bab-4d29-8f63-dc6c1c708018 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[COLOR="Red"]/dev/sdb1 /media/musicdrive ntfs-3g defaults 0 0[/COLOR]
```
make sure you make a backup of the original file just in case something goes wrong

---

### Post by alexe5 on 2010-07-22
thanks!!

---

