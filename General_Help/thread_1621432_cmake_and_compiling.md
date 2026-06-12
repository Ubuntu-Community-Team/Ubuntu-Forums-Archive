---
title: "cmake and compiling"
date: 2010-11-14
forum: General Help
---

### Post by 0xParse on 2010-11-14
I am trying to compile a project/program.  It is very new and the cmake files are not correctly formatted from what I understand.  I was told to use cmake-gui to fix it.  I have it downloaded and when I input the correct data into source and build, then click Configure here is what I get.

CMAKE_BUILD_TYPE          (there is nothing here, its blank)
CMAKE_INSTALL_PREFIX      /usr/local
PTHREAD                   /usr/lib/libpthread.so

I got an older version of this to compile and run fine.  After I 
Generate the build and make the project I get this error:
> Scanning dependencies of target freenect
[ 25%] Building C object lib/CMakeFiles/freenect.dir/cameras.c.o
/home/frankie/Documents/Kinect/Majorityy-openkinect-1f537d4/c/lib/cameras.c:4: fatal error: usb.h: No such file or directory
compilation terminated.
make[2]: *** [lib/CMakeFiles/freenect.dir/cameras.c.o] Error 1
make[1]: *** [lib/CMakeFiles/freenect.dir/all] Error 2
make: *** [all] Error 2



Here is the git page for the project i am trying to download.  You won't be able to run the compiled file without other hardware (kinect), but it will still compile without it.
github . com/Majorityy/openkinect/tree/win32  (remove spaces, not sure why it won't let my type it)

Note: Others have been able to compile this, but have not replied on IRC.

---

### Post by 0xParse on 2010-11-14
bump
anyone?

Edit: I was using the wrong version of the program.  So I guess that means its solved.

---

