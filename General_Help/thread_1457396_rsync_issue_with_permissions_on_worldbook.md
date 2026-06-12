---
title: "rsync issue with permissions on worldbook"
date: 2010-04-18
forum: General Help
---

### Post by xigen on 2010-04-18
Hi,

I am logged into the worldbook, both as a regular user: JOEJOE and as root.

I would like to use rsync to copy my music directory from my local disk to the backup server (worldbook).

local directory with music files:
/media/disk/wilson/Music/

The IP of my worldbook is:
192.168.1.67
into the directory:
/shares/internal/PUBLIC/SAMSAM

....
My attempts at using:

rsync -r /media/disk/wilson/Music/ JOEJOE@192.168.1.67:/shares/internal/PUBLIC/SAMSAM/

....

from my "wilson" login on my local system:
wilson@wilson-desktop:~$ rsync -r /media/disk/wilson/Music/ JOEJOE@192.168.1.67:/shares/internal/PUBLIC/SAMSAM/

JOEJOE@192.168.1.67's password: 
Could not chdir to home directory /home/JOEJOE: No such file or directory

..

from "myworldbook" .. when logged in as "JOEJOE"
and in the directory: /shares/internal/PUBLIC/SAMSAM/

[root@MyBookWorld SAMSAM]# rsync -r /media/disk/wilson/Music/ /shares/internal/PUBLIC/SAMSAM/
rsync: link_stat "/media/disk/wilson/Music/." failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(892) [sender=2.6.8]
..

Advice?

.......
It looks like I am in the right place in the filesystem of the worldbook device...
[root@MyBookWorld SAMSAM]# cd ..
[root@MyBookWorld PUBLIC]# pwd
/shares/internal/PUBLIC
[root@MyBookWorld PUBLIC]# ls
Backup		Documents1009  Music   Sarah&Mario (D)	TAL	pictures102008
Documents2     SAMSAM  stuff	
[root@MyBookWorld PUBLIC]#

---

