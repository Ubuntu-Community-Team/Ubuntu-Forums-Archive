---
title: "How to Compile/Produce a .exe in Ubuntu"
date: 2011-07-01
forum: General Help
---

### Post by johndebian on 2011-07-01
ok

I need to compile/produce a .exe that will work in windows(32-bit).
Right now im using Ubuntu(32-bit).

I've installed minGW: + some of its addons (just in-case)
```
sudo apt-get install mingw32
``` 

There is a cross-make-mingw.sh(In the source files):
```
#!/bin/sh

export CC=i586-mingw32msvc-gcc
export WINDRES=i586-mingw32msvc-windres
export PLATFORM=mingw32
exec make $*
```

And a Makefile that reads:
```
#
# Quake3 Unix Makefile
#
# Nov '98 by Zoid <zoid@idsoftware.com>
#
# Loki Hacking by Bernd Kreimeier
#  and a little more by Ryan C. Gordon.
#  and a little more by Rafael Barrero
#  and a little more by the ioq3 cr3w
#  and a little more by woekele for ioUrbanTerror  :)
#
# GNU Make required
#

COMPILE_PLATFORM=$(shell uname|sed -e s/_.*//|tr '[:upper:]' '[:lower:]')

ifeq ($(COMPILE_PLATFORM),darwin)
  # Apple does some things a little differently...
  COMPILE_ARCH=$(shell uname -p | sed -e s/i.86/i386/)
else
  COMPILE_ARCH=$(shell uname -m | sed -e s/i.86/i386/)
endif

ifeq ($(COMPILE_PLATFORM),mingw32)
  ifeq ($(COMPILE_ARCH),i386)
    COMPILE_ARCH=x86
  endif
endif

BUILD_CLIENT     =1
BUILD_CLIENT_SMP =0
BUILD_SERVER     =0
BUILD_GAME_SO    =0
BUILD_GAME_QVM   =0
OPTIMIZE         =1
USE_SDL          =1
USE_OPENAL       =0
USE_CURL         =1
USE_CODEC_VORBIS =0 

ifeq ($(V),1)
echo_cmd=@:
Q=
else
echo_cmd=@echo
Q=@
endif

#############################################################################
#
# If you require a different configuration from the defaults below, create a
# new file named "Makefile.local" in the same directory as this file and define
# your parameters there. This allows you to change configuration without
# causing problems with keeping up to date with the repository.
#
#############################################################################
-include Makefile.local

ifndef PLATFORM
PLATFORM=$(COMPILE_PLATFORM)
endif
export PLATFORM

ifndef ARCH
ARCH=$(COMPILE_ARCH)
endif

ifeq ($(ARCH),powerpc)
  ARCH=ppc
endif
export ARCH

ifneq ($(PLATFORM),$(COMPILE_PLATFORM))
  CROSS_COMPILING=1
else
  CROSS_COMPILING=0

  ifneq ($(ARCH),$(COMPILE_ARCH))
    CROSS_COMPILING=1
  endif
endif
export CROSS_COMPILING

ifndef COPYDIR
COPYDIR="/usr/local/games/quake3"
endif

ifndef MOUNT_DIR
MOUNT_DIR=code
endif

ifndef BUILD_DIR
BUILD_DIR=build
endif

ifndef GENERATE_DEPENDENCIES
GENERATE_DEPENDENCIES=1
endif

ifndef USE_CCACHE
USE_CCACHE=0
endif
export USE_CCACHE

ifndef USE_SDL
USE_SDL=1
endif

ifndef USE_OPENAL
USE_OPENAL=1
endif

ifndef USE_OPENAL_DLOPEN
USE_OPENAL_DLOPEN=0
endif

ifndef USE_CURL
USE_CURL=1
endif

ifndef USE_CURL_DLOPEN
  ifeq ($(PLATFORM),mingw32)
    USE_CURL_DLOPEN=0
  else
    USE_CURL_DLOPEN=1
  endif
endif

ifndef USE_CODEC_VORBIS
USE_CODEC_VORBIS=0
endif

ifndef USE_LOCAL_HEADERS
USE_LOCAL_HEADERS=1
endif

#############################################################################

BD=$(BUILD_DIR)/debug-$(PLATFORM)-$(ARCH)
BR=$(BUILD_DIR)/release-$(PLATFORM)-$(ARCH)
CDIR=$(MOUNT_DIR)/client
SDIR=$(MOUNT_DIR)/server
RDIR=$(MOUNT_DIR)/renderer
CMDIR=$(MOUNT_DIR)/qcommon
UDIR=$(MOUNT_DIR)/unix
W32DIR=$(MOUNT_DIR)/win32
GDIR=$(MOUNT_DIR)/game
CGDIR=$(MOUNT_DIR)/cgame
BLIBDIR=$(MOUNT_DIR)/botlib
NDIR=$(MOUNT_DIR)/null
UIDIR=$(MOUNT_DIR)/ui
Q3UIDIR=$(MOUNT_DIR)/q3_ui
JPDIR=$(MOUNT_DIR)/jpeg-6
TOOLSDIR=$(MOUNT_DIR)/tools
LOKISETUPDIR=$(UDIR)/setup
SDLHDIR=$(MOUNT_DIR)/SDL12
LIBSDIR=$(MOUNT_DIR)/libs

# extract version info
VERSION=$(shell grep "\#define Q3_VERSION" $(CMDIR)/q_shared.h | \
  sed -e 's/.*".* \([^ ]*\)"/\1/')

#USE_SVN=
#ifeq ($(wildcard .svn),.svn)
#  SVN_REV=$(shell LANG=C svnversion .)
#  ifneq ($(SVN_REV),)
#    SVN_VERSION=$(VERSION)_SVN$(SVN_REV)
#    USE_SVN=1
#  endif
#endif
#ifneq ($(USE_SVN),1)
#    SVN_VERSION=$(VERSION)
#endif


#############################################################################
# SETUP AND BUILD -- LINUX
#############################################################################

## Defaults
LIB=lib

INSTALL=install
MKDIR=mkdir

ifeq ($(PLATFORM),linux)

  ifeq ($(ARCH),alpha)
    ARCH=axp
  else
  ifeq ($(ARCH),x86_64)
    LIB=lib64
  else
  ifeq ($(ARCH),ppc64)
    LIB=lib64
  else
  ifeq ($(ARCH),s390x)
    LIB=lib64
  endif
  endif
  endif
  endif

  BASE_CFLAGS = -Wall -fno-strict-aliasing -Wimplicit -Wstrict-prototypes -pipe

  ifeq ($(USE_OPENAL),1)
    BASE_CFLAGS += -DUSE_OPENAL=1
    ifeq ($(USE_OPENAL_DLOPEN),1)
      BASE_CFLAGS += -DUSE_OPENAL_DLOPEN=1
    endif
  endif

  ifeq ($(USE_CURL),1)
    BASE_CFLAGS += -DUSE_CURL=1
    ifeq ($(USE_CURL_DLOPEN),1)
      BASE_CFLAGS += -DUSE_CURL_DLOPEN=1
    endif
  endif

  ifeq ($(USE_CODEC_VORBIS),1)
    BASE_CFLAGS += -DUSE_CODEC_VORBIS=1
  endif

  ifeq ($(USE_SDL),1)
    BASE_CFLAGS += -DUSE_SDL_VIDEO=1 -DUSE_SDL_SOUND=1 $(shell sdl-config --cflags)
  else
    BASE_CFLAGS += -I/usr/X11R6/include
  endif

  OPTIMIZE = -O3 -ffast-math -funroll-loops -fomit-frame-pointer

  ifeq ($(ARCH),x86_64)
    OPTIMIZE = -O3 -fomit-frame-pointer -ffast-math -funroll-loops \
      -falign-loops=2 -falign-jumps=2 -falign-functions=2 \
      -fstrength-reduce
    # experimental x86_64 jit compiler! you need GNU as
    HAVE_VM_COMPILED = true
  else
  ifeq ($(ARCH),i386)
    OPTIMIZE = -O3 -march=i586 -fomit-frame-pointer -ffast-math \
      -funroll-loops -falign-loops=2 -falign-jumps=2 \
      -falign-functions=2 -fstrength-reduce
    HAVE_VM_COMPILED=true
  else
  ifeq ($(ARCH),ppc)
    BASE_CFLAGS += -maltivec
    HAVE_VM_COMPILED=false
  endif
  endif
  endif

  ifneq ($(HAVE_VM_COMPILED),true)
    BASE_CFLAGS += -DNO_VM_COMPILED
  endif

  DEBUG_CFLAGS = $(BASE_CFLAGS) -g -O0

  RELEASE_CFLAGS=$(BASE_CFLAGS) -DNDEBUG $(OPTIMIZE)

  SHLIBEXT=so
  SHLIBCFLAGS=-fPIC
  SHLIBLDFLAGS=-shared $(LDFLAGS)

  THREAD_LDFLAGS=-lpthread
  LDFLAGS=-ldl -lm

  ifeq ($(USE_SDL),1)
    CLIENT_LDFLAGS=$(shell sdl-config --libs)
  else
    CLIENT_LDFLAGS=-L/usr/X11R6/$(LIB) -lX11 -lXext -lXxf86dga -lXxf86vm
  endif

  ifeq ($(USE_OPENAL),1)
    ifneq ($(USE_OPENAL_DLOPEN),1)
      CLIENT_LDFLAGS += -lopenal
    endif
  endif
 
  ifeq ($(USE_CURL),1)
    ifneq ($(USE_CURL_DLOPEN),1)
      CLIENT_LDFLAGS += -lcurl
    endif
  endif

  ifeq ($(USE_CODEC_VORBIS),1)
    CLIENT_LDFLAGS += -lvorbisfile -lvorbis -logg
  endif

  ifeq ($(ARCH),i386)
    # linux32 make ...
    BASE_CFLAGS += -m32
    LDFLAGS+=-m32
  endif

else # ifeq Linux

#############################################################################
# SETUP AND BUILD -- MAC OS X
#############################################################################

ifeq ($(PLATFORM),darwin)
  HAVE_VM_COMPILED=true
  BASE_CFLAGS=
  CLIENT_LDFLAGS=
  LDFLAGS=
  OPTIMIZE=
  ifeq ($(BUILD_MACOSX_UB),ppc)
    CC=gcc-3.3
    BASE_CFLAGS += -arch ppc -DSMP \
      -DMAC_OS_X_VERSION_MIN_REQUIRED=1020 -nostdinc \
      -F/Developer/SDKs/MacOSX10.2.8.sdk/System/Library/Frameworks \
      -I/Developer/SDKs/MacOSX10.2.8.sdk/usr/include/gcc/darwin/3.3 \
      -isystem /Developer/SDKs/MacOSX10.2.8.sdk/usr/include
    # when using the 10.2 SDK we are not allowed the two-level namespace so
    # in order to get the OpenAL dlopen() stuff to work without major
    # modifications, the controversial -m linker flag must be used.  this
    # throws a ton of multiply defined errors which cannot be suppressed.
    LDFLAGS += -arch ppc \
      -L/Developer/SDKs/MacOSX10.2.8.sdk/usr/lib/gcc/darwin/3.3 \
      -F/Developer/SDKs/MacOSX10.2.8.sdk/System/Library/Frameworks \
      -Wl,-syslibroot,/Developer/SDKs/MacOSX10.2.8.sdk,-m
    ARCH=ppc

    # OS X 10.2 sdk lacks dlopen() so ded would need libSDL anyway
    BUILD_SERVER=0

    # because of a problem with linking on 10.2 this will generate multiply
    # defined symbol errors.  The errors can be turned into warnings with
    # the -m linker flag, but you can't shut up the warnings
    USE_OPENAL_DLOPEN=1
  else
  ifeq ($(BUILD_MACOSX_UB),i386)
    CC=gcc-4.0
    BASE_CFLAGS += -arch i386 -DSMP \
      -mmacosx-version-min=10.4 \
      -DMAC_OS_X_VERSION_MIN_REQUIRED=1040 -nostdinc \
      -F/Developer/SDKs/MacOSX10.4u.sdk/System/Library/Frameworks \
      -I/Developer/SDKs/MacOSX10.4u.sdk/usr/lib/gcc/i686-apple-darwin8/4.0.1/include \
      -isystem /Developer/SDKs/MacOSX10.4u.sdk/usr/include
    LDFLAGS = -arch i386 -mmacosx-version-min=10.4 \
      -L/Developer/SDKs/MacOSX10.4u.sdk/usr/lib/gcc/i686-apple-darwin8/4.0.1 \
      -F/Developer/SDKs/MacOSX10.4u.sdk/System/Library/Frameworks \
      -Wl,-syslibroot,/Developer/SDKs/MacOSX10.4u.sdk
    ARCH=i386
    BUILD_SERVER=0
  else
    # for whatever reason using the headers in the MacOSX SDKs tend to throw
    # errors even though they are identical to the system ones which don't
    # therefore we shut up warning flags when running the universal build
    # script as much as possible.
    BASE_CFLAGS += -Wall -Wimplicit -Wstrict-prototypes
  endif
  endif

  ifeq ($(ARCH),ppc)
    OPTIMIZE += -faltivec -O3
  endif
  ifeq ($(ARCH),i386)
    OPTIMIZE += -march=prescott -mfpmath=sse
    # x86 vm will crash without -mstackrealign since MMX instructions will be
    # used no matter what and they corrupt the frame pointer in VM calls
    BASE_CFLAGS += -mstackrealign
  endif

  BASE_CFLAGS += -fno-strict-aliasing -DMACOS_X -fno-common -pipe

  # Always include debug symbols...you can strip the binary later...
  BASE_CFLAGS += -gfull

  ifeq ($(USE_OPENAL),1)
    BASE_CFLAGS += -DUSE_OPENAL=1
    ifneq ($(USE_OPENAL_DLOPEN),1)
      CLIENT_LDFLAGS += -framework OpenAL
    else
      BASE_CFLAGS += -DUSE_OPENAL_DLOPEN=1
    endif
  endif

  ifeq ($(USE_CURL),1)
    BASE_CFLAGS += -DUSE_CURL=1
    ifneq ($(USE_CURL_DLOPEN),1)
      CLIENT_LDFLAGS += -lcurl
    else
      BASE_CFLAGS += -DUSE_CURL_DLOPEN=1
    endif
  endif

  ifeq ($(USE_CODEC_VORBIS),1)
    BASE_CFLAGS += -DUSE_CODEC_VORBIS=1
    CLIENT_LDFLAGS += -lvorbisfile -lvorbis -logg
  endif

  ifeq ($(USE_SDL),1)
    BASE_CFLAGS += -DUSE_SDL_VIDEO=1 -DUSE_SDL_SOUND=1 -D_THREAD_SAFE=1 \
      -I$(SDLHDIR)/include
    # We copy sdlmain before ranlib'ing it so that subversion doesn't think
    #  the file has been modified by each build.
    LIBSDLMAIN=$(B)/libSDLmain.a
    LIBSDLMAINSRC=$(LIBSDIR)/macosx/libSDLmain.a
    CLIENT_LDFLAGS += -framework Cocoa -framework IOKit -framework OpenGL \
      $(LIBSDIR)/macosx/libSDL-1.2.0.dylib
  else
    # !!! FIXME: frameworks: OpenGL, Carbon, etc...
    #CLIENT_LDFLAGS += -L/usr/X11R6/$(LIB) -lX11 -lXext -lXxf86dga -lXxf86vm
  endif

  OPTIMIZE += -ffast-math -falign-loops=16

  ifneq ($(HAVE_VM_COMPILED),true)
    BASE_CFLAGS += -DNO_VM_COMPILED
  endif

  DEBUG_CFLAGS = $(BASE_CFLAGS) -g -O0

  RELEASE_CFLAGS=$(BASE_CFLAGS) -DNDEBUG $(OPTIMIZE)

  SHLIBEXT=dylib
  SHLIBCFLAGS=-fPIC -fno-common
  SHLIBLDFLAGS=-dynamiclib $(LDFLAGS)

  NOTSHLIBCFLAGS=-mdynamic-no-pic

else # ifeq darwin


#############################################################################
# SETUP AND BUILD -- MINGW32
#############################################################################

ifeq ($(PLATFORM),mingw32)

ifndef WINDRES
WINDRES=windres
endif

  ARCH=x86

  BASE_CFLAGS = -Wall -fno-strict-aliasing -Wimplicit -Wstrict-prototypes

  ifeq ($(USE_OPENAL),1)
    BASE_CFLAGS += -DUSE_OPENAL=1 -DUSE_OPENAL_DLOPEN=1
  endif

  ifeq ($(USE_CURL),1)
    BASE_CFLAGS += -DUSE_CURL=1
    ifneq ($(USE_CURL_DLOPEN),1)
      BASE_CFLAGS += -DCURL_STATICLIB
    endif
  endif

  ifeq ($(USE_CODEC_VORBIS),1)
    BASE_CFLAGS += -DUSE_CODEC_VORBIS=1
  endif

  OPTIMIZE = -O3 -march=i586 -fomit-frame-pointer -ffast-math -falign-loops=2 \
    -funroll-loops -falign-jumps=2 -falign-functions=2 -fstrength-reduce

  HAVE_VM_COMPILED = true

  DEBUG_CFLAGS=$(BASE_CFLAGS) -g -O0

  RELEASE_CFLAGS=$(BASE_CFLAGS) -DNDEBUG $(OPTIMIZE)

  SHLIBEXT=dll
  SHLIBCFLAGS=
  SHLIBLDFLAGS=-shared $(LDFLAGS)

  BINEXT=.exe

  LDFLAGS= -mwindows -lwsock32 -lgdi32 -lwinmm -lole32
  CLIENT_LDFLAGS=

  ifeq ($(USE_CURL),1)
    ifneq ($(USE_CURL_DLOPEN),1)
      CLIENT_LDFLAGS += $(LIBSDIR)/win32/libcurl.a
    endif
  endif

  ifeq ($(USE_CODEC_VORBIS),1)
    CLIENT_LDFLAGS += -lvorbisfile -lvorbis -logg
  endif

  ifeq ($(ARCH),x86)
    # build 32bit
    BASE_CFLAGS += -m32
    LDFLAGS+=-m32
  endif

  BUILD_SERVER = 0
  BUILD_CLIENT_SMP = 0

else # ifeq mingw32

#############################################################################
# SETUP AND BUILD -- FREEBSD
#############################################################################

ifeq ($(PLATFORM),freebsd)

  ifneq (,$(findstring alpha,$(shell uname -m)))
    ARCH=axp
  else #default to i386
    ARCH=i386
  endif #alpha test


  BASE_CFLAGS = -Wall -fno-strict-aliasing -Wimplicit -Wstrict-prototypes \
                -I/usr/X11R6/include

  DEBUG_CFLAGS=$(BASE_CFLAGS) -g

  ifeq ($(USE_OPENAL),1)
    BASE_CFLAGS += -DUSE_OPENAL=1
    ifeq ($(USE_OPENAL_DLOPEN),1)
      BASE_CFLAGS += -DUSE_OPENAL_DLOPEN=1
    endif
  endif

  ifeq ($(USE_CODEC_VORBIS),1)
    BASE_CFLAGS += -DUSE_CODEC_VORBIS=1
  endif

  ifeq ($(USE_SDL),1)
    BASE_CFLAGS += $(shell sdl-config --cflags) -DUSE_SDL_VIDEO=1 -DUSE_SDL_SOUND=1
  endif

  ifeq ($(ARCH),axp)
    BASE_CFLAGS += -DNO_VM_COMPILED
    RELEASE_CFLAGS=$(BASE_CFLAGS) -DNDEBUG -O3 -ffast-math -funroll-loops \
      -fomit-frame-pointer -fexpensive-optimizations
  else
  ifeq ($(ARCH),i386)
    RELEASE_CFLAGS=$(BASE_CFLAGS) -DNDEBUG -O3 -mtune=pentiumpro \
      -march=pentium -fomit-frame-pointer -pipe -ffast-math \
      -falign-loops=2 -falign-jumps=2 -falign-functions=2 \
      -funroll-loops -fstrength-reduce
    HAVE_VM_COMPILED=true
  else
    BASE_CFLAGS += -DNO_VM_COMPILED
  endif
  endif

  SHLIBEXT=so
  SHLIBCFLAGS=-fPIC
  SHLIBLDFLAGS=-shared $(LDFLAGS)

  THREAD_LDFLAGS=-lpthread
  # don't need -ldl (FreeBSD)
  LDFLAGS=-lm

  CLIENT_LDFLAGS =

  ifeq ($(USE_SDL),1)
    CLIENT_LDFLAGS += $(shell sdl-config --libs)
  else
    CLIENT_LDFLAGS += -L/usr/X11R6/$(LIB) -lGL -lX11 -lXext -lXxf86dga -lXxf86vm
  endif

  ifeq ($(USE_OPENAL),1)
    ifneq ($(USE_OPENAL_DLOPEN),1)
      CLIENT_LDFLAGS += $(THREAD_LDFLAGS) -lopenal
    endif
  endif

  ifeq ($(USE_CODEC_VORBIS),1)
    CLIENT_LDFLAGS += -lvorbisfile -lvorbis -logg
  endif


else # ifeq freebsd

#############################################################################
# SETUP AND BUILD -- NETBSD
#############################################################################

ifeq ($(PLATFORM),netbsd)

  ifeq ($(shell uname -m),i386)
    ARCH=i386
  endif

  LDFLAGS=-lm
  SHLIBEXT=so
  SHLIBCFLAGS=-fPIC
  SHLIBLDFLAGS=-shared $(LDFLAGS)
  THREAD_LDFLAGS=-lpthread

  BASE_CFLAGS = -Wall -fno-strict-aliasing -Wimplicit -Wstrict-prototypes
  DEBUG_CFLAGS=$(BASE_CFLAGS) -g

  ifneq ($(ARCH),i386)
    BASE_CFLAGS += -DNO_VM_COMPILED
  endif

  BUILD_CLIENT = 0
  BUILD_GAME_QVM = 0

else # ifeq netbsd

#############################################################################
# SETUP AND BUILD -- IRIX
#############################################################################

ifeq ($(PLATFORM),irix)

  ARCH=mips  #default to MIPS

  BASE_CFLAGS=-Dstricmp=strcasecmp -Xcpluscomm -woff 1185 -mips3 \
    -nostdinc -I. -I$(ROOT)/usr/include -DNO_VM_COMPILED
  RELEASE_CFLAGS=$(BASE_CFLAGS) -O3
  DEBUG_CFLAGS=$(BASE_CFLAGS) -g

  SHLIBEXT=so
  SHLIBCFLAGS=
  SHLIBLDFLAGS=-shared

  LDFLAGS=-ldl -lm
  CLIENT_LDFLAGS=-L/usr/X11/$(LIB) -lGL -lX11 -lXext -lm

else # ifeq IRIX

#############################################################################
# SETUP AND BUILD -- SunOS
#############################################################################

ifeq ($(PLATFORM),sunos)

  CC=gcc
  INSTALL=ginstall
  MKDIR=gmkdir
  COPYDIR="/usr/local/share/games/quake3"

  ifneq (,$(findstring i86pc,$(shell uname -m)))
    ARCH=i386
  else #default to sparc
    ARCH=sparc
  endif

  ifneq ($(ARCH),i386)
    ifneq ($(ARCH),sparc)
      $(error arch $(ARCH) is currently not supported)
    endif
  endif


  BASE_CFLAGS = -Wall -fno-strict-aliasing -Wimplicit -Wstrict-prototypes -pipe

  ifeq ($(USE_SDL),1)
    BASE_CFLAGS += -DUSE_SDL_SOUND=1 $(shell sdl-config --cflags)
  else
    BASE_CFLAGS += -I/usr/openwin/include
  endif

  OPTIMIZE = -O3 -ffast-math -funroll-loops

  ifeq ($(ARCH),sparc)
    OPTIMIZE = -O3 -ffast-math -falign-loops=2 \
      -falign-jumps=2 -falign-functions=2 -fstrength-reduce \
      -mtune=ultrasparc -mv8plus -mno-faster-structs \
      -funroll-loops
  else
  ifeq ($(ARCH),i386)
    OPTIMIZE = -O3 -march=i586 -fomit-frame-pointer -ffast-math \
      -funroll-loops -falign-loops=2 -falign-jumps=2 \
      -falign-functions=2 -fstrength-reduce
    HAVE_VM_COMPILED=true
    BASE_CFLAGS += -m32
    LDFLAGS += -m32
    BASE_CFLAGS += -I/usr/X11/include/NVIDIA
  endif
  endif

  ifneq ($(HAVE_VM_COMPILED),true)
    BASE_CFLAGS += -DNO_VM_COMPILED
  endif

  DEBUG_CFLAGS = $(BASE_CFLAGS) -ggdb -O0

  RELEASE_CFLAGS=$(BASE_CFLAGS) -DNDEBUG $(OPTIMIZE)

  SHLIBEXT=so
  SHLIBCFLAGS=-fPIC
  SHLIBLDFLAGS=-shared $(LDFLAGS)

  THREAD_LDFLAGS=-lpthread
  LDFLAGS=-lsocket -lnsl -ldl -lm

  BOTCFLAGS=-O0

  ifeq ($(USE_SDL),1)
    CLIENT_LDFLAGS=$(shell sdl-config --libs) -L/usr/X11/lib -lGLU -lX11 -lXext
  else
    CLIENT_LDFLAGS=-L/usr/openwin/$(LIB) -L/usr/X11/lib -lGLU -lX11 -lXext
  endif

else # ifeq sunos

#############################################################################
# SETUP AND BUILD -- GENERIC
#############################################################################
  BASE_CFLAGS=-DNO_VM_COMPILED
  DEBUG_CFLAGS=$(BASE_CFLAGS) -g
  RELEASE_CFLAGS=$(BASE_CFLAGS) -DNDEBUG -O3

  SHLIBEXT=so
  SHLIBCFLAGS=-fPIC
  SHLIBLDFLAGS=-shared

endif #Linux
endif #darwin
endif #mingw32
endif #FreeBSD
endif #NetBSD
endif #IRIX
endif #SunOS

TARGETS =

ifneq ($(BUILD_SERVER),0)
  TARGETS += $(B)/ioUrTded.$(ARCH)$(BINEXT)
endif

ifneq ($(BUILD_CLIENT),0)
  TARGETS += $(B)/ioUrbanTerror.$(ARCH)$(BINEXT)
  ifneq ($(BUILD_CLIENT_SMP),0)
    TARGETS += $(B)/ioUrbanTerror-smp.$(ARCH)$(BINEXT)
  endif
endif

ifneq ($(BUILD_GAME_SO),0)
  TARGETS += \
    $(B)/baseq3/cgame$(ARCH).$(SHLIBEXT) \
    $(B)/baseq3/qagame$(ARCH).$(SHLIBEXT) \
    $(B)/baseq3/ui$(ARCH).$(SHLIBEXT)     \
    $(B)/missionpack/cgame$(ARCH).$(SHLIBEXT) \
    $(B)/missionpack/qagame$(ARCH).$(SHLIBEXT) \
    $(B)/missionpack/ui$(ARCH).$(SHLIBEXT)
endif

ifneq ($(BUILD_GAME_QVM),0)
  ifneq ($(CROSS_COMPILING),1)
    TARGETS += \
      $(B)/baseq3/vm/cgame.qvm \
      $(B)/baseq3/vm/qagame.qvm \
      $(B)/baseq3/vm/ui.qvm \
      $(B)/missionpack/vm/qagame.qvm \
      $(B)/missionpack/vm/cgame.qvm \
      $(B)/missionpack/vm/ui.qvm
  endif
endif

ifeq ($(USE_CCACHE),1)
  CC := ccache $(CC)
endif

ifdef DEFAULT_BASEDIR
  BASE_CFLAGS += -DDEFAULT_BASEDIR=\\\"$(DEFAULT_BASEDIR)\\\"
endif

ifeq ($(USE_LOCAL_HEADERS),1)
  BASE_CFLAGS += -DUSE_LOCAL_HEADERS=1
endif

ifeq ($(GENERATE_DEPENDENCIES),1)
  BASE_CFLAGS += -MMD
endif

ifeq ($(USE_SVN),1)
  BASE_CFLAGS += -DSVN_VERSION=\\\"$(SVN_VERSION)\\\"
endif

define DO_CC       
$(echo_cmd) "CC $<"
$(Q)$(CC) $(NOTSHLIBCFLAGS) $(CFLAGS) -o $@ -c $<
endef

define DO_SMP_CC
$(echo_cmd) "SMP_CC $<"
$(Q)$(CC) $(NOTSHLIBCFLAGS) $(CFLAGS) -DSMP -o $@ -c $<
endef

define DO_BOT_CC
$(echo_cmd) "BOT_CC $<"
$(Q)$(CC) $(NOTSHLIBCFLAGS) $(CFLAGS) $(BOTCFLAGS) -DBOTLIB -o $@ -c $<
endef

ifeq ($(GENERATE_DEPENDENCIES),1)
  DO_QVM_DEP=cat $(@:%.o=%.d) | sed -e 's/\.o/\.asm/g' >> $(@:%.o=%.d)
endif

define DO_SHLIB_CC
$(echo_cmd) "SHLIB_CC $<"
$(Q)$(CC) $(CFLAGS) $(SHLIBCFLAGS) -o $@ -c $<
$(Q)$(DO_QVM_DEP)
endef

define DO_SHLIB_CC_MISSIONPACK
$(echo_cmd) "SHLIB_CC_MISSIONPACK $<"
$(Q)$(CC) -DMISSIONPACK $(CFLAGS) $(SHLIBCFLAGS) -o $@ -c $<
$(Q)$(DO_QVM_DEP)
endef

define DO_AS
$(echo_cmd) "AS $<"
$(Q)$(CC) $(CFLAGS) -DELF -x assembler-with-cpp -o $@ -c $<
endef

define DO_DED_CC
$(echo_cmd) "DED_CC $<"
$(Q)$(CC) $(NOTSHLIBCFLAGS) -DDEDICATED $(CFLAGS) -o $@ -c $<
endef

define DO_WINDRES
$(echo_cmd) "WINDRES $<"
$(Q)$(WINDRES) -i $< -o $@
endef


#############################################################################
# MAIN TARGETS
#############################################################################

default: release
all: debug release

debug:
	@$(MAKE) targets B=$(BD) CFLAGS="$(CFLAGS) $(DEBUG_CFLAGS)" V=$(V)

release:
	@$(MAKE) targets B=$(BR) CFLAGS="$(CFLAGS) $(RELEASE_CFLAGS)" V=$(V)

# Create the build directories and tools, print out
# an informational message, then start building
targets: makedirs tools
	@echo ""
	@echo "Building ioUrbanTerror in $(B):"
	@echo "  PLATFORM: $(PLATFORM)"
	@echo "  ARCH: $(ARCH)"
	@echo "  COMPILE_PLATFORM: $(COMPILE_PLATFORM)"
	@echo "  COMPILE_ARCH: $(COMPILE_ARCH)"
	@echo "  CC: $(CC)"
	@echo ""
	@echo "  CFLAGS:"
	@for i in $(CFLAGS); \
	do \
		echo "    $$i"; \
	done
	@echo ""
	@echo "  Output:"
	@for i in $(TARGETS); \
	do \
		echo "    $$i"; \
	done
	@echo ""
	@$(MAKE) $(TARGETS) V=$(V)

makedirs:
	@if [ ! -d $(BUILD_DIR) ];then $(MKDIR) $(BUILD_DIR);fi
	@if [ ! -d $(B) ];then $(MKDIR) $(B);fi
	@if [ ! -d $(B)/client ];then $(MKDIR) $(B)/client;fi
	@if [ ! -d $(B)/clientsmp ];then $(MKDIR) $(B)/clientsmp;fi
	@if [ ! -d $(B)/ded ];then $(MKDIR) $(B)/ded;fi
	@if [ ! -d $(B)/baseq3 ];then $(MKDIR) $(B)/baseq3;fi
	@if [ ! -d $(B)/baseq3/cgame ];then $(MKDIR) $(B)/baseq3/cgame;fi
	@if [ ! -d $(B)/baseq3/game ];then $(MKDIR) $(B)/baseq3/game;fi
	@if [ ! -d $(B)/baseq3/ui ];then $(MKDIR) $(B)/baseq3/ui;fi
	@if [ ! -d $(B)/baseq3/qcommon ];then $(MKDIR) $(B)/baseq3/qcommon;fi
	@if [ ! -d $(B)/baseq3/vm ];then $(MKDIR) $(B)/baseq3/vm;fi
	@if [ ! -d $(B)/missionpack ];then $(MKDIR) $(B)/missionpack;fi
	@if [ ! -d $(B)/missionpack/cgame ];then $(MKDIR) $(B)/missionpack/cgame;fi
	@if [ ! -d $(B)/missionpack/game ];then $(MKDIR) $(B)/missionpack/game;fi
	@if [ ! -d $(B)/missionpack/ui ];then $(MKDIR) $(B)/missionpack/ui;fi
	@if [ ! -d $(B)/missionpack/qcommon ];then $(MKDIR) $(B)/missionpack/qcommon;fi
	@if [ ! -d $(B)/missionpack/vm ];then $(MKDIR) $(B)/missionpack/vm;fi

#############################################################################
# QVM BUILD TOOLS
#############################################################################

Q3LCC=$(TOOLSDIR)/q3lcc$(BINEXT)
Q3ASM=$(TOOLSDIR)/q3asm$(BINEXT)

ifeq ($(CROSS_COMPILING),1)
tools:
	@echo QVM tools not built when cross-compiling
else
tools:
	$(MAKE) -C $(TOOLSDIR)/lcc install
	$(MAKE) -C $(TOOLSDIR)/asm install
endif

define DO_Q3LCC
$(echo_cmd) "Q3LCC $<"
$(Q)$(Q3LCC) -o $@ $<
endef

define DO_Q3LCC_MISSIONPACK
$(echo_cmd) "Q3LCC_MISSIONPACK $<"
$(Q)$(Q3LCC) -DMISSIONPACK -o $@ $<
endef


#############################################################################
# CLIENT/SERVER
#############################################################################

Q3OBJ = \
  $(B)/client/cl_cgame.o \
  $(B)/client/cl_cin.o \
  $(B)/client/cl_console.o \
  $(B)/client/cl_input.o \
  $(B)/client/cl_keys.o \
  $(B)/client/cl_main.o \
  $(B)/client/cl_net_chan.o \
  $(B)/client/cl_parse.o \
  $(B)/client/cl_scrn.o \
  $(B)/client/cl_ui.o \
  $(B)/client/cl_avi.o \
  \
  $(B)/client/cm_load.o \
  $(B)/client/cm_patch.o \
  $(B)/client/cm_polylib.o \
  $(B)/client/cm_test.o \
  $(B)/client/cm_trace.o \
  \
  $(B)/client/cmd.o \
  $(B)/client/common.o \
  $(B)/client/cvar.o \
  $(B)/client/files.o \
  $(B)/client/md4.o \
  $(B)/client/md5.o \
  $(B)/client/msg.o \
  $(B)/client/net_chan.o \
  $(B)/client/net_ip.o \
  $(B)/client/huffman.o \
  \
  $(B)/client/snd_adpcm.o \
  $(B)/client/snd_dma.o \
  $(B)/client/snd_mem.o \
  $(B)/client/snd_mix.o \
  $(B)/client/snd_wavelet.o \
  \
  $(B)/client/snd_main.o \
  $(B)/client/snd_codec.o \
  $(B)/client/snd_codec_wav.o \
  $(B)/client/snd_codec_ogg.o \
  \
  $(B)/client/qal.o \
  $(B)/client/snd_openal.o \
  \
  $(B)/client/cl_curl.o \
  \
  $(B)/client/sv_bot.o \
  $(B)/client/sv_ccmds.o \
  $(B)/client/sv_client.o \
  $(B)/client/sv_game.o \
  $(B)/client/sv_init.o \
  $(B)/client/sv_main.o \
  $(B)/client/sv_net_chan.o \
  $(B)/client/sv_snapshot.o \
  $(B)/client/sv_world.o \
  \
  $(B)/client/q_math.o \
  $(B)/client/q_shared.o \
  \
  $(B)/client/unzip.o \
  $(B)/client/puff.o \
  $(B)/client/vm.o \
  $(B)/client/vm_interpreted.o \
  \
  $(B)/client/be_aas_bspq3.o \
  $(B)/client/be_aas_cluster.o \
  $(B)/client/be_aas_debug.o \
  $(B)/client/be_aas_entity.o \
  $(B)/client/be_aas_file.o \
  $(B)/client/be_aas_main.o \
  $(B)/client/be_aas_move.o \
  $(B)/client/be_aas_optimize.o \
  $(B)/client/be_aas_reach.o \
  $(B)/client/be_aas_route.o \
  $(B)/client/be_aas_routealt.o \
  $(B)/client/be_aas_sample.o \
  $(B)/client/be_ai_char.o \
  $(B)/client/be_ai_chat.o \
  $(B)/client/be_ai_gen.o \
  $(B)/client/be_ai_goal.o \
  $(B)/client/be_ai_move.o \
  $(B)/client/be_ai_weap.o \
  $(B)/client/be_ai_weight.o \
  $(B)/client/be_ea.o \
  $(B)/client/be_interface.o \
  $(B)/client/l_crc.o \
  $(B)/client/l_libvar.o \
  $(B)/client/l_log.o \
  $(B)/client/l_memory.o \
  $(B)/client/l_precomp.o \
  $(B)/client/l_script.o \
  $(B)/client/l_struct.o \
  \
  $(B)/client/jcapimin.o \
  $(B)/client/jchuff.o   \
  $(B)/client/jcinit.o \
  $(B)/client/jccoefct.o  \
  $(B)/client/jccolor.o \
  $(B)/client/jfdctflt.o \
  $(B)/client/jcdctmgr.o \
  $(B)/client/jcphuff.o \
  $(B)/client/jcmainct.o \
  $(B)/client/jcmarker.o \
  $(B)/client/jcmaster.o \
  $(B)/client/jcomapi.o \
  $(B)/client/jcparam.o \
  $(B)/client/jcprepct.o \
  $(B)/client/jcsample.o \
  $(B)/client/jdapimin.o \
  $(B)/client/jdapistd.o \
  $(B)/client/jdatasrc.o \
  $(B)/client/jdcoefct.o \
  $(B)/client/jdcolor.o \
  $(B)/client/jddctmgr.o \
  $(B)/client/jdhuff.o \
  $(B)/client/jdinput.o \
  $(B)/client/jdmainct.o \
  $(B)/client/jdmarker.o \
  $(B)/client/jdmaster.o \
  $(B)/client/jdpostct.o \
  $(B)/client/jdsample.o \
  $(B)/client/jdtrans.o \
  $(B)/client/jerror.o \
  $(B)/client/jidctflt.o \
  $(B)/client/jmemmgr.o \
  $(B)/client/jmemnobs.o \
  $(B)/client/jutils.o \
  \
  $(B)/client/tr_animation.o \
  $(B)/client/tr_backend.o \
  $(B)/client/tr_bsp.o \
  $(B)/client/tr_cmds.o \
  $(B)/client/tr_curve.o \
  $(B)/client/tr_flares.o \
  $(B)/client/tr_font.o \
  $(B)/client/tr_image.o \
  $(B)/client/tr_init.o \
  $(B)/client/tr_light.o \
  $(B)/client/tr_main.o \
  $(B)/client/tr_marks.o \
  $(B)/client/tr_mesh.o \
  $(B)/client/tr_model.o \
  $(B)/client/tr_noise.o \
  $(B)/client/tr_scene.o \
  $(B)/client/tr_shade.o \
  $(B)/client/tr_shade_calc.o \
  $(B)/client/tr_shader.o \
  $(B)/client/tr_shadows.o \
  $(B)/client/tr_sky.o \
  $(B)/client/tr_surface.o \
  $(B)/client/tr_world.o \

ifeq ($(ARCH),i386)
  Q3OBJ += \
    $(B)/client/snd_mixa.o \
    $(B)/client/matha.o \
    $(B)/client/ftola.o \
    $(B)/client/snapvectora.o
endif
ifeq ($(ARCH),x86)
  Q3OBJ += \
    $(B)/client/snd_mixa.o \
    $(B)/client/matha.o \
    $(B)/client/ftola.o \
    $(B)/client/snapvectora.o
endif

ifeq ($(HAVE_VM_COMPILED),true)
  ifeq ($(ARCH),i386)
    Q3OBJ += $(B)/client/vm_x86.o
  endif
  ifeq ($(ARCH),x86)
    Q3OBJ += $(B)/client/vm_x86.o
  endif
  ifeq ($(ARCH),x86_64)
    Q3OBJ += $(B)/client/vm_x86_64.o $(B)/client/vm_x86_64_assembler.o
  endif
  ifeq ($(ARCH),ppc)
    Q3OBJ += $(B)/client/vm_ppc.o
  endif
endif

ifeq ($(PLATFORM),mingw32)
  Q3OBJ += \
    $(B)/client/win_gamma.o \
    $(B)/client/win_glimp.o \
    $(B)/client/win_input.o \
    $(B)/client/win_main.o \
    $(B)/client/win_qgl.o \
    $(B)/client/win_shared.o \
    $(B)/client/win_snd.o \
    $(B)/client/win_syscon.o \
    $(B)/client/win_wndproc.o \
    $(B)/client/win_resource.o
else
  Q3OBJ += \
    $(B)/client/unix_main.o \
    $(B)/client/unix_shared.o \
    $(B)/client/linux_signals.o \
    $(B)/client/linux_qgl.o \
    $(B)/client/linux_snd.o \
    $(B)/client/sdl_snd.o

  ifeq ($(PLATFORM),linux)
    Q3OBJ += $(B)/client/linux_joystick.o
  endif

  ifeq ($(USE_SDL),1)
    ifneq ($(PLATFORM),darwin)
      BUILD_CLIENT_SMP = 0
    endif
  endif

  Q3POBJ = \
    $(B)/client/linux_glimp.o \
    $(B)/client/sdl_glimp.o

  Q3POBJ_SMP = \
    $(B)/clientsmp/linux_glimp.o \
    $(B)/clientsmp/sdl_glimp.o
endif

$(B)/ioUrbanTerror.$(ARCH)$(BINEXT): $(Q3OBJ) $(Q3POBJ) $(LIBSDLMAIN)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) -o $@ $(Q3OBJ) $(Q3POBJ) $(CLIENT_LDFLAGS) \
		$(LDFLAGS) $(LIBSDLMAIN)

$(B)/ioUrbanTerror-smp.$(ARCH)$(BINEXT): $(Q3OBJ) $(Q3POBJ_SMP) $(LIBSDLMAIN)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) -o $@ $(Q3OBJ) $(Q3POBJ_SMP) $(CLIENT_LDFLAGS) \
		$(THREAD_LDFLAGS) $(LDFLAGS) $(LIBSDLMAIN)

ifneq ($(strip $(LIBSDLMAIN)),)
ifneq ($(strip $(LIBSDLMAINSRC)),)
$(LIBSDLMAIN) : $(LIBSDLMAINSRC)
	cp $< $@
	ranlib $@
endif
endif



#############################################################################
# DEDICATED SERVER
#############################################################################

Q3DOBJ = \
  $(B)/ded/sv_bot.o \
  $(B)/ded/sv_client.o \
  $(B)/ded/sv_ccmds.o \
  $(B)/ded/sv_game.o \
  $(B)/ded/sv_init.o \
  $(B)/ded/sv_main.o \
  $(B)/ded/sv_net_chan.o \
  $(B)/ded/sv_snapshot.o \
  $(B)/ded/sv_world.o \
  \
  $(B)/ded/cm_load.o \
  $(B)/ded/cm_patch.o \
  $(B)/ded/cm_polylib.o \
  $(B)/ded/cm_test.o \
  $(B)/ded/cm_trace.o \
  $(B)/ded/cmd.o \
  $(B)/ded/common.o \
  $(B)/ded/cvar.o \
  $(B)/ded/files.o \
  $(B)/ded/md4.o \
  $(B)/ded/msg.o \
  $(B)/ded/net_chan.o \
  $(B)/ded/net_ip.o \
  $(B)/ded/huffman.o \
  \
  $(B)/ded/q_math.o \
  $(B)/ded/q_shared.o \
  \
  $(B)/ded/unzip.o \
  $(B)/ded/vm.o \
  $(B)/ded/vm_interpreted.o \
  \
  $(B)/ded/be_aas_bspq3.o \
  $(B)/ded/be_aas_cluster.o \
  $(B)/ded/be_aas_debug.o \
  $(B)/ded/be_aas_entity.o \
  $(B)/ded/be_aas_file.o \
  $(B)/ded/be_aas_main.o \
  $(B)/ded/be_aas_move.o \
  $(B)/ded/be_aas_optimize.o \
  $(B)/ded/be_aas_reach.o \
  $(B)/ded/be_aas_route.o \
  $(B)/ded/be_aas_routealt.o \
  $(B)/ded/be_aas_sample.o \
  $(B)/ded/be_ai_char.o \
  $(B)/ded/be_ai_chat.o \
  $(B)/ded/be_ai_gen.o \
  $(B)/ded/be_ai_goal.o \
  $(B)/ded/be_ai_move.o \
  $(B)/ded/be_ai_weap.o \
  $(B)/ded/be_ai_weight.o \
  $(B)/ded/be_ea.o \
  $(B)/ded/be_interface.o \
  $(B)/ded/l_crc.o \
  $(B)/ded/l_libvar.o \
  $(B)/ded/l_log.o \
  $(B)/ded/l_memory.o \
  $(B)/ded/l_precomp.o \
  $(B)/ded/l_script.o \
  $(B)/ded/l_struct.o \
  \
  $(B)/ded/linux_signals.o \
  $(B)/ded/unix_main.o \
  $(B)/ded/unix_shared.o \
  \
  $(B)/ded/null_client.o \
  $(B)/ded/null_input.o \
  $(B)/ded/null_snddma.o

ifeq ($(ARCH),i386)
  Q3DOBJ += \
      $(B)/ded/ftola.o \
      $(B)/ded/snapvectora.o \
      $(B)/ded/matha.o
endif
ifeq ($(ARCH),x86)
  Q3DOBJ += \
      $(B)/ded/ftola.o \
      $(B)/ded/snapvectora.o \
      $(B)/ded/matha.o
endif

ifeq ($(HAVE_VM_COMPILED),true)
  ifeq ($(ARCH),i386)
    Q3DOBJ += $(B)/ded/vm_x86.o
  endif
  ifeq ($(ARCH),x86)
    Q3DOBJ += $(B)/ded/vm_x86.o
  endif
  ifeq ($(ARCH),x86_64)
    Q3DOBJ += $(B)/ded/vm_x86_64.o $(B)/client/vm_x86_64_assembler.o
  endif
  ifeq ($(ARCH),ppc)
    Q3DOBJ += $(B)/ded/vm_ppc.o
  endif
endif

$(B)/ioUrTded.$(ARCH)$(BINEXT): $(Q3DOBJ)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) -o $@ $(Q3DOBJ) $(LDFLAGS)



#############################################################################
## BASEQ3 CGAME
#############################################################################

Q3CGOBJ_ = \
  $(B)/baseq3/cgame/cg_main.o \
  $(B)/baseq3/game/bg_misc.o \
  $(B)/baseq3/game/bg_pmove.o \
  $(B)/baseq3/game/bg_slidemove.o \
  $(B)/baseq3/cgame/cg_consolecmds.o \
  $(B)/baseq3/cgame/cg_draw.o \
  $(B)/baseq3/cgame/cg_drawtools.o \
  $(B)/baseq3/cgame/cg_effects.o \
  $(B)/baseq3/cgame/cg_ents.o \
  $(B)/baseq3/cgame/cg_event.o \
  $(B)/baseq3/cgame/cg_info.o \
  $(B)/baseq3/cgame/cg_localents.o \
  $(B)/baseq3/cgame/cg_marks.o \
  $(B)/baseq3/cgame/cg_players.o \
  $(B)/baseq3/cgame/cg_playerstate.o \
  $(B)/baseq3/cgame/cg_predict.o \
  $(B)/baseq3/cgame/cg_scoreboard.o \
  $(B)/baseq3/cgame/cg_servercmds.o \
  $(B)/baseq3/cgame/cg_snapshot.o \
  $(B)/baseq3/cgame/cg_view.o \
  $(B)/baseq3/cgame/cg_weapons.o \
  \
  $(B)/baseq3/qcommon/q_math.o \
  $(B)/baseq3/qcommon/q_shared.o

Q3CGOBJ = $(Q3CGOBJ_) $(B)/baseq3/cgame/cg_syscalls.o
Q3CGVMOBJ = $(Q3CGOBJ_:%.o=%.asm) $(B)/baseq3/game/bg_lib.asm

$(B)/baseq3/cgame$(ARCH).$(SHLIBEXT) : $(Q3CGOBJ)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) $(SHLIBLDFLAGS) -o $@ $(Q3CGOBJ)

$(B)/baseq3/vm/cgame.qvm: $(Q3CGVMOBJ) $(CGDIR)/cg_syscalls.asm
	$(echo_cmd) "Q3ASM $@"
	$(Q)$(Q3ASM) -o $@ $(Q3CGVMOBJ) $(CGDIR)/cg_syscalls.asm

#############################################################################
## MISSIONPACK CGAME
#############################################################################

MPCGOBJ_ = \
  $(B)/missionpack/cgame/cg_main.o \
  $(B)/missionpack/game/bg_misc.o \
  $(B)/missionpack/game/bg_pmove.o \
  $(B)/missionpack/game/bg_slidemove.o \
  $(B)/missionpack/cgame/cg_consolecmds.o \
  $(B)/missionpack/cgame/cg_newdraw.o \
  $(B)/missionpack/cgame/cg_draw.o \
  $(B)/missionpack/cgame/cg_drawtools.o \
  $(B)/missionpack/cgame/cg_effects.o \
  $(B)/missionpack/cgame/cg_ents.o \
  $(B)/missionpack/cgame/cg_event.o \
  $(B)/missionpack/cgame/cg_info.o \
  $(B)/missionpack/cgame/cg_localents.o \
  $(B)/missionpack/cgame/cg_marks.o \
  $(B)/missionpack/cgame/cg_players.o \
  $(B)/missionpack/cgame/cg_playerstate.o \
  $(B)/missionpack/cgame/cg_predict.o \
  $(B)/missionpack/cgame/cg_scoreboard.o \
  $(B)/missionpack/cgame/cg_servercmds.o \
  $(B)/missionpack/cgame/cg_snapshot.o \
  $(B)/missionpack/cgame/cg_view.o \
  $(B)/missionpack/cgame/cg_weapons.o \
  $(B)/missionpack/ui/ui_shared.o \
  \
  $(B)/missionpack/qcommon/q_math.o \
  $(B)/missionpack/qcommon/q_shared.o

MPCGOBJ = $(MPCGOBJ_) $(B)/missionpack/cgame/cg_syscalls.o
MPCGVMOBJ = $(MPCGOBJ_:%.o=%.asm) $(B)/missionpack/game/bg_lib.asm

$(B)/missionpack/cgame$(ARCH).$(SHLIBEXT) : $(MPCGOBJ)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) $(SHLIBLDFLAGS) -o $@ $(MPCGOBJ)

$(B)/missionpack/vm/cgame.qvm: $(MPCGVMOBJ) $(CGDIR)/cg_syscalls.asm
	$(echo_cmd) "Q3ASM $@"
	$(Q)$(Q3ASM) -o $@ $(MPCGVMOBJ) $(CGDIR)/cg_syscalls.asm



#############################################################################
## BASEQ3 GAME
#############################################################################

Q3GOBJ_ = \
  $(B)/baseq3/game/g_main.o \
  $(B)/baseq3/game/ai_chat.o \
  $(B)/baseq3/game/ai_cmd.o \
  $(B)/baseq3/game/ai_dmnet.o \
  $(B)/baseq3/game/ai_dmq3.o \
  $(B)/baseq3/game/ai_main.o \
  $(B)/baseq3/game/ai_team.o \
  $(B)/baseq3/game/ai_vcmd.o \
  $(B)/baseq3/game/bg_misc.o \
  $(B)/baseq3/game/bg_pmove.o \
  $(B)/baseq3/game/bg_slidemove.o \
  $(B)/baseq3/game/g_active.o \
  $(B)/baseq3/game/g_arenas.o \
  $(B)/baseq3/game/g_bot.o \
  $(B)/baseq3/game/g_client.o \
  $(B)/baseq3/game/g_cmds.o \
  $(B)/baseq3/game/g_combat.o \
  $(B)/baseq3/game/g_items.o \
  $(B)/baseq3/game/g_mem.o \
  $(B)/baseq3/game/g_misc.o \
  $(B)/baseq3/game/g_missile.o \
  $(B)/baseq3/game/g_mover.o \
  $(B)/baseq3/game/g_session.o \
  $(B)/baseq3/game/g_spawn.o \
  $(B)/baseq3/game/g_svcmds.o \
  $(B)/baseq3/game/g_target.o \
  $(B)/baseq3/game/g_team.o \
  $(B)/baseq3/game/g_trigger.o \
  $(B)/baseq3/game/g_utils.o \
  $(B)/baseq3/game/g_weapon.o \
  \
  $(B)/baseq3/qcommon/q_math.o \
  $(B)/baseq3/qcommon/q_shared.o

Q3GOBJ = $(Q3GOBJ_) $(B)/baseq3/game/g_syscalls.o
Q3GVMOBJ = $(Q3GOBJ_:%.o=%.asm) $(B)/baseq3/game/bg_lib.asm

$(B)/baseq3/qagame$(ARCH).$(SHLIBEXT) : $(Q3GOBJ)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) $(SHLIBLDFLAGS) -o $@ $(Q3GOBJ)

$(B)/baseq3/vm/qagame.qvm: $(Q3GVMOBJ) $(GDIR)/g_syscalls.asm
	$(echo_cmd) "Q3ASM $@"
	$(Q)$(Q3ASM) -o $@ $(Q3GVMOBJ) $(GDIR)/g_syscalls.asm

#############################################################################
## MISSIONPACK GAME
#############################################################################

MPGOBJ_ = \
  $(B)/missionpack/game/g_main.o \
  $(B)/missionpack/game/ai_chat.o \
  $(B)/missionpack/game/ai_cmd.o \
  $(B)/missionpack/game/ai_dmnet.o \
  $(B)/missionpack/game/ai_dmq3.o \
  $(B)/missionpack/game/ai_main.o \
  $(B)/missionpack/game/ai_team.o \
  $(B)/missionpack/game/ai_vcmd.o \
  $(B)/missionpack/game/bg_misc.o \
  $(B)/missionpack/game/bg_pmove.o \
  $(B)/missionpack/game/bg_slidemove.o \
  $(B)/missionpack/game/g_active.o \
  $(B)/missionpack/game/g_arenas.o \
  $(B)/missionpack/game/g_bot.o \
  $(B)/missionpack/game/g_client.o \
  $(B)/missionpack/game/g_cmds.o \
  $(B)/missionpack/game/g_combat.o \
  $(B)/missionpack/game/g_items.o \
  $(B)/missionpack/game/g_mem.o \
  $(B)/missionpack/game/g_misc.o \
  $(B)/missionpack/game/g_missile.o \
  $(B)/missionpack/game/g_mover.o \
  $(B)/missionpack/game/g_session.o \
  $(B)/missionpack/game/g_spawn.o \
  $(B)/missionpack/game/g_svcmds.o \
  $(B)/missionpack/game/g_target.o \
  $(B)/missionpack/game/g_team.o \
  $(B)/missionpack/game/g_trigger.o \
  $(B)/missionpack/game/g_utils.o \
  $(B)/missionpack/game/g_weapon.o \
  \
  $(B)/missionpack/qcommon/q_math.o \
  $(B)/missionpack/qcommon/q_shared.o

MPGOBJ = $(MPGOBJ_) $(B)/missionpack/game/g_syscalls.o
MPGVMOBJ = $(MPGOBJ_:%.o=%.asm) $(B)/missionpack/game/bg_lib.asm

$(B)/missionpack/qagame$(ARCH).$(SHLIBEXT) : $(MPGOBJ)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) $(SHLIBLDFLAGS) -o $@ $(MPGOBJ)

$(B)/missionpack/vm/qagame.qvm: $(MPGVMOBJ) $(GDIR)/g_syscalls.asm
	$(echo_cmd) "Q3ASM $@"
	$(Q)$(Q3ASM) -o $@ $(MPGVMOBJ) $(GDIR)/g_syscalls.asm



#############################################################################
## BASEQ3 UI
#############################################################################

Q3UIOBJ_ = \
  $(B)/baseq3/ui/ui_main.o \
  $(B)/baseq3/game/bg_misc.o \
  $(B)/baseq3/ui/ui_addbots.o \
  $(B)/baseq3/ui/ui_atoms.o \
  $(B)/baseq3/ui/ui_cdkey.o \
  $(B)/baseq3/ui/ui_cinematics.o \
  $(B)/baseq3/ui/ui_confirm.o \
  $(B)/baseq3/ui/ui_connect.o \
  $(B)/baseq3/ui/ui_controls2.o \
  $(B)/baseq3/ui/ui_credits.o \
  $(B)/baseq3/ui/ui_demo2.o \
  $(B)/baseq3/ui/ui_display.o \
  $(B)/baseq3/ui/ui_gameinfo.o \
  $(B)/baseq3/ui/ui_ingame.o \
  $(B)/baseq3/ui/ui_loadconfig.o \
  $(B)/baseq3/ui/ui_menu.o \
  $(B)/baseq3/ui/ui_mfield.o \
  $(B)/baseq3/ui/ui_mods.o \
  $(B)/baseq3/ui/ui_network.o \
  $(B)/baseq3/ui/ui_options.o \
  $(B)/baseq3/ui/ui_playermodel.o \
  $(B)/baseq3/ui/ui_players.o \
  $(B)/baseq3/ui/ui_playersettings.o \
  $(B)/baseq3/ui/ui_preferences.o \
  $(B)/baseq3/ui/ui_qmenu.o \
  $(B)/baseq3/ui/ui_removebots.o \
  $(B)/baseq3/ui/ui_saveconfig.o \
  $(B)/baseq3/ui/ui_serverinfo.o \
  $(B)/baseq3/ui/ui_servers2.o \
  $(B)/baseq3/ui/ui_setup.o \
  $(B)/baseq3/ui/ui_sound.o \
  $(B)/baseq3/ui/ui_sparena.o \
  $(B)/baseq3/ui/ui_specifyserver.o \
  $(B)/baseq3/ui/ui_splevel.o \
  $(B)/baseq3/ui/ui_sppostgame.o \
  $(B)/baseq3/ui/ui_spskill.o \
  $(B)/baseq3/ui/ui_startserver.o \
  $(B)/baseq3/ui/ui_team.o \
  $(B)/baseq3/ui/ui_teamorders.o \
  $(B)/baseq3/ui/ui_video.o \
  \
  $(B)/baseq3/qcommon/q_math.o \
  $(B)/baseq3/qcommon/q_shared.o

Q3UIOBJ = $(Q3UIOBJ_) $(B)/missionpack/ui/ui_syscalls.o
Q3UIVMOBJ = $(Q3UIOBJ_:%.o=%.asm) $(B)/baseq3/game/bg_lib.asm

$(B)/baseq3/ui$(ARCH).$(SHLIBEXT) : $(Q3UIOBJ)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) $(CFLAGS) $(SHLIBLDFLAGS) -o $@ $(Q3UIOBJ)

$(B)/baseq3/vm/ui.qvm: $(Q3UIVMOBJ) $(UIDIR)/ui_syscalls.asm
	$(echo_cmd) "Q3ASM $@"
	$(Q)$(Q3ASM) -o $@ $(Q3UIVMOBJ) $(UIDIR)/ui_syscalls.asm

#############################################################################
## MISSIONPACK UI
#############################################################################

MPUIOBJ_ = \
  $(B)/missionpack/ui/ui_main.o \
  $(B)/missionpack/ui/ui_atoms.o \
  $(B)/missionpack/ui/ui_gameinfo.o \
  $(B)/missionpack/ui/ui_players.o \
  $(B)/missionpack/ui/ui_shared.o \
  \
  $(B)/missionpack/game/bg_misc.o \
  \
  $(B)/missionpack/qcommon/q_math.o \
  $(B)/missionpack/qcommon/q_shared.o

MPUIOBJ = $(MPUIOBJ_) $(B)/missionpack/ui/ui_syscalls.o
MPUIVMOBJ = $(MPUIOBJ_:%.o=%.asm) $(B)/baseq3/game/bg_lib.asm

$(B)/missionpack/ui$(ARCH).$(SHLIBEXT) : $(MPUIOBJ)
	$(echo_cmd) "LD $@"
	$(Q)$(CC) $(CFLAGS) $(SHLIBLDFLAGS) -o $@ $(MPUIOBJ)

$(B)/missionpack/vm/ui.qvm: $(MPUIVMOBJ) $(UIDIR)/ui_syscalls.asm
	$(echo_cmd) "Q3ASM $@"
	$(Q)$(Q3ASM) -o $@ $(MPUIVMOBJ) $(UIDIR)/ui_syscalls.asm



#############################################################################
## CLIENT/SERVER RULES
#############################################################################

$(B)/client/%.o: $(UDIR)/%.s
	$(DO_AS)

$(B)/client/%.o: $(CDIR)/%.c
	$(DO_CC)

$(B)/client/%.o: $(SDIR)/%.c
	$(DO_CC)

$(B)/client/%.o: $(CMDIR)/%.c
	$(DO_CC)

$(B)/client/%.o: $(BLIBDIR)/%.c
	$(DO_BOT_CC)

$(B)/client/%.o: $(JPDIR)/%.c
	$(DO_CC)

$(B)/client/%.o: $(RDIR)/%.c
	$(DO_CC)

$(B)/client/%.o: $(UDIR)/%.c
	$(DO_CC)

$(B)/clientsmp/%.o: $(UDIR)/%.c
	$(DO_SMP_CC)

$(B)/client/%.o: $(W32DIR)/%.c
	$(DO_CC)

$(B)/client/%.o: $(W32DIR)/%.rc
	$(DO_WINDRES)


$(B)/ded/%.o: $(UDIR)/%.s
	$(DO_AS)

$(B)/ded/%.o: $(SDIR)/%.c
	$(DO_DED_CC)

$(B)/ded/%.o: $(CMDIR)/%.c
	$(DO_DED_CC)

$(B)/ded/%.o: $(BLIBDIR)/%.c
	$(DO_BOT_CC)

$(B)/ded/%.o: $(UDIR)/%.c
	$(DO_DED_CC)

$(B)/ded/%.o: $(NDIR)/%.c
	$(DO_DED_CC)

# Extra dependencies to ensure the SVN version is incorporated
ifeq ($(USE_SVN),1)
  $(B)/client/cl_console.o : .svn/entries
  $(B)/client/common.o : .svn/entries
  $(B)/ded/common.o : .svn/entries
endif


#############################################################################
## GAME MODULE RULES
#############################################################################

$(B)/baseq3/cgame/%.o: $(CGDIR)/%.c
	$(DO_SHLIB_CC)

$(B)/baseq3/cgame/%.asm: $(CGDIR)/%.c
	$(DO_Q3LCC)

$(B)/missionpack/cgame/%.o: $(CGDIR)/%.c
	$(DO_SHLIB_CC_MISSIONPACK)

$(B)/missionpack/cgame/%.asm: $(CGDIR)/%.c
	$(DO_Q3LCC_MISSIONPACK)


$(B)/baseq3/game/%.o: $(GDIR)/%.c
	$(DO_SHLIB_CC)

$(B)/baseq3/game/%.asm: $(GDIR)/%.c
	$(DO_Q3LCC)

$(B)/missionpack/game/%.o: $(GDIR)/%.c
	$(DO_SHLIB_CC_MISSIONPACK)

$(B)/missionpack/game/%.asm: $(GDIR)/%.c
	$(DO_Q3LCC_MISSIONPACK)


$(B)/baseq3/ui/%.o: $(Q3UIDIR)/%.c
	$(DO_SHLIB_CC)

$(B)/baseq3/ui/%.asm: $(Q3UIDIR)/%.c
	$(DO_Q3LCC)

$(B)/missionpack/ui/%.o: $(UIDIR)/%.c
	$(DO_SHLIB_CC_MISSIONPACK)

$(B)/missionpack/ui/%.asm: $(UIDIR)/%.c
	$(DO_Q3LCC_MISSIONPACK)


$(B)/baseq3/qcommon/%.o: $(CMDIR)/%.c
	$(DO_SHLIB_CC)

$(B)/baseq3/qcommon/%.asm: $(CMDIR)/%.c
	$(DO_Q3LCC)

$(B)/missionpack/qcommon/%.o: $(CMDIR)/%.c
	$(DO_SHLIB_CC_MISSIONPACK)

$(B)/missionpack/qcommon/%.asm: $(CMDIR)/%.c
	$(DO_Q3LCC_MISSIONPACK)


#############################################################################
# MISC
#############################################################################

copyfiles: release
	@if [ ! -d $(COPYDIR)/baseq3 ]; then echo "You need to set COPYDIR to where your Quake3 data is!"; fi
	-$(MKDIR) -p -m 0755 $(COPYDIR)/baseq3
	-$(MKDIR) -p -m 0755 $(COPYDIR)/missionpack

ifneq ($(BUILD_CLIENT),0)
	$(INSTALL) -s -m 0755 $(BR)/ioUrbanTerror.$(ARCH)$(BINEXT) $(COPYDIR)/ioUrbanTerror.$(ARCH)$(BINEXT)
endif

# Don't copy the SMP until it's working together with SDL.
#ifneq ($(BUILD_CLIENT_SMP),0)
#	$(INSTALL) -s -m 0755 $(BR)/ioUrbanTerror-smp.$(ARCH)$(BINEXT) $(COPYDIR)/ioUrbanTerror-smp.$(ARCH)$(BINEXT)
#endif

ifneq ($(BUILD_SERVER),0)
	@if [ -f $(BR)/ioUrTded.$(ARCH)$(BINEXT) ]; then \
		$(INSTALL) -s -m 0755 $(BR)/ioUrTded.$(ARCH)$(BINEXT) $(COPYDIR)/ioUrTded.$(ARCH)$(BINEXT); \
	fi
endif

ifneq ($(BUILD_GAME_SO),0)
	$(INSTALL) -s -m 0755 $(BR)/baseq3/cgame$(ARCH).$(SHLIBEXT) \
					$(COPYDIR)/baseq3/.
	$(INSTALL) -s -m 0755 $(BR)/baseq3/qagame$(ARCH).$(SHLIBEXT) \
					$(COPYDIR)/baseq3/.
	$(INSTALL) -s -m 0755 $(BR)/baseq3/ui$(ARCH).$(SHLIBEXT) \
					$(COPYDIR)/baseq3/.
	-$(MKDIR) -p -m 0755 $(COPYDIR)/missionpack
	$(INSTALL) -s -m 0755 $(BR)/missionpack/cgame$(ARCH).$(SHLIBEXT) \
					$(COPYDIR)/missionpack/.
	$(INSTALL) -s -m 0755 $(BR)/missionpack/qagame$(ARCH).$(SHLIBEXT) \
					$(COPYDIR)/missionpack/.
	$(INSTALL) -s -m 0755 $(BR)/missionpack/ui$(ARCH).$(SHLIBEXT) \
					$(COPYDIR)/missionpack/.
endif

clean: clean-debug clean-release
	@$(MAKE) -C $(LOKISETUPDIR) clean

clean2:
	@echo "CLEAN $(B)"
	@if [ -d $(B) ];then (find $(B) -name '*.d' -exec rm {} \;)fi
	@rm -f $(Q3OBJ) $(Q3POBJ) $(Q3POBJ_SMP) $(Q3DOBJ) \
		$(MPGOBJ) $(Q3GOBJ) $(Q3CGOBJ) $(MPCGOBJ) $(Q3UIOBJ) $(MPUIOBJ) \
		$(MPGVMOBJ) $(Q3GVMOBJ) $(Q3CGVMOBJ) $(MPCGVMOBJ) $(Q3UIVMOBJ) $(MPUIVMOBJ)
	@rm -f $(TARGETS)

clean-debug:
	@$(MAKE) clean2 B=$(BD)

clean-release:
	@$(MAKE) clean2 B=$(BR)

toolsclean:
	@$(MAKE) -C $(TOOLSDIR)/asm clean uninstall
	@$(MAKE) -C $(TOOLSDIR)/lcc clean uninstall

distclean: clean toolsclean
	@rm -rf $(BUILD_DIR)

installer: release
	@$(MAKE) VERSION=$(VERSION) -C $(LOKISETUPDIR) V=$(V)

dist:
	rm -rf ioUrbanTerror-$(SVN_VERSION)
	svn export . ioUrbanTerror-$(SVN_VERSION)
	tar --owner=root --group=root --force-local -cjf ioUrbanTerror-$(SVN_VERSION).tar.bz2 ioUrbanTerror-$(SVN_VERSION)
	rm -rf ioUrbanTerror-$(SVN_VERSION)

#############################################################################
# DEPENDENCIES
#############################################################################

D_FILES=$(shell find . -name '*.d')

ifneq ($(strip $(D_FILES)),)
  include $(D_FILES)
endif

.PHONY: all clean clean2 clean-debug clean-release copyfiles \
	debug default dist distclean installer makedirs release \
	targets tools toolsclean
```

