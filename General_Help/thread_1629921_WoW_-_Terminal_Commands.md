---
title: "WoW - Terminal Commands"
date: 2010-11-24
forum: General Help
---

### Post by pockets08 on 2010-11-24
Alright, everyone and their mother seems to be having this issue.

Installing WoW by disc - the computer hides all the files BUT Installer.exe. 

So to unhide them, CTRL +H. Not work.

To unhide them, going into desktop/gnome/file_view - and so on to permenantly change the unhide settings. Does not work.

Going into the Terminal and typing 
```
 sudo umount dev/cdrom 
``` - 
Will properly unmount the disc - however, when remounting i come across an issue.

```
 sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/  
```That obviously doesnt work. because cdrom0 isnt the name at the  end...I THOUGHT I place the name of the disc, which woudl be  wow3.2.0...that is false also. Now - if i remove the cdrom, and just  make it mount to /media/ - the disk drives start up and goes, but i get  an error saying false string or bad something. so - what goes into  cdrom0? - because that doesnt exist on my computer - and idk how to find  the name of what its looking for - when nothing is there.

---

### Post by WorMzy on 2010-11-24
When manually mounting, you need to specify an existing directory (preferably empty) to mount the filesystem onto. Whereas when the system automatically detects the CD, it creates the cdrom0 folder and mounts the filesystem for you. I'd recommend mounting the CD to /mnt for the time being.

```
sudo mount -t iso9660 -o ro,unhide /dev/cdrom /mnt
```

Note that the unhide mount option is depreciated and is treated as a synonym for the showassoc option.

I'm not sure whether manually mounting the filesystem will have any effect.

---

### Post by pockets08 on 2010-11-24
```
ryan@ryan-VGN-AR190G:~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

Okay....this happened the firs ttime. whats up?

---

### Post by WorMzy on 2010-11-24
Apparently the CD isn't iso9660 compliant. Is it a DVD? If so, try mounting it as udf instead. The nohide option is apparently *not* depreciated for this filesystem type, so it should work as expected (or not, as the case may be).

---

### Post by pockets08 on 2010-11-24
> **WorMzy said:**
> Apparently the CD isn't iso9660 compliant. Is it a DVD? If so, try mounting it as udf instead. The nohide option is apparently *not* depreciated for this filesystem type, so it should work as expected (or not, as the case may be).

```
ryan@ryan-VGN-AR190G:~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /udf
[sudo] password for ryan: 
mount: mount point /udf does not exist

```Maybe i wrote that wrong? haha idk.

Its the game Disc - which is DVD.

Scratch that - i see what I did wrong. replace the iso - with udf, my bad. lol 

ANyways, it worked - but the disc isnt appearing. I dont see it anywhere. and cant pull it up.

---

### Post by WorMzy on 2010-11-24
It'll be mounted in /mnt, assuming the command executed correctly. You can browse to that directory normally, or just write
```
nautilus /mnt
``` in a terminal.

---

