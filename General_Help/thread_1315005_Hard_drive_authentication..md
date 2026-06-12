---
title: "Hard drive authentication."
date: 2009-11-04
forum: General Help
---

### Post by StoneCrow on 2009-11-04
Every time I open one of my hard drives in karmic it asks me for authentication. I understand that it is a security measure but I find it to be more annoying than helpful.

Is there a way to have it automatically authenticate or failing that turn it off?

---

### Post by soapBAR2 on 2009-11-04
If I understand what's happening correctly, your hard drives are not mounted and it's asking for permission to mount them. So, make an /etc/fstab entry. What you do is this: 

1) Mount the hard drive
2) GNOME (Ubuntu):
```
gedit /etc/mtab
```
KDE (Kubuntu):
```
kate /etc/mtab
```
3) Copy the last line to clipboard
4) Close gedit (don't save)
5) GNOME (Ubuntu):
```
gksudo gedit /etc/fstab
```
KDE (Kubuntu):
```
kdesudo kate /etc/fstab
```
6) Paste the line at the end
7) Save and close

That should be it. **_Be very careful in /etc/fstab (steps 5-7)_**.

---

### Post by StoneCrow on 2009-11-04
Thank you very much.

---

### Post by StoneCrow on 2009-11-05
A slight problem.

The drives still do not mount automatically, and now when I try and access them manually it says that only root can mount them...

I can undo the previous changes but then I am back to square 1.

Ideas?

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>       <type>      <options>           <dump>      <pass>
proc            /proc               proc        defaults            0           0
#
# / was on /dev/sdb2 during installation
#(file system)                           (mountpoint)    (type)    (options)               (dump)(pass)
UUID=e1a953d7-ca20-466e-823f-8c9d311aa7e1 /               ext4    relatime,errors=remount-ro 0       1
#
# swap was on /dev/sdb3 during installation
#
#(fs)                                    (mountpoint)    (type)    (opt)        (dump)    (pass)
UUID=729a1beb-cba6-4a15-a724-520911ae7505 none            swap       sw             0       0
#
#<file system> <mount point>           <type>      <options>                 <dump>      <pass>
/dev/scd0       /media/cdrom1           udf,iso9660 user,noauto,exec,utf8      0           0
/dev/fd0        /media/floppy0          auto        rw,user,noauto,exec,utf8   0           0
/dev/sdb1       /media/Cobalt           fuseblk     rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdc1       /media/9418AEF118AED192 fuseblk     rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda1       /media/Antimony         fuseblk     rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
```Here is my fstab.
The bottom 3 entries are my own.

---

### Post by StoneCrow on 2009-11-05
From background reading I have found out that my problem probably lies in the string of options for the device.

Does anyone know of an option that allows me to mount the device without being root?

---

