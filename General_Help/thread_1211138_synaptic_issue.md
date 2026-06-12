---
title: "synaptic issue"
date: 2009-07-12
forum: General Help
---

### Post by metalmaniac248 on 2009-07-12
i recently canceled an installation of O3 server in gdebi and now i get this error message when i open synaptic

> E: The package o3spaces-server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


any ideas?

---

### Post by northern lights on 2009-07-12
What happens if you run```
sudo aptitude purge o3spaces-server
```?

---

### Post by metalmaniac248 on 2009-07-12
```
nick@nick-desktop:~$ sudo aptitude purge o3spaces-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  libboost-regex1.34.1{u} libglu1-xorg-dev{u} libosp5{u} libpq-dev{u} 
  libqt4-assistant{u} libqt4-help{u} libqt4-scripttools{u} 
  libqt4-xmlpatterns{u} libsqlite0-dev{u} mkvtoolnix{u} o3spaces-server{p} 
  qt4-qmake{u} twolame{u} vamps{u} w3c-dtd-xhtml{u} 
0 packages upgraded, 0 newly installed, 15 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 21.0MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing o3spaces-server (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 o3spaces-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done

nick@nick-desktop:~$ 

```

is the terminal output 

i still get the error when i open synaptic and a crash report was detected saying 


> sorry, the package "o3spaces-server 2.4.1p1" failed to install or upgrade

---

### Post by northern lights on 2009-07-12
Run```
sudo dpkg --remove --force-remove-reinstreq o3spaces-server && sudo apt-get autoremove && sudo apt-get autoclean && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by metalmaniac248 on 2009-07-12
thanks worked great

---

