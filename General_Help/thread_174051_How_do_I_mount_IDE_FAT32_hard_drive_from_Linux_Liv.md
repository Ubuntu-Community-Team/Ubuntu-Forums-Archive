---
title: "How do I mount IDE FAT32 hard drive from Linux Live environment?"
date: 2006-05-11
forum: General Help
---

### Post by otakuj462 on 2006-05-11
Hi, could anyone tell me how to mount my IDE FAT32 hard drives from within the  Ubuntu Live CD environment? Thanks.

-Jake

---

### Post by Irony on 2006-05-11
Boot up the live CD then right click on your desktop and create a folder.

Then mount the drive to that folder via terminal;

[PHP]sudo mount /dev/hda1 /home/username/Desktop/folder/ -t vfat -o iocharset=utf8,umask=000[/PHP]

where hda1 is whatever the fat partition is and username is your username and folder is the name of the folder.

[PHP]mount[/PHP]

will confirm whether the instruction has worked.

See;

[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

