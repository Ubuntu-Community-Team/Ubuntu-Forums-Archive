---
title: "ATI Radeon performance"
date: 2011-09-30
forum: General Help
---

### Post by megabuffen on 2011-09-30
Hi!

I've been having problems with graphics performance. I just installed Ubuntu and enabled the proprietary ATI driver, believing that it would give me better performance. However, the desktop effects seemed to suffer from some lag, and there even seems to be some problems with video playback at standard definition. 

Disabling the proprietary driver fixed this, until I wanted to play some Minecraft. With the standard Ubuntu driver, I get just 5 fps on a computer that delivers 10 times that on Windows. With the ATI driver, Java crashes. OpenJDK Runtime or the official one doesn't matter.

What can I do about this problem? Any help is much appreciated.

---

### Post by megabuffen on 2011-09-30
After some deactivating and reactivating the driver, performance seems fine. Playing 1080p video files is no problem and I tried some tux racer just to confirm that graphics performance is great.

However, java is still crashing. This is the bug report: > #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb76f7424, pid=2073, tid=1686223728
#
# JRE version: 6.0_22-b22
# Java VM: OpenJDK Server VM (20.0-b11 mixed mode linux-x86 )
# Derivative: IcedTea6 1.10.2
# Distribution: Ubuntu 11.04, package 6b22-1.10.2-0ubuntu1~11.04.1
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x00000819

Registers:
EAX=0x00000000, EBX=0x00000819, ECX=0x00000846, EDX=0x0000000b
ESP=0x6481b27c, EBP=0x6481b294, ESI=0x00000020, EDI=0xb76caff4
EIP=0xb76f7424, EFLAGS=0x00000202, CR2=0xb6865980

Top of Stack: (sp=0x6481b27c)
0x6481b27c:   6481b294 0000000b 00000846 b76c38a0
0x6481b28c:   b76caff4 6862a680 6481b398 680aebf3
0x6481b29c:   0000000b 00000000 00000000 00000000
0x6481b2ac:   00001000 00000000 00000000 00000000
0x6481b2bc:   00000000 00000000 7fffffff fffffffe
0x6481b2cc:   ffffffff ffffffff ffffffff ffffffff
0x6481b2dc:   ffffffff ffffffff ffffffff ffffffff
0x6481b2ec:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb76f7424)
0xb76f7404:   00 00 cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90
0xb76f7414:   51 52 55 89 e5 0f 34 90 90 90 90 90 90 90 eb f3
0xb76f7424:   5d 5a 59 c3 00 2e 73 68 73 74 72 74 61 62 00 2e
0xb76f7434:   68 61 73 68 00 2e 64 79 6e 73 79 6d 00 2e 64 79 

Register to memory mapping:

EAX=0x00000000 is an unknown value
EBX=0x00000819 is an unknown value
ECX=0x00000846 is an unknown value
EDX=0x0000000b is an unknown value
ESP=0x6481b27c is an unknown value
EBP=0x6481b294 is an unknown value
ESI=0x00000020 is an unknown value
EDI=0xb76caff4: <offset 0x15ff4> in /lib/i386-linux-gnu/libpthread.so.0 at 0xb76b5000


Stack: [0x6480b000,0x6481c000],  sp=0x6481b27c,  free space=64k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x424]  __kernel_vsyscall+0x10
C  [fglrx_dri.so+0x1837bf3]  atiQDS+0xa20e5
C  [libpthread.so.0+0x5e99]  start_thread+0xd9


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 68736K, used 2190K [0x9e800000, 0xa47d0000, 0xb3750000)
  eden space 65984K, 3% used [0x9e800000,0x9ea23ac8,0xa2870000)
  from space 2752K, 0% used [0xa2870000,0xa2870000,0xa2b20000)
  to   space 16064K, 0% used [0xa3820000,0xa3820000,0xa47d0000)
 PSOldGen        total 62912K, used 30966K [0x74950000, 0x786c0000, 0x9e800000)
  object space 62912K, 49% used [0x74950000,0x7678dab0,0x786c0000)
 PSPermGen       total 42496K, used 20741K [0x6c950000, 0x6f2d0000, 0x74950000)
  object space 42496K, 48% used [0x6c950000,0x6dd91610,0x6f2d0000)

Code Cache  [0xb3817000, 0xb3a57000, 0xb6817000)
 total_blobs=927 nmethods=585 adapters=296 free_code_cache=48556480 largest_free_block=18112

