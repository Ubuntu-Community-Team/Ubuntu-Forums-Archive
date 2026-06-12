---
title: "input/output error when trying to install packages"
date: 2011-08-04
forum: General Help
---

### Post by coronacolada on 2011-08-04
```
tom@TriciaHelfer:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  dovecot-common resolvconf postfix-cdb gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/1,753 kB of archives.
After this operation, 5,124 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 65%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'xcompmgr': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I tried dpkg --clear-avail and apt-get update. it didn't help. 
Where do I go from here? It doesn't matter what package i try to install.

---

### Post by wildmanne39 on 2011-08-05
Hi, you can try these commands one at a time.
```
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
```
If you get more errors post them here please.
Thank you

---

