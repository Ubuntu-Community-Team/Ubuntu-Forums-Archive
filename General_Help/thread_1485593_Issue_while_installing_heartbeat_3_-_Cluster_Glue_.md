---
title: "Issue while installing heartbeat 3 - Cluster Glue component on Ubuntu 9"
date: 2010-05-17
forum: General Help
---

### Post by sumanmshan on 2010-05-17
Hi All,

I have the following configurations:

Description:    Ubuntu 9.04
Release:        9.04

Trying to install heartbeat version 3, for this I have copied the required files on Ubuntu to one of the folder I have created:

Cluster-Resource-Agents-agents-1.0.3.tar.bz2
Heartbeat-3-0-STABLE-3.0.3.tar.bz2
Reusable-Cluster-Components-glue-1.0.5.tar.bz2

I started installing "Reusable-Cluster-Components-glue-1.0.5.tar.bz2" first. Steps followed are:

1) ```
tar -vxjf Reusable-Cluster-Components-glue-1.0.5.tar.bz2
```2) ```
wget http://hg.linux-ha.org/glue/archive/tip.tar.bz2
```3) ```
tar -vxjf tip.tar.bz2
```4) ```
apt-get install mercurial
```5) ```
hg clone http://hg.linux-ha.org/glue cluster-glue
```6) ```
./configure
```7) ```
make
```#6 (configure step) throws an error in the end: 
```
configure: error: You need pkgconfig installed in order to build cluster-glue
```The output for #6 is:
```
root@SumanEDBHA2:/usr/local/desktone/package/Reusable-Cluster-Components-glue-1.0.5# ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for preprocessor stringizing operator... yes
checking for size_t... yes
checking size of char... 1
checking size of short... 2
checking size of int... 4
checking size of long... 8
checking size of long long... 8
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct tm.tm_zone... yes
Our Host OS: linux-gnu/x86_64-unknown-linux-gnu
configure: Sanitizing prefix: NONE
configure: Sanitizing exec_prefix: NONE
configure: Sanitizing INITDIR:
checking which init (rc) directory to use... /etc/init.d
configure: Sanitizing libdir: ${exec_prefix}/lib
checking which lib directory to use... /usr/lib64
checking for the location of the lock directory... configure: WARNING: libexecdir directory (/usr/libexec) does not exist!
configure: WARNING: sharedstatedir directory (/usr/com) does not exist!
configure: WARNING: docdir directory (/usr/share/doc/cluster-glue) does not exist!
configure: WARNING: HA_VARLOCKDIR directory (/usr/var/lock) does not exist!
configure: Host CPU: x86_64
checking which format is needed to print uint64_t... %lu
checking for hg... /usr/bin/hg
checking build version... 3af80b93d9e5d5e441f3f4c3aad16775ea27d2d9
checking for getpid() consistency in multi-process/threads program... cat: ./config/pidtest.c: No such file or directory
fail
checking for byteorder... cat: ./config/byteorder_test.c: No such file or directory
big-endian
checking for glibtool... $(SHELL) $(top_builddir)/libtool
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... /usr/lib/python2.6/dist-packages
checking for python extension module directory... /usr/lib/python2.6/dist-packages
checking for gmake... no
checking for make... make
checking for lynx... no
checking for w3m... /usr/bin/w3m
checking for help2man... no
checking for pod2man... /usr/bin/pod2man
checking for ssh... /usr/bin/ssh
checking for scp... /usr/bin/scp
checking for hg... (cached) /usr/bin/hg
checking for tar... /bin/tar
checking for md5... no
checking for rpm... no
checking for test... /usr/bin/test
checking for ping... /bin/ping
checking for ifconfig... /sbin/ifconfig
checking for mailx... no
checking for mail... no
checking for egrep... (cached) /bin/grep -E
checking for pkg-config... no
checking for xml2-config... no
checking for xsltproc... no
configure: WARNING: xsltproc not installed, unable to (re-)build manual pages
checking for valgrind... no
checking ifconfig option to list interfaces... -a
checking for socket in -lsocket... no
checking for dlopen in -lc... no
checking for dlopen in -ldl... (cached) yes
checking for sched_getscheduler in -lrt... yes
checking for getopt_long in -lgnugetopt... no
checking for uuid_parse in -luuid... no
checking for uuid_create in -luuid... no
checking for sched_getscheduler in -lposix4... no
configure: error: You need pkgconfig installed in order to build cluster-glue
```Any pointers to resolve this would be of great help. I might have overlooked/missed something here.
Thank You.

