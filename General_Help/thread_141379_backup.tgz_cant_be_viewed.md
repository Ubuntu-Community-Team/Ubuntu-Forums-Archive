---
title: "backup.tgz cant be viewed ??"
date: 2006-03-08
forum: General Help
---

### Post by muzaki on 2006-03-08
hy guys, i need some help here....
I just tried this...
> #!/bin/bash
#script to backup all files on your system even configuration files that can then at a later date be restored by "untaring" the backup file. Based on the threads in the Ubuntu forums by Heliode and A-star.

sudo cd /

sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/backup.tgz --exclude=/mnt --exclude=/sys / 

#Ubuntulifestyle


I successfully got an output backup.tgz 4 GB file.no errorr output.
then i check ,whats inside backup.tgz with archieve manager just for curiousity...
wait for awhile,then i cant see whats inside with message that error-has-happened  dialog box.

then i check to / 
then select all file that i should have backup,try to see the cumulative amount .....
it says 3.1 GB with some files unreadable....
so  what does i t mean? have i successfullly back up my system or not ?
any response will be nice
thanks in advance

---

### Post by justleen on 2006-03-08
you can check the contents/file with tar -tvzf backup.tgz  | more

---

### Post by engla on 2006-03-08
Try the tar xfvz command given above

Since archive manager always tries to unpack the whole archive before showing it, I can imagine it gets some trouble when you throw >3GB at it (unless you have lots of ram or swap space)

---

### Post by muzaki on 2006-03-09
thanks solved

---

### Post by muzaki on 2006-03-09
[QUOTE=justleen]you can check the contents/file with tar -tvzf backup.tgz  | more[/QUOTE]
EDIT : i did that , thought work fine ....BUT

in the end i got this...
 
> 
-rw-r--r-- demorg/demorg         189 2006-03-08 05:32:04 root/.Trash/slackware-10.2-iso/slackware-10.2-source-d3.iso.asc
-rw-r--r-- demorg/demorg          63 2006-03-08 05:32:05 root/.Trash/slackware-10.2-iso/slackware-10.2-source-d3.iso.md5
-rw-r--r-- demorg/demorg  697643008 2006-03-08 05:53:11 root/.Trash/slackware-10.2-iso/slackware-10.2-source-d4.iso

[B]gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now[/B]:confused: 
kool@kdouy69:/media/HD-HU2/fromlin/firefoxed/backupproject#

oopps my fault, its OK now

---

