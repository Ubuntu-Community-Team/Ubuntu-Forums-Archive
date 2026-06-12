---
title: "Ubuntu 9.10 beta firefox flash problems"
date: 2009-10-23
forum: General Help
---

### Post by MichaelDance on 2009-10-23
When i open the .DEB file in the Packaghe Installer this error comes up:
" dpkg: unable to read filedescriptor flags for <package status and progress file
descriptor>: Bad file descriptor "

Do you know whats causing this problem installing Flash Player 10 Linux.DEB

Thanks

---

### Post by tommcd on 2009-10-24
To install flash in 9.10 just open a terminal and run:
```
sudo apt-get install flashplugin-installer
```
If you are trying to install to install flash from the .deb package from the Ubuntu repos, if perhaps you don't have an internet connection on the Ubuntu computer or something, then you don't need to open the .deb package. Put the .deb package in your home directoery, then open a terminal and run:
```
sudo dpkg -i package_name.deb
```
Replace package_name.deb with the exact package name.
Did you get the flash .deb package from the Ubuntu repos, or someplace else?

---

