---
title: "Mo' Creatures for Minecraft refusing to work"
date: 2011-12-20
forum: General Help
---

### Post by Yuffie yamamoto on 2011-12-20
Hello I was wondering if anyone has experienced this problem or even if you haven't if you would be able to help me with the above mentioned problem.

For about one month I have been trying to get the mo' creatures mod by DrZhark to work. I have tried several tactics and finally decided maybe I should just post my problem here. For some weird reason even though it seems I have installed audiomod, modloader custom spawner, and Gui api correctly (no black screens or frozen screens) when I finally come to a new world no new creatures have spawned. I have done as the creator asked and updated lwjgl and waited several days and nights in the world but still no creatures.

I am an Ubuntu newbie and do not understand the operating system I am using now. So if you can find a way to help me please have patience with me when I ask for exact steps.

Computer Specifics: 
Gateway
Ubuntu 11.04 (natty)
kernel linux 2.6.38-8-generic
GNOME 2.32.1

1.6 GiB
processor 0:AMD Turion(tm) 64X2 Mobile Technology TL-60
processor 1: AMD Turion(tm) 64 X2 Mobile Technology TL-60

211.0GiB available space
ATI radeon graphics

Minecraft specifics: 
version 1.0.0
optifine installed successfully
single player commands installed successfully
openJDK java (no problems with it)

Tried:
1. [http://www.youtube.com/watch?v=SslgINvC55w](http://www.youtube.com/watch?v=SslgINvC55w)
2. followed all instructions and tutorial videos on the actual mod page
3. [http://www.youtube.com/watch?v=amwavLyGHNs&feature=related](http://www.youtube.com/watch?v=amwavLyGHNs&feature=related)
4. [http://www.youtube.com/watch?v=VWn4328IclI](http://www.youtube.com/watch?v=VWn4328IclI)
*Note*I am in no way saying the tutors in the videos and links before were wrong only that their methods do not seem to work for me or I am missing steps which are  simple/major.

I will also try any tutorial pertaining to THIS problem I have a clean computer and am not afraid to start a fresh minecraft jar I know how to back up my worlds.
Any and especially all help is appreciated. Thank you all.

---

### Post by ronnoc on 2012-01-09
> **Yuffie yamamoto said:**
> Hello I was wondering if anyone has experienced this problem or even if you haven't if you would be able to help me with the above mentioned problem.

For about one month I have been trying to get the mo' creatures mod by DrZhark to work. I have tried several tactics and finally decided maybe I should just post my problem here. For some weird reason even though it seems I have installed audiomod, modloader custom spawner, and Gui api correctly (no black screens or frozen screens) when I finally come to a new world no new creatures have spawned. I have done as the creator asked and updated lwjgl and waited several days and nights in the world but still no creatures.

I am an Ubuntu newbie and do not understand the operating system I am using now. So if you can find a way to help me please have patience with me when I ask for exact steps.

Computer Specifics: 
Gateway
Ubuntu 11.04 (natty)
kernel linux 2.6.38-8-generic
GNOME 2.32.1

1.6 GiB
processor 0:AMD Turion(tm) 64X2 Mobile Technology TL-60
processor 1: AMD Turion(tm) 64 X2 Mobile Technology TL-60

211.0GiB available space
ATI radeon graphics

Minecraft specifics: 
version 1.0.0
optifine installed successfully
single player commands installed successfully
openJDK java (no problems with it)

Tried:
1. [http://www.youtube.com/watch?v=SslgINvC55w](http://www.youtube.com/watch?v=SslgINvC55w)
2. followed all instructions and tutorial videos on the actual mod page
3. [http://www.youtube.com/watch?v=amwavLyGHNs&feature=related](http://www.youtube.com/watch?v=amwavLyGHNs&feature=related)
4. [http://www.youtube.com/watch?v=VWn4328IclI](http://www.youtube.com/watch?v=VWn4328IclI)
*Note*I am in no way saying the tutors in the videos and links before were wrong only that their methods do not seem to work for me or I am missing steps which are  simple/major.

I will also try any tutorial pertaining to THIS problem I have a clean computer and am not afraid to start a fresh minecraft jar I know how to back up my worlds.
Any and especially all help is appreciated. Thank you all.

Same issue here on Kubuntu. There's obviouisly some Canonical-specific java thing causing this to not work, since it appears to have worked in the past, and on other distributions. I really want this to work. :/ 

Here's my last error log:

> #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fa569450c08, pid=2986, tid=140348434794240
#
# JRE version: 6.0_23-b23
# Java VM: OpenJDK 64-Bit Server VM (20.0-b11 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.11pre
# Distribution: Ubuntu 11.10, package 6b23~pre11-0ubuntu1.11.10
# Problematic frame:
# C  [libX11.so.6+0x35c08]  XQueryExtension+0x28
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

---------------  T H R E A D  ---------------

Current thread (0x00007fa564056000):  VMThread [stack: 0x00007fa56a89c000,0x00007fa56a99d000] [id=2992]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x0000000064350998

Registers:
RAX=0x0000000002630420, RBX=0x0000000064350030, RCX=0x00007fa56a99b5c8, RDX=0x00007fa56a99b5c4
RSP=0x00007fa56a99b560, RBP=0x00007fa55fd582d2, RSI=0x00007fa55fd582d2, RDI=0x0000000064350030
R8 =0x00007fa56a99b5cc, R9 =0x0000000000000000, R10=0x00007fa57155bea8, R11=0x00007fa5711fbba0
R12=0x00007fa56a99b5c4, R13=0x00007fa55fd582d2, R14=0x0000000002630420, R15=0x0000000000000000
RIP=0x00007fa569450c08, EFLAGS=0x0000000000010206, CSGSFS=0x0000000000000033, ERR=0x0000000000000004
  TRAPNO=0x000000000000000e

Top of Stack: (sp=0x00007fa56a99b560)
0x00007fa56a99b560:   00007fa5711ce5c8 00007fa571d809e0
0x00007fa56a99b570:   00007fa571da6048 00007fa57155a1c0
0x00007fa56a99b580:   0000000000000000 0000000064350030
0x00007fa56a99b590:   00007fa55fd582d2 0000000000000000
0x00007fa56a99b5a0:   00007fa55fd582d2 0000000002630420
0x00007fa56a99b5b0:   0000000000000000 00007fa5694444f5
0x00007fa56a99b5c0:   00007fa571da6048 00007fa55fe8fe60
0x00007fa56a99b5d0:   00007fa55fe8fe60 0000000064350030
0x00007fa56a99b5e0:   00000000020ed780 00007fa56976173b
0x00007fa56a99b5f0:   0000000002630420 00000011711ce5c8
0x00007fa56a99b600:   00007fa56a99b680 0000000000000000
0x00007fa56a99b610:   00007fa56a99b680 0000000064350030
0x00007fa56a99b620:   0000000000000000 00007fa571da6048
0x00007fa56a99b630:   00007fa55fea8ed0 00007fa55fcfef49
0x00007fa56a99b640:   0000000000000000 0000000000000049
0x00007fa56a99b650:   00007fa56a99b680 00007fa56a99b6a0
0x00007fa56a99b660:   0000000000000000 00007fa571da6048
0x00007fa56a99b670:   00007fa56414e4d0 00007fa55fcf5b82
0x00007fa56a99b680:   00007fa56a99b960 00007fa55fd58251
0x00007fa56a99b690:   00007fa56a99b960 00007fa571b94105
0x00007fa56a99b6a0:   00007fa571da72c8 00007fa571da7858
0x00007fa56a99b6b0:   00007fa571d80000 0000000001ea1b50
0x00007fa56a99b6c0:   0000000001ea2610 0000000001ea2b10
0x00007fa56a99b6d0:   0000000001ea77b0 00007fa5641bcd80
0x00007fa56a99b6e0:   00007fa5641bd250 00007fa571d7f000
0x00007fa56a99b6f0:   0000000002298430 00000000022988e0
0x00007fa56a99b700:   00007fa564297a60 00007fa564298c70
0x00007fa56a99b710:   00007fa5642f28f0 00000000022977c0
0x00007fa56a99b720:   00007fa5644979d0 00007fa564498360
0x00007fa56a99b730:   00007fa564490080 00007fa564498820
0x00007fa56a99b740:   00007fa5644a7e80 00007fa5644a79e0
0x00007fa56a99b750:   00007fa5644a8320 00007fa564490540 

Instructions: (pc=0x00007fa569450c08)
0x00007fa569450be8:   24 d8 48 89 fb 4c 89 64 24 e0 4c 89 6c 24 e8 49
0x00007fa569450bf8:   89 d4 4c 89 74 24 f0 4c 89 7c 24 f8 48 83 ec 58
0x00007fa569450c08:   48 8b 87 68 09 00 00 49 89 f5 48 89 cd 4d 89 c6
0x00007fa569450c18:   48 85 c0 74 02 ff 10 4c 8b bb b0 00 00 00 49 8d 

Register to memory mapping:

RAX=0x0000000002630420 is an unknown value
RBX=0x0000000064350030 is an unknown value
RCX=0x00007fa56a99b5c8 is an unknown value
RDX=0x00007fa56a99b5c4 is an unknown value
RSP=0x00007fa56a99b560 is an unknown value
RBP=0x00007fa55fd582d2: <offset 0x952d2> in /usr/lib/fglrx/libGL.so.1 at 0x00007fa55fcc3000
RSI=0x00007fa55fd582d2: <offset 0x952d2> in /usr/lib/fglrx/libGL.so.1 at 0x00007fa55fcc3000
RDI=0x0000000064350030 is an unknown value
R8 =0x00007fa56a99b5cc is an unknown value
R9 =0x0000000000000000 is an unknown value
R10=0x00007fa57155bea8: <offset 0x39bea8> in /lib/x86_64-linux-gnu/libc.so.6 at 0x00007fa5711c0000
R11=0x00007fa5711fbba0: __cxa_finalize+0 in /lib/x86_64-linux-gnu/libc.so.6 at 0x00007fa5711c0000
R12=0x00007fa56a99b5c4 is an unknown value
R13=0x00007fa55fd582d2: <offset 0x952d2> in /usr/lib/fglrx/libGL.so.1 at 0x00007fa55fcc3000
R14=0x0000000002630420 is an unknown value
R15=0x0000000000000000 is an unknown value


Stack: [0x00007fa56a89c000,0x00007fa56a99d000],  sp=0x00007fa56a99b560,  free space=1021k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libX11.so.6+0x35c08]  XQueryExtension+0x28

VM_Operation (0x00007fa55a5ec5c0): Exit, mode: safepoint, requested by thread 0x0000000002637800


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0000000002637800 JavaThread "SIGHUP handler" daemon [_thread_blocked, id=3157, stack(0x00007fa55a4ed000,0x00007fa55a5ee000)]
  0x00000000029b8000 JavaThread "TimerQueue" daemon [_thread_blocked, id=3120, stack(0x00007fa5628b1000,0x00007fa5629b2000)]
  0x0000000001fd6800 JavaThread "Thread-8" daemon [_thread_blocked, id=3076, stack(0x00007fa5611b7000,0x00007fa5612b8000)]
  0x0000000001ec9000 JavaThread "Timer hack thread" daemon [_thread_blocked, id=3070, stack(0x00007fa5610b6000,0x00007fa5611b7000)]
  0x00007fa5643d6000 JavaThread "DestroyJavaVM" [_thread_blocked, id=2987, stack(0x00007fa571c7b000,0x00007fa571d7c000)]
  0x00007fa5642b8000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=3009, stack(0x00007fa5638eb000,0x00007fa5639ec000)]
  0x00007fa564272800 JavaThread "AWT-Shutdown" [_thread_blocked, id=3008, stack(0x00007fa5639ec000,0x00007fa563aed000)]
  0x00007fa56423b000 JavaThread "AWT-XAWT" daemon [_thread_blocked, id=3001, stack(0x00007fa56802a000,0x00007fa56812b000)]
  0x00007fa564185000 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=3000, stack(0x00007fa568200000,0x00007fa568301000)]
  0x00007fa564085000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=2998, stack(0x00007fa569fcd000,0x00007fa56a0ce000)]
  0x00007fa564082800 JavaThread "C2 CompilerThread1" daemon [_thread_blocked, id=2997, stack(0x00007fa56a0ce000,0x00007fa56a1cf000)]
  0x00007fa56407f800 JavaThread "C2 CompilerThread0" daemon [_thread_blocked, id=2996, stack(0x00007fa56a1cf000,0x00007fa56a2d0000)]
  0x00007fa564071000 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=2995, stack(0x00007fa56a2d0000,0x00007fa56a3d1000)]
  0x00007fa56405f000 JavaThread "Finalizer" daemon [_thread_blocked, id=2994, stack(0x00007fa56a69a000,0x00007fa56a79b000)]
  0x00007fa56405d000 JavaThread "Reference Handler" daemon [_thread_blocked, id=2993, stack(0x00007fa56a79b000,0x00007fa56a89c000)]

Other Threads:
=>0x00007fa564056000 VMThread [stack: 0x00007fa56a89c000,0x00007fa56a99d000] [id=2992]

VM state:at safepoint (shutting down)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0x0000000001e9ff20] Threads_lock - owner thread: 0x00007fa564056000

