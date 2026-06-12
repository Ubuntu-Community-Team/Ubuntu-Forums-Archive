---
title: "File Won't mount.."
date: 2010-06-26
forum: General Help
---

### Post by TheAnomalyCoder on 2010-06-26
Well I'm new to Ubuntu, and I'm not quite familiar with what's going on, but I found this command online, and I tried it, and here's my output..
Where exactly is this being mounted?

```

marek@marek-desktop:~$ sudo mount -o loop /home/marek/Desktop/Visual Studio 2008.iso
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
marek@marek-desktop:~$ ^C
marek@marek-desktop:~$ 


```

---

### Post by Leppie on 2010-06-26
it's not mounting anywhere as in linux spaces are parameter seperators.
you have to escape the spaces (place a \ in front of them), or double quote the complete path.
like this:
```
sudo mount -o loop /home/marek/Desktop/Visual\ Studio\ 2008.iso

```
or this:
```
sudo mount -o loop "/home/marek/Desktop/Visual Studio 2008.iso"

```

---

### Post by TheAnomalyCoder on 2010-06-26
> **Leppie said:**
> it's not mounting anywhere as in linux spaces are parameter seperators.
you have to escape the spaces (place a \ in front of them), or double quote the complete path.
like this:
```
sudo mount -o loop /home/marek/Desktop/Visual\ Studio\ 2008.iso

```or this:
```
sudo mount -o loop "/home/marek/Desktop/Visual Studio 2008.iso"

```
Oh, I didn't know that, one new thing I learned about Linux today :guitar:.
That seems to have solved one problem, but now I get this:

mount: can't find /home/marek/Desktop/Visual Studio 2008.iso in /etc/fstab or /etc/mtab

The file is sitting on my Desktop right in front of me..
Kind of odd. Any ideas what I might be doing wrong?

---

### Post by Leppie on 2010-06-26
because you haven't told your system where to mount the image.
if you want, you could create a folder Virtcd in media:
```
sudo mkdir /media/Virtcd
```like this, the image should show on the deskop when it's mounted.
then try to mount like this:
```
sudo mount -o loop "/home/marek/Desktop/Visual Studio 2008.iso" /media/Virtcd
```

as the output states, you can only mount whatever is already specified in your fstab or mtab without providing the mounting point at the command line.

---

### Post by TheAnomalyCoder on 2010-06-26
> **Leppie said:**
> because you haven't told your system where to mount the image.
if you want, you could create a folder Virtcd in media:
```
sudo mkdir /media/Virtcd
```like this, the image should show on the deskop when it's mounted.
then try to mount like this:
```
sudo mount -o loop "/home/marek/Desktop/Visual Studio 2008.iso" /media/Virtcd
```as the output states, you can only mount whatever is already specified in your fstab or mtab without providing the mounting point at the command line.
Oh, that explains it.
I ran the new code, and it worked!
Thank you so much for your help, I'm copying these commands and saving them, they will come in handy in the future. :p

---

