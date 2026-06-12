---
title: "Problem compiling OpenSceneGraph for FlightGear"
date: 2011-03-19
forum: General Help
---

### Post by Keith_Beef on 2011-03-19
Hello, all.

I've been trying this for a while, getting nowhere...

I'm following the instructions [here]("http://wiki.flightgear.org/index.php/Manual_Compilation_on_Ubuntu_Linux"), to compile OpenSceneGraph that I got on DVDs purchased from Curtis Olsen.

The instruction for this step goes like this.

> mkdir osg_build
cd osg_build
cmake -D CMAKE_BUILD_TYPE="Release" -D CMAKE_CXX_FLAGS="-O3 -march=native" \
CMAKE_C_FLAGS="-O3 -march=native" -D CMAKE_INSTALL_PREFIX:PATH="/usr" ../src
make -j4
sudo make install
cd ..


So, I try that, and I get the following.
> 
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
CMake Error at OpenThreads/CMakeLists.txt:12 (INCLUDE):
  include could not find load file:

    CheckAtomicOps


-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE
CMake Error: File /usr/local/src/FlightGear_2.0.0/Source/OpenSceneGraph/src/packaging/pkgconfig/openthreads.pc.in does not exist.
CMake Error at OpenThreads/CMakeLists.txt:103 (CONFIGURE_FILE):
  configure_file Problem configuring file


-- Looking for pthread_yield
-- Looking for pthread_yield - found
-- Looking for pthread_setconcurrency
-- Looking for pthread_setconcurrency - found
-- Looking for pthread_getconcurrency
-- Looking for pthread_getconcurrency - found
-- Looking for pthread_setaffinity_np
-- Looking for pthread_setaffinity_np - found
CMake Error at osg/CMakeLists.txt:331 (LINK_INTERNAL):
  Unknown CMake command "LINK_INTERNAL".


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!

So, thinking that it is a problem with the version not being specified,I added cmake_minimum_required(VERSION 2.8) to the beginning of CMakeLists.txt

Tried again.
Still no joy!

> CMake Error at OpenThreads/CMakeLists.txt:12 (INCLUDE):
  include could not find load file:

    CheckAtomicOps


CMake Error: File /usr/local/src/FlightGear_2.0.0/Source/OpenSceneGraph/src/packaging/pkgconfig/openthreads.pc.in does not exist.
CMake Error at OpenThreads/CMakeLists.txt:103 (CONFIGURE_FILE):
  configure_file Problem configuring file


CMake Error at osg/CMakeLists.txt:331 (LINK_INTERNAL):
  Unknown CMake command "LINK_INTERNAL".


-- Configuring incomplete, errors occurred!


Any ideas what I'm doing wrong?

K.

---

### Post by Keith_Beef on 2011-03-27
Bump!

Can anybody shed some light on this problem for me?

---

