---
title: "Problem With chmod ing files in different drives"
date: 2011-07-15
forum: General Help
---

### Post by hacker_at_linux on 2011-07-15
I am trying to install VMware to my new ubuntu system. It is a bundle file. I have installed this particular file on previous versions of Ubuntu by chmoding(755) it. but the new ubuntu is not chmoding any of the executable files that are placed in some other drives other than the / . I have also tried the graphical way of doing it from the properties but that does not work as well . It just unchecks the bos as soon as I check it. Is there a problem with mounting the drives ? or something like that 
Please help there are a lot  of applications I need to install and I cannot copy all of my programs to the / drive

---

### Post by briealeida on 2011-07-15
Do you have the rights necessary to chmod that file?

Please try sending us the output of:

ls -ahl /path/to/file


and:
id USERNAME

Replace 'USERNAME' with your username. If you don't know what it is, just run:

whoami

---

### Post by hacker_at_linux on 2011-07-17
@briealeida 
this is for ls -ahl /path/to/file
total 383M
drwx------ 1 ashmeet ashmeet 4.0K 2011-03-24 11:51 .
drwx------ 1 ashmeet ashmeet 8.0K 2011-05-22 08:54 ..
-rw------- 1 ashmeet ashmeet   96 2011-03-24 11:51 Desktop.ini
-rw------- 1 ashmeet ashmeet  22K 2008-09-24 11:36 embrace.nfo
-rw------- 1 ashmeet ashmeet 445K 2008-09-23 23:51 keygen
-rw------- 2 ashmeet ashmeet 382M 2008-09-23 23:46 VMware-Workstation-6.5.0-118166.i386.bundle

and for id USERNAME
uid=1000(ashmeet) gid=1000(ashmeet) groups=1000(ashmeet),4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare)

---

### Post by mcduck on 2011-07-17
That sounds like you are trying to change permissions of files that are located on a non-linux file system, like FAT or NTFS. Those filesystems were made for Windows, and they lack support for file and directory ownerships as they are used on Unix and Linux systems. So you can't change permissions on files located on FAT or NTFS partitions, the file system's simply have no way of handling such thing.

Instead permissions for FAT and NTFS are set whole the whole filesystem at the time it's mounted, if you use fstab to mount your partitions then you can define the default permissions for each partition there. I suppose it should also be possible to change the default permissions for automatically mounted drives, but I've never seen any reason to do that so I can't help you there.

The easiest solution, though, is to simply move the files to any drive that's formated with a Linux file system.

---

