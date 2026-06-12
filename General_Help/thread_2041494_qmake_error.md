---
title: "qmake error"
date: 2012-08-12
forum: General Help
---

### Post by alenn on 2012-08-12
```
sudo pbuilder build bpad_0.9-ubuntu1.dsc
[sudo] password for alen: 
I: using fakeroot in build.
I: Current time: Mon Aug 13 00:00:27 CEST 2012
I: pbuilder-time-stamp: 1344808827
I: Building the build Environment
I: extracting base tarball [/var/cache/pbuilder/base.tgz]
I: creating local configuration
I: copying local configuration
I: mounting /proc filesystem
I: mounting /dev/pts filesystem
I: Mounting /var/cache/pbuilder/ccache
I: policy-rc.d already exists
I: Obtaining the cached apt archive contents
I: Setting up ccache
I: Installing the build-deps
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: i386
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder to satisfy the
 build-dependencies of the package being currently built.
Depends: debhelper (>= 8.0.0)
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 13785 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: pbuilder-satisfydepends-dummy: dependency problems, but configuring anyway as you requested:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 8.0.0); however:
  Package debhelper is not installed.
Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
The following NEW packages will be installed:
  bsdmainutils{a} debhelper{a} file{a} gettext{a} gettext-base{a} 
  groff-base{a} html2text{a} intltool-debian{a} libcroco3{a} libmagic1{a} 
  libpipeline1{a} libunistring0{a} libxml2{a} man-db{a} po-debconf{a} 
The following packages are RECOMMENDED but will NOT be installed:
  curl libmail-sendmail-perl lynx-cur wget xml-core 
0 packages upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/5440 kB of archives. After unpacking 18.4 MB will be used.
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously deselected package libpipeline1.
(Reading database ... 13785 files and directories currently installed.)
Unpacking libpipeline1 (from .../libpipeline1_1.2.0-3_i386.deb) ...
Selecting previously deselected package libmagic1.
Unpacking libmagic1 (from .../libmagic1_5.04-5ubuntu3_i386.deb) ...
Selecting previously deselected package file.
Unpacking file (from .../file_5.04-5ubuntu3_i386.deb) ...
Selecting previously deselected package bsdmainutils.
Unpacking bsdmainutils (from .../bsdmainutils_8.2.3_i386.deb) ...
Selecting previously deselected package gettext-base.
Unpacking gettext-base (from .../gettext-base_0.18.1.1-3ubuntu1_i386.deb) ...
Selecting previously deselected package groff-base.
Unpacking groff-base (from .../groff-base_1.21-6_i386.deb) ...
Selecting previously deselected package libxml2.
Unpacking libxml2 (from .../libxml2_2.7.8.dfsg-4_i386.deb) ...
Selecting previously deselected package man-db.
Unpacking man-db (from .../man-db_2.6.0.2-2_i386.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-15_i386.deb) ...
Selecting previously deselected package libcroco3.
Unpacking libcroco3 (from .../libcroco3_0.6.2-1_i386.deb) ...
Selecting previously deselected package libunistring0.
Unpacking libunistring0 (from .../libunistring0_0.9.3-4_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.18.1.1-3ubuntu1_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.16+nmu1_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_8.9.0ubuntu1_all.deb) ...
Setting up libpipeline1 (1.2.0-3) ...
Setting up libmagic1 (5.04-5ubuntu3) ...
Setting up file (5.04-5ubuntu3) ...
Setting up bsdmainutils (8.2.3) ...
update-alternatives: using /usr/bin/bsd-write to provide /usr/bin/write (write) in auto mode.
update-alternatives: using /usr/bin/bsd-from to provide /usr/bin/from (from) in auto mode.
Setting up gettext-base (0.18.1.1-3ubuntu1) ...
Setting up groff-base (1.21-6) ...
Setting up libxml2 (2.7.8.dfsg-4) ...
Setting up man-db (2.6.0.2-2) ...
Building database of manual pages ...
Setting up html2text (1.3.2a-15) ...
Setting up libcroco3 (0.6.2-1) ...
Setting up libunistring0 (0.9.3-4) ...
Setting up gettext (0.18.1.1-3ubuntu1) ...
Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.16+nmu1) ...
Setting up debhelper (8.9.0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
Current status: 0 broken [-1].
 -> Finished parsing the build-deps
Reading package lists...
Building dependency tree...
Reading state information...
fakeroot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
I: Copying back the cached apt archive contents
I: Copying source file
I: copying [bpad_0.9-ubuntu1.dsc]
I: copying [./bpad_0.9-ubuntu1.tar.gz]
I: Extracting source
gpgv: Signature made Sun Aug 12 21:56:00 2012 UTC using RSA key ID 6CCE5D08
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./bpad_0.9-ubuntu1.dsc
dpkg-source: info: extracting bpad in bpad-0.9
dpkg-source: info: unpacking bpad_0.9-ubuntu1.tar.gz
I: Building the package
I: Running cd tmp/buildd/*/ && env PATH=/usr/lib/ccache:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin dpkg-buildpackage -us -uc  -rfakeroot
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package bpad
dpkg-buildpackage: source version 0.9-ubuntu1
dpkg-buildpackage: source changed by Alen Masic (Novi gpg) <alenn.masic@gmail.com>
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build bpad-0.9
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
   dh_clean
 dpkg-source -b bpad-0.9
dpkg-source: warning: no source format specified in debian/source/format, see dpkg-source(1)
dpkg-source: info: using source format `1.0'
dpkg-source: warning: Version number suggests Ubuntu changes, but Maintainer: does not have Ubuntu address
dpkg-source: warning: Version number suggests Ubuntu changes, but there is no XSBC-Original-Maintainer field
dpkg-source: info: building bpad in bpad_0.9-ubuntu1.tar.gz
dpkg-source: info: building bpad in bpad_0.9-ubuntu1.dsc
 debian/rules build
dh build 
   dh_testdir
   dh_auto_configure
Can't exec "qmake": No such file or directory at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 211.
dh_auto_configure: qmake -makefile -nocache QMAKE_CFLAGS_RELEASE=-g -O2 QMAKE_CFLAGS_DEBUG=-g -O2 QMAKE_CXXFLAGS_RELEASE=-g -O2 QMAKE_CXXFLAGS_DEBUG=-g -O2 QMAKE_LFLAGS_RELEASE=-Wl,-Bsymbolic-functions QMAKE_LFLAGS_DEBUG=-Wl,-Bsymbolic-functions QMAKE_STRIP=: PREFIX=/usr failed to to execute: No such file or directory
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
E: Failed autobuilding of package
I: unmounting /var/cache/pbuilder/ccache filesystem
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//18055 and its subdirectories
```

Hi all, I'm trying to build source package but I'm keep getting this error: "Can't exec "qmake": No such file or directory at..."
can you help me to solve this.

---

### Post by ad17yam on 2013-07-04
Hi alenn, just wondering if you were able to figure this issue out. I am facing the same problem. Any help would be appreciated.

---

