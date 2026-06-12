---
title: "make CARMEN (Robot Navigation Toolbox) - undefined reference"
date: 2012-09-05
forum: General Help
---

### Post by EliteTUM on 2012-09-05
Hi all,

I encountered several issues when trying to get CARMEN ( [https://wiki.ubuntu.com/carmen](https://wiki.ubuntu.com/carmen) ) up and running.

Right now I'm stuck on this error message:

```

****************************************************************
* Module  : PARAMDAEMON
* Comment : Module providing central repository for module parameters
****************************************************************

  --> Starting make
    ---- Compiling param_daemon.c to param_daemon.o (cc)
param_daemon.c: In function ‘lookup_name’:
param_daemon.c:100:16: warning: variable ‘name_length’ set but not used [-Wunused-but-set-variable]
param_daemon.c: In function ‘read_parameters_from_file’:
param_daemon.c:331:10: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result [-Wunused-result]
    ---- Linking param_daemon.o to param_daemon (cc)
/home/johnny/carmen-0.7.4-beta/lib/libglobal.a(global.o): In function `carmen_distance_traj':
global.c:(.text+0x253): undefined reference to `sqrt'
/home/johnny/carmen-0.7.4-beta/lib/libglobal.a(global.o): In function `carmen_angle_between':
global.c:(.text+0x27d): undefined reference to `atan2'
/home/johnny/carmen-0.7.4-beta/lib/libglobal.a(global.o): In function `carmen_distance':
global.c:(.text+0x2c3): undefined reference to `sqrt'
/home/johnny/carmen-0.7.4-beta/lib/libglobal.a(global.o): In function `carmen_rect_to_polar':
global.c:(.text+0x29cf): undefined reference to `hypot'
global.c:(.text+0x29e9): undefined reference to `atan2'
/home/johnny/carmen-0.7.4-beta/lib/libglobal.a(global.o): In function `carmen_rotate_2d':
global.c:(.text+0x2a2b): undefined reference to `sincos'
/home/johnny/carmen-0.7.4-beta/lib/libglobal.a(global.o): In function `carmen_gaussian_random':
global.c:(.text+0x2d5b): undefined reference to `log'
global.c:(.text+0x2d8b): undefined reference to `cos'
global.c:(.text+0x2da9): undefined reference to `sqrt'
/home/johnny/carmen-0.7.4-beta/lib/libglobal.a(global.o): In function `carmen_eigs_to_covariance':
global.c:(.text+0x3e5d): undefined reference to `sincos'
/home/johnny/carmen-0.7.4-beta/lib/libmap_interface.a(map_interface.o): In function `carmen_distance_map':
map_interface.c:(.text+0x2a1d): undefined reference to `hypot'
/home/johnny/carmen-0.7.4-beta/lib/libmap_interface.a(map_interface.o): In function `carmen_distance_world':
map_interface.c:(.text+0x2a4d): undefined reference to `hypot'
collect2: ld returned 1 exit status
make[3]: *** [param_daemon] Error 1
exit: 7: Illegal number: -1
make[2]: *** [binaries] Error 2
make[1]: *** [phase2] Error 2
exit: 1: Illegal number: -1
make: *** [phase2] Error 2
```

Actually an obvious sign, that "-lm" is missing in the linker flags. But I checked and it looks like it was set (would have been surprised if not). So any idea how I can solve this?

I try installing it on a 32Bit Ubuntu 11.10 running inside a Virtual Machine (VMWare) on a 64-bit Win7 System.

```
johnny@ubuntu:~/carmen-0.7.4-beta/src$ uname -a
Linux ubuntu 3.0.0-25-generic #41-Ubuntu SMP Mon Aug 13 17:59:54 UTC 2012 i686 i686 i386 GNU/Linux
```

Before I ran into this error, I got the problem with all warning meassages being treated as error. I solved this by deleting the "-Werror" flags from gcc and gXX.
Furthermore, I had an error with the Quickcamera Module. So I deleted it from the "PACKAGES" list. Both hints were taken from the Wiki:
[https://wiki.ubuntu.com/carmen](https://wiki.ubuntu.com/carmen)

Additional Info:

```
johnny@ubuntu:~/carmen-0.7.4-beta/src$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
stepping	: 2
cpu MHz		: 2128.049
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology tsc_reliable nonstop_tsc aperfmperf pni ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm arat dtherm
bogomips	: 4256.09
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
stepping	: 2
cpu MHz		: 2128.049
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology tsc_reliable nonstop_tsc aperfmperf pni ssse3 cx16 sse4_1 sse4_2 popcnt hypervisor lahf_lm arat dtherm
bogomips	: 4256.09
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management:

```

Thanks for any advice!

---

### Post by gordintoronto on 2012-09-05
Did you perform this step:
sudo apt-get install --yes --force-yes libgtk2.0-* libwrap0-deb  libjpeg-dev lib*zlib*  doxygen doxygen-doc doxygen-docs doxygen-gui swig swig-doc swig-examples g++  libgtk1.2-dev gdk-imlib-dev

The "sudo" was missing from the Wiki article, which means it would have completely failed, I think.

---

### Post by EliteTUM on 2012-09-06
Hi @gordintoronto,

yes I installed all of those packages. One by one, took some time but I managed to get them.

Furthermore, I found the Solution to my problem. I opened the Makefile in the subfolder "param_daemon" and added to the line

```
LFLAGS += *****
```

the entry "-lm". So:

```
LFLAGS += ***** -lm
```

Then the "PARAM_DAEMON" compiled just perfectly. Unfortunately, all other packages that followed and used the math.h-bib showed the same error. So every time the error occured, I had to edit the "Makefile". About 10-12 times. I don't exatly understand why. In the "Makefile" in the parent src-folder, the "-lm" Flag was set. Nevertheless, making & installing worked.
I allready tested the CARMEN Simulator, also working.

---

### Post by huangdongze on 2012-11-20
Thanks,I come up with the same problems. It took me a lot of time. Now I have solved the question of "undefined reference 'sin'...".I am now studying Robot Navigation of UAV,so I chose the software of carmen. We may be friends,ha.

  huangdongze
  2012.11.20

---

### Post by EliteTUM on 2012-11-20
I didn't do any further work with CARMEN yet. Maybe later again. For now I worked with selfmade simulations, since they were sufficient.

Glad I could help you! Good luck!

I do some research on Autonomous Vehicles :)

---

