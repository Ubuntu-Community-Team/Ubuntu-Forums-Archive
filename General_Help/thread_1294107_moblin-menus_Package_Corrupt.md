---
title: "moblin-menus Package Corrupt?"
date: 2009-10-17
forum: General Help
---

### Post by Jason Cook on 2009-10-17
I am trying to figure out if the moblin-menus package is corrupt. A few packages depend on it so I can't install anything until the dependencies are met. this is what I do to recieve the error.
```
sudo apt-get install moblin-menus
```The output from the terminal is
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 evolution-common xulrunner-1.9.1 xulrunner-1.9.1-gnome-support libnotify0.4-cil
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  moblin-menus
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
1 not fully installed or removed.
Need to get 0B/5596B of archives.
After this operation, 135kB of additional disk space will be used.
(Reading database ... 195434 files and directories currently installed.)
Unpacking moblin-menus (from .../moblin-menus_0.1.3-0moblin1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/moblin-menus_0.1.3-0moblin1_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/settings.menu', which is also in package gnome-menus
Errors were encountered while processing:
 /var/cache/apt/archives/moblin-menus_0.1.3-0moblin1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
In Synaptic Package Manager it says that I have one broken package which is nautilus. In the package manager I try to reinstall nautilus and get this error
```
E: /var/cache/apt/archives/moblin-menus_0.1.3-0moblin1_all.deb: trying to overwrite `/etc/xdg/menus/settings.menu', which is also in package gnome-menus
```

---

### Post by Jason Cook on 2009-10-26
bump

---

