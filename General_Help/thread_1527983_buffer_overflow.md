---
title: "buffer overflow"
date: 2010-07-10
forum: General Help
---

### Post by dieter-erich on 2010-07-10
Hi, sorry for posting a somewhat modified version of my previous post, but I have not got any answer and am desperately seeking help. I very much like UBUNTU and want to continue using it.

but:

The program "robem" from the package auto3dem  ([http://cryoem.ucsd.edu/programs-auto3dem-archive.shtm](http://cryoem.ucsd.edu/programs-auto3dem-archive.shtm)) compiles without any error message on UBUNTU 10.04 (with all updates). However on launching it, it issues the error messages (including buffer overflow) below. There no such problem compiling and running it under CentOS 5. How can I find the reason for this? Where are the differences between UBUNTU and CentOS ? 
Thanks for any input,
D-E

PID[1816][RobEM-v3.15 Jun  2 2010 23:54:35]
Using default colormap: visual = [188380312], DEC colormap = [65011724]
Full path to UID file: [/usr/local/auto3dem_v3.15/bin/new_robem.uid]
*** buffer overflow detected ***: robem terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x7a9390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x7a82ca]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0x7a7644]
/usr/lib/libMrm.so.3(Idb__HDR_GetHeader+0x2b8)[0xe22018]
/usr/lib/libMrm.so.3(UrmIdbOpenFileRead+0xec)[0xe2571c]
/usr/lib/libMrm.so.3(+0xfe76)[0xe26e76]
/usr/lib/libMrm.so.3(Urm__OpenHierarchy+0x1ab)[0xe2722b]
/usr/lib/libMrm.so.3(MrmOpenHierarchyPerDisplay+0x65)[0xe263b5]
robem[0x80cd236]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x6ddbd6]
robem[0x804b9c1]
======= Memory map: ========
00110000-0015f000 r-xp 00000000 07:00 1049426    /usr/lib/libXt.so.6.0.0
0015f000-00160000 r--p 0004e000 07:00 1049426    /usr/lib/libXt.so.6.0.0
00160000-00163000 rw-p 0004f000 07:00 1049426    /usr/lib/libXt.so.6.0.0
00163000-0027c000 r-xp 00000000 07:00 1049383    /usr/lib/libX11.so.6.3.0
0027c000-0027d000 r--p 00118000 07:00 1049383    /usr/lib/libX11.so.6.3.0
0027d000-0027f000 rw-p 00119000 07:00 1049383    /usr/lib/libX11.so.6.3.0
0027f000-00280000 rw-p 00000000 00:00 0 
00280000-00344000 r-xp 00000000 07:00 1050269    /usr/lib/libgfortran.so.3.0.0
00344000-00345000 ---p 000c4000 07:00 1050269    /usr/lib/libgfortran.so.3.0.0
00345000-00346000 r--p 000c4000 07:00 1050269    /usr/lib/libgfortran.so.3.0.0
00346000-00347000 rw-p 000c5000 07:00 1050269    /usr/lib/libgfortran.so.3.0.0
00347000-00348000 rw-p 00000000 00:00 0 
00348000-00360000 r-xp 00000000 07:00 1050394    /usr/lib/libxcb.so.1.1.0
00360000-00361000 r--p 00017000 07:00 1050394    /usr/lib/libxcb.so.1.1.0
00361000-00362000 rw-p 00018000 07:00 1050394    /usr/lib/libxcb.so.1.1.0
00362000-00365000 r-xp 00000000 07:00 654272     /lib/libuuid.so.1.3.0
00365000-00366000 r--p 00002000 07:00 654272     /lib/libuuid.so.1.3.0
00366000-00367000 rw-p 00003000 07:00 654272     /lib/libuuid.so.1.3.0
00367000-0036f000 r-xp 00000000 07:00 1049422    /usr/lib/libXrender.so.1.3.0
0036f000-00370000 r--p 00007000 07:00 1049422    /usr/lib/libXrender.so.1.3.0
00370000-00371000 rw-p 00008000 07:00 1049422    /usr/lib/libXrender.so.1.3.0
0037c000-00383000 r-xp 00000000 07:00 1049381    /usr/lib/libSM.so.6.0.1
00383000-00384000 r--p 00006000 07:00 1049381    /usr/lib/libSM.so.6.0.1
00384000-00385000 rw-p 00007000 07:00 1049381    /usr/lib/libSM.so.6.0.1
003bb000-003d0000 r-xp 00000000 07:00 1049352    /usr/lib/libICE.so.6.3.0
003d0000-003d1000 r--p 00014000 07:00 1049352    /usr/lib/libICE.so.6.3.0
003d1000-003d2000 rw-p 00015000 07:00 1049352    /usr/lib/libICE.so.6.3.0
003d2000-003d4000 rw-p 00000000 00:00 0 
00460000-00462000 r-xp 00000000 07:00 654432     /lib/tls/i686/cmov/libdl-2.11.1.so
00462000-00463000 r--p 00001000 07:00 654432     /lib/tls/i686/cmov/libdl-2.11.1.so
00463000-00464000 rw-p 00002000 07:00 654432     /lib/tls/i686/cmov/libdl-2.11.1.so
004a6000-004aa000 r-xp 00000000 07:00 1049398    /usr/lib/libXdmcp.so.6.0.0
004aa000-004ab000 r--p 00003000 07:00 1049398    /usr/lib/libXdmcp.so.6.0.0
004ab000-004ac000 rw-p 00004000 07:00 1049398    /usr/lib/libXdmcp.so.6.0.0
004e6000-004ea000 r-xp 00000000 07:00 1049402    /usr/lib/libXfixes.so.3.1.0
004ea000-004eb000 r--p 00003000 07:00 1049402    /usr/lib/libXfixes.so.3.1.0
004eb000-004ec000 rw-p 00004000 07:00 1049402    /usr/lib/libXfixes.so.3.1.0
00512000-0052f000 r-xp 00000000 07:00 654164     /lib/libgcc_s.so.1
0052f000-00530000 r--p 0001c000 07:00 654164     /lib/libgcc_s.so.1
00530000-00531000 rw-p 0001d000 07:00 654164     /lib/libgcc_s.so.1
005bf000-005c1000 r-xp 00000000 07:00 1049387    /usr/lib/libXau.so.6.0.0
005c1000-005c2000 r--p 00001000 07:00 1049387    /usr/lib/libXau.so.6.0.0
005c2000-005c3000 rw-p 00002000 07:00 1049387    /usr/lib/libXau.so.6.0.0
005e9000-005fe000 r-xp 00000000 07:00 654443     /lib/tls/i686/cmov/libpthread-2.11.1.so
005fe000-005ff000 r--p 00014000 07:00 654443     /lib/tls/i686/cmov/libpthread-2.11.1.so
005ff000-00600000 rw-p 00015000 07:00 654443     /lib/tls/i686/cmov/libpthread-2.11.1.so
00600000-00602000 rw-p 00000000 00:00 0 
006be000-006c5000 r-xp 00000000 07:00 1049416    /usr/lib/libXp.so.6.2.0
006c5000-006c6000 r--p 00006000 07:00 1049416    /usr/lib/libXp.so.6.2.0
006c6000-006c7000 rw-p 00007000 07:00 1049416    /usr/lib/libXp.so.6.2.0
006c7000-0081a000 r-xp 00000000 07:00 654429     /lib/tls/i686/cmov/libc-2.11.1.so
0081a000-0081b000 ---p 00153000 07:00 654429     /lib/tls/i686/cmov/libc-2.11.1.so
0081b000-0081d000 r--p 00153000 07:00 654429     /lib/tls/i686/cmov/libc-2.11.1.so
0081d000-0081e000 rw-p 00155000 07:00 654429     /lib/tls/i686/cmov/libc-2.11.1.so
0081e000-00821000 rw-p 00000000 00:00 0 
00889000-00891000 r-xp 00000000 07:00 1049394    /usr/lib/libXcursor.so.1.0.2
00891000-00892000 r--p 00007000 07:00 1049394    /usr/lib/libXcursor.so.1.0.2
00892000-00893000 rw-p 00008000 07:00 1049394    /usr/lib/libXcursor.so.1.0.2
009ea000-00a05000 r-xp 00000000 07:00 654394     /lib/ld-2.11.1.so
00a05000-00a06000 r--p 0001a000 07:00 654394     /lib/ld-2.11.1.so
00a06000-00a07000 rw-p 0001b000 07:00 654394     /lib/ld-2.11.1.so
00a0b000-00c44000 r-xp 00000000 07:00 1047336    /usr/lib/libXm.so.3.0.2
00c44000-00c45000 ---p 00239000 07:00 1047336    /usr/lib/libXm.so.3.0.2
00c45000-00c47000 r--p 00239000 07:00 1047336    /usr/lib/libXm.so.3.0.2
00c47000-00c5d000 rw-p 0023b000 07:00 1047336    /usr/lib/libXm.so.3.0.2
00c5d000-00c5f000 rw-p 00000000 00:00 0 
00c91000-00cb5000 r-xp 00000000 07:00 654433     /lib/tls/i686/cmov/libm-2.11.1.so
00cb5000-00cb6000 r--p 00023000 07:00 654433     /lib/tls/i686/cmov/libm-2.11.1.so
00cb6000-00cb7000 rw-p 00024000 07:00 654433     /lib/tls/i686/cmov/libm-2.11.1.so
00cc5000-00cd3000 r-xp 00000000 07:00 1049400    /usr/lib/libXext.so.6.4.0
00cd3000-00cd4000 r--p 0000d000 07:00 1049400    /usr/lib/libXext.so.6.4.0
00cd4000-00cd5000 rw-p 0000e000 07:00 1049400    /usr/lib/libXext.so.6.4.0
00d7a000-00d7b000 r-xp 00000000 00:00 0          [vdso]
00e17000-00e37000 r-xp 00000000 07:00 1046990    /usr/lib/libMrm.so.3.0.2
00e37000-00e38000 r--p 00020000 07:00 1046990    /usr/lib/libMrm.so.3.0.2
00e38000-00e39000 rw-p 00021000 07:00 1046990    /usr/lib/libMrm.so.3.0.2
00edc000-00ef1000 r-xp 00000000 07:00 1049412    /usr/lib/libXmu.so.6.2.0
00ef1000-00ef2000 r--p 00014000 07:00 1049412    /usr/lib/libXmu.so.6.2.0
00ef2000-00ef3000 rw-p 00015000 07:00 1049412    /usr/lib/libXmu.so.6.2.0
08048000-08172000 r-xp 00000000 07:00 1439234    /usr/local/auto3dem_v3.15/bin/robem
08172000-08173000 r--p 00129000 07:00 1439234    /usr/local/auto3dem_v3.15/bin/robem
08173000-08177000 rw-p 0012a000 07:00 1439234    /usr/local/auto3dem_v3.15/bin/robemAborted

