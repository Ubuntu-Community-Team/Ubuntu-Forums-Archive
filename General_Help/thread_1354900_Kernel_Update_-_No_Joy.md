---
title: "Kernel Update - No Joy"
date: 2009-12-14
forum: General Help
---

### Post by ACMarina on 2009-12-14
I'd been gone for about two weeks and found a slew of updates waiting for me when I got home.  Let the update manager do its thing, and on reboot I got this error..

"One or more of the mounts listed in /etc/fstab cannot yet be mounted:

I went back and forth, trying to comment out lines of my fstab, and I'm just now getting back up and running.  To get going again I have to issue

sudo mount -n -o remount,rw / 

And then start xfce running.

This is my current fstab..

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1
UUID=0aab3d8a-6387-4047-94bb-bac86e27a6f4 /               ext3    relatime,errors=remount-ro 0       1
#/dev/sda5
#UUID=f926e172-60d0-4d0d-a4ac-197ba27b2b04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

none /proc/bus/usb usbfs devgid=122,devmode=664 0 0 
#devpts /dev/pts devpts (rw,noexec,nosuid,gid=5,mode=620)

```

Any ideas or thoughts?

---

### Post by jmmL on 2009-12-14
Sorry can't offer any help as of yet. I am also affected by this, although I use plain ubuntu.

I'm pretty sure this happened on the first reboot after the latest kernel update to -17.

Edit:
Hmm. It's now working for me. I booted off a LiveCD, checked for errors through gparted (which calls e2fsck) - nothing reported. Mounted both my root and home (they're on separate partitions, home had the problem). Didn't really do anything else except change some permissions in home which looked odd, but that shouldn't effect this. Also I noted that before mounting my /home, it had no UUID information listed in gparted, after mounting from the LiveCD, it did. Mounting seemed to solve the problem.

---

### Post by efflandt on 2009-12-14
Where did that exteranious /dev/sda1 come from with nothing after it (no mount point, etc.)?  If that is the same as the UUID on the line after it, perhaps it should be commented out (leading #):

#/dev/sda1

That probably originally said:

# / was on /dev/sda1 during installation

---

