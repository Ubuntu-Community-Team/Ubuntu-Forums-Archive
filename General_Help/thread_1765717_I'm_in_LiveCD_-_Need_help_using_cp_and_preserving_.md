---
title: "I'm in LiveCD - Need help using cp and preserving all that is in my /home"
date: 2011-05-23
forum: General Help
---

### Post by Mark_in_Hollywood on 2011-05-23
I'm in LiveCD (Natty)

I blew up the OS. Can't get past login & password. 'Puter just hangs there. 

I'm going to do a clean install, but want to make a copy of my /home.

I tried gksudo nautilus to copy all of /home to an external hard drive (via USB). It won't copy all, saying that I lack permissions.

I've read about recursively copying, etc. and cannot make out the sequence I need. I must copy all that is in my /home and preserve all the links, dependencies, file and directory ownership permissions and also must get the command for copying them from the external hard drive if the clean install goes bad.

My idea is:

cp -ablpr /media/name-of-mounted-drive/home /media/name-of-external-hard-drive

anybody?

I have my /home on a separate partition:

[SIZE="1"]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8937    71680000    7  HPFS/NTFS
/dev/sda3   *        8938       10842    15301912+  83  Linux
/dev/sda4           10843       48641   303620437    5  Extended
/dev/sda5           10843       47583   295122051   83  Linux
/dev/sda6           47584       48641     8498353+  82  Linux swap / Solaris[/SIZE]

---

### Post by ashekarema@gmail.com on 2011-05-23
To copy a folder in the terminal you need to place a -r after cp and start with sudo for permissions.  An example would be something like this:

sudo cp -r /media/name-of-mounted-drive/home /media/name-of-external-hard-drive

--------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by Mark_in_Hollywood on 2011-05-24
I cannot figure out the correct set of command strings to 

1 - mount my /home

2 - copy /home to an external usb hard drive, preserving all the permissions, symlinks, timestamps, groups, and other specific settings or configs that are in /home.

I tried the cp -adlpr but received about 1000s of the below, before I stopped the process with ctrl-c.

cp: cannot create link `/mnt/usbex/mark/Food & Foodways/Mexico/México Desconocido Las haciendas pulqueras, ruta cultural de gran atractivo._files/redes_btn6_off.png': Invalid cross-device link

---

### Post by Mark_in_Hollywood on 2011-05-25
I have learned that only 'tar' and 'dar' can copy (or backup) files and directories and preserve the file or folder attributes and extended attributes.

---

