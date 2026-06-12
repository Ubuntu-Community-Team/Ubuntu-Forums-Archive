---
title: "Respitory help"
date: 2006-05-24
forum: General Help
---

### Post by souteneur3190 on 2006-05-24
E: python2.4-minimal: subprocess post-installation script returned error exit status 1

how do i get rid of that i tried to reinstall python but it says the same thing.

---

### Post by souteneur3190 on 2006-05-24
i also tried to reinstall python

---

### Post by az on 2006-05-24
[QUOTE=souteneur3190]E: python2.4-minimal: subprocess post-installation script returned error exit status 1

how do i get rid of that i tried to reinstall python but it says the same thing.[/QUOTE]
Show all the output from running:

sudo apt-get -f install

---

### Post by souteneur3190 on 2006-05-24
[QUOTE=azz]Show all the output from running:

sudo apt-get -f install[/QUOTE]

here u r

> malubankudi@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1169 not upgraded.
58 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python2.4-minimal (2.4.3-0ubuntu4) ...
Compiling python modules in /usr/lib/python2.4 ...
Compiling /usr/lib/python2.4/site-packages/fuse.py ...
  File "/usr/lib/python2.4/site-packages/fuse.py", line 67
    self.optdict =
                  ^
SyntaxError: invalid syntax

dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
Setting up debconf (1.4.72ubuntu9) ...
Compiling /usr/lib/python2.4/site-packages/fuse.py ...
  File "/usr/lib/python2.4/site-packages/fuse.py", line 67
    self.optdict =
                  ^
SyntaxError: invalid syntax

