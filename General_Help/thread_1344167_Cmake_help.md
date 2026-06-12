---
title: "Cmake help"
date: 2009-12-02
forum: General Help
---

### Post by puzzler995 on 2009-12-02
I have Ubuntu 9.10 and I'm trying to install Usbmuxd (which you can only get in a tarball) so I can get my internet up and running (off my iPod Touch since my wi-fi stick doesn't work on it). I got the .deb file for Cmake off the Ubuntu website, and installed it. The first time I ran Cmake, there was a problem about the C++ Compiler, but I got G++ and fixed it. Then I ran it and there was this error... 
```
checking for module 'libusb-1.0>=1.0.3'
  package 'libusb-1.0>=1.0.3' not found
USB_INCLUDE_DIR=USB_INCLUDE_DIR-NOTFOUND
USB_LIBRARY=USB_LIBRARY-NOTFOUND
CMake Error at Modules/LibFindMacros.cmake:74 (message):
  Required library USB NOT FOUND.

  Install the library (dev version) and try again.  If the library is already
  installed, use ccmake to set the missing variables manually.
Call Stack (most recent call first):
  Modules/FindUSB.cmake:31 (libfind_process)
  daemon/CMakeLists.txt:1 (find_package)


Configuring incomplete, errors occurred!
```

I have Libusb installed!!! Please help me!!!

---

### Post by lloyd_b on 2009-12-02
You may have the library itself installed, but do you have the development package ("libusb-dev") installed as well?  This is probably what it's looking for.

Also - if you haven't already done so, install the package "build-essential" just to make sure you have a complete build system.

Lloyd B.

---

### Post by puzzler995 on 2009-12-11
I figured it out, but now it wont make the file.UGH! ](*,)

---

