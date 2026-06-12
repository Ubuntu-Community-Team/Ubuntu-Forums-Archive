---
title: "Error while installing mediatomb"
date: 2012-03-28
forum: General Help
---

### Post by mayur.shetye on 2012-03-28
I get the following error when I try to install packages on my ubuntu 11.10
```
Sub-process /usr/bin/dpkg returned an error code (1)
```What is going wrong?What is the fix for this?

---

### Post by mayur.shetye on 2012-03-29
Please someone help me

---

### Post by raja.genupula on 2012-03-29
hi please post the complete outcome of terminal , only this small part not gonna help us . 

Thank you and wrap the text in Code tags by clicking at # in this window .

---

### Post by mayur.shetye on 2012-03-30
This is what I get while installing mediatomb
```
mayur@Mayur-PC:~$ sudo apt-get install minidlna[sudo] password for mayur: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-utils encfs libnet-ssleay-perl libaprutil1-dbd-sqlite3 libapr1
  libaprutil1-ldap librlog5 libindicate-qt1 libc-ares2 libio-socket-ssl-perl
  php5-cli liblastfm0 projectm-data libaprutil1 libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  minidlna
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 152 kB of archives.
After this operation, 422 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu/ oneiric/main minidlna i386 1.1.0stedy5 [152 kB]
Fetched 152 kB in 2s (54.5 kB/s)   
(Reading database ... 255807 files and directories currently installed.)
Unpacking minidlna (from .../minidlna_1.1.0stedy5_i386.deb) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/minidlna -g minidlna -s /usr/sbin/nologin -u 116 minidlna' returned error code 1. Exiting.
dpkg: error processing /var/cache/apt/archives/minidlna_1.1.0stedy5_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/minidlna_1.1.0stedy5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mayur@Mayur-PC:~$ sudo apt-get install mediatomb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-utils encfs libnet-ssleay-perl libaprutil1-dbd-sqlite3 libapr1
  libaprutil1-ldap librlog5 libindicate-qt1 libc-ares2 libio-socket-ssl-perl
  php5-cli liblastfm0 projectm-data libaprutil1 libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mediatomb-daemon
The following NEW packages will be installed:
  mediatomb mediatomb-daemon
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/21.2 kB of archives.
After this operation, 242 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 255807 files and directories currently installed.)
Unpacking mediatomb-daemon (from .../mediatomb-daemon_0.12.1-0ubuntu2_all.deb) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/mediatomb -g mediatomb -s /usr/sbin/nologin -u 116 mediatomb' returned error code 1. Exiting.
dpkg: error processing /var/cache/apt/archives/mediatomb-daemon_0.12.1-0ubuntu2_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package mediatomb.
Unpacking mediatomb (from .../mediatomb_0.12.1-0ubuntu2_all.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/mediatomb-daemon_0.12.1-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by raja.genupula on 2012-03-30
```
sudo rm -f /etc/gshadow.lock /etc/shadow.lock /etc/passwd.lock
```

do in terminal and try again

---

