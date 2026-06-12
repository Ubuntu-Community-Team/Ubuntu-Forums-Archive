---
title: "cant install kdelibs5"
date: 2009-09-23
forum: General Help
---

### Post by boogey on 2009-09-23
update manager wants me to install:

kdelibs5 and kdelibs5-data

if I try I get this:

"you have 1 broken package on your system"

and: An error occurred: 
E: /var/cache/apt/archives/kdelibs5-data_4%
3a4.0.5-0ubuntu1~hardy3_all.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/kdelibs5_4%3a4.0.5-0ubuntu1~hardy3_i386.deb: failed in buffer_write(fd) (10, ret=-1)

I tried to fix the broken package in the Synaptic Package Manager with "Fix broken packages" but after applying I get the same error message as above. details of the failure are:

 /var/cache/apt/archives/kdelibs5-data_4%3a4.0.5-0ubuntu1~hardy3_all.deb
 /var/cache/apt/archives/kdelibs5_4%3a4.0.5-0ubuntu1~hardy3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of kde4libs-bin:
 kde4libs-bin depends on kdelibs5 (= 4:4.0.5-0ubuntu1~hardy3); however:
  Package kdelibs5 is not installed.
dpkg: error processing kde4libs-bin (--configure):
 dependency problems - leaving unconfigured
Setting up network-manager (0.6.6-0ubuntu5.8.04.2) ...
 * Reloading system message bus config...
   ...done.
 * Restarting network connection manager NetworkManager
/usr/sbin/NetworkManager: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured


anyone any idea how to fix this dependency problem?
thanks


edit: maybe I should have posed this in the installation section - if anyone wants to move it there, that's cool.

---

