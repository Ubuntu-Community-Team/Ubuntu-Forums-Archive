---
title: "Compiling VBA-M"
date: 2010-04-28
forum: General Help
---

### Post by digg on 2010-04-28
I'm trying to compile VBA-M, using the recommended ccmake.

svn co [https://vbam.svn.sourceforge.net/svnroot/vbam](https://vbam.svn.sourceforge.net/svnroot/vbam) vbam 

However, I get this error:
```

 CMake Error at
 /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:70 (MESSAGE):
   Could NOT find SFML (missing: SFML_LIBRARY SFML_INCLUDE_DIR)
 Call Stack (most recent call first):
   CMakeScripts/FindSFML.cmake:78 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
   CMakeLists.txt:44 (FIND_PACKAGE)

```

I've installed SFML-dev and the SFML libraries using aptitude. But it doesn't seem to help. I'm now using the modified [FindSFML.cmake at the bottom of this thread]("http://www.sfml-dev.org/forum/viewtopic.php?p=15578&sid=83b0c5734a8df1023012f7cf737b4eed").

Please help!

---

### Post by gmargo on 2010-04-29
I tried it, running "cmake ." at the vbam/trunk level.  Installing the **libsfml-dev** package satisfied the SFML dependency for me.  Tested on 9.10 Karmic.

---

### Post by digg on 2010-04-29
It works, thanks. Also had to get libsdl-dev.

Anyone using VBA-M with a GUI? I thought that was one of it's advantages over vba...

---

