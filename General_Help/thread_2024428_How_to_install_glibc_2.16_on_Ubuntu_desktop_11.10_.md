---
title: "How to install glibc 2.16 on Ubuntu desktop 11.10 x64"
date: 2012-07-13
forum: General Help
---

### Post by newmore on 2012-07-13
Hi,

I downloaded glibc 2.16 on [http://ftp.gnu.org/gnu/libc/glibc-2.16.0.tar.gz](http://ftp.gnu.org/gnu/libc/glibc-2.16.0.tar.gz) and untar into /home/user1. I tried to following steps to install glibc, but I can't install it successfully. Please help! 

Steps to install glibc 2.16


user1@ubuntu:~/glibc-2.16$ **mkdir -v ../glibc_build**
mkdir: created directory `../glibc_build'
user1@ubuntu:~/glibc-2.16$ **cd ../glibc_build/**
user1@ubuntu:~/glibc_build$ **../glibc-2.16/configure**
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
configure: running configure fragment for add-on libidn
configure: running configure fragment for add-on nptl
checking for assembler gnu_indirect_function symbol type support... yes
checking whether .text pseudo-op must be used... yes
checking for assembler global-symbol directive... .globl
checking for assembler .type directive prefix... @
checking sysdep dirs... sysdeps/x86_64/elf nptl/sysdeps/unix/sysv/linux/x86_64 sysdeps/unix/sysv/linux/x86_64 sysdeps/unix/sysv/linux/wordsize-64 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet nptl/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/x86_64 nptl/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/x86_64/fpu/multiarch sysdeps/x86_64/fpu sysdeps/x86_64/multiarch nptl/sysdeps/x86_64 sysdeps/x86_64 sysdeps/wordsize-64 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64/wordsize-64 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether as is GNU as... yes
checking whether ld is GNU ld... yes
checking for as... as
checking version of as... 2.21.53.20110810, ok
checking for ld... ld
checking version of ld... 2.21.53.20110810, ok
checking for pwd... /bin/pwd
checking for gcc... gcc
checking version of gcc... 4.6.1, ok
checking for gnumake... no
checking for gmake... no
checking for make... make
checking version of make... 3.81, ok
checking for gnumsgfmt... no
checking for gmsgfmt... no
checking for msgfmt... no
checking for makeinfo... no
checking for sed... sed
checking version of sed... 4.2.1, ok
checking for readelf... readelf
checking for autoconf... no
configure: WARNING:
*** These auxiliary programs are missing or incompatible versions: msgfmt makeinfo autoconf
*** some features will be disabled.
*** Check the INSTALL file for required versions.
checking LD_LIBRARY_PATH variable... ok
checking whether GCC supports -static-libgcc... -static-libgcc
checking for bash... /bin/bash
checking for gawk... no
checking for mawk... mawk
checking for perl... /usr/bin/perl
checking for install-info... /usr/sbin/install-info
checking for bison... no
checking for signed size_t type... no
checking for libc-friendly stddef.h... yes
checking whether we need to use -P to assemble .S files... no
checking for .set assembler directive... yes
checking for assembler gnu_unique_object symbol type... yes
checking for .symver assembler directive... yes
checking for ld --version-script... yes
checking for .previous assembler directive... yes
checking for .protected and .hidden assembler directive... yes
checking whether __attribute__((visibility())) is supported... yes
checking for broken __attribute__((visibility()))... no
checking for broken __attribute__((alias()))... no
checking whether to put _rtld_local into .sdata section... no
checking for .preinit_array/.init_array/.fini_array support... yes
checking whether to use .ctors/.dtors header and trailer... mawk: line 15: function strtonum never defined
mawk: line 15: function strtonum never defined
yes
checking for libunwind-support in compiler... no
checking for -z nodelete option... yes
checking for -z nodlopen option... yes
checking for -z initfirst option... yes
checking for -z relro option... no
configure: error: linker with -z relro support required

---

### Post by Rexilion on 2012-07-14
Binutils should support this, could you post your config.log?

---

### Post by elliotn on 2012-07-14
you should use synaptic and generate download package script so u can get all the dependencies and ease of compiling

---

### Post by newmore on 2012-07-16
> **Rexilion said:**
> Binutils should support this, could you post your config.log?

```
config.log

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by GNU C Library configure (see version.h), which was
generated by GNU Autoconf 2.68.  Invocation command line was

  $ ../glibc-2.15/configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = user1
uname -m = x86_64
uname -r = 3.0.0-12-generic
uname -s = Linux
uname -v = #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/lib/lightdm/lightdm
PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2367: checking build system type
configure:2381: result: x86_64-unknown-linux-gnu
configure:2401: checking host system type
configure:2414: result: x86_64-unknown-linux-gnu
configure:2483: checking for gcc
configure:2499: found /usr/bin/gcc
configure:2510: result: gcc
configure:2739: checking for C compiler version
configure:2748: gcc --version >&5
gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2759: $? = 0
configure:2748: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.6.1/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
configure:2759: $? = 0
configure:2748: gcc -V >&5
gcc: error: unrecognized option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:2759: $? = 4
configure:2748: gcc -qversion >&5
gcc: error: unrecognized option '-qversion'
gcc: fatal error: no input files
compilation terminated.
configure:2759: $? = 4
configure:2764: checking for suffix of object files
configure:2786: gcc -c   conftest.c >&5
configure:2790: $? = 0
configure:2811: result: o
configure:2815: checking whether we are using the GNU C compiler
configure:2834: gcc -c   conftest.c >&5
configure:2834: $? = 0
configure:2843: result: yes
configure:2852: checking whether gcc accepts -g
configure:2872: gcc -c -g  conftest.c >&5
configure:2872: $? = 0
configure:2913: result: yes
configure:2930: checking for gcc option to accept ISO C89
configure:2994: gcc  -c -g -O2  conftest.c >&5
configure:2994: $? = 0
configure:3007: result: none needed
configure:3077: checking how to run the C preprocessor
configure:3108: gcc -E  conftest.c
configure:3108: $? = 0
configure:3122: gcc -E  conftest.c
conftest.c:9:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
configure:3122: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "glibc"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "http://sourceware.org/bugzilla/"
| #define PACKAGE_URL "http://www.gnu.org/software/glibc/"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3147: result: gcc -E
configure:3167: gcc -E  conftest.c
configure:3167: $? = 0
configure:3181: gcc -E  conftest.c
conftest.c:9:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
configure:3181: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "glibc"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "http://sourceware.org/bugzilla/"
| #define PACKAGE_URL "http://www.gnu.org/software/glibc/"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3268: checking for g++
configure:3284: found /usr/bin/g++
configure:3295: result: g++
configure:3322: checking for C++ compiler version
configure:3331: g++ --version >&5
g++ (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3342: $? = 0
configure:3331: g++ -v >&5
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.6.1/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
configure:3342: $? = 0
configure:3331: g++ -V >&5
g++: error: unrecognized option '-V'
g++: fatal error: no input files
compilation terminated.
configure:3342: $? = 4
configure:3331: g++ -qversion >&5
g++: error: unrecognized option '-qversion'
g++: fatal error: no input files
compilation terminated.
configure:3342: $? = 4
configure:3346: checking whether we are using the GNU C++ compiler
configure:3365: g++ -c   conftest.cpp >&5
configure:3365: $? = 0
configure:3374: result: yes
configure:3383: checking whether g++ accepts -g
configure:3403: g++ -c -g  conftest.cpp >&5
configure:3403: $? = 0
configure:3444: result: yes
configure:3949: running configure fragment for add-on libidn
configure:3949: running configure fragment for add-on nptl
configure:4091: checking for assembler gnu_indirect_function symbol type support
configure:4107: result: yes
configure:4110: checking whether .text pseudo-op must be used
configure:4120: gcc  -c conftest.s 1>&5
configure:4123: $? = 0
configure:4134: result: yes
configure:4138: checking for assembler global-symbol directive
configure:4151: gcc  -c conftest.s 1>&5
configure:4154: $? = 0
configure:4162: result: .globl
configure:4173: checking for assembler .type directive prefix
configure:4189: gcc  -c conftest.s 1>&5
configure:4192: $? = 0
configure:4200: result: @
configure:4223: checking sysdep dirs
configure:4468: result: sysdeps/generic/elf sysdeps/generic
configure:4545: checking for a BSD-compatible install
configure:4613: result: /usr/bin/install -c
configure:4628: checking whether ln -s works
configure:4632: result: yes
configure:4656: checking whether as is GNU as
configure:4670: result: yes
configure:4675: checking whether ld is GNU ld
configure:4689: result: yes
configure:4699: checking for as
configure:4726: result: as
configure:4741: checking version of as
configure:4751: result: 2.21.53.20110810, ok
configure:4762: checking for ld
configure:4789: result: ld
configure:4804: checking version of ld
configure:4814: result: 2.21.53.20110810, ok
configure:4829: checking for pwd
configure:4847: found /bin/pwd
configure:4860: result: /bin/pwd
configure:4878: checking for gcc
configure:4905: result: gcc
configure:4920: checking version of gcc
configure:4930: result: 4.6.1, ok
configure:4941: checking for gnumake
configure:4971: result: no
configure:4941: checking for gmake
configure:4971: result: no
configure:4941: checking for make
configure:4957: found /usr/bin/make
configure:4968: result: make
configure:4983: checking version of make
configure:4993: result: 3.81, ok
configure:5005: checking for gnumsgfmt
configure:5035: result: no
configure:5005: checking for gmsgfmt
configure:5035: result: no
configure:5005: checking for msgfmt
configure:5035: result: no
configure:5068: checking for makeinfo
configure:5098: result: no
configure:5131: checking for sed
configure:5147: found /bin/sed
configure:5158: result: sed
configure:5173: checking version of sed
configure:5183: result: 4.2.1, ok
configure:5234: checking for readelf
configure:5250: found /usr/bin/readelf
configure:5261: result: readelf
configure:5288: checking for autoconf
configure:5318: result: no
configure:5357: WARNING:
*** These auxiliary programs are missing or incompatible versions: msgfmt makeinfo autoconf
*** some features will be disabled.
*** Check the INSTALL file for required versions.
configure:5400: checking LD_LIBRARY_PATH variable
configure:5410: result: ok
configure:5419: checking whether GCC supports -static-libgcc
configure:5430: result: -static-libgcc
configure:5436: checking for bash
configure:5454: found /bin/bash
configure:5467: result: /bin/bash
configure:5542: checking for gawk
configure:5572: result: no
configure:5542: checking for mawk
configure:5558: found /usr/bin/mawk
configure:5569: result: mawk
configure:5582: checking for perl
configure:5600: found /usr/bin/perl
configure:5613: result: /usr/bin/perl
configure:5627: checking for install-info
configure:5646: found /usr/sbin/install-info
configure:5659: result: /usr/sbin/install-info
configure:5669: checking for bison
configure:5701: result: no
configure:5710: checking for signed size_t type
configure:5725: result: no
configure:5734: checking for libc-friendly stddef.h
configure:5758: gcc -c -g -O2  conftest.c >&5
conftest.c: In function 'main':
conftest.c:25:38: warning: incompatible implicit declaration of built-in function 'abort' [enabled by default]
configure:5758: $? = 0
configure:5765: result: yes
configure:5772: checking whether we need to use -P to assemble .S files
configure:5782: gcc   -c conftest.S 1>&5
configure:5785: $? = 0
configure:5793: result: no
configure:5800: checking for .set assembler directive
configure:5826: result: yes
configure:5833: checking for assembler gnu_unique_object symbol type
configure:5850: result: yes
configure:5857: checking for .symver assembler directive
configure:5874: result: yes
configure:5876: checking for ld --version-script
configure:5902: gcc -g -O2  -shared
				-o conftest.so conftest.o
				-nostartfiles -nostdlib
				-Wl,--version-script,conftest.map
		       1>&5
configure:5905: $? = 0
configure:5920: result: yes
configure:5942: checking for .previous assembler directive
configure:5952: gcc -c  conftest.s 1>&5
configure:5955: $? = 0
configure:5963: result: yes
configure:5997: checking for .protected and .hidden assembler directive
configure:6009: gcc -c  conftest.s 1>&5
configure:6012: $? = 0
configure:6020: result: yes
configure:6024: checking whether __attribute__((visibility())) is supported
configure:6035: gcc -Werror -S conftest.c -o conftest.s 1>&5
configure:6038: $? = 0
configure:6049: result: yes
configure:6057: checking for broken __attribute__((visibility()))
configure:6069: gcc -Werror -S conftest.c -o conftest.s 1>&5
configure:6072: $? = 0
configure:6081: result: no
configure:6088: checking for broken __attribute__((alias()))
configure:6103: gcc -Werror -S conftest.c -o conftest.s 1>&5
configure:6106: $? = 0
configure:6116: result: no
configure:6123: checking whether to put _rtld_local into .sdata section
configure:6137: result: no
configure:6145: checking for .preinit_array/.init_array/.fini_array support
configure:6158: gcc -g -O2   -o conftest conftest.c
		     -static -nostartfiles -nostdlib 1>&5
configure:6161: $? = 0
configure:6174: result: yes
configure:6180: checking whether to use .ctors/.dtors header and trailer
configure:6200: gcc -o conftest -g -O2   conftest.c  >&5
configure:6200: $? = 0
configure:6226: result: yes
configure:6233: checking for libunwind-support in compiler
configure:6250: result: no
configure:6258: checking for -z nodelete option
configure:6270: gcc -g -O2  
		     -fPIC -shared -o conftest.so conftest.c
		     -nostartfiles -nostdlib
		     -Wl,--enable-new-dtags,-z,nodelete 1>&5
configure:6273: $? = 0
configure:6282: result: yes
configure:6285: checking for -z nodlopen option
configure:6297: gcc -g -O2  
			-fPIC -shared -o conftest.so conftest.c
			-nostartfiles -nostdlib
			-Wl,--enable-new-dtags,-z,nodlopen 1>&5
configure:6300: $? = 0
configure:6309: result: yes
configure:6312: checking for -z initfirst option
configure:6324: gcc -g -O2  
			-fPIC -shared -o conftest.so conftest.c
			-nostartfiles -nostdlib
			-Wl,--enable-new-dtags,-z,initfirst 1>&5
configure:6327: $? = 0
configure:6336: result: yes
configure:6361: checking for -z relro option
configure:6402: gcc -g -O2  
		    -fPIC -shared -o conftest.so conftest.c
		    -nostartfiles -nostdlib
		    -Wl,-z,relro 1>&5
configure:6405: $? = 0
configure:6408: readelf -Wl conftest.so > conftest.ph
configure:6411: $? = 0
configure:6417: 
      mawk -v commonpagesize=0x1000 -f conftest.awk
	   conftest.ph > conftest.cps
    
mawk: conftest.awk: line 16: function strtonum never defined
mawk: conftest.awk: line 16: function strtonum never defined
mawk: conftest.awk: line 16: function strtonum never defined
configure:6420: $? = 2
configure:6425: result: no
configure:6431: error: linker with -z relro support required

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=x86_64-unknown-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=x86_64-unknown-linux-gnu
ac_cv_objext=o
ac_cv_path_BASH_SHELL=/bin/bash
ac_cv_path_BISON=no
ac_cv_path_INSTALL_INFO=/usr/sbin/install-info
ac_cv_path_PERL=/usr/bin/perl
ac_cv_path_PWD_P=/bin/pwd
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AS=as
ac_cv_prog_AWK=mawk
ac_cv_prog_CC=gcc
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_LD=ld
ac_cv_prog_MAKE=make
ac_cv_prog_SED=sed
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_ac_ct_READELF=readelf
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_cxx_g=yes
libc_cv_asm_global_directive=.globl
libc_cv_asm_gnu_indirect_function=yes
libc_cv_asm_previous_directive=yes
libc_cv_asm_protected_directive=yes
libc_cv_asm_set_directive=yes
libc_cv_asm_symver_directive=yes
libc_cv_asm_type_prefix=@
libc_cv_asm_unique_object=yes
libc_cv_broken_alias_attribute=no
libc_cv_broken_visibility_attribute=no
libc_cv_cc_with_libunwind=no
libc_cv_ctors_header=yes
libc_cv_dot_text=.text
libc_cv_friendly_stddef=yes
libc_cv_gcc_static_libgcc=-static-libgcc
libc_cv_have_bash2=yes
libc_cv_have_ksh=yes
libc_cv_have_sdata_section=no
libc_cv_initfini_array=yes
libc_cv_ld_version_script_option=yes
libc_cv_need_minus_P=no
libc_cv_nss_crypt=no
libc_cv_prog_as_gnu=yes
libc_cv_prog_ld_gnu=yes
libc_cv_signed_size_t=no
libc_cv_visibility_attribute=yes
libc_cv_z_initfirst=yes
libc_cv_z_nodelete=yes
libc_cv_z_nodlopen=yes
libc_cv_z_relro=no

## ----------------- ##
## Output variables. ##
## ----------------- ##

AR='ar'
AS='as'
ASFLAGS_config=''
AUTOCONF='no'
AWK='mawk'
BASH_SHELL='/bin/bash'
BISON='no'
BUILD_CC=''
CC='gcc'
CFLAGS='-g -O2'
CPP='gcc -E'
CPPFLAGS=''
CXX='g++'
CXXFLAGS='-g -O2'
CXX_SYSINCLUDES=''
DEFINES=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
GREP=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_INFO='/usr/sbin/install-info'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
KSH='/bin/bash'
LD='ld'
LDFLAGS=''
LIBGD=''
LIBOBJS=''
LIBS=''
LN_S='ln -s'
LTLIBOBJS=''
MAKE='make'
MAKEINFO=':'
MIG=''
MSGFMT=':'
OBJCOPY='objcopy'
OBJDUMP='objdump'
OBJEXT='o'
PACKAGE_BUGREPORT='http://sourceware.org/bugzilla/'
PACKAGE_NAME='GNU C Library'
PACKAGE_STRING='GNU C Library (see version.h)'
PACKAGE_TARNAME='glibc'
PACKAGE_URL='http://www.gnu.org/software/glibc/'
PACKAGE_VERSION='(see version.h)'
PATH_SEPARATOR=':'
PERL='/usr/bin/perl'
PWD_P='/bin/pwd'
READELF='readelf'
RELEASE=''
SED='sed'
SHELL='/bin/bash'
SYSINCLUDES=''
VERSION=''
VERSIONING='yes'
ac_ct_CC='gcc'
ac_ct_CXX='g++'
add_on_subdirs=' libidn'
add_ons='libidn nptl'
all_warnings=''
base_machine='x86_64'
bindir='${exec_prefix}/bin'
bindnow='no'
bounded='no'
build='x86_64-unknown-linux-gnu'
build_alias=''
build_cpu='x86_64'
build_os='linux-gnu'
build_vendor='unknown'
cross_compiling='no'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
elf='yes'
enable_check_abi='no'
exceptions=''
exec_prefix='NONE'
fno_unit_at_a_time=''
force_install='yes'
gnu89_inline=''
have_libaudit=''
have_libcap=''
have_selinux=''
host='x86_64-unknown-linux-gnu'
host_alias=''
host_cpu='x86_64'
host_os='linux-gnu'
host_vendor='unknown'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
ldd_rewrite_script=''
libc_cv_Bgroup=''
libc_cv_as_i686=''
libc_cv_as_needed=''
libc_cv_cc_avx=''
libc_cv_cc_fma4=''
libc_cv_cc_novzeroupper=''
libc_cv_cc_sse4=''
libc_cv_cc_submachine=''
libc_cv_cc_with_libunwind='no'
libc_cv_cpp_asm_debuginfo=''
libc_cv_forced_unwind=''
libc_cv_fpie=''
libc_cv_gcc_static_libgcc='-static-libgcc'
libc_cv_gcc_unwind_find_fde=''
libc_cv_hashstyle=''
libc_cv_have_bash2='yes'
libc_cv_have_initfini=''
libc_cv_have_ksh='yes'
libc_cv_libgcc_s_suffix=''
libc_cv_localedir=''
libc_cv_nss_crypt='no'
libc_cv_output_format=''
libc_cv_pic_default=''
libc_cv_rootsbindir=''
libc_cv_slibdir=''
libc_cv_ssp=''
libc_cv_sysconfdir=''
libc_cv_z_combreloc=''
libc_cv_z_execstack=''
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mach_interface_list=''
mandir='${datarootdir}/man'
multi_arch='default'
nopic_initfini=''
old_glibc_headers=''
oldest_abi='default'
oldincludedir='/usr/include'
omitfp='no'
pdfdir='${docdir}'
prefix='NONE'
profile='no'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
shared='default'
sharedstatedir='${prefix}/com'
sizeof_long_double=''
static='yes'
static_nss='no'
subdirs='  '
submachine=''
sysconfdir='${prefix}/etc'
sysdeps_add_ons=' nptl'
sysnames=' sysdeps/x86_64/elf nptl/sysdeps/unix/sysv/linux/x86_64 sysdeps/unix/sysv/linux/x86_64 sysdeps/unix/sysv/linux/wordsize-64 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet nptl/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/x86_64 nptl/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/x86_64/fpu/multiarch sysdeps/x86_64/fpu sysdeps/x86_64/multiarch nptl/sysdeps/x86_64 sysdeps/x86_64 sysdeps/wordsize-64 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64/wordsize-64 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic'
target_alias=''
use_default_link='default'
use_ldconfig=''
with_fp='yes'
xcoff='no'

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME "GNU C Library"
#define PACKAGE_TARNAME "glibc"
#define PACKAGE_VERSION "(see version.h)"
#define PACKAGE_STRING "GNU C Library (see version.h)"
#define PACKAGE_BUGREPORT "http://sourceware.org/bugzilla/"
#define PACKAGE_URL "http://www.gnu.org/software/glibc/"
#define HAVE_LIBIDN 1
#define ASM_GLOBAL_DIRECTIVE .globl
#define ASM_TYPE_DIRECTIVE_PREFIX @
#define USE_MULTIARCH 1
#define HAVE_ASM_SET_DIRECTIVE 1
#define HAVE_ASM_UNIQUE_OBJECT 1
#define DO_VERSIONING 1
#define HAVE_ASM_PREVIOUS_DIRECTIVE 1

configure: exit 1
```

---

### Post by Rexilion on 2012-08-25
> **newmore said:**
> config.log

configure:6431: error: linker with -z relro support required

configure: exit 1

There is your error. Maybe [this]("http://sourceware.org/ml/libc-help/2011-08/msg00043.html") might give a pointer.

---

### Post by vagran on 2012-08-30
Seems glibc has poor support for mawk. 'gawk' installing fixes the problem:
```
sudo apt-get install gawk
```

---

