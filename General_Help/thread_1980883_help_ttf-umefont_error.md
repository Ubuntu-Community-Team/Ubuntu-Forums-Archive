---
title: "help ttf-umefont error"
date: 2012-05-15
forum: General Help
---

### Post by frito on 2012-05-15
hi i just did a clean install of ubuntu 12.04 and i went to install the adobe package 
and i got this message:

```
remove   the transitional dummy package  or  ttf-umefont   in order to install Abobe.
```

i ran: dpkg cause im confused

```
me@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for me:
dpkg: dependency problems prevent configuration of ttf-umefont:
 ttf-umefont depends on fonts-horai-umefont; however:
 Package fonts-horai-umefont is not installed.
dpkg: error processing ttf-umefont (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-umefont
```

I went into Ubuntu software Centre and I keep getting  "no items installed or removed until package catalog is repaired."

I found ttf-umefont and tried to remove it.  I get this message of "Package system is broken - check if using third party repositories"

help

---

### Post by josephmills on 2012-05-15
try 
```
sudo apt-get -f install 
```
what happens ?
also what is output of
```
apt-cache dump ttf-umefont
```
and 
```
apt-cache policy show ttf-umefont
```

---

### Post by HamburgerTS on 2012-09-01
I stumbled over the same problem while installing wine 1.4 via software center (Ubuntu 12.04 64).

As suggested, I tried "sudo apt-get -f install":

```
martin@multivac:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fonts-horai-umefont
The following NEW packages will be installed:
  fonts-horai-umefont
0 upgraded, 1 newly installed, 0 to remove and 188 not upgraded.
1 not fully installed or removed.
Need to get 0 B/45.4 MB of archives.
After this operation, 89.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 264687 files and directories currently installed.)
Unpacking fonts-horai-umefont (from .../fonts-horai-umefont_434-1_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/fonts-horai-umefont_434-1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Processing triggers for fontconfig ...
Errors were encountered while processing:
 /var/cache/apt/archives/fonts-horai-umefont_434-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
martin@multivac:~$ 

```

Output from "apt-cache policy show ttf-umefont":

```
martin@multivac:~$ apt-cache policy show ttf-umefont
ttf-umefont:
  Installed: 434-1
  Candidate: 434-1
  Version table:
 *** 434-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
        100 /var/lib/dpkg/status
N: Unable to locate package show
martin@multivac:~$ 
```

Output of "apt-cache dump ttf-umefont" is extensive so I waive it (delivery on demand).

---

