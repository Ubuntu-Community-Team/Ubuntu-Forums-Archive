---
title: "permission denied for shared libraries"
date: 2011-12-08
forum: General Help
---

### Post by vonHerman on 2011-12-08
Hello,

I'm working on Ubuntu 10.04.3 with 2.6.32-34-server kernel. 
Yesterday I started to experience weird permission problems with shared libraries.
Last thing I have done without any issues was installng awstats

```
Log started: 2011-12-07  16:09:10
Selecting previously deselected package awstats.
(Reading database ...
Unpacking awstats (from .../awstats_6.9~dfsg-1ubuntu3.10.04.1_all.deb) ...
Selecting previously deselected package libnet-xwhois-perl.
Unpacking libnet-xwhois-perl (from .../libnet-xwhois-perl_0.90-3_all.deb) ...
Processing triggers for man-db ...
Setting up awstats (6.9~dfsg-1ubuntu3.10.04.1) ...

Setting up libnet-xwhois-perl (0.90-3) ...
Log ended: 2011-12-07  16:09:12
```

When I found that my perl_mod for apache stopped working as it should I tried reinstalling it and found that there are some problems with access to libgdbm.so.3

```
Log started: 2011-12-07  19:31:22
(Reading database ...
Removing libapache2-reload-perl ...
Removing libapache2-mod-perl2 ...
Module perl disabled.
Run '/etc/init.d/apache2 restart' to activate new configuration!
Processing triggers for man-db ...
/usr/bin/mandb: error while loading shared libraries: libgdbm.so.3: cannot open shared object file: Permission denied
Log ended: 2011-12-07  19:31:25
```

As I started to investigate the error I found that there are numerous problems with access permission to shared libraries. Below are several examples:

```
[Thu Dec 08 14:48:13 2011] [error] [client 85.89.188.195] /usr/bin/perl: error while loading shared libraries: libperl.so.5.10: cannot open shared object file: Permission denied

 * Starting ClamAV daemon clamd /usr/sbin/clamd: error while loading shared libraries: libclamav.so.6: cannot open shared object file: Permission denied

 postfix/proxymap[2110]: fatal: dict_open: unsupported dictionary type: mysql (/usr/lib/postfix/dict_mysql.so not found.

imapd: /usr/bin/imapd: error while loading shared libraries: libfam.so.0: cannot open shared object file: Permission denied
```Can you please help me find the reason for this?

---

### Post by vonHerman on 2011-12-08
For anyone willing to help there is kern.log: [http://pastebin.com/7c1xUNKU](http://pastebin.com/7c1xUNKU)
and example of rights set for one of the libs and /usr dir rights
```
-rw-r--r-- 1 root root 1487368 2011-04-22 21:05 /usr/lib/libperl.so.5.10.1
drwxr-xr-x  10 root root  4096 2011-10-14 08:23 /usr
```

---

### Post by vonHerman on 2011-12-09
awwww...

Although i haven't changed rights to /usr/lib directory (and no trace for it in history)  simple: ```
chmod 755 /usr/lib 
``` resolved the problem. Was looking for it all day.

---

