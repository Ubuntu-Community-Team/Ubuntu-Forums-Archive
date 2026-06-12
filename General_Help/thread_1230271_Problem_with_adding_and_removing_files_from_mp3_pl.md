---
title: "Problem with adding and removing files from mp3 player."
date: 2009-08-03
forum: General Help
---

### Post by audriens on 2009-08-03
Hi. When i try to add files to my Acme v500x player its says :  There was an error copying the file into /media/disk-1.  ->  Error opening file '/media/disk-1/l.png': Read-only file system, and when i try to remove : The file "DSCN1904.JPG" cannot be moved to the wastebasket. ->  Error removing file: Read-only file system. How can i make file system not "read-only", but "read and writte" ?

---

### Post by nikhilk on 2009-08-03
> **audriens said:**
> Hi. When i try to add files to my Acme v500x player its says :  There was an error copying the file into /media/disk-1.  ->  Error opening file '/media/disk-1/l.png': Read-only file system, and when i try to remove : The file "DSCN1904.JPG" cannot be moved to the wastebasket. ->  Error removing file: Read-only file system. How can i make file system not "read-only", but "read and writte" ?

Post the output of these commands
```
cat /etc/fstab
```
```
sudo cat /proc/mounts
```

---

### Post by audriens on 2009-08-03
Sorry for wasting your time and server resources, with this post, because i found thread with same problem. This solve my problem : 

1. With the USB drive mounted, use the command:

 	Code:
 	mount 
to figure out which device it is. (for example, /dev/sdd1 on my computer... it will probably be different on your computer.

2. Unmount the USB device using:

 	Code:
 	sudo umount /dev/sdd1 
3. Check and repaire the errors on the USB device:

 	Code:
 	sudo fsck -r /dev/sdd1 
4. Then unplug it and plug it back in and see if it mounts correctly as read/write.

---

