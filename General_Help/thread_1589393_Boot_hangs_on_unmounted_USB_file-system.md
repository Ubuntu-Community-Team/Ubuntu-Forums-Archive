---
title: "Boot hangs on unmounted USB file-system"
date: 2010-10-06
forum: General Help
---

### Post by zenon222 on 2010-10-06
This began on 10.04.  Ubuntu will not boot until it has found all file-systems listed in fstab.  I have an external USB drive I use to store files and like to have control over its mounting options an mount-point. This is why I have configured it through fstab.

I have been waiting for this to go away (ie: bugfix) but at this point it seems the developers have intended this operation.

TIA.

---

### Post by ridgeland on 2010-10-06
I hate this "feature".
It's annoying when you have fstab and UUID set up in 9.04 only to have 10.04 break it by design.  If I put my card reader or external drive in fstab then 10.04 hangs on boot waiting for the device if it's not there. "Hit S to skip this drive" to me is "hangs".
A user (me) can mount the card reader and unmount it but any files copied over cannot be edited by any other user.
In /etc/udev/rules.d I have 99-local.rules with some ideas from Arch I think.  I want to mount my card reader and copy photos from the camera card to a NFS directory.  By default other users (my wife on her PC) cannot edit those files (photos).  So my local rules gets it mounted with 777 so she can edit them.  The bad side effect I haven't solved is unmount.  Only root can unmount such USB drives!  So I made a panel launcher for sudo umount and have to enter a password to unmount the device.
I hate this regression in functionality.
I hope someone knows an easy answer.

---

### Post by zenon222 on 2010-10-06
If someone would just add the option in fstab ```
wait on boot [y/n]
```it could actually be a useful feature, being able to specify whether a file-system is "essential" for system startup.

---

### Post by QLee on 2010-10-07
> **zenon222 said:**
> If someone would just add the option in fstab ```
wait on boot [y/n]
```it could actually be a useful feature, being able to specify whether a file-system is "essential" for system startup.
I use the option "noauto" in fstab for volumes that I don't want mounted by the system at boot time. Just mount them when I want to use them.

---

### Post by dabl on 2010-10-07
For any device/partition listed in /etc/fstab, with an "auto" mount option, if the item is not present at boot time, an error will be generated and the boot process might hang.  As QLee says, change the "auto" option to "noauto" for devices that might not be connected at boot time.

---

### Post by zenon222 on 2010-10-07
The trouble with using noauto is that when I do plug-in the USB drive that I have to manually mount it.  Is there no option to mount automatically when detected, but not require the drive at boot time?

---

### Post by dabl on 2010-10-07
> **zenon222 said:**
> 

 Is there no option to mount automatically when detected, but not require the drive at boot time?

Sure -- that's the default action for a USB storage device!

---

### Post by Zimmer on 2010-10-07
FWIW 
my easy answer is not to have them in FSTAB and to use the disk mounter applet on the Gnome panel for mounting/ unmounting my removable drives and other partitions on an ad hoc basis.

---

