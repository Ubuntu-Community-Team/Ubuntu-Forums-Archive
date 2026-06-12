---
title: "Doomsday 1.9 beta6.8 Cruses missing"
date: 2009-12-30
forum: General Help
---

### Post by obsrv on 2009-12-30
Hello,
I am trying to compile **Doomsday 1.9 beta6.8** and when I run cmake, I get this error about missing Curses:

```
obsrv@pirate:~/Downloads/deng-1.9.0-beta6.8/doomsday/builddir$ cmake ..
CMake Error at /usr/share/cmake-2.6/Modules/FindPackageHandleStandardArgs.cmake:57 (MESSAGE):
  Could NOT find Curses (missing: CURSES_LIBRARY CURSES_INCLUDE_PATH)
Call Stack (most recent call first):
  /usr/share/cmake-2.6/Modules/FindCurses.cmake:137 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:244 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!
obsrv@pirate:~/Downloads/deng-1.9.0-beta6.8/doomsday/builddir$


```

I have all ncurses packages installed:

```
obsrv@pirate:~/Downloads/deng-1.9.0-beta6.8/doomsday/builddir$ sudo apt-get install ncurses-base ncurses-bin ncurses-runtime ncurses-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
ncurses-base is already the newest version.
ncurses-bin is already the newest version.
Note, selecting ncurses-base instead of ncurses-runtime
ncurses-base is already the newest version.
Note, selecting libncurses5-dev instead of ncurses-dev
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
obsrv@pirate:~/Downloads/deng-1.9.0-beta6.8/doomsday/builddir$

```

What package am I missing?

Thank you.

---

### Post by J V on 2009-12-30
You need curses to run doomsday, consult your local witch for more information...

---

### Post by obsrv on 2009-12-30
HA HA J V HA HA very funny :D

---

### Post by obsrv on 2010-01-01
bump bump

---

### Post by KuriKai on 2010-02-03
You are able to install the doomsday engine from the ubuntu repos found on [http://dengine.net](http://dengine.net)

---

