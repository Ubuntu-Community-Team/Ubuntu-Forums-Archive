---
title: "Can not build OpenCV 2.0 from source"
date: 2010-03-10
forum: General Help
---

### Post by mamadhadi on 2010-03-10
Hello every one
I want to install OpenCV 2.0 from source.
After using ./configure and running make, this output appears
```
$ make
make  all-recursive
make[1]: Entering directory `/home/student/BSP/OpenCV/OpenCV-2.0.0'
Making all in 3rdparty
make[2]: Entering directory `/home/student/BSP/OpenCV/OpenCV-2.0.0/3rdparty'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/student/BSP/OpenCV/OpenCV-2.0.0/3rdparty'
Making all in src
make[2]: Entering directory `/home/student/BSP/OpenCV/OpenCV-2.0.0/src'
/bin/bash ../libtool --tag=CXX   --mode=link g++ -O3 -g -march=x86-64 -ffast-math -fomit-frame-pointer   -no-undefined -Wc,-fopenmp -version-info 4:0:0   -o libcvaux.la -rpath /usr/local/lib libcvaux_la-cvauxprecomp.lo lib_cvaux.la libcxcore.la libcv.la  -lavformat -lavcodec -lrt -lz -lpthread -ldl -lm 
../libtool: line 6412: cd: Project/OpenCV/OpenCV-2.0.0/src: No such file or directory
libtool: link: warning: cannot determine absolute directory name of `Project/OpenCV/OpenCV-2.0.0/src'
/bin/grep: Project/OpenCV/OpenCV-2.0.0/src/libcxcore.la: No such file or directory
/bin/sed: can't read Project/OpenCV/OpenCV-2.0.0/src/libcxcore.la: No such file or directory
libtool: link: `Project/OpenCV/OpenCV-2.0.0/src/libcxcore.la' is not a valid libtool archive
make[2]: *** [libcvaux.la] Error 1
make[2]: Leaving directory `/home/student/BSP/OpenCV/OpenCV-2.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/student/BSP/OpenCV/OpenCV-2.0.0'
make: *** [all] Error 2

```I have download the source files from SourceForge.net.
And I'm running Ubuntu 9.10 64 bit version.

Friends, what should I do?
Thanks in advance

---

