---
title: "Java Crashes"
date: 2010-08-20
forum: General Help
---

### Post by Vapourstreak on 2010-08-20
Trying to run Moparscape's .sh file.  After a few seconds, maybe 5 or so, it crashes.

> #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb6c0f85d, pid=14720, tid=2414599024
#
# JRE version: 6.0_21-b06
# Java VM: Java HotSpot(TM) Server VM (17.0-b16 mixed mode linux-x86 )
# Problematic frame:
# V  [libjvm.so+0x12a85d]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread (0x08f76400):  JavaThread "CompilerThread0" daemon [_thread_in_native, id=14728, stack(0x8fe3d000,0x8febe000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000000

Registers:
EAX=0x0949ec94, EBX=0xb725f748, ECX=0x090e5e14, EDX=0x00000000
ESP=0x8febae64, EBP=0x8febaea8, ESI=0x8febc0f0, EDI=0x090e5e14
EIP=0xb6c0f85d, CR2=0x00000000, EFLAGS=0x00010296

Top of Stack: (sp=0x8febae64)
0x8febae64:   8febc0f0 00000007 b725f748 8febc930
0x8febae74:   8febc0f0 8febaea8 b708f7c2 090e5e14
0x8febae84:   8febaee8 00000001 00000001 0949ec94
0x8febae94:   00000000 0100eca3 b725f748 8febc0f0
0x8febaea4:   090e5e14 8febaef8 b7091abc 090e5e14
0x8febaeb4:   8febc0f0 00000001 8e6adf78 094a0bbc
0x8febaec4:   094a0bbc 090e5e14 8e6acd28 0949cd14
0x8febaed4:   0000196e 08f03138 8e6adb30 00000003 

Instructions: (pc=0xb6c0f85d)
0xb6c0f84d:   fe fe 64 00 8b 50 04 89 55 ec 8b 40 08 89 45 e8
0xb6c0f85d:   8b 02 52 ff 10 8b 55 e8 89 c7 8b 02 89 14 24 ff 

Stack: [0x8fe3d000,0x8febe000],  sp=0x8febae64,  free space=1f78feba7e0k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x12a85d]
V  [libjvm.so+0x5acabc]
V  [libjvm.so+0x5ac720]
V  [libjvm.so+0x4f6a8f]
V  [libjvm.so+0x27b85f]
V  [libjvm.so+0x278043]
V  [libjvm.so+0x209767]
V  [libjvm.so+0x280f8c]
V  [libjvm.so+0x280839]
V  [libjvm.so+0x66feb6]
V  [libjvm.so+0x66959e]
V  [libjvm.so+0x57a89e]
C  [libpthread.so.0+0x596e]


Current CompileTask:
C2:441      client.doWalkTo(IIIIIIIIIIZI)Z (1987 bytes)


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x09441400 JavaThread "Thread-11" daemon [_thread_blocked, id=14754, stack(0x8ea0d000,0x8ea5e000)]
  0x09440400 JavaThread "Thread-10" daemon [_thread_blocked, id=14753, stack(0x8f3bc000,0x8f40d000)]
  0x093f1c00 JavaThread "Thread-9" daemon [_thread_in_native, id=14749, stack(0x8ea5e000,0x8eaaf000)]
  0x8fd0a800 JavaThread "Thread-8" daemon [_thread_blocked, id=14748, stack(0x8eaaf000,0x8eb00000)]
  0x08ee2c00 JavaThread "Thread-7" daemon [_thread_blocked, id=14747, stack(0x8e830000,0x8e881000)]
  0x8fd04000 JavaThread "DestroyJavaVM" [_thread_blocked, id=14721, stack(0xb6a6e000,0xb6abf000)]
  0x091abc00 JavaThread "Thread-6" daemon [_thread_blocked, id=14744, stack(0x8ec40000,0x8ec91000)]
  0x8fafe400 JavaThread "Java Sound Event Dispatcher" daemon [_thread_blocked, id=14740, stack(0x8ec91000,0x8ece2000)]
  0x8f55c400 JavaThread "Java Sound Event Dispatcher" daemon [_thread_blocked, id=14739, stack(0x8ece2000,0x8ed33000)]
  0x09192400 JavaThread "Thread-2" daemon [_thread_in_Java, id=14738, stack(0x8f36b000,0x8f3bc000)]
  0x0917f000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=14736, stack(0x8f40d000,0x8f45e000)]
  0x0917e400 JavaThread "AWT-Shutdown" [_thread_blocked, id=14735, stack(0x8f45e000,0x8f4af000)]
  0x0915e800 JavaThread "Thread-1" daemon [_thread_blocked, id=14734, stack(0x8f4af000,0x8f500000)]
  0x8faf9000 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=14733, stack(0x8f704000,0x8f755000)]
  0x8fa65800 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=14732, stack(0x8f755000,0x8f7a6000)]
  0x08f79c00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=14730, stack(0x8fc2e000,0x8fc7f000)]
  0x08f78000 JavaThread "CompilerThread1" daemon [_thread_blocked, id=14729, stack(0x8fc7f000,0x8fd00000)]
