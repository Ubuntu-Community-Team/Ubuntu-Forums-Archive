---
title: "Gimp won't start  using Ubuntu 12.04LTS"
date: 2012-05-06
forum: General Help
---

### Post by hxleet on 2012-05-06
Hey guys I'm having some trouble with Gimp 2.8 on Ubuntu 12.04 LTS .  It won't start using the terminal or dash. I've tried uninstalling/reinstalling and still wont load.  it gives an error back when trying to start from terminal :

```
gimp: error while loading shared libraries: libbabl-0.0.so.0: 
cannot open shared object file: No such file or directory
```I've tried the following tips from other threads with no avail :

```
:~$ sudo apt-get purge gimp libgegl*
[sudo] password for hxsub: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgegl-0.0-0' for regex 'libgegl*'
Note, selecting 'libgegl-0.0-dbg' for regex 'libgegl*'
Note, selecting 'libgegl-0.0-dev' for regex 'libgegl*'
Note, selecting 'libgegl-0.0-doc' for regex 'libgegl*'
Package libgegl-0.0-dev is not installed, so not removed
Package libgegl-0.0-doc is not installed, so not removed
Package libgegl-0.0-dbg is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgfortran3 liblqr-1-0 libtiff-tools liblapack3gf libgtkglext1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gimp* libgegl-0.0-0*
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
After this operation, 15.8 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 172745 files and directories currently installed.)
Removing gimp ...
Purging configuration files for gimp ...
Removing libgegl-0.0-0 ...
Purging configuration files for libgegl-0.0-0 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

``````
:~$ sudo apt-get clean

sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgfortran3 liblqr-1-0 libtiff-tools liblapack3gf libgtkglext1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgegl-0.0-0
Suggested packages:
  gimp-help-en gimp-help
The following NEW packages will be installed:
  gimp libgegl-0.0-0
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 5,449 kB of archives.
After this operation, 15.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main gimp i386 2.6.12-1ubuntu1 [4,722 kB]
Get:2 http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ precise/main libgegl-0.0-0 i386 0.2.1-2~pp [727 kB]
Fetched 5,449 kB in 5s (913 kB/s)                                     
Selecting previously unselected package libgegl-0.0-0.
(Reading database ... 172180 files and directories currently installed.)
Unpacking libgegl-0.0-0 (from .../libgegl-0.0-0_0.2.1-2~pp_i386.deb) ...
Selecting previously unselected package gimp.
Unpacking gimp (from .../gimp_2.6.12-1ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up libgegl-0.0-0 (0.2.1-2~pp) ...
Setting up gimp (2.6.12-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

apt-cache policy libgegl-0.0.so.0
N: Unable to locate package libgegl-0.0.so.0
N: Couldn't find any package by regex 'libgegl-0.0.so.0'

:~$ aptitude search libgegl
i A libgegl-0.0-0                   - Generic Graphics Library                  
p   libgegl-0.0-dbg                 - Generic Graphics Library (debugging files)
p   libgegl-0.0-dev                 - Generic Graphics Library (development file
p   libgegl-0.0-doc                 - Generic Graphics Library (documentation)  

:~$ gimp
gimp: error while loading shared libraries: libgegl-0.0.so.0: 
cannot open shared object file: No such file or directory





```TIA
Paul.

---

### Post by lakerssuperman on 2012-05-06
[http://www.noobslab.com/2012/04/fixed-gimperror-while-loading-shared.html](http://www.noobslab.com/2012/04/fixed-gimperror-while-loading-shared.html)

Perhaps this will help you.

---

### Post by mc4man on 2012-05-06
looks like you're are using this ppa where the gimp builds failed so you're getting it's libgegl & the ubuntu repo gimp which aren't compatible
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

Either wait for gimp to actually build or switch to a different ppa like

[https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp)

---

### Post by hxleet on 2012-05-06
> **lakerssuperman said:**
> [http://www.noobslab.com/2012/04/fixed-gimperror-while-loading-shared.html](http://www.noobslab.com/2012/04/fixed-gimperror-while-loading-shared.html)

Perhaps this will help you.


I tried that already with no success. I noticed however that the link you posted(As do all the help forums I've found) show the error as 
```
gimp: error while loading shared libraries:** libbabl-0.0.so.0:** cannot open shared object file: No such file or directory
```But the error I'm receiving is:

```
gimp: error while loading shared libraries:** libgegl-0.0.so.0:** cannot open shared object file: No such file or directory
```NOTICE THE **libraries: libgegl-0.0.so.0: **PART.
Don't know if that matters but it still wont load.

---

### Post by hxleet on 2012-05-06
> **mc4man said:**
> 

Either wait for gimp to actually build or switch to a different ppa 



Thanks 4 the reply.  Ill just wait for gimp to come around.:-({|=  not in any rush.  
 Thanks again +1

---

### Post by mc4man on 2012-05-06
> **hxleet said:**
> Thanks 4 the reply.  Ill just wait for gimp to come around.:-({|=  not in any rush.  
 Thanks again +1

You'll likely see an update available when the ppa gets a gimp build done if you've left the ubuntu repo version installed. (gimp_2.6.12-1ubuntu1

Otherwise or in addition check that page linked - when you see a green arrow next to gimp in the latest updates section you'll be good to go
(update your sources before re-trying an install or even upgrade

---

