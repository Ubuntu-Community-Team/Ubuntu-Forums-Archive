---
title: "Broken package while installing deluge"
date: 2009-10-20
forum: General Help
---

### Post by SableSlayer on 2009-10-20
So i was upgrading deluge from version 1.1.9 to 1.2.0_rc1 using the PPA repo's and package libtorrent-rasterbar2_0.14.6b-0ubuntu1_i386.deb broke.

So I tried the usual "sudo apt-get -f install" but to no avail.
> 
sableslayer@SableSlayer-DESKTOP:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-pygame python-numeric libtorrent-rasterbar2 deluge-core
  libsdl-ttf2.0-0 libmikmod2 libsdl-mixer1.2 python-libtorrent
  libboost-python1.37.0 libsdl-image1.2 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtorrent-rasterbar2
Suggested packages:
  libtorrent-rasterbar-dbg
The following NEW packages will be installed:
  libtorrent-rasterbar2
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/1166kB of archives.
After this operation, 3256kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 208730 files and directories currently installed.)
Unpacking libtorrent-rasterbar2 (from .../libtorrent-rasterbar2_0.14.6b-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libtorrent-rasterbar2_0.14.6b-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libtorrent-rasterbar.so.5.0.0', which is also in package libtorrent-rasterbar5
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libtorrent-rasterbar2_0.14.6b-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


After reading that I did "sudo apt-get autoremove"
> 
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  python-libtorrent: Depends: libtorrent-rasterbar2 (= 0.14.6b-0ubuntu1) but it is not installed
E: Unmet dependencies. Try using -f.



So after that I proceeded to command "sudo dpkg --configure -a" but yet again it didnt work.

> 
sableslayer@SableSlayer-DESKTOP:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of python-libtorrent:
 python-libtorrent depends on libtorrent-rasterbar2 (= 0.14.6b-0ubuntu1); however:
  Package libtorrent-rasterbar2 is not installed.
dpkg: error processing python-libtorrent (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deluge-core:
 deluge-core depends on python-libtorrent (>= 0.14.2); however:
  Package python-libtorrent is not configured yet.
dpkg: error processing deluge-core (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-libtorrent
 deluge-core


And after that one I decided to go use the synaptic broken filter which had no effect either. I also used synaptic to remove and reinstall deluge, which didnt work what so ever.

So now I am here, asking how can I fix this? Any help would be greatly appreciated!

---

### Post by SableSlayer on 2009-10-21
Fixed broken package by going into synaptic and removing every element that conflicted

---

