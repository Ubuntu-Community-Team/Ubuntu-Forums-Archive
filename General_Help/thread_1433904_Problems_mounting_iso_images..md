---
title: "Problems mounting iso images."
date: 2010-03-19
forum: General Help
---

### Post by kyletstrand on 2010-03-19
I'm trying trying to create/burn/mount .iso image files using the command line.  I'm able to create and burn them using the following commands:

```
[INDENT]mkisofs -f -R -r -l -J -V -o*.iso source
cdrecord -v -pad speed=1 dev=0,0,0 *.iso             [/INDENT]
```These two commands work with no problem.  But when  I try to mount an iso image, I use the following command and get this output.

```


sudo mount -t iso9660 loop0 Miles.iso /media/iso

kyle@Avant:~/Music/Miles Davis$ sudo mount -t iso9660 loop0 Miles.iso /media/iso
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
```I'm probably missing something very obvious, but I haven't been able to successfully mount the image.  I have a mount point created which is /media/iso.

If it makes any difference, I'm using Kubuntu 9.10.

Anyone have any advice as to how I can mount this without getting the help info?

Thanks!

And yes, I'm creating an iso filled with Miles Davis albums :D

---

### Post by mridkash on 2010-03-19
```

sudo mount -t iso9660 -o loop Miles.iso /media/iso

```
as found on [http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html)

---

### Post by kyletstrand on 2010-03-19
Ok, I've been doing this instead now and getting a different error:

```

sudo mount -o Miles.iso /media/iso

kyle@Avant:~/Music/Miles Davis$ sudo mount -o Miles.iso /media/iso
mount: can't find /media/iso in /etc/fstab or /etc/mtab


```

Can someone shed a little light on this part for me?

---

### Post by mridkash on 2010-03-19
you're missing **-o loop** in that command, check the command again. or simply copy paste the command  given above.

---

### Post by kyletstrand on 2010-03-20
Awesome!  Got it now.  Thanks!

---

