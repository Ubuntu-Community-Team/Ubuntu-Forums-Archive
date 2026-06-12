---
title: "Problems with CMake and implicit directories"
date: 2009-11-11
forum: General Help
---

### Post by Aslund on 2009-11-11
Hey everyone

I am pretty new with CMake, but need to use it due to a course at my university. 
I use cmake to create a CodeBlocks project, but while it compile I get the following error: 

--------------------------------------------------------------------------
CMake Warning at plugin/CMakeLists.txt:15 (ADD_LIBRARY):
  Cannot generate a safe linker search path for target Rob01Ex1 because files
  in some directories may conflict with libraries in implicit directories:

    link library [libyaobi.so] in /usr/lib may be hidden by files in:
      /home/aslund/Desktop/workspace/RobWork/build/../libs/Release

  Some of these libraries may not be found correctly.
--------------------------------------------------------------------------

How can I create a safe link to a library? 


Regards

Sebastian

---

