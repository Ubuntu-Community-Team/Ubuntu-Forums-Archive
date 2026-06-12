---
title: "Can't change mount point of second hard drive"
date: 2009-11-06
forum: General Help
---

### Post by vanepelw on 2009-11-06
I recently installed Karmic on a fresh HD.  My old Intrepid installation is on a second HD that was hooked up as a slave during the install.

The second HD shows up in Places as '115 GB Filesystem', which is fine, but mounts to /media/<UUID>.  I'd like to change the mount point for the second drive to something easier to reference, like /media/OldDrive.

However, I don't see an entry for this drive in /etc/fstab.  If I add an entry in /etc/fstab for the second drive it mounts at the correct folder, but I also get an (annoying) additional entry in the 'Places' menu (OldDrive), which gives me a 'busy mount' error when I click on it.  

How can I modify the mount location for the 2nd hard drive?  Thanks in advance!

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d1939ef4-7f8b-45dc-98f4-8aefdf1ed384 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eaa1cc17-65b0-4bc2-9a81-b3861319a12b none           swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

And the entry that I added to try to outline the mount point:

```
UUID=2cf43340-c024-4dd4-a8f2-d234ab4379bd /media/OldDrive           ext3    user,noauto              0       0 
```

---

### Post by vanepelw on 2009-11-07
Bump

---

### Post by vanepelw on 2009-11-08
This appears to be a known bug in Karmic:

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/390304](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/390304)

I changed the label of the drive and it mounted correctly.

---

