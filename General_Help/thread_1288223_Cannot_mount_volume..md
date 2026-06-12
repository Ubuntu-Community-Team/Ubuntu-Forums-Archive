---
title: "Cannot mount volume."
date: 2009-10-11
forum: General Help
---

### Post by suffer1989 on 2009-10-11
Never happened to me before. I Inserted my memory card from my camera into the memorycard slot on my laptop, and i got :

> You are not privileged to mount the volume 'CANON_DC'.

After a bit, this came up 
> 
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Its never happened before, just now. I tried googling, but i cant find any cases for memory cards. 

Thanks in advance.


Oh, im running ubuntu 8.10 , and the output for ```
 gksudo gedit /etc/fstab

```

Is
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda5 :
UUID=a9ae4f17-db1c-4097-bb2b-e3ff1223b779	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/mmcblk0p1 :
UUID=6DF4-7F1A	/media/CANON_DC	vfat	defaults,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush	0	2
#Entry for /dev/sda1 :
UUID=6EDC5CFF559C1016	/media/mediadrive	ntfs-3g	defaults	0	0
#Entry for /dev/sda6 :
UUID=c8e02d97-0725-49b7-8787-f98c3394ae26	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


```

---

### Post by suffer1989 on 2009-10-11
Bump ??

---

### Post by delcypher on 2009-10-11
Sounds like you don't have permission to use the camera.

First thing to try
1. Edit /etc/fstab using sudo
2. Change ```
UID=6DF4-7F1A	/media/CANON_DC	vfat	defaults,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush	0	2

```
to
```
UID=6DF4-7F1A	/media/CANON_DC	vfat	defaults,user,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush	0	2

```

3. Make sure you've created the directory /media/CANON_DC (mounting will fail if it doesn't exist)
```
sudo mkdir /media/CANON_DC
```

4. Run
```
sudo mount -a
```
This will read /etc/fstab and mount filesystems that are marked to be automatically mounted (and that are not already mounted)

and see what the output is.

I don't this will fix your problem though as the "defaults" option includes user and that you had to be root to mount the filesystem



Second thing to check
1. System > Administration > Users and Groups
2. click the "Unlock" button, it will prompt you for the root password
3. Select your user and click the "properties" button
4. Click on the user tab, make sure you have everything ticked (technically not all those are necessary, but it's probably easier if you have them all ticked)

5. Once you've done that comment (# symbol) your CANON_DC line in /etc/fstab file. I've found that the fstab line interferes with HAL's mounting procedure.
6. Remove the old mount point you made (HAL automatically makes it's own)
```
sudo rmdir /media/CANON_DC
```
7. Make sure the CANON_DC device is unmounted, if it's still mounted via the /etc/fstab then run
```
sudo umount /media/CANON_DC
```
8. Remove your device and plug it back in, now try to access the device.

Let us know how you get on.

---

### Post by suffer1989 on 2009-10-11
> **delcypher said:**
> Sounds like you don't have permission to use the camera.

First thing to try
1. Edit /etc/fstab using sudo
2. Change ```
UID=6DF4-7F1A	/media/CANON_DC	vfat	defaults,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush	0	2

```
to
```
UID=6DF4-7F1A	/media/CANON_DC	vfat	defaults,user,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush	0	2

```

3. Make sure you've created the directory /media/CANON_DC (mounting will fail if it doesn't exist)
```
sudo mkdir /media/CANON_DC
```

4. Run
```
sudo mount -a
```
This will read /etc/fstab and mount filesystems that are marked to be automatically mounted (and that are not already mounted)

and see what the output is.

I don't this will fix your problem though as the "defaults" option includes user and that you had to be root to mount the filesystem



Second thing to check
1. System > Administration > Users and Groups
2. click the "Unlock" button, it will prompt you for the root password
3. Select your user and click the "properties" button
4. Click on the user tab, make sure you have everything ticked (technically not all those are necessary, but it's probably easier if you have them all ticked)

5. Once you've done that comment (# symbol) your CANON_DC line in /etc/fstab file. I've found that the fstab line interferes with HAL's mounting procedure.
6. Remove the old mount point you made (HAL automatically makes it's own)
```
sudo rmdir /media/CANON_DC
```
7. Make sure the CANON_DC device is unmounted, if it's still mounted via the /etc/fstab then run
```
sudo umount /media/CANON_DC
```
8. Remove your device and plug it back in, now try to access the device.

Let us know how you get on.

Thanks, thats helped. Im gonna try doing some stuff, and rebooting a few times, then if it works out fine, give it the all clear. thanks for the help :D..

---

