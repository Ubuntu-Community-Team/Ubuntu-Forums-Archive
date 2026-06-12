---
title: "Unable to mount external hard drive"
date: 2010-05-08
forum: General Help
---

### Post by BadlyNeedHelp on 2010-05-08
Hi guys,

You was all a great help last time, Ubuntu has been running fine until I installed the upgrade today, so I am using Ubuntu 10.04 LTS.

My external hard drive was connecting fine before I installed the update, now when I try and connect my hard drive I keep getting this error.

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

I have already followed and done the steps here

[http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

But still, the problem persists.

---

### Post by bumanie on 2010-05-08
You could try ntfs-config so that the drive is recognised in /etc/fstab -  ntfs-config is meant to work fine on external drives. Failing that > sudo mount -t ntfs /dev/sdx substituting your drive designation in sdx. If you don't know the drive letter, > sudo blkid should give you the answer.

---

### Post by BadlyNeedHelp on 2010-05-08
Thank you, I did that but its really confusing...what do I do now?

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by bumanie on 2010-05-08
I am assuming it is formatted to ntfs as the first output you supplied indicated. If it is formatted to ntfs, go to  terminal and type > sudo apt-get install ntfs-config then fill out the gui window that appears under Applications --> System Tools --> ntfs-configuration tool and the drive should mount whenever it is plugged in.

---

### Post by BadlyNeedHelp on 2010-05-08
I cant find system tools?

---