This is my first time trying this, and i hope i can get it to compile a .exe ;) Any help is greatly appreciated.

---

### Post by johndebian on 2011-07-01
>.< bump time :)

ok i have made some progress >;/
Heres what i have done so far to get it to at least compile.


1.
```
chmod +x cross-make-mingw.sh
```
2.
```
cd ~/Desktop/ioUrbanTerrorClientSource
```
3.
```
./cross-make-mingw.sh -ik
```

And it compiles, but its not spitting out a .exe, so i guess i might be missing a package for  minGW. :(

---

### Post by adam814 on 2011-07-01
It's compiling without error but not producing an .exe?  My guess is it's making executables without the .exe extension.  I'd try running "file example" where example is any file it does produce.  If you get this it's a Windows executable and you can just rename it example.exe:

```
PE32 executable for MS Windows (GUI) Intel 80386 32-bit
```

---

### Post by johndebian on 2011-07-02
Here is the output

```
family@ubuntu:~$ cd ~/Desktop/ioUrbanTerrorClientSource/
family@ubuntu:~/Desktop/ioUrbanTerrorClientSource$ chmod +x cross-make-mingw.sh
family@ubuntu:~/Desktop/ioUrbanTerrorClientSource$ ./cross-make-mingw.sh -ikmake[1]: Entering directory `/home/family/Desktop/ioUrbanTerrorClientSource'
QVM tools not built when cross-compiling

Building ioUrbanTerror in build/release-mingw32-x86:
  PLATFORM: mingw32
  ARCH: x86
  COMPILE_PLATFORM: linux
  COMPILE_ARCH: x86_64
  CC: i586-mingw32msvc-gcc

  CFLAGS:
    -Wall
    -fno-strict-aliasing
    -Wimplicit
    -Wstrict-prototypes
    -DUSE_CURL=1
    -DCURL_STATICLIB
    -m32
    -DUSE_LOCAL_HEADERS=1
    -MMD
    -DNDEBUG
    -O3
    -march=i586
    -fomit-frame-pointer
    -ffast-math
    -falign-loops=2
    -funroll-loops
    -falign-jumps=2
    -falign-functions=2
    -fstrength-reduce

  Output:
    build/release-mingw32-x86/ioUrbanTerror.x86.exe

make[2]: Entering directory `/home/family/Desktop/ioUrbanTerrorClientSource'
CC code/client/cl_cgame.c
CC code/client/cl_cin.c
CC code/client/cl_console.c
CC code/client/cl_input.c
CC code/client/cl_keys.c
CC code/client/cl_main.c
CC code/client/cl_net_chan.c
CC code/client/cl_parse.c
CC code/client/cl_scrn.c
CC code/client/cl_ui.c
CC code/client/cl_avi.c
CC code/qcommon/cm_load.c
CC code/qcommon/cm_patch.c
CC code/qcommon/cm_polylib.c
CC code/qcommon/cm_test.c
CC code/qcommon/cm_trace.c
CC code/qcommon/cmd.c
CC code/qcommon/common.c
CC code/qcommon/cvar.c
code/qcommon/cvar.c: In function ‘Cvar_Update’:
code/qcommon/cvar.c:911: warning: unknown conversion type character ‘z’ in format
code/qcommon/cvar.c:911: warning: too many arguments for format
CC code/qcommon/files.c
CC code/qcommon/md4.c
CC code/qcommon/md5.c
CC code/qcommon/msg.c
CC code/qcommon/net_chan.c
CC code/qcommon/net_ip.c
code/qcommon/net_ip.c: In function ‘Sys_GetPacket’:
code/qcommon/net_ip.c:250: warning: pointer targets in passing argument 2 of ‘recvfrom’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/winsock.h:446: note: expected ‘char *’ but argument is of type ‘byte *’
code/qcommon/net_ip.c: In function ‘NET_OpenSocks’:
code/qcommon/net_ip.c:561: warning: pointer targets in passing argument 2 of ‘send’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/winsock.h:447: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
code/qcommon/net_ip.c:568: warning: pointer targets in passing argument 2 of ‘recv’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/winsock.h:445: note: expected ‘char *’ but argument is of type ‘unsigned char *’
code/qcommon/net_ip.c:608: warning: pointer targets in passing argument 2 of ‘send’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/winsock.h:447: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
code/qcommon/net_ip.c:615: warning: pointer targets in passing argument 2 of ‘recv’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/winsock.h:445: note: expected ‘char *’ but argument is of type ‘unsigned char *’
code/qcommon/net_ip.c:638: warning: pointer targets in passing argument 2 of ‘send’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/winsock.h:447: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
code/qcommon/net_ip.c:645: warning: pointer targets in passing argument 2 of ‘recv’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/winsock.h:445: note: expected ‘char *’ but argument is of type ‘unsigned char *’
CC code/qcommon/huffman.c
CC code/client/snd_adpcm.c
CC code/client/snd_dma.c
CC code/client/snd_mem.c
CC code/client/snd_mix.c
CC code/client/snd_wavelet.c
CC code/client/snd_main.c
CC code/client/snd_codec.c
CC code/client/snd_codec_wav.c
CC code/client/snd_codec_ogg.c
CC code/client/qal.c
CC code/client/snd_openal.c
CC code/client/cl_curl.c
CC code/server/sv_bot.c
CC code/server/sv_ccmds.c
CC code/server/sv_client.c
CC code/server/sv_game.c
CC code/server/sv_init.c
CC code/server/sv_main.c
code/server/sv_main.c: In function ‘SV_Frame’:
code/server/sv_main.c:883: warning: implicit declaration of function ‘SV_CheckClientUserinfoTimer’
CC code/server/sv_net_chan.c
CC code/server/sv_snapshot.c
code/server/sv_snapshot.c: In function ‘SV_CheckClientUserinfoTimer’:
code/server/sv_snapshot.c:719: warning: implicit declaration of function ‘SV_UpdateUserinfo_f’
CC code/server/sv_world.c
CC code/qcommon/q_math.c
CC code/qcommon/q_shared.c
CC code/qcommon/unzip.c
CC code/qcommon/puff.c
CC code/qcommon/vm.c
CC code/qcommon/vm_interpreted.c
BOT_CC code/botlib/be_aas_bspq3.c
BOT_CC code/botlib/be_aas_cluster.c
BOT_CC code/botlib/be_aas_debug.c
BOT_CC code/botlib/be_aas_entity.c
BOT_CC code/botlib/be_aas_file.c
BOT_CC code/botlib/be_aas_main.c
BOT_CC code/botlib/be_aas_move.c
BOT_CC code/botlib/be_aas_optimize.c
BOT_CC code/botlib/be_aas_reach.c
BOT_CC code/botlib/be_aas_route.c
BOT_CC code/botlib/be_aas_routealt.c
BOT_CC code/botlib/be_aas_sample.c
BOT_CC code/botlib/be_ai_char.c
BOT_CC code/botlib/be_ai_chat.c
BOT_CC code/botlib/be_ai_gen.c
BOT_CC code/botlib/be_ai_goal.c
BOT_CC code/botlib/be_ai_move.c
BOT_CC code/botlib/be_ai_weap.c
BOT_CC code/botlib/be_ai_weight.c
BOT_CC code/botlib/be_ea.c
BOT_CC code/botlib/be_interface.c
BOT_CC code/botlib/l_crc.c
BOT_CC code/botlib/l_libvar.c
BOT_CC code/botlib/l_log.c
BOT_CC code/botlib/l_memory.c
BOT_CC code/botlib/l_precomp.c
code/botlib/l_precomp.c: In function ‘PC_ExpandBuiltinDefine’:
code/botlib/l_precomp.c:744: warning: pointer targets in passing argument 1 of ‘ctime’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/time.h:100: note: expected ‘const time_t *’ but argument is of type ‘long unsigned int *’
code/botlib/l_precomp.c:759: warning: pointer targets in passing argument 1 of ‘ctime’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/time.h:100: note: expected ‘const time_t *’ but argument is of type ‘long unsigned int *’
BOT_CC code/botlib/l_script.c
BOT_CC code/botlib/l_struct.c
CC code/jpeg-6/jcapimin.c
CC code/jpeg-6/jchuff.c
CC code/jpeg-6/jcinit.c
CC code/jpeg-6/jccoefct.c
CC code/jpeg-6/jccolor.c
CC code/jpeg-6/jfdctflt.c
CC code/jpeg-6/jcdctmgr.c
CC code/jpeg-6/jcphuff.c
CC code/jpeg-6/jcmainct.c
CC code/jpeg-6/jcmarker.c
CC code/jpeg-6/jcmaster.c
CC code/jpeg-6/jcomapi.c
CC code/jpeg-6/jcparam.c
CC code/jpeg-6/jcprepct.c
CC code/jpeg-6/jcsample.c
CC code/jpeg-6/jdapimin.c
CC code/jpeg-6/jdapistd.c
CC code/jpeg-6/jdatasrc.c
CC code/jpeg-6/jdcoefct.c
CC code/jpeg-6/jdcolor.c
CC code/jpeg-6/jddctmgr.c
CC code/jpeg-6/jdhuff.c
CC code/jpeg-6/jdinput.c
CC code/jpeg-6/jdmainct.c
CC code/jpeg-6/jdmarker.c
CC code/jpeg-6/jdmaster.c
CC code/jpeg-6/jdpostct.c
CC code/jpeg-6/jdsample.c
CC code/jpeg-6/jdtrans.c
CC code/jpeg-6/jerror.c
CC code/jpeg-6/jidctflt.c
CC code/jpeg-6/jmemmgr.c
CC code/jpeg-6/jmemnobs.c
CC code/jpeg-6/jutils.c
CC code/renderer/tr_animation.c
CC code/renderer/tr_backend.c
CC code/renderer/tr_bsp.c
CC code/renderer/tr_cmds.c
CC code/renderer/tr_curve.c
CC code/renderer/tr_flares.c
CC code/renderer/tr_font.c
CC code/renderer/tr_image.c
CC code/renderer/tr_init.c
CC code/renderer/tr_light.c
CC code/renderer/tr_main.c
CC code/renderer/tr_marks.c
CC code/renderer/tr_mesh.c
CC code/renderer/tr_model.c
CC code/renderer/tr_noise.c
CC code/renderer/tr_scene.c
CC code/renderer/tr_shade.c
CC code/renderer/tr_shade_calc.c
CC code/renderer/tr_shader.c
CC code/renderer/tr_shadows.c
CC code/renderer/tr_sky.c
CC code/renderer/tr_surface.c
CC code/renderer/tr_world.c
AS code/unix/snd_mixa.s
AS code/unix/matha.s
AS code/unix/ftola.s
AS code/unix/snapvectora.s
CC code/qcommon/vm_x86.c
CC code/win32/win_gamma.c
In file included from code/win32/win_gamma.c:29:
code/win32/win_local.h:36:20: warning: dinput.h: No such file or directory
code/win32/win_local.h:37:20: warning: dsound.h: No such file or directory
CC code/win32/win_glimp.c
In file included from code/win32/win_glimp.c:42:
code/win32/win_local.h:36:20: warning: dinput.h: No such file or directory
code/win32/win_local.h:37:20: warning: dsound.h: No such file or directory
code/win32/win_glimp.c: In function ‘GLimp_Init’:
code/win32/win_glimp.c:1438: warning: pointer targets in passing argument 2 of ‘Q_strncpyz’ differ in signedness
code/win32/../renderer/../qcommon/q_shared.h:685: note: expected ‘const char *’ but argument is of type ‘const GLubyte *’
code/win32/win_glimp.c:1439: warning: pointer targets in passing argument 2 of ‘Q_strncpyz’ differ in signedness
code/win32/../renderer/../qcommon/q_shared.h:685: note: expected ‘const char *’ but argument is of type ‘const GLubyte *’
code/win32/win_glimp.c:1440: warning: pointer targets in passing argument 2 of ‘Q_strncpyz’ differ in signedness
code/win32/../renderer/../qcommon/q_shared.h:685: note: expected ‘const char *’ but argument is of type ‘const GLubyte *’
code/win32/win_glimp.c:1441: warning: pointer targets in passing argument 2 of ‘Q_strncpyz’ differ in signedness
code/win32/../renderer/../qcommon/q_shared.h:685: note: expected ‘const char *’ but argument is of type ‘const GLubyte *’
code/win32/win_glimp.c: In function ‘GLimp_SpawnRenderThread’:
code/win32/win_glimp.c:1653: warning: pointer targets in passing argument 6 of ‘CreateThread’ differ in signedness
/usr/lib/gcc/i586-mingw32msvc/4.4.4/../../../../i586-mingw32msvc/include/winbase.h:1269: note: expected ‘PDWORD’ but argument is of type ‘long int *’
CC code/win32/win_input.c
In file included from code/win32/win_input.c:26:
code/win32/win_local.h:36:20: warning: dinput.h: No such file or directory
code/win32/win_local.h:37:20: warning: dsound.h: No such file or directory
code/win32/win_input.c:211: error: expected declaration specifiers or ‘...’ before ‘LPDIRECTINPUT’
code/win32/win_input.c:225: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rgodf’
code/win32/win_input.c:238: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘df’
code/win32/win_input.c:247: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_pdi’
code/win32/win_input.c:248: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_pMouse’
code/win32/win_input.c: In function ‘IN_InitDIMouse’:
code/win32/win_input.c:260: error: ‘DIPROPDWORD’ undeclared (first use in this function)
code/win32/win_input.c:260: error: (Each undeclared identifier is reported only once
code/win32/win_input.c:260: error: for each function it appears in.)
code/win32/win_input.c:260: error: expected ‘;’ before ‘dipdw’
code/win32/win_input.c:282: error: expected declaration specifiers or ‘...’ before ‘LPDIRECTINPUT’
code/win32/win_input.c:292: error: ‘g_pdi’ undeclared (first use in this function)
code/win32/win_input.c:292: error: too many arguments to function ‘pDirectInputCreate’
code/win32/win_input.c:300: warning: implicit declaration of function ‘IDirectInput_CreateDevice’
code/win32/win_input.c:300: error: ‘g_pMouse’ undeclared (first use in this function)
code/win32/win_input.c:308: warning: implicit declaration of function ‘IDirectInputDevice_SetDataFormat’
code/win32/win_input.c:308: error: ‘df’ undeclared (first use in this function)
code/win32/win_input.c:316: warning: implicit declaration of function ‘IDirectInputDevice_SetCooperativeLevel’
code/win32/win_input.c:317: error: ‘DISCL_EXCLUSIVE’ undeclared (first use in this function)
code/win32/win_input.c:317: error: ‘DISCL_FOREGROUND’ undeclared (first use in this function)
code/win32/win_input.c:328: warning: implicit declaration of function ‘IDirectInputDevice_SetProperty’
code/win32/win_input.c:328: error: ‘DIPROP_BUFFERSIZE’ undeclared (first use in this function)
code/win32/win_input.c:328: error: ‘dipdw’ undeclared (first use in this function)
code/win32/win_input.c: In function ‘IN_ShutdownDIMouse’:
code/win32/win_input.c:349: error: ‘g_pMouse’ undeclared (first use in this function)
code/win32/win_input.c:350: warning: implicit declaration of function ‘IDirectInputDevice_Release’
code/win32/win_input.c:354: error: ‘g_pdi’ undeclared (first use in this function)
code/win32/win_input.c:355: warning: implicit declaration of function ‘IDirectInput_Release’
code/win32/win_input.c: In function ‘IN_ActivateDIMouse’:
code/win32/win_input.c:368: error: ‘g_pMouse’ undeclared (first use in this function)
code/win32/win_input.c:373: warning: implicit declaration of function ‘IDirectInputDevice_Acquire’
code/win32/win_input.c: In function ‘IN_DeactivateDIMouse’:
code/win32/win_input.c:388: error: ‘g_pMouse’ undeclared (first use in this function)
code/win32/win_input.c:391: warning: implicit declaration of function ‘IDirectInputDevice_Unacquire’
code/win32/win_input.c: In function ‘IN_DIMouse’:
code/win32/win_input.c:401: error: ‘DIDEVICEOBJECTDATA’ undeclared (first use in this function)
code/win32/win_input.c:401: error: expected ‘;’ before ‘od’
code/win32/win_input.c:402: error: ‘DIMOUSESTATE’ undeclared (first use in this function)
code/win32/win_input.c:402: error: expected ‘;’ before ‘state’
code/win32/win_input.c:407: error: ‘g_pMouse’ undeclared (first use in this function)
code/win32/win_input.c:416: warning: implicit declaration of function ‘IDirectInputDevice_GetDeviceData’
code/win32/win_input.c:417: error: ‘od’ undeclared (first use in this function)
code/win32/win_input.c:418: error: ‘DIERR_INPUTLOST’ undeclared (first use in this function)
code/win32/win_input.c:418: error: ‘DIERR_NOTACQUIRED’ undeclared (first use in this function)
code/win32/win_input.c:433: error: ‘DIMOFS_BUTTON0’ undeclared (first use in this function)
code/win32/win_input.c:440: error: ‘DIMOFS_BUTTON1’ undeclared (first use in this function)
code/win32/win_input.c:447: error: ‘DIMOFS_BUTTON2’ undeclared (first use in this function)
code/win32/win_input.c:454: error: ‘DIMOFS_BUTTON3’ undeclared (first use in this function)
code/win32/win_input.c:461: error: ‘DIMOFS_Z’ undeclared (first use in this function)
code/win32/win_input.c:478: warning: implicit declaration of function ‘IDirectInputDevice_GetDeviceState’
code/win32/win_input.c:479: error: ‘state’ undeclared (first use in this function)
code/win32/win_input.c: In function ‘IN_MouseMove’:
code/win32/win_input.c:631: error: ‘g_pMouse’ undeclared (first use in this function)
make[2]: [build/release-mingw32-x86/client/win_input.o] Error 1 (ignored)
CC code/win32/win_main.c
In file included from code/win32/win_main.c:26:
code/win32/win_local.h:36:20: warning: dinput.h: No such file or directory
code/win32/win_local.h:37:20: warning: dsound.h: No such file or directory
CC code/win32/win_qgl.c
CC code/win32/win_shared.c
In file included from code/win32/win_shared.c:25:
code/win32/win_local.h:36:20: warning: dinput.h: No such file or directory
code/win32/win_local.h:37:20: warning: dsound.h: No such file or directory
CC code/win32/win_snd.c
In file included from code/win32/win_snd.c:25:
code/win32/win_local.h:36:20: warning: dinput.h: No such file or directory
code/win32/win_local.h:37:20: warning: dsound.h: No such file or directory
code/win32/win_snd.c:27: error: expected declaration specifiers or ‘...’ before ‘LPDIRECTSOUND’
code/win32/win_snd.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pDS’
code/win32/win_snd.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pDSBuf’
code/win32/win_snd.c: In function ‘DSoundError’:
code/win32/win_snd.c:44: error: ‘DSERR_BUFFERLOST’ undeclared (first use in this function)
code/win32/win_snd.c:44: error: (Each undeclared identifier is reported only once
code/win32/win_snd.c:44: error: for each function it appears in.)
code/win32/win_snd.c:46: error: ‘DSERR_INVALIDCALL’ undeclared (first use in this function)
code/win32/win_snd.c:48: error: ‘DSERR_INVALIDPARAM’ undeclared (first use in this function)
code/win32/win_snd.c:50: error: ‘DSERR_PRIOLEVELNEEDED’ undeclared (first use in this function)
code/win32/win_snd.c: In function ‘SNDDMA_Shutdown’:
code/win32/win_snd.c:65: error: ‘pDS’ undeclared (first use in this function)
code/win32/win_snd.c:70: error: ‘DSSCL_PRIORITY’ undeclared (first use in this function)
code/win32/win_snd.c:73: error: ‘pDSBuf’ undeclared (first use in this function)
code/win32/win_snd.c:81: error: ‘pDSPBuf’ undeclared (first use in this function)
code/win32/win_snd.c: In function ‘SNDDMA_InitDS’:
code/win32/win_snd.c:154: error: ‘DSBUFFERDESC’ undeclared (first use in this function)
code/win32/win_snd.c:154: error: expected ‘;’ before ‘dsbuf’
code/win32/win_snd.c:155: error: ‘DSBCAPS’ undeclared (first use in this function)
code/win32/win_snd.c:155: error: expected ‘;’ before ‘dsbcaps’
code/win32/win_snd.c:163: error: ‘pDS’ undeclared (first use in this function)
code/win32/win_snd.c:178: error: ‘DS_OK’ undeclared (first use in this function)
code/win32/win_snd.c:178: error: ‘DSSCL_PRIORITY’ undeclared (first use in this function)
code/win32/win_snd.c:207: error: ‘dsbuf’ undeclared (first use in this function)
code/win32/win_snd.c:211: error: ‘DSBCAPS_LOCHARDWARE’ undeclared (first use in this function)
code/win32/win_snd.c:213: error: ‘DSBCAPS_GETCURRENTPOSITION2’ undeclared (first use in this function)
code/win32/win_snd.c:218: error: ‘dsbcaps’ undeclared (first use in this function)
code/win32/win_snd.c:222: error: ‘pDSBuf’ undeclared (first use in this function)
code/win32/win_snd.c:227: error: ‘DSBCAPS_LOCSOFTWARE’ undeclared (first use in this function)
code/win32/win_snd.c:240: error: ‘DSBPLAY_LOOPING’ undeclared (first use in this function)
code/win32/win_snd.c: In function ‘SNDDMA_GetDMAPos’:
code/win32/win_snd.c:289: error: ‘pDSBuf’ undeclared (first use in this function)
code/win32/win_snd.c: In function ‘SNDDMA_BeginPainting’:
code/win32/win_snd.c:314: error: ‘pDSBuf’ undeclared (first use in this function)
code/win32/win_snd.c:319: error: ‘DS_OK’ undeclared (first use in this function)
code/win32/win_snd.c:323: error: ‘DSBSTATUS_BUFFERLOST’ undeclared (first use in this function)
code/win32/win_snd.c:326: error: ‘DSBSTATUS_PLAYING’ undeclared (first use in this function)
code/win32/win_snd.c:327: error: ‘DSBPLAY_LOOPING’ undeclared (first use in this function)
code/win32/win_snd.c:337: error: ‘DSERR_BUFFERLOST’ undeclared (first use in this function)
code/win32/win_snd.c: In function ‘SNDDMA_Submit’:
code/win32/win_snd.c:364: error: ‘pDSBuf’ undeclared (first use in this function)
code/win32/win_snd.c: In function ‘SNDDMA_Activate’:
code/win32/win_snd.c:378: error: ‘pDS’ undeclared (first use in this function)
code/win32/win_snd.c:382: error: ‘DS_OK’ undeclared (first use in this function)
code/win32/win_snd.c:382: error: ‘DSSCL_PRIORITY’ undeclared (first use in this function)
make[2]: [build/release-mingw32-x86/client/win_snd.o] Error 1 (ignored)
CC code/win32/win_syscon.c
In file included from code/win32/win_syscon.c:24:
code/win32/win_local.h:36:20: warning: dinput.h: No such file or directory
code/win32/win_local.h:37:20: warning: dsound.h: No such file or directory
CC code/win32/win_wndproc.c
In file included from code/win32/win_wndproc.c:24:
code/win32/win_local.h:36:20: warning: dinput.h: No such file or directory
code/win32/win_local.h:37:20: warning: dsound.h: No such file or directory
WINDRES code/win32/win_resource.rc
LD build/release-mingw32-x86/ioUrbanTerror.x86.exe
i586-mingw32msvc-gcc: build/release-mingw32-x86/client/win_input.o: No such file or directory
i586-mingw32msvc-gcc: build/release-mingw32-x86/client/win_snd.o: No such file or directory
make[2]: [build/release-mingw32-x86/ioUrbanTerror.x86.exe] Error 1 (ignored)
make[2]: Leaving directory `/home/family/Desktop/ioUrbanTerrorClientSource'
make[1]: Leaving directory `/home/family/Desktop/ioUrbanTerrorClientSource'
family@ubuntu:~/Desktop/ioUrbanTerrorClientSource$ 

```

---

### Post by johndebian on 2011-08-16
Super Bump!!!
Still haven't figured this one out.

:popcorn:

---

