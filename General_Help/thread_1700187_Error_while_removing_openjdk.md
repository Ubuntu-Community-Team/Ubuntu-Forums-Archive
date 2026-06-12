---
title: "Error while removing openjdk"
date: 2011-03-04
forum: General Help
---

### Post by patelR on 2011-03-04
I wanted to remove openjdk so used the command :
 sudo apt-get remove openjdk-6-jdk

Details :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openjdk-6-jdk is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libpthread-stubs0 x11proto-kb-dev xtrans-dev
  x11proto-input-dev libxt-dev libxau-dev libx11-dev libxcb1-dev
  x11proto-core-dev libxdmcp-dev libpthread-stubs0-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up slapd (2.4.23-0ubuntu3.4) ...
  Creating initial slapd configuration... mkdir: cannot create directory `/etc/openldap/slapd.conf': No such file or directory
dpkg: error processing slapd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

Why is it trying to access slapd configuration file. What's the realtion?
 (Just few days back I was experimenting with openldap, then had deleted the /etc/openldap folder).

---

