---
title: "Software center break - how to repair?"
date: 2012-08-17
forum: General Help
---

### Post by eslavko on 2012-08-17
Hello..

I try to install some library to support i386 for freebasic but I break software center utiliti.

I try to click repair few times but doesn't work.
Some help?


installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 308635 files and directories currently installed.) 
Unpacking libxpm-dev (from .../libxpm-dev_1%3a3.5.9-4_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libxpm-dev_1%3a3.5.9-4_amd64.deb (--unpack): 
 './usr/share/doc/libxpm-dev/xpm.pdf.gz' is different from the same file on the system 
Errors were encountered while processing: 
 /var/cache/apt/archives/libxpm-dev_1%3a3.5.9-4_amd64.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
dpkg: dependency problems prevent configuration of libxaw7-dev: 
 libxaw7-dev depends on libxpm-dev; however: 
  Package libxpm-dev is not installed. 
dpkg: error processing libxaw7-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of xorg-dev: 
 xorg-dev depends on libxaw7-dev; however: 
  Package libxaw7-dev is not configured yet. 
 xorg-dev depends on libxpm-dev; however: 
  Package libxpm-dev is not installed. 
dpkg: error processing xorg-dev (--configure): 
 dependency problems - leaving unconfigured

---

### Post by eslavko on 2012-08-17
when I delete folder
./usr/share/doc/libxpm-dev/
and reinstal libxpm-dev all comes ok again.

---

