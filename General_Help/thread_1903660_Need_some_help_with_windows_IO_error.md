---
title: "Need some help with windows I/O error"
date: 2012-01-03
forum: General Help
---

### Post by curt_nav_as on 2012-01-03
I have an ASUS UL50VT laptop that is unable to boot windows due to an I/O error. My main concern is the files on the HD that I haven't been able to backup to an external (i.e. pics and music). I created a bootable Ubuntu USB drive to access my files with worked like a charm however I am receiving error message (error splicing file: input/output error) while copying the files over. 

Any ideas or suggestions on how I can fix this headache? I'm pretty much clueless to Ubuntu...

Any help is much appreciated.

---

### Post by curt_nav_as on 2012-01-05
I've read that by fixing my windows MBR it will resolve this problem, however when I attempt to do so I get this error code:

ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo
0 upgraded, 1 newly installed, 0 to remove and 317 not upgraded.
1 not fully installed or removed.
Need to get 0 B/275 kB of archives.
After this operation, 807 kB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libpam0g (1.1.3-2ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libpam0g (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libpam0g
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?

---

### Post by jamesisin on 2012-01-05
I should think you won't want to try to fix your MBR by installing Lilo if Windows is controlling boot on that machine since Windows has its own boot loader.

If you are getting this kind of I/O error you may be right in thinking your drive is dying or dead.

You might try using a back-up utility like dd or rsync to copy files from the dying drive onto some external space (via USB?).

I would be apprehensive about performing any write operations on this drive until you have secured your data.

---

### Post by Bucky Ball on 2012-01-05
Hardware I'd say. Leave LILO alone and learn a bit more. You want to fix Windows but first you want to grab that data. If attempting to do so while booting Ubuntu from a CD or USB and you are getting I/O errors I maybe don't like the chances ...

---