---

### Post by arloth on 2010-08-02
I'm getting a similar error to this as well.  I can't say for sure if I've run the program in older versions of ubuntu, but it runs just fine in SL 4.1.  

It's from th MrmOpenHierarchyPerDisplay call, but the error seems to be from the libMRM library instead, part of libmotif, and not a mistake in my program.

**4846** *** strcpy_chk: buffer overflow detected ***: program terminated
==4846==    at 0x4027927: VALGRIND_PRINTF_BACKTRACE (valgrind.h:4214)
==4846==    by 0x4027AFF: __strcpy_chk (mc_replace_strmem.c:757)
==4846==    by 0x433A017: Idb__HDR_GetHeader (in /usr/lib/libMrm.so.3.0.2)
==4846==    by 0x433D71B: UrmIdbOpenFileRead (in /usr/lib/libMrm.so.3.0.2)
==4846==    by 0x433EE75: ??? (in /usr/lib/libMrm.so.3.0.2)
==4846==    by 0x433F22A: Urm__OpenHierarchy (in /usr/lib/libMrm.so.3.0.2)
==4846==    by 0x433E3B4: MrmOpenHierarchyPerDisplay (in /usr/lib/libMrm.so.3.0.2)
==4846==    by 0x805255E: main (test.c:2532)
==4846== 

