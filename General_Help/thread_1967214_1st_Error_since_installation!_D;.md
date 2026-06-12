---
title: "1st Error since installation! D;"
date: 2012-04-27
forum: General Help
---

### Post by Lord_Solrac2 on 2012-04-27
Ok, so I wubi'd my Xubuntu 12.04 and I normally installed all 
the apps I use normally until...

> solrac@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up man-db (2.6.1-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
solrac@ubuntu:~$ 


Any Suggestions?

---

### Post by Rubi1200 on 2012-04-28
Hi,
you can try the following command:

```
sudo dpkg --configure -a
```

Let us know what happens (post error messages please).

---

