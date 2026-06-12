---
title: "UBUNTU 8.04 Server: Unable to install using apt-get/dpkg"
date: 2009-08-26
forum: General Help
---

### Post by mlb85in on 2009-08-26
Hi,
I recently installed ubuntu 8.04 server on a Sun x2100 server. This server doesnot have direct internet connectivity. I installed it using an external CD drive.

I am trying to install few softwares but am unable to run an of the tools used to install any packages.

I am trying to install these:
-rw-r--r-- 1 root root  107256 2009-08-26 05:15 alien_8.78_all.deb
-rw-r--r-- 1 root root  515506 2009-08-26 05:15 debhelper_6.0.4ubuntu1_all.deb
-rw-r--r-- 1 root root 2232297 2009-08-26 05:15 cacti-0.8.7e.tar.gz
-rw-r--r-- 1 root root 1021427 2009-08-26 05:16 rrdtool-1.3.8.tar.gz
-rw-r--r-- 1 root root 2822465 2009-08-26 05:16 net-snmp-5.4.2.1-1.f9.i386.rpm



Here are the errors:
root@dpicacti:/var/cache/apt/archives# alien net-snmp-5.4.2.1-1.f9.i386.rpm
sh: rpm: not found
Error executing "LANG=C rpm -qp --queryformat %{NAME} net-snmp-5.4.2.1-1.f9.i386.rpm":  at /usr/share/perl5/Alien/Package.pm line 482.
root@dpicacti:/var/cache/apt/archives#



root@dpicacti:/myfiles# dpkg -i alien_8.78_all.deb
(Reading database ... 18154 files and directories currently installed.)
Preparing to replace alien 8.78 (using alien_8.78_all.deb) ...
Unpacking replacement alien ...
dpkg: dependency problems prevent configuration of alien:
 alien depends on debhelper (>= 3); however:
  Package debhelper is not configured yet.
 alien depends on rpm (>= 2.4.4-2); however:
  Package rpm is not installed.
 alien depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 alien depends on make; however:
  Package make is not installed.
dpkg: error processing alien (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alien
root@dpicacti:/myfiles#


root@dpicacti:/myfiles# dpkg -i debhelper_6.0.4ubuntu1_all.deb
(Reading database ... 18154 files and directories currently installed.)
Preparing to replace debhelper 6.0.4ubuntu1 (using debhelper_6.0.4ubuntu1_all.deb) ...
Unpacking replacement debhelper ...
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on binutils; however:
  Package binutils is not installed.
 debhelper depends on dpkg-dev (>= 1.14.15); however:
  Package dpkg-dev is not installed.
 debhelper depends on html2text; however:
  Package html2text is not installed.
 debhelper depends on po-debconf; however:
  Package po-debconf is not installed.
dpkg: error processing debhelper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 debhelper
root@dpicacti:/myfiles#


root@dpicacti:/var/cache/apt/archives# apt-get install rrdtool-1.3.8.tar.gz
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package rrdtool-1.3.8.tar.gz
root@dpicacti:/var/cache/apt/archives#

root@dpicacti:/var/cache/apt/archives# apt-get install rrdtool
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package rrdtool
root@dpicacti:/var/cache/apt/archives#



what I can I do to get this working... I am trying to setup cacti on this server and its giving me all sorts of trouble.

I was expecting these basic packages to be installed when I installed the OS and I was surprised to find out they aren't.
Please help.

---

### Post by Sam Lars on 2009-08-27
I think you would have to keep going on the dependencies, try to find a package where you can start.
There's a way with Synaptic to save a list of changes... not sure if that translates to the terminal.
How about using a machine that's connected to the Internet to download all the needed packages, and then copying them all?

---

### Post by bchurchill on 2009-08-27
For sudo apt-get install rrdtool you can try editing /etc/apt/sources.list and uncomment the appropriate repository lines.  Then run

sudo apt-get update

and then try

sudo apt-get install rrdtool

again.  Then install any dependencies you may need to get those .deb packages working.  Although in general I'd try and stick with Ubuntu packages if you can.

EDIT: Also the Ubuntu packages are great because they'll resolve dependencies for you and you won't have to go through all this...

---

### Post by mlb85in on 2009-08-27
Thank you both of you for your responses. Got this issue resolved.

FTP'd all the packages I got from the iso file to the server then continued installing all the dependencies and downloaded unavailable ones from online ubuntu repository...

finally had it all working 
now working on setting up OID's on cacti

---

