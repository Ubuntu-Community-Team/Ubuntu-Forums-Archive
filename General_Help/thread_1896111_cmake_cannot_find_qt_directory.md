---
title: "cmake cannot find qt directory"
date: 2011-12-16
forum: General Help
---

### Post by y10linux on 2011-12-16
Hi,

I am trying to get some old libraries made by a work mate.

These libraries need qt3, so I have instaled it using synaptic (I am in ubuntu 10.10 64 bit).

When I try to run cmake i get the following error:

> CMake Warning at CMakeLists.txt:25 (FIND_PACKAGE):
Could not find module FindQT.cmake or a configuration file for package QT.

   Adjust CMAKE_MODULE_PATH to find FindQT.cmake or set QT_DIR to the
   directory containing a CMake configuration file for QT.  The file will have
   one of the following names:

     QTConfig.cmake
     qt-config.cmake
I have been looking for the mentioned configuration files but cannot seem to locate them , anyone now where they should be?

Thanks

---

### Post by maverickaddicted on 2011-12-16
Check this guide for setting the path and proper installation of QT.

[http://doc.trolltech.com/4.5/qt-embedded-install.html](http://doc.trolltech.com/4.5/qt-embedded-install.html)

---

