---
title: "GTK+  dev libraries and Ubuntu 10.04"
date: 2010-10-03
forum: General Help
---

### Post by cap10Ibraim on 2010-10-03
after some googling the only way i can find to install  libgtk2.0-dev is 

```
aptitude install libgtk2.0-dev
```
below is my output is it safe to proceed ? 
```

root@CoreRoute:/home/ibrahim# aptitude install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  libatk1.0-dev libfreetype6-dev libglib2.0-dev libgtk2.0-dev libpng12-dev 
The following NEW packages will be installed:
  build-essential{a} cvs{a} debhelper{a} dpkg-dev{a} fakeroot{a} gettext{a} html2text{a} intltool-debian{a} libcairo2-dev{a} 
  libdirectfb-dev{a} libdirectfb-extra{a} libexpat1-dev{a} libfontconfig1-dev{a} libice-dev{a} libjpeg62-dev{a} 
  libmail-sendmail-perl{a} libpango1.0-dev{a} libpixman-1-dev{a} libpthread-stubs0{a} libpthread-stubs0-dev{a} libsm-dev{a} 
  libsys-hostname-long-perl{a} libsysfs-dev{a} libx11-dev{a} libxau-dev{a} libxcb-render-util0-dev{a} libxcb-render0-dev{a} 
  libxcb1-dev{a} libxcomposite-dev{a} libxcursor-dev{a} libxdamage-dev{a} libxdmcp-dev{a} libxext-dev{a} libxfixes-dev{a} 
  libxft-dev{a} libxi-dev{a} libxinerama-dev{a} libxrandr-dev{a} libxrender-dev{a} patch{a} po-debconf{a} 
  x11proto-composite-dev{a} x11proto-core-dev{a} x11proto-damage-dev{a} x11proto-fixes-dev{a} x11proto-input-dev{a} 
  x11proto-kb-dev{a} x11proto-randr-dev{a} x11proto-render-dev{a} x11proto-xext-dev{a} x11proto-xinerama-dev{a} 
  xtrans-dev{a} xz-utils{a} zlib1g-dev{a} 
The following packages will be REMOVED:
  liblzo2-2{u} libpkcs11-helper1{u} openssl-blacklist{u} openvpn-blacklist{u} python-bittorrent{u} 
0 packages upgraded, 59 newly installed, 5 to remove and 4 not upgraded.
Need to get 16.1MB/20.3MB of archives. After unpacking 56.4MB will be used.
The following packages have unmet dependencies:
  libatk1.0-dev: Depends: libatk1.0-0 (= 1.30.0-0ubuntu2) but 1.30.0-0ubuntu2.1 is installed.
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.24.0-0ubuntu4) but 2.24.1-0ubuntu1 is installed.
  libfreetype6-dev: Depends: libfreetype6 (= 2.3.11-1ubuntu2) but 2.3.11-1ubuntu2.2 is installed.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is installed.
  libpng12-dev: Depends: libpng12-0 (= 1.2.42-1ubuntu2) but 1.2.42-1ubuntu2.1 is installed.
The following actions will resolve these dependencies:

Downgrade the following packages:
gtk2-engines-pixbuf [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libatk1.0-0 [1.30.0-0ubuntu2.1 (now) -> 1.30.0-0ubuntu2 (lucid)]
libatk1.0-data [1.30.0-0ubuntu2.1 (now) -> 1.30.0-0ubuntu2 (lucid)]
libfreetype6 [2.3.11-1ubuntu2.2 (now) -> 2.3.11-1ubuntu2 (lucid)]
libgail-common [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libgail18 [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libglib2.0-0 [2.24.1-0ubuntu1 (now) -> 2.24.0-0ubuntu4 (lucid)]
libglib2.0-data [2.24.1-0ubuntu1 (now) -> 2.24.0-0ubuntu4 (lucid)]
libgtk2.0-0 [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libgtk2.0-bin [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libpng12-0 [1.2.42-1ubuntu2.1 (now) -> 1.2.42-1ubuntu2 (lucid)]

Score is 386

Accept this solution? [Y/n/q/?] 


```

---

### Post by mc4man on 2010-10-03
you should not do that - open your software sources and under the updates tab make sure that the first 2 boxes are enables (security and updates

If you had to enable either then click close and reload, otherwise open a terminal and run 
sudo apt-get update

All those mentioned packages being downgraded are at lucid-updates versions, but only lucid versions are being found for the -dev packages
dev packages must match the installed shared package

Ex.
[http://packages.ubuntu.com/lucid-updates/libatk1.0-dev](http://packages.ubuntu.com/lucid-updates/libatk1.0-dev)
ect., ect.

---

### Post by cap10Ibraim on 2010-10-03
thanks 
I was expecting a a lot of mess if I  answered "Y"

```
Accept this solution? [Y/n/q/?]
```

---

