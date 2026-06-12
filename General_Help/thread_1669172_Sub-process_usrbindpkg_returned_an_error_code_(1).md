---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-01-17
forum: General Help
---

### Post by xanbkn on 2011-01-17
[FONT=Verdana][SIZE=2]I just installed Ubuntu 10.10 LTS on my Dell today.  I'm trying to install LAMP by using the command [/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2]sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server[/SIZE][/FONT]

[FONT=Verdana][SIZE=2](I've already tried Tasksel).  I get this error:

[FONT=Lucida Console]Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.1_5.1.49-1ubuntu8.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]

I get an error while trying

[FONT=Lucida Console]sudo dpkg --configure -a


Setting up libxfcegui4-4 (4.6.4-1) ...
Setting up xfce4-appfinder (4.6.2-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 man-db
 php5-cli
 libapache2-mod-php5
 php5
 mysql-server
 php5-mysql
[/FONT]
I have no idea what to do.  I've also tried this:

[FONT=Lucida Console]sudo apt-get install -f[/FONT]

7 not fully installed or removed.
Need to get 0B/6,969kB of archives.
After this operation, 14.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

I have played around with deleting the pkgcache in /var/cache/apt/, but that doesn't help.  I've also realized that any other tools I try to install don't work (a search utility that I tried).

Thanks in advance,

XanBKN
[/SIZE][/FONT]

---

### Post by xanbkn on 2011-01-17
[SIZE=2]Deleting also doesn't work, with Synaptic and with sudo apt-get remove
[/SIZE]

---