- Suman

---

### Post by sumanmshan on 2010-05-24
hi All,

I have figured it out that there are few packages that needs to be installed before running the "configure" script. Following are the packages:

```

apt-get install pkg-config
apt-get install glib2-devel
apt-get install libxml2-devel
apt-get install libbz2
apt-get install libbz2-dev(not sure why we require this)

```

Now the configure script executes fine, but when I invoke the "make" command then following error is displayed:

```
/bin/bash ../../libtool --tag=CC  --tag=CC   --mode=link gcc -std=gnu99  -g -O2 -ggdb3 -O0  -fgnu89-inline -fstack-protector-all -Wall -Waggregate-return -Wbad-function-cast -Wcast-qual -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Wfloat-equal -Wformat=2 -Wformat-security -Wformat-nonliteral -Winline -Wmissing-prototypes -Wmissing-declarations -Wmissing-format-attribute -Wnested-externs -Wno-long-long -Wno-strict-aliasing -Wpointer-arith -Wstrict-prototypes -Wwrite-strings -ansi -D_GNU_SOURCE -DANSI_ONLY -Werror   -o ipctest ipctest.o libplumb.la ../../replace/libreplace.la  ../../lib/pils/libpils.la -lbz2 -lxml2 -lc -lrt -ldl  -lglib-2.0   -lltdl
libtool: link: gcc -std=gnu99 -g -O2 -ggdb3 -O0 -fgnu89-inline -fstack-protector-all -Wall -Waggregate-return -Wbad-function-cast -Wcast-qual -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Wfloat-equal -Wformat=2 -Wformat-security -Wformat-nonliteral -Winline -Wmissing-prototypes -Wmissing-declarations -Wmissing-format-attribute -Wnested-externs -Wno-long-long -Wno-strict-aliasing -Wpointer-arith -Wstrict-prototypes -Wwrite-strings -ansi -D_GNU_SOURCE -DANSI_ONLY -Werror -o .libs/ipctest ipctest.o  ./.libs/libplumb.so /usr/local/desktone/package/Reusable-Cluster-Components-glue-1.0.5/lib/pils/.libs/libpils.so ../../replace/.libs/libreplace.a ../../lib/pils/.libs/libpils.so -lbz2 /usr/lib/libxml2.so -lc -lrt /usr/lib/libglib-2.0.so /usr/lib/libltdl.so -ldl -Wl,-rpath -Wl,/usr/lib64
./.libs/libplumb.so: undefined reference to `uuid_parse'
./.libs/libplumb.so: undefined reference to `uuid_generate'
./.libs/libplumb.so: undefined reference to `uuid_copy'
./.libs/libplumb.so: undefined reference to `uuid_is_null'
./.libs/libplumb.so: undefined reference to `uuid_unparse'
./.libs/libplumb.so: undefined reference to `uuid_clear'
./.libs/libplumb.so: undefined reference to `uuid_compare'
collect2: ld returned 1 exit status
make[2]: *** [ipctest] Error 1
make[2]: Leaving directory `/usr/local/desktone/package/Reusable-Cluster-Components-glue-1.0.5/lib/clplumbing'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/desktone/package/Reusable-Cluster-Components-glue-1.0.5/lib'
make: *** [all-recursive] Error 1
```

Any pointers would be of great help.
Thank You.

-Suman

---

