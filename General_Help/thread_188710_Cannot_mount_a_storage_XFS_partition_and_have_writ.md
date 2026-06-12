---
title: "Cannot mount a storage XFS partition and have write privleges"
date: 2006-06-04
forum: General Help
---

### Post by clarke.rainey on 2006-06-04
I have been reading through the forums trying to figure this out before I bothered everyone with it... but I have not found an answer that works so far...

I had a second blank HD in my comp /dev/sdb so I used

mkfs -t xfs /dev/sdb1 

then

sudo mkdir /mnt/60GB

then I pulled a

sudo mount -t xfs /dev/sdb1 /mnt/60GB

then I have no write privs what so ever...

I have tried chmoding the /mnt/60GB directory to 777

but other than that there is not much that I could do... 


so in the end... I would like to be able to 

1) Have read write access to that xfs drive.
2) Have a link to that drive on my desktop or in the "Computer" part of the Places menu.


thanks for any help that comes my way!... if not... I have plenty of storage for a while... so I can try and figure it out later...


forgot to add this (I know that I have not added anything to it for that drive/partition, I was just going to wait till I figured out what to do...)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           reiserfs defaults        0       2
/dev/sda1       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by blueberrycheesecake on 2006-06-07
i have the very same problem.

but the thing is my second HD contains mp3s

could somebody please help. :(

---

### Post by Ares Drake on 2006-08-20
Hey,

just ran into the very same problem. You two found a solution yet? If so, please let me know, thx!

---

### Post by The Uniphobiac on 2006-08-20
check the permissions of your mount directory before you mount the partition.

```
ls -l
```

If they are correct, not sure what to do next.

---

### Post by gregb49 on 2006-08-20
I have a similar problem with a USB disk formatted as win32 which contains all my data. I can read and write to it using its host computer, but not from a networked computer (both Ubuntu 606). Using 
```
sudo chmod 777 /dev/sda1
```
I have managed to change the permissions to 755 (not 777) and can now read the disk over the network but cannot write to it. Running
```
sudo nautilus
```
did not allow me to change the permissions for some reasons. To be technical, the ticks wouldn't stay in the 'Write' boxes.    
Greg

---

### Post by gregb49 on 2006-08-22
BTW There seems to be a similar thread at [http://www.ubuntuforums.org/showthread.php?t=240675]("http://www.ubuntuforums.org/showthread.php?t=240675") "Permission to write on a external USB disc". Greg

---

