---
title: "asterisk install error"
date: 2006-02-22
forum: General Help
---

### Post by vrao on 2006-02-22
HI,

I am not getting too much info on this error..has anyone else had problems installing asterisk on ubuntu 5.10 before?

root@ndiasterisk:/home/vrao/software# apt-get install asterisk
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  asterisk-config asterisk-sounds-main unixodbc
Suggested packages:
  ohphone kphone asterisk-doc asterisk-dev rate-engine mpg123 libmyodbc odbc-postgresql libct1
The following NEW packages will be installed:
  asterisk asterisk-config asterisk-sounds-main unixodbc
0 upgraded, 4 newly installed, 0 to remove and 53 not upgraded.
Need to get 2601kB of archives.
After unpacking 6210kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main unixodbc 2.2.11-8ubuntu1 [268kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe asterisk-sounds-main 1:1.0.9.dfsg-1 [1183kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe asterisk-config 1:1.0.9.dfsg-1 [63.3kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe asterisk 1:1.0.9.dfsg-1 [1087kB]
Fetched 2601kB in 12s (215kB/s)

Preconfiguring packages ...
Selecting previously deselected package unixodbc.
(Reading database ... 56661 files and directories currently installed.)
Unpacking unixodbc (from .../unixodbc_2.2.11-8ubuntu1_i386.deb) ...
Selecting previously deselected package asterisk-sounds-main.
Unpacking asterisk-sounds-main (from .../asterisk-sounds-main_1%3a1.0.9.dfsg-1_all.deb) ...
Selecting previously deselected package asterisk-config.
Unpacking asterisk-config (from .../asterisk-config_1%3a1.0.9.dfsg-1_all.deb) ...
Selecting previously deselected package asterisk.
Unpacking asterisk (from .../asterisk_1%3a1.0.9.dfsg-1_i386.deb) ...
Setting up unixodbc (2.2.11-8ubuntu1) ...

Setting up asterisk-sounds-main (1.0.9.dfsg-1) ...
Setting up asterisk-config (1.0.9.dfsg-1) ...
Setting up asterisk (1.0.9.dfsg-1) ...
adduser: Warning: The home dir you specified already exists.
Adding system user `asterisk'...
Adding new group `asterisk' (114).
Adding new user `asterisk' (114) with group `asterisk'.
Home directory `/var/lib/asterisk' already exists.
adduser: No more than two names.
dpkg: error processing asterisk (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 asterisk
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ndiasterisk:/home/vrao/software#

-v

---

### Post by suRoot on 2006-02-22
It's complaining that the home directory & user already exist.  Have you tried removing them & reinstalling?

---

