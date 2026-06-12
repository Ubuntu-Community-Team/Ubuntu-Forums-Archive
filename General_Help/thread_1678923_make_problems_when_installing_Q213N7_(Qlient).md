---
title: "make problems when installing Q213N7 (Qlient)"
date: 2011-01-31
forum: General Help
---

### Post by mikul on 2011-01-31
Hi.
I'm trying to install Q213N7 (Qlient) witch is a quake3 client based on ioquake with some extra features from dfengine.

The problem is now when i'm trying to install it.
Can't get it to work. I think it has something to do with curl, but i'v installd curl and tried to install curl libs but cant find a soultion. 

this is the what happens:
```
mikul@anus:~/qlone-trunk$ make 
make[1]: Entering directory `/home/mikul/qlone-trunk'

Building Qlone in build/release-linux-i386:
  PLATFORM: linux
  ARCH: i386
  VERSION: beta-115
  COMPILE_PLATFORM: linux
  COMPILE_ARCH: i386
  CC: cc

  CFLAGS:
    -MMD
    -Wall
    -fno-strict-aliasing
    -Wimplicit
    -Wstrict-prototypes
    -pipe
    -DUSE_ICON
    -D_GNU_SOURCE=1
    -D_REENTRANT
    -I/usr/include/SDL
    -DUSE_OPENAL
    -DUSE_OPENAL_DLOPEN
    -DUSE_CURL
    -DUSE_CURL_DLOPEN
    -Icode/SDL12/include
    -m32
    -DUSE_MUMBLE
    -DUSE_VOIP
    -DFLOATING_POINT
    -DUSE_ALLOCA
    -Icode/libspeex/include
    -DNO_GZIP
    -DUSE_LOCAL_HEADERS
    -DPRODUCT_VERSION="beta-115"
    -DNDEBUG
    -O3
    -march=i586
    -fomit-frame-pointer
    -ffast-math
    -funroll-loops
    -falign-loops=2
    -falign-jumps=2
    -falign-functions=2
    -fstrength-reduce

  LDFLAGS:

  LIBS:
    -ldl
    -lm

  CLIENT_LIBS:
    -lSDL
    -lGL
    -lrt

  Output:
    build/release-linux-i386/qlnded.i386
    build/release-linux-i386/qlone.i386
    build/release-linux-i386/qloned/cgamei386.so
    build/release-linux-i386/qloned/qagamei386.so
    build/release-linux-i386/qloned/uii386.so
    build/release-linux-i386/missionpack/cgamei386.so
    build/release-linux-i386/missionpack/qagamei386.so
    build/release-linux-i386/missionpack/uii386.so
    build/release-linux-i386/qloned/vm/cgame.qvm
    build/release-linux-i386/qloned/vm/qagame.qvm
    build/release-linux-i386/qloned/vm/ui.qvm
    build/release-linux-i386/missionpack/vm/qagame.qvm
    build/release-linux-i386/missionpack/vm/cgame.qvm
    build/release-linux-i386/missionpack/vm/ui.qvm

make[2]: Entering directory `/home/mikul/qlone-trunk'
make[2]: `build/release-linux-i386/qlnded.i386' is up to date.
LD build/release-linux-i386/qlone.i386
build/release-linux-i386/client/cl_download.o: In function `DL_Shutdown':
cl_download.c:(.text+0x3c): undefined reference to `curl_global_cleanup'
build/release-linux-i386/client/cl_download.o: In function `Curl_ShowVersion_f':
cl_download.c:(.text+0x188): undefined reference to `curl_version'
build/release-linux-i386/client/cl_download.o: In function `DL_Init':
cl_download.c:(.text+0x1a4): undefined reference to `curl_global_init'
cl_download.c:(.text+0x221): undefined reference to `curl_version'
collect2: ld returned 1 exit status
make[2]: *** [build/release-linux-i386/qlone.i386] Error 1
make[2]: Leaving directory `/home/mikul/qlone-trunk'
make[1]: *** [targets] Error 2
make[1]: Leaving directory `/home/mikul/qlone-trunk'
make: *** [release] Error 2
mikul@anus:~/qlone-trunk$
```
what to do?

---

