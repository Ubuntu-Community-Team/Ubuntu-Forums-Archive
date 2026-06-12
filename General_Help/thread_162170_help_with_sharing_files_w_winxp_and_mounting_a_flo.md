---
title: "help with sharing files w winxp and mounting a floppy drive"
date: 2006-04-18
forum: General Help
---

### Post by sjoseph on 2006-04-18
hello,

1. i would like to be able to access my linux docs with win xp, i've created shared folder under SMB but don't know how to access this from xp.

2. i would like to be able to access my floppy from ubuntu, but don't know how. is this an easy task. 

steve

---

### Post by sYs^ on 2006-04-18
1. Start -> Run -> \\your_ubuntu's_hostname
But before that create a samba user with this command:sudo smbpasswd -a USERNAME
2. mount -t fat32 /media/floppy

---

### Post by sjoseph on 2006-04-18
thanks, i try to mount the floppy but it won't do it. this is what i get:

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
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by sjoseph on 2006-04-19
i also tried the start-run-\\myusername and xp came back with it couldn't find the network path.

---

### Post by eentonig on 2006-04-19
Do you have connectivity between the two machines? Can they ping eachother?

Oops, It's shouldn't be "\\myusername", but "\\Ubuntu_ip_address" or "\\Ubuntu_ip_address\sharename"

---

