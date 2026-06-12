---
title: "Unable to start process error!"
date: 2010-09-04
forum: General Help
---

### Post by LaMbChOpS on 2010-09-04
Hi all, 

First post so be kind!! :p

I am using Ubuntu Lucid 10.04 and wanted to try out the KDE desktop as I was becoming bored with GNOME. 

Trouble is I keep getting the following error message whenever I try and open any form of file manager (Dolphin, Konqueror etc) or use any application that has to access the file system. 

**Error Message:**
Unable to start process. Unable to create io-slave. klauncher said: Error loading 'kio_file'

I am currently using KDE Version 4.5.1.

I have googled for a solution but have not found anything that has helped!! 

I found one post regarding an error in fstab but mine looks fine, copy is below just in case you can see something wrong.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc   /proc   proc   nodev,noexec,nosuid   0   0
#Entry for /dev/sdb5 :
UUID=b1b09572-dce6-4fb7-b57c-89ad2d615974   /   ext4   errors=remount-ro   0   1
##Entry for /dev/sdb1 :
UUID=D8C2C1DFC2C1C1CC   /media/The_Big_Bloke   ntfs-3g   defaults,locale=en_AU.utf8   0   0
#Entry for /dev/sdb6 :
UUID=dd2a7af7-8c57-413f-8542-eca99775e741   none   swap   sw   0   0

```

Anybody able to point me in the right direction as I would really love to be able to use KDE.

Thanks for the help.

---

