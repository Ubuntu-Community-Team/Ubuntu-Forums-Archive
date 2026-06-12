---
title: "Installing OpenCV 2.4 python support make error"
date: 2012-05-09
forum: General Help
---

### Post by XxNocturnxX on 2012-05-09
Hi! I'm trying to install opencv 2.4 with python support. At first I forgot to install numpy but I search for it and everything came clear.

Now I just installed numpy but when I tried to run make in opencv again, it gave me this errors. I'm tired of searching with no success, so please I'll appreciate your help.

[ 95%] Building CXX object modules/python/CMakeFiles/opencv_python.dir/src2/cv2.cpp.o
In file included from /home/nock/Documents/OpenCV-2.4.0/modules/python/src2/cv2.cv.hpp:3842:0,
                 from /home/nock/Documents/OpenCV-2.4.0/modules/python/src2/cv2.cpp:993:
/home/nock/Documents/OpenCV-2.4.0/release/modules/python/generated0.i: In function ‘PyObject* pycvDrawChessboardCorners(PyObject*, PyObject*)’:
/home/nock/Documents/OpenCV-2.4.0/release/modules/python/generated0.i:2387:1: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/nock/Documents/OpenCV-2.4.0/modules/python/src2/cv2.cv.hpp:3842:0,
                 from /home/nock/Documents/OpenCV-2.4.0/modules/python/src2/cv2.cpp:993:
/home/nock/Documents/OpenCV-2.4.0/release/modules/python/generated0.i: In function ‘PyObject* pycvSnakeImage(PyObject*, PyObject*, PyObject*)’:
/home/nock/Documents/OpenCV-2.4.0/release/modules/python/generated0.i:6440:3: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
Linking CXX shared library ../../lib/cv2.so
/usr/bin/ld: /usr/local/lib/libpython2.7.a(abstract.o): relocation R_X86_64_32S against `_Py_NotImplementedStruct' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libpython2.7.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [lib/cv2.so] Error 1
make[1]: *** [modules/python/CMakeFiles/opencv_python.dir/all] Error 2
make: *** [all] Error 2

I'm using ubuntu 11.10 64 bits and python 2.7,

Cheers,

Nock

---

