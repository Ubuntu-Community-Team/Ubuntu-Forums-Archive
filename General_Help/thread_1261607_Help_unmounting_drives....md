---
title: "Help unmounting drives..."
date: 2009-09-08
forum: General Help
---

### Post by alms66 on 2009-09-08
It used to be that only my user account could mount two internal drives.  I thought, wouldn't it be nice if that was done automatically at bootup?  So I installed the NTFS tools and set the drives to automatically mount at bootup.  Turns out, I prefer it to not be that way after all since it then mounts for all users, not just my account - and now I can't undo it.  When I try to unmount the drives and I get a message saying only root can unmount the drive.  My first thought was that if I used the NTFS tools to configure this, surely removing that would undo the setting, but no.  I did a little digging on the forums here and found fstab, but am not sure what's wrong here.  These are the two lines from fstab for the two drives I want to unmount for all users - or get back to the old behaviour:

/dev/sda6 /media/Data\040Drive ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

Actually, I suppose I don't want anyone, except myself, to be able to access the Windows drive from within Linux, however, the Data Drive should be accessible to all users as that's where everything is shared between the two OS's.

---

### Post by XCan on 2009-09-09
```
 sudo umount /dev/sda6
sudo umount /dev/sda1 
```

to unmount them. You can also comment out those two lines you found and Ubuntu shouldn't mount them on boot.

---

### Post by vanadium on 2009-09-09
You can control the permissions of ntfs partitions using additional options: the options "uid" and "gid" allow to assign a user and a group (default it is "root") and the option "umask" allows to restrict permissions (default is all permissions are open for users, groups and others).

---

### Post by Zimmer on 2009-09-09
DISK MOUNTER gnome-applet 

My favourite app that I have on the Gnome panel.... Install gnome-applets from Synaptic, then right click on your gnome panel and add it....

---

### Post by vanadium on 2009-09-11
won't automatically mount on startup, as far as I know.

---

### Post by alms66 on 2009-09-20
> **XCan said:**
> ```
 sudo umount /dev/sda6
sudo umount /dev/sda1 
```

to unmount them. You can also comment out those two lines you found and Ubuntu shouldn't mount them on boot.

A comment is just "#", correct?

---

### Post by Zimmer on 2009-09-20
yes #  at the start of the line will comment out the following statement.

---

