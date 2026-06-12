---
title: "dapper drake"
date: 2006-05-26
forum: General Help
---

### Post by bobanshirl on 2006-05-26
Bearing in mind that after much soul searching I have Ubuntu installed alongside my Windows even though I cant go on line and my floppy drive wont mount,when this Dapper Drake comes out will I be able to install it over the top of Ubuntu or will I have to uninstall Ubuntu and then install DD and if at the end of the day will my modem be seen and will my floppy mount.I know I have said this before on a previous thread but why does it have to be mounted,why cant I just put a formatted disc in and copy or read it.Oh well heres hoping

---

### Post by bruce89 on 2006-05-26
[QUOTE=bobanshirl]Bearing in mind that after much soul searching I have Ubuntu installed alongside my Windows even though I cant go on line and my floppy drive wont mount,when this Dapper Drake comes out will I be able to install it over the top of Ubuntu or will I have to uninstall Ubuntu and then install DD and if at the end of the day will my modem be seen and will my floppy mount.I know I have said this before on a previous thread but why does it have to be mounted,why cant I just put a formatted disc in and copy or read it.Oh well heres hoping[/QUOTE]
The computer needs to know it's there, there is no way of telling whether a floppy is in the drive or not.  Dapper Drake can be installed on top of an existing installation.  By any chance is this a Speedtouch modem?

---

### Post by Sef on 2006-05-26
> when this Dapper Drake comes out will I be able to install it over the top of Ubuntu or will I have to uninstall Ubuntu and then install DD

You will be able to click on a button once Dapper is stable to upgrade to it.

---

### Post by Ramses de Norre on 2006-05-26
He'll need to be able to connect to the internet for a dist-upgrade..

---

### Post by chris_andrew on 2006-05-26
For your floppy problem, have you tried:

*mount /dev/fd0*

If so, what happened?

Hope this helps.

Cheers,

Chris.

---

### Post by 3rdalbum on 2006-05-26
Just thought I'd clear up a technical term for the original poster.

"Mounting" is the process whereby the OS is told that a particular disk/drive is available. "Unmounting" is the opposite - where the OS is told that the disk/drive is no longer available.

On Windows and Mac, mounting is done automatically. On Ubuntu, mounting should happen automatically, but should it not there is a manual route. Obviously, since floppy disks are seriously old technology (like dialup modems), there's not much work being put into improving their support in Linux.

---

### Post by bobanshirl on 2006-05-26
tried that got cant find dev/fd0 in /etc/fstab or /etc/mtab seeing as how you are in Wiltshire and I am in Dorset can we email Q&As to each other

---

