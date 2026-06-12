---
title: "reading mac formatted externial harddrive"
date: 2009-12-01
forum: General Help
---

### Post by Baconfatty on 2009-12-01
Hey,

One of my harddrives is formatted for use with mac, I'm not 100% sure what that formate is, but nether my ubuntu or windows machine can read it only os x.  Is there something I can do to get the ubuntu machine to be able to get the data off it?

-Zee

---

### Post by StuartN on 2009-12-01
> **Baconfatty said:**
> Is there something I can do to get the ubuntu machine to be able to get the data off it?

I think you only need to install hfsplus using Synaptic Package Manager.

---

### Post by Baconfatty on 2009-12-01
I've installed hfsplus and hfsutils and restarted, its still not seeing it.

edit-
It sees it in "Disk Utility" just wont open it. Only options are to "Detach" or "Erase" is, "Mount" is greyed out.

Know how to un-grey that option?

---

### Post by Baconfatty on 2009-12-01
Attempted mount in term this is the result


```

zeewes@ZeeWes:~$ sudo mount -t htsplus /dev/sdb
[sudo] password for zeewes: 
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
zeewes@ZeeWes:~$ mount -t hfs /dev/sdb
mount: only root can do that
zeewes@ZeeWes:~$ sudo mount -t hfs /dev/sdb
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
zeewes@ZeeWes:~$ 


```

Does anyone know what this means or how I can fix it?

---

### Post by Dysport on 2009-12-01
> The command is `mount [-t fstype] something somewhere'.

You should read the output more carefully ;) you always need to specify WHERE to mount the drive.
Try this:
```

sudo mkdir /media/hfsdrive
sudo mount -t hfsplus /dev/sdb1 /media/hfsdrive 

```

---

### Post by Baconfatty on 2009-12-01
> **Dysport said:**
> You should read the output more carefully ;) you always need to specify WHERE to mount the drive.
Try this:
```

sudo mkdir /media/hfsdrive
sudo mount -t hfsplus /dev/sdb1 /media/hfsdrive 

```

You sir are my hero, Thank you.

---

### Post by cholericfun on 2009-12-01
i recently tried something similar (able to read files) but had a permission problem that i could'nt solve, after some searching i decided it wasnt my stupidity but something with mac-format that wouldnt allow me to copy **to** that partition. Any ideas?

---

### Post by Dysport on 2009-12-01
You should check your /etc/fstab whether the partition is mounted as readonly:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Also you might want to check the permissions whether the folder where you mount the drive is writeable by the user you are logged on.
```
ls -l /media 
```

---

### Post by 3rdalbum on 2009-12-01
> **Baconfatty said:**
> You sir are my hero, Thank you.

Don't forget you'll need to create the /media/hfsdrive directory, and make sure it's readable by "all" users. (or at least by your user).

The 'hfsutils' and 'hfsplus' packages contain command-line programs that allow you to "sort of" mount those drives and get at their contents. See "man hfsutils" and "man hfsplus" for more details.

---

### Post by 3rdalbum on 2009-12-01
> **cholericfun said:**
> i recently tried something similar (able to read files) but had a permission problem that i could'nt solve, after some searching i decided it wasnt my stupidity but something with mac-format that wouldnt allow me to copy **to** that partition. Any ideas?

Linux can't write to HFS+ filesystems that have Journalling enabled. You should first disable journalling in the Apple Disk Utility, then you'll be able to write to it in Linux.

---

