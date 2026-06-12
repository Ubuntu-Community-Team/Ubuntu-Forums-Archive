---
title: "Cannot install any new software."
date: 2012-03-10
forum: General Help
---

### Post by masterman934 on 2012-03-10
Please, help!

I was trying to install wine but I accidently closed the terminal during the installation and now I can not install anything. I get this message:


marin@marin-Inspiron-N5010:~$ sudo apt-get upgrade
[sudo] password for marin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up wine1.3 (1.3.28-0ubuntu2~oneiric1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.3 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 wine1.3
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

Tried to fix broken packages with synaptic but this didnt work out. What should I do?

---

### Post by masterman934 on 2012-03-10
tried to purge wine but this is not working either.

---

### Post by kc1di on 2012-03-10
Go to a terminal and issue the following command:

 sudo dpkg --configure -a

If that does not work try this again in terminal
sudo apt-get clean
sudo apt-get auto clean

P.S. Sometimes a reboot will also help.

---

### Post by masterman934 on 2012-03-10
doesn't work:

marin@marin-Inspiron-N5010:~$ sudo dpkg --configure -a
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db

sudo apt-get clean also doesnt work

---

### Post by matt_symes on 2012-03-10
Hi

Have you rebooted to try to release the lock ?

> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up wine1.3 (1.3.28-0ubuntu2~oneiric1) ..

EDIT: You can see what has the lock on the file with

```
lsof /var/cache/debconf/config.dat
```

EDIT2: Just noticed to was beaten to the reboot idea.

Kind regards

---

### Post by masterman934 on 2012-03-10
Rebooting did the work. Thanks

---

### Post by kc1di on 2012-03-10
> **masterman934 said:**
> Rebooting did the work. Thanks

If that solved it please mark thread as Solved :)

---

