---
title: "Contradictory application installation on 11.10"
date: 2011-10-15
forum: General Help
---

### Post by EvilRobot69 on 2011-10-15
So I am running Ubuntu 11.10 (fresh install) x64 on a Lenovo x120e with an E-350 processor, 4G of RAM, a 120G Intel X25-M SSD, and I have a problem. I try to install VLC and it uninstalls ZSNES. Then I try to install ZSNES and it wants to uninstall VLC and a bunch of my other games. What's the deal?

Output from apt-get:

ariw@polymorph:~/Downloads$ sudo apt-get install zsnes
[sudo] password for ariw: 
Sorry, try again.
[sudo] password for ariw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-wcf3.0-cil
  libmono-system2.0-cil libmono-sqlite2.0-cil libmono-corlib2.0-cil xclip
  libmono-i18n-west2.0-cil libmono-system-messaging2.0-cil
  libmono-posix2.0-cil libmono-messaging2.0-cil
  libmono-system-data-linq2.0-cil libmikmod2 libmono-system-data2.0-cil
  libmono2.0-cil libmono-sharpzip2.84-cil libmono-webbrowser2.0-cil
  libmono-system-web2.0-cil libmono-accessibility2.0-cil
  libmono-winforms2.0-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsdl1.2debian:i386 libsdl1.2debian-alsa:i386
The following packages will be REMOVED:
  libsdl-image1.2 libsdl-mixer1.2 libsdl1.2debian libsdl1.2debian-alsa
  libsmpeg0 vlc vvvvvv zachtronicsindustries-spacechem
The following NEW packages will be installed:
  libsdl1.2debian:i386 libsdl1.2debian-alsa:i386 zsnes:i386
0 upgraded, 3 newly installed, 8 to remove and 0 not upgraded.
Need to get 0 B/1,118 kB of archives.
After this operation, 296 MB disk space will be freed.

WTF?

---

### Post by EvilRobot69 on 2011-10-15
Could be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/854196](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/854196)

---

