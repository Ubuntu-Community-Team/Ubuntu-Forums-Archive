---
title: "Cannot &quot;make&quot;"
date: 2006-03-15
forum: General Help
---

### Post by steve196 on 2006-03-15
I have an app, that uses "make install" for installation, but the system does not recognize the "make" command.
gcc is installed.
Any suggestions?

---

### Post by Ramses de Norre on 2006-03-15
Run ./configure in the source dir and check the output on missing dependencies (libs, compilers, ...).

---

### Post by lamego on 2006-03-15
You should install the build essential package:
```
sudo apt-get install build-essential
```

---

### Post by gnomefreak on 2006-03-15
iirc you need to use sudo make install. also it is a good idea to install build-essential if you have not done so already. as for me i use checkinstall instead of make install. i was always told that checkinstall handles packages better.

---

### Post by steve196 on 2006-03-15
Thank you. I thought "make" was part of the gcc package.

---

### Post by petervk on 2006-03-15
Try to use [checkinstall]("https://wiki.ubuntulinux.org/CheckInstall") if you can insted of "make install". [Checkinstall]("https://wiki.ubuntulinux.org/CheckInstall") will create a deb with all references to the files installed through "make install".

So run
```
sudo apt-get install build-essential checkinstall
```

then in the directory with the source code
```
./configure
```
then
```
make
```
then
```
sudo checkinstall
```

Then if the program/package screws up or you decide you don't want it any more you run
```
sudo apt-get remove packagename
```

---

