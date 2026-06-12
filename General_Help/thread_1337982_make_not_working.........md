---
title: "make not working........"
date: 2009-11-26
forum: General Help
---

### Post by happy_win on 2009-11-26
cmake worked fine bt when I do make it shows following error:

> happywin@happywin-laptop:/usr/share/vtk/Medical/Cxx$ sudo cmake .
-- Loading VTK CMake commands
-- Loading VTK CMake commands - done
CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring done
-- Generating done
-- Build files have been written to: /usr/share/vtk/Medical/Cxx
happywin@happywin-laptop:/usr/share/vtk/Medical/Cxx$ make
make[2]: *** No rule to make target `/usr/lib/libtiff.so', needed by `Medical1'.  Stop.
make[1]: *** [CMakeFiles/Medical1.dir/all] Error 2
make: *** [all] Error 2
plz help!!!

---

### Post by diesch on 2009-11-26
install *libtiff4-dev*

---

