---
title: "synaptic(apt) problems"
date: 2006-04-21
forum: General Help
---

### Post by aiduciukas on 2006-04-21
look at this:
*****@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libbrlapi1
The following NEW packages will be installed:
  libbrlapi1
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/50.8kB of archives.
After unpacking 115kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 119970 files and directories currently installed.)
Unpacking libbrlapi1 (from .../libbrlapi1_3.7.2-2ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libbrlapi1_3.7.2-2ubuntu1_i386.deb (--unpack):
 trying to overwrite `/lib/libbrlapi.so.0.4', which is also in package libbrlapiErrors were encountered while processing:
 /var/cache/apt/archives/libbrlapi1_3.7.2-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
help me, when i'm trying to remove this package it says that it isn't installed :|

---

### Post by krusbjorn on 2006-04-21
Probably not the optimal solution, but I would try:

sudo mv /lib/libbrlapi.so.0.4 /lib/libbrlapi.so.0.4.old

Then install the package. If things work out well, I would delete the /lib/libbrlapi.so.0.4.old after a while. Or keep it as a backup.

---

### Post by aiduciukas on 2006-04-21
nop it isn't working, same problem

---

### Post by krusbjorn on 2006-04-21
Restore the old name of the file you just renamed and try "sudo dpkg-divert --package libbrlapi1 --divert /lib/libbrlapi.so.0.4 --rename /lib/libbrlapi.so.0.4.new"

It will let you keep the old file and install the new one as ".new".

Edit: Check this thread. Seems to be a related problem: [http://ubuntuforums.org/showthread.php?t=162320](http://ubuntuforums.org/showthread.php?t=162320)

---

