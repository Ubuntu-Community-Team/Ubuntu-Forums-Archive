---
title: "Autopano-Sift-C / Could not find REQUIRED package TIFF while building from source"
date: 2010-07-27
forum: General Help
---

### Post by Naggobot on 2010-07-27
OS Version: Ubuntu / Karmic / 9.10
While building the Autopano-Sift-C according to instructions from

[http://wiki.panotools.org/Hugin_Compiling_Ubuntu](http://wiki.panotools.org/Hugin_Compiling_Ubuntu)

I received following error

```

CMake Error at CMakeModules/FindPackageHandleStandardArgs.cmake:51 (MESSAGE):
  Could not find REQUIRED package TIFF
Call Stack (most recent call first):
  CMakeModules/FindTIFF.cmake:38 (find_package_handle_standard_args)
  CMakeLists.txt:48 (FIND_PACKAGE)

```Evidently this is solved in the [Italian forum]("http://forum.ubuntu-it.org/index.php?topic=326860.msg2514325"). I do not speak/read IT but from thread I deciphered that installing libtiff4-dev solves this particular problem. 

Unfortunatelly Cmake still gives another error. I'll make separate thread of that if necessary.

Edit: Autopano-Sift-C version 2.5.1

---

