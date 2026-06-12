---
title: "A fatal error has been detected by the Java Runtime Environment"
date: 2010-11-21
forum: General Help
---

### Post by shadow9234 on 2010-11-21
So when I try to run minecraft(Go to minecraft.net if you don't know what it is) it crashes and I get this in a .log file:
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00a53ef6, pid=7235, tid=3034143600
#
# JRE version: 6.0_18-b18
# Java VM: OpenJDK Client VM (16.0-b13 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.8.2
# Distribution: Ubuntu 10.04.1 LTS, package 6b18-1.8.2-4ubuntu2
# Problematic frame:
# C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x09e68000):  JavaThread "Thread-5" [_thread_in_native, id=7257, stack(0xb4d45000,0xb4d96000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000004

Registers:
EAX=0x00000041, EBX=0x09d238c8, ECX=0x09d6c848, EDX=0x00aa0d60
ESP=0xb4d92a74, EBP=0x09d34300, ESI=0x00000000, EDI=0x00000001
EIP=0x00a53ef6, CR2=0x00000004, EFLAGS=0x00210202

Top of Stack: (sp=0xb4d92a74)
0xb4d92a74:   004b29ae 004b4ecd 00000000 00000000
0xb4d92a84:   0000000d 00000078 b4d92aac 0000000d
0xb4d92a94:   00000064 00000001 09d34300 00002000
0xb4d92aa4:   09f72d9c 00a515d0 09d34300 b4d92af0
0xb4d92ab4:   b4d92af4 0059c3c0 00000080 0059c3f0
0xb4d92ac4:   0059aff4 0059c3c0 b4d94b1c bfb65ac8
0xb4d92ad4:   bfb67f18 b4d92b08 00473932 bfb67f1a
0xb4d92ae4:   00a7f0de 00000013 00a7f0de 00000013 

Instructions: (pc=0x00a53ef6)
0x00a53ee6:   00 66 89 79 02 83 45 6c 04 83 45 60 01 8b 76 08
0x00a53ef6:   0f b6 56 04 88 11 88 41 01 33 c9 8d 04 24 51 51 

Stack: [0xb4d45000,0xb4d96000],  sp=0xb4d92a74,  free space=136b4d92414k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(JILjava/nio/ByteBuffer;Lorg/lwjgl/opengl/PixelFormat;)V+0
j  org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(Lorg/lwjgl/opengl/PixelFormat;)V+24
j  org.lwjgl.opengl.LinuxDisplay.createPeerInfo(Lorg/lwjgl/opengl/PixelFormat;)Lorg/lwjgl/opengl/PeerInfo;+6
j  org.lwjgl.opengl.Display.create(Lorg/lwjgl/opengl/PixelFormat;Lorg/lwjgl/opengl/Drawable;Lorg/lwjgl/opengl/ContextAttribs;)V+55
j  org.lwjgl.opengl.Display.create(Lorg/lwjgl/opengl/PixelFormat;)V+9
j  org.lwjgl.opengl.Display.create()V+13
j  com.mojang.minecraft.l.run()V+88
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x09cec400 JavaThread "DestroyJavaVM" [_thread_blocked, id=7236, stack(0xb77c4000,0xb7815000)]
  0x09f4e400 JavaThread "Timer-1" [_thread_blocked, id=7258, stack(0xb4cf4000,0xb4d45000)]
=>0x09e68000 JavaThread "Thread-5" [_thread_in_native, id=7257, stack(0xb4d45000,0xb4d96000)]
  0x09f47400 JavaThread "Thread-4" daemon [_thread_blocked, id=7256, stack(0xb4d96000,0xb4de7000)]
  0x09e4b000 JavaThread "TimerQueue" daemon [_thread_blocked, id=7255, stack(0xb4e6d000,0xb4ebe000)]
  0x09dc6000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=7254, stack(0xb4f82000,0xb4fd3000)]
  0x09d31800 JavaThread "AWT-Shutdown" [_thread_blocked, id=7253, stack(0xb4f31000,0xb4f82000)]
  0x09e2fc00 JavaThread "AWT-XAWT" daemon [_thread_blocked, id=7246, stack(0xb4fd3000,0xb5024000)]
  0x09dfcc00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=7245, stack(0xb50ac000,0xb50fd000)]
  0x09de9000 JavaThread "Timer-0" daemon [_thread_blocked, id=7244, stack(0xb50fd000,0xb514e000)]
  0x09d27400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=7242, stack(0xb51f8000,0xb5249000)]
  0x09d25800 JavaThread "CompilerThread0" daemon [_thread_blocked, id=7241, stack(0xb5249000,0xb52ca000)]
  0x09d23c00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=7240, stack(0xb52ca000,0xb531b000)]
  0x09d1ac00 JavaThread "Finalizer" daemon [_thread_blocked, id=7239, stack(0xb5361000,0xb53b2000)]
  0x09d19400 JavaThread "Reference Handler" daemon [_thread_blocked, id=7238, stack(0xb53b2000,0xb5403000)]

