---
title: "Trying to install &quot;CMake&quot; but getting an error"
date: 2011-09-06
forum: General Help
---

### Post by aria john on 2011-09-06
I am trying to install "CMake"
I downloaded the source file "                           [COLOR=Black][cmake-2.8.5.tar.gz]("http://www.cmake.org/files/v2.8/cmake-2.8.5.tar.gz")[/COLOR] " but after I wrote the commands:
#
./bootstrap
                        make      
                 make install

it was fine until I reached the last command "make install" where I got an Error:

#
aria@aria-laptop:~/Documents/cmake-2.8.5$ make install
[  5%] Built target cmsys
[  5%] Built target cmsysTestDynload
[  6%] Built target cmsys_c
[  6%] Built target cmsysTestProcess
[  7%] Built target cmsysTestSharedForward
[  7%] Built target cmsysTestsC
[ 11%] Built target cmsysTestsCxx
[ 15%] Built target cmzlib
[ 33%] Built target cmcurl
[ 34%] Built target LIBCURL
[ 34%] Built target cmcompress
[ 36%] Built target cmbzip2
[ 54%] Built target cmlibarchive
[ 55%] Built target cmexpat
[ 81%] Built target CMakeLib
[ 85%] Built target CPackLib
[ 97%] Built target CTestLib
[ 97%] Built target cmake
[ 97%] Built target cpack
[ 97%] Built target ctest
[ 98%] Built target documentation
[ 99%] Built target CMakeLibTests
[100%] Built target runcompilecommands
Install the project...
-- Install configuration: ""
CMake Error at cmake_install.cmake:36 (FILE):
  file cannot create directory: /usr/local/doc/cmake-2.8.  Maybe need
  administrative privileges.


make: *** [install] Error 1
----------

Any suggestions ?

---

### Post by aria john on 2011-09-06
I installed it from the package manager
it worked

---

