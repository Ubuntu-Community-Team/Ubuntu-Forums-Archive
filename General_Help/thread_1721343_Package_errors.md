---
title: "Package errors"
date: 2011-04-04
forum: General Help
---

### Post by c-m on 2011-04-04
Hi,

I'm getting the following error every time i run the package manager to install or update etc..

```
E: nxserver: subprocess installed post-installation script returned error exit status 1
```

Despite the error, apt still works and allows me to install/remove apps.

The application in question also works fine too.

---

### Post by zvacet on 2011-04-05
Try 

```
sudo dpkg --configure -a
```

---

### Post by c-m on 2011-04-20
Got two errors using that command:

```
carl@Mint ~ $ sudo dpkg --configure -a
[sudo] password for carl: 
Setting up gerix-wifi-cracker-ng (2.0-bt11) ...
ln: creating symbolic link `/pentest/wireless/gerix-wifi-cracker-ng': No such file or directory
dpkg: error processing gerix-wifi-cracker-ng (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up nxserver (3.4.0-14) ...
NX> 704 ERROR: Cannot add user: nx.
NX> 704 ERROR: User: nx already exists.
NX> 704 To fix the problem, you may try to completely uninstall NX
NX> 704 Server and install it from scratch. If this is not enough,
NX> 704 please delete the nx user by using the system commands and
NX> 704 proceed with a new installation of NX Server.
dpkg: error processing nxserver (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gerix-wifi-cracker-ng
 nxserver
  
```

---

