---
title: "big troubles: ubuntu doesn't mount my ntfs partition"
date: 2009-11-17
forum: General Help
---

### Post by nahuel_89p on 2009-11-17
Hi forum... I'm in big troubles, since i really need that partition, it has all my mp3, photos, movies, etc...

Usually, that partition mounts automatically, and it always worked fine, but today, suddenly, without any reason i can tell, it just doesn't mount not even manually from nautilus.
When i try to do so, i get a "Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/disk"

If i run nautilus in sudo mode, partitions are not even visible...

this is the partitions structure (i have only one hard disk, plus an usb hard disk):

**/dev/sda1/** (my ntfs partition)
**/dev/sda2/** (inside this partition, i have several others: )
**--/dev/sda8/** (my root folder/... 15 gb, Ext3)
**--/dev/sda9/** (swap)
**--/dev/sda5/** (another swap)
**--/dev/sda6/** (a 300mb ext3 partitions, it mounts fine)
**--free space** 15GB free
**--/dev/sda7/** (another swap)

I really can't tell what happened. It just happened without any reason at all. But i really need your help, i've my most important stuff in that partition.
Thanks.

---

### Post by nahuel_89p on 2009-11-17
update: 

if i run:

> nahuel@nahuel-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk/
[sudo] password for nahuel:
fuse: failed to access mountpoint /media/disk/: No existe el fichero ó directorio
nahuel@nahuel-desktop:~$

---

### Post by garvinrick4 on 2009-11-17
What does it look like in a GUI program such as Palimpsest Disk Utility. And will it
mount from there? It is in Administration. Just wondering if it will work in a case like this.

---

### Post by nahuel_89p on 2009-11-17
problem solved!
if any of you have some problem like this, just run:

> cd /media

sudo mkdir disk

sudo mount -t ntfs-3g /dev/sda1 /media/disk/

---

### Post by oldfred on 2009-11-18
If you want it to mount on startup you can edit fstab with an entry like your manual entry. 
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

### Post by VanillaMozilla on 2009-11-18
As far as I know, that solution works only for a privileged user.  There seems to be a problem with mount, ntfs-3g, or fstab after the update.

There seem to be quite a few threads about this without a lot of progress, so I started yet another one ;) here:
[http://ubuntuforums.org/showthread.php?p=8341959#post8341959](http://ubuntuforums.org/showthread.php?p=8341959#post8341959)

---