=>0x08f76400 JavaThread "CompilerThread0" daemon [_thread_in_native, id=14728, stack(0x8fe3d000,0x8febe000)]
  0x08f74800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=14727, stack(0x8febe000,0x8ff0f000)]
  0x08f65800 JavaThread "Finalizer" daemon [_thread_blocked, id=14726, stack(0x8ff4e000,0x8ff9f000)]
  0x08f60c00 JavaThread "Reference Handler" daemon [_thread_blocked, id=14725, stack(0x8ff9f000,0x8fff0000)]

Other Threads:
  0x08f5e400 VMThread [stack: 0x8fff0000,0x90071000] [id=14724]
  0x08f7c000 WatcherThread [stack: 0x8fbad000,0x8fc2e000] [id=14731]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 46976K, used 7595K [0xa9280000, 0xad3a0000, 0xb3920000)
  eden space 29184K, 26% used [0xa9280000,0xa99eac08,0xaaf00000)
  from space 17792K, 0% used [0xac240000,0xac240000,0xad3a0000)
  to   space 18752K, 0% used [0xaaf00000,0xaaf00000,0xac150000)
 PSOldGen        total 95616K, used 77360K [0x94520000, 0x9a280000, 0xa9280000)
  object space 95616K, 80% used [0x94520000,0x990ac1a8,0x9a280000)
 PSPermGen       total 21760K, used 12096K [0x90520000, 0x91a60000, 0x94520000)
  object space 21760K, 55% used [0x90520000,0x910f0278,0x91a60000)

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:01 669820     /opt/java/32/jre1.6.0_21/bin/java
08052000-08053000 rwxp 00009000 08:01 669820     /opt/java/32/jre1.6.0_21/bin/java
08edd000-0ae4d000 rwxp 00000000 00:00 0          [heap]
8c900000-8c9fc000 rwxp 00000000 00:00 0 
8c9fc000-8ca00000 ---p 00000000 00:00 0 
8ca00000-8caf6000 rwxp 00000000 00:00 0 
8caf6000-8cb00000 ---p 00000000 00:00 0 
8cb00000-8cbf9000 rwxp 00000000 00:00 0 
8cbf9000-8cc00000 ---p 00000000 00:00 0 
8cc00000-8ccf8000 rwxp 00000000 00:00 0 
8ccf8000-8cd00000 ---p 00000000 00:00 0 
8cd00000-8cdf9000 rwxp 00000000 00:00 0 
8cdf9000-8ce00000 ---p 00000000 00:00 0 
8ce00000-8cef9000 rwxp 00000000 00:00 0 
8cef9000-8cf00000 ---p 00000000 00:00 0 
8cf00000-8cff9000 rwxp 00000000 00:00 0 
8cff9000-8d000000 ---p 00000000 00:00 0 
8d000000-8d0f9000 rwxp 00000000 00:00 0 
8d0f9000-8d100000 ---p 00000000 00:00 0 
8d100000-8d1f9000 rwxp 00000000 00:00 0 
8d1f9000-8d200000 ---p 00000000 00:00 0 
8d200000-8d2f9000 rwxp 00000000 00:00 0 
8d2f9000-8d300000 ---p 00000000 00:00 0 
8d300000-8d3f9000 rwxp 00000000 00:00 0 
8d3f9000-8d400000 ---p 00000000 00:00 0 
8d400000-8d4f9000 rwxp 00000000 00:00 0 
8d4f9000-8d500000 ---p 00000000 00:00 0 
8d500000-8d5f9000 rwxp 00000000 00:00 0 
8d5f9000-8d600000 ---p 00000000 00:00 0 
8d600000-8d6f9000 rwxp 00000000 00:00 0 
8d6f9000-8d700000 ---p 00000000 00:00 0 
8d700000-8d7f9000 rwxp 00000000 00:00 0 
8d7f9000-8d800000 ---p 00000000 00:00 0 
8d800000-8d8f9000 rwxp 00000000 00:00 0 
8d8f9000-8d900000 ---p 00000000 00:00 0 
8d900000-8d9f9000 rwxp 00000000 00:00 0 
8d9f9000-8da00000 ---p 00000000 00:00 0 
8da00000-8daf9000 rwxp 00000000 00:00 0 
8daf9000-8db00000 ---p 00000000 00:00 0 
8db00000-8dbf9000 rwxp 00000000 00:00 0 
8dbf9000-8dc00000 ---p 00000000 00:00 0 
8dc00000-8dcf9000 rwxp 00000000 00:00 0 
8dcf9000-8dd00000 ---p 00000000 00:00 0 
8dd00000-8ddfc000 rwxp 00000000 00:00 0 
8ddfc000-8de00000 ---p 00000000 00:00 0 
8de00000-8def9000 rwxp 00000000 00:00 0 
8def9000-8df00000 ---p 00000000 00:00 0 
8df00000-8dff4000 rwxp 00000000 00:00 0 
8dff4000-8e000000 ---p 00000000 00:00 0 
8e100000-8e1f6000 rwxp 00000000 00:00 0 
8e1f6000-8e200000 ---p 00000000 00:00 0 
8e200000-8e2f2000 rwxp 00000000 00:00 0 
8e2f2000-8e300000 ---p 00000000 00:00 0 
8e300000-8e400000 rwxp 00000000 00:00 0 
8e500000-8e5fb000 rwxp 00000000 00:00 0 
8e5fb000-8e600000 ---p 00000000 00:00 0 
8e600000-8e6f6000 rwxp 00000000 00:00 0 
8e6f6000-8e700000 ---p 00000000 00:00 0 
8e700000-8e7f6000 rwxp 00000000 00:00 0 
8e7f6000-8e800000 ---p 00000000 00:00 0 
8e830000-8e833000 ---p 00000000 00:00 0 
8e833000-8e881000 rwxp 00000000 00:00 0 
8e881000-8e8af000 r-xp 00000000 08:01 669952     /opt/java/32/jre1.6.0_21/lib/i386/libjpeg.so
8e8af000-8e8b0000 rwxp 0002e000 08:01 669952     /opt/java/32/jre1.6.0_21/lib/i386/libjpeg.so
8e8b0000-8e8c0000 r-xp 00000000 08:01 133534     /lib/tls/i686/cmov/libresolv-2.11.1.so
8e8c0000-8e8c1000 r-xp 00010000 08:01 133534     /lib/tls/i686/cmov/libresolv-2.11.1.so
8e8c1000-8e8c2000 rwxp 00011000 08:01 133534     /lib/tls/i686/cmov/libresolv-2.11.1.so
8e8c2000-8e8c4000 rwxp 00000000 00:00 0 
8e900000-8e9f8000 rwxp 00000000 00:00 0 
8e9f8000-8ea00000 ---p 00000000 00:00 0 
8ea0d000-8ea10000 ---p 00000000 00:00 0 
8ea10000-8ea5e000 rwxp 00000000 00:00 0 
8ea5e000-8ea61000 ---p 00000000 00:00 0 
8ea61000-8eaaf000 rwxp 00000000 00:00 0 
8eaaf000-8eab2000 ---p 00000000 00:00 0 
8eab2000-8eb00000 rwxp 00000000 00:00 0 
8eb00000-8ebe4000 rwxp 00000000 00:00 0 
8ebe4000-8ec00000 ---p 00000000 00:00 0 
8ec40000-8ec43000 ---p 00000000 00:00 0 
8ec43000-8ec91000 rwxp 00000000 00:00 0 
8ec91000-8ec94000 ---p 00000000 00:00 0 
8ec94000-8ece2000 rwxp 00000000 00:00 0 
8ece2000-8ece5000 ---p 00000000 00:00 0 
8ece5000-8ed33000 rwxp 00000000 00:00 0 
8ed35000-8ed39000 r-xp 00000000 08:01 133488     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
8ed39000-8ed3a000 r-xp 00004000 08:01 133488     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
8ed3a000-8ed3b000 rwxp 00005000 08:01 133488     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
8ed5f000-8ed62000 ---p 00000000 00:00 0 
8ed62000-8edb0000 rwxp 00000000 00:00 0 
8edb0000-8edb5000 r-xp 00000000 08:01 141687     /usr/lib/libogg.so.0.6.0
8edb5000-8edb6000 r-xp 00004000 08:01 141687     /usr/lib/libogg.so.0.6.0
8edb6000-8edb7000 rwxp 00005000 08:01 141687     /usr/lib/libogg.so.0.6.0
8edb7000-8edde000 r-xp 00000000 08:01 141929     /usr/lib/libvorbis.so.0.4.3
8edde000-8eddf000 r-xp 00026000 08:01 141929     /usr/lib/libvorbis.so.0.4.3
8eddf000-8ede0000 rwxp 00027000 08:01 141929     /usr/lib/libvorbis.so.0.4.3
8ede0000-8eecc000 r-xp 00000000 08:01 141931     /usr/lib/libvorbisenc.so.2.0.6
8eecc000-8eecd000 ---p 000ec000 08:01 141931     /usr/lib/libvorbisenc.so.2.0.6
8eecd000-8eedb000 r-xp 000ec000 08:01 141931     /usr/lib/libvorbisenc.so.2.0.6
8eedb000-8eedc000 rwxp 000fa000 08:01 141931     /usr/lib/libvorbisenc.so.2.0.6
8eedc000-8ef27000 r-xp 00000000 08:01 140913     /usr/lib/libFLAC.so.8.2.0
8ef27000-8ef28000 r-xp 0004a000 08:01 140913     /usr/lib/libFLAC.so.8.2.0
8ef28000-8ef29000 rwxp 0004b000 08:01 140913     /usr/lib/libFLAC.so.8.2.0
8ef29000-8ef60000 r-xp 00000000 08:01 133438     /lib/libdbus-1.so.3.4.0
8ef60000-8ef61000 r-xp 00036000 08:01 133438     /lib/libdbus-1.so.3.4.0
8ef61000-8ef62000 rwxp 00037000 08:01 133438     /lib/libdbus-1.so.3.4.0
8ef62000-8efc3000 r-xp 00000000 08:01 141841     /usr/lib/libsndfile.so.1.0.21
8efc3000-8efc4000 ---p 00061000 08:01 141841     /usr/lib/libsndfile.so.1.0.21
8efc4000-8efc5000 r-xp 00061000 08:01 141841     /usr/lib/libsndfile.so.1.0.21
8efc5000-8efc6000 rwxp 00062000 08:01 141841     /usr/lib/libsndfile.so.1.0.21
8efc6000-8efca000 rwxp 00000000 00:00 0 
8efca000-8efd1000 r-xp 00000000 08:01 133570     /lib/libwrap.so.0.7.6
8efd1000-8efd2000 r-xp 00006000 08:01 133570     /lib/libwrap.so.0.7.6
8efd2000-8efd3000 rwxp 00007000 08:01 133570     /lib/libwrap.so.0.7.6
8efd3000-8f01c000 r-xp 00000000 08:01 141782     /usr/lib/libpulsecommon-0.9.21.so
8f01c000-8f01d000 r-xp 00048000 08:01 141782     /usr/lib/libpulsecommon-0.9.21.so
8f01d000-8f01e000 rwxp 00049000 08:01 141782     /usr/lib/libpulsecommon-0.9.21.so
8f01e000-8f033000 r-xp 00000000 08:01 140928     /usr/lib/libICE.so.6.3.0
8f033000-8f034000 r-xp 00014000 08:01 140928     /usr/lib/libICE.so.6.3.0
8f034000-8f035000 rwxp 00015000 08:01 140928     /usr/lib/libICE.so.6.3.0
8f035000-8f037000 rwxp 00000000 00:00 0 
8f037000-8f077000 r-xp 00000000 08:01 141781     /usr/lib/libpulse.so.0.12.2
8f077000-8f078000 r-xp 00040000 08:01 141781     /usr/lib/libpulse.so.0.12.2
8f078000-8f079000 rwxp 00041000 08:01 141781     /usr/lib/libpulse.so.0.12.2
8f079000-8f13c000 r-xp 00000000 08:01 141043     /usr/lib/libasound.so.2.0.0
8f13c000-8f140000 r-xp 000c2000 08:01 141043     /usr/lib/libasound.so.2.0.0
8f140000-8f141000 rwxp 000c6000 08:01 141043     /usr/lib/libasound.so.2.0.0
8f143000-8f145000 r-xp 00000000 08:01 133498     /lib/libnss_mdns4_minimal.so.2
8f145000-8f146000 r-xp 00001000 08:01 133498     /lib/libnss_mdns4_minimal.so.2
8f146000-8f147000 rwxp 00002000 08:01 133498     /lib/libnss_mdns4_minimal.so.2
8f151000-8f36b000 rwxs 00000000 00:04 83099669   /SYSV00000000 (deleted)
8f36b000-8f36e000 ---p 00000000 00:00 0 
8f36e000-8f3bc000 rwxp 00000000 00:00 0 
8f3bc000-8f3bf000 ---p 00000000 00:00 0 
8f3bf000-8f40d000 rwxp 00000000 00:00 0 
8f40d000-8f410000 ---p 00000000 00:00 0 
8f410000-8f45e000 rwxp 00000000 00:00 0 
8f45e000-8f461000 ---p 00000000 00:00 0 
8f461000-8f4af000 rwxp 00000000 00:00 0 
8f4af000-8f4b2000 ---p 00000000 00:00 0 
8f4b2000-8f500000 rwxp 00000000 00:00 0 
8f500000-8f5fc000 rwxp 00000000 00:00 0 
8f5fc000-8f600000 ---p 00000000 00:00 0 
8f601000-8f602000 r-xs 00000000 08:01 404266     /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
8f602000-8f603000 r-xs 00000000 08:01 425477     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
8f603000-8f609000 r-xs 00000000 08:01 425474     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
8f609000-8f60b000 r-xs 00000000 08:01 425475     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
8f60b000-8f671000 r-xs 00000000 08:01 397055     /var/cache/fontconfig/8abd9214ecbfa594f22f45cb5742dd09-le32d4.cache-3
8f671000-8f674000 r-xs 00000000 08:01 425484     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
8f674000-8f675000 r-xs 00000000 08:01 425485     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
8f675000-8f678000 r-xs 00000000 08:01 425471     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
8f678000-8f67c000 r-xs 00000000 08:01 425476     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
8f67c000-8f683000 r-xs 00000000 08:01 408743     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
8f683000-8f68e000 r-xs 00000000 08:01 425462     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
8f68e000-8f6b0000 r-xs 00000000 08:01 406106     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
8f6b0000-8f6b8000 r-xs 00000000 08:01 425480     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
8f6bb000-8f6c2000 r-xp 00000000 08:01 140957     /usr/lib/libSM.so.6.0.1
8f6c2000-8f6c3000 r-xp 00006000 08:01 140957     /usr/lib/libSM.so.6.0.1
8f6c3000-8f6c4000 rwxp 00007000 08:01 140957     /usr/lib/libSM.so.6.0.1
8f6c4000-8f6d3000 r-xp 00000000 08:01 669933     /opt/java/32/jre1.6.0_21/lib/i386/libjsoundalsa.so
8f6d3000-8f6d4000 rwxp 0000e000 08:01 669933     /opt/java/32/jre1.6.0_21/lib/i386/libjsoundalsa.so
8f6d4000-8f702000 r-xp 00000000 08:01 669932     /opt/java/32/jre1.6.0_21/lib/i386/libjsound.so
8f702000-8f703000 rwxp 0002e000 08:01 669932     /opt/java/32/jre1.6.0_21/lib/i386/libjsound.so
8f703000-8f704000 rwxp 00000000 00:00 0 
8f704000-8f707000 ---p 00000000 00:00 0 
8f707000-8f755000 rwxp 00000000 00:00 0 
8f755000-8f758000 ---p 00000000 00:00 0 
8f758000-8f7a6000 rwxp 00000000 00:00 0 
8f7a6000-8f825000 r-xp 00000000 08:01 669950     /opt/java/32/jre1.6.0_21/lib/i386/libfontmanager.so
8f825000-8f830000 rwxp 0007e000 08:01 669950     /opt/java/32/jre1.6.0_21/lib/i386/libfontmanager.so
8f830000-8f834000 rwxp 00000000 00:00 0 
8f834000-8f94d000 r-xp 00000000 08:01 140959     /usr/lib/libX11.so.6.3.0
8f94d000-8f94e000 r-xp 00118000 08:01 140959     /usr/lib/libX11.so.6.3.0
8f94e000-8f950000 rwxp 00119000 08:01 140959     /usr/lib/libX11.so.6.3.0
8f950000-8f951000 rwxp 00000000 00:00 0 
8f951000-8f9d5000 r-xp 00000000 08:01 669941     /opt/java/32/jre1.6.0_21/lib/i386/libawt.so
8f9d5000-8f9dc000 rwxp 00084000 08:01 669941     /opt/java/32/jre1.6.0_21/lib/i386/libawt.so
8f9dc000-8fa00000 rwxp 00000000 00:00 0 
8fa00000-8faff000 rwxp 00000000 00:00 0 
8faff000-8fb00000 ---p 00000000 00:00 0 
8fb01000-8fb04000 r-xp 00000000 08:01 133568     /lib/libuuid.so.1.3.0
8fb04000-8fb05000 r-xp 00002000 08:01 133568     /lib/libuuid.so.1.3.0
8fb05000-8fb06000 rwxp 00003000 08:01 133568     /lib/libuuid.so.1.3.0
8fb09000-8fb1c000 r-xp 00000000 08:01 669926     /opt/java/32/jre1.6.0_21/lib/i386/libnet.so
8fb1c000-8fb1d000 rwxp 00013000 08:01 669926     /opt/java/32/jre1.6.0_21/lib/i386/libnet.so
8fb1d000-8fb21000 r-xp 00000000 08:01 140978     /usr/lib/libXfixes.so.3.1.0
8fb21000-8fb22000 r-xp 00003000 08:01 140978     /usr/lib/libXfixes.so.3.1.0
8fb22000-8fb23000 rwxp 00004000 08:01 140978     /usr/lib/libXfixes.so.3.1.0
8fb23000-8fb2b000 r-xp 00000000 08:01 140998     /usr/lib/libXrender.so.1.3.0
8fb2b000-8fb2c000 r-xp 00007000 08:01 140998     /usr/lib/libXrender.so.1.3.0
8fb2c000-8fb2d000 rwxp 00008000 08:01 140998     /usr/lib/libXrender.so.1.3.0
8fb2d000-8fb35000 r-xp 00000000 08:01 140970     /usr/lib/libXcursor.so.1.0.2
8fb35000-8fb36000 r-xp 00007000 08:01 140970     /usr/lib/libXcursor.so.1.0.2
8fb36000-8fb37000 rwxp 00008000 08:01 140970     /usr/lib/libXcursor.so.1.0.2
8fb37000-8fb3e000 r-xp 00000000 08:01 669927     /opt/java/32/jre1.6.0_21/lib/i386/libnio.so
8fb3e000-8fb3f000 rwxp 00006000 08:01 669927     /opt/java/32/jre1.6.0_21/lib/i386/libnio.so
8fb3f000-8fb47000 r-xs 00115000 08:01 670110     /opt/java/32/jre1.6.0_21/lib/resources.jar
8fb47000-8fb4b000 r-xp 00000000 08:01 140974     /usr/lib/libXdmcp.so.6.0.0
8fb4b000-8fb4c000 r-xp 00003000 08:01 140974     /usr/lib/libXdmcp.so.6.0.0
8fb4c000-8fb4d000 rwxp 00004000 08:01 140974     /usr/lib/libXdmcp.so.6.0.0
8fb4d000-8fb65000 r-xp 00000000 08:01 141970     /usr/lib/libxcb.so.1.1.0
8fb65000-8fb66000 r-xp 00017000 08:01 141970     /usr/lib/libxcb.so.1.1.0
8fb66000-8fb67000 rwxp 00018000 08:01 141970     /usr/lib/libxcb.so.1.1.0
8fb67000-8fbaa000 r-xp 00000000 08:01 669944     /opt/java/32/jre1.6.0_21/lib/i386/xawt/libmawt.so
8fbaa000-8fbac000 rwxp 00043000 08:01 669944     /opt/java/32/jre1.6.0_21/lib/i386/xawt/libmawt.so
8fbac000-8fbad000 rwxp 00000000 00:00 0 
8fbad000-8fbae000 ---p 00000000 00:00 0 
8fbae000-8fc2e000 rwxp 00000000 00:00 0 
8fc2e000-8fc31000 ---p 00000000 00:00 0 
8fc31000-8fc7f000 rwxp 00000000 00:00 0 
8fc7f000-8fc82000 ---p 00000000 00:00 0 
8fc82000-8fd00000 rwxp 00000000 00:00 0 
8fd00000-8fdfc000 rwxp 00000000 00:00 0 
8fdfc000-8fe00000 ---p 00000000 00:00 0 
8fe00000-8fe02000 r-xp 00000000 08:01 140963     /usr/lib/libXau.so.6.0.0
8fe02000-8fe03000 r-xp 00001000 08:01 140963     /usr/lib/libXau.so.6.0.0
8fe03000-8fe04000 rwxp 00002000 08:01 140963     /usr/lib/libXau.so.6.0.0
8fe04000-8fe10000 r-xp 00000000 08:01 140984     /usr/lib/libXi.so.6.1.0
8fe10000-8fe11000 r-xp 0000c000 08:01 140984     /usr/lib/libXi.so.6.1.0
8fe11000-8fe12000 rwxp 0000d000 08:01 140984     /usr/lib/libXi.so.6.1.0
8fe12000-8fe16000 r-xp 00000000 08:01 141004     /usr/lib/libXtst.so.6.1.0
8fe16000-8fe17000 r-xp 00003000 08:01 141004     /usr/lib/libXtst.so.6.1.0
8fe17000-8fe18000 rwxp 00004000 08:01 141004     /usr/lib/libXtst.so.6.1.0
8fe18000-8fe26000 r-xp 00000000 08:01 140976     /usr/lib/libXext.so.6.4.0
8fe26000-8fe27000 r-xp 0000d000 08:01 140976     /usr/lib/libXext.so.6.4.0
8fe27000-8fe28000 rwxp 0000e000 08:01 140976     /usr/lib/libXext.so.6.4.0
8fe2a000-8fe2d000 r-xs 00000000 08:01 425481     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
8fe2d000-8fe35000 r-xs 00000000 08:01 407789     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
8fe35000-8fe38000 r-xs 00000000 08:01 402964     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
8fe38000-8fe3d000 r-xs 00081000 08:01 671491     /home/vapourstreak/Downloads/MoparScape/MoparScape.jar
8fe3d000-8fe40000 ---p 00000000 00:00 0 
8fe40000-8febe000 rwxp 00000000 00:00 0 
8febe000-8fec1000 ---p 00000000 00:00 0 
8fec1000-8ff0f000 rwxp 00000000 00:00 0 
8ff0f000-8ff4e000 r-xp 00000000 08:01 146042     /usr/lib/locale/en_CA.utf8/LC_CTYPE
8ff4e000-8ff51000 ---p 00000000 00:00 0 
8ff51000-8ff9f000 rwxp 00000000 00:00 0 
8ff9f000-8ffa2000 ---p 00000000 00:00 0 
8ffa2000-8fff0000 rwxp 00000000 00:00 0 
8fff0000-8fff1000 ---p 00000000 00:00 0 
8fff1000-900a5000 rwxp 00000000 00:00 0 
900a5000-9023c000 r-xs 02b02000 08:01 669810     /opt/java/32/jre1.6.0_21/lib/rt.jar
9023c000-9023d000 ---p 00000000 00:00 0 
9023d000-902bd000 rwxp 00000000 00:00 0 
902bd000-902be000 ---p 00000000 00:00 0 
902be000-90349000 rwxp 00000000 00:00 0 
90349000-9034b000 ---p 00000000 00:00 0 
9034b000-9035e000 rwxp 00000000 00:00 0 
9035e000-9038d000 rwxp 00000000 00:00 0 
9038d000-90405000 rwxp 00000000 00:00 0 
90405000-90410000 rwxp 00000000 00:00 0 
90410000-90412000 ---p 00000000 00:00 0 
90412000-90425000 rwxp 00000000 00:00 0 
90425000-90454000 rwxp 00000000 00:00 0 
90454000-904cb000 rwxp 00000000 00:00 0 
904cb000-904ed000 rwxp 00000000 00:00 0 
904ed000-904ee000 ---p 00000000 00:00 0 
904ee000-9051f000 rwxp 00000000 00:00 0 
9051f000-91a60000 rwxp 00000000 00:00 0 
91a60000-91de0000 ---p 00000000 00:00 0 
91de0000-94520000 rwxp 00000000 00:00 0 
94520000-9a280000 rwxp 00000000 00:00 0 
9a280000-a9280000 rwxp 00000000 00:00 0 
a9280000-ad3a0000 rwxp 00000000 00:00 0 
ad3a0000-ad580000 ---p 00000000 00:00 0 
ad580000-b3920000 rwxp 00000000 00:00 0 
b3922000-b392c000 rwxp 00000000 00:00 0 
b392c000-b39e2000 rwxp 00000000 00:00 0 
b39e2000-b3c52000 rwxp 00000000 00:00 0 
b3c52000-b69e2000 rwxp 00000000 00:00 0 
b69e2000-b69f1000 r-xp 00000000 08:01 669921     /opt/java/32/jre1.6.0_21/lib/i386/libzip.so
b69f1000-b69f3000 rwxp 0000e000 08:01 669921     /opt/java/32/jre1.6.0_21/lib/i386/libzip.so
b69f3000-b69fd000 r-xp 00000000 08:01 133490     /lib/tls/i686/cmov/libnss_files-2.11.1.so
b69fd000-b69fe000 r-xp 00009000 08:01 133490     /lib/tls/i686/cmov/libnss_files-2.11.1.so
b69fe000-b69ff000 rwxp 0000a000 08:01 133490     /lib/tls/i686/cmov/libnss_files-2.11.1.so
b69ff000-b6a07000 r-xp 00000000 08:01 133494     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b6a07000-b6a08000 r-xp 00007000 08:01 133494     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b6a08000-b6a09000 rwxp 00008000 08:01 133494     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b6a09000-b6a0a000 r-xs 00000000 08:01 425467     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b6a0a000-b6a11000 r-xs 00000000 08:01 137498     /usr/lib/gconv/gconv-modules.cache
b6a11000-b6a19000 rwxs 00000000 08:01 393567     /tmp/hsperfdata_vapourstreak/14720
b6a19000-b6a2c000 r-xp 00000000 08:01 133477     /lib/tls/i686/cmov/libnsl-2.11.1.so
b6a2c000-b6a2d000 r-xp 00012000 08:01 133477     /lib/tls/i686/cmov/libnsl-2.11.1.so
b6a2d000-b6a2e000 rwxp 00013000 08:01 133477     /lib/tls/i686/cmov/libnsl-2.11.1.so
b6a2e000-b6a30000 rwxp 00000000 00:00 0 
b6a30000-b6a31000 r-xs 00000000 08:01 425461     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b6a31000-b6a37000 r-xp 00000000 08:01 133486     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b6a37000-b6a38000 r-xp 00006000 08:01 133486     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b6a38000-b6a39000 rwxp 00007000 08:01 133486     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b6a39000-b6a3f000 r-xp 00000000 08:01 669891     /opt/java/32/jre1.6.0_21/lib/i386/native_threads/libhpi.so
b6a3f000-b6a40000 rwxp 00006000 08:01 669891     /opt/java/32/jre1.6.0_21/lib/i386/native_threads/libhpi.so
b6a40000-b6a63000 r-xp 00000000 08:01 669914     /opt/java/32/jre1.6.0_21/lib/i386/libjava.so
b6a63000-b6a65000 rwxp 00023000 08:01 669914     /opt/java/32/jre1.6.0_21/lib/i386/libjava.so
b6a65000-b6a6c000 r-xp 00000000 08:01 133538     /lib/tls/i686/cmov/librt-2.11.1.so
b6a6c000-b6a6d000 r-xp 00006000 08:01 133538     /lib/tls/i686/cmov/librt-2.11.1.so
b6a6d000-b6a6e000 rwxp 00007000 08:01 133538     /lib/tls/i686/cmov/librt-2.11.1.so
b6a6e000-b6a71000 ---p 00000000 00:00 0 
b6a71000-b6abf000 rwxp 00000000 00:00 0 
b6abf000-b6ae3000 r-xp 00000000 08:01 133440     /lib/tls/i686/cmov/libm-2.11.1.so
b6ae3000-b6ae4000 r-xp 00023000 08:01 133440     /lib/tls/i686/cmov/libm-2.11.1.so
b6ae4000-b6ae5000 rwxp 00024000 08:01 133440     /lib/tls/i686/cmov/libm-2.11.1.so
b6ae5000-b7211000 r-xp 00000000 08:01 669896     /opt/java/32/jre1.6.0_21/lib/i386/server/libjvm.so
b7211000-b7264000 rwxp 0072c000 08:01 669896     /opt/java/32/jre1.6.0_21/lib/i386/server/libjvm.so
b7264000-b7684000 rwxp 00000000 00:00 0 
b7684000-b77d7000 r-xp 00000000 08:01 133409     /lib/tls/i686/cmov/libc-2.11.1.so
b77d7000-b77d8000 ---p 00153000 08:01 133409     /lib/tls/i686/cmov/libc-2.11.1.so
b77d8000-b77da000 r-xp 00153000 08:01 133409     /lib/tls/i686/cmov/libc-2.11.1.so
b77da000-b77db000 rwxp 00155000 08:01 133409     /lib/tls/i686/cmov/libc-2.11.1.so
b77db000-b77de000 rwxp 00000000 00:00 0 
b77de000-b77e0000 r-xp 00000000 08:01 133434     /lib/tls/i686/cmov/libdl-2.11.1.so
b77e0000-b77e1000 r-xp 00001000 08:01 133434     /lib/tls/i686/cmov/libdl-2.11.1.so
b77e1000-b77e2000 rwxp 00002000 08:01 133434     /lib/tls/i686/cmov/libdl-2.11.1.so
b77e2000-b77e9000 r-xp 00000000 08:01 669916     /opt/java/32/jre1.6.0_21/lib/i386/jli/libjli.so
b77e9000-b77eb000 rwxp 00006000 08:01 669916     /opt/java/32/jre1.6.0_21/lib/i386/jli/libjli.so
b77eb000-b77ec000 rwxp 00000000 00:00 0 
b77ec000-b7801000 r-xp 00000000 08:01 133516     /lib/tls/i686/cmov/libpthread-2.11.1.so
b7801000-b7802000 r-xp 00014000 08:01 133516     /lib/tls/i686/cmov/libpthread-2.11.1.so
b7802000-b7803000 rwxp 00015000 08:01 133516     /lib/tls/i686/cmov/libpthread-2.11.1.so
b7803000-b7805000 rwxp 00000000 00:00 0 
b7805000-b7806000 r-xs 00000000 08:01 425469     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b7806000-b7807000 r-xs 00000000 08:01 401073     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b7807000-b7808000 rwxp 00000000 00:00 0 
b7808000-b7809000 r-xp 00000000 00:00 0 
b7809000-b7814000 r-xp 00000000 08:01 669913     /opt/java/32/jre1.6.0_21/lib/i386/libverify.so
b7814000-b7815000 rwxp 0000b000 08:01 669913     /opt/java/32/jre1.6.0_21/lib/i386/libverify.so
b7815000-b7817000 rwxp 00000000 00:00 0 
b7817000-b7818000 r-xp 00000000 00:00 0          [vdso]
b7818000-b7833000 r-xp 00000000 08:01 131252     /lib/ld-2.11.1.so
b7833000-b7834000 r-xp 0001a000 08:01 131252     /lib/ld-2.11.1.so
b7834000-b7835000 rwxp 0001b000 08:01 131252     /lib/ld-2.11.1.so
bfee8000-bfefd000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xverify:none -Xmx500m 
java_command: Bot 0
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=vapourstreak
LD_LIBRARY_PATH=/opt/java/32/jre1.6.0_21/lib/i386/server:/opt/java/32/jre1.6.0_21/lib/i386:/opt/java/32/jre1.6.0_21/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x6a9eb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x6a9eb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x578180], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x578180], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x578180], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x578180], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x57adc0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x57aaf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x57aaf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x57aaf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x57aaf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:2.89 4.48 3.71

CPU:total 2 (2 cores per cpu, 1 threads per core) family 16 model 6 stepping 2, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext, 3dnow, 3dnowext, lzcnt

Memory: 4k page, physical 2966248k(86548k free), swap 701432k(701432k free)

vm_info: Java HotSpot(TM) Server VM (17.0-b16) for linux-x86 JRE (1.6.0_21-b06), built on Jun 22 2010 01:04:46 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Thu Aug 19 21:06:17 2010
elapsed time: 33 seconds


---

### Post by Vapourstreak on 2010-08-20
No help?

---

### Post by Vapourstreak on 2010-08-20
Is this wrong forum or something.

---

### Post by lykeion on 2010-08-20
The reason why you don't get any answers here may be that moparscape is illegal, at least according to this:

[http://www.runescape-blog.com/runescape-guides/moparscape-servers.html](http://www.runescape-blog.com/runescape-guides/moparscape-servers.html)

You should try your luck at the moparscape forum

[http://www.moparscape.org/smf/](http://www.moparscape.org/smf/)

---