The solution seems to be update to Openmotif 2.3.  Fortunately for us 2.3 seems to have been released in 2007, and Ubuntu ships with the most ancient 2.2.3.  This is madness, hopefully somebody has this in a repo somewhere.
[http://www.psfc.mit.edu/pnews/read.php?server=www.mdsplus.org&group=mdsplus.development&artnum=888](http://www.psfc.mit.edu/pnews/read.php?server=www.mdsplus.org&group=mdsplus.development&artnum=888)

---

### Post by arloth on 2010-08-02
Yes, I can confirm updating to 2.3.3 fixes the issue.  I didn't really bother to search for in in a repo, but instead grabbed the two .deb files from [http://openmotif.org/filebrowser/openmotif/2.3/2.3.3](http://openmotif.org/filebrowser/openmotif/2.3/2.3.3)  It's not exactly a perfect method, but it works.

Hopefully somebody is listening and will at least update it to 2.3.3 in 10.10, but then again maybe I should see if I remember my launchpad login. ;)

---

### Post by dieter-erich on 2010-08-24
Hi Arloth,
    you won't believe, but I had also contacted Canonical and they drew my attention to just this (my) posting! Apparently, the old software is using the old Motif libraries that are not compatible with the newer UBUNTU versions. If I have some spare time I'll try your suggestion and install the updated Motif libraries to see whether this solves the problem. In any case, the issue is solved by compiling under Centos 5.4 and copying the binaries to the UBUNTU machine.
Thanks for your input, best, D-E
I haven't looked into the forum since some time because I had not got any answer. This is why I have not seen yours before!

---

### Post by no2498 on 2010-08-24
AS YOU CAN SEE THIS COMES FROM CHEESE

it may or may NOT be what you need


5.6.&#8195;My Quickcam Express doesn't work with Cheese...


      or gstreamer, and I see errors like "Not enough buffers. We got 1, we
      want at least 2" in the Cheese output. With driver "qc-usb".
    


      Try running "qcset /dev/video0 compat=dblbuf" to enable double buffer
      compatibility mode, then restart Cheese

---

### Post by dieter-erich on 2010-08-28
Yes, robem, oned, and ctfdisp compile and run with the new openmotif libraries from [www.motifzone.org](www.motifzone.org)! The issue is solved!

---

### Post by arloth on 2010-09-15
> **dieter-erich said:**
> Yes, robem, oned, and ctfdisp compile and run with the new openmotif libraries from [www.motifzone.org](www.motifzone.org)! The issue is solved!

Remembered my launchpad login, time to make people aware this problem still exists.  [https://bugs.launchpad.net/ubuntu/+source/openmotif/+bug/374907](https://bugs.launchpad.net/ubuntu/+source/openmotif/+bug/374907)

also, @no2498, this bug has nothing to do with cheese...  the programs involved aren't even using webcams or gtk for that mater.

---

