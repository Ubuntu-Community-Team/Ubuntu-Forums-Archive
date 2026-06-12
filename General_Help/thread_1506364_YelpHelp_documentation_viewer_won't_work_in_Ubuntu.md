---
title: "Yelp/Help documentation viewer won't work in Ubuntu 9.04 after update"
date: 2010-06-10
forum: General Help
---

### Post by jre6 on 2010-06-10
I use Ubuntu 9.04. The help documentation viewer (yelp) in Ubuntu does not work after updating to Linux kernel 2.6.28-19. If I type yelp in terminal, this is what I get:
```

pseudouser@ubuntu:~$ yelp
Could not initialize gecko!

```I have all the yelp dependancies, but still it won't work. I also reinstalled yelp in the following manner:
```

pseudouser@ubuntu:~$ sudo apt-get remove yelp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-user-guide gnome-user-guide-en ubuntu-desktop ubuntu-docs yelp
0 upgraded, 0 newly installed, 5 to remove and 4 not upgraded.
After this operation, 72.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 126291 files and directories currently installed.)
Removing ubuntu-docs ...
Removing gnome-user-guide-en ...
Removing gnome-user-guide ...
Removing ubuntu-desktop ...
Removing yelp ...
Processing triggers for man-db ...
pseudouser@ubuntu:~$ sudo apt-get install yelp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  yelp
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 368kB of archives.
After this operation, 4575kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com jaunty/main yelp 2.25.1-0ubuntu5 [368kB]
Fetched 368kB in 12s (30.4kB/s)                                                                                                                             
Selecting previously deselected package yelp.
(Reading database ... 123329 files and directories currently installed.)
Unpacking yelp (from .../yelp_2.25.1-0ubuntu5_i386.deb) ...
Processing triggers for man-db ...
Setting up yelp (2.25.1-0ubuntu5) ...

pseudouser@ubuntu:~$ sudo apt-get install gnome-user-guide
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-user-guide
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 1784kB of archives.
After this operation, 3633kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com jaunty/main gnome-user-guide 2.26.0+svn20090323ubuntu5 [1784kB]
Fetched 1784kB in 59s (30.2kB/s)                                                                                                                            
Selecting previously deselected package gnome-user-guide.
(Reading database ... 123375 files and directories currently installed.)
Unpacking gnome-user-guide (from .../gnome-user-guide_2.26.0+svn20090323ubuntu5_all.deb) ...
Setting up gnome-user-guide (2.26.0+svn20090323ubuntu5) ...

pseudouser@ubuntu:~$ sudo apt-get install gnome-user-guide-en
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-user-guide-en
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 183kB of archives.
After this operation, 2621kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com jaunty/main gnome-user-guide-en 2.26.0+svn20090323ubuntu5 [183kB]
Fetched 183kB in 7s (24.2kB/s)                                                                                                                              
Selecting previously deselected package gnome-user-guide-en.
(Reading database ... 123543 files and directories currently installed.)
Unpacking gnome-user-guide-en (from .../gnome-user-guide-en_2.26.0+svn20090323ubuntu5_all.deb) ...
Setting up gnome-user-guide-en (2.26.0+svn20090323ubuntu5) ...

pseudouser@ubuntu:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ubuntu-docs
The following NEW packages will be installed:
  ubuntu-desktop ubuntu-docs
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 29.1kB/4003kB of archives.
After this operation, 61.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty/main ubuntu-desktop 1.140 [29.1kB]
Fetched 29.1kB in 2s (11.5kB/s)        
Selecting previously deselected package ubuntu-docs.
(Reading database ... 123891 files and directories currently installed.)
Unpacking ubuntu-docs (from .../ubuntu-docs_9.04.10_all.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.140_i386.deb) ...
Setting up ubuntu-docs (9.04.10) ...

Setting up ubuntu-desktop (1.140) ...
pseudouser@ubuntu:~$ sudo apt-get install ubuntu-docs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-docs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


```
A few days earlier, I refused to update Firefox. Could this be the problem?

---

