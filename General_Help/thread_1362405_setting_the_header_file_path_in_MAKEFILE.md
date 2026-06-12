---
title: "setting the header file path in MAKEFILE"
date: 2009-12-23
forum: General Help
---

### Post by shariefbe on 2009-12-23
Hello,
   I am trying to compile the gstreamer. for that i tries make to compile and i got some error. That error shows that it didnt find the correct header file where it searches for header file. now how to change that searching path in 'Makefile"

errors are ```

dec_la-mfw_gst_aacdec.o
mfw_gst_aacdec.c:52:32: error: aacd_dec_interface.h: No such file or directory
In file included from mfw_gst_aacdec.c:53:
mfw_gst_aacdec.h:96: error: expected specifier-qualifier-list before 'AACD_Block_Params'
mfw_gst_aacdec.c:113: error: 'AACD_INPUT_BUFFER_SIZE' undeclared here (not in a function)
mfw_gst_aacdec.c:117: error: 'INTERNAL_BS_BUFSIZE' undeclared here (not in a function)
mfw_gst_aacdec.c:161: error: expected ')' before '*' token
mfw_gst_aacdec.c:170: error: expected ')' before '*' token
mfw_gst_aacdec.c:172: error: expected ')' before '*' token
mfw_gst_aacdec.c:173: error: expected ')' before '*' token
mfw_gst_aacdec.c:174: error: expected ')' before '*' token
mfw_gst_aacdec.c: In function 'App_FindFileType':
mfw_gst_aacdec.c:240: error: 'AACD_App_params' has no member named 'App_adif_header_present'
mfw_gst_aacdec.c:245: error: 'AACD_App_params' has no member named 'App_adts_header_present'
mfw_gst_aacdec.c: At top level:
mfw_gst_aacdec.c:253: error: expected ')' before '*' token
mfw_gst_aacdec.c: In function 'App_bs_readinit':
mfw_gst_aacdec.c:359: error: 'BIT_COUNTER_INIT' undeclared (first use in this function)
mfw_gst_aacdec.c:359: error: (Each undeclared identifier is reported only once
mfw_gst_aacdec.c:359: error: for each function it appears in.)
mfw_gst_aacdec.c: In function 'App_bs_read_bits':
mfw_gst_aacdec.c:399: error: 'AACD_App_params' has no member named 'BitsInHeader'
mfw_gst_aacdec.c:408: error: 'MIN_REQD_BITS' undeclared (first use in this function)
mfw_gst_aacdec.c: In function 'App_bs_byte_align':
mfw_gst_aacdec.c:461: error: 'MIN_REQD_BITS' undeclared (first use in this function)
mfw_gst_aacdec.c:464: error: 'AACD_App_params' has no member named 'BitsInHeader'
mfw_gst_aacdec.c: At top level:

```

But the header file are in the location of ```

root@ariem-desktop:/gst-fsl-plugin-1.6.0/src# find /home/ -iname "aacd_dec_interface.h"
/home/ariem/Desktop/plugins/fsl_linux_sdk_codecs_1.6.0_1/fsl-mm-codeclib-1.6.0/ghdr/aacd_dec_interface.h
root@ariem-desktop:/gst-fsl-plugin-1.6.0/src#
```

Some specific part in "Makefile" which is needed for denoting the path for hearder file 
```

BUILD_GCC_TRUE = #
CC = gcc
CCDEPMODE = depmode=gcc3
CFLAGS = -g -O2 -I/usr/include/mm_ghdr
CPP = gcc -E
CPPFLAGS =
CXX = g++
CXXCPP = g++ -E
CXXDEPMODE = depmode=gcc3
CXXFLAGS = -g -O2
CYGPATH_W = echo
DEFS = -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"\" -DVERSION=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1
DEPDIR = .deps
ECHO = echo
ECHO_C =
ECHO_N = -n
ECHO_T =
EGREP = grep -E
EXEEXT =
F77 =
FFLAGS =
FSL_MM_CORE_CFLAGS = -I/usr/include/mm_ghdr  
FSL_MM_CORE_LIBS =
GST_BASE_CFLAGS = -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2
GST_BASE_LIBS = -pthread -lgstbase-0.10 -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0
GST_CFLAGS = -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2
GST_LIBS = -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0
GST_MAJORMINOR = 0.10
GST_PLUGINS_BASE_CFLAGS = -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2
GST_PLUGINS_BASE_LIBS = -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0
GST_PLUGIN_LDFLAGS = -module -avoid-version -export-symbols-regex _*\(gst_\|Gst\|GST_\).*
HAVE_PKGCONFIG = yes
INSTALL_DATA = ${INSTALL} -m 644
INSTALL_PROGRAM = ${INSTALL}
INSTALL_SCRIPT = ${INSTALL}
INSTALL_STRIP_PROGRAM = ${SHELL} $(install_sh) -c -s
LDFLAGS =

```
 Can anyone help me. In which area in makefile i have to change?i am confused. Please help me

