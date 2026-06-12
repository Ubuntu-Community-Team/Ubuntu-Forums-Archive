---
title: "GCC Problems"
date: 2012-05-01
forum: General Help
---

### Post by jrdavis on 2012-05-01
Hey, I don't actually use Ubuntu; I use Pardus.  It's another very complete distro, but there isn't much of an online community for it, so I came here.  I'm having trouble compiling my first C++ program (helloworld).  Can somebody help me?  It says "no such file or directory," but there clearly is.  Below, I've copied and pasted all relevant information from the terminal:

jacob@D830 Documents $ ls
HelloWorld.cpp  MATLAB  ME 203 Project.docx  Te&#351;kilat-&#305; Esasiye Kanunu.odt

jacob@D830 Documents $ g++ -o HelloWorld HelloWorld.cpp
In file included from /usr/include/c++/i686-pc-linux-gnu/bits/c++config.h:275:0,
                 from /usr/include/c++/iostream:39,
                 from HelloWorld.cpp:1:
/usr/include/c++/i686-pc-linux-gnu/bits/os_defines.h:39:22: fatal error: features.h: No such file or directory
compilation terminated.

jacob@D830 Documents $

---

### Post by steeldriver on 2012-05-01
> **jrdavis said:**
> It says "no such file or directory," but there clearly is.

it's complaining about a missing header file called 'features.h', *not* about anything in your current directory - it should be located somewhere like /usr/include

my guess is you only installed the bare gcc compiler package - you probably need to install the build-essential package to get the C libraries and headers, then try again

---

