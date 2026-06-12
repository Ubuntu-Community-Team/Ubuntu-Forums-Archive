---
title: "can not make files"
date: 2010-04-03
forum: General Help
---

### Post by kanew1994 on 2010-04-03
Hi, experts

I'm new on linux.
Just installed the ubuntu on my new netbook yesterday. :p
I want to use opencv and get some information from web site.
Installed ffmpeg and libjpeg followed the instruction. 
./configure---make---make install---
Those files were fine execpt gtk2, libtiff and libpng.
These three files only finished the configure part.
When I run make command, errors came out.
"
kane@kane-laptop:~/Downloads/gtk+-2.20.0-doneconfig$ make
make: *** No targets specified and no makefile found.  Stop.
kane@kane-laptop:~/Downloads/gtk+-2.20.0-doneconfig$ ^C
kane@kane-laptop:~/Downloads/gtk+-2.20.0-doneconfig$ 
"
Same problem on them.
Anyone can help me?
Thanks

By the way, I tried make under root but same problems.

---

### Post by Lepy on 2010-04-03
Have you tried:

```
sudo apt-get install libtiff4 libpng3 gtk2-engines
```

or will opencv only work with svn versions? You may to try a different version. After typing install, you can press TAB to try an autocomplete the program name or list all available packges...depending on the package repositories you have enabled.

---

### Post by nem75 on 2010-04-03
kanew1994, maybe I don't get what you're tryig to do, but if you want to use the opencv library all you need to do is open Synaptic, search for opencv and install the package *libhighgui4*.

---

### Post by kanew1994 on 2010-04-03
Hi Lepy,
Thanks.
Problems solved.
I ran your command and get this information.
I didn't know when I install those two files.

kane@kane-laptop:~$ sudo apt-get install libtiff4 libpng3 gtk2-engines
[sudo] password for kane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtiff4 is already the newest version.
gtk2-engines is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libpng3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 934B of archives.
After this operation, 24.6kB of additional disk space will be used.
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/universe libpng3 1.2.37-1ubuntu0.1 [934B]
Fetched 934B in 0s (1,617B/s)
Selecting previously deselected package libpng3.
(Reading database ... 140271 files and directories currently installed.)
Unpacking libpng3 (from .../libpng3_1.2.37-1ubuntu0.1_all.deb) ...
Setting up libpng3 (1.2.37-1ubuntu0.1) ...

---

