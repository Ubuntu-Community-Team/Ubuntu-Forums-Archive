---
title: "Mounting image files(iso)"
date: 2006-05-04
forum: General Help
---

### Post by Strike&gt;&gt; on 2006-05-04
Hello 
I have tried to mount an iso image but it keeps giving me these instructions everytime i run the command.

This is what it looks like:

nav@Freedom:~$ sudo modprobe loop 
nav@Freedom:~$ sudo mount /hda2/Documents and Settings/Navid/My Documents/Incomplete/My Music/My Received Files/New Folder/dapper-install-i386.iso /media/iso/ -t iso9660 -o loop
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
nav@Freedom:~$ sudo mount /hda2/Documents and Settings/Navid/My Documents/Incomplete/My Music/My Received Files/New Folder/dapper-install-i386.iso /media/iso/ -t iso9660 -o loop
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
nav@Freedom:~$

---

### Post by ZylGadis on 2006-05-04
sudo mount -t iso9660 -o loop something somewhere

the -t and -o are before the rest, which the error message you received clearly shows :) Read those, they are useful occasionally.

---

### Post by Strike&gt;&gt; on 2006-05-04
if u mean like:

sudo mount-t iso9660 -o loop /hda2/Documents and Settings/Navid/My Documents/Incomplete/My Music/My Received Files/New Folder/dapper-install-i386.iso /media/iso/

i did that but got the error again

---

### Post by Rasitiln on 2006-05-04
**sudo mount -t iso9660 -o loop** /closet/cd\ images/Windows\ XP\ Pro\ Corp/XP_PRO__CORP_EN.iso /media/cdrom/

worked for me

is the command i used your error maybe because you are not puting "\" after a space like

/mnt/cdrom\ main/ 

Hope this helps

---

### Post by ZylGadis on 2006-05-04
You need the correct syntax. It is not mount-t, it is mount -t. You also need to escape the spaces in the directory names with backslash, like this:
/My\ Documents/
And, to top it all, you really should use Ubuntu as your primary OS, if not ditch Windows completely. It's difficult at first, but soon you slap your forehead and yell "why didn't I do it sooner!" Until you do, you'll keep hitting similar weird problems related to Windows behaving stupidly and getting in the way of Ubuntu.
You'd do better to value others' time, too. Read first and and only after you can't find the answer to your question in an hour or two, come here and ask. You would be amazed at how much time you'd save yourself (and others) if you try to help yourself first (and learn plenty in the process).

---

### Post by Strike&gt;&gt; on 2006-05-04
Thank you for your help, i forgot to put the "\"s. 

And sorry if i have asked a question like this before researching for it.

---

### Post by bluenova on 2006-05-05
I do this when dealing with spaces:
sudo mount -t iso9660 -o loop "/hda2/Documents and Settings/Navid/My Documents/Incomplete/My Music/My Received Files/New Folder/dapper-install-i386.iso" /media/iso/

"" are easier IMO.

---

