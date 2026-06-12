---
title: "apt crashes on zumodrive deb"
date: 2011-07-22
forum: General Help
---

### Post by muckblit on 2011-07-22
Easy. Instead use dpkg -i zumo*deb, and then apt-get -f install will install two missing libs and then config zumodrive. 32-bit natty here. Somebody actually submitted a bug report against apt for this.

sudo dpkg -i zum*deb
Selecting previously deselected package zumodrive.
(Reading database ... 245533 files and directories currently installed.)
Unpacking zumodrive (from zumodrive-ubuntu8-i386-0.989.deb) ...
dpkg: dependency problems prevent configuration of zumodrive:
 zumodrive depends on libinotifytools0 (>= 3.12-1); however:
  Package libinotifytools0 is not installed.
 zumodrive depends on libgnet2.0-0 (>= 2.0.0); however:
  Package libgnet2.0-0 is not installed.
dpkg: error processing zumodrive (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 zumodrive
bob@laptop:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgnet2.0-0 libinotifytools0
The following NEW packages will be installed:
  libgnet2.0-0 libinotifytools0
0 upgraded, 2 newly installed, 0 to remove and 38 not upgraded.
1 not fully installed or removed.
Need to get 90.5 kB of archives.
After this operation, 303 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe libinotifytools0 i386 3.13-3 [21.2 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe libgnet2.0-0 i386 2.0.8-2 [69.3 kB]
Fetched 90.5 kB in 0s (117 kB/s)       
Selecting previously deselected package libinotifytools0.
(Reading database ... 245713 files and directories currently installed.)
Unpacking libinotifytools0 (from .../libinotifytools0_3.13-3_i386.deb) ...
Selecting previously deselected package libgnet2.0-0.
Unpacking libgnet2.0-0 (from .../libgnet2.0-0_2.0.8-2_i386.deb) ...
Setting up libinotifytools0 (3.13-3) ...
Setting up libgnet2.0-0 (2.0.8-2) ...
Setting up zumodrive (0.989) ...
Processing triggers for libc-bin ...

---

