---
title: "Problemi con il montaggio di una partizione"
date: 2011-09-08
forum: General Help
---

### Post by agavin on 2011-09-08
Salve sto cercando di montare una partizione dalla quale dovrei recuperare dei files, in base a quanto trovato in internet ho eseguito i seguenti comandi, ditemi cosa sbaglio oppure cos'è che non va, grazie mille.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cc627

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris
root@ubuntu:~# mount -t ext3 /dev/sda1 /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by howefield on 2011-09-08
Hello and welcome to the forum, you might get a better response reposting in English or perhaps you could try here...

[http://forum.ubuntu-it.org/](http://forum.ubuntu-it.org/)

---