### Post by hafthanhf on 2010-10-25
hi all, I have the same problem, after successfully ./configure cluster-glue, I do the "make", and this is what I received:
> cc1: warnings being treated as errors
In file included from /usr/include/glib-2.0/glib/gasyncqueue.h:34,
                 from /usr/include/glib-2.0/glib.h:34,
                 from pils.c:34:
/usr/include/glib-2.0/glib/gthread.h: In function 'g_once_init_enter':
/usr/include/glib-2.0/glib/gthread.h:348: error: cast discards qualifiers from p                                                                                        ointer target type
make[2]: *** [pils.lo] Error 1
make[2]: Leaving directory `/usr/src/heatbeat/Reusable-Cluster-Components-glue-1.0.6/lib/pils'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/heatbeat/Reusable-Cluster-Components-glue-1.0.6/lib'
make: *** [all-recursive] Error 1


Thanks any advice

---

### Post by abid.ahad.pir on 2011-10-01
I am trying to install glue on Ubuntu:

```
root@abid-VirtualBox:/opt/ha/glue/Reusable-Cluster-Components-glue--601814740a68# uname -a
Linux abid-VirtualBox 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

```And I am also running into same issue:

```
/bin/bash ../../libtool --tag=CC  --tag=CC   --mode=link gcc -std=gnu99  -g -O2 -ggdb3 -O0  -fgnu89-inline -fstack-protector-all -Wall -Waggregate-return -Wbad-function-cast -Wcast-qual -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Wfloat-equal -Wformat=2 -Wformat-security -Wformat-nonliteral -Winline -Wmissing-prototypes -Wmissing-declarations -Wmissing-format-attribute -Wnested-externs -Wno-long-long -Wno-strict-aliasing -Wpointer-arith -Wstrict-prototypes -Wwrite-strings -ansi -D_GNU_SOURCE -DANSI_ONLY -Werror   -o ipctest ipctest.o libplumb.la ../../replace/libreplace.la  ../../lib/pils/libpils.la -lbz2 -lxml2 -lc -lrt -ldl  -L/usr/lib/i386-linux-gnu -lglib-2.0   -lltdl
libtool: link: gcc -std=gnu99 -g -O2 -ggdb3 -O0 -fgnu89-inline -fstack-protector-all -Wall -Waggregate-return -Wbad-function-cast -Wcast-qual -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Wfloat-equal -Wformat=2 -Wformat-security -Wformat-nonliteral -Winline -Wmissing-prototypes -Wmissing-declarations -Wmissing-format-attribute -Wnested-externs -Wno-long-long -Wno-strict-aliasing -Wpointer-arith -Wstrict-prototypes -Wwrite-strings -ansi -D_GNU_SOURCE -DANSI_ONLY -Werror -o .libs/ipctest ipctest.o  ./.libs/libplumb.so ../../replace/.libs/libreplace.a -L/usr/lib/i386-linux-gnu ../../lib/pils/.libs/libpils.so -lbz2 /usr/lib/libxml2.so -lc -lrt -ldl /usr/lib/i386-linux-gnu/libglib-2.0.so /usr/lib/libltdl.so -Wl,-rpath -Wl,/usr/lib64
./.libs/libplumb.so: undefined reference to `uuid_parse'
./.libs/libplumb.so: undefined reference to `uuid_generate'
./.libs/libplumb.so: undefined reference to `uuid_copy'
./.libs/libplumb.so: undefined reference to `uuid_is_null'
./.libs/libplumb.so: undefined reference to `uuid_unparse'
./.libs/libplumb.so: undefined reference to `uuid_clear'
./.libs/libplumb.so: undefined reference to `uuid_compare'
collect2: ld returned 1 exit status
make[2]: *** [ipctest] Error 1
make[2]: Leaving directory `/opt/ha/glue/Reusable-Cluster-Components-glue--601814740a68/lib/clplumbing'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/ha/glue/Reusable-Cluster-Components-glue--601814740a68/lib'
make: *** [all-recursive] Error 1
```Any pointers?

-Abid

---

### Post by abid.ahad.pir on 2011-10-01
Got past this error by installing uuid-dev:

```
apt-get install uuid-dev
```

---