Other Threads:
  0x09d17c00 VMThread [stack: 0xb5403000,0xb5484000] [id=7237]
  0x09d2b000 WatcherThread [stack: 0xb5177000,0xb51f8000] [id=7243]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 4352K, used 562K [0x83070000, 0x83520000, 0x87310000)
  eden space 3904K,  14% used [0x83070000, 0x830fcb10, 0x83440000)
  from space 448K,   0% used [0x83440000, 0x83440000, 0x834b0000)
  to   space 448K,   0% used [0x834b0000, 0x834b0000, 0x83520000)
 tenured generation   total 9448K, used 5668K [0x87310000, 0x87c4a000, 0x8f870000)
   the space 9448K,  59% used [0x87310000, 0x87899140, 0x87899200, 0x87c4a000)
 compacting perm gen  total 12288K, used 3840K [0x8f870000, 0x90470000, 0x93870000)
   the space 12288K,  31% used [0x8f870000, 0x8fc300c0, 0x8fc30200, 0x90470000)
    ro space 10240K,  72% used [0x93870000, 0x93fba9f8, 0x93fbaa00, 0x94270000)
    rw space 12288K,  60% used [0x94270000, 0x949ab0d0, 0x949ab200, 0x94e70000)

Dynamic libraries:
00110000-00125000 r-xp 00000000 07:00 396838     /lib/tls/i686/cmov/libpthread-2.11.1.so
00125000-00126000 r--p 00014000 07:00 396838     /lib/tls/i686/cmov/libpthread-2.11.1.so
00126000-00127000 rw-p 00015000 07:00 396838     /lib/tls/i686/cmov/libpthread-2.11.1.so
00127000-00129000 rw-p 00000000 00:00 0 
00129000-0014d000 r-xp 00000000 07:00 396828     /lib/tls/i686/cmov/libm-2.11.1.so
0014d000-0014e000 r--p 00023000 07:00 396828     /lib/tls/i686/cmov/libm-2.11.1.so
0014e000-0014f000 rw-p 00024000 07:00 396828     /lib/tls/i686/cmov/libm-2.11.1.so
0014f000-00155000 r-xp 00000000 07:00 396831     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00155000-00156000 r--p 00006000 07:00 396831     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00156000-00157000 rw-p 00007000 07:00 396831     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00158000-0015f000 r-xp 00000000 07:00 396840     /lib/tls/i686/cmov/librt-2.11.1.so
0015f000-00160000 r--p 00006000 07:00 396840     /lib/tls/i686/cmov/librt-2.11.1.so
00160000-00161000 rw-p 00007000 07:00 396840     /lib/tls/i686/cmov/librt-2.11.1.so
00161000-00168000 r-xp 00000000 07:00 415177     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00168000-00169000 r--p 00006000 07:00 415177     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00169000-0016a000 rw-p 00007000 07:00 415177     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
0016a000-00178000 r-xp 00000000 07:00 394997     /usr/lib/libXext.so.6.4.0
00178000-00179000 r--p 0000d000 07:00 394997     /usr/lib/libXext.so.6.4.0
00179000-0017a000 rw-p 0000e000 07:00 394997     /usr/lib/libXext.so.6.4.0
0017a000-0017e000 r-xp 00000000 07:00 395025     /usr/lib/libXtst.so.6.1.0
0017e000-0017f000 r--p 00003000 07:00 395025     /usr/lib/libXtst.so.6.1.0
0017f000-00180000 rw-p 00004000 07:00 395025     /usr/lib/libXtst.so.6.1.0
00180000-0018c000 r-xp 00000000 07:00 395005     /usr/lib/libXi.so.6.1.0
0018c000-0018d000 r--p 0000c000 07:00 395005     /usr/lib/libXi.so.6.1.0
0018d000-0018e000 rw-p 0000d000 07:00 395005     /usr/lib/libXi.so.6.1.0
0018e000-001d2000 r-xp 00000000 07:00 415153     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
001d2000-001d4000 r--p 00043000 07:00 415153     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
001d4000-001d5000 rw-p 00045000 07:00 415153     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
001d5000-001da000 rw-p 00000000 00:00 0 
001da000-001de000 r-xp 00000000 07:00 394999     /usr/lib/libXfixes.so.3.1.0
001de000-001df000 r--p 00003000 07:00 394999     /usr/lib/libXfixes.so.3.1.0
001df000-001e0000 rw-p 00004000 07:00 394999     /usr/lib/libXfixes.so.3.1.0
001e2000-001f5000 r-xp 00000000 07:00 396830     /lib/tls/i686/cmov/libnsl-2.11.1.so
001f5000-001f6000 r--p 00012000 07:00 396830     /lib/tls/i686/cmov/libnsl-2.11.1.so
001f6000-001f7000 rw-p 00013000 07:00 396830     /lib/tls/i686/cmov/libnsl-2.11.1.so
001f7000-001f9000 rw-p 00000000 00:00 0 
001f9000-0027e000 r-xp 00000000 07:00 415151     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
0027e000-0027f000 r--p 00084000 07:00 415151     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
0027f000-00285000 rw-p 00085000 07:00 415151     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00285000-002aa000 rw-p 00000000 00:00 0 
002aa000-002ab000 r-xp 00000000 07:00 415162     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
002ab000-002ac000 r--p 00000000 07:00 415162     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
002ac000-002ad000 rw-p 00001000 07:00 415162     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
002ae000-002b6000 r-xp 00000000 07:00 396835     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
002b6000-002b7000 r--p 00007000 07:00 396835     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
002b7000-002b8000 rw-p 00008000 07:00 396835     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
002b8000-002d5000 r-xp 00000000 07:00 263309     /lib/libgcc_s.so.1
002d5000-002d6000 r--p 0001c000 07:00 263309     /lib/libgcc_s.so.1
002d6000-002d7000 rw-p 0001d000 07:00 263309     /lib/libgcc_s.so.1
002d7000-002eb000 r-xp 00000000 07:00 415170     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
002eb000-002ec000 r--p 00013000 07:00 415170     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
002ec000-002ed000 rw-p 00014000 07:00 415170     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
002ed000-002fd000 r-xp 00000000 07:00 396839     /lib/tls/i686/cmov/libresolv-2.11.1.so
002fd000-002fe000 r--p 00010000 07:00 396839     /lib/tls/i686/cmov/libresolv-2.11.1.so
002fe000-002ff000 rw-p 00011000 07:00 396839     /lib/tls/i686/cmov/libresolv-2.11.1.so
002ff000-00301000 rw-p 00000000 00:00 0 
00301000-00308000 r-xp 00000000 07:00 545699     /usr/lib/fglrx/libatiuki.so.1.0
00308000-00309000 rw-p 00006000 07:00 545699     /usr/lib/fglrx/libatiuki.so.1.0
00317000-0032f000 r-xp 00000000 07:00 396035     /usr/lib/libxcb.so.1.1.0
0032f000-00330000 r--p 00017000 07:00 396035     /usr/lib/libxcb.so.1.1.0
00330000-00331000 rw-p 00018000 07:00 396035     /usr/lib/libxcb.so.1.1.0
00331000-003a2000 r-xp 00000000 07:00 395203     /usr/lib/libfreetype.so.6.3.22
003a2000-003a6000 r--p 00070000 07:00 395203     /usr/lib/libfreetype.so.6.3.22
003a6000-003a7000 rw-p 00074000 07:00 395203     /usr/lib/libfreetype.so.6.3.22
003d4000-003de000 r-xp 00000000 07:00 396833     /lib/tls/i686/cmov/libnss_files-2.11.1.so
003de000-003df000 r--p 00009000 07:00 396833     /lib/tls/i686/cmov/libnss_files-2.11.1.so
003df000-003e0000 rw-p 0000a000 07:00 396833     /lib/tls/i686/cmov/libnss_files-2.11.1.so
0041a000-0041c000 r-xp 00000000 07:00 394984     /usr/lib/libXau.so.6.0.0
0041c000-0041d000 r--p 00001000 07:00 394984     /usr/lib/libXau.so.6.0.0
0041d000-0041e000 rw-p 00002000 07:00 394984     /usr/lib/libXau.so.6.0.0
00445000-00598000 r-xp 00000000 07:00 396824     /lib/tls/i686/cmov/libc-2.11.1.so
00598000-00599000 ---p 00153000 07:00 396824     /lib/tls/i686/cmov/libc-2.11.1.so
00599000-0059b000 r--p 00153000 07:00 396824     /lib/tls/i686/cmov/libc-2.11.1.so
0059b000-0059c000 rw-p 00155000 07:00 396824     /lib/tls/i686/cmov/libc-2.11.1.so
0059c000-0059f000 rw-p 00000000 00:00 0 
0059f000-005e0000 r-xp 00000000 07:00 144239     /home/debbie/Desktop/Womclient/Womclient/native/linux/liblwjgl.so
005e0000-005e1000 rw-p 00041000 07:00 144239     /home/debbie/Desktop/Womclient/Womclient/native/linux/liblwjgl.so
005e2000-005e4000 r-xp 00000000 07:00 263347     /lib/libnss_mdns4_minimal.so.2
005e4000-005e5000 r--p 00001000 07:00 263347     /lib/libnss_mdns4_minimal.so.2
005e5000-005e6000 rw-p 00002000 07:00 263347     /lib/libnss_mdns4_minimal.so.2
0060c000-0061f000 r-xp 00000000 07:00 263424     /lib/libz.so.1.2.3.3
0061f000-00620000 r--p 00012000 07:00 263424     /lib/libz.so.1.2.3.3
00620000-00621000 rw-p 00013000 07:00 263424     /lib/libz.so.1.2.3.3
006c4000-006c8000 r-xp 00000000 07:00 396832     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
006c8000-006c9000 r--p 00004000 07:00 396832     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
006c9000-006ca000 rw-p 00005000 07:00 396832     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
006ec000-006f4000 r-xp 00000000 07:00 395019     /usr/lib/libXrender.so.1.3.0
006f4000-006f5000 r--p 00007000 07:00 395019     /usr/lib/libXrender.so.1.3.0
006f5000-006f6000 rw-p 00008000 07:00 395019     /usr/lib/libXrender.so.1.3.0
00721000-0073c000 r-xp 00000000 07:00 266752     /lib/ld-2.11.1.so
0073c000-0073d000 r--p 0001a000 07:00 266752     /lib/ld-2.11.1.so
0073d000-0073e000 rw-p 0001b000 07:00 266752     /lib/ld-2.11.1.so
0074b000-0074e000 r-xp 00000000 07:00 415148     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
0074e000-0074f000 r--p 00003000 07:00 415148     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
0074f000-00750000 rw-p 00004000 07:00 415148     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00760000-00784000 r-xp 00000000 07:00 415160     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00784000-00785000 r--p 00023000 07:00 415160     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00785000-00787000 rw-p 00024000 07:00 415160     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0078e000-00792000 r-xp 00000000 07:00 394995     /usr/lib/libXdmcp.so.6.0.0
00792000-00793000 r--p 00003000 07:00 394995     /usr/lib/libXdmcp.so.6.0.0
00793000-00794000 rw-p 00004000 07:00 394995     /usr/lib/libXdmcp.so.6.0.0
007ab000-007b7000 r-xp 00000000 07:00 415176     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
007b7000-007b8000 r--p 0000b000 07:00 415176     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
007b8000-007b9000 rw-p 0000c000 07:00 415176     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
007ba000-007c1000 r-xp 00000000 07:00 415171     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
007c1000-007c2000 r--p 00006000 07:00 415171     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
007c2000-007c3000 rw-p 00007000 07:00 415171     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
00818000-0081e000 r-xp 00000000 07:00 395017     /usr/lib/libXrandr.so.2.2.0
0081e000-0081f000 r--p 00005000 07:00 395017     /usr/lib/libXrandr.so.2.2.0
0081f000-00820000 rw-p 00006000 07:00 395017     /usr/lib/libXrandr.so.2.2.0
008b1000-008b8000 r-xp 00000000 07:00 673079     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
008b8000-008b9000 r--p 00006000 07:00 673079     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
008b9000-008ba000 rw-p 00007000 07:00 673079     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
008d0000-008d1000 r-xp 00000000 00:00 0          [vdso]
008d1000-009ea000 r-xp 00000000 07:00 394982     /usr/lib/libX11.so.6.3.0
009ea000-009eb000 r--p 00118000 07:00 394982     /usr/lib/libX11.so.6.3.0
009eb000-009ed000 rw-p 00119000 07:00 394982     /usr/lib/libX11.so.6.3.0
009ed000-009ee000 rw-p 00000000 00:00 0 
009ee000-00a95000 r-xp 00000000 07:00 545683     /usr/lib/fglrx/libGL.so.1.2
00a95000-00a9f000 rwxp 000a7000 07:00 545683     /usr/lib/fglrx/libGL.so.1.2
00a9f000-00aa4000 rwxp 00000000 00:00 0 
00af7000-00aff000 r-xp 00000000 07:00 394991     /usr/lib/libXcursor.so.1.0.2
00aff000-00b00000 r--p 00007000 07:00 394991     /usr/lib/libXcursor.so.1.0.2
00b00000-00b01000 rw-p 00008000 07:00 394991     /usr/lib/libXcursor.so.1.0.2
00b6e000-00bb3000 r-xp 00000000 07:00 416050     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00bb3000-00bb4000 r--p 00045000 07:00 416050     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00bb4000-00bb6000 rw-p 00046000 07:00 416050     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00bb6000-00bb7000 rw-p 00000000 00:00 0 
00c89000-00c8b000 r-xp 00000000 07:00 396827     /lib/tls/i686/cmov/libdl-2.11.1.so
00c8b000-00c8c000 r--p 00001000 07:00 396827     /lib/tls/i686/cmov/libdl-2.11.1.so
00c8c000-00c8d000 rw-p 00002000 07:00 396827     /lib/tls/i686/cmov/libdl-2.11.1.so
00c8d000-010a0000 r-xp 00000000 07:00 415143     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
010a0000-010b7000 r--p 00412000 07:00 415143     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
010b7000-010c4000 rw-p 00429000 07:00 415143     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
010c4000-014e0000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 07:00 267114     /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 07:00 267114     /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 07:00 267114     /usr/lib/jvm/java-6-openjdk/jre/bin/java
09ce6000-0a055000 rw-p 00000000 00:00 0          [heap]
83070000-83520000 rw-p 00000000 00:00 0 
83520000-87310000 rw-p 00000000 00:00 0 
87310000-87c4a000 rw-p 00000000 00:00 0 
87c4a000-8f870000 rw-p 00000000 00:00 0 
8f870000-90470000 rw-p 00000000 00:00 0 
90470000-93870000 rw-p 00000000 00:00 0 
93870000-93fbb000 r--s 00001000 07:00 415592     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
93fbb000-94270000 rw-p 00000000 00:00 0 
94270000-949ac000 rw-p 0074c000 07:00 415592     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
949ac000-94e70000 rw-p 00000000 00:00 0 
94e70000-94f6a000 rw-p 00e88000 07:00 415592     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94f6a000-95270000 rw-p 00000000 00:00 0 
95270000-95278000 r-xs 00f82000 07:00 415592     /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
95278000-95670000 rw-p 00000000 00:00 0 
b4a00000-b4a21000 rw-p 00000000 00:00 0 
b4a21000-b4b00000 ---p 00000000 00:00 0 
b4b05000-b4c96000 rw-s 00000000 00:04 7274497    /SYSV00000000 (deleted)
b4cf4000-b4cf7000 ---p 00000000 00:00 0 
b4cf7000-b4d45000 rw-p 00000000 00:00 0 
b4d45000-b4d48000 ---p 00000000 00:00 0 
b4d48000-b4d96000 rw-p 00000000 00:00 0 
b4d96000-b4d99000 ---p 00000000 00:00 0 
b4d99000-b4de7000 rw-p 00000000 00:00 0 
b4e6d000-b4e70000 ---p 00000000 00:00 0 
b4e70000-b4ebe000 rw-p 00000000 00:00 0 
b4eed000-b4eee000 r--s 00000000 07:00 401447     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4eee000-b4ef4000 r--s 00000000 07:00 401444     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4ef4000-b4ef6000 r--s 00000000 07:00 401445     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4ef6000-b4ef9000 r--s 00000000 07:00 401454     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4ef9000-b4efa000 r--s 00000000 07:00 401455     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4efa000-b4efe000 r--s 00000000 07:00 415882     /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-le32d4.cache-3
b4efe000-b4f01000 r--s 00000000 07:00 401441     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4f01000-b4f02000 r--s 00000000 07:00 401437     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4f02000-b4f03000 r--s 00000000 07:00 401431     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4f03000-b4f04000 r--s 00000000 07:00 401439     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4f04000-b4f08000 r--s 00000000 07:00 401446     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4f08000-b4f0f000 r--s 00000000 07:00 401440     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4f0f000-b4f1a000 r--s 00000000 07:00 401432     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4f1a000-b4f1d000 r--s 00000000 07:00 401451     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4f1d000-b4f1e000 r--s 00000000 07:00 401435     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4f1e000-b4f26000 r--s 00000000 07:00 401450     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4f26000-b4f2e000 r--s 00000000 07:00 412681     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4f2e000-b4f31000 r--s 00000000 07:00 406039     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4f31000-b4f34000 ---p 00000000 00:00 0 
b4f34000-b4f82000 rw-p 00000000 00:00 0 
b4f82000-b4f85000 ---p 00000000 00:00 0 
b4f85000-b4fd3000 rw-p 00000000 00:00 0 
b4fd3000-b4fd6000 ---p 00000000 00:00 0 
b4fd6000-b5024000 rw-p 00000000 00:00 0 
b5024000-b5025000 r--s 00000000 07:00 401447     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b5025000-b502b000 r--s 00000000 07:00 401444     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b502b000-b502d000 r--s 00000000 07:00 401445     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b502d000-b5030000 r--s 00000000 07:00 401454     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b5030000-b5031000 r--s 00000000 07:00 401455     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b5031000-b5035000 r--s 00000000 07:00 415882     /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-le32d4.cache-3
b5035000-b5038000 r--s 00000000 07:00 401441     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b5038000-b5039000 r--s 00000000 07:00 401437     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b5039000-b503a000 r--s 00000000 07:00 401431     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b503a000-b503b000 r--s 00000000 07:00 401439     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b503b000-b503f000 r--s 00000000 07:00 401446     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b503f000-b5046000 r--s 00000000 07:00 401440     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b5046000-b5051000 r--s 00000000 07:00 401432     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b5051000-b5054000 r--s 00000000 07:00 401451     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b5054000-b5055000 r--s 00000000 07:00 401435     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b5055000-b505d000 r--s 00000000 07:00 401450     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b505d000-b5065000 r--s 00000000 07:00 412681     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b5065000-b5068000 r--s 00000000 07:00 406039     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b5068000-b5069000 r--s 00000000 07:00 401447     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b5069000-b506f000 r--s 00000000 07:00 401444     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b506f000-b5071000 r--s 00000000 07:00 401445     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b5071000-b5074000 r--s 00000000 07:00 401454     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b5074000-b5075000 r--s 00000000 07:00 401455     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b5075000-b5079000 r--s 00000000 07:00 415882     /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-le32d4.cache-3
b5079000-b507c000 r--s 00000000 07:00 401441     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b507c000-b507d000 r--s 00000000 07:00 401437     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b507d000-b507e000 r--s 00000000 07:00 401431     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b507e000-b507f000 r--s 00000000 07:00 401439     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b507f000-b5083000 r--s 00000000 07:00 401446     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b5083000-b508a000 r--s 00000000 07:00 401440     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b508a000-b5095000 r--s 00000000 07:00 401432     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b5095000-b5098000 r--s 00000000 07:00 401451     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b5098000-b5099000 r--s 00000000 07:00 401435     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b5099000-b50a1000 r--s 00000000 07:00 401450     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b50a1000-b50a9000 r--s 00000000 07:00 412681     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b50a9000-b50ac000 r--s 00000000 07:00 406039     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b50ac000-b50af000 ---p 00000000 00:00 0 
b50af000-b50fd000 rw-p 00000000 00:00 0 
b50fd000-b5100000 ---p 00000000 00:00 0 
b5100000-b514e000 rw-p 00000000 00:00 0 
b514e000-b5155000 r--s 00102000 07:00 415119     /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
b5155000-b515a000 r--s 00043000 07:00 144232     /home/debbie/Desktop/Womclient/Womclient/lib/minecraft.jar
b515a000-b515c000 r--s 00007000 07:00 144233     /home/debbie/Desktop/Womclient/Womclient/lib/wom.jar
b515c000-b515f000 r--s 00011000 07:00 144231     /home/debbie/Desktop/Womclient/Womclient/lib/lwjgl_util.jar
b515f000-b5166000 r--s 00083000 07:00 144229     /home/debbie/Desktop/Womclient/Womclient/lib/lwjgl.jar
b5166000-b516b000 r--s 0002f000 07:00 144227     /home/debbie/Desktop/Womclient/Womclient/lib/jinput.jar
b516b000-b516e000 r--s 0000f000 07:00 415113     /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b516e000-b5177000 r--s 00065000 07:00 549594     /usr/share/java/gnome-java-bridge.jar
b5177000-b5178000 ---p 00000000 00:00 0 
b5178000-b51f8000 rw-p 00000000 00:00 0 
b51f8000-b51fb000 ---p 00000000 00:00 0 
b51fb000-b5249000 rw-p 00000000 00:00 0 
b5249000-b524c000 ---p 00000000 00:00 0 
b524c000-b52ca000 rw-p 00000000 00:00 0 
b52ca000-b52cd000 ---p 00000000 00:00 0 
b52cd000-b531b000 rw-p 00000000 00:00 0 
b531b000-b5322000 r--s 00000000 07:00 414028     /usr/lib/gconv/gconv-modules.cache
b5322000-b5361000 r--p 00000000 07:00 398510     /usr/lib/locale/en_US.utf8/LC_CTYPE
b5361000-b5364000 ---p 00000000 00:00 0 
b5364000-b53b2000 rw-p 00000000 00:00 0 
b53b2000-b53b5000 ---p 00000000 00:00 0 
b53b5000-b5403000 rw-p 00000000 00:00 0 
b5403000-b5404000 ---p 00000000 00:00 0 
b5404000-b54b7000 rw-p 00000000 00:00 0 
b54b7000-b5649000 r--s 03916000 07:00 415141     /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b5649000-b5657000 rw-p 00000000 00:00 0 
b5657000-b5671000 rw-p 00000000 00:00 0 
b5671000-b5676000 rw-p 00000000 00:00 0 
b5676000-b56b4000 rw-p 00000000 00:00 0 
b56b4000-b56b7000 rw-p 00000000 00:00 0 
b56b7000-b56d5000 rw-p 00000000 00:00 0 
b56d5000-b56da000 rw-p 00000000 00:00 0 
b56da000-b5718000 rw-p 00000000 00:00 0 
b5718000-b571e000 rw-p 00000000 00:00 0 
b571e000-b5738000 rw-p 00000000 00:00 0 
b5738000-b5749000 rw-p 00000000 00:00 0 
b5749000-b57c4000 rw-p 00000000 00:00 0 
b57c4000-b58fc000 rwxp 00000000 00:00 0 
b58fc000-b77c4000 rw-p 00000000 00:00 0 
b77c4000-b77c7000 ---p 00000000 00:00 0 
b77c7000-b7818000 rw-p 00000000 00:00 0 
b7818000-b7819000 r--p 00000000 00:00 0 
b7819000-b781f000 rw-p 00000000 00:00 0 
b781f000-b7827000 rw-s 00000000 07:00 678516     /tmp/hsperfdata_debbie/7235
b7827000-b7828000 rw-p 00000000 00:00 0 
b7828000-b7829000 r--p 00000000 00:00 0 
b7829000-b782b000 rw-p 00000000 00:00 0 
bfb53000-bfb68000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Djava.library.path=native/linux -Dsun.java2d.noddraw=true -Dsun.awt.noerasebackground=true -Dsun.java2d.d3d=false -Dsun.java2d.opengl=false -Dsun.java2d.pmoffscreen=false -Xmx200M 
java_command: Main
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3af380], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3af380], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x2d93c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x2d93c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x2d93c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x2d93c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x2d8ab0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x2db260], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x2db260], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x2db260], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x2db260], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:2.53 2.29 1.61

