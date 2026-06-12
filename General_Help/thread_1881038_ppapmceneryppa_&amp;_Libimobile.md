---
title: "ppa:pmcenery/ppa &amp; Libimobile"
date: 2011-11-14
forum: General Help
---

### Post by brothergrok on 2011-11-14
my terminal seems to not be able to find the ppa or the libimobiledevice. I just get:

sudo apt-get update shows:

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

&

After I type 'sudo apt-get install libimobiledevice'
I just get 'E: Unable to locate package libimobiledevice'.

This is the method I tried using:[http://askubuntu.com/questions/78535/how-to-install-libimobiledevice](http://askubuntu.com/questions/78535/how-to-install-libimobiledevice)

Use of synaptic package center does not help, either.

Still trying to get my ipod to sync and not freeze my laptop up in Rhythmbox or GTKPOD.

---

### Post by Toz on 2011-11-19
ppa: pmcenery/ppa doesn't seem to have an oneiric repository (see: [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/]("http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/")). There is a libmobiledevice2 in the regular repositories. 
> Package: libimobiledevice2
Priority: optional
Section: libs
Installed-Size: 208
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: gtkpod Maintainers <pkg-gtkpod-devel@lists.alioth.debian.or
g>
Architecture: i386
Source: libimobiledevice
Version: 1.1.1-1
Replaces: libimobiledevice0, libimobiledevice1, libiphone0
Depends: libc6 (>= 2.8), libgcrypt11 (>= 1.4.6), libglib2.0-0 (>= 2.14.1), libgn
utls26 (>= 2.7.14-0), libplist1 (>= 0.16), libtasn1-3 (>= 1.6-0), libusbmuxd1 (>
= 1.0.0), usbmuxd
Conflicts: libiphone0
Filename: pool/main/libi/libimobiledevice/libimobiledevice2_1.1.1-1_i386.deb
Size: 58148
MD5sum: 54294a6b81623032c3315bd95f0ffd65
SHA1: afb74d92e830efaa95567f48da06d04d50ab102c
SHA256: f94297b2402672148821040e8520e5731a6f42b80def729a6b00b3fb5d9b98e9
Description-en: Library for communicating with the iPhone and iPod Touch
 libimobiledevice is a library that talks the native Apple USB protocols that
 the iPhone and iPod Touch use. Unlike other projects, libimobiledevice does not depend on using any existing libraries from Apple.
Homepage: [http://libimobiledevice.org/](http://libimobiledevice.org/)
Description-md5: b63dfdd75baa933b181ba059d3cb96a2
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-mobile-desktop, kubun
tu-mobile, edubuntu-desktop, edubuntu-desktop-kde, edubuntu-usb, xubuntu-desktop
, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbunt
u-frontend, lubuntu-desktop, ubuntustudio-desktop

Not sure if that would help.

---

