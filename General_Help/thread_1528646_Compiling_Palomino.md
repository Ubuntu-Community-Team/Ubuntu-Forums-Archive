---
title: "Compiling Palomino"
date: 2010-07-11
forum: General Help
---

### Post by vamc on 2010-07-11
Hi, I just tried to compile the source code of Palomino flight simulator. Here is the error message:
```
vamc@LINUX-MACHINE:~/Desktop/palomino$ cmake .
CMake Error at CMakeModules/FindOpenThreads.cmake:49 (MESSAGE):
  Could not find OpenThreads
Call Stack (most recent call first):
  CMakeModules/libraries.cmake:68 (FIND_PACKAGE)
  CMakeLists.txt:30 (COMPILE_WITH_OPENSCENEGRAPH)


-- Configuring incomplete, errors occurred!
```

Openscenegraph is installed and so is cmake. I could not figure out what the problem is. Help me.

Thanks in advance.

---

### Post by walidzohair on 2011-05-15
same error here .. my vote too .. any help ?

---

### Post by gmargo on 2011-05-15
I built this on 10.10 Maverick.
Make sure you have all of the following packages installed:
```

libopenscenegraph-dev
lua5.1
liblua5.1-0-dev
libsdl1.2-dev
libsdl-mixer1.2-dev
libfltk1.1-dev
zlib1g-dev

```

---

