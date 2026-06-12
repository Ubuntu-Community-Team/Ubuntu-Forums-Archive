---
title: "Please help with cmake installation"
date: 2010-04-20
forum: General Help
---

### Post by JCBARCA on 2010-04-20
Hi. 

I am new to Ubuntu and I need to install a robot simulator on a Linux based system. However the simulator requires that I install cmake. I have tried to do this for several hours by running the ./bootstrap command and installing several other required programs (including a c++ comiler and GCC), but nothing seems to work....:confused:

cmake gives me the following error message:

CMake 2.8.1, Copyright 2000-2009 Kitware, Inc.
C compiler on this system is: cc 
---------------------------------------------
Error when bootstrapping CMake:
Cannot find appropriate C++ compiler on this system.
Please specify one using environment variable CXX.
See cmake_bootstrap.log for compilers attempted.
---------------------------------------------
Log of errors: /home/carlo/Documents/cmake-2.8.1/Bootstrap.cmk/cmake_bootstrap.log

Can someone please assist me with getting cmake to work..

Jan Carlo

---

### Post by klemes on 2010-04-20
I think in a few words it wants to know the path to your C++ compiler,and for doing this you must set the environment variable CXX to the path of the executable of your C++ compiler.That's it what I gather from the above message although I don't know why this variable is not set automatically since you said you have installed a C++ compiler.Maybe it is installed in a non-standard path....or in a path other than that cmake expects to find it.

---

### Post by JCBARCA on 2010-04-20
I have tried to install a c++ compiler, but it does not seem to work.. I am sorry but I am really new to Linux. Which C++ compiler do you suggest that I install, and how do I set the CXX enviroment variable to the correct path when I have installed the compiler....

---

### Post by klemes on 2010-04-20
I would open up Synaptic and put in the search tab C++ compiler.The one that turns up in my system is g++ compiler,the GNU C++ compiler.Not exactly sure what version it will be in your system that's why I don't write the full name+version tag ,which you must specify in order to install it with aptitude or apt-get install.But if you use Synaptic you will be able to see all available versions for your system and choose which you want to install.I think this will take care of setting the correct path by itself and you will have no more worries.

---

### Post by JCBARCA on 2010-04-20
Thank you very much for your suggestion. I will test Synaptic :)

Have a nice day

---

### Post by klemes on 2010-04-20
You too!!!

---

