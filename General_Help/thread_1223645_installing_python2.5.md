---
title: "installing python2.5?"
date: 2009-07-26
forum: General Help
---

### Post by fcuk112 on 2009-07-26
i am trying to install python2.5 which is a dependency of guake.  i get the following error:

franky@bazooka:~$ sudo apt-get install python2.5
[sudo] password for franky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python2.5-doc python-profiler
The following NEW packages will be installed
  python2.5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2917kB of archives.
After this operation, 10.5MB of additional disk space will be used.
(Reading database ... 142154 files and directories currently installed.)
Unpacking python2.5 (from .../python2.5_2.5.4-1ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python2.5_2.5.4-1ubuntu4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python2.5_2.5.4-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

anyone else experiencing this and is there a fix?

thanks.

---

