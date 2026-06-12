---
title: "installing  kobo-desktop on 64bit system fails"
date: 2012-02-01
forum: General Help
---

### Post by foxy123 on 2012-02-01
Has anyone managed to install kobo-desktop on 64bit system? It asks fro dependencies but when I try to fetch them nothing happens:

```
$ sudo dpkg -i --force-architecture kobo-desktop.deb
[sudo] password for alex: 
Selecting previously deselected package kobo-desktop:i386.
(Reading database ... 197615 files and directories currently installed.)
Unpacking kobo-desktop:i386 (from kobo-desktop.deb) ...
dpkg: dependency problems prevent configuration of kobo-desktop:i386:
 kobo-desktop:i386 depends on libusb-0.1-4.
 kobo-desktop:i386 depends on libxml2.
dpkg: error processing kobo-desktop:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 kobo-desktop:i386

```

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED
  kobo-desktop:i386
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 200685 files and directories currently installed.)
Removing kobo-desktop:i386 ...
dpkg: warning: while removing kobo-desktop:i386, directory '/usr/local' not empty so not removed.
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...

```

---

