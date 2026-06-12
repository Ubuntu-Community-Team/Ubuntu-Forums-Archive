---
title: "[Problem] Error while loading shared libraries"
date: 2010-05-31
forum: General Help
---

### Post by choikwa on 2010-05-31
I'm using code::blocks on 10.04, using opencv2.1 library

I get an error while trying to load my compiled program. It compiles without errors, but when it tries to execute the program, I get the error below:

/media/FE4653354652EDC1/Workspace/jpgFaceTracker/jpgFaceTracker: error while loading shared libraries: libcv.so.2.1: cannot open shared object file: No such file or directory

It seems that the problem is linux library path doesn't know where to locate the opencv library.
I followed these commands to install opencv on my computer
   1. tar -xjf OpenCV-2.1.0.tar.bz2 
   2. mkdir opencv.build 
   3. cd opencv.build 
   4. cmake [<extra_options>] ../OpenCV-2.1.0 # CMake-way 
   5. make -j 2 
   6. sudo make install 
   7. sudo ldconfig # linux only

I think 7th step sets library path, but I wasn't completely sure so I tried doing this as well but to no avail

**export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib**
or... 
**export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<dir to opencv lib>**

both don't seem to work. 

I also tried writing to "etc/ld.so.conf.d" a custom file "opencv.conf" with entry being opencv library directory, but it says permission denied.


Please help me, I'm stuck as I don't know what else to do.
Any help would be greatly appreciated.

---

### Post by choikwa on 2010-06-04
bump

---

### Post by tuxmanic on 2010-07-18
Could you please upload that opencv programme  which causes error ?

---

