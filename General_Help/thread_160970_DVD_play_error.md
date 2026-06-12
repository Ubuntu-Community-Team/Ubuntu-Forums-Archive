---
title: "DVD play error"
date: 2006-04-16
forum: General Help
---

### Post by anxean on 2006-04-16
lanxean@ubuntu:~$ ogle
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshot'
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshotWithSPU'
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread3/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread3/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
FATAL[ogle_mpeg_ps]: dvdreadblocks failed
anxean@ubuntu:~$

Any ideas on what to do ?

-anxean

---

### Post by Perfect Storm on 2006-04-16
First setup your soucelist: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) 

```
sudo apt-get install libdvdcss2 libdvdread3
```

---

### Post by anxean on 2006-04-16
Reading package lists... Done
anxean@ubuntu:~$ sudo apt-get install libdvdcss2 libdvdread3
Reading package lists... Done
Building dependency tree... Done
libdvdcss2 is already the newest version.
libdvdread3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 284 not upgraded

i get the same error

---

### Post by Perfect Storm on 2006-04-16
Hmmm...Why don't you upgrade? It says there is 284 waiting for updating and upgrading? It's possible it will solve your problem.

```
sudo apt-get update
sudo apt-get upgrade
```

---

