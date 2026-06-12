---
title: "Odd java crash on 9.10 Karmic"
date: 2009-11-24
forum: General Help
---

### Post by mrdek11 on 2009-11-24
Hi there!

I'm not entirely sure whether this problem has to do with ubuntu or java, so I apologize if this not the place to ask for help. I'm trying to run a java app, which works fine in Windows and OS X, and it works for a while in Ubuntu, but will then crash and spit out: 

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
# *SIGSEGV (0xb) at pc=0xb6d1d34d, pid=16528, tid=2415463280
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) Server VM (14.1-b02 mixed mode linux-x86 )
# Problematic frame:
# V *[libjvm.so+0x11934d]
#
# An error report file with more information is saved as:
# /home/anthony/Desktop/client/hs_err_pid16528.log
#
# If you would like to submit a bug report, please visit:
# **http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted
```

hs_err_pid16528.log contains:
```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb6d1d34d, pid=16528, tid=2415463280
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) Server VM (14.1-b02 mixed mode linux-x86 )
# Problematic frame:
# V  [libjvm.so+0x11934d]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x0996bc00):  JavaThread "CompilerThread0" daemon [_thread_in_native, id=16536, stack(0x8ff10000,0x8ff91000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000000

Registers:
EAX=0x09fcf3a4, EBX=0xb731a720, ECX=0x8f268720, EDX=0x00000000
ESP=0x8ff8df04, EBP=0x8ff8df48, ESI=0x8ff8f180, EDI=0x8f268720
EIP=0xb6d1d34d, CR2=0x00000000, EFLAGS=0x00210292

Top of Stack: (sp=0x8ff8df04)
0x8ff8df04:   8ff8f180 00000007 b731a720 8ff8f960
0x8ff8df14:   8ff8f180 8ff8df48 b7164ab2 8f268720
0x8ff8df24:   8ff8df88 00000001 00000001 09fcf3a4
0x8ff8df34:   00000000 0100f3b3 b731a720 8ff8f180
0x8ff8df44:   8f268720 8ff8df98 b7166d2c 8f268720
0x8ff8df54:   8ff8f180 00000001 8f1c3744 09fd12cc
0x8ff8df64:   09fd12cc 8f268720 8f1c253c 09fcd424
0x8ff8df74:   0000195a 09975a90 8f1c32fc 00000003 

Instructions: (pc=0xb6d1d34d)
0xb6d1d33d:   e6 d3 5f 00 8b 50 04 89 55 ec 8b 40 08 89 45 e8
0xb6d1d34d:   8b 02 52 ff 10 8b 55 e8 89 c7 8b 02 89 14 24 ff 

Stack: [0x8ff10000,0x8ff91000],  sp=0x8ff8df04,  free space=503k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x11934d]
V  [libjvm.so+0x562d2c]
V  [libjvm.so+0x562990]
V  [libjvm.so+0x4c6fd5]
V  [libjvm.so+0x25b75f]
V  [libjvm.so+0x2585df]
V  [libjvm.so+0x1f2c2f]
V  [libjvm.so+0x260ceb]
V  [libjvm.so+0x260609]
V  [libjvm.so+0x617286]
V  [libjvm.so+0x6108fe]
V  [libjvm.so+0x531c4e]
C  [libpthread.so.0+0x580e]


Current CompileTask:
C2:347      client.a(IIIIIIIIIIZI)Z (1957 bytes)


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x09ae0c00 JavaThread "Thread-7" [_thread_blocked, id=16553, stack(0x8fa80000,0x8fad1000)]
  0x0a486400 JavaThread "Thread-6" [_thread_blocked, id=16552, stack(0x8f45e000,0x8f4af000)]
  0x0a4b8000 JavaThread "Thread-5" [_thread_blocked, id=16550, stack(0x8f63c000,0x8f68d000)]
  0x8f77d800 JavaThread "DestroyJavaVM" [_thread_blocked, id=16529, stack(0xb6b8d000,0xb6bde000)]
  0x8f77c800 JavaThread "Thread-3" [_thread_in_Java, id=16546, stack(0x8f6af000,0x8f700000)]
  0x8f779400 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=16545, stack(0x8f810000,0x8f861000)]
  0x8f773400 JavaThread "AWT-Shutdown" [_thread_blocked, id=16544, stack(0x8f8d5000,0x8f926000)]
  0x8f76b000 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=16543, stack(0x8f926000,0x8f977000)]
  0x09afc800 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=16542, stack(0x8f9a1000,0x8f9f2000)]
  0x09ad2800 JavaThread "Thread-1" daemon [_thread_blocked, id=16540, stack(0x8faec000,0x8fb3d000)]
  0x09970800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=16538, stack(0x8fe3e000,0x8fe8f000)]
  0x0996e800 JavaThread "CompilerThread1" daemon [_thread_blocked, id=16537, stack(0x8fe8f000,0x8ff10000)]
