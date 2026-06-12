---
title: "df command hangs"
date: 2006-06-27
forum: General Help
---

### Post by Mortuis on 2006-06-27
Ever since updating my **Ubuntu Server** installation to 6.06 the df command hangs.  I have to hit ctrl-c to get back the command line.

user@ubuntuserver:~$ df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              9614148   1513896   7611876  17% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                   46924       116     46808   1% /var/run
varlock                  46924         4     46920   1% /var/lock
procbususb                   0         0         0   -  /proc/bus/usb
udev                     46924        60     46864   1% /dev
devpts                       0         0         0   -  /dev/pts
devshm                   46924         0     46924   0% /dev/shm
lrm                      46924     18856     28068  41% /lib/modules/2.6.15-23-386/volatile
**this is where I have to hit ctrl-c**
user@ubuntuserver:~$

Anyone know what might be going wrong?

---

### Post by snowx1000 on 2006-06-27
Do you have any nfs shares or other network mounted drives?

---

### Post by Mortuis on 2006-07-06
I have a couple smbfs mounts.

---

### Post by jmacak on 2006-07-06
Hi 

The df command will 'hang' if there is no response from network mounted filesystems, such as samba shares.  I don't know if there is a timeout in linux--there is in some other unixes--where it might eventually come back.

cheers

joe in seattle

---

