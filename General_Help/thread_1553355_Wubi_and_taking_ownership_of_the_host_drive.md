---
title: "Wubi and taking ownership of the host drive"
date: 2010-08-14
forum: General Help
---

### Post by codemyster on 2010-08-14
So, I used Wubi to install Lucid, and I'm not able to write to my host drive unless I'm root. 

I tried chmod'ing /host to give my user account ownership but even as root, the permission was denied. 

Note, the host drive is NOT the partition I have Windows installed on. In fact, the partition Windows is installed on, I have both read and write access to as my normal user account. I have the Ubuntu virtual hard disk on an extra partition I had. 

Here's the relevant output from mount:

> /dev/sda3 on /host type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


Does anyone know how I can fix this?

---

### Post by bodhi.zazen on 2010-08-14
> **codemyster said:**
> So, I used Wubi to install Lucid, and I'm not able to write to my host drive unless I'm root. 

I tried chmod'ing /host to give my user account ownership but even as root, the permission was denied. 

Note, the host drive is NOT the partition I have Windows installed on. In fact, the partition Windows is installed on, I have both read and write access to as my normal user account. I have the Ubuntu virtual hard disk on an extra partition I had. 

Here's the relevant output from mount:



Does anyone know how I can fix this?

You need to change the options in fstab. You can either set the uid to a user other then root or change the umask values (or both).

See :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

or man mount (look at the ntfs section).

---

### Post by codemyster on 2010-08-16
> **bodhi.zazen said:**
> You need to change the options in fstab. You can either set the uid to a user other then root or change the umask values (or both).

See :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

or man mount (look at the ntfs section).

I noticed that in my fstab, there is no entry for that drive. I assume that's because whatever way Wubi loads the filesystem, it mounts /host with special options considering the entire HD that the Ubuntu installation resides on it on that drive. 

Should I add an entry in my fstab for that drive? For some reason I don't think it'd make a difference because /host is mounted before actually booting the OS (and therefor before the other drives in the fstab are mounted). Something tells me that there's something other than fstab that needs to be edited, I just don't know what it would be. I don't know the details of how wubi works. :)

---

### Post by codemyster on 2010-08-19
Pardon my bumping, but can anyone help? So far, this is the single thing preventing my switch over.

---

### Post by bodhi.zazen on 2010-08-20
Did you add an entry in fstab ?

If you are going to switch over, you should re-install, make a partition for Ubuntu, and install grub.

IMO wubi is for testing purposes only and, again IMO, it is more hassle to maintain.

---

