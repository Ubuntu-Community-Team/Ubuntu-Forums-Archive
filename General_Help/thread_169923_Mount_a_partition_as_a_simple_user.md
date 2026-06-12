---
title: "Mount a partition as a simple user"
date: 2006-05-03
forum: General Help
---

### Post by albox on 2006-05-03
Hi,
I have some problems to mount a partition as a simple user (I don't want to be root to 

do that).

Here is my fstab :
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /home/al/aldisk     ntfs    rw,defaults,noauto,user        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hdc3       /media/hdc3     ntfs    defaults        0       0
/dev/hdc4       /media/hdc4     ntfs    defaults        0       0
/dev/hdc2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

$ mount /dev/hda5
$ ls /home/al/aldisk
ls: /home/al/aldisk: Permission denied
$ sudo chmod 777 /home/al/aldisk/
chmod: changing permissions of `/home/al/aldisk/': Read-only file system

I tried a lot of things that I saw on this forum but nothing worked ](*,)  . Can you help me ?
Thank you :mrgreen:

---

### Post by neouser99 on 2006-05-03
you probably want the set the
```
uid=<user>
```
flag, as it is NTFS specific.

-neo

---

### Post by albox on 2006-05-03
It works ! I should have paid more attention to the documentation.
Thank you very much !!!

---

### Post by aysiu on 2006-05-03
You can't *chmod* NTFS.

Change these lines: ```
/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda5 /home/al/aldisk ntfs rw,defaults,noauto,user 0 0
/dev/hda6 /media/hda6 ntfs defaults 0 0
/dev/hdc3 /media/hdc3 ntfs defaults 0 0
/dev/hdc4 /media/hdc4 ntfs defaults 0 0
``` to these lines ```
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /home/al/aldisk ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /media/hda6 ntfs nls=utf8,umask=0222 0 0
/dev/hdc3 /media/hdc3 ntfs nls=utf8,umask=0222 0 0
/dev/hdc4 /media/hdc4 ntfs nls=utf8,umask=0222 0 0
``` Then reboot.

For full instructions: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

