---
title: "operating system not found problem"
date: 2006-03-26
forum: General Help
---

### Post by matthewinuk on 2006-03-26
I installed ubuntu on an old hp pavillion 8600, which used to have windows 98. Its not a very comp, so ubuntu doesnt run too well, so i whacked in the old recovery cd, and chose "format and recover" to reinstall windows.

Next only GRUB came up and was trying to load ubuntu. Windows 98 was not an option. Then I looked on another thread and it said to use a program to remove unwanted partition with ubuuntu on it which i did. THen i just deleted all partitions and made a new one to fill the hard drive as my new windows partition. THen rebooted and reinstalled windows wih format.
Now it only loads a black screen with "operating system not found". I think I deleted the master boot record. How do i make a new one? I dont have a recover disk, and cannot make a recvery floppy disk since my new laptop next to the computer im talking about doesnt have a floppy drive.

If anyone know of a way to  make a boot cd instead of a boot floppy then please say so. I tried going to command line using recovery cd and typed fixmbr, which didnt work. then tried fdisk /mbr and it said that there wasnt enough memory

also, command prompt seems to open d:\
it used to open c:\
when i type c:\ it comes up with c:\
dir/w/p shows my windows installation files are in c drive.

HELP! ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Sef on 2006-03-27
Since it is that old and Ubuntu don't work well on it, I would do a server install. (Type server before enter.)

Once it is done,  I would install a lightweight window manager, e.g. xubuntu, fluxbox (superlight), icewm, etc.

to install them:

sudo apt-get update

sudo apt-get install  (window manager)-desktop

---

### Post by az on 2006-03-27
From any linux cd (like the installer cd) you can wipe the mbr clean by running

dd if=/dev/zero of=/dev/hda bs=512 count=1

Boot the ubuntu installer and let it load up the extra components.  When it offers you the partitionner screen , hit CTRL-ALT-F2 and run that command.

---

