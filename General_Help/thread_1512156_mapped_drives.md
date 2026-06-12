---
title: "mapped drives"
date: 2010-06-17
forum: General Help
---

### Post by chrismitt2002 on 2010-06-17
well were do i start i decided to reboot my pc (as ktorrent was being weird and copying something no clue what but i rebooted i had all my drives mapped from my server pc D E F G H and heres the part that i dont get they mapped PERFECT before the reboot but after the reboot i get here is the command 

notmyrealusername@intel-quad:~$ sudo smbmount //192.168.1.3/F-1.5tb#1 /media/F -o username=notmyrealusername ,password=notmyrealpassword,uid-1000,mask00
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
owner@intel-quad:~$ but yet when i enter another password i get 

retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
owner@intel-quad:~$ 

so wtf am i doing wrong any help would be great as i said b4 before i rebooted everything mapped perfectly

---

### Post by bodhi.zazen on 2010-06-17
Try cifs ...

```
sudo mount -t cifs //192.168.1.3/F-1.5tb#1 /media/F -o username=notmyrealusername  ,password=notmyrealpassword
```

I think the options for cifs are a bit different ...

---

### Post by chrismitt2002 on 2010-06-17
notmyrealusername@intel-quad:~$ sudo mount -t cifs //192.168.1.3/F-1.5tb#1 /media/F -o username=notmyrealusername  ,password=notmyrealpassword Usage: mount -V                 : print version
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
notmyrealusername@intel-quad:~$ 
thats all i got when i did what u said

---

### Post by bodhi.zazen on 2010-06-17
That output is usually from a typo somewhere in your mount command. Perhaps it does not like the # sign in your share name, I am not sure about that.

In looking at your output, you have a space between "username=notmyrealusername" and  ",password=notmyrealpassword"

That extra space is more likely the problem.

---

### Post by chrismitt2002 on 2010-06-17
corrected it and still no go

---

### Post by chrismitt2002 on 2010-06-17
for some reason it was asking for both my passwords no idea why but when i entered both it mounted fine

---

### Post by bodhi.zazen on 2010-06-18
> **chrismitt2002 said:**
> for some reason it was asking for both my passwords no idea why but when i entered both it mounted fine

I would guess the first is for sudo, and the second is for the actual mount.

You could possibly add an entry to fstab to simplify that if you wish.

---

### Post by chrismitt2002 on 2010-06-18
not under standing what your saying

---

### Post by bodhi.zazen on 2010-06-18
> **chrismitt2002 said:**
> not under standing what your saying

When you run a command with sudo, you are asked for a password

```
sudo ls
```

After entering your password you have a 15 minute grace period when you can use sudo and not enter a pasword.

so I assume the first password you enter is for sudo ...

When you mount a samba share, you often need to enter your user password, thus I assume the second password is your samba share password.

---

