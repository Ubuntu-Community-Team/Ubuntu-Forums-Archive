---
title: "mounting ext3 with user permissions?"
date: 2006-04-19
forum: General Help
---

### Post by B3Nji on 2006-04-19
I have a really stupid question to ask, I cant seem to find the answer to. 

Basically I have 3 hard drives that were NTFS, i backed up the data, converted them to ext3. Now I want to mount the three drives with the proper permissions, at the moment i have the following in my fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/mapper/Ubuntu-root / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda1 /boot ext3 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/mapper/Ubuntu-swap_1 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5       /media/music ext3 auto,user,exec,rw,sync 0 0
/dev/hdc1       /media/video ext3 auto,user,exec,rw,sync 0 0
/dev/hdd1       /media/multimedia ext3 auto,user,exec,rw,sync 0 0 

as you can see i probably have the settings wrong for the bottom 3 hard drives. At the moment I get "you do not have permission to view this hard drive"

All i want is to access them normally through any user, read write, execute things etc. 

Thanks for your help

---

### Post by aysiu on 2006-04-19
Change these last three entries to ```
/dev/hdb5 /media/music ext3 defaults 0 0
/dev/hdc1 /media/video ext3 defaults 0 0
/dev/hdd1 /media/multimedia ext3 defaults 0 0
``` Then do this: ```
sudo chown -R b3nji:b3nji /media/music
sudo chown -R b3nji:b3nji /media/video
sudo chown -R b3nji:b3nji /media/multimedia
sudo chmod -R 775 /media/music
sudo chmod -R 775 /media/video
sudo chmod -R 775 /media/multimedia
```

---

### Post by B3Nji on 2006-04-19
[QUOTE=aysiu]Change these last three entries to ```
/dev/hdb5 /media/music ext3 defaults 0 0
/dev/hdc1 /media/video ext3 defaults 0 0
/dev/hdd1 /media/multimedia ext3 defaults 0 0
``` Then do this: ```
sudo chown -R b3nji:b3nji /media/music
sudo chown -R b3nji:b3nji /media/video
sudo chown -R b3nji:b3nji /media/multimedia
sudo chmod -R 775 /media/music
sudo chmod -R 775 /media/video
sudo chmod -R 775 /media/multimedia
```[/QUOTE]

dude you rule!

worked perfectly. Cheers for your help mate.

---

