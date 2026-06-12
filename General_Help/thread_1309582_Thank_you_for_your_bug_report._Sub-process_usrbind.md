---
title: "Thank you for your bug report. Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2009-11-01
forum: General Help
---

### Post by friendsforravi on 2009-11-01
I could not install any software in ubuntu 9.10 .

I am getting an error message that " Sub-process /usr/bin/dpkg returned an error code (1)"

for example:

ravi@ravi-desktop:~$ sudo apt-get install d4x
Reading package lists... Done
Building dependency tree
Reading state information... Done
d4x is already the newest version.
The following packages were automatically installed and are no longer required:
  ttf-liberation ttf-mscorefonts-installer cabextract
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)

I could not install any software through "Ubuntu software center" also.

---

