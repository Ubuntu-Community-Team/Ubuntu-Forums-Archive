---
title: "sample CPU usage at sub-second granularity"
date: 2012-06-15
forum: General Help
---

### Post by mohanradhakrishnan on 2012-06-15
I tried to sample CPU usage for a single process several times in a second. Since DTrace seems to be able to do it I tried to build DTrace from this git 
[SIZE=2]( [http://liberumvir.com/2012/06/01/zfs-and-dtrace-running-on-ubuntu.html](http://liberumvir.com/2012/06/01/zfs-and-dtrace-running-on-ubuntu.html)).[/SIZE]
 
[SIZE=2]I got this error though.[/SIZE]

gcc -g -I../common -I../common/ctf -I../uts/common/ -I../common/ctf -I. -I../linux -DCTF_OLD_VERSIONS -D_ILP32 -D_LONGLONG_TYPE -D_LARGEFILE_SOURCE=1 -D_LARGEFILE64_SOURCE=1 -D_FILE_OFFSET_BITS=64 -c -o ctf_lib.o ctf_lib.c
In file included from ../linux/sys/types.h:4:0,
from ctf_lib.c:29:
../linux/linux_types.h:146:38: fatal error: /usr/include/sys/types.h: No such file or directory
compilation terminated.
make[3]: *** [ctf_lib.o] Error 1
make[2]: *** [do_cmds] Error 2
tools/bug.sh
make[1]: *** [all] Error 1
 
 
Is there any other way to do this ? I am not a expert Ubuntu user. Any suggestion for this compilation ?
 
Thanks.
Mohan

---

### Post by David Andersson on 2012-06-15
> **mohanradhakrishnan said:**
> 
../linux/linux_types.h:146:38: fatal error: /usr/include/sys/types.h: No such file or directory


You need to install some dev packages for header files. /usr/include/sys/types.h is in package **libc6-dev**.

---

### Post by mohanradhakrishnan on 2012-06-18
Thanks. I coud proceed. If this thread title is confusing I will ask any DTrace forums available.
 
But I am unable to run DTrace even though it seems to have installed with this message
 
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]build/ctfconvert not available - so not building the linux.ctf file[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]NOTE: The build is complete, but build/ctfconvert is not available.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      This means you will get run time errors from the io.d and sched.d files[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      due to undefined kernel structure definitions. Simply delete or rename[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      these files until a fix can be put in place to handle older[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      distros which do not have the required libdwarf dependencies.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      (Typical error is references to undefined struct definitions such[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      as dtrace_cpu_t).[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
 
Trying to run :
 
~/statistics/DTrace/DTraceToolkit-0.99$ ./iosnoop
: probe description io:genunix::start does not match any probes
 
~/statistics/DTrace/DTraceToolkit-0.99$ dtrace -ln io:genunix::start
   ID   PROVIDER            MODULE                          FUNCTION NAME
dtrace: failed to match io:genunix::start: No probe matches description

---

### Post by David Andersson on 2012-06-18
> **mohanradhakrishnan said:**
> 
But I am unable to run DTrace even though it seems to have installed with this message
 
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]build/ctfconvert not available - so not building the linux.ctf file[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]NOTE: The build is complete, but build/ctfconvert is not available.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      This means you will get run time errors from the io.d and sched.d files[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      due to undefined kernel structure definitions. Simply delete or rename[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      these files until a fix can be put in place to handle older[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      distros which do not have the required libdwarf dependencies.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      (Typical error is references to undefined struct definitions such[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]      as dtrace_cpu_t).[/FONT][/COLOR][/COLOR][/SIZE][/FONT]


The message above says you will get run time errors from io.d and sched.d. And sure enough, you get run time errors with "sched" and "io" in the error messages. Further, it indicates libdwarf is a dependency. Try install package libdwarf-dev.

There should be some documentation of dtrace that lists all its dependencies. Try find it, so you can install all needed dev packages at once, instead of installing one at a time in a trial and error loop.

---

### Post by mohanradhakrishnan on 2012-06-18
I think I have installed the dependencies. Now after making, installing and loading I get
 
 
: "/usr/lib/dtrace/sched.d", line 60: no symbolic type information is available for kernel`dtrace_cpu_id: Invalid argument
 
 
install -m 644 -o root etc/io.d ""/usr/lib/dtrace
install -m 644 -o root etc/sched.d ""/usr/lib/dtrace
install -m 644 -o root etc/unistd.d ""/usr/lib/dtrace
scripts/mkinstall.pl -o=""/usr/lib/dtrace
fssadmin@fSSCHNDLINUX:~/statistics/dtrace/dtrace-for-linux$ sudo make load
tools/load.pl
21:02:45 Syncing...
21:02:46 Loading: build-3.0.0-17-generic/driver/dtracedrv.ko
21:02:48 Preparing symbols...
21:02:48 Probes available: 367778
21:02:53 Time: 8s
 
It looks like it is built properly this time.

---

