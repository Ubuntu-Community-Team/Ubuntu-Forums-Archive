---
title: "cmake problems"
date: 2012-07-19
forum: General Help
---

### Post by Dorganec on 2012-07-19
Hi There!
 
I'm very new to Ubuntu and Linux and I need to use this program for a research project that involves Skybotix CoaX robots. When I'm in the "reu2012@reu2012-VirtualBox:/media/sf_Linux_Share/CoaX_Repository_Backup_07132012/PC/simulation_ode/build$" directory and type in "cmake .." I get this message:
CMake Warning (dev) at CMakeLists.txt:51 (ADD_DEFINITIONS):
Policy CMP0005 is not set: Preprocessor definition values are now escaped
automatically. Run "cmake --help-policy CMP0005" for policy details. Use
the cmake_policy command to set the policy and suppress this warning.
This warning is for project developers. Use -Wno-dev to suppress it.
 
-- Configuring done
CMake Warning (dev) at CMakeLists.txt:74 (ADD_EXECUTABLE):
Policy CMP0003 should be set before this line. Add code such as
 
if(COMMAND cmake_policy)
cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)
 
as early as possible but after the most recent call to
cmake_minimum_required or cmake_policy(VERSION). This warning appears
because target "coaxSim" links to some libraries for which the linker must
search:
 
sbcom, pthread, rt, ode, SM, ICE, GL, GLU, jpeg, X11, m
 
and other libraries with known full path:
 
/media/sf_Linux_Share/CoaX_Repository_Backup_07132012/PC/simulation_ode/build/libdrawstuff.a
 
CMake is adding directories in the second list to the linker search path in
case they are needed to find libraries from the first list (for backwards
compatibility with CMake 2.4). Set policy CMP0003 to OLD or NEW to enable
or disable this behavior explicitly. Run "cmake --help-policy CMP0003" for
more information.
This warning is for project developers. Use -Wno-dev to suppress it.
 
-- Generating done
-- Build files have been written to: /media/sf_Linux_Share/CoaX_Repository_Backup_07132012/PC/simulation_ode/build
 
What does this mean and how do I fix it? I'm using an Oracle VirtualBox with a Windows OS as the host. The program that I am working on the VirtualBox is Ubuntu 11.1 and the cmake version that I am using is cmake 2.8.5 if that is any help. Please help me. I would greatly appreciate the help. Thank you and have a good day.

---