dpkg: error processing debconf (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of console-data:
 console-data depends on debconf | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
 console-data depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing console-data (--configure):
 dependency problems - leaving unconfigured
Setting up libconsole (0.2.3dbs-60ubuntu3) ...

dpkg: dependency problems prevent configuration of console-tools:
 console-tools depends on debconf | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing console-tools (--configure):
 dependency problems - leaving unconfigured
Setting up readline-common (5.1-7build1) ...

Setting up libreadline5 (5.1-7build1) ...

dpkg: dependency problems prevent configuration of libssl0.9.8:
 libssl0.9.8 depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing libssl0.9.8 (--configure):
 dependency problems - leaving unconfigured
Setting up libdb4.3 (4.3.29-5build1) ...
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.3-0ubuntu4); however:
  Package python2.4-minimal is not configured yet.
 python2.4 depends on libssl0.9.8 (>= 0.9.8a-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python:
 python depends on python2.4 (>= 2.4.2); however:
  Package python2.4 is not configured yet.
dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python (>> 2.3); however:
  Package python is not configured yet.
 lsb-release depends on python (<< 2.5); however:
  Package python is not configured yet.
dpkg: error processing lsb-release (--configure):
 dependency problems - leaving unconfigured
Setting up libglib2.0-0 (2.10.2-1ubuntu3) ...

Setting up libatk1.0-0 (1.11.4-0ubuntu1) ...

Setting up pkg-config (0.20-1) ...
Setting up libglib2.0-dev (2.10.2-1ubuntu3) ...
Setting up libatk1.0-dev (1.11.4-0ubuntu1) ...
Setting up libfreetype6 (2.1.10-1ubuntu2) ...

Setting up libfontconfig1 (2.3.2-1.1ubuntu12) ...

Setting up libpng12-0 (1.2.8rel-5) ...

Setting up libcairo2 (1.0.4-0ubuntu1) ...

Setting up zlib1g-dev (1.2.3-6ubuntu4) ...
Setting up libfreetype6-dev (2.1.10-1ubuntu2) ...

Setting up libfontconfig1-dev (2.3.2-1.1ubuntu12) ...
Setting up libpng12-dev (1.2.8rel-5) ...

Setting up libcairo2-dev (1.0.4-0ubuntu1) ...
Setting up libglib2.0-data (2.10.2-1ubuntu3) ...
dpkg: dependency problems prevent configuration of libpango1.0-common:
 libpango1.0-common depends on debconf | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing libpango1.0-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libpango1.0-common (>= 1.12.2-0ubuntu3); however:
  Package libpango1.0-common is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libpango1.0-0 (>= 1.12.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
Setting up libjpeg62 (6b-11) ...

Setting up libtiff4 (3.7.4-1ubuntu3) ...

dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libgtk2.0-bin (>= 2.8.17-1ubuntu5); however:
  Package libgtk2.0-bin is not configured yet.
 libgtk2.0-0 depends on libpango1.0-0 (>= 1.12.2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-common:
 libgtk2.0-common depends on libgtk2.0-0; however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-dev:
 libpango1.0-dev depends on libpango1.0-0 (= 1.12.2-0ubuntu3); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libpango1.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libgtk2.0-0 (= 2.8.17-1ubuntu5); however:
  Package libgtk2.0-0 is not configured yet.
 libgtk2.0-dev depends on libpango1.0-dev (>= 1.10.0-2); however:
  Package libpango1.0-dev is not configured yet.
dpkg: error processing libgtk2.0-dev (--configure):
 dependency problems - leaving unconfigured
Setting up libjpeg62-dev (6b-11) ...
Setting up libncurses5-dev (5.5-1ubuntu3) ...
Setting up libperl5.8 (5.8.7-10ubuntu1) ...

Setting up libreadline4 (4.3-18) ...

Setting up libvte-common (0.12.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of libvte4:
 libvte4 depends on libgtk2.0-0 (>= 2.8.0); however:
  Package libgtk2.0-0 is not configured yet.
 libvte4 depends on libpango1.0-0 (>= 1.12.1); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libvte4 (--configure):
 dependency problems - leaving unconfigured
Setting up libxml2 (2.6.24.dfsg-1ubuntu1) ...

Setting up libxml2-dev (2.6.24.dfsg-1ubuntu1) ...
dpkg: dependency problems prevent configuration of python-apt:
 python-apt depends on python (<< 2.5); however:
  Package python is not configured yet.
 python-apt depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing python-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on python (<< 2.5); however:
  Package python is not configured yet.
 python-gnome2 depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-vte:
 python-vte depends on libgtk2.0-0 (>= 2.8.0); however:
  Package libgtk2.0-0 is not configured yet.
 python-vte depends on libpango1.0-0 (>= 1.12.1); however:
  Package libpango1.0-0 is not configured yet.
 python-vte depends on libvte4 (>= 1:0.12.1); however:
  Package libvte4 is not configured yet.
 python-vte depends on python (<< 2.5); however:
  Package python is not configured yet.
 python-vte depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing python-vte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gamin:
 python2.4-gamin depends on python2.4; however:
  Package python2.4 is not configured yet.
 python2.4-gamin depends on python (>= 2.4); however:
  Package python is not configured yet.
 python2.4-gamin depends on python (<< 3); however:
  Package python is not configured yet.
dpkg: error processing python2.4-gamin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gdbm:
 python2.4-gdbm depends on python2.4 (= 2.4.3-0ubuntu4); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-gdbm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-libxml2:
 python2.4-libxml2 depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-libxml2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-tk:
 python2.4-tk depends on python2.4 (= 2.4.3-0ubuntu4); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sabayon:
 sabayon depends on libgtk2.0-0 (>= 2.8.0); however:
  Package libgtk2.0-0 is not configured yet.
 sabayon depends on libpango1.0-0 (>= 1.12.1); however:
  Package libpango1.0-0 is not configured yet.
 sabayon depends on python (<< 2.5); however:
  Package python is not configured yet.
 sabayon depends on python (>= 2.4); however:
  Package python is not configured yet.
 sabayon depends on python2.4-gamin; however:
  Package python2.4-gamin is not configured yet.
 sabayon depends on python2.4-libxml2; however:
  Package python2.4-libxml2 is not configured yet.
dpkg: error processing sabayon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python (<< 2.5); however:
  Package python is not configured yet.
 update-manager depends on python (>= 2.4); however:
  Package python is not configured yet.
 update-manager depends on python; however:
  Package python is not configured yet.
 update-manager depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
 update-manager depends on python-apt (>= 0.6.14); however:
  Package python-apt is not configured yet.
 update-manager depends on python-vte (>= 1:0.11.15-0ubuntu3); however:
  Package python-vte is not configured yet.
 update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.
 update-manager depends on libvte4 (>= 1:0.11.15-0ubuntu3); however:
  Package libvte4 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
Setting up perl-modules (5.8.7-10ubuntu1) ...
Setting up gamin (0.1.7-2ubuntu1) ...
Setting up libgamin0 (0.1.7-2ubuntu1) ...

Setting up libgamin-dev (0.1.7-2ubuntu1) ...
Setting up perl (5.8.7-10ubuntu1) ...

Errors were encountered while processing:
 python2.4-minimal
 debconf
 console-data
 console-tools
 libssl0.9.8
 python2.4
 python
 lsb-release
 libpango1.0-common
 libpango1.0-0
 libgtk2.0-bin
 libgtk2.0-0
 libgtk2.0-common
 libpango1.0-dev
 libgtk2.0-dev
 libvte4
 python-apt
 python-gnome2
 python-vte
 python2.4-gamin
 python2.4-gdbm
 python2.4-libxml2
 python2.4-tk
 sabayon
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
malubankudi@ubuntu:~$ sudo apt-get -f install



---

### Post by az on 2006-05-24
Do you only have ubuntu repositories in your list?  If so, keep running

sudo apt-get -f install
and
sudo apt-get dist-upgrade

to try to untie the knot.

---

