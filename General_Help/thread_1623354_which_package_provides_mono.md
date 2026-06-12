---
title: "which package provides mono?"
date: 2010-11-16
forum: General Help
---

### Post by scharkalvin on 2010-11-16
I'm trying to install a third party development package for the TI DM355 platform.  The build script for this tests for the mono package which must have been available in a previous release of Ubuntu but has been deprecated in version 10.  Which package provides mono support and how can I touch the package database to make it look like mono is installed so the ./configure script will be happy?

---

### Post by Ocxic on 2010-11-16
mono-complete - complete Mono runtime, development tools and all libraries

"sudo apt-get install mono-complete"

---

### Post by scharkalvin on 2010-11-16
I've tried installing mono-complete, which added a few more packages.  However the application I'm trying to configure still complains that no package named mono is installed.  I guess there used to be a meta package named "mono" now deprecated.  Is there a way to satisfy the autoconfigure script so that installing mono-complete will report a meta package named mono as being installed?  IE can I 'touch' the package database so it thinks that a package suppling 'mono' is installed?

ken@PACALAdev ~/DM355SDK840402 $ make kernel
The system is linuxmint-9 running in a 32 bit architecture
SYSID: linuxmint-9_32
Checking for host packages required by the SDK build system:
    buildsystem (build-essential) is installed
    make (make) is installed
    ncurses (libncurses5-dev) is installed
    texinfo (texinfo) is installed
    minicom (minicom) is installed
    perl (perl) is installed
    quilt (quilt) is installed
    dc (dc) is installed
    quilt (quilt) is installed
    libusb (libusb-dev) is installed
    perl-expect (libexpect-perl) is installed
 >> mono (mono) is NOT installed
There are missing packages, please install them:
 apt-get install mono
make: *** [.oscheck] Error 1
ken@PACALAdev ~/DM355SDK840402 $

---

