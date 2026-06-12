---
title: "Mounting all filesystem"
date: 2010-03-06
forum: General Help
---

### Post by coyotemk on 2010-03-06
I'm using ubuntu 9.10, and i dont have access to my ntfs partitions, and i cant access to anyUSB flash drive. i've tried the command "mountall" and i have a error mess:
This is normally a bug in some application using the D-Bus library.
process 1955: arguments to dbus_pending_call_set_notify() were incorrect, assertion "pending != NULL" failed in file dbus-pending-call.c line 596.

i've tried to get some help, but for now no result. 
Anyone had the same probleme?

---

### Post by coyotemk on 2010-03-06
i've tried with sudo mountall and this is the error message:
swapon: /dev/disk/by-uuid/9607f5db-aa08-445e-8808-18a454803652: swapon failed: Device or resource busy
mountall: swapon /dev/disk/by-uuid/9607f5db-aa08-445e-8808-18a454803652 [1987] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/9607f5db-aa08-445e-8808-18a454803652


and i've tried to create a to creat a mount directory for my partiton ntfs, and it worked, but ubuntu doesnt do it in the start.

---

### Post by Intrepid Ibex on 2010-03-06
Hmm.. well did you try reinstalling dbus? ```
sudo apt-get reinstall dbus
```

---

### Post by Intrepid Ibex on 2010-03-06
Ok, so what is the message you get when doing ```
sudo ntfs-3g /dev/sdXX
``` where the first x ist the drive and the seccond one the number of the ntfs partition is located in.

---

### Post by coyotemk on 2010-03-06
when i've tried 
sudo apt-get reinstall dbus

i get a mess: 
E: Invalid operation reinstal


the mess for 
sudo ntfs-3g /dev/sda1 ntfs-3g: No mountpoint is specified.

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver


But the big probleme is that this isnt happening only with my ntfs partition, i cant mount any external file system, not even usb flash drive

---

### Post by oldfred on 2010-03-06
man mountall says it reads fstab for mounting information. You have to have a mount point and add the partition to fstab to have it mounted.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)


After you read and understand the above then you can use this easier tool to create mount & add to fstab, but you need to understand the settings it asks for:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

