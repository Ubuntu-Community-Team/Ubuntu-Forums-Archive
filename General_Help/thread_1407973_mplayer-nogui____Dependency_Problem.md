---
title: "mplayer-nogui    Dependency Problem?"
date: 2010-02-15
forum: General Help
---

### Post by mykrob on 2010-02-15
Haven't come across dependency problems in years..
Went to install DeVeDe on my desktop computer today, which is running Ubuntu 9.10. The app is working, but Apt/Synaptic complains about this:

```

sudo robinson@robinson-desktop:~$ sudo apt-get -f install
[sudo] password for robinson: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libvdpau1
The following NEW packages will be installed:
  libvdpau1
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0B/23.2kB of archives.
After this operation, 131kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 267905 files and directories currently installed.)
Unpacking libvdpau1 (from .../libvdpau1_0.3-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvdpau1_0.3-0ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau.so.1', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9
Errors were encountered while processing:
 /var/cache/apt/archives/libvdpau1_0.3-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
robinson@robinson-desktop:~$ 

```
The offending package according to Synaptic is mplayer-nogui, but if i remove it to satisfy the problem, then it wants to remove devede...

help?

---

### Post by mykrob on 2010-02-16
bump

---

### Post by mc4man on 2010-02-16
What ppa's, if any,  do you have enabled? ( would think you must have at least one - Avenard..?

---

