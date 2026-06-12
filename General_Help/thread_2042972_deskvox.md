---
title: "deskvox"
date: 2012-08-15
forum: General Help
---

### Post by demonskier on 2012-08-15
Hey guys, I'm trying to build a piece of software called deskvox ([http://ivl.calit2.net/wiki/index.php/VOX_and_Virvo](http://ivl.calit2.net/wiki/index.php/VOX_and_Virvo)) I pulled everything from their subversion server, installed the dependencies with apt-get (and synaptic) ran cmake (using the gui) and am now trying to build this piece of software but for the life of me can't seem to get it to build.  Has anybody gotten this to build before or have the time to give it a shot?


In case it matters I'm using Xubuntu

---

### Post by ubudog on 2012-08-15
Could you post any errors from compiling here?

Best,
ubudog

---

### Post by demonskier on 2012-08-16
Sorry for the delay company had an emergency I will likely get my errors up tomorrow, thanks for looking at this

---

### Post by demonskier on 2012-08-17
demonskier@demonskier:~/deskvox/build$ cmake -P cmake_install.cmake
-- Install configuration: ""
CMake Error at virvo/shader/cmake_install.cmake:36 (FILE):
  file INSTALL cannot find
  "/home/demonskier/deskvox/trunk/virvo/shader/vv_passthrough_frag_shader.cg".
Call Stack (most recent call first):
  virvo/cmake_install.cmake:37 (INCLUDE)
  cmake_install.cmake:37 (INCLUDE)



I have also tried using make with the makefiles that cmake created but that seems like an even bigger rabbit hole to chase down

---

### Post by demonskier on 2012-08-17
This is one of the errors when using make(and it seems to be along the same lines as many of the other ones I've seen when trying to build different parts of the application one at a time)

In file included from /home/demonskier/deskvox/trunk/virvo/virvo/vvmulticast.cpp:35:0:
/home/demonskier/deskvox/trunk/norm-1.4b2/common/normApi.h:51:23: error: conflicting declaration ‘typedef long unsigned int NormNodeId’
/home/demonskier/deskvox/trunk/virvo/virvo/vvmulticast.h:34:21: error: ‘NormNodeId’ has a previous declaration as ‘typedef uint32_t NormNodeId’
/home/demonskier/deskvox/trunk/norm-1.4b2/common/normApi.h:494:69: warning: type qualifiers ignored on function return type [-Wignored-qualifiers]
make[2]: *** [virvo/virvo/CMakeFiles/virvo.dir/vvmulticast.cpp.o] Error 1
make[1]: *** [virvo/virvo/CMakeFiles/virvo.dir/all] Error 2

---

### Post by szellmann on 2012-09-20
Hi demonskier,
I'm one of the DeskVOX devs. I wonder if you were able to install DeskVOX after all. DeskVOX is subject to quite some change these days. We moved from subversion to git on sourceforge and we also have a new build system. Maybe it is a better idea to obtain DeskVOX from here:

git://deskvox.git.sourceforge.net/gitroot/deskvox/deskvox

All the new changes are committed to the git repo. The Subversion repo is obsolete and we only keep it so far because a proprietary visualization software at our institute strongly relies on it. We will completely move from svn to git soon.

The error messages you posted are due to bugs that are fixed on the git repo. We test our code on Windows, Mac OS X Mountain Lion, Ubuntu 10.04 and Ubuntu 12.04. Please contact me if you require further assistance!

Kind Regards!

---

