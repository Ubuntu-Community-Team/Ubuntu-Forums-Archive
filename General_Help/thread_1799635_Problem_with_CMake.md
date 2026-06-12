---
title: "Problem with CMake"
date: 2011-07-07
forum: General Help
---

### Post by lakshmen on 2011-07-07
i hope someone can help me.  I have a simple CMakeLists.txt in order to build my project on Ubuntu. At the moment this is the code:
  

cmake_minimum_required(VERSION 2.4.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(ROS_BUILD_TYPE RelWithDebInfo)

rosbuild_init()

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

#uncomment if you have defined messages
#rosbuild_genmsg()
#uncomment if you have defined services
#rosbuild_gensrv()


#common commands for building c++ executables and libraries
#rosbuild_add_library(${PROJECT_NAME} src/example.cpp)
#target_link_libraries(${PROJECT_NAME} another_library)
#rosbuild_add_boost_directories()
#rosbuild_link_boost(${PROJECT_NAME} thread)
#rosbuild_add_executable(example examples/example.cpp)
#target_link_libraries(example ${PROJECT_NAME})

include_directories(${CMAKE_SOURCE_DIR}/include
                                  ${OpenCV_INCLUDE_DIRS})

file(GLOB_RECURSE src_files src/*.cpp)

# additional link directories... MUST specify in this order!!
link_directories(${CMAKE_SOURCE_DIR}/lib)

rosbuild_add_executable(RosPub ${src_files})
target_link_libraries(RosPub openni_driver usb-1.0 ${OpenCV_LIBS})
  I need to add opencv libraries on my project. I have added them but i  can't still get my code to work. its keeps posting me this error:
  &#8216;struct MyOpenNIExample::ImgContext&#8217; has no member named &#8216;image&#8217;
  there is a few of them. 
  

after i added find_package(OpenCV REQUIRED to the CMakeLists.txt,  i get this error
  
Adjust CMAKE_MODULE_PATH to find FindOpenCV.cmake or set OpenCV_DIR to the
   directory containing a CMake configuration file for OpenCV.  The file will
   have one of the following names:

     OpenCVConfig.cmake
     opencv-config.cmake
  what shld i do? I am using Apple and using Ubuntu 10.04

---

