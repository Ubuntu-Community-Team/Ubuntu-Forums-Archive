---
title: "do I need internet connection to install ccsm from ubuntu 9.04 live dvd"
date: 2009-07-06
forum: General Help
---

### Post by paneer_samosa on 2009-07-06
*do I need internet connection to install compiz configuration manager (ccsm) package from ubuntu 9.04 live dvd*

---

### Post by kpkeerthi on 2009-07-06
samosa,
It'd be easier if you are connected online so the package manager automatically downloads the required dependent packages. 

If you are not connected online, you need find out the dependencies of the package you are installing, download and install them, all yourself. 

Go to [http://packages.ubuntu.com](http://packages.ubuntu.com), search for the package, and in the package detail page, scroll to the bottom to download. Repeat the steps for all the dependencies. The dependencies will be listed in the package detail page.

Assuming you have your packages and its dependencies downloaded to a folder ~/pkgs, you could use dpkg to install them all at once.
```
cd ~/pkgs
sudo dpkg -i *.deb
```

---

### Post by paneer_samosa on 2009-07-06
actually I do not have internet connection, but have a live DVD so just wondering if it is there in that disto and can install from the DVD. is there a way to check if the package is available in DVD? I can see this in add/remove window but not sure if it'll install from dvd or net.

---

### Post by x33a on 2009-07-06
go to system -> administration -> software sources

enable installable from cdrom/dvd.

after that try
```
sudo aptitude install packagename
```
if it's available in the dvd, it should install, provided the dependencies are satisfied.

---

### Post by paneer_samosa on 2009-07-07
yes, this can be checked. will do this, thank you for guidance.

---

### Post by paneer_samosa on 2009-07-07
I have another LIVE DVD of Open Solaris that includes GNOME 2.24 and has this package installed (when I boot with this live DVD I am able to work with compiz desktop manager and able to do 3D settings).


Now is there a way, I can extract this package from this Open Solaris LIVE DVD and install on my system.

---

### Post by x33a on 2009-07-07
i don't think you can use opensolaris packages on ubuntu, but i may be wrong.

---

### Post by paneer_samosa on 2009-07-08
oh... I simply missed this angle. thank you for pointing out.

---

