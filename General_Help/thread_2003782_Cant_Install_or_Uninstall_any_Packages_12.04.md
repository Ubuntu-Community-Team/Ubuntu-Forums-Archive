---
title: "Cant Install or Uninstall any Packages 12.04"
date: 2012-06-14
forum: General Help
---

### Post by Phillipie99 on 2012-06-14
Every time I run apt-get upgrade or apt-get -f install on my Ubuntu 12.04 server, I get the output below

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-24-generic (3.2.0-24.37) ...
Internal Error: Could not find image (/boot/vmlinuz-3.2.0-24-generic)
dpkg: error processing linux-image-3.2.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-24-generic; however:
  Package linux-image-3.2.0-24-generic is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.24.26); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                              Errors were encountered while processing:
 linux-image-3.2.0-24-generic
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I have run dpkg-reconfigure -a,  apt-get clean, and apt-get autoremove then tried the update/upgrade command and still got the errors. This occurred after an upgrade from 11.10.

---

### Post by hwttdz on 2012-06-14
I don't have linux-image-server installed on my machine, but I'd try

sudo dpkg --configure linux-image-server 

and hopefully it'll walk you through.  Or maybe it's complaining that you need linux-image-server but you don't have it installed, in which case just install it.

---

