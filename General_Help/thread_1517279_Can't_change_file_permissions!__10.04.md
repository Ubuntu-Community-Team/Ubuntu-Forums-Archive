---
title: "Can't change file permissions!  10.04"
date: 2010-06-24
forum: General Help
---

### Post by j_oly1999 on 2010-06-24
Ok, this is really frustrating.  Here's the breakdown of what i'm doing.  Fresh install of 10.04, updates, dell poweredge server that i'm using to host FTP and misc. file xfer and backups of all my engineering/cad/cnc files.  I have proftpd setup, and xfering to it no prob.  BUT i needed more capacity.  I installed 2 120G HDD (IDE , old tower) and they are mounted as SDB1 and SDC1, i mkdir'd new folders at first in /media and fstab'd the config to auto mount, but no matter what, it gives ownership to root.  I've tried every combination of chown, chmod and some other #^&$% i could think of and it wasn't working.  SO, i then went into my /home folder and just right-clicked and added a directory, checked the permissions, and it was mine, but as soon as i edited the fstab to mount the HD's to those folders, it changed them to root ownership again?  WTF???  so, at this time, i have mkdir'd a total 10, count 'em 10! directories in various places on my #^%$& comp. that i cannot for the life of me figure out how to assume ownership of and delete, or mount the HDD's to them?  Hmm, as i type, i wonder if formatting them to FAT32 would have caused this?  but if so, i added umask=000 to the options infstab?  i really need help, i'm (twitching violently) starting (rage building!) to wonder if i should have left windows alone (#^%$^&#^&) cause it was working, AAAAAHHHHHH.  



Here's my /etc/fstab


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=0d9c4638-0e49-4a4a-9ecb-bdc3cca1f86b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=85f3e0e0-1b36-404a-bfac-f7d4523d84d2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1    /home/xxxxx/JMCFTP    auto    rw,user,auto,exec,utf8,umask=000    0    0
/dev/sdb1    /home/xxxxx/FTPXFER    auto    rw,user,auto,exec,utf8,umask=000    0    0

and here is my ls -l on the folders

xxxxx@xxxxx:~/FTPXFER$ cd /home/xxxxx
xxxxx@xxxxxr:~$ ls -l
total 100
drwxr-xr-x 2 xxxxx  xxxxx  4096 2010-06-24 20:17 Desktop
drwxr-xr-x 2  xxxxx xxxxx 4096 2010-06-24 16:33 Documents
drwxr-xr-x 2 xxxxx xxxxx 4096 2010-06-24 16:33 Downloads
-rw-r--r-- 1   xxxxx xxxxx 167 2010-06-24 16:26 examples.desktop
drwxr-xr-x 2 root     root     16384 1969-12-31 19:00 ftpdrv         [COLOR=Red] (THIS IS ONE I MKDIR'D[/COLOR])
drwxr-xr-x 2 root     root     16384 1969-12-31 19:00 FTPXFER  [COLOR=Red] (THIS ONE TOO)[/COLOR]
drwxr-xr-x 2 root     root     16384 1969-12-31 19:00 JMCFTP    [COLOR=Red] (AND AGAIN)[/COLOR]
drwxr-xr-x 2 root     root     16384 1969-12-31 19:00 jwmftp         [COLOR=Red](ONE MORE FOR FUN)[/COLOR]
drwxr-xr-x 2 xxxxx xxxxx  4096 2010-06-24 16:33 Music
drwxr-xr-x 2   xxxxx xxxxx 4096 2010-06-24 16:33 Pictures
drwxr-xr-x 2  xxxxx xxxxx 4096 2010-06-24 16:33 Public
drwxr-xr-x 2  xxxxx xxxxx 4096 2010-06-24 16:33 Templates
drwxr-xr-x 2   xxxxx xxxxx 4096 2010-06-24 16:33 Videos

Please, please, what am i doing wrong?

Update, thought this might help maybe?

xxxxx@xxxxx:~$ sudo chown -R xxxxx /home/xxxxx/FTPXFER
[sudo] password for xxxxx: 
chown: changing ownership of `/home/xxxxx/FTPXFER': Operation not permitted

---

### Post by j_oly1999 on 2010-06-25
Bump to the top!  Anyone have any ideas here?

---

