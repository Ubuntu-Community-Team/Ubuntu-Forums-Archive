---
title: "Error logs in home?"
date: 2011-03-21
forum: General Help
---

### Post by Guenhwyvar on 2011-03-21
what does this error log mean?

```


#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0xb695dd12, pid=16158, tid=1824521072
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.10, package 6b20-1.9.7-0ubuntu1
# Problematic frame:
# C  [libzip.so+0x3d12]
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x6d042800):  JavaThread "DetectPluginApplet" [_thread_in_native, id=16229, stack(0x6cbaf000,0x6cc00000)]

siginfo:si_signo=SIGBUS: si_errno=0, si_code=2 (BUS_ADRERR), si_addr=0x6d108dbe

Registers:
EAX=0x6deb1fd0, EBX=0xb6960ff4, ECX=0xb76cb3c0, EDX=0x09128378
ESP=0x6cbfda40, EBP=0x6cbfda98, ESI=0x6d108da1, EDI=0x09128380
EIP=0xb695dd12, CR2=0x6d108dbe, EFLAGS=0x00210202

Register to memory mapping:

EAX=0x6deb1fd0
0x6deb1fd0 is pointing to unknown location

EBX=0xb6960ff4
0xb6960ff4: <offset 0x6ff4> in /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so at 0xb695a000

ECX=0xb76cb3c0
0xb76cb3c0: <offset 0x15a3c0> in /lib/libc.so.6 at 0xb7571000

EDX=0x09128378
0x09128378 is pointing to unknown location

ESP=0x6cbfda40
0x6cbfda40 is pointing into the stack for thread: 0x6d042800
"DetectPluginApplet" prio=10 tid=0x6d042800 nid=0x3f65 runnable [0x6cbfd000]
   java.lang.Thread.State: RUNNABLE

EBP=0x6cbfda98
0x6cbfda98 is pointing into the stack for thread: 0x6d042800
"DetectPluginApplet" prio=10 tid=0x6d042800 nid=0x3f65 runnable [0x6cbfd000]
   java.lang.Thread.State: RUNNABLE

ESI=0x6d108da1
0x6d108da1 is pointing to unknown location

EDI=0x09128380
0x09128380 is pointing to unknown location


Top of Stack: (sp=0x6cbfda40)
0x6cbfda40:   00000030 6cbfdaa8 6cbfda68 b7140ff4
0x6cbfda50:   00000041 6deb1fd0 6cbfda78 b6e01920
0x6cbfda60:   6de9eb18 00000037 6cbfdad8 b6e018fc
0x6cbfda70:   6cbfdabc 09128380 6deb1fd0 b695dbb0
0x6cbfda80:   6de9eb18 6d042800 b695dccd b6960ff4
0x6cbfda90:   6d042da8 6deb1fd0 6cbfdad8 b695e098
0x6cbfdaa0:   00000000 6cbfdb2a 6d042800 00000000
0x6cbfdab0:   00000000 6de7fbf8 291e193c 00000090 

Instructions: (pc=0xb695dd12)
0xb695dd02:   00 00 00 00 8b 45 e0 8b 76 04 2b 70 1c 03 70 10
0xb695dd12:   0f b6 56 1d 0f b6 46 1c c1 e2 08 09 c2 89 55 e4 

Stack: [0x6cbaf000,0x6cc00000],  sp=0x6cbfda40,  free space=314k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libzip.so+0x3d12]
C  [libzip.so+0x4098]  ZIP_GetEntry+0xc8
C  [libzip.so+0x313f]  Java_java_util_zip_ZipFile_getEntry+0xff
j  java.util.zip.ZipFile.getEntry(JLjava/lang/String;Z)J+0
j  java.util.zip.ZipFile.getEntry(Ljava/lang/String;)Ljava/util/zip/ZipEntry;+31
j  java.util.jar.JarFile.getEntry(Ljava/lang/String;)Ljava/util/zip/ZipEntry;+2
j  java.util.jar.JarFile.getJarEntry(Ljava/lang/String;)Ljava/util/jar/JarEntry;+2
j  sun.misc.URLClassPath$JarLoader.getResource(Ljava/lang/String;Z)Lsun/misc/Resource;+48
j  sun.misc.URLClassPath.getResource(Ljava/lang/String;Z)Lsun/misc/Resource;+53
j  java.net.URLClassLoader$1.run()Ljava/lang/Object;+26
v  ~StubRoutines::call_stub
V  [libjvm.so+0x387902]
V  [libjvm.so+0x518d19]
V  [libjvm.so+0x38683f]
V  [libjvm.so+0x3d597d]
C  [libjava.so+0x9cda]  Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedExceptionAction_2Ljava_security_AccessControlContext_2+0x3a
j  java.security.AccessController.doPrivileged(Ljava/security/PrivilegedExceptionAction;Ljava/security/AccessControlContext;)Ljava/lang/Object;+0
j  java.net.URLClassLoader.findClass(Ljava/lang/String;)Ljava/lang/Class;+13
j  net.sourceforge.jnlp.runtime.JNLPClassLoader.findClass(Ljava/lang/String;)Ljava/lang/Class;+23
j  net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClassExt(Ljava/lang/String;)Ljava/lang/Class;+6
j  net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClass(Ljava/lang/String;)Ljava/lang/Class;+36
v  ~StubRoutines::call_stub
V  [libjvm.so+0x387902]
V  [libjvm.so+0x518d19]
V  [libjvm.so+0x38683f]
V  [libjvm.so+0x38738a]
V  [libjvm.so+0x387482]
V  [libjvm.so+0x5e39b9]
V  [libjvm.so+0x5e42e2]
V  [libjvm.so+0x5e46c4]
V  [libjvm.so+0x5e56a0]
V  [libjvm.so+0x28d3ba]
V  [libjvm.so+0x28ed19]
V  [libjvm.so+0x47d705]
V  [libjvm.so+0x47d76a]
V  [libjvm.so+0x47fa32]
V  [libjvm.so+0x481309]
V  [libjvm.so+0x380cac]
j  com.webct.platform.tools.dragndrop.common.DetectPluginApplet.destroy()V+6
j  sun.applet.AppletPanel.run()V+523
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub
V  [libjvm.so+0x387902]
V  [libjvm.so+0x518d19]
V  [libjvm.so+0x38683f]
V  [libjvm.so+0x38738a]
V  [libjvm.so+0x3874e8]
V  [libjvm.so+0x3d1cab]
V  [libjvm.so+0x60ee7c]
V  [libjvm.so+0x60ef42]
V  [libjvm.so+0x51f741]
C  [libpthread.so.0+0x5cc9]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  java.util.zip.ZipFile.getEntry(JLjava/lang/String;Z)J+0
j  java.util.zip.ZipFile.getEntry(Ljava/lang/String;)Ljava/util/zip/ZipEntry;+31
j  java.util.jar.JarFile.getEntry(Ljava/lang/String;)Ljava/util/zip/ZipEntry;+2
j  java.util.jar.JarFile.getJarEntry(Ljava/lang/String;)Ljava/util/jar/JarEntry;+2
j  sun.misc.URLClassPath$JarLoader.getResource(Ljava/lang/String;Z)Lsun/misc/Resource;+48
j  sun.misc.URLClassPath.getResource(Ljava/lang/String;Z)Lsun/misc/Resource;+53
j  java.net.URLClassLoader$1.run()Ljava/lang/Object;+26
v  ~StubRoutines::call_stub
j  java.security.AccessController.doPrivileged(Ljava/security/PrivilegedExceptionAction;Ljava/security/AccessControlContext;)Ljava/lang/Object;+0
j  java.net.URLClassLoader.findClass(Ljava/lang/String;)Ljava/lang/Class;+13
j  net.sourceforge.jnlp.runtime.JNLPClassLoader.findClass(Ljava/lang/String;)Ljava/lang/Class;+23
j  net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClassExt(Ljava/lang/String;)Ljava/lang/Class;+6
j  net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClass(Ljava/lang/String;)Ljava/lang/Class;+36
v  ~StubRoutines::call_stub
j  com.webct.platform.tools.dragndrop.common.DetectPluginApplet.destroy()V+6
j  sun.applet.AppletPanel.run()V+523
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x6d697c00 JavaThread "Thread-34" [_thread_blocked, id=16250, stack(0x6c70d000,0x6c75e000)]
  0x095a4800 JavaThread "myApplet applet" [_thread_in_native, id=16242, stack(0x6c7af000,0x6c800000)]
  0x09631400 JavaThread "Thread-30" [_thread_blocked, id=16241, stack(0x6cb0d000,0x6cb5e000)]
  0x6d061400 JavaThread "Thread-29" [_thread_blocked, id=16240, stack(0x6cf5e000,0x6cfaf000)]
  0x6d682800 JavaThread "WIOMessageProcessor" [_thread_blocked, id=16235, stack(0x6cb5e000,0x6cbaf000)]
=>0x6d042800 JavaThread "DetectPluginApplet" [_thread_in_native, id=16229, stack(0x6cbaf000,0x6cc00000)]
  0x6d02ec00 JavaThread "TCPSession Thread #0" daemon [_thread_in_native, id=16228, stack(0x6cf0d000,0x6cf5e000)]
  0x6d043400 JavaThread "Thread-18" [_thread_blocked, id=16222, stack(0x6cfaf000,0x6d000000)]
  0x6d013000 JavaThread "WIOServerStatusThread" [_thread_blocked, id=16221, stack(0x6d125000,0x6d176000)]
  0x094bf400 JavaThread "Keep-Alive-Timer" daemon [_thread_blocked, id=16220, stack(0x6c927000,0x6c978000)]
  0x0979c400 JavaThread "Keep-Alive-SocketCleaner" daemon [_thread_blocked, id=16219, stack(0x6c978000,0x6c9c9000)]
  0x09543400 JavaThread "Thread-16" [_thread_blocked, id=16218, stack(0x6c9c9000,0x6ca1a000)]
  0x09542000 JavaThread "Thread-15" [_thread_blocked, id=16217, stack(0x6ca1a000,0x6ca6b000)]
  0x09541000 JavaThread "Thread-14" [_thread_blocked, id=16216, stack(0x6ca6b000,0x6cabc000)]
  0x09464000 JavaThread "Thread-13" [_thread_blocked, id=16215, stack(0x6cabc000,0x6cb0d000)]
  0x6d690000 JavaThread "Messenger" [_thread_blocked, id=16207, stack(0x6d176000,0x6d1c7000)]
  0x6d685000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=16206, stack(0x6d1c7000,0x6d218000)]
  0x0933bc00 JavaThread "AWT-Shutdown" [_thread_blocked, id=16205, stack(0x6d218000,0x6d269000)]
  0x0927f400 JavaThread "Thread-5" [_thread_blocked, id=16203, stack(0x6d269000,0x6d2ba000)]
  0x0913bc00 JavaThread "Thread-4" [_thread_blocked, id=16202, stack(0x6d2ba000,0x6d30b000)]
  0x08f1c000 JavaThread "DestroyJavaVM" [_thread_blocked, id=16165, stack(0xb69c1000,0xb6a12000)]
  0x0913b400 JavaThread "Thread-3" [_thread_in_native, id=16200, stack(0x6d30b000,0x6d35c000)]
  0x09019400 JavaThread "Image Fetcher 0" daemon [_thread_blocked, id=16197, stack(0x6d5af000,0x6d600000)]
  0x09018000 JavaThread "Thread-2" [_thread_in_Java, id=16196, stack(0x6d72e000,0x6d77f000)]
  0x6d62a400 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=16190, stack(0x6d77f000,0x6d7d0000)]
  0x6de7cc00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=16189, stack(0x6d90d000,0x6d95e000)]
  0x6de01c00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=16184, stack(0x6dd2e000,0x6dd7f000)]
  0x08fe0800 JavaThread "CompilerThread1" daemon [_thread_blocked, id=16183, stack(0x6dd7f000,0x6de00000)]
  0x08fde800 JavaThread "CompilerThread0" daemon [_thread_in_native, id=16182, stack(0x6df13000,0x6df94000)]
  0x08fdd000 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=16181, stack(0x6df94000,0x6dfe5000)]
  0x08fcd400 JavaThread "Finalizer" daemon [_thread_blocked, id=16175, stack(0x6e1e5000,0x6e236000)]
  0x08fc8c00 JavaThread "Reference Handler" daemon [_thread_blocked, id=16174, stack(0x6e236000,0x6e287000)]

Other Threads:
  0x08fc4c00 VMThread [stack: 0x6e287000,0x6e308000] [id=16171]
  0x6de03c00 WatcherThread [stack: 0x6dcad000,0x6dd2e000] [id=16185]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 203264K, used 128004K [0x9f3e0000, 0xb3310000, 0xb3880000)
  eden space 199616K, 63% used [0x9f3e0000,0xa7079238,0xab6d0000)
  from space 3648K, 11% used [0xab6d0000,0xab738060,0xaba60000)
  to   space 3712K, 0% used [0xb2f70000,0xb2f70000,0xb3310000)
 PSOldGen        total 41536K, used 3977K [0x76a80000, 0x79310000, 0x9f3e0000)
  object space 41536K, 9% used [0x76a80000,0x76e62628,0x79310000)
 PSPermGen       total 16384K, used 13550K [0x6ea80000, 0x6fa80000, 0x76a80000)
  object space 16384K, 82% used [0x6ea80000,0x6f7bb9b0,0x6fa80000)

Dynamic libraries:
08048000-08051000 r-xp 00000000 08:05 6039390    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:05 6039390    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:05 6039390    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08f16000-097ef000 rw-p 00000000 00:00 0          [heap]
6c600000-6c636000 rw-p 00000000 00:00 0 
6c636000-6c700000 ---p 00000000 00:00 0 
6c70d000-6c710000 ---p 00000000 00:00 0 
6c710000-6c75e000 rw-p 00000000 00:00 0 
6c75e000-6c761000 ---p 00000000 00:00 0 
6c761000-6c7af000 rw-p 00000000 00:00 0 
6c7af000-6c7b2000 ---p 00000000 00:00 0 
6c7b2000-6c800000 rw-p 00000000 00:00 0 
6c800000-6c8fa000 rw-p 00000000 00:00 0 
6c8fa000-6c900000 ---p 00000000 00:00 0 
6c927000-6c92a000 ---p 00000000 00:00 0 
6c92a000-6c978000 rw-p 00000000 00:00 0 
6c978000-6c97b000 ---p 00000000 00:00 0 
6c97b000-6c9c9000 rw-p 00000000 00:00 0 
6c9c9000-6c9cc000 ---p 00000000 00:00 0 
6c9cc000-6ca1a000 rw-p 00000000 00:00 0 
6ca1a000-6ca1d000 ---p 00000000 00:00 0 
6ca1d000-6ca6b000 rw-p 00000000 00:00 0 
6ca6b000-6ca6e000 ---p 00000000 00:00 0 
6ca6e000-6cabc000 rw-p 00000000 00:00 0 
6cabc000-6cabf000 ---p 00000000 00:00 0 
6cabf000-6cb0d000 rw-p 00000000 00:00 0 
6cb0d000-6cb10000 ---p 00000000 00:00 0 
6cb10000-6cb5e000 rw-p 00000000 00:00 0 
6cb5e000-6cb61000 ---p 00000000 00:00 0 
6cb61000-6cbaf000 rw-p 00000000 00:00 0 
6cbaf000-6cbb2000 ---p 00000000 00:00 0 
6cbb2000-6cc00000 rw-p 00000000 00:00 0 
6cc00000-6ccf9000 rw-p 00000000 00:00 0 
6ccf9000-6cd00000 ---p 00000000 00:00 0 
6cd00000-6cdf8000 rw-p 00000000 00:00 0 
6cdf8000-6ce00000 ---p 00000000 00:00 0 
6ce00000-6cefb000 rw-p 00000000 00:00 0 
6cefb000-6cf00000 ---p 00000000 00:00 0 
6cf0d000-6cf10000 ---p 00000000 00:00 0 
6cf10000-6cf5e000 rw-p 00000000 00:00 0 
6cf5e000-6cf61000 ---p 00000000 00:00 0 
6cf61000-6cfaf000 rw-p 00000000 00:00 0 
6cfaf000-6cfb2000 ---p 00000000 00:00 0 
6cfb2000-6d000000 rw-p 00000000 00:00 0 
6d000000-6d0f6000 rw-p 00000000 00:00 0 
6d0f6000-6d100000 ---p 00000000 00:00 0 
6d105000-6d108000 r--s 00028000 00:14 917535     /home/nyx/.icedteaplugin/cache/http/vista.shef.ac.uk/webct/jar/dragndrop_applet.jar
6d108000-6d10b000 r--s 00028000 00:14 917535     /home/nyx/.icedteaplugin/cache/http/vista.shef.ac.uk/webct/jar/dragndrop_applet.jar
6d10b000-6d11b000 r-xp 00000000 08:05 6818410    /lib/libresolv-2.12.1.so
6d11b000-6d11c000 r--p 00010000 08:05 6818410    /lib/libresolv-2.12.1.so
6d11c000-6d11d000 rw-p 00011000 08:05 6818410    /lib/libresolv-2.12.1.so
6d11d000-6d11f000 rw-p 00000000 00:00 0 
6d11f000-6d123000 r-xp 00000000 08:05 6818403    /lib/libnss_dns-2.12.1.so
6d123000-6d124000 r--p 00004000 08:05 6818403    /lib/libnss_dns-2.12.1.so
6d124000-6d125000 rw-p 00005000 08:05 6818403    /lib/libnss_dns-2.12.1.so
6d125000-6d128000 ---p 00000000 00:00 0 
6d128000-6d176000 rw-p 00000000 00:00 0 
6d176000-6d179000 ---p 00000000 00:00 0 
6d179000-6d1c7000 rw-p 00000000 00:00 0 
6d1c7000-6d1ca000 ---p 00000000 00:00 0 
6d1ca000-6d218000 rw-p 00000000 00:00 0 
6d218000-6d21b000 ---p 00000000 00:00 0 
6d21b000-6d269000 rw-p 00000000 00:00 0 
6d269000-6d26c000 ---p 00000000 00:00 0 
6d26c000-6d2ba000 rw-p 00000000 00:00 0 
6d2ba000-6d2bd000 ---p 00000000 00:00 0 
6d2bd000-6d30b000 rw-p 00000000 00:00 0 
6d30b000-6d30e000 ---p 00000000 00:00 0 
6d30e000-6d35c000 rw-p 00000000 00:00 0 
6d35c000-6d3a3000 r-xp 00000000 08:05 6031463    /usr/lib/nss/libfreebl3.so
6d3a3000-6d3a4000 r--p 00047000 08:05 6031463    /usr/lib/nss/libfreebl3.so
6d3a4000-6d3a5000 rw-p 00048000 08:05 6031463    /usr/lib/nss/libfreebl3.so
6d3a5000-6d3a9000 rw-p 00000000 00:00 0 
6d3a9000-6d431000 r-xp 00000000 08:05 6031177    /usr/lib/libsqlite3.so.0.8.6
6d431000-6d432000 r--p 00088000 08:05 6031177    /usr/lib/libsqlite3.so.0.8.6
6d432000-6d433000 rw-p 00089000 08:05 6031177    /usr/lib/libsqlite3.so.0.8.6
6d433000-6d468000 r-xp 00000000 08:05 6031464    /usr/lib/nss/libsoftokn3.so
6d468000-6d469000 r--p 00035000 08:05 6031464    /usr/lib/nss/libsoftokn3.so
6d469000-6d46a000 rw-p 00036000 08:05 6031464    /usr/lib/nss/libsoftokn3.so
6d46a000-6d49a000 r-xp 00000000 08:05 6032797    /usr/lib/libnspr4.so
6d49a000-6d49b000 r--p 0002f000 08:05 6032797    /usr/lib/libnspr4.so
6d49b000-6d49c000 rw-p 00030000 08:05 6032797    /usr/lib/libnspr4.so
6d49c000-6d49e000 rw-p 00000000 00:00 0 
6d49e000-6d5aa000 r-xp 00000000 08:05 6031473    /usr/lib/libnss3.so
6d5aa000-6d5ad000 r--p 0010b000 08:05 6031473    /usr/lib/libnss3.so
6d5ad000-6d5af000 rw-p 0010e000 08:05 6031473    /usr/lib/libnss3.so
6d5af000-6d5b2000 ---p 00000000 00:00 0 
6d5b2000-6d600000 rw-p 00000000 00:00 0 
6d600000-6d700000 rw-p 00000000 00:00 0 
6d700000-6d701000 r--s 00004000 00:14 917527     /home/nyx/.icedteaplugin/cache/http/vista.shef.ac.uk/webct/jar/wioAppletResources_en_GB.jar
6d701000-6d702000 r--s 00005000 00:14 917525     /home/nyx/.icedteaplugin/cache/http/vista.shef.ac.uk/webct/jar/wioAppletResources_de.jar
6d702000-6d707000 r--s 0002e000 00:14 917524     /home/nyx/.icedteaplugin/cache/http/vista.shef.ac.uk/webct/jar/crimson.jar
6d707000-6d715000 r--s 000d8000 00:14 917522     /home/nyx/.icedteaplugin/cache/http/vista.shef.ac.uk/webct/jar/wio_applet.jar
6d715000-6d729000 r-xp 00000000 08:05 6031472    /usr/lib/libnssutil3.so
6d729000-6d72a000 ---p 00014000 08:05 6031472    /usr/lib/libnssutil3.so
6d72a000-6d72d000 r--p 00014000 08:05 6031472    /usr/lib/libnssutil3.so
6d72d000-6d72e000 rw-p 00017000 08:05 6031472    /usr/lib/libnssutil3.so
6d72e000-6d731000 ---p 00000000 00:00 0 
6d731000-6d77f000 rw-p 00000000 00:00 0 
6d77f000-6d782000 ---p 00000000 00:00 0 
6d782000-6d7d0000 rw-p 00000000 00:00 0 
6d7d0000-6d7d1000 r--s 00000000 08:05 1053651    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
6d7d1000-6d7d2000 r--s 00000000 08:05 1048640    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6d7d2000-6d7d8000 r--s 00000000 08:05 1048637    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6d7d8000-6d7da000 r--s 00000000 08:05 1048638    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6d7da000-6d7dd000 r--s 00000000 08:05 1048647    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6d7dd000-6d7e0000 r--s 00000000 08:05 1049452    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6d7e0000-6d7e2000 r--s 00000000 08:05 1056292    /var/cache/fontconfig/ea47318ec9849e1a71e80a5d69d13859-le32d4.cache-3
6d7e2000-6d7e3000 r--s 00000000 08:05 1056291    /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-le32d4.cache-3
6d7e3000-6d7e4000 r--s 00000000 08:05 1048648    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6d7e4000-6d7e7000 r--s 00000000 08:05 1048634    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6d7e7000-6d7e8000 r--s 00000000 08:05 1048630    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6d7e8000-6d7e9000 r--s 00000000 08:05 1048623    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6d7e9000-6d7ea000 r--s 00000000 08:05 1048632    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6d7ea000-6d7ee000 r--s 00000000 08:05 1048639    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6d7ee000-6d7f2000 r--s 00000000 08:05 1055937    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
6d7f2000-6d7f9000 r--s 00000000 08:05 1048642    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6d7f9000-6d804000 r--s 00000000 08:05 1048624    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6d804000-6d826000 r--s 00000000 08:05 1055870    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6d828000-6d83c000 r-xp 00000000 08:05 6166532    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
6d83c000-6d83d000 r--p 00013000 08:05 6166532    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
6d83d000-6d83e000 rw-p 00014000 08:05 6166532    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
6d83e000-6d84b000 r-xp 00000000 08:05 6166497    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
6d84b000-6d84c000 r--p 0000c000 08:05 6166497    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
6d84c000-6d84d000 rw-p 0000d000 08:05 6166497    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
6d84d000-6d84e000 r--s 00000000 08:05 1053651    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
6d84e000-6d84f000 r--s 00000000 08:05 1048640    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6d84f000-6d855000 r--s 00000000 08:05 1048637    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6d855000-6d857000 r--s 00000000 08:05 1048638    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6d857000-6d85a000 r--s 00000000 08:05 1048647    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6d85a000-6d85d000 r--s 00000000 08:05 1049452    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6d85d000-6d85f000 r--s 00000000 08:05 1056292    /var/cache/fontconfig/ea47318ec9849e1a71e80a5d69d13859-le32d4.cache-3
6d85f000-6d860000 r--s 00000000 08:05 1056291    /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-le32d4.cache-3
6d860000-6d861000 r--s 00000000 08:05 1048648    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6d861000-6d864000 r--s 00000000 08:05 1048634    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6d864000-6d865000 r--s 00000000 08:05 1048630    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6d865000-6d866000 r--s 00000000 08:05 1048623    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6d866000-6d867000 r--s 00000000 08:05 1048632    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6d867000-6d86b000 r--s 00000000 08:05 1048639    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6d86b000-6d86f000 r--s 00000000 08:05 1055937    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
6d86f000-6d876000 r--s 00000000 08:05 1048642    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6d876000-6d881000 r--s 00000000 08:05 1048624    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6d881000-6d884000 r--s 00000000 08:05 1048644    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6d884000-6d8a6000 r--s 00000000 08:05 1055870    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6d8a6000-6d8ae000 r--s 00000000 08:05 1048643    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6d8ae000-6d8b6000 r--s 00000000 08:05 1053365    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6d8b8000-6d8bb000 r--s 00000000 08:05 1048644    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6d8bb000-6d8c3000 r--s 00000000 08:05 1048643    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6d8c3000-6d8cb000 r--s 00000000 08:05 1053365    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6d8cb000-6d8cc000 r--s 00008000 00:14 917533     /home/nyx/.icedteaplugin/cache/http/vista.shef.ac.uk/webct/jar/browserchecker_applet.jar
6d8cc000-6d8ce000 r-xp 00000000 08:05 6815861    /lib/libnss_mdns4_minimal.so.2
6d8ce000-6d8cf000 r--p 00001000 08:05 6815861    /lib/libnss_mdns4_minimal.so.2
6d8cf000-6d8d0000 rw-p 00002000 08:05 6815861    /lib/libnss_mdns4_minimal.so.2
6d8d0000-6d8d2000 r-xp 00000000 08:05 6032858    /usr/lib/libplds4.so
6d8d2000-6d8d3000 r--p 00001000 08:05 6032858    /usr/lib/libplds4.so
6d8d3000-6d8d4000 rw-p 00002000 08:05 6032858    /usr/lib/libplds4.so
6d8d4000-6d8d8000 r-xp 00000000 08:05 6032144    /usr/lib/libXfixes.so.3.1.0
6d8d8000-6d8d9000 r--p 00003000 08:05 6032144    /usr/lib/libXfixes.so.3.1.0
6d8d9000-6d8da000 rw-p 00004000 08:05 6032144    /usr/lib/libXfixes.so.3.1.0
6d8da000-6d8e2000 r-xp 00000000 08:05 6032136    /usr/lib/libXcursor.so.1.0.2
6d8e2000-6d8e3000 r--p 00007000 08:05 6032136    /usr/lib/libXcursor.so.1.0.2
6d8e3000-6d8e4000 rw-p 00008000 08:05 6032136    /usr/lib/libXcursor.so.1.0.2
6d8e5000-6d8e8000 r-xp 00000000 08:05 6032856    /usr/lib/libplc4.so
6d8e8000-6d8e9000 r--p 00002000 08:05 6032856    /usr/lib/libplc4.so
6d8e9000-6d8ea000 rw-p 00003000 08:05 6032856    /usr/lib/libplc4.so
6d8ea000-6d8ed000 r--s 00038000 08:05 6039366    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
6d8ed000-6d8ef000 r--s 00013000 08:05 6039341    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
6d8ef000-6d8f2000 r--s 00031000 08:05 6039368    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
6d8f2000-6d8f6000 r--s 0007c000 08:05 6039339    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
6d8f6000-6d8fc000 r--s 000fc000 08:05 6039380    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
6d8fc000-6d8ff000 r--s 00000000 08:05 1056290    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6d8ff000-6d90d000 r--s 00000000 08:05 1053331    /var/cache/fontconfig/865f88548240fee46819705c6468c165-le32d4.cache-3
6d90d000-6d910000 ---p 00000000 00:00 0 
6d910000-6d95e000 rw-p 00000000 00:00 0 
6d95e000-6d978000 r-xp 00000000 08:05 6815823    /lib/libgcc_s.so.1
6d978000-6d979000 r--p 00019000 08:05 6815823    /lib/libgcc_s.so.1
6d979000-6d97a000 rw-p 0001a000 08:05 6815823    /lib/libgcc_s.so.1
6d97a000-6d9ec000 r-xp 00000000 08:05 6029547    /usr/lib/libfreetype.so.6.6.0
6d9ec000-6d9f0000 r--p 00071000 08:05 6029547    /usr/lib/libfreetype.so.6.6.0
6d9f0000-6d9f1000 rw-p 00075000 08:05 6029547    /usr/lib/libfreetype.so.6.6.0
6d9f1000-6da35000 r-xp 00000000 08:05 6166534    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
6da35000-6da37000 r--p 00043000 08:05 6166534    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
6da37000-6da38000 rw-p 00045000 08:05 6166534    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
6da38000-6da3d000 rw-p 00000000 00:00 0 
6da3d000-6da41000 r-xp 00000000 08:05 6032140    /usr/lib/libXdmcp.so.6.0.0
6da41000-6da42000 r--p 00003000 08:05 6032140    /usr/lib/libXdmcp.so.6.0.0
6da42000-6da43000 rw-p 00004000 08:05 6032140    /usr/lib/libXdmcp.so.6.0.0
6da43000-6da45000 r-xp 00000000 08:05 6032129    /usr/lib/libXau.so.6.0.0
6da45000-6da46000 r--p 00001000 08:05 6032129    /usr/lib/libXau.so.6.0.0
6da46000-6da47000 rw-p 00002000 08:05 6032129    /usr/lib/libXau.so.6.0.0
6da47000-6da5f000 r-xp 00000000 08:05 6033091    /usr/lib/libxcb.so.1.1.0
6da5f000-6da60000 r--p 00017000 08:05 6033091    /usr/lib/libxcb.so.1.1.0
6da60000-6da61000 rw-p 00018000 08:05 6033091    /usr/lib/libxcb.so.1.1.0
6da61000-6da6d000 r-xp 00000000 08:05 6032150    /usr/lib/libXi.so.6.1.0
6da6d000-6da6e000 r--p 0000b000 08:05 6032150    /usr/lib/libXi.so.6.1.0
6da6e000-6da6f000 rw-p 0000c000 08:05 6032150    /usr/lib/libXi.so.6.1.0
6da6f000-6da77000 r-xp 00000000 08:05 6032164    /usr/lib/libXrender.so.1.3.0
6da77000-6da78000 r--p 00007000 08:05 6032164    /usr/lib/libXrender.so.1.3.0
6da78000-6da79000 rw-p 00008000 08:05 6032164    /usr/lib/libXrender.so.1.3.0
6da79000-6db92000 r-xp 00000000 08:05 6032125    /usr/lib/libX11.so.6.3.0
6db92000-6db93000 r--p 00118000 08:05 6032125    /usr/lib/libX11.so.6.3.0
6db93000-6db95000 rw-p 00119000 08:05 6032125    /usr/lib/libX11.so.6.3.0
6db95000-6db96000 rw-p 00000000 00:00 0 
6db96000-6dba4000 r-xp 00000000 08:05 6032142    /usr/lib/libXext.so.6.4.0
6dba4000-6dba5000 r--p 0000d000 08:05 6032142    /usr/lib/libXext.so.6.4.0
6dba5000-6dba6000 rw-p 0000e000 08:05 6032142    /usr/lib/libXext.so.6.4.0
6dba7000-6dbaa000 r--s 00000000 08:05 1056290    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6dbaa000-6dbb8000 r--s 00000000 08:05 1053331    /var/cache/fontconfig/865f88548240fee46819705c6468c165-le32d4.cache-3
6dbb8000-6dbfb000 r-xp 00000000 08:05 7345808    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
6dbfb000-6dbfc000 r--p 00042000 08:05 7345808    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
6dbfc000-6dbfe000 rw-p 00043000 08:05 7345808    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
6dbfe000-6dbff000 rw-p 00000000 00:00 0 
6dbff000-6dc81000 r-xp 00000000 08:05 6166499    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
6dc81000-6dc82000 r--p 00081000 08:05 6166499    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
6dc82000-6dc88000 rw-p 00082000 08:05 6166499    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
6dc88000-6dcad000 rw-p 00000000 00:00 0 
6dcad000-6dcae000 ---p 00000000 00:00 0 
6dcae000-6dd2e000 rw-p 00000000 00:00 0 
6dd2e000-6dd31000 ---p 00000000 00:00 0 
6dd31000-6dd7f000 rw-p 00000000 00:00 0 
6dd7f000-6dd82000 ---p 00000000 00:00 0 
6dd82000-6de00000 rw-p 00000000 00:00 0 
6de00000-6deff000 rw-p 00000000 00:00 0 
6deff000-6df00000 ---p 00000000 00:00 0 
6df02000-6df06000 r-xp 00000000 08:05 6032170    /usr/lib/libXtst.so.6.1.0
6df06000-6df07000 r--p 00003000 08:05 6032170    /usr/lib/libXtst.so.6.1.0
6df07000-6df08000 rw-p 00004000 08:05 6032170    /usr/lib/libXtst.so.6.1.0
6df08000-6df10000 r--s 00066000 08:05 6431677    /usr/share/java/gnome-java-bridge.jar
6df10000-6df13000 r--s 0000f000 08:05 6039371    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
6df13000-6df16000 ---p 00000000 00:00 0 
6df16000-6df94000 rw-p 00000000 00:00 0 
6df94000-6df97000 ---p 00000000 00:00 0 
6df97000-6dfe5000 rw-p 00000000 00:00 0 
6dfe5000-6e1e5000 r--p 00000000 08:05 6031710    /usr/lib/locale/locale-archive
6e1e5000-6e1e8000 ---p 00000000 00:00 0 
6e1e8000-6e236000 rw-p 00000000 00:00 0 
6e236000-6e239000 ---p 00000000 00:00 0 
6e239000-6e287000 rw-p 00000000 00:00 0 
6e287000-6e288000 ---p 00000000 00:00 0 
6e288000-6e308000 rw-p 00000000 00:00 0 
6e308000-6e30d000 r--s 00044000 08:05 6039347    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
6e30d000-6e340000 rw-p 00000000 00:00 0 
6e340000-6e4cf000 r--s 038c2000 08:05 6039397    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
6e4cf000-6e4d0000 ---p 00000000 00:00 0 
6e4d0000-6e550000 rw-p 00000000 00:00 0 
6e550000-6e551000 ---p 00000000 00:00 0 
6e551000-6e5d1000 rw-p 00000000 00:00 0 
6e5d1000-6e5d2000 ---p 00000000 00:00 0 
6e5d2000-6e652000 rw-p 00000000 00:00 0 
6e652000-6e653000 ---p 00000000 00:00 0 
6e653000-6e6db000 rw-p 00000000 00:00 0 
6e6db000-6e713000 rw-p 00000000 00:00 0 
6e713000-6e728000 rw-p 00000000 00:00 0 
6e728000-6e858000 rw-p 00000000 00:00 0 
6e858000-6e860000 rw-p 00000000 00:00 0 
6e860000-6e898000 rw-p 00000000 00:00 0 
6e898000-6e8ad000 rw-p 00000000 00:00 0 
6e8ad000-6e9dc000 rw-p 00000000 00:00 0 
6e9dc000-6ea7d000 rw-p 00000000 00:00 0 
6ea7d000-6ea7f000 rw-p 00000000 00:00 0 
6ea7f000-6fa80000 rw-p 00000000 00:00 0 
6fa80000-76a80000 rw-p 00000000 00:00 0 
76a80000-79310000 rw-p 00000000 00:00 0 
79310000-9f3e0000 rw-p 00000000 00:00 0 
9f3e0000-b3310000 rw-p 00000000 00:00 0 
b3310000-b3880000 rw-p 00000000 00:00 0 
b3881000-b388a000 rw-p 00000000 00:00 0 
b388a000-b3941000 rw-p 00000000 00:00 0 
b3941000-b3b81000 rwxp 00000000 00:00 0 
b3b81000-b6941000 rw-p 00000000 00:00 0 
b6941000-b694b000 r-xp 00000000 08:05 6818404    /lib/libnss_files-2.12.1.so
b694b000-b694c000 r--p 00009000 08:05 6818404    /lib/libnss_files-2.12.1.so
b694c000-b694d000 rw-p 0000a000 08:05 6818404    /lib/libnss_files-2.12.1.so
b694d000-b6956000 r-xp 00000000 08:05 6818406    /lib/libnss_nis-2.12.1.so
b6956000-b6957000 r--p 00008000 08:05 6818406    /lib/libnss_nis-2.12.1.so
b6957000-b6958000 rw-p 00009000 08:05 6818406    /lib/libnss_nis-2.12.1.so
b6958000-b6959000 r--p 00000000 00:00 0 
b6959000-b695a000 r--s 00000000 08:05 1049451    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b695a000-b6960000 r-xp 00000000 08:05 6166501    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
b6960000-b6961000 r--p 00005000 08:05 6166501    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
b6961000-b6962000 rw-p 00006000 08:05 6166501    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
b6962000-b696a000 rw-s 00000000 08:05 8398505    /tmp/hsperfdata_nyx/16158
b696a000-b697d000 r-xp 00000000 08:05 6818401    /lib/libnsl-2.12.1.so
b697d000-b697e000 r--p 00012000 08:05 6818401    /lib/libnsl-2.12.1.so
b697e000-b697f000 rw-p 00013000 08:05 6818401    /lib/libnsl-2.12.1.so
b697f000-b6981000 rw-p 00000000 00:00 0 
b6981000-b6982000 r--s 00000000 08:05 1049451    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b6982000-b6983000 r--p 00299000 08:05 6031710    /usr/lib/locale/locale-archive
b6983000-b6989000 r-xp 00000000 08:05 6818402    /lib/libnss_compat-2.12.1.so
b6989000-b698a000 r--p 00006000 08:05 6818402    /lib/libnss_compat-2.12.1.so
b698a000-b698b000 rw-p 00007000 08:05 6818402    /lib/libnss_compat-2.12.1.so
b698b000-b6991000 r-xp 00000000 08:05 6166517    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
b6991000-b6992000 r--p 00005000 08:05 6166517    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
b6992000-b6993000 rw-p 00006000 08:05 6166517    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
b6993000-b69b5000 r-xp 00000000 08:05 6166496    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
b69b5000-b69b6000 r--p 00021000 08:05 6166496    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
b69b6000-b69b8000 rw-p 00022000 08:05 6166496    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
b69b8000-b69bf000 r-xp 00000000 08:05 6818411    /lib/librt-2.12.1.so
b69bf000-b69c0000 r--p 00006000 08:05 6818411    /lib/librt-2.12.1.so
b69c0000-b69c1000 rw-p 00007000 08:05 6818411    /lib/librt-2.12.1.so
b69c1000-b69c4000 ---p 00000000 00:00 0 
b69c4000-b6a12000 rw-p 00000000 00:00 0 
b6a12000-b6a36000 r-xp 00000000 08:05 6818399    /lib/libm-2.12.1.so
b6a36000-b6a37000 r--p 00023000 08:05 6818399    /lib/libm-2.12.1.so
b6a37000-b6a38000 rw-p 00024000 08:05 6818399    /lib/libm-2.12.1.so
b6a38000-b70fc000 r-xp 00000000 08:05 6166515    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
b70fc000-b7141000 r--p 006c4000 08:05 6166515    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
b7141000-b7150000 rw-p 00709000 08:05 6166515    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
b7150000-b7571000 rw-p 00000000 00:00 0 
b7571000-b76c8000 r-xp 00000000 08:05 6818395    /lib/libc-2.12.1.so
b76c8000-b76ca000 r--p 00157000 08:05 6818395    /lib/libc-2.12.1.so
b76ca000-b76cb000 rw-p 00159000 08:05 6818395    /lib/libc-2.12.1.so
b76cb000-b76ce000 rw-p 00000000 00:00 0 
b76ce000-b76d0000 r-xp 00000000 08:05 6818398    /lib/libdl-2.12.1.so
b76d0000-b76d1000 r--p 00001000 08:05 6818398    /lib/libdl-2.12.1.so
b76d1000-b76d2000 rw-p 00002000 08:05 6818398    /lib/libdl-2.12.1.so
b76d2000-b76d5000 r-xp 00000000 08:05 6166505    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
b76d5000-b76d6000 r--p 00002000 08:05 6166505    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
b76d6000-b76d7000 rw-p 00003000 08:05 6166505    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
b76d7000-b76ec000 r-xp 00000000 08:05 6818409    /lib/libpthread-2.12.1.so
b76ec000-b76ed000 ---p 00015000 08:05 6818409    /lib/libpthread-2.12.1.so
b76ed000-b76ee000 r--p 00015000 08:05 6818409    /lib/libpthread-2.12.1.so
b76ee000-b76ef000 rw-p 00016000 08:05 6818409    /lib/libpthread-2.12.1.so
b76ef000-b76f2000 rw-p 00000000 00:00 0 
b76f2000-b7705000 r-xp 00000000 08:05 6815938    /lib/libz.so.1.2.3.4
b7705000-b7706000 r--p 00012000 08:05 6815938    /lib/libz.so.1.2.3.4
b7706000-b7707000 rw-p 00013000 08:05 6815938    /lib/libz.so.1.2.3.4
b7707000-b7709000 r--s 0001d000 08:05 6039343    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
b7709000-b770a000 rw-p 00000000 00:00 0 
b770a000-b770b000 r--p 00000000 00:00 0 
b770b000-b7716000 r-xp 00000000 08:05 6166524    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
b7716000-b7717000 ---p 0000b000 08:05 6166524    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
b7717000-b7718000 r--p 0000b000 08:05 6166524    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
b7718000-b7719000 rw-p 0000c000 08:05 6166524    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
b7719000-b771b000 rw-p 00000000 00:00 0 
b771b000-b771c000 r-xp 00000000 00:00 0          [vdso]
b771c000-b7738000 r-xp 00000000 08:05 6818392    /lib/ld-2.12.1.so
b7738000-b7739000 r--p 0001b000 08:05 6818392    /lib/ld-2.12.1.so
b7739000-b773a000 rw-p 0001c000 08:05 6818392    /lib/ld-2.12.1.so
bf9a2000-bf9c3000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
java_command: sun.applet.PluginMain /tmp/icedteaplugin-nyx/3499-icedteanp-plugin-to-appletviewer /tmp/icedteaplugin-nyx/3499-icedteanp-appletviewer-to-plugin
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=nyx
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x6497c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x6497c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x51ba60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x51ba60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x51ba60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x51b110], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x51dc80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x51dc80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x51dc80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x51dc80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.10 (maverick)
uname:Linux 2.6.35-28-generic-pae #49-Ubuntu SMP Tue Mar 1 14:58:06 UTC 2011 i686
libc:glibc 2.12.1 NPTL 2.12.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.00 1.01 1.05

/proc/meminfo:
MemTotal:        3981740 kB
MemFree:         1449492 kB
Buffers:          189076 kB
Cached:          1132512 kB
SwapCached:            0 kB
Active:          1432828 kB
Inactive:         939312 kB
Active(anon):    1051068 kB
Inactive(anon):     9776 kB
Active(file):     381760 kB
Inactive(file):   929536 kB
Unevictable:          32 kB
Mlocked:              32 kB
HighTotal:       3138364 kB
HighFree:         933520 kB
LowTotal:         843376 kB
LowFree:          515972 kB
SwapTotal:       5989372 kB
SwapFree:        5989372 kB
Dirty:              1608 kB
Writeback:             0 kB
AnonPages:       1051040 kB
Mapped:           153720 kB
Shmem:             10296 kB
Slab:              89464 kB
SReclaimable:      57136 kB
SUnreclaim:        32328 kB
KernelStack:        3720 kB
PageTables:         8460 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7980240 kB
Committed_AS:    2892144 kB
VmallocTotal:     122880 kB
VmallocUsed:       75348 kB
VmallocChunk:      29692 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       67576 kB
DirectMap2M:      845824 kB


CPU:total 4 (2 cores per cpu, 2 threads per core) family 6 model 37 stepping 5, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1, sse4.2, popcnt, ht

Memory: 4k page, physical 3981740k(1449492k free), swap 5989372k(5989372k free)

vm_info: OpenJDK Server VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Feb 23 2011 09:09:10 by "buildd" with gcc 4.4.5

time: Sun Mar 20 21:04:57 2011
elapsed time: 4 seconds


```

I have several similar error logs.

---

### Post by r-senior on 2011-03-21
It means the Java plugin in your web browser crashed.

What were you doing, trying to run a web page that has a Java applet on it?

Is it repeatable? In other words, is there a particular site you visit that doesn't work and then you notice another log?

You can safely delete them if you don't plan on reporting the bug using the link it gives.

---

### Post by Guenhwyvar on 2011-03-21
Thank you, I think it is my uni's website. Unavoidable really, but at least I know I can delete them.

---