Heap
 PSYoungGen      total 69056K, used 10887K [0x00000007d6800000, 0x00000007db0a0000, 0x0000000800000000)
  eden space 63744K, 17% used [0x00000007d6800000,0x00000007d72a1d90,0x00000007da640000)
  from space 5312K, 0% used [0x00000007dab70000,0x00000007dab70000,0x00000007db0a0000)
  to   space 5312K, 0% used [0x00000007da640000,0x00000007da640000,0x00000007dab70000)
 PSOldGen        total 84992K, used 17180K [0x0000000783800000, 0x0000000788b00000, 0x00000007d6800000)
  object space 84992K, 20% used [0x0000000783800000,0x00000007848c73c0,0x0000000788b00000)
 PSPermGen       total 58368K, used 29733K [0x0000000779200000, 0x000000077cb00000, 0x0000000783800000)
  object space 58368K, 50% used [0x0000000779200000,0x000000077af09760,0x000000077cb00000)

Code Cache  [0x00007fa56bbb5000, 0x00007fa56be25000, 0x00007fa56ebb5000)
 total_blobs=1128 nmethods=420 adapters=662 free_code_cache=48559168 largest_free_block=16384

Dynamic libraries:
00400000-00409000 r-xp 00000000 08:01 16122111                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
00608000-00609000 r--p 00008000 08:01 16122111                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
00609000-0060a000 rw-p 00009000 08:01 16122111                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
01e99000-02b82000 rw-p 00000000 00:00 0                                  [heap]
779200000-77cb00000 rw-p 00000000 00:00 0 
77cb00000-77cfa0000 ---p 00000000 00:00 0 
77cfa0000-783800000 rw-p 00000000 00:00 0 
783800000-788b00000 rw-p 00000000 00:00 0 
788b00000-7d6800000 rw-p 00000000 00:00 0 
7d6800000-7db0a0000 rw-p 00000000 00:00 0 
7db0a0000-800000000 rw-p 00000000 00:00 0 
7fa544000000-7fa544911000 rw-p 00000000 00:00 0 
7fa544911000-7fa548000000 ---p 00000000 00:00 0 
7fa548feb000-7fa548fee000 ---p 00000000 00:00 0 
7fa548fee000-7fa55312c000 rw-p 00000000 00:00 0 
7fa55312c000-7fa55312d000 ---p 00000000 00:00 0 
7fa55312d000-7fa55392d000 rw-p 00000000 00:00 0 
7fa55392d000-7fa55392e000 ---p 00000000 00:00 0 
7fa55392e000-7fa55412e000 rw-p 00000000 00:00 0 
7fa55812f000-7fa558134000 r-xp 00000000 08:01 13245707                   /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
7fa558134000-7fa558334000 ---p 00005000 08:01 13245707                   /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
7fa558334000-7fa558335000 r--p 00005000 08:01 13245707                   /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
7fa558335000-7fa558336000 rw-p 00006000 08:01 13245707                   /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
7fa558336000-7fa55833c000 r-xp 00000000 08:01 13115343                   /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7fa55833c000-7fa55853b000 ---p 00006000 08:01 13115343                   /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7fa55853b000-7fa55853c000 r--p 00005000 08:01 13115343                   /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7fa55853c000-7fa55853d000 rw-p 00006000 08:01 13115343                   /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7fa55853d000-7fa558568000 r-xp 00000000 08:01 13115414                   /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7fa558568000-7fa558767000 ---p 0002b000 08:01 13115414                   /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7fa558767000-7fa558768000 r--p 0002a000 08:01 13115414                   /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7fa558768000-7fa558769000 rw-p 0002b000 08:01 13115414                   /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7fa558769000-7fa558a1c000 r-xp 00000000 08:01 13115416                   /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7fa558a1c000-7fa558c1b000 ---p 002b3000 08:01 13115416                   /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7fa558c1b000-7fa558c37000 r--p 002b2000 08:01 13115416                   /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7fa558c37000-7fa558c38000 rw-p 002ce000 08:01 13115416                   /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7fa558c38000-7fa558c80000 r-xp 00000000 08:01 13115110                   /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7fa558c80000-7fa558e80000 ---p 00048000 08:01 13115110                   /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7fa558e80000-7fa558e81000 r--p 00048000 08:01 13115110                   /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7fa558e81000-7fa558e82000 rw-p 00049000 08:01 13115110                   /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7fa558e82000-7fa558e87000 r-xp 00000000 08:01 13115219                   /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7fa558e87000-7fa559086000 ---p 00005000 08:01 13115219                   /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7fa559086000-7fa559087000 r--p 00004000 08:01 13115219                   /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7fa559087000-7fa559088000 rw-p 00005000 08:01 13115219                   /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7fa559088000-7fa5590e8000 r-xp 00000000 08:01 13115383                   /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.24
7fa5590e8000-7fa5592e8000 ---p 00060000 08:01 13115383                   /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.24
7fa5592e8000-7fa5592ea000 r--p 00060000 08:01 13115383                   /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.24
7fa5592ea000-7fa5592eb000 rw-p 00062000 08:01 13115383                   /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.24
7fa5592eb000-7fa5592ef000 rw-p 00000000 00:00 0 
7fa5592ef000-7fa5592f7000 r-xp 00000000 08:01 1183451                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fa5592f7000-7fa5594f6000 ---p 00008000 08:01 1183451                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fa5594f6000-7fa5594f7000 r--p 00007000 08:01 1183451                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fa5594f7000-7fa5594f8000 rw-p 00008000 08:01 1183451                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fa5594f8000-7fa55953a000 r-xp 00000000 08:01 1183380                    /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7fa55953a000-7fa559739000 ---p 00042000 08:01 1183380                    /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7fa559739000-7fa55973a000 r--p 00041000 08:01 1183380                    /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7fa55973a000-7fa55973b000 rw-p 00042000 08:01 1183380                    /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7fa55973b000-7fa559797000 r-xp 00000000 08:01 13112095                   /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so
7fa559797000-7fa559997000 ---p 0005c000 08:01 13112095                   /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so
7fa559997000-7fa559998000 r--p 0005c000 08:01 13112095                   /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so
7fa559998000-7fa559999000 rw-p 0005d000 08:01 13112095                   /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so
7fa559999000-7fa5599a0000 r-xp 00000000 08:01 13115317                   /usr/lib/x86_64-linux-gnu/libjson.so.0.0.1
7fa5599a0000-7fa559b9f000 ---p 00007000 08:01 13115317                   /usr/lib/x86_64-linux-gnu/libjson.so.0.0.1
7fa559b9f000-7fa559ba0000 r--p 00006000 08:01 13115317                   /usr/lib/x86_64-linux-gnu/libjson.so.0.0.1
7fa559ba0000-7fa559ba1000 rw-p 00007000 08:01 13115317                   /usr/lib/x86_64-linux-gnu/libjson.so.0.0.1
7fa559ba1000-7fa559be7000 r-xp 00000000 08:01 13112093                   /usr/lib/x86_64-linux-gnu/libpulse.so.0.13.4
7fa559be7000-7fa559de6000 ---p 00046000 08:01 13112093                   /usr/lib/x86_64-linux-gnu/libpulse.so.0.13.4
7fa559de6000-7fa559de7000 r--p 00045000 08:01 13112093                   /usr/lib/x86_64-linux-gnu/libpulse.so.0.13.4
7fa559de7000-7fa559de8000 rw-p 00046000 08:01 13112093                   /usr/lib/x86_64-linux-gnu/libpulse.so.0.13.4
7fa559ee9000-7fa559eec000 ---p 00000000 00:00 0 
7fa559eec000-7fa559fea000 rw-p 00000000 00:00 0 
7fa559fea000-7fa55a0cf000 r-xp 00000000 08:01 13115215                   /usr/lib/x86_64-linux-gnu/libasound.so.2.0.0
7fa55a0cf000-7fa55a2ce000 ---p 000e5000 08:01 13115215                   /usr/lib/x86_64-linux-gnu/libasound.so.2.0.0
7fa55a2ce000-7fa55a2d4000 r--p 000e4000 08:01 13115215                   /usr/lib/x86_64-linux-gnu/libasound.so.2.0.0
7fa55a2d4000-7fa55a2d5000 rw-p 000ea000 08:01 13115215                   /usr/lib/x86_64-linux-gnu/libasound.so.2.0.0
7fa55a4ed000-7fa55a4f0000 ---p 00000000 00:00 0 
7fa55a4f0000-7fa55a5ee000 rw-p 00000000 00:00 0 
7fa55a5ee000-7fa55a5f1000 ---p 00000000 00:00 0 
7fa55a5f1000-7fa55a6ef000 rw-p 00000000 00:00 0 
7fa55a6ef000-7fa55a6f2000 r-xp 00000000 08:01 6425965                    /home/ronnoc/.minecraft/bin/natives/libjinput-linux64.so
7fa55a6f2000-7fa55a8f1000 ---p 00003000 08:01 6425965                    /home/ronnoc/.minecraft/bin/natives/libjinput-linux64.so
7fa55a8f1000-7fa55a8f2000 r--p 00002000 08:01 6425965                    /home/ronnoc/.minecraft/bin/natives/libjinput-linux64.so
7fa55a8f2000-7fa55a8f3000 rw-p 00003000 08:01 6425965                    /home/ronnoc/.minecraft/bin/natives/libjinput-linux64.so
7fa55b8f3000-7fa55d0f7000 rw-p 00000000 00:00 0 
7fa55d137000-7fa55d837000 rw-s 00006000 00:05 9289                       /dev/ati/card0
7fa55d837000-7fa55d839000 r-xp 00000000 08:01 13115201                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7fa55d839000-7fa55da38000 ---p 00002000 08:01 13115201                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7fa55da38000-7fa55da39000 r--p 00001000 08:01 13115201                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7fa55da39000-7fa55da3a000 rw-p 00002000 08:01 13115201                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7fa55da3a000-7fa55da73000 r-xp 00000000 08:01 16123623                   /usr/lib/fglrx/libatiadlxx.so
7fa55da73000-7fa55db72000 ---p 00039000 08:01 16123623                   /usr/lib/fglrx/libatiadlxx.so
7fa55db72000-7fa55db7b000 rw-p 00038000 08:01 16123623                   /usr/lib/fglrx/libatiadlxx.so
7fa55db9d000-7fa55dba4000 r-xp 00000000 08:01 16123628                   /usr/lib/fglrx/libatiuki.so.1.0
7fa55dba4000-7fa55dca4000 ---p 00007000 08:01 16123628                   /usr/lib/fglrx/libatiuki.so.1.0
7fa55dca4000-7fa55dca5000 rw-p 00007000 08:01 16123628                   /usr/lib/fglrx/libatiuki.so.1.0
7fa55dca5000-7fa55dca6000 rw-p 00000000 00:00 0 
7fa55dca6000-7fa55f987000 r-xp 00000000 08:01 16123630                   /usr/lib/fglrx/dri/fglrx_dri.so
7fa55f987000-7fa55fa87000 ---p 01ce1000 08:01 16123630                   /usr/lib/fglrx/dri/fglrx_dri.so
7fa55fa87000-7fa55fba9000 rwxp 01ce1000 08:01 16123630                   /usr/lib/fglrx/dri/fglrx_dri.so
7fa55fba9000-7fa55fcc3000 rwxp 00000000 00:00 0 
7fa55fcc3000-7fa55fd84000 r-xp 00000000 08:01 16123622                   /usr/lib/fglrx/libGL.so.1.2
7fa55fd84000-7fa55fe83000 ---p 000c1000 08:01 16123622                   /usr/lib/fglrx/libGL.so.1.2
7fa55fe83000-7fa55fea9000 rwxp 000c0000 08:01 16123622                   /usr/lib/fglrx/libGL.so.1.2
7fa55fea9000-7fa55fec9000 rwxp 00000000 00:00 0 
7fa55fec9000-7fa55feca000 r-xp 00000000 08:01 16122151                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjawt.so
7fa55feca000-7fa5600c9000 ---p 00001000 08:01 16122151                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjawt.so
7fa5600c9000-7fa5600ca000 r--p 00000000 08:01 16122151                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjawt.so
7fa5600ca000-7fa5600cb000 rw-p 00001000 08:01 16122151                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjawt.so
7fa5600cb000-7fa5600d0000 r-xp 00000000 08:01 13115213                   /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7fa5600d0000-7fa5602cf000 ---p 00005000 08:01 13115213                   /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7fa5602cf000-7fa5602d0000 r--p 00004000 08:01 13115213                   /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7fa5602d0000-7fa5602d1000 rw-p 00005000 08:01 13115213                   /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7fa5602d1000-7fa5602d9000 r-xp 00000000 08:01 13115203                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7fa5602d9000-7fa5604d8000 ---p 00008000 08:01 13115203                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7fa5604d8000-7fa5604d9000 r--p 00007000 08:01 13115203                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7fa5604d9000-7fa5604da000 rw-p 00008000 08:01 13115203                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7fa5604da000-7fa5604fa000 rw-s fea20000 00:05 9289                       /dev/ati/card0
7fa5604fa000-7fa5604fc000 rw-s 00002000 00:05 9289                       /dev/ati/card0
7fa5604fc000-7fa56056a000 r-xp 00000000 08:01 6425967                    /home/ronnoc/.minecraft/bin/natives/liblwjgl64.so
7fa56056a000-7fa560769000 ---p 0006e000 08:01 6425967                    /home/ronnoc/.minecraft/bin/natives/liblwjgl64.so
7fa560769000-7fa56076b000 r--p 0006d000 08:01 6425967                    /home/ronnoc/.minecraft/bin/natives/liblwjgl64.so
7fa56076b000-7fa56076c000 rw-p 0006f000 08:01 6425967                    /home/ronnoc/.minecraft/bin/natives/liblwjgl64.so
7fa560eda000-7fa5610b6000 rw-s 00000000 00:04 6553676                    /SYSV00000000 (deleted)
7fa5610b6000-7fa5610b9000 ---p 00000000 00:00 0 
7fa5610b9000-7fa5611b7000 rw-p 00000000 00:00 0 
7fa5611b7000-7fa5611ba000 ---p 00000000 00:00 0 
7fa5611ba000-7fa5612b8000 rw-p 00000000 00:00 0 
7fa5612b8000-7fa5612bb000 ---p 00000000 00:00 0 
7fa5612bb000-7fa5613b9000 rw-p 00000000 00:00 0 
7fa5613b9000-7fa56141f000 r-xp 00000000 08:01 13242005                   /usr/lib/x86_64-linux-gnu/nss/libfreebl3.so
7fa56141f000-7fa56161f000 ---p 00066000 08:01 13242005                   /usr/lib/x86_64-linux-gnu/nss/libfreebl3.so
7fa56161f000-7fa561620000 r--p 00066000 08:01 13242005                   /usr/lib/x86_64-linux-gnu/nss/libfreebl3.so
7fa561620000-7fa561621000 rw-p 00067000 08:01 13242005                   /usr/lib/x86_64-linux-gnu/nss/libfreebl3.so
7fa561621000-7fa561625000 rw-p 00000000 00:00 0 
7fa561625000-7fa5616c0000 r-xp 00000000 08:01 13115389                   /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7fa5616c0000-7fa5618bf000 ---p 0009b000 08:01 13115389                   /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7fa5618bf000-7fa5618c1000 r--p 0009a000 08:01 13115389                   /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7fa5618c1000-7fa5618c3000 rw-p 0009c000 08:01 13115389                   /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
7fa5618c3000-7fa5618c4000 rw-p 00000000 00:00 0 
7fa5618c4000-7fa561904000 r-xp 00000000 08:01 13242010                   /usr/lib/x86_64-linux-gnu/nss/libsoftokn3.so
7fa561904000-7fa561b03000 ---p 00040000 08:01 13242010                   /usr/lib/x86_64-linux-gnu/nss/libsoftokn3.so
7fa561b03000-7fa561b05000 r--p 0003f000 08:01 13242010                   /usr/lib/x86_64-linux-gnu/nss/libsoftokn3.so
7fa561b05000-7fa561b06000 rw-p 00041000 08:01 13242010                   /usr/lib/x86_64-linux-gnu/nss/libsoftokn3.so
7fa561b06000-7fa561b3d000 r-xp 00000000 08:01 13115337                   /usr/lib/x86_64-linux-gnu/libnspr4.so
7fa561b3d000-7fa561d3c000 ---p 00037000 08:01 13115337                   /usr/lib/x86_64-linux-gnu/libnspr4.so
7fa561d3c000-7fa561d3d000 r--p 00036000 08:01 13115337                   /usr/lib/x86_64-linux-gnu/libnspr4.so
7fa561d3d000-7fa561d3e000 rw-p 00037000 08:01 13115337                   /usr/lib/x86_64-linux-gnu/libnspr4.so
7fa561d3e000-7fa561d41000 rw-p 00000000 00:00 0 
7fa561d41000-7fa561d44000 r-xp 00000000 08:01 13115365                   /usr/lib/x86_64-linux-gnu/libplds4.so
7fa561d44000-7fa561f43000 ---p 00003000 08:01 13115365                   /usr/lib/x86_64-linux-gnu/libplds4.so
7fa561f43000-7fa561f44000 r--p 00002000 08:01 13115365                   /usr/lib/x86_64-linux-gnu/libplds4.so
7fa561f44000-7fa561f45000 rw-p 00003000 08:01 13115365                   /usr/lib/x86_64-linux-gnu/libplds4.so
7fa561f45000-7fa561f49000 r-xp 00000000 08:01 13115364                   /usr/lib/x86_64-linux-gnu/libplc4.so
7fa561f49000-7fa562148000 ---p 00004000 08:01 13115364                   /usr/lib/x86_64-linux-gnu/libplc4.so
7fa562148000-7fa562149000 r--p 00003000 08:01 13115364                   /usr/lib/x86_64-linux-gnu/libplc4.so
7fa562149000-7fa56214a000 rw-p 00004000 08:01 13115364                   /usr/lib/x86_64-linux-gnu/libplc4.so
7fa56214a000-7fa562164000 r-xp 00000000 08:01 13115340                   /usr/lib/x86_64-linux-gnu/libnssutil3.so
7fa562164000-7fa562363000 ---p 0001a000 08:01 13115340                   /usr/lib/x86_64-linux-gnu/libnssutil3.so
7fa562363000-7fa562368000 r--p 00019000 08:01 13115340                   /usr/lib/x86_64-linux-gnu/libnssutil3.so
7fa562368000-7fa562369000 rw-p 0001e000 08:01 13115340                   /usr/lib/x86_64-linux-gnu/libnssutil3.so
7fa562369000-7fa562499000 r-xp 00000000 08:01 13115338                   /usr/lib/x86_64-linux-gnu/libnss3.so
7fa562499000-7fa562698000 ---p 00130000 08:01 13115338                   /usr/lib/x86_64-linux-gnu/libnss3.so
7fa562698000-7fa56269d000 r--p 0012f000 08:01 13115338                   /usr/lib/x86_64-linux-gnu/libnss3.so
7fa56269d000-7fa56269f000 rw-p 00134000 08:01 13115338                   /usr/lib/x86_64-linux-gnu/libnss3.so
7fa56269f000-7fa5626a1000 rw-p 00000000 00:00 0 
7fa5626a1000-7fa5626af000 r-xp 00000000 08:01 16122132                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libj2pkcs11.so
7fa5626af000-7fa5628af000 ---p 0000e000 08:01 16122132                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libj2pkcs11.so
7fa5628af000-7fa5628b0000 r--p 0000e000 08:01 16122132                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libj2pkcs11.so
7fa5628b0000-7fa5628b1000 rw-p 0000f000 08:01 16122132                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libj2pkcs11.so
7fa5628b1000-7fa5628b4000 ---p 00000000 00:00 0 
7fa5628b4000-7fa5629b2000 rw-p 00000000 00:00 0 
7fa5629b2000-7fa5629ba000 r-xp 00000000 08:01 16122120                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
7fa5629ba000-7fa562bb9000 ---p 00008000 08:01 16122120                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
7fa562bb9000-7fa562bba000 r--p 00007000 08:01 16122120                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
7fa562bba000-7fa562bbb000 rw-p 00008000 08:01 16122120                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
7fa562bbb000-7fa562bc5000 r-xp 00000000 08:01 16122149                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
7fa562bc5000-7fa562dc4000 ---p 0000a000 08:01 16122149                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
7fa562dc4000-7fa562dc5000 r--p 00009000 08:01 16122149                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
7fa562dc5000-7fa562dc6000 rw-p 0000a000 08:01 16122149                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
7fa562dc6000-7fa562df8000 r-xp 00000000 08:01 16122133                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
7fa562df8000-7fa562ff7000 ---p 00032000 08:01 16122133                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
7fa562ff7000-7fa562ff8000 r--p 00031000 08:01 16122133                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
7fa562ff8000-7fa562ff9000 rw-p 00032000 08:01 16122133                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
7fa562ff9000-7fa562ffb000 rw-p 00000000 00:00 0 
7fa562ffb000-7fa563012000 r-xp 00000000 08:01 1183432                    /lib/x86_64-linux-gnu/libresolv-2.13.so
7fa563012000-7fa563212000 ---p 00017000 08:01 1183432                    /lib/x86_64-linux-gnu/libresolv-2.13.so
7fa563212000-7fa563213000 r--p 00017000 08:01 1183432                    /lib/x86_64-linux-gnu/libresolv-2.13.so
7fa563213000-7fa563214000 rw-p 00018000 08:01 1183432                    /lib/x86_64-linux-gnu/libresolv-2.13.so
7fa563214000-7fa563216000 rw-p 00000000 00:00 0 
7fa563216000-7fa56321c000 r-xp 00000000 08:01 1183409                    /lib/x86_64-linux-gnu/libnss_dns-2.13.so
7fa56321c000-7fa56341b000 ---p 00006000 08:01 1183409                    /lib/x86_64-linux-gnu/libnss_dns-2.13.so
7fa56341b000-7fa56341c000 r--p 00005000 08:01 1183409                    /lib/x86_64-linux-gnu/libnss_dns-2.13.so
7fa56341c000-7fa56341d000 rw-p 00006000 08:01 1183409                    /lib/x86_64-linux-gnu/libnss_dns-2.13.so
7fa56341d000-7fa56341f000 r-xp 00000000 08:01 1179713                    /lib/libnss_mdns4_minimal.so.2
7fa56341f000-7fa56361e000 ---p 00002000 08:01 1179713                    /lib/libnss_mdns4_minimal.so.2
7fa56361e000-7fa56361f000 r--p 00001000 08:01 1179713                    /lib/libnss_mdns4_minimal.so.2
7fa56361f000-7fa563620000 rw-p 00002000 08:01 1179713                    /lib/libnss_mdns4_minimal.so.2
7fa563620000-7fa563621000 r--s 00000000 08:01 3145805                    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3
7fa563621000-7fa56362a000 r--s 00000000 08:01 3145802                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7fa56362a000-7fa56362c000 r--s 00000000 08:01 3145803                    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3
7fa56362c000-7fa56362f000 r--s 00000000 08:01 3145813                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le64.cache-3
7fa56362f000-7fa563633000 r--s 00000000 08:01 3145790                    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le64.cache-3
7fa563633000-7fa563634000 r--s 00000000 08:01 3145814                    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le64.cache-3
7fa563634000-7fa563639000 r--s 00000000 08:01 3145799                    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le64.cache-3
7fa563639000-7fa56363a000 r--s 00000000 08:01 3145794                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le64.cache-3
7fa56363a000-7fa56363b000 r--s 00000000 08:01 3145787                    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le64.cache-3
7fa56363b000-7fa56363c000 r--s 00000000 08:01 3145797                    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le64.cache-3
7fa56363c000-7fa563642000 r--s 00000000 08:01 3145804                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3
7fa563642000-7fa563648000 r--s 00000000 08:01 3157569                    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le64.cache-3
7fa563648000-7fa563651000 r--s 00000000 08:01 3147089                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
7fa563651000-7fa563661000 r--s 00000000 08:01 3145788                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le64.cache-3
7fa563661000-7fa56368f000 r--s 00000000 08:01 3155855                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le64.cache-3
7fa563691000-7fa563694000 rw-s 00000000 00:04 7012423                    /SYSV00000000 (deleted)
7fa56369a000-7fa5636ac000 r--s 00240000 08:01 6423065                    /home/ronnoc/.minecraft/bin/minecraft.jar
7fa5636ac000-7fa5636af000 r--s 0001f000 08:01 6425733                    /home/ronnoc/.minecraft/bin/lwjgl_util.jar
7fa5636af000-7fa5636b4000 r--s 00033000 08:01 6425299                    /home/ronnoc/.minecraft/bin/jinput.jar
7fa5636b8000-7fa5636bf000 r--s 00000000 08:01 13241915                   /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
7fa5636bf000-7fa5636c4000 r--s 0049e000 08:01 6422614                    /home/ronnoc/.minecraft/mods/DrZhark's Mo'Creatures Mod v3.1.0.zip
7fa5636c4000-7fa5636cd000 r--s 000ac000 08:01 6425298                    /home/ronnoc/.minecraft/bin/lwjgl.jar
7fa5636cd000-7fa5636d1000 r--s 00038000 08:01 14423648                   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
7fa5636d5000-7fa5636ea000 r-xp 00000000 08:01 16122130                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
7fa5636ea000-7fa5638e9000 ---p 00015000 08:01 16122130                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
7fa5638e9000-7fa5638ea000 r--p 00014000 08:01 16122130                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
7fa5638ea000-7fa5638eb000 rw-p 00015000 08:01 16122130                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
7fa5638eb000-7fa5638ee000 ---p 00000000 00:00 0 
7fa5638ee000-7fa5639ec000 rw-p 00000000 00:00 0 
7fa5639ec000-7fa5639ef000 ---p 00000000 00:00 0 
7fa5639ef000-7fa563aed000 rw-p 00000000 00:00 0 
7fa563aed000-7fa563aef000 r--s 00013000 08:01 14157400                   /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
7fa563aef000-7fa563af2000 ---p 00000000 00:00 0 
7fa563af2000-7fa563bf0000 rw-p 00000000 00:00 0 
7fa563bf0000-7fa563bf5000 r-xp 00000000 08:01 13115195                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fa563bf5000-7fa563df4000 ---p 00005000 08:01 13115195                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fa563df4000-7fa563df5000 r--p 00004000 08:01 13115195                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fa563df5000-7fa563df6000 rw-p 00005000 08:01 13115195                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fa563df6000-7fa563dff000 r-xp 00000000 08:01 13115187                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7fa563dff000-7fa563ffe000 ---p 00009000 08:01 13115187                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7fa563ffe000-7fa563fff000 r--p 00008000 08:01 13115187                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7fa563fff000-7fa564000000 rw-p 00009000 08:01 13115187                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7fa564000000-7fa564d99000 rw-p 00000000 00:00 0 
7fa564d99000-7fa568000000 ---p 00000000 00:00 0 
7fa568000000-7fa568003000 r--s 00077000 08:01 14423649                   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar
7fa568003000-7fa568006000 r--s 00031000 08:01 14423650                   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
7fa568006000-7fa568009000 r--s 00000000 08:01 3145810                    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le64.cache-3
7fa568009000-7fa56800a000 r--s 00000000 08:01 3148414                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le64.cache-3
7fa56800a000-7fa56801a000 r--s 00000000 08:01 3145809                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
7fa56801a000-7fa568022000 r--s 00000000 08:01 3157568                    /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le64.cache-3
7fa568022000-7fa568025000 r--s 00000000 08:01 3148439                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le64.cache-3
7fa568025000-7fa568029000 r--s 00000000 08:01 3157567                    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3
7fa568029000-7fa56802a000 r--p 00000000 00:00 0 
7fa56802a000-7fa56802d000 ---p 00000000 00:00 0 
7fa56802d000-7fa56812b000 rw-p 00000000 00:00 0 
7fa56812b000-7fa56812c000 r--s 00000000 08:01 3145805                    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3
7fa56812c000-7fa568135000 r--s 00000000 08:01 3145802                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7fa568135000-7fa568137000 r--s 00000000 08:01 3145803                    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3
7fa568137000-7fa56813a000 r--s 00000000 08:01 3145813                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le64.cache-3
7fa56813a000-7fa56813e000 r--s 00000000 08:01 3145790                    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le64.cache-3
7fa56813e000-7fa56813f000 r--s 00000000 08:01 3145814                    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le64.cache-3
7fa56813f000-7fa568144000 r--s 00000000 08:01 3145799                    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le64.cache-3
7fa568144000-7fa568145000 r--s 00000000 08:01 3145794                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le64.cache-3
7fa568145000-7fa568146000 r--s 00000000 08:01 3145787                    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le64.cache-3
7fa568146000-7fa568147000 r--s 00000000 08:01 3145797                    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le64.cache-3
7fa568147000-7fa56814d000 r--s 00000000 08:01 3145804                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3
7fa56814d000-7fa568153000 r--s 00000000 08:01 3157569                    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le64.cache-3
7fa568153000-7fa56815c000 r--s 00000000 08:01 3147089                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
7fa56815c000-7fa56816c000 r--s 00000000 08:01 3145788                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le64.cache-3
7fa56816c000-7fa56816f000 r--s 00000000 08:01 3145810                    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le64.cache-3
7fa56816f000-7fa56819d000 r--s 00000000 08:01 3155855                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le64.cache-3
7fa56819d000-7fa5681ad000 r--s 00000000 08:01 3145809                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
7fa5681ad000-7fa5681b5000 r--s 00000000 08:01 3157568                    /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le64.cache-3
7fa5681b5000-7fa5681b9000 r--s 00000000 08:01 3157567                    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3
7fa5681b9000-7fa5681ba000 r--s 00000000 08:01 3145805                    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3
7fa5681ba000-7fa5681c3000 r--s 00000000 08:01 3145802                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7fa5681c3000-7fa5681c5000 r--s 00000000 08:01 3145803                    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3
7fa5681c5000-7fa5681c8000 r--s 00000000 08:01 3145813                    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le64.cache-3
7fa5681c8000-7fa5681cc000 r--s 00000000 08:01 3145790                    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le64.cache-3
7fa5681cc000-7fa5681d2000 r--s 00000000 08:01 3145804                    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3
7fa5681d2000-7fa568200000 r--s 00000000 08:01 3155855                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le64.cache-3
7fa568200000-7fa568203000 ---p 00000000 00:00 0 
7fa568203000-7fa568301000 rw-p 00000000 00:00 0 
7fa568301000-7fa568393000 r-xp 00000000 08:01 13107906                   /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
7fa568393000-7fa568592000 ---p 00092000 08:01 13107906                   /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
7fa568592000-7fa568598000 r--p 00091000 08:01 13107906                   /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
7fa568598000-7fa568599000 rw-p 00097000 08:01 13107906                   /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
7fa568599000-7fa5685d2000 r-xp 00000000 08:01 16122140                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
7fa5685d2000-7fa5687d2000 ---p 00039000 08:01 16122140                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
7fa5687d2000-7fa5687d4000 r--p 00039000 08:01 16122140                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
7fa5687d4000-7fa5687d5000 rw-p 0003b000 08:01 16122140                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
7fa5687d5000-7fa5687da000 r-xp 00000000 08:01 13115191                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7fa5687da000-7fa5689d9000 ---p 00005000 08:01 13115191                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7fa5689d9000-7fa5689da000 r--p 00004000 08:01 13115191                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7fa5689da000-7fa5689db000 rw-p 00005000 08:01 13115191                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7fa5689db000-7fa5689dd000 r-xp 00000000 08:01 13115183                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7fa5689dd000-7fa568bdc000 ---p 00002000 08:01 13115183                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7fa568bdc000-7fa568bdd000 r--p 00001000 08:01 13115183                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7fa568bdd000-7fa568bde000 rw-p 00002000 08:01 13115183                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7fa568bde000-7fa568bf9000 r-xp 00000000 08:01 13115428                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7fa568bf9000-7fa568df8000 ---p 0001b000 08:01 13115428                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7fa568df8000-7fa568df9000 r--p 0001a000 08:01 13115428                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7fa568df9000-7fa568dfa000 rw-p 0001b000 08:01 13115428                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7fa568dfa000-7fa568e09000 r-xp 00000000 08:01 13115199                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7fa568e09000-7fa569008000 ---p 0000f000 08:01 13115199                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7fa569008000-7fa569009000 r--p 0000e000 08:01 13115199                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7fa569009000-7fa56900a000 rw-p 0000f000 08:01 13115199                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7fa56900a000-7fa56900f000 r-xp 00000000 08:01 13108776                   /usr/lib/libXtst.so.6.1.0
7fa56900f000-7fa56920e000 ---p 00005000 08:01 13108776                   /usr/lib/libXtst.so.6.1.0
7fa56920e000-7fa56920f000 r--p 00004000 08:01 13108776                   /usr/lib/libXtst.so.6.1.0
7fa56920f000-7fa569210000 rw-p 00005000 08:01 13108776                   /usr/lib/libXtst.so.6.1.0
7fa569210000-7fa569219000 r-xp 00000000 08:01 13115205                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7fa569219000-7fa569419000 ---p 00009000 08:01 13115205                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7fa569419000-7fa56941a000 r--p 00009000 08:01 13115205                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7fa56941a000-7fa56941b000 rw-p 0000a000 08:01 13115205                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7fa56941b000-7fa56954e000 r-xp 00000000 08:01 13115181                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7fa56954e000-7fa56974e000 ---p 00133000 08:01 13115181                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7fa56974e000-7fa56974f000 r--p 00133000 08:01 13115181                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7fa56974f000-7fa569753000 rw-p 00134000 08:01 13115181                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7fa569753000-7fa569765000 r-xp 00000000 08:01 13115193                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7fa569765000-7fa569964000 ---p 00012000 08:01 13115193                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7fa569964000-7fa569965000 r--p 00011000 08:01 13115193                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7fa569965000-7fa569966000 rw-p 00012000 08:01 13115193                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7fa569966000-7fa569969000 r--s 00000000 08:01 3148439                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le64.cache-3
7fa569969000-7fa56996f000 r--s 00000000 08:01 3157569                    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le64.cache-3
7fa56996f000-7fa569978000 r--s 00000000 08:01 3147089                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
7fa569978000-7fa569988000 r--s 00000000 08:01 3145788                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le64.cache-3
7fa569988000-7fa5699d3000 r-xp 00000000 08:01 16122230                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
7fa5699d3000-7fa569bd3000 ---p 0004b000 08:01 16122230                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
7fa569bd3000-7fa569bd4000 r--p 0004b000 08:01 16122230                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
7fa569bd4000-7fa569bd7000 rw-p 0004c000 08:01 16122230                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
7fa569bd7000-7fa569bd8000 rw-p 00000000 00:00 0 
7fa569bd8000-7fa569c84000 r-xp 00000000 08:01 16122150                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
7fa569c84000-7fa569e83000 ---p 000ac000 08:01 16122150                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
7fa569e83000-7fa569e84000 r--p 000ab000 08:01 16122150                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
7fa569e84000-7fa569e8f000 rw-p 000ac000 08:01 16122150                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
7fa569e8f000-7fa569eb4000 rw-p 00000000 00:00 0 
7fa569eb4000-7fa569ebb000 r--s 000fb000 08:01 14157410                   /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
7fa569ebb000-7fa569ebe000 r--s 0007d000 08:01 14157399                   /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
7fa569ebe000-7fa569ec0000 r--s 00014000 08:01 18350110                   /home/ronnoc/Downloads/minecraft.jar
7fa569ec0000-7fa569ec8000 r--s 00066000 08:01 13376589                   /usr/share/java/gnome-java-bridge.jar
7fa569ec8000-7fa569eca000 r--s 0000f000 08:01 14423653                   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
7fa569ecb000-7fa569ecc000 rw-s 00005000 00:05 9289                       /dev/ati/card0
7fa569ecc000-7fa569ecd000 ---p 00000000 00:00 0 
7fa569ecd000-7fa569fcd000 rw-p 00000000 00:00 0 
7fa569fcd000-7fa569fd0000 ---p 00000000 00:00 0 
7fa569fd0000-7fa56a0ce000 rw-p 00000000 00:00 0 
7fa56a0ce000-7fa56a0d1000 ---p 00000000 00:00 0 
7fa56a0d1000-7fa56a1cf000 rw-p 00000000 00:00 0 
7fa56a1cf000-7fa56a1d2000 ---p 00000000 00:00 0 
7fa56a1d2000-7fa56a2d0000 rw-p 00000000 00:00 0 
7fa56a2d0000-7fa56a2d3000 ---p 00000000 00:00 0 
7fa56a2d3000-7fa56a3d1000 rw-p 00000000 00:00 0 
7fa56a3d1000-7fa56a69a000 r--p 00000000 08:01 13113849                   /usr/lib/locale/locale-archive
7fa56a69a000-7fa56a69d000 ---p 00000000 00:00 0 
7fa56a69d000-7fa56a79b000 rw-p 00000000 00:00 0 
7fa56a79b000-7fa56a79e000 ---p 00000000 00:00 0 
7fa56a79e000-7fa56a89c000 rw-p 00000000 00:00 0 
7fa56a89c000-7fa56a89d000 ---p 00000000 00:00 0 
7fa56a89d000-7fa56aed5000 rw-p 00000000 00:00 0 
7fa56aed5000-7fa56b066000 r--s 037b8000 08:01 14157415                   /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
7fa56b066000-7fa56b08e000 rw-p 00000000 00:00 0 
7fa56b08e000-7fa56b08f000 ---p 00000000 00:00 0 
7fa56b08f000-7fa56b18f000 rw-p 00000000 00:00 0 
7fa56b18f000-7fa56b190000 ---p 00000000 00:00 0 
7fa56b190000-7fa56b290000 rw-p 00000000 00:00 0 
7fa56b290000-7fa56b291000 ---p 00000000 00:00 0 
7fa56b291000-7fa56b391000 rw-p 00000000 00:00 0 
7fa56b391000-7fa56b392000 ---p 00000000 00:00 0 
7fa56b392000-7fa56b4af000 rw-p 00000000 00:00 0 
7fa56b4af000-7fa56b4b1000 ---p 00000000 00:00 0 
7fa56b4b1000-7fa56b4e5000 rw-p 00000000 00:00 0 
7fa56b4e5000-7fa56b50f000 rw-p 00000000 00:00 0 
7fa56b50f000-7fa56b77d000 rw-p 00000000 00:00 0 
7fa56b77d000-7fa56b79a000 rw-p 00000000 00:00 0 
7fa56b79a000-7fa56b79c000 ---p 00000000 00:00 0 
7fa56b79c000-7fa56b7d0000 rw-p 00000000 00:00 0 
7fa56b7d0000-7fa56b7fa000 rw-p 00000000 00:00 0 
7fa56b7fa000-7fa56ba68000 rw-p 00000000 00:00 0 
7fa56ba68000-7fa56ba8d000 rw-p 00000000 00:00 0 
7fa56ba8d000-7fa56bbb4000 rw-p 00000000 00:00 0 
7fa56bbb4000-7fa56bbb5000 rw-p 00000000 00:00 0 
7fa56bbb5000-7fa56be25000 rwxp 00000000 00:00 0 
7fa56be25000-7fa56ebb5000 rw-p 00000000 00:00 0 
7fa56ebb5000-7fa56ebbc000 r-xp 00000000 08:01 16122144                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
7fa56ebbc000-7fa56edbb000 ---p 00007000 08:01 16122144                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
7fa56edbb000-7fa56edbc000 r--p 00006000 08:01 16122144                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
7fa56edbc000-7fa56edbd000 rw-p 00007000 08:01 16122144                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
7fa56edbd000-7fa56edc9000 r-xp 00000000 08:01 1183411                    /lib/x86_64-linux-gnu/libnss_files-2.13.so
7fa56edc9000-7fa56efc8000 ---p 0000c000 08:01 1183411                    /lib/x86_64-linux-gnu/libnss_files-2.13.so
7fa56efc8000-7fa56efc9000 r--p 0000b000 08:01 1183411                    /lib/x86_64-linux-gnu/libnss_files-2.13.so
7fa56efc9000-7fa56efca000 rw-p 0000c000 08:01 1183411                    /lib/x86_64-linux-gnu/libnss_files-2.13.so
7fa56efca000-7fa56efd4000 r-xp 00000000 08:01 1183415                    /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7fa56efd4000-7fa56f1d4000 ---p 0000a000 08:01 1183415                    /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7fa56f1d4000-7fa56f1d5000 r--p 0000a000 08:01 1183415                    /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7fa56f1d5000-7fa56f1d6000 rw-p 0000b000 08:01 1183415                    /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7fa56f1d6000-7fa56f1ed000 r-xp 00000000 08:01 1183405                    /lib/x86_64-linux-gnu/libnsl-2.13.so
7fa56f1ed000-7fa56f3ec000 ---p 00017000 08:01 1183405                    /lib/x86_64-linux-gnu/libnsl-2.13.so
7fa56f3ec000-7fa56f3ed000 r--p 00016000 08:01 1183405                    /lib/x86_64-linux-gnu/libnsl-2.13.so
7fa56f3ed000-7fa56f3ee000 rw-p 00017000 08:01 1183405                    /lib/x86_64-linux-gnu/libnsl-2.13.so
7fa56f3ee000-7fa56f3f0000 rw-p 00000000 00:00 0 
7fa56f3f0000-7fa56f3f8000 r-xp 00000000 08:01 1183407                    /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7fa56f3f8000-7fa56f5f7000 ---p 00008000 08:01 1183407                    /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7fa56f5f7000-7fa56f5f8000 r--p 00007000 08:01 1183407                    /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7fa56f5f8000-7fa56f5f9000 rw-p 00008000 08:01 1183407                    /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7fa56f5f9000-7fa56f625000 r-xp 00000000 08:01 16122143                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
7fa56f625000-7fa56f824000 ---p 0002c000 08:01 16122143                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
7fa56f824000-7fa56f825000 r--p 0002b000 08:01 16122143                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
7fa56f825000-7fa56f828000 rw-p 0002c000 08:01 16122143                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
7fa56f828000-7fa56f836000 r-xp 00000000 08:01 16122129                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
7fa56f836000-7fa56fa35000 ---p 0000e000 08:01 16122129                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
7fa56fa35000-7fa56fa37000 r--p 0000d000 08:01 16122129                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
7fa56fa37000-7fa56fa38000 rw-p 0000f000 08:01 16122129                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
7fa56fa38000-7fa56fa3f000 r-xp 00000000 08:01 1183434                    /lib/x86_64-linux-gnu/librt-2.13.so
7fa56fa3f000-7fa56fc3e000 ---p 00007000 08:01 1183434                    /lib/x86_64-linux-gnu/librt-2.13.so
7fa56fc3e000-7fa56fc3f000 r--p 00006000 08:01 1183434                    /lib/x86_64-linux-gnu/librt-2.13.so
7fa56fc3f000-7fa56fc40000 rw-p 00007000 08:01 1183434                    /lib/x86_64-linux-gnu/librt-2.13.so
7fa56fc40000-7fa56fc55000 r-xp 00000000 08:01 1183391                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa56fc55000-7fa56fe54000 ---p 00015000 08:01 1183391                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa56fe54000-7fa56fe55000 r--p 00014000 08:01 1183391                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa56fe55000-7fa56fe56000 rw-p 00015000 08:01 1183391                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa56fe56000-7fa56fed9000 r-xp 00000000 08:01 1183400                    /lib/x86_64-linux-gnu/libm-2.13.so
7fa56fed9000-7fa5700d8000 ---p 00083000 08:01 1183400                    /lib/x86_64-linux-gnu/libm-2.13.so
7fa5700d8000-7fa5700d9000 r--p 00082000 08:01 1183400                    /lib/x86_64-linux-gnu/libm-2.13.so
7fa5700d9000-7fa5700da000 rw-p 00083000 08:01 1183400                    /lib/x86_64-linux-gnu/libm-2.13.so
7fa5700da000-7fa5701c2000 r-xp 00000000 08:01 13115398                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7fa5701c2000-7fa5703c2000 ---p 000e8000 08:01 13115398                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7fa5703c2000-7fa5703ca000 r--p 000e8000 08:01 13115398                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7fa5703ca000-7fa5703cc000 rw-p 000f0000 08:01 13115398                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7fa5703cc000-7fa5703e1000 rw-p 00000000 00:00 0 
7fa5703e1000-7fa570ce4000 r-xp 00000000 08:01 16122147                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
7fa570ce4000-7fa570ee3000 ---p 00903000 08:01 16122147                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
7fa570ee3000-7fa570f64000 r--p 00902000 08:01 16122147                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
7fa570f64000-7fa570f7f000 rw-p 00983000 08:01 16122147                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
7fa570f7f000-7fa570fa8000 rw-p 00000000 00:00 0 
7fa570fa8000-7fa570fbf000 r-xp 00000000 08:01 1183453                    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7fa570fbf000-7fa5711be000 ---p 00017000 08:01 1183453                    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7fa5711be000-7fa5711bf000 r--p 00016000 08:01 1183453                    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7fa5711bf000-7fa5711c0000 rw-p 00017000 08:01 1183453                    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7fa5711c0000-7fa571355000 r-xp 00000000 08:01 1183370                    /lib/x86_64-linux-gnu/libc-2.13.so
7fa571355000-7fa571554000 ---p 00195000 08:01 1183370                    /lib/x86_64-linux-gnu/libc-2.13.so
7fa571554000-7fa571558000 r--p 00194000 08:01 1183370                    /lib/x86_64-linux-gnu/libc-2.13.so
7fa571558000-7fa571559000 rw-p 00198000 08:01 1183370                    /lib/x86_64-linux-gnu/libc-2.13.so
7fa571559000-7fa57155f000 rw-p 00000000 00:00 0 
7fa57155f000-7fa571561000 r-xp 00000000 08:01 1183381                    /lib/x86_64-linux-gnu/libdl-2.13.so
7fa571561000-7fa571761000 ---p 00002000 08:01 1183381                    /lib/x86_64-linux-gnu/libdl-2.13.so
7fa571761000-7fa571762000 r--p 00002000 08:01 1183381                    /lib/x86_64-linux-gnu/libdl-2.13.so
7fa571762000-7fa571763000 rw-p 00003000 08:01 1183381                    /lib/x86_64-linux-gnu/libdl-2.13.so
7fa571763000-7fa571767000 r-xp 00000000 08:01 16122127                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
7fa571767000-7fa571966000 ---p 00004000 08:01 16122127                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
7fa571966000-7fa571967000 r--p 00003000 08:01 16122127                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
7fa571967000-7fa571968000 rw-p 00004000 08:01 16122127                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
7fa571968000-7fa571980000 r-xp 00000000 08:01 1183430                    /lib/x86_64-linux-gnu/libpthread-2.13.so
7fa571980000-7fa571b7f000 ---p 00018000 08:01 1183430                    /lib/x86_64-linux-gnu/libpthread-2.13.so
7fa571b7f000-7fa571b80000 r--p 00017000 08:01 1183430                    /lib/x86_64-linux-gnu/libpthread-2.13.so
7fa571b80000-7fa571b81000 rw-p 00018000 08:01 1183430                    /lib/x86_64-linux-gnu/libpthread-2.13.so
7fa571b81000-7fa571b85000 rw-p 00000000 00:00 0 
7fa571b85000-7fa571ba6000 r-xp 00000000 08:01 1183357                    /lib/x86_64-linux-gnu/ld-2.13.so
7fa571ba6000-7fa571bab000 r--s 00000000 08:01 3145799                    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le64.cache-3
7fa571bab000-7fa571bbb000 r--s 00000000 08:01 3145809                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
7fa571bbb000-7fa571bc5000 rw-p 00000000 00:00 0 
7fa571bc5000-7fa571c7b000 rw-p 00000000 00:00 0 
7fa571c7b000-7fa571c7e000 ---p 00000000 00:00 0 
7fa571c7e000-7fa571d81000 rw-p 00000000 00:00 0 
7fa571d81000-7fa571d82000 r--s 00000000 08:01 3148414                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le64.cache-3
7fa571d82000-7fa571d83000 r--s 00000000 08:01 3145814                    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le64.cache-3
7fa571d83000-7fa571d84000 r--s 00000000 08:01 3145794                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le64.cache-3
7fa571d84000-7fa571d85000 r--s 00000000 08:01 3145787                    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le64.cache-3
7fa571d85000-7fa571d86000 r--s 00000000 08:01 3145797                    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le64.cache-3
7fa571d86000-7fa571d89000 r--s 00000000 08:01 3145810                    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le64.cache-3
7fa571d89000-7fa571d8a000 r--s 00000000 08:01 3148414                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le64.cache-3
7fa571d8a000-7fa571d92000 r--s 00000000 08:01 3157568                    /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le64.cache-3
7fa571d92000-7fa571d95000 r--s 00000000 08:01 3148439                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le64.cache-3
7fa571d95000-7fa571d99000 r--s 00000000 08:01 3157567                    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3
7fa571d99000-7fa571da1000 rw-s 00000000 08:01 18350126                   /tmp/hsperfdata_ronnoc/2986 (deleted)
7fa571da1000-7fa571da2000 rw-p 00000000 00:00 0 
7fa571da2000-7fa571da3000 ---p 00000000 00:00 0 
7fa571da3000-7fa571da5000 rw-p 00000000 00:00 0 
7fa571da5000-7fa571da6000 r--p 00020000 08:01 1183357                    /lib/x86_64-linux-gnu/ld-2.13.so
7fa571da6000-7fa571da8000 rw-p 00021000 08:01 1183357                    /lib/x86_64-linux-gnu/ld-2.13.so
7fff13793000-7fff137c9000 rw-p 00000000 00:00 0                          [stack]
7fff137ff000-7fff13800000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

