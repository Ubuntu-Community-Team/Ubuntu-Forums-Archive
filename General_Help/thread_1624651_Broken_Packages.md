---
title: "Broken Packages"
date: 2010-11-18
forum: General Help
---

### Post by NoNameWill on 2010-11-18
I have 9 that won't install because of some error in libmagickcore2 :confused:

Here what I get from terminal.

```
will@Mobile-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcrypto++8 linux-headers-2.6.32-21-generic iw linux-headers-2.6.32-21 libfltk1.1 libupnp3 dkms libmpeg3-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6 libmagickcore2
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libmagickcore2
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
4 not fully installed or removed.
Need to get 0B/6,115kB of archives.
After this operation, 6,144kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/status' near line 760 package 'libmagickcore2':
 `Depends' field, invalid package name `libfreetype6!': character `!' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by NoNameWill on 2010-11-18
Don't know why this happened but I had to go in and clean up the sloppy package control file for libmagickcore2. There was a total of 4 errors. 
If any one else get this when updating you will get 9 broken packages because libmagickcore2 won't install correctly. 

The fix is to clean up the file to this. 

```
Package: libmagickcore2
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 6000
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: imagemagick
Version: 7:6.5.7.8-1ubuntu1
Depends: libbz2-1.0, libc6 (>= 2.4), libfreetype6 (>= 2.2.1), libgomp1 (>= 4.2.1), libice6 (>= 1:1.0.0), libjasper1 (>= 1.900.1), libjpeg62, liblcms1 (>= 1.15-1), libltdl7 (>= 2.2.6a), libpng12-0 (>= 1.2.13-4), libsm6, libtiff4, libx11-6, libxext6, libxml2 (>= 2.7.4), libxt6, zlib1g (>= 1:1.2.3.3.dfsg)
Recommends: ghostscript, gsfonts
Suggests: libmagickcore2-extra
Description: low-level image manipulation library
 The MagickCore API is a low-level interface between the C programming language
 and the ImageMagick image processing libraries and is recommended for
 wizard-level programmers only. Unlike the MagickWand C API which uses only a
 few opaque types and accessors, with MagickCore you almost exlusively access
 the structure members directly.
 .
 This package contains the C libraries needed to run executables that make
 use of MagickCore.
Homepage: http://www.imagemagick.org/
Original-Maintainer: ImageMagick Packaging Team <pkg-gmagick-im-team@lists.alioth.debian.org>

```After doing this the package will install either from terminal or one of the synaptic's.

---

