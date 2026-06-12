---
title: "Problem including OpenCV lib"
date: 2011-07-07
forum: General Help
---

### Post by lakshmen on 2011-07-07
The problem i have now is that I have opencv include file in my code. I need to link the opencv libraries but can't seem to able to do it.

I was told to include these in my CMakeLists.txt.

find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIR})
target_link_libraries(example1 ${OpenCV_LIBS})

After including those lines,

I have this error.

Adjust CMAKE_MODULE_PATH to find FindOpenCV.cmake or set OpenCV_DIR to the
   directory containing a CMake configuration file for OpenCV.  The file will
   have one of the following names:
 
     OpenCVConfig.cmake
     opencv-config.cmake

I am using Apple.

what shld i do next?

---

