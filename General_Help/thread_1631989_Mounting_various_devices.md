---
title: "Mounting various devices"
date: 2010-11-27
forum: General Help
---

### Post by fubeca6 on 2010-11-27
I'm having trouble mounting my Vista partition through the terminal. I'm typing ```
sudo mount -t ntfs dev/sda3 /media
``` but that's where I'm getting tripped up, because I'm fairly confident that my mount-point is "40 GB Filesystem" and I'm unable to change the name. So I guess the real question is how to open files/directories that have spaces in them in the terminal.

I've read the man page, and also docs on help.ubuntu.com, but haven't been able to figure out a solution. I'm sure it's an easy fix. Oh, also I can't figure out how to mount a DVD drive or USB from the terminal. Please help!

---

### Post by Miyavix3 on 2010-11-27
I'm not sure you can directly mount storage devices directly on /media.
Make a folder inside /media

Then mount at /media/folder:
```
sudo mount -t ntfs dev/sda3 /media/folder
```

If you have any concern as to which partition is which:

```
sudo fdisk -l
```

---

### Post by fubeca6 on 2010-11-28
I ended up figuring it out. it was ```
 sudo mount -t /dev/sda3 /media/sda3 
``` Bleh, knew it was just something simple. thank you for the help tho!

---

### Post by fubeca6 on 2010-12-01
If anyone is still paying attention to this thread...

I can't mount using ```
sudo mount -t /dev/sda3 /media/sda3
```

anymore. I get the following message: 

****@****:~$ sudo mount -t /dev/sda3 /media/sda3
[sudo] password for ****: 
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

Any and all help is appreciated!

---

