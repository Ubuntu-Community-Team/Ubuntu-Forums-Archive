---
title: "Create direct links to windows"
date: 2010-11-27
forum: General Help
---

### Post by estebanLInux on 2010-11-27
Hi I'm new in Ubuntu and in Linux.

I've created a direct link to my music folder in the partition that has window and I put the direct link in my Ubuntu Desktop. It works fine, but when I restart the system the direct link stop working.

Can anyone help me ?

I wanted to the link to be always available.

Thanks.

---

### Post by Elfy on 2010-11-27
You need to have windows mount on boot so it is always available.

An easy way to do that is with pysdm - [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by estebanLInux on 2011-03-19
Hi, I know it's been a while since a started this thread but I'll try to continue it.
Forestpiskie the program that you recommended me doesn't show me the partition in which I've got installed windows 7. Actually, it just show me one of type EXT4.
Are there another ways of mounting my NTFS drive on boot ?

---

### Post by Matt__ on 2011-03-19
```
sudo apt-get install ntfs-config
```
launch via menu (system tools if i recall correctly) or via terminal
and enable write support when prompted

---

### Post by estebanLInux on 2011-03-19
I did as you said Matt. But what was supposed to happen? 
I tried open pysdm after I did what you said. But it won't show the NTFS partition.
Any suggestion?

---

### Post by Matt__ on 2011-03-19
your ntfs partition will auto mount on boot from now on.

---

### Post by gandaran on 2011-03-19
> **estebanLInux said:**
> I did as you said Matt. But what was supposed to happen? 
I tried open pysdm after I did what you said. But it won't show the NTFS partition.
Any suggestion?
look you don't have to install anything to mount the windows partition permanently, all you have to do is add the windows drive/partition to /etc/fstab, its easy, but you have to know what to write in fstab.
you add a line like this one
```
UUID=1ABC9F967605D379 /windows        ntfs    defaults,umask=007,gid=46 0       0
```
you have to change the UUID for your drive, to find out your drive UUID type in terminal
```
sudo blkid
```
then change the UUID in this code line and add it to /etc/fstab.
your windows will be mounted every time in the file system as /windows (or choose you own personal label) now when booting the computer.

---

### Post by estebanLInux on 2011-03-19
Well, actually Matt was right I reboot the computer and my windows drive was mounted. Thanks Matt and Gandarean.
I hope one day I can modify the fstab file and understand what I'm doing jaja. I'm new on Linux. :)

---

