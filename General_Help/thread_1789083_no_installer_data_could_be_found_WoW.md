---
title: "no installer data could be found WoW"
date: 2011-06-23
forum: General Help
---

### Post by PrimeRadiant on 2011-06-23
Hi I am running a Dell inspiron 570 with the following specifications:

CPU: AMD Athlon II X2/X3/X4
Memory: 8 GB of RAM
Graphics Card: ATI Radeon HD 4200
Driver Packaging Version: 8.84.6-110324a-116088c-ATI
2D Driver Version: 8.84.60
Catalyst Control Center Version: 2.13
RandR Version: !.3

Wine 1.3+

The wine version was the most recent recommended in these forums.

Anyway I get the following message: "No installer data could be found" when I execute WOW.exe from the command line.

I read a post from another user and there may be hidden files. Then I checked the howto:" WoW with Wine" again and saw that some files may be hidden and the following would uhide them:

**Note** that on some WoW DVD's the  installer executable is hidden and you need to re-mount the disc with  the 'unhide' option. To do this type in a terminal:
  
sudo umount /dev/cdrom
sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

However when I ran the second command I got the following

william@PrimeRadiant:~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Can anyone help give me the proper command to unhide these files on WoW. And I have another question. Once I unhide the files, can I simply copy them to a directory on my computer and install WoW from there? Thanks. Any help is appreciated.

---

