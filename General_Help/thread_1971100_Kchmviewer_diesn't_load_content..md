---
title: "Kchmviewer diesn't load content."
date: 2012-05-02
forum: General Help
---

### Post by praveenthivari on 2012-05-02
I am trying to use kchmviewer to read chm files but the app opens certain files but refuses to open certain other filesa. 

For Eg: 
screenshot attached.

Problem is Kubuntu has version 5.3 where as new version is 6, which I hape may fix the problem.
I didn't find any deb files for latest version. The developer of that app has prepared only rpm files. I tried to convert it to deb using alien but the app doesn't run after installation.(Some libchm.so file missing).

My request is if anyone would build it for me from source so that I could use that.

Thanks in advance :-)

---

### Post by praveenthivari on 2012-05-02
Can someone please create a deb file from source? My knowledge about building from source is very poor so ........

---

### Post by praveenthivari on 2012-05-02
I tried to build it after following instruction from:
[http://www.ulduzsoft.com/kchmviewer/getting-kchmviewer/](http://www.ulduzsoft.com/kchmviewer/getting-kchmviewer/)

According to that article i tried to find required packages; I was able to install gcc, g++, make,cmake,libchm-dev, but I couldn't find 'qt4-devel' and kde4-workspace-devel. But I proceeded to create the binary and this was the output I got:


> 
ram@ram-pc:~$ cd Downloads/kchmviewer-6.0
ram@ram-pc:~/Downloads/kchmviewer-6.0$ mkdir build; cd build && cmake .. && make
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
CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/ram/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:9 (FIND_PACKAGE)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
ram@ram-pc:~/Downloads/kchmviewer-6.0/build$ cd /home/ram/


Any suggestions???

---

### Post by praveenthivari on 2012-05-02
Update: I could install kde-workspace-dev and reran the command and got the deb file.

Marked the thread as 'Solved'.

---

