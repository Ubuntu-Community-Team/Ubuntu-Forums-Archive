---
title: "Problem automatically mounting a drive at startup."
date: 2012-01-12
forum: General Help
---

### Post by Randy Schilling on 2012-01-12
My system has 2 drives, one with Ubuntu and the other XP.
This XP drive shows up as a device (285 GB Filesystem) under nautilus 
and nautilus mounts the drive when you click the device.

I would like to mount the XP drive to a different location 
from the mount point where nautilus places it.
Working from a bash shell, the command 
$sudo mount -t ntfs /dev/sdb1 /home/randy/XP
does exactly what I want;   
when you go to nautilus and click on 285 GB Filesystem 
you're taken to new mount point, /home/randy/XP.

The next step is to have this done autmatically at login.
I want to place the command
	mount -t ntfs /dev/sdb1 /home/randy/XP
in a file that is executed with root privilege with every startup.
Tried /etc/profile and /root/.profile and neither seemed to work.

What do I have to do to make this work?

Thanks and Regards - Randy

---

### Post by Double.J on 2012-01-12
Hi there, the file you want to edit is called fstab, located at /etc/fstab - you can either go there in the terminal and use an editor of your choice or navigate there in nautilus and open with gedit :)

The setting you want to put in is
> 
#Windows XP Partition
/dev/sdb1   /home/randy/XP   ntfs-3g   rw,auto,user,noexec,async   0 0


for a detailed list of the options listed above look [here]("https://help.ubuntu.com/community/Fstab"). I think I've selected the options you asked for - you may want to change noexec to exec - noexec prevents binary files being executed from the partition - with windows this is a security feature.

Hope it helps :)
Edit you'll have to restart to take effect!

---

### Post by Randy Schilling on 2012-01-12
That was easy.  Thanks

---

