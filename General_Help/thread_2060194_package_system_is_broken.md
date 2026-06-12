---
title: "package system is broken"
date: 2012-09-19
forum: General Help
---

### Post by roadbase on 2012-09-19
i'm having problems with update manager, any help is appreciated. There seems to be some issue with cups not being recognized or installable...
apt-get tries its best but fails...any suggestions? 


sudo apt-get install -f
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libopenjpeg2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cups
Suggested packages:
  cups-pdf
The following NEW packages will be installed:
  cups
0 upgraded, 1 newly installed, 0 to remove and 268 not upgraded.
5 not fully installed or removed.
Need to get 0 B/1,275 kB of archives.
After this operation, 4,246 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 399624 files and directories currently installed.)
Unpacking cups (from .../cups_1.5.3-0ubuntu4_i386.deb) ...
update-rc.d: /etc/init.d/cups exists during rc.d purge (use -f to force)
dpkg: error processing /var/cache/apt/archives/cups_1.5.3-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/cups_1.5.3-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by f8l_0e on 2012-09-19
You might try the steps in the second to last post in this bug report: 

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1016376]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1016376")

---

### Post by roadbase on 2012-09-19
Excellent, that resolved it, thanks for the sleuthing.

---

### Post by f8l_0e on 2012-09-19
Cool.  Please mark the thread solved.

---