CPU:total 1 (1 cores per cpu, 1 threads per core) family 15 model 15 stepping 0, cmov, cx8, fxsr, mmx, sse, sse2, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 508256k(6388k free), swap 261112k(242936k free)

vm_info: OpenJDK Client VM (16.0-b13) for linux-x86 JRE (1.6.0_18-b18), built on Oct 25 2010 18:26:10 by "buildd" with gcc 4.4.3

time: Sun Nov 21 09:52:42 2010
elapsed time: 32 seconds 

:confused: Help?

---

### Post by shadow9234 on 2010-11-21
bump :(

---

### Post by epsolon77 on 2010-12-02
I'm having the same issue with minecraft.  I'm on 10.04 server and have used both OpenJDK and SunJava JRE.  Would love to know a solution.

---

### Post by lykeion on 2010-12-03
@Shadoww9234
First of all, please enclose code output with CODE tags otherwise it's pretty unreadable.
The error pinpoints the problematic frame to libGL.so.1, and for me this suggests it has to do with the graphics driver (fglrx in your case). 
The problem is discussed in the minecraft forums: [http://www.minecraftforum.net/viewtopic.php?f=17&t=29864](http://www.minecraftforum.net/viewtopic.php?f=17&t=29864)
You should try that forum for help.

EDIT
Just dug a little deeper into this and it seems that someone got rid of the problem when updating to Ubuntu 10.10, see: [http://www.minecraftforum.net/viewtopic.php?f=17&t=34493](http://www.minecraftforum.net/viewtopic.php?f=17&t=34493)

---