=>0x0996bc00 JavaThread "CompilerThread0" daemon [_thread_in_native, id=16536, stack(0x8ff10000,0x8ff91000)]
  0x0996a400 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=16535, stack(0x8ff91000,0x8ffe2000)]
  0x09956800 JavaThread "Finalizer" daemon [_thread_blocked, id=16534, stack(0x90028000,0x90079000)]
  0x09955400 JavaThread "Reference Handler" daemon [_thread_blocked, id=16533, stack(0x90079000,0x900ca000)]

Other Threads:
  0x09951400 VMThread [stack: 0x900ca000,0x9014b000] [id=16532]
  0x09972400 WatcherThread [stack: 0x8fdbd000,0x8fe3e000] [id=16539]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 32960K, used 18367K [0xb02b0000, 0xb3830000, 0xb3a30000)
  eden space 25472K, 72% used [0xb02b0000,0xb149fdb8,0xb1b90000)
  from space 7488K, 0% used [0xb1b90000,0xb1b90000,0xb22e0000)
  to   space 14656K, 0% used [0xb29e0000,0xb29e0000,0xb3830000)
 PSOldGen        total 89728K, used 67996K [0x94630000, 0x99dd0000, 0xb02b0000)
  object space 89728K, 75% used [0x94630000,0x98897270,0x99dd0000)
 PSPermGen       total 16384K, used 8383K [0x90630000, 0x91630000, 0x94630000)
  object space 16384K, 51% used [0x90630000,0x90e5ff30,0x91630000)

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:06 402616     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/bin/java
08052000-08053000 rwxp 00009000 08:06 402616     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/bin/java
098cf000-0ab0f000 rwxp 00000000 00:00 0          [heap]
8db00000-8dbfa000 rwxp 00000000 00:00 0 
8dbfa000-8dc00000 ---p 00000000 00:00 0 
8dc00000-8dced000 rwxp 00000000 00:00 0 
8dced000-8dd00000 ---p 00000000 00:00 0 
8dd00000-8ddf9000 rwxp 00000000 00:00 0 
8ddf9000-8de00000 ---p 00000000 00:00 0 
8de00000-8deee000 rwxp 00000000 00:00 0 
8deee000-8df00000 ---p 00000000 00:00 0 
8df00000-8dffa000 rwxp 00000000 00:00 0 
8dffa000-8e000000 ---p 00000000 00:00 0 
8e000000-8e0e1000 rwxp 00000000 00:00 0 
8e0e1000-8e100000 ---p 00000000 00:00 0 
8e100000-8e1f9000 rwxp 00000000 00:00 0 
8e1f9000-8e200000 ---p 00000000 00:00 0 
8e200000-8e2e7000 rwxp 00000000 00:00 0 
8e2e7000-8e300000 ---p 00000000 00:00 0 
8e300000-8e3f4000 rwxp 00000000 00:00 0 
8e3f4000-8e400000 ---p 00000000 00:00 0 
8e500000-8e5f4000 rwxp 00000000 00:00 0 
8e5f4000-8e600000 ---p 00000000 00:00 0 
8e600000-8e6fd000 rwxp 00000000 00:00 0 
8e6fd000-8e700000 ---p 00000000 00:00 0 
8e700000-8e7fc000 rwxp 00000000 00:00 0 
8e7fc000-8e800000 ---p 00000000 00:00 0 
8e800000-8e8e4000 rwxp 00000000 00:00 0 
8e8e4000-8e900000 ---p 00000000 00:00 0 
8e900000-8e9f9000 rwxp 00000000 00:00 0 
8e9f9000-8ea00000 ---p 00000000 00:00 0 
8eb00000-8ebfe000 rwxp 00000000 00:00 0 
8ebfe000-8ec00000 ---p 00000000 00:00 0 
8ec00000-8ecfc000 rwxp 00000000 00:00 0 
8ecfc000-8ed00000 ---p 00000000 00:00 0 
8ed00000-8edd1000 rwxp 00000000 00:00 0 
8edd1000-8ee00000 ---p 00000000 00:00 0 
8ee00000-8eeef000 rwxp 00000000 00:00 0 
8eeef000-8ef00000 ---p 00000000 00:00 0 
8f000000-8f0f4000 rwxp 00000000 00:00 0 
8f0f4000-8f100000 ---p 00000000 00:00 0 
8f100000-8f1fd000 rwxp 00000000 00:00 0 
8f1fd000-8f200000 ---p 00000000 00:00 0 
8f200000-8f2f6000 rwxp 00000000 00:00 0 
8f2f6000-8f300000 ---p 00000000 00:00 0 
8f355000-8f358000 rwxp 00000000 00:00 0 
8f358000-8f3a6000 rwxp 00000000 00:00 0 
8f3b7000-8f45e000 rwxs 00000000 00:09 780894230  /SYSV00000000 (deleted)
8f45e000-8f461000 ---p 00000000 00:00 0 
8f461000-8f4af000 rwxp 00000000 00:00 0 
8f4af000-8f4b2000 rwxp 00000000 00:00 0 
8f4b2000-8f500000 rwxp 00000000 00:00 0 
8f500000-8f5fa000 rwxp 00000000 00:00 0 
8f5fa000-8f600000 ---p 00000000 00:00 0 
8f63c000-8f63f000 ---p 00000000 00:00 0 
8f63f000-8f68d000 rwxp 00000000 00:00 0 
8f6af000-8f6b2000 ---p 00000000 00:00 0 
8f6b2000-8f700000 rwxp 00000000 00:00 0 
8f700000-8f7fc000 rwxp 00000000 00:00 0 
8f7fc000-8f800000 ---p 00000000 00:00 0 
8f810000-8f813000 ---p 00000000 00:00 0 
8f813000-8f861000 rwxp 00000000 00:00 0 
8f861000-8f862000 r-xs 00000000 08:06 340201     /var/cache/fontconfig/48fef66b76e7de9c5c56a6dcc7723c04-x86.cache-2
8f862000-8f863000 r-xs 00000000 08:06 340200     /var/cache/fontconfig/cb7d13eeb0521c8bf38f4717320dc78b-x86.cache-2
8f863000-8f864000 r-xs 00000000 08:06 340198     /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-x86.cache-2
8f864000-8f865000 r-xs 00000000 08:06 359196     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-x86.cache-2
8f865000-8f86b000 r-xs 00000000 08:06 359193     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
8f86b000-8f86d000 r-xs 00000000 08:06 359194     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-x86.cache-2
8f86d000-8f86f000 r-xs 00000000 08:06 359204     /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-x86.cache-2
8f86f000-8f872000 r-xs 00000000 08:06 359202     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
8f872000-8f875000 r-xs 00000000 08:06 340194     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
8f875000-8f876000 r-xs 00000000 08:06 359188     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
8f876000-8f87a000 r-xs 00000000 08:06 359181     /var/cache/fontconfig/062808c12e6e608270f93bb230aed730-x86.cache-2
8f87a000-8f87d000 r-xs 00000000 08:06 359195     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
8f87d000-8f880000 r-xs 00000000 08:06 359190     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
8f880000-8f88b000 r-xs 00000000 08:06 359182     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
8f88b000-8f88c000 r-xs 00000000 08:06 359186     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
8f88c000-8f8ae000 r-xs 00000000 08:06 340273     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
8f8ae000-8f8b0000 r-xs 00000000 08:06 359184     /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2
8f8b0000-8f8b8000 r-xs 00000000 08:06 359199     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
8f8d5000-8f8d8000 ---p 00000000 00:00 0 
8f8d8000-8f926000 rwxp 00000000 00:00 0 
8f926000-8f929000 ---p 00000000 00:00 0 
8f929000-8f977000 rwxp 00000000 00:00 0 
8f977000-8f97b000 r-xp 00000000 08:06 263736     /usr/lib/libXfixes.so.3.1.0
8f97b000-8f97c000 r-xp 00003000 08:06 263736     /usr/lib/libXfixes.so.3.1.0
8f97c000-8f97d000 rwxp 00004000 08:06 263736     /usr/lib/libXfixes.so.3.1.0
8f97d000-8f985000 r-xp 00000000 08:06 263756     /usr/lib/libXrender.so.1.3.0
8f985000-8f986000 r-xp 00007000 08:06 263756     /usr/lib/libXrender.so.1.3.0
8f986000-8f987000 rwxp 00008000 08:06 263756     /usr/lib/libXrender.so.1.3.0
8f987000-8f990000 r-xp 00000000 08:06 263728     /usr/lib/libXcursor.so.1.0.2
8f990000-8f991000 r-xp 00008000 08:06 263728     /usr/lib/libXcursor.so.1.0.2
8f991000-8f992000 rwxp 00009000 08:06 263728     /usr/lib/libXcursor.so.1.0.2
8f999000-8f9a0000 r-xp 00000000 08:06 402648     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnio.so
8f9a0000-8f9a1000 rwxp 00006000 08:06 402648     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnio.so
8f9a1000-8f9a4000 ---p 00000000 00:00 0 
8f9a4000-8f9f2000 rwxp 00000000 00:00 0 
8f9f2000-8fa71000 r-xp 00000000 08:06 402663     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libfontmanager.so
8fa71000-8fa7c000 rwxp 0007e000 08:06 402663     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libfontmanager.so
8fa7c000-8fa80000 rwxp 00000000 00:00 0 
8fa80000-8fa83000 ---p 00000000 00:00 0 
8fa83000-8fad1000 rwxp 00000000 00:00 0 
8fad1000-8fae1000 r-xp 00000000 08:06 131709     /lib/tls/i686/cmov/libresolv-2.10.1.so
8fae1000-8fae2000 r-xp 00010000 08:06 131709     /lib/tls/i686/cmov/libresolv-2.10.1.so
8fae2000-8fae3000 rwxp 00011000 08:06 131709     /lib/tls/i686/cmov/libresolv-2.10.1.so
8fae3000-8fae5000 rwxp 00000000 00:00 0 
8fae5000-8faea000 r-xp 00000000 08:06 131696     /lib/tls/i686/cmov/libnss_dns-2.10.1.so
8faea000-8faeb000 r-xp 00004000 08:06 131696     /lib/tls/i686/cmov/libnss_dns-2.10.1.so
8faeb000-8faec000 rwxp 00005000 08:06 131696     /lib/tls/i686/cmov/libnss_dns-2.10.1.so
8faec000-8faef000 ---p 00000000 00:00 0 
8faef000-8fb3d000 rwxp 00000000 00:00 0 
8fb3d000-8fb50000 r-xp 00000000 08:06 402647     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnet.so
8fb50000-8fb51000 rwxp 00013000 08:06 402647     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnet.so
8fb51000-8fb6d000 r-xp 00000000 08:06 264753     /usr/lib/libxcb.so.1.1.0
8fb6d000-8fb6e000 r-xp 0001c000 08:06 264753     /usr/lib/libxcb.so.1.1.0
8fb6e000-8fb6f000 rwxp 0001d000 08:06 264753     /usr/lib/libxcb.so.1.1.0
8fb6f000-8fb78000 r-xp 00000000 08:06 263742     /usr/lib/libXi.so.6.0.0
8fb78000-8fb79000 r-xp 00008000 08:06 263742     /usr/lib/libXi.so.6.0.0
8fb79000-8fb7a000 rwxp 00009000 08:06 263742     /usr/lib/libXi.so.6.0.0
8fb7a000-8fca4000 r-xp 00000000 08:06 263715     /usr/lib/libX11.so.6.2.0
8fca4000-8fca5000 ---p 0012a000 08:06 263715     /usr/lib/libX11.so.6.2.0
8fca5000-8fca6000 r-xp 0012a000 08:06 263715     /usr/lib/libX11.so.6.2.0
8fca6000-8fca8000 rwxp 0012b000 08:06 263715     /usr/lib/libX11.so.6.2.0
8fca8000-8fca9000 rwxp 00000000 00:00 0 
8fca9000-8fcb7000 r-xp 00000000 08:06 263734     /usr/lib/libXext.so.6.4.0
8fcb7000-8fcb8000 r-xp 0000d000 08:06 263734     /usr/lib/libXext.so.6.4.0
8fcb8000-8fcb9000 rwxp 0000e000 08:06 263734     /usr/lib/libXext.so.6.4.0
8fcbe000-8fcc6000 r-xs 00000000 08:06 340195     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
8fcc6000-8fcc8000 r-xs 00000000 08:06 340272     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
8fcc8000-8fd0b000 r-xp 00000000 08:06 402660     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/xawt/libmawt.so
8fd0b000-8fd0d000 rwxp 00043000 08:06 402660     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/xawt/libmawt.so
8fd0d000-8fd0e000 rwxp 00000000 00:00 0 
8fd0e000-8fd92000 r-xp 00000000 08:06 402658     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libawt.so
8fd92000-8fd99000 rwxp 00084000 08:06 402658     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libawt.so
8fd99000-8fdbd000 rwxp 00000000 00:00 0 
8fdbd000-8fdbe000 ---p 00000000 00:00 0 
8fdbe000-8fe3e000 rwxp 00000000 00:00 0 
8fe3e000-8fe41000 ---p 00000000 00:00 0 
8fe41000-8fe8f000 rwxp 00000000 00:00 0 
8fe8f000-8fe92000 ---p 00000000 00:00 0 
8fe92000-8ff10000 rwxp 00000000 00:00 0 
8ff10000-8ff13000 ---p 00000000 00:00 0 
8ff13000-8ff91000 rwxp 00000000 00:00 0 
8ff91000-8ff94000 ---p 00000000 00:00 0 
8ff94000-8ffe2000 rwxp 00000000 00:00 0 
8ffe2000-8ffe9000 r-xs 00000000 08:06 265795     /usr/lib/gconv/gconv-modules.cache
8ffe9000-90028000 r-xp 00000000 08:06 657124     /usr/lib/locale/en_US.utf8/LC_CTYPE
90028000-9002b000 ---p 00000000 00:00 0 
9002b000-90079000 rwxp 00000000 00:00 0 
90079000-9007c000 ---p 00000000 00:00 0 
9007c000-900ca000 rwxp 00000000 00:00 0 
900ca000-900cb000 ---p 00000000 00:00 0 
900cb000-9017e000 rwxp 00000000 00:00 0 
9017e000-90314000 r-xs 02fb3000 08:06 402791     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/rt.jar
90314000-90315000 ---p 00000000 00:00 0 
90315000-90395000 rwxp 00000000 00:00 0 
90395000-90396000 ---p 00000000 00:00 0 
90396000-9041e000 rwxp 00000000 00:00 0 
9041e000-90436000 rwxp 00000000 00:00 0 
90436000-90462000 rwxp 00000000 00:00 0 
90462000-90515000 rwxp 00000000 00:00 0 
90515000-9051d000 rwxp 00000000 00:00 0 
9051d000-90535000 rwxp 00000000 00:00 0 
90535000-90561000 rwxp 00000000 00:00 0 
90561000-90613000 rwxp 00000000 00:00 0 
90613000-9062e000 rwxp 00000000 00:00 0 
9062e000-9062f000 rwxp 00000000 00:00 0 
9062f000-91630000 rwxp 00000000 00:00 0 
91630000-94630000 rwxp 00000000 00:00 0 
94630000-99dd0000 rwxp 00000000 00:00 0 
99dd0000-b02b0000 rwxp 00000000 00:00 0 
b02b0000-b3830000 rwxp 00000000 00:00 0 
b3830000-b3a30000 rwxp 00000000 00:00 0 
b3a31000-b3a33000 r-xp 00000000 08:06 606        /lib/libnss_mdns4_minimal.so.2
b3a33000-b3a34000 r-xp 00001000 08:06 606        /lib/libnss_mdns4_minimal.so.2
b3a34000-b3a35000 rwxp 00002000 08:06 606        /lib/libnss_mdns4_minimal.so.2
b3a35000-b3a39000 r-xp 00000000 08:06 263732     /usr/lib/libXdmcp.so.6.0.0
b3a39000-b3a3a000 rwxp 00003000 08:06 263732     /usr/lib/libXdmcp.so.6.0.0
b3a3a000-b3a44000 rwxp 00000000 00:00 0 
b3a44000-b3afa000 rwxp 00000000 00:00 0 
b3afa000-b3d6a000 rwxp 00000000 00:00 0 
b3d6a000-b6afa000 rwxp 00000000 00:00 0 
b6afa000-b6b09000 r-xp 00000000 08:06 402643     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libzip.so
b6b09000-b6b0b000 rwxp 0000e000 08:06 402643     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libzip.so
b6b0b000-b6b15000 r-xp 00000000 08:06 131698     /lib/tls/i686/cmov/libnss_files-2.10.1.so
b6b15000-b6b16000 r-xp 00009000 08:06 131698     /lib/tls/i686/cmov/libnss_files-2.10.1.so
b6b16000-b6b17000 rwxp 0000a000 08:06 131698     /lib/tls/i686/cmov/libnss_files-2.10.1.so
b6b17000-b6b20000 r-xp 00000000 08:06 131702     /lib/tls/i686/cmov/libnss_nis-2.10.1.so
b6b20000-b6b21000 r-xp 00008000 08:06 131702     /lib/tls/i686/cmov/libnss_nis-2.10.1.so
b6b21000-b6b22000 rwxp 00009000 08:06 131702     /lib/tls/i686/cmov/libnss_nis-2.10.1.so
b6b22000-b6b28000 r-xp 00000000 08:06 131694     /lib/tls/i686/cmov/libnss_compat-2.10.1.so
b6b28000-b6b29000 r-xp 00005000 08:06 131694     /lib/tls/i686/cmov/libnss_compat-2.10.1.so
b6b29000-b6b2a000 rwxp 00006000 08:06 131694     /lib/tls/i686/cmov/libnss_compat-2.10.1.so
b6b2b000-b6b2f000 r-xp 00000000 08:06 263762     /usr/lib/libXtst.so.6.1.0
b6b2f000-b6b30000 r-xp 00004000 08:06 263762     /usr/lib/libXtst.so.6.1.0
b6b30000-b6b31000 rwxp 00005000 08:06 263762     /usr/lib/libXtst.so.6.1.0
b6b31000-b6b39000 rwxs 00000000 08:06 3068       /tmp/hsperfdata_anthony/16528
b6b39000-b6b4c000 r-xp 00000000 08:06 131692     /lib/tls/i686/cmov/libnsl-2.10.1.so
b6b4c000-b6b4d000 r-xp 00012000 08:06 131692     /lib/tls/i686/cmov/libnsl-2.10.1.so
b6b4d000-b6b4e000 rwxp 00013000 08:06 131692     /lib/tls/i686/cmov/libnsl-2.10.1.so
b6b4e000-b6b50000 rwxp 00000000 00:00 0 
b6b50000-b6b52000 r-xp 00000000 08:06 263721     /usr/lib/libXau.so.6.0.0
b6b52000-b6b53000 r-xp 00001000 08:06 263721     /usr/lib/libXau.so.6.0.0
b6b53000-b6b54000 rwxp 00002000 08:06 263721     /usr/lib/libXau.so.6.0.0
b6b54000-b6b56000 r-xs 00051000 08:06 336962     /home/anthony/Desktop/client/client.jar
b6b56000-b6b5c000 r-xp 00000000 08:06 402631     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/native_threads/libhpi.so
b6b5c000-b6b5d000 rwxp 00006000 08:06 402631     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/native_threads/libhpi.so
b6b5d000-b6b5e000 rwxp 00000000 00:00 0 
b6b5e000-b6b5f000 r-xp 00000000 00:00 0 
b6b5f000-b6b82000 r-xp 00000000 08:06 402641     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libjava.so
b6b82000-b6b84000 rwxp 00023000 08:06 402641     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libjava.so
b6b84000-b6b8b000 r-xp 00000000 08:06 131711     /lib/tls/i686/cmov/librt-2.10.1.so
b6b8b000-b6b8c000 r-xp 00006000 08:06 131711     /lib/tls/i686/cmov/librt-2.10.1.so
b6b8c000-b6b8d000 rwxp 00007000 08:06 131711     /lib/tls/i686/cmov/librt-2.10.1.so
b6b8d000-b6b90000 ---p 00000000 00:00 0 
b6b90000-b6bde000 rwxp 00000000 00:00 0 
b6bde000-b6c02000 r-xp 00000000 08:06 131689     /lib/tls/i686/cmov/libm-2.10.1.so
b6c02000-b6c03000 r-xp 00023000 08:06 131689     /lib/tls/i686/cmov/libm-2.10.1.so
b6c03000-b6c04000 rwxp 00024000 08:06 131689     /lib/tls/i686/cmov/libm-2.10.1.so
b6c04000-b72d1000 r-xp 00000000 08:06 402632     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/server/libjvm.so
b72d1000-b731e000 rwxp 006cc000 08:06 402632     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/server/libjvm.so
b731e000-b7742000 rwxp 00000000 00:00 0 
b7742000-b7880000 r-xp 00000000 08:06 131681     /lib/tls/i686/cmov/libc-2.10.1.so
b7880000-b7882000 r-xp 0013e000 08:06 131681     /lib/tls/i686/cmov/libc-2.10.1.so
b7882000-b7883000 rwxp 00140000 08:06 131681     /lib/tls/i686/cmov/libc-2.10.1.so
b7883000-b7886000 rwxp 00000000 00:00 0 
b7886000-b7888000 r-xp 00000000 08:06 131687     /lib/tls/i686/cmov/libdl-2.10.1.so
b7888000-b7889000 r-xp 00001000 08:06 131687     /lib/tls/i686/cmov/libdl-2.10.1.so
b7889000-b788a000 rwxp 00002000 08:06 131687     /lib/tls/i686/cmov/libdl-2.10.1.so
b788a000-b7891000 r-xp 00000000 08:06 402642     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/jli/libjli.so
b7891000-b7893000 rwxp 00006000 08:06 402642     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/jli/libjli.so
b7893000-b7894000 rwxp 00000000 00:00 0 
b7894000-b78a9000 r-xp 00000000 08:06 131707     /lib/tls/i686/cmov/libpthread-2.10.1.so
b78a9000-b78aa000 r-xp 00014000 08:06 131707     /lib/tls/i686/cmov/libpthread-2.10.1.so
b78aa000-b78ab000 rwxp 00015000 08:06 131707     /lib/tls/i686/cmov/libpthread-2.10.1.so
b78ab000-b78ad000 rwxp 00000000 00:00 0 
b78b0000-b78bb000 r-xp 00000000 08:06 402640     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libverify.so
b78bb000-b78bc000 rwxp 0000b000 08:06 402640     /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libverify.so
b78bc000-b78be000 rwxp 00000000 00:00 0 
b78be000-b78bf000 r-xp 00000000 00:00 0          [vdso]
b78bf000-b78da000 r-xp 00000000 08:06 521        /lib/ld-2.10.1.so
b78da000-b78db000 r-xp 0001a000 08:06 521        /lib/ld-2.10.1.so
b78db000-b78dc000 rwxp 0001b000 08:06 521        /lib/ld-2.10.1.so
bf8a0000-bf8b5000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xmx500m 
java_command: client.jar -d32
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=anthony
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.15/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x650690], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x650690], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x52f580], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x52f580], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x52f580], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x52f580], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x532170], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x531ea0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x531ea0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x531ea0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x531ea0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
libc:glibc 2.10.1 NPTL 2.10.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:2.60 1.10 1.02

CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 15 stepping 13, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3

Memory: 4k page, physical 3096712k(1780984k free), swap 5968108k(5968108k free)

vm_info: Java HotSpot(TM) Server VM (14.1-b02) for linux-x86 JRE (1.6.0_15-b03), built on Jul  2 2009 15:49:13 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Tue Nov 24 22:50:59 2009
elapsed time: 87 seconds

```

Again, I'm not sure what's happening, so I don't know if this is Ubuntu or Java-related.

Does anybody have any ideas of how I could get it to run correctly?

Thanks!

---

### Post by AlexMason on 2010-01-13
BUMP i need help on this too!!!!!!!!!!!!!!!!!

---

### Post by AlexMason on 2010-01-13
bump+

---

### Post by cavh on 2010-01-13
You might get a quicker response by posting on [http://forums.sun.com/forum.jspa?forumID=32]("http://forums.sun.com/forum.jspa?forumID=32")

---