---

### Post by Some Penguin on 2009-12-23
> **shariefbe said:**
> Hello,
   I am trying to compile the gstreamer. for that i tries make to compile and i got some error. That error shows that it didnt find the correct header file where it searches for header file. now how to change that searching path in 'Makefile"


```

CFLAGS = -g -O2 -I/usr/include/mm_ghdr

```Add -I/path/you/need/to/add

---

### Post by shariefbe on 2009-12-23
No again i am getting the same error even i changed that path

```

mfw_gst_aacdec.c:52:32: error: aacd_dec_interface.h: No such file or directory
In file included from mfw_gst_aacdec.c:53:
mfw_gst_aacdec.h:96: error: expected specifier-qualifier-list before 'AACD_Block_Params'
mfw_gst_aacdec.c:113: error: 'AACD_INPUT_BUFFER_SIZE' undeclared here (not in a function)
mfw_gst_aacdec.c:117: error: 'INTERNAL_BS_BUFSIZE' undeclared here (not in a function)
mfw_gst_aacdec.c:161: error: expected ')' before '*' token

```

The makefile part which i changed is 
```

BUILD_GCC_TRUE = #
CC = gcc
CCDEPMODE = depmode=gcc3
#CFLAGS = -g -O2 -I/usr/include/mm_ghdr  
CFLAGS = -g -O2 -I/home/ariem/Desktop/plugins/fsl_linux_sdk_codecs_1.6.0_1/fsl-mm-codeclib-1.6.0/ghdr/
CPP = gcc -E
CPPFLAGS =
CXX = g++
CXXCPP = g++ -E
CXXDEPMODE = depmode=gcc3

```
Help me

---

### Post by shariefbe on 2009-12-24
Now my problem is fixed. I copied that file and remaned as mm_ghdr in /usr/include directory. So it works fine. Now i am getting another one error.
when i do make i am getting missing library as below 
```

root@ariem-desktop:/home/ariem/Desktop/plugins/fsl_linux_sdk_gstreamer_plugins_1.6.0_1/gst-fsl-plugin-1.6.0/src# make
Making all in audio/aac_dec/src
make[1]: Entering directory `/home/ariem/Desktop/plugins/fsl_linux_sdk_gstreamer_plugins_1.6.0_1/gst-fsl-plugin-1.6.0/src/audio/aac_dec/src'
/bin/sh ../../../libtool --tag=CC --mode=link gcc  -g -O2 -I/usr/include/mm_ghdr     -o libmfw_gst_aacdec.la -rpath /usr/local/lib/gstreamer-0.10 -module -avoid-version -export-symbols-regex _*\(gst_\|Gst\|GST_\).*  -lgstriff-0.10 libmfw_gst_aacdec_la-mfw_gst_aacdec.lo -pthread -lgstbase-0.10 -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0   -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0   -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0   -l_aac_dec_arm12_elinux 
rm -fr  .libs/libmfw_gst_aacdec.exp .libs/libmfw_gst_aacdec.ver
generating symbol list for `libmfw_gst_aacdec.la'
/usr/bin/nm -B  .libs/libmfw_gst_aacdec_la-mfw_gst_aacdec.o  | sed -n -e 's/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' | /bin/sed 's/.* //' | sort | uniq > .libs/libmfw_gst_aacdec.exp
grep -E -e "_*(gst_|Gst|GST_).*" ".libs/libmfw_gst_aacdec.exp" > ".libs/libmfw_gst_aacdec.expT"
mv -f ".libs/libmfw_gst_aacdec.expT" ".libs/libmfw_gst_aacdec.exp"
echo "{ global:" > .libs/libmfw_gst_aacdec.ver
 cat .libs/libmfw_gst_aacdec.exp | sed -e "s/\(.*\)/\1;/" >> .libs/libmfw_gst_aacdec.ver
 echo "local: *; };" >> .libs/libmfw_gst_aacdec.ver
 gcc -shared  .libs/libmfw_gst_aacdec_la-mfw_gst_aacdec.o  -lgstriff-0.10 /usr/lib/libgstbase-0.10.so -L/usr/lib /usr/lib/libgstreamer-0.10.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libgthread-2.0.so -lrt /usr/lib/libxml2.so /usr/lib/libglib-2.0.so -l_aac_dec_arm12_elinux  -pthread -pthread -pthread -Wl,-soname -Wl,libmfw_gst_aacdec.so -Wl,-version-script -Wl,.libs/libmfw_gst_aacdec.ver -o .libs/libmfw_gst_aacdec.so
/usr/bin/ld: cannot find -l_aac_dec_arm12_elinux
collect2: ld returned 1 exit status
make[1]: *** [libmfw_gst_aacdec.la] Error 1
make[1]: Leaving directory `/home/ariem/Desktop/plugins/fsl_linux_sdk_gstreamer_plugins_1.6.0_1/gst-fsl-plugin-1.6.0/src/audio/aac_dec/src'
make: *** [all-recursive] Error 1
root@ariem-desktop:/home/ariem/Desktop/plugins/fsl_linux_sdk_gstreamer_plugins_1.6.0_1/gst-fsl-plugin-1.6.0/src# 