VM Arguments:
java_command: minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server:/usr/lib/jvm/java-6-openjdk/jre/lib/amd64:/usr/lib/jvm/java-6-openjdk/jre/../lib/amd64
SHELL=/bin/bash
DISPLAY=:0

Signal Handlers:
SIGSEGV: [libjvm.so+0x783e60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x783e60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x6485c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x6485c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x6485c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x648770], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x64b280], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x64b280], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x64b280], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x64b280], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 11.10 (oneiric)
uname:Linux 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
libc:glibc 2.13 NPTL 2.13 
rlimit: STACK 8192k, CORE 0k, NPROC 63041, NOFILE 4096, AS infinity
load average:0.42 0.70 0.43

/proc/meminfo:
MemTotal:        8156636 kB
MemFree:         5634648 kB
Buffers:           42624 kB
Cached:           992688 kB
SwapCached:            0 kB
Active:          1299976 kB
Inactive:         815068 kB
Active(anon):    1080492 kB
Inactive(anon):    29820 kB
Active(file):     219484 kB
Inactive(file):   785248 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       8347644 kB
SwapFree:        8347644 kB
Dirty:             22156 kB
Writeback:             0 kB
AnonPages:       1079740 kB
Mapped:           223764 kB
Shmem:             30584 kB
Slab:              61792 kB
SReclaimable:      35864 kB
SUnreclaim:        25928 kB
KernelStack:        3128 kB
PageTables:        33608 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    12425960 kB
Committed_AS:    2451812 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      331688 kB
VmallocChunk:   34359400388 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      189440 kB
DirectMap2M:     5019648 kB
DirectMap1G:     3145728 kB


CPU:total 4 (4 cores per cpu, 1 threads per core) family 16 model 5 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext, 3dnow, 3dnowext, lzcnt, sse4a

Memory: 4k page, physical 8156636k(5634648k free), swap 8347644k(8347644k free)

vm_info: OpenJDK 64-Bit Server VM (20.0-b11) for linux-amd64 JRE (1.6.0_23-b23), built on Oct 22 2011 01:00:57 by "buildd" with gcc 4.6.1

time: Sun Jan  8 12:46:36 2012
elapsed time: 88 seconds



---

