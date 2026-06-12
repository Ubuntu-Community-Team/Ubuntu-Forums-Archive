---
title: "/windows partition belongs to root"
date: 2009-12-04
forum: General Help
---

### Post by blurred on 2009-12-04
i freshly installed karmic kde.i m hanving to ntfs partitions which i mounted (during installation)as /windows/XP and /windows/NTFS..my problem is that i m unable to share the folders belonging them.more over the owner of those partitions are root.my question is how can i become owner(which i m very much;))of those partitions and render them sharable..plz help..thnx..

---

### Post by jbrown96 on 2009-12-04
You should not be mounting those partitions in /windows. That's not an appropriate place.

The best location would be in your home folder. The next best location would be in /media. If you mount in your home folder, there shouldn't be any permission problems. In /media, you will still have to fix the permissions, but at least they will be mounted in the correct location.

---

### Post by oldfred on 2009-12-04
See these links for info:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

This is one of my entries that works:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0

---

### Post by blurred on 2009-12-04
hi..thnx for the quick reply.i m bit naive..i dont really understand how to mount my ntfs partitions to home..which mount point shud i assign to it during installation..during installation i gave assingned them /windows/XP...thnx a lot..

---

### Post by jbrown96 on 2009-12-04
It you go into your home folder, just create a folder called windows, xp, or whatever you want (if you have two drives, then create two folders). Then you need to open and modify fstab. Open a terminal (Apps-->Accessories) and run the follwoing commands. 

1) backup your fstab ```
sudo cp /etc/fstab /etc/fstab.backup
```
2) Modify fstab ```
gksu /etc/fstab
``` This will open a text editor that looks something like this > # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=4899ec0f-7b97-43cd-8d93-688e1a1d8ade /home           ext4    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
 Yours will have more entries. Just find the lines that have /windows/xp and /windows/ntfs that start with UUID=... Then change /windows/xp to /home/YOUR_USERNAME/xp (or whatever you name the folder) and repeat for /windows/ntfs. Then save and exit. Reboot for the changes to take effect. Now you should have access to those your files in your home folder. 

If you don't understand those directions. Then Copy and paste your /etc/fstab file (you can copy and paste it from the text editor), and I'll edit it for you. Just be sure to put it in Quote tags. There's a button at the top of the box where you post a message that looks like a text bubble, just paste in between the [quote and [/quote

---

### Post by blurred on 2009-12-04
thanku very much sir...that was awesome..i rebooted and found those partitions as folders in my home directory..only 2 problems remain..
1-i cannot share them as root is still the owner..
2-i am still having /windows in my root dir..
plz help me eliminating these remaining problems...thnx..

by the way foloowing is my fstab text...
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=8a4153d7-d245-4b66-8624-a43e32ae4c82 /               ext4    errors=remount-ro 0       1
# /windows/mirage was on /dev/sda1 during installation
UUID=24A8FB3CA8FB0AD6 /home/blurred/mirage ntfs    defaults,umask=007,gid=46 0       0
# /windows/oasis was on /dev/sda8 during installation
UUID=520C8CC90C8CA995 /home/blurred/oasis  ntfs    defaults,umask=007,gid=46 0       0
# /windows/ocean was on /dev/sda5 during installation
UUID=9638F34F38F32D3D /home/blurred/ocean  ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=73a9d8fd-78d7-4b3e-881e-dd6b131a3dee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by sisco311 on 2009-12-04
The owner is root, but the the files/directories are writable by the plugdev(gid 46) group.

To grant write permissions for a user, add the user to the plugdev group:
```
sudo adduser username plugdev
```
where username is the login name of the user.  

The mount point doesn't matter, you can mount the partitions anywhere in the file system. I would mount the partitions in /media (/media/XP and /media/NTFS), since this directories will show up in the Places menu. 

To create the mount points in /media you need root permissions:
i.e.
```
sudo mkdir /media/XP
```
Before mounting the partitions you may have to set the group ownership of the mount point:
```
sudo chgrp plugdev /media/XP
```

---

### Post by jbrown96 on 2009-12-04
To remove /windows ```
sudo rm -rf /windows
``` That will delete the folder and it's contents, so double check that everything is mounted in your home folder. 

To fix the the permission problems ```
sudo chmod o+rw ./windows
``` repeat that with the other folders if you created them.

---

### Post by sisco311 on 2009-12-04
> **jbrown96 said:**
> That will delete the folder and it's contents, so double check that everything is mounted in your home folder. 

To fix the the permission problems ```
sudo chmod o+rw ./windows
``` repeat that with the other folders if you created them.

rm -rf is a little overkill in this case.


rmdir removes empty directories:
```
sudo rmdir /windows
```

---

### Post by blurred on 2009-12-04
this is my first educative lab work on linux under a wise guru..thanku so much sir..i m der to stay wid linux..bbyee /windows...

---