```

 But when i searched for that file i am getting

```
ariem@ariem-desktop:~/Desktop/plugins/fsl_linux_sdk_codecs_1.6.0_1/fsl-mm-codeclib-1.6.0/test/aacplus_dec$ grep -r "aac_dec_arm12_elinux" /
grep: /home/xloader/include/asm/proc: No such file or directory
grep: /home/lost+found: Permission denied
grep: /home/ariem/.nano_history: Permission denied
grep: /home/ariem/xloader/include/asm/proc: No such file or directory
grep: /home/ariem/Desktop/pegatron/opt/freescale/pkgs/fsl-mm-codeclib-1.6.0/ghdr/wma10_dec/license.h: No such file or directory
grep: /home/ariem/Desktop/pegatron/opt/freescale/pkgs/fsl-mm-codeclib-1.6.0/test/aacplus_dec/lib_aac_dec_arm11_lervds.a: No such file or directory
grep: /home/ariem/Desktop/pegatron/opt/freescale/pkgs/fsl-mm-codeclib-1.6.0/test/aacplus_dec/lib_aac_dec_arm9_lervds.a: No such file or directory
grep: /home/ariem/Desktop/pegatron/opt/freescale/pkgs/fsl-mm-codeclib-1.6.0/test/aacplus_dec/lib_aac_dec_arm11_elinux.a: No such file or directory
grep: /home/ariem/Desktop/pegatron/opt/freescale/pkgs/fsl-mm-codeclib-1.6.0/test/aacplus_dec/lib_aac_dec_arm9_elinux.a: No such file or directory
Binary file /home/ariem/Desktop/pegatron/opt/freescale/pkgs/fsl-mm-codeclib-1.6.0/release/exe/test_aac_dec_arm12_elinux matches
/home/ariem/Desktop/pegatron/opt/freescale/pkgs/gst-fsl-plugin-1.6.0/src/audio/aacplus_dec/src/Makefile.am:CORELIB=_aac_dec_arm12_elinux 
/home/ariem/Desktop/pegatron/opt/freescale/pkgs/gst-fsl-plugin-1.6.0/src/audio/aacplus_dec/src/Makefile.in:@PLATFORM_IS_MX51_TRUE@CORELIB = _aac_dec_arm12_elinux 
/home/ariem/Desktop/pegatron/opt/freescale/pkgs/gst-fsl-plugin-1.6.0/src/audio/aac_dec/src/Makefile.am:CORELIB=_aac_dec_arm12_elinux
/home/ariem/Desktop/pegatron/opt/freescale/pkgs/gst-fsl-plugin-1.6.0/src/audio/aac_dec/src/Makefile.in:@PLATFORM_IS_MX51_TRUE@CORELIB = _aac_dec_arm12_elinux
grep: /home/ariem/Desktop/pegatron/opt/freescale/ltib/usr/lib/rpmpopt: No such file or directory

```
Kindly help me

---

### Post by shariefbe on 2009-12-24
Now my problem is changed
```

/home/ariem/CodeSourcery/Sourcery_G++_Lite/bin/../lib/gcc/arm-none-linux-gnueabi/4.3.3/../../../../arm-none-linux-gnueabi/bin/ld: cannot find -lgstriff-0.10
collect2: ld returned 1 exit status
make[1]: *** [libmfw_gst_aacdec.la] Error 1
make[1]: Leaving directory `/home/ariem/Desktop/plugins/fsl_linux_sdk_gstreamer_plugins_1.6.0_1/gst-fsl-plugin-1.6.0/src/audio/aac_dec/src'
make: *** [all-recursive] Error 1
Building  of glib library  has failed
```

---

