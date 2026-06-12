---
title: "when i install Install Compiz 0.8.x Experimental plugins i get an error"
date: 2012-07-12
forum: General Help
---

### Post by louie123 on 2012-07-12
it says 
E: Unable to locate package compiz-plugins-extra
but i have compiz -fusion -plugins extra install when i install Compiz 0.8.x Experimental plugins i get this error Installing all plugins without prompting.
Installing dependencies..
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package compiz-plugins-extra
Cloning into 'anaglyph'...
remote: Counting objects: 134, done.
remote: Compressing objects: 100% (129/129), done.
remote: Total 134 (delta 62), reused 0 (delta 0)
Receiving objects: 100% (134/134), 30.37 KiB, done.
Resolving deltas: 100% (62/62), done.
Building anaglyph..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at CMakeLists.txt:1 (find_package):
  Could not find module FindCompiz.cmake or a configuration file for package
  Compiz.

  Adjust CMAKE_MODULE_PATH to find FindCompiz.cmake or set Compiz_DIR to the
  directory containing a CMake configuration file for Compiz.  The file will
  have one of the following names:

    CompizConfig.cmake
    compiz-config.cmake



CMake Error at CMakeLists.txt:3 (include):
  include could not find load file:

    CompizPlugin


CMake Error at CMakeLists.txt:5 (compiz_plugin):
  Unknown CMake command "compiz_plugin".


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
make: *** No targets specified and no makefile found.  Stop.
Installing..
make: *** No rule to make target `install'.  Stop.
Cloning into 'animationjc'...
remote: Counting objects: 85, done.
remote: Compressing objects: 100% (78/78), done.
remote: Total 85 (delta 46), reused 0 (delta 0)
Receiving objects: 100% (85/85), 16.92 KiB | 6 KiB/s, done.
Resolving deltas: 100% (46/46), done.
Building animationjc..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at CMakeLists.txt:1 (find_package):
  Could not find module FindCompiz.cmake or a configuration file for package
  Compiz.

  Adjust CMAKE_MODULE_PATH to find FindCompiz.cmake or set Compiz_DIR to the
  directory containing a CMake configuration file for Compiz.  The file will
  have one of the following names:

    CompizConfig.cmake
    compiz-config.cmake



CMake Error at CMakeLists.txt:2 (include):
  include could not find load file:

    CompizPlugin


-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/libX11.so
CMake Error at CMakeLists.txt:6 (compiz_plugin):
  Unknown CMake command "compiz_plugin".


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
make: *** No targets specified and no makefile found.  Stop.
Installing..
make: *** No rule to make target `install'.  Stop.
Cloning into 'atlantis'...
remote: Counting objects: 966, done.
remote: Compressing objects: 100% (961/961), done.
remote: Total 966 (delta 655), reused 0 (delta 0)
Receiving objects: 100% (966/966), 2.98 MiB | 78 KiB/s, done.
Resolving deltas: 100% (655/655), done.
Building atlantis..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at CMakeLists.txt:1 (find_package):
  Could not find module FindCompiz.cmake or a configuration file for package
  Compiz.

  Adjust CMAKE_MODULE_PATH to find FindCompiz.cmake or set Compiz_DIR to the
  directory containing a CMake configuration file for Compiz.  The file will
  have one of the following names:

    CompizConfig.cmake
    compiz-config.cmake



CMake Error at CMakeLists.txt:3 (include):
  include could not find load file:

    CompizPlugin


CMake Error at CMakeLists.txt:5 (compiz_plugin):
  Unknown CMake command "compiz_plugin".


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
make: *** No targets specified and no makefile found.  Stop.
Installing..
make: *** No rule to make target `install'.  Stop.
Cloning into 'cubemodel'...
remote: Counting objects: 321, done.
remote: Compressing objects: 100% (319/319), done.
remote: Total 321 (delta 209), reused 0 (delta 0)
Receiving objects: 100% (321/321), 154.31 KiB | 23 KiB/s, done.
Resolving deltas: 100% (209/209), done.
Building cubemodel..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at CMakeLists.txt:1 (find_package):
  Could not find module FindCompiz.cmake or a configuration file for package
  Compiz.

  Adjust CMAKE_MODULE_PATH to find FindCompiz.cmake or set Compiz_DIR to the
  directory containing a CMake configuration file for Compiz.  The file will
  have one of the following names:

    CompizConfig.cmake
    compiz-config.cmake



CMake Error at CMakeLists.txt:3 (include):
  include could not find load file:

    CompizPlugin


CMake Error at CMakeLists.txt:5 (compiz_plugin):
  Unknown CMake command "compiz_plugin".


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
make: *** No targets specified and no makefile found.  Stop.
Installing..
make: *** No rule to make target `install'.  Stop.
Cloning into 'dialog'...
remote: Counting objects: 85, done.
remote: Compressing objects: 100% (80/80), done.
remote: Total 85 (delta 34), reused 0 (delta 0)
Receiving objects: 100% (85/85), 17.58 KiB | 4 KiB/s, done.
Resolving deltas: 100% (34/34), done.
Building dialog..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at CMakeLists.txt:1 (find_package):
  Could not find module FindCompiz.cmake or a configuration file for package
  Compiz.

  Adjust CMAKE_MODULE_PATH to find FindCompiz.cmake or set Compiz_DIR to the
  directory containing a CMake configuration file for Compiz.  The file will
  have one of the following names:

    CompizConfig.cmake
    compiz-config.cmake



CMake Error at CMakeLists.txt:3 (include):
  include could not find load file:

    CompizPlugin


CMake Error at CMakeLists.txt:5 (compiz_plugin):
  Unknown CMake command "compiz_plugin".


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
make: *** No targets specified and no makefile found.  Stop.
Installing..
make: *** No rule to make target `install'.  Stop.
Cloning into 'extra-animations'...
remote: Counting objects: 1468, done.
remote: Compressing objects: 100% (1463/1463), done.
Receiving objects:  14% (206/1468), 28.00 KiB | 5 KiB/s

---

