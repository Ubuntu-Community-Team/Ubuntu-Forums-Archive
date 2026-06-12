---
title: "Problems installing k9copy2.3.7-Source with Cmake"
date: 2011-08-06
forum: General Help
---

### Post by luangwa on 2011-08-06
I installed cmake, cmake-qt-qui, cmake-data, cmake-curses-gui using the Synaptic Package manager and tried installing k9copy2.3.7-Source using the cmake gui but I get the following error:

[COLOR="Red"]CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/john/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:9 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION "2.8")
  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

Configuring incomplete, errors occurred![/COLOR]

How can I install in the directories /home/john/.kde/share/apps;/usr/share/kde4/apps? 

The rest of the error has left me lost. HELP :confused:

---

### Post by mihalybaci on 2011-08-06
do you have all the dependencies installed? also, do you already have the older k9copy that comes in the repositories?

[http://k9copy.sourceforge.net/web/index.php/en/](http://k9copy.sourceforge.net/web/index.php/en/)  prereqs at the bottom.

---

### Post by mc4man on 2011-08-06
Open the CMakeLists.txt in your source folder and add the line in blue as shown below (if your cmake version is lower than adjust, should be ok

```
project(k9copy)
[COLOR="Blue"]cmake_minimum_required(VERSION 2.8)[/COLOR]
....clipped

```

---