Dynamic libraries:
08048000-08051000 r-xp 00000000 08:06 797627     /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:06 797627     /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:06 797627     /usr/lib/jvm/java-6-openjdk/jre/bin/java
09994000-0a266000 rw-p 00000000 00:00 0          [heap]
53000000-530f4000 rw-p 00000000 00:00 0 
530f4000-53100000 ---p 00000000 00:00 0 
53200000-532fa000 rw-p 00000000 00:00 0 
532fa000-53300000 ---p 00000000 00:00 0 
53300000-533fe000 rw-p 00000000 00:00 0 
533fe000-53400000 ---p 00000000 00:00 0 
53400000-534fa000 rw-p 00000000 00:00 0 
534fa000-53500000 ---p 00000000 00:00 0 
53500000-535fa000 rw-p 00000000 00:00 0 
535fa000-53600000 ---p 00000000 00:00 0 
53600000-536af000 rw-p 00000000 00:00 0 
536af000-53700000 ---p 00000000 00:00 0 
53700000-537f9000 rw-p 00000000 00:00 0 
537f9000-53800000 ---p 00000000 00:00 0 
53800000-53900000 rw-p 00000000 00:00 0 
539fd000-539fe000 ---p 00000000 00:00 0 
539fe000-53bfe000 rw-p 00000000 00:00 0 
53bfe000-53bff000 ---p 00000000 00:00 0 
53bff000-53dff000 rw-p 00000000 00:00 0 
53dff000-53e00000 ---p 00000000 00:00 0 
53e00000-54000000 rw-p 00000000 00:00 0 
54000000-540fb000 rw-p 00000000 00:00 0 
540fb000-54100000 ---p 00000000 00:00 0 
54200000-542f3000 rw-p 00000000 00:00 0 
542f3000-54300000 ---p 00000000 00:00 0 
54300000-543ff000 rw-p 00000000 00:00 0 
543ff000-54400000 ---p 00000000 00:00 0 
54400000-544fd000 rw-p 00000000 00:00 0 
544fd000-54500000 ---p 00000000 00:00 0 
545fe000-54700000 rw-p 00000000 00:00 0 
54700000-547fd000 rw-p 00000000 00:00 0 
547fd000-54800000 ---p 00000000 00:00 0 
54800000-548fd000 rw-p 00000000 00:00 0 
548fd000-54900000 ---p 00000000 00:00 0 
54900000-549fd000 rw-p 00000000 00:00 0 
549fd000-54a00000 ---p 00000000 00:00 0 
54a00000-54afd000 rw-p 00000000 00:00 0 
54afd000-54b00000 ---p 00000000 00:00 0 
54b00000-54bfb000 rw-p 00000000 00:00 0 
54bfb000-54c00000 ---p 00000000 00:00 0 
54c19000-54c1c000 ---p 00000000 00:00 0 
54c1c000-5ecaa000 rw-p 00000000 00:00 0 
5ecaa000-5ecab000 ---p 00000000 00:00 0 
5ecab000-5f4ab000 rw-p 00000000 00:00 0 
5f4ab000-5f4ac000 ---p 00000000 00:00 0 
5f4ac000-5fcac000 rw-p 00000000 00:00 0 
5fcac000-63cad000 rw-s 00000000 00:10 19626      /dev/shm/pulse-shm-1471976742
63cad000-63e12000 r-xp 00000000 08:06 662151     /usr/lib/libvorbisenc.so.2.0.8
63e12000-63e13000 ---p 00165000 08:06 662151     /usr/lib/libvorbisenc.so.2.0.8
63e13000-63e24000 r--p 00165000 08:06 662151     /usr/lib/libvorbisenc.so.2.0.8
63e24000-63e25000 rw-p 00176000 08:06 662151     /usr/lib/libvorbisenc.so.2.0.8
63e25000-63e6f000 r-xp 00000000 08:06 661268     /usr/lib/libFLAC.so.8.2.0
63e6f000-63e70000 r--p 00049000 08:06 661268     /usr/lib/libFLAC.so.8.2.0
63e70000-63e71000 rw-p 0004a000 08:06 661268     /usr/lib/libFLAC.so.8.2.0
63e71000-63ed1000 r-xp 00000000 08:06 658159     /usr/lib/libsndfile.so.1.0.23
63ed1000-63ed2000 ---p 00060000 08:06 658159     /usr/lib/libsndfile.so.1.0.23
63ed2000-63ed3000 r--p 00060000 08:06 658159     /usr/lib/libsndfile.so.1.0.23
63ed3000-63ed4000 rw-p 00061000 08:06 658159     /usr/lib/libsndfile.so.1.0.23
63ed4000-63ed8000 rw-p 00000000 00:00 0 
63ed8000-63f1f000 r-xp 00000000 08:06 663043     /usr/lib/libpulsecommon-0.9.22.so
63f1f000-63f20000 r--p 00046000 08:06 663043     /usr/lib/libpulsecommon-0.9.22.so
63f20000-63f21000 rw-p 00047000 08:06 663043     /usr/lib/libpulsecommon-0.9.22.so
63f21000-63fe8000 r-xp 00000000 08:06 661342     /usr/lib/libasound.so.2.0.0
63fe8000-63fec000 r--p 000c6000 08:06 661342     /usr/lib/libasound.so.2.0.0
63fec000-63fed000 rw-p 000ca000 08:06 661342     /usr/lib/libasound.so.2.0.0
63fed000-64012000 r-xp 00000000 08:06 147004     /home/kalle/.minecraft/bin/natives/libopenal.so
64012000-64013000 rw-p 00025000 08:06 147004     /home/kalle/.minecraft/bin/natives/libopenal.so
64013000-64100000 rw-p 00000000 00:00 0 
64100000-64200000 rw-s 03ffe000 00:05 9115       /dev/ati/card0
64200000-64300000 rw-s 03ffd000 00:05 9115       /dev/ati/card0
64300000-64400000 rw-s 03ffc000 00:05 9115       /dev/ati/card0
64400000-64500000 rw-s 03ff9000 00:05 9115       /dev/ati/card0
64500000-64700000 rw-s d64df000 00:05 9115       /dev/ati/card0
64700000-647c5000 rw-p 00000000 00:00 0 
647c5000-64800000 ---p 00000000 00:00 0 
6480b000-6480c000 ---p 00000000 00:00 0 
6480c000-6481c000 rw-p 00000000 00:00 0 
6481c000-6485b000 r-xp 00000000 08:06 663041     /usr/lib/libpulse.so.0.12.3
6485b000-6485c000 r--p 0003e000 08:06 663041     /usr/lib/libpulse.so.0.12.3
6485c000-6485d000 rw-p 0003f000 08:06 663041     /usr/lib/libpulse.so.0.12.3
6485d000-64860000 ---p 00000000 00:00 0 
64860000-648ae000 rw-p 00000000 00:00 0 
648ae000-648b1000 ---p 00000000 00:00 0 
648b1000-66103000 rw-p 00000000 00:00 0 
66103000-66143000 rw-s 00010000 00:05 9115       /dev/ati/card0
66143000-66843000 rw-s 00006000 00:05 9115       /dev/ati/card0
66843000-66876000 r-xp 00000000 08:06 812386     /usr/lib/fglrx/libatiadlxx.so
66876000-66877000 rw-p 00033000 08:06 812386     /usr/lib/fglrx/libatiadlxx.so
66877000-6849a000 r-xp 00000000 08:06 812392     /usr/lib/fglrx/dri/fglrx_dri.so
6849a000-68575000 rw-p 01c23000 08:06 812392     /usr/lib/fglrx/dri/fglrx_dri.so
68575000-6862c000 rw-p 00000000 00:00 0 
6862c000-686f5000 r-xp 00000000 08:06 812390     /usr/lib/fglrx/libGL.so.1.2
686f5000-68700000 rwxp 000c8000 08:06 812390     /usr/lib/fglrx/libGL.so.1.2
68700000-68716000 rwxp 00000000 00:00 0 
68716000-6876d000 r-xp 00000000 08:06 147002     /home/kalle/.minecraft/bin/natives/liblwjgl.so
6876d000-6876e000 r--p 00056000 08:06 147002     /home/kalle/.minecraft/bin/natives/liblwjgl.so
6876e000-6876f000 rw-p 00057000 08:06 147002     /home/kalle/.minecraft/bin/natives/liblwjgl.so
6876f000-68900000 rw-s 00000000 00:04 3604503    /SYSV00000000 (deleted)
68900000-689fc000 rw-p 00000000 00:00 0 
689fc000-68a00000 ---p 00000000 00:00 0 
68a00000-68b00000 rw-p 00000000 00:00 0 
68b00000-68bff000 rw-p 00000000 00:00 0 
68bff000-68c00000 ---p 00000000 00:00 0 
68c04000-68c0b000 r-xp 00000000 08:06 525421     /lib/libwrap.so.0.7.6
68c0b000-68c0c000 r--p 00006000 08:06 525421     /lib/libwrap.so.0.7.6
68c0c000-68c0d000 rw-p 00007000 08:06 525421     /lib/libwrap.so.0.7.6
68c0d000-68c72000 rw-s 00000000 00:04 3571734    /SYSV00000000 (deleted)
68c72000-68c75000 ---p 00000000 00:00 0 
68c75000-68cc3000 rw-p 00000000 00:00 0 
68cc3000-68cc6000 ---p 00000000 00:00 0 
68cc6000-68d14000 rw-p 00000000 00:00 0 
68d14000-68d9b000 r-xp 00000000 08:06 664194     /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
68d9b000-68d9c000 ---p 00087000 08:06 664194     /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
68d9c000-68d9d000 r--p 00087000 08:06 664194     /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
68d9d000-68d9e000 rw-p 00088000 08:06 664194     /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
68d9e000-68d9f000 rw-p 00000000 00:00 0 
68d9f000-68f30000 rw-s 00000000 00:04 2785299    /SYSV00000000 (deleted)
68f30000-691a8000 rw-p 00000000 00:00 0 
691a8000-69208000 rw-s 00000000 00:04 2654228    /SYSV00000000 (deleted)
6920c000-69256000 r-xp 00000000 08:06 656762     /usr/lib/nss/libfreebl3.so
69256000-69257000 r--p 0004a000 08:06 656762     /usr/lib/nss/libfreebl3.so
69257000-69258000 rw-p 0004b000 08:06 656762     /usr/lib/nss/libfreebl3.so
69258000-6925c000 rw-p 00000000 00:00 0 
6925c000-6925f000 ---p 00000000 00:00 0 
6925f000-692ad000 rw-p 00000000 00:00 0 
692ad000-692b0000 ---p 00000000 00:00 0 
692b0000-692fe000 rw-p 00000000 00:00 0 
692fe000-692ff000 ---p 00000000 00:00 0 
692ff000-69aff000 rw-p 00000000 00:00 0 
69aff000-69b00000 ---p 00000000 00:00 0 
69b00000-6a300000 rw-p 00000000 00:00 0 
6a300000-6a3ef000 rw-p 00000000 00:00 0 
6a3ef000-6a400000 ---p 00000000 00:00 0 
6a408000-6a40b000 r-xp 00000000 08:06 526231     /lib/i386-linux-gnu/libuuid.so.1.3.0
6a40b000-6a40c000 r--p 00002000 08:06 526231     /lib/i386-linux-gnu/libuuid.so.1.3.0
6a40c000-6a40d000 rw-p 00003000 08:06 526231     /lib/i386-linux-gnu/libuuid.so.1.3.0
6a40d000-6a413000 r-xp 00000000 08:06 664059     /usr/lib/i386-linux-gnu/libSM.so.6.0.1
6a413000-6a414000 r--p 00005000 08:06 664059     /usr/lib/i386-linux-gnu/libSM.so.6.0.1
6a414000-6a415000 rw-p 00006000 08:06 664059     /usr/lib/i386-linux-gnu/libSM.so.6.0.1
6a415000-6a441000 r-xp 00000000 08:06 797680     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
6a441000-6a442000 r--p 0002b000 08:06 797680     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
6a442000-6a443000 rw-p 0002c000 08:06 797680     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
6a443000-6a445000 rw-p 00000000 00:00 0 
6a445000-6a449000 r-xp 00000000 08:06 526194     /lib/i386-linux-gnu/libnss_dns-2.13.so
6a449000-6a44a000 r--p 00004000 08:06 526194     /lib/i386-linux-gnu/libnss_dns-2.13.so
6a44a000-6a44b000 rw-p 00005000 08:06 526194     /lib/i386-linux-gnu/libnss_dns-2.13.so
6a44b000-6a460000 r-xp 00000000 08:06 662576     /usr/lib/libdbusmenu-glib.so.3.0.14
6a460000-6a461000 r--p 00014000 08:06 662576     /usr/lib/libdbusmenu-glib.so.3.0.14
6a461000-6a462000 rw-p 00015000 08:06 662576     /usr/lib/libdbusmenu-glib.so.3.0.14
6a462000-6a470000 r-xp 00000000 08:06 658472     /usr/lib/libdbusmenu-gtk.so.3.0.14
6a470000-6a471000 r--p 0000d000 08:06 658472     /usr/lib/libdbusmenu-gtk.so.3.0.14
6a471000-6a472000 rw-p 0000e000 08:06 658472     /usr/lib/libdbusmenu-gtk.so.3.0.14
6a473000-6a476000 r-xp 00000000 08:06 662179     /usr/lib/libxcb-atom.so.1.0.0
6a476000-6a477000 r--p 00002000 08:06 662179     /usr/lib/libxcb-atom.so.1.0.0
6a477000-6a478000 rw-p 00003000 08:06 662179     /usr/lib/libxcb-atom.so.1.0.0
6a478000-6a481000 r-xp 00000000 08:06 797669     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
6a481000-6a482000 r--p 00008000 08:06 797669     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
6a482000-6a483000 rw-p 00009000 08:06 797669     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
6a483000-6a485000 r-xp 00000000 08:06 526228     /lib/i386-linux-gnu/libutil-2.13.so
6a485000-6a486000 r--p 00001000 08:06 526228     /lib/i386-linux-gnu/libutil-2.13.so
6a486000-6a487000 rw-p 00002000 08:06 526228     /lib/i386-linux-gnu/libutil-2.13.so
6a487000-6a492000 r-xp 00000000 08:06 526227     /lib/i386-linux-gnu/libudev.so.0.11.1
6a492000-6a493000 r--p 0000a000 08:06 526227     /lib/i386-linux-gnu/libudev.so.0.11.1
6a493000-6a494000 rw-p 0000b000 08:06 526227     /lib/i386-linux-gnu/libudev.so.0.11.1
6a494000-6a4a7000 r-xp 00000000 08:06 658143     /usr/lib/libgvfscommon.so.0.0.0
6a4a7000-6a4a8000 r--p 00012000 08:06 658143     /usr/lib/libgvfscommon.so.0.0.0
6a4a8000-6a4a9000 rw-p 00013000 08:06 658143     /usr/lib/libgvfscommon.so.0.0.0
6a4a9000-6a4cc000 r-xp 00000000 08:06 664035     /usr/lib/gio/modules/libgvfsdbus.so
6a4cc000-6a4cd000 r--p 00023000 08:06 664035     /usr/lib/gio/modules/libgvfsdbus.so
6a4cd000-6a4ce000 rw-p 00024000 08:06 664035     /usr/lib/gio/modules/libgvfsdbus.so
6a4ce000-6a509000 r-xp 00000000 08:06 525702     /lib/i386-linux-gnu/libdbus-1.so.3.5.4
6a509000-6a50a000 r--p 0003a000 08:06 525702     /lib/i386-linux-gnu/libdbus-1.so.3.5.4
6a50a000-6a50b000 rw-p 0003b000 08:06 525702     /lib/i386-linux-gnu/libdbus-1.so.3.5.4
6a50b000-6a545000 r-xp 00000000 08:06 661748     /usr/lib/libibus.so.2.0.0
6a545000-6a546000 r--p 00039000 08:06 661748     /usr/lib/libibus.so.2.0.0
6a546000-6a547000 rw-p 0003a000 08:06 661748     /usr/lib/libibus.so.2.0.0
6a549000-6a54c000 r--s 00031000 08:06 797594     /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
6a54c000-6a54e000 r-xp 00000000 08:06 525385     /lib/libnss_mdns4_minimal.so.2
6a54e000-6a54f000 r--p 00001000 08:06 525385     /lib/libnss_mdns4_minimal.so.2
6a54f000-6a550000 rw-p 00002000 08:06 525385     /lib/libnss_mdns4_minimal.so.2
6a550000-6a552000 r--s 00013000 08:06 794641     /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
6a552000-6a556000 r-xp 00000000 08:06 663983     /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
6a556000-6a557000 r--p 00003000 08:06 663983     /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
6a557000-6a558000 rw-p 00004000 08:06 663983     /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
6a558000-6a5a7000 r--p 00000000 08:06 14058      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
6a5a7000-6a5ff000 r--p 00000000 08:06 139128     /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
6a5ff000-6a601000 r-xp 00000000 08:06 664561     /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
6a601000-6a602000 r--p 00001000 08:06 664561     /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
6a602000-6a603000 rw-p 00002000 08:06 664561     /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
6a603000-6a604000 r--s 00000000 08:06 680862     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6a604000-6a60a000 r--s 00000000 08:06 680859     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6a60a000-6a60c000 r--s 00000000 08:06 680860     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6a60c000-6a60f000 r--s 00000000 08:06 680870     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6a60f000-6a611000 r--s 00000000 08:06 680847     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6a611000-6a612000 r--s 00000000 08:06 680871     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6a612000-6a615000 r--s 00000000 08:06 680856     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6a615000-6a616000 r--s 00000000 08:06 680851     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6a616000-6a617000 r--s 00000000 08:06 680844     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6a617000-6a618000 r--s 00000000 08:06 680854     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6a618000-6a61c000 r--s 00000000 08:06 680861     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6a61c000-6a623000 r--s 00000000 08:06 656754     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6a623000-6a62e000 r--s 00000000 08:06 680845     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6a62e000-6a631000 r--s 00000000 08:06 680867     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6a631000-6a632000 r--s 00000000 08:06 660604     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
6a632000-6a63a000 r--s 00000000 08:06 680866     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6a63a000-6a63c000 r--s 00000000 08:06 656752     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6a63c000-6a63f000 r--s 00000000 08:06 680858     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6a63f000-6a640000 r--s 00000000 08:06 421451     /home/kalle/.fontconfig/e40a361c340a86a6e3f2027d8a44d45d-le32d4.cache-3
6a642000-6a656000 r-xp 00000000 08:06 664057     /usr/lib/i386-linux-gnu/libICE.so.6.3.0
6a656000-6a657000 r--p 00013000 08:06 664057     /usr/lib/i386-linux-gnu/libICE.so.6.3.0
6a657000-6a658000 rw-p 00014000 08:06 664057     /usr/lib/i386-linux-gnu/libICE.so.6.3.0
6a658000-6a65a000 rw-p 00000000 00:00 0 
6a665000-6a669000 r-xp 00000000 08:06 662300     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6a669000-6a66a000 r--p 00004000 08:06 662300     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6a66a000-6a66b000 rw-p 00005000 08:06 662300     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6a66b000-6a672000 r-xp 00000000 08:06 812408     /usr/lib/fglrx/libatiuki.so.1.0
6a672000-6a673000 rw-p 00006000 08:06 812408     /usr/lib/fglrx/libatiuki.so.1.0
6a674000-6a684000 rw-s fdde0000 00:05 9115       /dev/ati/card0
6a684000-6a6bb000 r-xp 00000000 08:06 656763     /usr/lib/nss/libsoftokn3.so
6a6bb000-6a6bc000 r--p 00036000 08:06 656763     /usr/lib/nss/libsoftokn3.so
6a6bc000-6a6bd000 rw-p 00037000 08:06 656763     /usr/lib/nss/libsoftokn3.so
6a6bd000-6a6ec000 r-xp 00000000 08:06 661885     /usr/lib/libnspr4.so
6a6ec000-6a6ed000 r--p 0002e000 08:06 661885     /usr/lib/libnspr4.so
6a6ed000-6a6ee000 rw-p 0002f000 08:06 661885     /usr/lib/libnspr4.so
6a6ee000-6a6f0000 rw-p 00000000 00:00 0 
6a6f0000-6a7fb000 r-xp 00000000 08:06 656772     /usr/lib/libnss3.so
6a7fb000-6a7fe000 r--p 0010a000 08:06 656772     /usr/lib/libnss3.so
6a7fe000-6a800000 rw-p 0010d000 08:06 656772     /usr/lib/libnss3.so
6a800000-6a8d4000 rw-p 00000000 00:00 0 
6a8d4000-6a900000 ---p 00000000 00:00 0 
6a904000-6a905000 r-xp 00000000 08:06 664061     /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
6a905000-6a906000 r--p 00000000 08:06 664061     /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
6a906000-6a907000 rw-p 00001000 08:06 664061     /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
6a907000-6a90a000 r-xp 00000000 08:06 147000     /home/kalle/.minecraft/bin/natives/libjinput-linux.so
6a90a000-6a90b000 r--p 00002000 08:06 147000     /home/kalle/.minecraft/bin/natives/libjinput-linux.so
6a90b000-6a90c000 rw-p 00003000 08:06 147000     /home/kalle/.minecraft/bin/natives/libjinput-linux.so
6a90c000-6a91b000 r--s 001d9000 08:06 146997     /home/kalle/.minecraft/bin/minecraft.jar
6a91b000-6a91d000 r-xp 00000000 08:06 661955     /usr/lib/libplds4.so
6a91d000-6a91e000 r--p 00001000 08:06 661955     /usr/lib/libplds4.so
6a91e000-6a91f000 rw-p 00002000 08:06 661955     /usr/lib/libplds4.so
6a91f000-6a922000 r-xp 00000000 08:06 661954     /usr/lib/libplc4.so
6a922000-6a923000 r--p 00002000 08:06 661954     /usr/lib/libplc4.so
6a923000-6a924000 rw-p 00003000 08:06 661954     /usr/lib/libplc4.so
6a924000-6a938000 r-xp 00000000 08:06 656771     /usr/lib/libnssutil3.so
6a938000-6a939000 ---p 00014000 08:06 656771     /usr/lib/libnssutil3.so
6a939000-6a93c000 r--p 00014000 08:06 656771     /usr/lib/libnssutil3.so
6a93c000-6a93d000 rw-p 00017000 08:06 656771     /usr/lib/libnssutil3.so
6a940000-6a945000 r--s 00033000 08:06 146995     /home/kalle/.minecraft/bin/jinput.jar
6a945000-6a94e000 r--s 000ac000 08:06 146994     /home/kalle/.minecraft/bin/lwjgl.jar
6a94e000-6a95b000 r-xp 00000000 08:06 797659     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
6a95b000-6a95c000 r--p 0000c000 08:06 797659     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
6a95c000-6a95d000 rw-p 0000d000 08:06 797659     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
6a95d000-6a961000 r--s 00038000 08:06 797592     /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
6a962000-6a963000 r-xp 00000000 08:06 797665     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
6a963000-6a964000 r--p 00000000 08:06 797665     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
6a964000-6a965000 rw-p 00001000 08:06 797665     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
6a965000-6a968000 ---p 00000000 00:00 0 
6a968000-6a9b6000 rw-p 00000000 00:00 0 
6a9b6000-6a9b9000 r--s 0001f000 08:06 146996     /home/kalle/.minecraft/bin/lwjgl_util.jar
6a9b9000-6a9bc000 r--s 00077000 08:06 797593     /usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar
6a9bc000-6a9bf000 ---p 00000000 00:00 0 
6a9bf000-6aa0d000 rw-p 00000000 00:00 0 
6aa0d000-6aa10000 ---p 00000000 00:00 0 
6aa10000-6aa5e000 rw-p 00000000 00:00 0 
6aa5e000-6aa65000 r-xp 00000000 08:06 797662     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
6aa65000-6aa66000 r--p 00006000 08:06 797662     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
6aa66000-6aa67000 rw-p 00007000 08:06 797662     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
6aa67000-6aa7a000 r-xp 00000000 08:06 797694     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
6aa7a000-6aa7b000 r--p 00013000 08:06 797694     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
6aa7b000-6aa7c000 rw-p 00014000 08:06 797694     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
6aa7c000-6aaa9000 r-xp 00000000 08:06 663966     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6aaa9000-6aaaa000 r--p 0002c000 08:06 663966     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6aaaa000-6aaab000 rw-p 0002d000 08:06 663966     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6aaab000-6aab0000 r-xp 00000000 08:06 661911     /usr/lib/libogg.so.0.7.0
6aab0000-6aab1000 r--p 00004000 08:06 661911     /usr/lib/libogg.so.0.7.0
6aab1000-6aab2000 rw-p 00005000 08:06 661911     /usr/lib/libogg.so.0.7.0
6aab2000-6aad7000 r-xp 00000000 08:06 662149     /usr/lib/libvorbis.so.0.4.5
6aad7000-6aad8000 r--p 00025000 08:06 662149     /usr/lib/libvorbis.so.0.4.5
6aad8000-6aad9000 rw-p 00026000 08:06 662149     /usr/lib/libvorbis.so.0.4.5
6aad9000-6aae0000 r-xp 00000000 08:06 661822     /usr/lib/libltdl.so.7.2.1
6aae0000-6aae1000 r--p 00006000 08:06 661822     /usr/lib/libltdl.so.7.2.1
6aae1000-6aae2000 rw-p 00007000 08:06 661822     /usr/lib/libltdl.so.7.2.1
6aae2000-6aaf1000 r-xp 00000000 08:06 662087     /usr/lib/libtdb.so.1.2.9
6aaf1000-6aaf2000 r--p 0000e000 08:06 662087     /usr/lib/libtdb.so.1.2.9
6aaf2000-6aaf3000 rw-p 0000f000 08:06 662087     /usr/lib/libtdb.so.1.2.9
6aaf3000-6aafa000 r-xp 00000000 08:06 662153     /usr/lib/libvorbisfile.so.3.3.4
6aafa000-6aafb000 r--p 00006000 08:06 662153     /usr/lib/libvorbisfile.so.3.3.4
6aafb000-6aafc000 rw-p 00007000 08:06 662153     /usr/lib/libvorbisfile.so.3.3.4
6aafc000-6ab0a000 r-xp 00000000 08:06 661391     /usr/lib/libcanberra.so.0.2.5
6ab0a000-6ab0b000 r--p 0000d000 08:06 661391     /usr/lib/libcanberra.so.0.2.5
6ab0b000-6ab0c000 rw-p 0000e000 08:06 661391     /usr/lib/libcanberra.so.0.2.5
6ab0c000-6ab0f000 r-xp 00000000 08:06 661389     /usr/lib/libcanberra-gtk.so.0.1.8
6ab0f000-6ab10000 r--p 00002000 08:06 661389     /usr/lib/libcanberra-gtk.so.0.1.8
6ab10000-6ab11000 rw-p 00003000 08:06 661389     /usr/lib/libcanberra-gtk.so.0.1.8
6ab12000-6ab16000 r-xp 00000000 08:06 663974     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
6ab16000-6ab17000 r--p 00003000 08:06 663974     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
6ab17000-6ab18000 rw-p 00004000 08:06 663974     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
6ab18000-6ab1f000 r-xp 00000000 08:06 663967     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
6ab1f000-6ab20000 ---p 00007000 08:06 663967     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
6ab20000-6ab21000 r--p 00007000 08:06 663967     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
6ab21000-6ab22000 rw-p 00008000 08:06 663967     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
6ab22000-6ab48000 r-xp 00000000 08:06 526173     /lib/i386-linux-gnu/libexpat.so.1.5.2
6ab48000-6ab49000 ---p 00026000 08:06 526173     /lib/i386-linux-gnu/libexpat.so.1.5.2
6ab49000-6ab4b000 r--p 00026000 08:06 526173     /lib/i386-linux-gnu/libexpat.so.1.5.2
6ab4b000-6ab4c000 rw-p 00028000 08:06 526173     /lib/i386-linux-gnu/libexpat.so.1.5.2
6ab4c000-6ab65000 r-xp 00000000 08:06 526221     /lib/i386-linux-gnu/libselinux.so.1
6ab65000-6ab66000 r--p 00018000 08:06 526221     /lib/i386-linux-gnu/libselinux.so.1
6ab66000-6ab67000 rw-p 00019000 08:06 526221     /lib/i386-linux-gnu/libselinux.so.1
6ab67000-6ab78000 r-xp 00000000 08:06 526217     /lib/i386-linux-gnu/libresolv-2.13.so
6ab78000-6ab79000 r--p 00010000 08:06 526217     /lib/i386-linux-gnu/libresolv-2.13.so
6ab79000-6ab7a000 rw-p 00011000 08:06 526217     /lib/i386-linux-gnu/libresolv-2.13.so
6ab7a000-6ab7c000 rw-p 00000000 00:00 0 
6ab7c000-6abb9000 r-xp 00000000 08:06 526212     /lib/i386-linux-gnu/libpcre.so.3.12.1
6abb9000-6abba000 r--p 0003c000 08:06 526212     /lib/i386-linux-gnu/libpcre.so.3.12.1
6abba000-6abbb000 rw-p 0003d000 08:06 526212     /lib/i386-linux-gnu/libpcre.so.3.12.1
6abbb000-6abde000 r-xp 00000000 08:06 525700     /lib/i386-linux-gnu/libpng12.so.0.44.0
6abde000-6abdf000 r--p 00022000 08:06 525700     /lib/i386-linux-gnu/libpng12.so.0.44.0
6abdf000-6abe0000 rw-p 00023000 08:06 525700     /lib/i386-linux-gnu/libpng12.so.0.44.0
6abe0000-6ac47000 r-xp 00000000 08:06 661953     /usr/lib/libpixman-1.so.0.20.2
6ac47000-6ac48000 ---p 00067000 08:06 661953     /usr/lib/libpixman-1.so.0.20.2
6ac48000-6ac4b000 r--p 00067000 08:06 661953     /usr/lib/libpixman-1.so.0.20.2
6ac4b000-6ac4c000 rw-p 0006a000 08:06 661953     /usr/lib/libpixman-1.so.0.20.2
6ac4c000-6ad21000 r-xp 00000000 08:06 526182     /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
6ad21000-6ad22000 r--p 000d4000 08:06 526182     /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
6ad22000-6ad23000 rw-p 000d5000 08:06 526182     /lib/i386-linux-gnu/libglib-2.0.so.0.2800.6
6ad23000-6ad68000 r-xp 00000000 08:06 664140     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
6ad68000-6ad69000 r--p 00044000 08:06 664140     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
6ad69000-6ad6a000 rw-p 00045000 08:06 664140     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
6ad6a000-6ad97000 r-xp 00000000 08:06 664121     /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
6ad97000-6ad98000 r--p 0002c000 08:06 664121     /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
6ad98000-6ad99000 rw-p 0002d000 08:06 664121     /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
6ad99000-6add7000 r-xp 00000000 08:06 664174     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
6add7000-6add8000 r--p 0003e000 08:06 664174     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
6add8000-6add9000 rw-p 0003f000 08:06 664174     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
6add9000-6adfe000 r-xp 00000000 08:06 664178     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2800.4
6adfe000-6adff000 ---p 00025000 08:06 664178     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2800.4
6adff000-6ae00000 r--p 00025000 08:06 664178     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2800.4
6ae00000-6ae01000 rw-p 00026000 08:06 664178     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2800.4
6ae01000-6aeff000 r-xp 00000000 08:06 664130     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2800.6
6aeff000-6af00000 ---p 000fe000 08:06 664130     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2800.6
6af00000-6af02000 r--p 000fe000 08:06 664130     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2800.6
6af02000-6af03000 rw-p 00100000 08:06 664130     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.2800.6
6af03000-6af04000 rw-p 00000000 00:00 0 
6af04000-6af1f000 r-xp 00000000 08:06 661547     /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
6af1f000-6af20000 r--p 0001a000 08:06 661547     /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
6af20000-6af21000 rw-p 0001b000 08:06 661547     /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
6af21000-6afcf000 r-xp 00000000 08:06 661381     /usr/lib/libcairo.so.2.11000.2
6afcf000-6afd0000 ---p 000ae000 08:06 661381     /usr/lib/libcairo.so.2.11000.2
6afd0000-6afd1000 r--p 000ae000 08:06 661381     /usr/lib/libcairo.so.2.11000.2
6afd1000-6afd2000 rw-p 000af000 08:06 661381     /usr/lib/libcairo.so.2.11000.2
6afd2000-6afd4000 rw-p 00000000 00:00 0 
6afd4000-6afed000 r-xp 00000000 08:06 664095     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.9.1
6afed000-6afee000 ---p 00019000 08:06 664095     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.9.1
6afee000-6afef000 r--p 00019000 08:06 664095     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.9.1
6afef000-6aff0000 rw-p 0001a000 08:06 664095     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.9.1
6aff0000-6b085000 r-xp 00000000 08:06 661545     /usr/lib/libgdk-x11-2.0.so.0.2400.4
6b085000-6b086000 ---p 00095000 08:06 661545     /usr/lib/libgdk-x11-2.0.so.0.2400.4
6b086000-6b088000 r--p 00095000 08:06 661545     /usr/lib/libgdk-x11-2.0.so.0.2400.4
6b088000-6b089000 rw-p 00097000 08:06 661545     /usr/lib/libgdk-x11-2.0.so.0.2400.4
6b089000-6b45a000 r-xp 00000000 08:06 661691     /usr/lib/libgtk-x11-2.0.so.0.2400.4
6b45a000-6b45e000 r--p 003d0000 08:06 661691     /usr/lib/libgtk-x11-2.0.so.0.2400.4
6b45e000-6b460000 rw-p 003d4000 08:06 661691     /usr/lib/libgtk-x11-2.0.so.0.2400.4
6b460000-6b462000 rw-p 00000000 00:00 0 
6b462000-6b465000 ---p 00000000 00:00 0 
6b465000-6b4b3000 rw-p 00000000 00:00 0 
6b4b3000-6b4b6000 ---p 00000000 00:00 0 
6b4b6000-6b504000 rw-p 00000000 00:00 0 
6b504000-6b505000 r--s 00000000 08:06 680862     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6b505000-6b50b000 r--s 00000000 08:06 680859     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6b50b000-6b50d000 r--s 00000000 08:06 680860     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6b50d000-6b510000 r--s 00000000 08:06 680870     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6b510000-6b512000 r--s 00000000 08:06 680847     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6b512000-6b513000 r--s 00000000 08:06 680871     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6b513000-6b516000 r--s 00000000 08:06 680856     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6b516000-6b517000 r--s 00000000 08:06 680851     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6b518000-6b51e000 r-xp 00000000 08:06 664208     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
6b51e000-6b51f000 r--p 00005000 08:06 664208     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
6b51f000-6b520000 rw-p 00006000 08:06 664208     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
6b520000-6b522000 r-xp 00000000 08:06 664212     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
6b522000-6b523000 r--p 00001000 08:06 664212     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
6b523000-6b524000 rw-p 00002000 08:06 664212     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
6b524000-6b52a000 r-xp 00000000 08:06 664085     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
6b52a000-6b52b000 r--p 00005000 08:06 664085     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
6b52b000-6b52c000 rw-p 00006000 08:06 664085     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
6b52c000-6b52e000 r-xp 00000000 08:06 664083     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
6b52e000-6b52f000 r--p 00001000 08:06 664083     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
6b52f000-6b530000 rw-p 00002000 08:06 664083     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
6b530000-6b531000 rw-s 00005000 00:05 9115       /dev/ati/card0
6b531000-6b535000 r-xp 00000000 08:06 663989     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6b535000-6b536000 r--p 00003000 08:06 663989     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6b536000-6b537000 rw-p 00004000 08:06 663989     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6b537000-6b53f000 r-xp 00000000 08:06 658052     /usr/lib/liboverlay-scrollbar-0.1.so.0.0.12
6b53f000-6b540000 r--p 00007000 08:06 658052     /usr/lib/liboverlay-scrollbar-0.1.so.0.0.12
6b540000-6b541000 rw-p 00008000 08:06 658052     /usr/lib/liboverlay-scrollbar-0.1.so.0.0.12
6b541000-6b542000 r--s 00000000 08:06 680862     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6b542000-6b548000 r--s 00000000 08:06 680859     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6b548000-6b54a000 r--s 00000000 08:06 680860     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6b54a000-6b54d000 r--s 00000000 08:06 680870     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6b54d000-6b551000 r--s 00000000 08:06 680861     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6b551000-6b558000 r--s 00000000 08:06 656754     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6b558000-6b563000 r--s 00000000 08:06 680845     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6b563000-6b567000 r--s 00000000 08:06 680861     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6b567000-6b56e000 r--s 00000000 08:06 656754     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6b56e000-6b579000 r--s 00000000 08:06 680845     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6b579000-6b57c000 r--s 00000000 08:06 680867     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6b57c000-6b57d000 r--p 002a1000 08:06 665734     /usr/lib/locale/locale-archive
6b57d000-6b580000 r-xp 00000000 08:06 664146     /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
6b580000-6b581000 r--p 00003000 08:06 664146     /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
6b581000-6b582000 rw-p 00004000 08:06 664146     /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
6b582000-6b584000 r-xp 00000000 08:06 664132     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
6b584000-6b585000 r--p 00002000 08:06 664132     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
6b585000-6b586000 rw-p 00003000 08:06 664132     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
6b586000-6b588000 r-xp 00000000 08:06 664071     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
6b588000-6b589000 r--p 00001000 08:06 664071     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
6b589000-6b58a000 rw-p 00002000 08:06 664071     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
6b58a000-6b58e000 r-xp 00000000 08:06 664077     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
6b58e000-6b58f000 r--p 00003000 08:06 664077     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
6b58f000-6b590000 rw-p 00004000 08:06 664077     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
6b590000-6b598000 r-xp 00000000 08:06 664069     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
6b598000-6b599000 r--p 00007000 08:06 664069     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
6b599000-6b59a000 rw-p 00008000 08:06 664069     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
6b59a000-6b59c000 r-xp 00000000 08:06 664067     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
6b59c000-6b59d000 r--p 00001000 08:06 664067     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
6b59d000-6b59e000 rw-p 00002000 08:06 664067     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
6b59e000-6b5a8000 r-xp 00000000 08:06 664176     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
6b5a8000-6b5a9000 r--p 00009000 08:06 664176     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
6b5a9000-6b5aa000 rw-p 0000a000 08:06 664176     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
6b5aa000-6b5ab000 r--p 00000000 00:00 0 
6b5ab000-6b5ac000 r--s 00000000 08:06 680844     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6b5ac000-6b5ad000 r--s 00000000 08:06 680854     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6b5ad000-6b5ae000 r--s 00000000 08:06 660604     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
6b5ae000-6b5b6000 r--s 00000000 08:06 680866     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6b5b6000-6b5b8000 r--s 00000000 08:06 656752     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6b5b8000-6b5bb000 r--s 00000000 08:06 680858     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6b5bb000-6b5bc000 r--s 00000000 08:06 421451     /home/kalle/.fontconfig/e40a361c340a86a6e3f2027d8a44d45d-le32d4.cache-3
6b5bc000-6b5bf000 ---p 00000000 00:00 0 
6b5bf000-6b60d000 rw-p 00000000 00:00 0 
6b60d000-6b68e000 r-xp 00000000 08:06 665904     /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
6b68e000-6b692000 r--p 00080000 08:06 665904     /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
6b692000-6b693000 rw-p 00084000 08:06 665904     /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
6b693000-6b6cb000 r-xp 00000000 08:06 797696     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
6b6cb000-6b6cc000 ---p 00038000 08:06 797696     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
6b6cc000-6b6cd000 r--p 00038000 08:06 797696     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
6b6cd000-6b6ce000 rw-p 00039000 08:06 797696     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
6b6ce000-6b6d2000 r-xp 00000000 08:06 664073     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
6b6d2000-6b6d3000 r--p 00003000 08:06 664073     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
6b6d3000-6b6d4000 rw-p 00004000 08:06 664073     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
6b6d4000-6b6d6000 r-xp 00000000 08:06 664065     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
6b6d6000-6b6d7000 r--p 00001000 08:06 664065     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
6b6d7000-6b6d8000 rw-p 00002000 08:06 664065     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
6b6d8000-6b6ef000 r-xp 00000000 08:06 664214     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
6b6ef000-6b6f0000 r--p 00016000 08:06 664214     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
6b6f0000-6b6f1000 rw-p 00017000 08:06 664214     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
6b6f1000-6b6fe000 r-xp 00000000 08:06 664081     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
6b6fe000-6b6ff000 r--p 0000c000 08:06 664081     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
6b6ff000-6b700000 rw-p 0000d000 08:06 664081     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
6b700000-6b704000 r-xp 00000000 08:06 661317     /usr/lib/libXtst.so.6.1.0
6b704000-6b705000 r--p 00003000 08:06 661317     /usr/lib/libXtst.so.6.1.0
6b705000-6b706000 rw-p 00004000 08:06 661317     /usr/lib/libXtst.so.6.1.0
6b706000-6b70e000 r-xp 00000000 08:06 664087     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
6b70e000-6b70f000 r--p 00007000 08:06 664087     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
6b70f000-6b710000 rw-p 00008000 08:06 664087     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
6b710000-6b826000 r-xp 00000000 08:06 664063     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
6b826000-6b827000 ---p 00116000 08:06 664063     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
6b827000-6b828000 r--p 00116000 08:06 664063     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
6b828000-6b82a000 rw-p 00117000 08:06 664063     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
6b82a000-6b82b000 rw-p 00000000 00:00 0 
6b82b000-6b838000 r-xp 00000000 08:06 664075     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
6b838000-6b839000 r--p 0000c000 08:06 664075     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
6b839000-6b83a000 rw-p 0000d000 08:06 664075     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
6b83a000-6b83c000 r--s 00000000 08:06 680847     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6b83c000-6b83d000 r--s 00000000 08:06 660604     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
6b83d000-6b845000 r--s 00000000 08:06 680866     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6b845000-6b847000 r--s 00000000 08:06 656752     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6b847000-6b84a000 r--s 00000000 08:06 680858     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6b84a000-6b84b000 r--s 00000000 08:06 421451     /home/kalle/.fontconfig/e40a361c340a86a6e3f2027d8a44d45d-le32d4.cache-3
6b84b000-6b8d4000 r-xp 00000000 08:06 797661     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
6b8d4000-6b8d5000 r--p 00088000 08:06 797661     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
6b8d5000-6b8dc000 rw-p 00089000 08:06 797661     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
6b8dc000-6b900000 rw-p 00000000 00:00 0 
6b900000-6b9fc000 rw-p 00000000 00:00 0 
6b9fc000-6ba00000 ---p 00000000 00:00 0 
6ba00000-6ba03000 r--s 00000000 08:06 680856     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6ba03000-6ba46000 r-xp 00000000 08:06 798091     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
6ba46000-6ba47000 r--p 00042000 08:06 798091     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
6ba47000-6ba49000 rw-p 00043000 08:06 798091     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
6ba49000-6ba4a000 rw-p 00000000 00:00 0 
6ba4a000-6ba51000 r--s 000fb000 08:06 797605     /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
6ba51000-6ba59000 r--s 00066000 08:06 2230       /usr/share/java/gnome-java-bridge.jar
6ba59000-6ba5a000 ---p 00000000 00:00 0 
6ba5a000-6bada000 rw-p 00000000 00:00 0 
6bada000-6badd000 ---p 00000000 00:00 0 
6badd000-6bb2b000 rw-p 00000000 00:00 0 
6bb2b000-6bb2e000 ---p 00000000 00:00 0 
6bb2e000-6bbac000 rw-p 00000000 00:00 0 
6bbac000-6bbaf000 ---p 00000000 00:00 0 
6bbaf000-6bc2d000 rw-p 00000000 00:00 0 
6bc2d000-6bc30000 ---p 00000000 00:00 0 
6bc30000-6bc7e000 rw-p 00000000 00:00 0 
6bc7e000-6bd9e000 r--p 0090e000 08:06 665734     /usr/lib/locale/locale-archive
6bd9e000-6bf9e000 r--p 00000000 08:06 665734     /usr/lib/locale/locale-archive
6bf9e000-6bfa1000 ---p 00000000 00:00 0 
6bfa1000-6bfef000 rw-p 00000000 00:00 0 
6bfef000-6bff0000 ---p 00000000 00:00 0 
6bff0000-6c070000 rw-p 00000000 00:00 0 
6c070000-6c200000 r--s 037af000 08:06 797699     /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
6c200000-6c2ff000 rw-p 00000000 00:00 0 
6c2ff000-6c300000 ---p 00000000 00:00 0 
6c300000-6c303000 ---p 00000000 00:00 0 
6c303000-6c384000 rw-p 00000000 00:00 0 
6c384000-6c385000 ---p 00000000 00:00 0 
6c385000-6c405000 rw-p 00000000 00:00 0 
6c405000-6c406000 ---p 00000000 00:00 0 
6c406000-6c486000 rw-p 00000000 00:00 0 
6c486000-6c487000 ---p 00000000 00:00 0 
6c487000-6c507000 rw-p 00000000 00:00 0 
6c507000-6c508000 ---p 00000000 00:00 0 
6c508000-6c59d000 rw-p 00000000 00:00 0 
6c59d000-6c5c8000 rw-p 00000000 00:00 0 
6c5c8000-6c5e7000 rw-p 00000000 00:00 0 
6c5e7000-6c718000 rw-p 00000000 00:00 0 
6c718000-6c72d000 rw-p 00000000 00:00 0 
6c72d000-6c758000 rw-p 00000000 00:00 0 
6c758000-6c777000 rw-p 00000000 00:00 0 
6c777000-6c8a7000 rw-p 00000000 00:00 0 
6c8a7000-6c8d8000 rw-p 00000000 00:00 0 
6c8d8000-6c8da000 ---p 00000000 00:00 0 
6c8da000-6c94f000 rw-p 00000000 00:00 0 
6c94f000-6f2d0000 rw-p 00000000 00:00 0 
6f2d0000-74950000 rw-p 00000000 00:00 0 
74950000-786c0000 rw-p 00000000 00:00 0 
786c0000-9e800000 rw-p 00000000 00:00 0 
9e800000-a47d0000 rw-p 00000000 00:00 0 
a47d0000-a4cd0000 ---p 00000000 00:00 0 
a4cd0000-b3750000 rw-p 00000000 00:00 0 
b3750000-b3753000 r--s 00000000 08:06 680867     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b3753000-b3757000 r--s 0007c000 08:06 794640     /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
b3757000-b3760000 rw-p 00000000 00:00 0 
b3760000-b3817000 rw-p 00000000 00:00 0 
b3817000-b3a57000 rwxp 00000000 00:00 0 
b3a57000-b6817000 rw-p 00000000 00:00 0 
b6817000-b6821000 r-xp 00000000 08:06 526196     /lib/i386-linux-gnu/libnss_files-2.13.so
b6821000-b6822000 r--p 00009000 08:06 526196     /lib/i386-linux-gnu/libnss_files-2.13.so
b6822000-b6823000 rw-p 0000a000 08:06 526196     /lib/i386-linux-gnu/libnss_files-2.13.so
b6823000-b682c000 r-xp 00000000 08:06 526200     /lib/i386-linux-gnu/libnss_nis-2.13.so
b682c000-b682d000 r--p 00008000 08:06 526200     /lib/i386-linux-gnu/libnss_nis-2.13.so
b682d000-b682e000 rw-p 00009000 08:06 526200     /lib/i386-linux-gnu/libnss_nis-2.13.so
b682e000-b682f000 r--s 00000000 08:06 680871     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b682f000-b6835000 r-xp 00000000 08:06 797663     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
b6835000-b6836000 r--p 00005000 08:06 797663     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
b6836000-b6837000 rw-p 00006000 08:06 797663     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
b6837000-b683f000 rw-s 00000000 08:06 274042     /tmp/hsperfdata_kalle/2073
b683f000-b6852000 r-xp 00000000 08:06 526190     /lib/i386-linux-gnu/libnsl-2.13.so
b6852000-b6853000 r--p 00012000 08:06 526190     /lib/i386-linux-gnu/libnsl-2.13.so
b6853000-b6854000 rw-p 00013000 08:06 526190     /lib/i386-linux-gnu/libnsl-2.13.so
b6854000-b6856000 rw-p 00000000 00:00 0 
b6856000-b6857000 r--s 00000000 08:06 680851     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b6857000-b6858000 r--s 00000000 08:06 680844     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b6858000-b685a000 r--s 00014000 08:06 146988     /home/kalle/Desktop/minecraft.jar
b685a000-b685d000 r--s 0000f000 08:06 797597     /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b685d000-b6863000 r-xp 00000000 08:06 526192     /lib/i386-linux-gnu/libnss_compat-2.13.so
b6863000-b6864000 r--p 00005000 08:06 526192     /lib/i386-linux-gnu/libnss_compat-2.13.so
b6864000-b6865000 rw-p 00006000 08:06 526192     /lib/i386-linux-gnu/libnss_compat-2.13.so
b6865000-b6866000 rw-p 00000000 00:00 0 
b6866000-b6867000 r--p 00000000 00:00 0 
b6867000-b688a000 r-xp 00000000 08:06 797658     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
b688a000-b688b000 r--p 00022000 08:06 797658     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
b688b000-b688d000 rw-p 00023000 08:06 797658     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
b688d000-b6894000 r-xp 00000000 08:06 526219     /lib/i386-linux-gnu/librt-2.13.so
b6894000-b6895000 r--p 00006000 08:06 526219     /lib/i386-linux-gnu/librt-2.13.so
b6895000-b6896000 rw-p 00007000 08:06 526219     /lib/i386-linux-gnu/librt-2.13.so
b6896000-b6899000 ---p 00000000 00:00 0 
b6899000-b68e7000 rw-p 00000000 00:00 0 
b68e7000-b6901000 r-xp 00000000 08:06 526178     /lib/i386-linux-gnu/libgcc_s.so.1
b6901000-b6902000 r--p 00019000 08:06 526178     /lib/i386-linux-gnu/libgcc_s.so.1
b6902000-b6903000 rw-p 0001a000 08:06 526178     /lib/i386-linux-gnu/libgcc_s.so.1
b6903000-b6927000 r-xp 00000000 08:06 526187     /lib/i386-linux-gnu/libm-2.13.so
b6927000-b6928000 r--p 00023000 08:06 526187     /lib/i386-linux-gnu/libm-2.13.so
b6928000-b6929000 rw-p 00024000 08:06 526187     /lib/i386-linux-gnu/libm-2.13.so
b6929000-b6a08000 r-xp 00000000 08:06 664196     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
b6a08000-b6a0c000 r--p 000de000 08:06 664196     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
b6a0c000-b6a0d000 rw-p 000e2000 08:06 664196     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
b6a0d000-b6a14000 rw-p 00000000 00:00 0 
b6a14000-b70da000 r-xp 00000000 08:06 797677     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
b70da000-b70db000 ---p 006c6000 08:06 797677     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
b70db000-b7120000 r--p 006c6000 08:06 797677     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
b7120000-b712f000 rw-p 0070b000 08:06 797677     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
b712f000-b754b000 rw-p 00000000 00:00 0 
b754b000-b76a5000 r-xp 00000000 08:06 526150     /lib/i386-linux-gnu/libc-2.13.so
b76a5000-b76a6000 ---p 0015a000 08:06 526150     /lib/i386-linux-gnu/libc-2.13.so
b76a6000-b76a8000 r--p 0015a000 08:06 526150     /lib/i386-linux-gnu/libc-2.13.so
b76a8000-b76a9000 rw-p 0015c000 08:06 526150     /lib/i386-linux-gnu/libc-2.13.so
b76a9000-b76ac000 rw-p 00000000 00:00 0 
b76ac000-b76ae000 r-xp 00000000 08:06 526160     /lib/i386-linux-gnu/libdl-2.13.so
b76ae000-b76af000 r--p 00001000 08:06 526160     /lib/i386-linux-gnu/libdl-2.13.so
b76af000-b76b0000 rw-p 00002000 08:06 526160     /lib/i386-linux-gnu/libdl-2.13.so
b76b0000-b76b3000 r-xp 00000000 08:06 797667     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
b76b3000-b76b4000 r--p 00002000 08:06 797667     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
b76b4000-b76b5000 rw-p 00003000 08:06 797667     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
b76b5000-b76ca000 r-xp 00000000 08:06 526215     /lib/i386-linux-gnu/libpthread-2.13.so
b76ca000-b76cb000 r--p 00015000 08:06 526215     /lib/i386-linux-gnu/libpthread-2.13.so
b76cb000-b76cc000 rw-p 00016000 08:06 526215     /lib/i386-linux-gnu/libpthread-2.13.so
b76cc000-b76cf000 rw-p 00000000 00:00 0 
b76cf000-b76e2000 r-xp 00000000 08:06 526233     /lib/i386-linux-gnu/libz.so.1.2.3.4
b76e2000-b76e3000 r--p 00012000 08:06 526233     /lib/i386-linux-gnu/libz.so.1.2.3.4
b76e3000-b76e4000 rw-p 00013000 08:06 526233     /lib/i386-linux-gnu/libz.so.1.2.3.4
b76e4000-b76e5000 r--s 00000000 08:06 680854     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b76e5000-b76e7000 rw-s 00002000 00:05 9115       /dev/ati/card0
b76e7000-b76f2000 r-xp 00000000 08:06 797686     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
b76f2000-b76f3000 ---p 0000b000 08:06 797686     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
b76f3000-b76f4000 r--p 0000b000 08:06 797686     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
b76f4000-b76f5000 rw-p 0000c000 08:06 797686     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
b76f5000-b76f7000 rw-p 00000000 00:00 0 
b76f7000-b76f8000 r-xp 00000000 00:00 0          [vdso]
b76f8000-b7714000 r-xp 00000000 08:06 526137     /lib/i386-linux-gnu/ld-2.13.so
b7714000-b7715000 r--p 0001b000 08:06 526137     /lib/i386-linux-gnu/ld-2.13.so
b7715000-b7716000 rw-p 0001c000 08:06 526137     /lib/i386-linux-gnu/ld-2.13.so
bf994000-bf9ca000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
java_command: minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=kalle
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x656ef0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x656ef0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x51d410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x51d410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x51d410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x51d280], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x520070], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x520070], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x520070], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x520070], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 11.04 (natty)
uname:Linux 2.6.38-11-generic-pae #50-Ubuntu SMP Mon Sep 12 22:21:04 UTC 2011 i686
libc:glibc 2.13 NPTL 2.13 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 4096, AS infinity
load average:0,05 0,30 0,34

/proc/meminfo:
MemTotal:        4119460 kB
MemFree:         1989736 kB
Buffers:          452248 kB
Cached:           763584 kB
SwapCached:            0 kB
Active:           798424 kB
Inactive:        1102300 kB
Active(anon):     685724 kB
Inactive(anon):    10432 kB
Active(file):     112700 kB
Inactive(file):  1091868 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       3279752 kB
HighFree:        1693544 kB
LowTotal:         839708 kB
LowFree:          296192 kB
SwapTotal:       4185084 kB
SwapFree:        4185084 kB
Dirty:               196 kB
Writeback:             0 kB
AnonPages:        685172 kB
Mapped:           154192 kB
Shmem:             11268 kB
Slab:              36000 kB
SReclaimable:      22248 kB
SUnreclaim:        13752 kB
KernelStack:        2984 kB
PageTables:         6840 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6244812 kB
Committed_AS:    2112800 kB
VmallocTotal:     122880 kB
VmallocUsed:       58504 kB
VmallocChunk:      59892 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       10232 kB
DirectMap2M:      903168 kB


CPU:total 4 (4 cores per cpu, 1 threads per core) family 16 model 4 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext, 3dnow, 3dnowext, lzcnt, sse4a

Memory: 4k page, physical 4119460k(1989736k free), swap 4185084k(4185084k free)

vm_info: OpenJDK Server VM (20.0-b11) for linux-x86 JRE (1.6.0_22-b22), built on Jun 11 2011 05:56:20 by "buildd" with gcc 4.5.2

time: Fri Sep 30 17:03:42 2011
elapsed time: 20 seconds


Help please?

---

### Post by megabuffen on 2011-09-30
After reading up on the issue, it seems to be a typical AMD/ATI problem. The latest proprietary ATI drivers for Ubuntu 11.04 are causing trouble. Seems like my next planned upgrade will be nVidia. At least my AMD CPU is working though.

---

