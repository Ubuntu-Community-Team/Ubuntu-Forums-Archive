---
title: "Java Runtime Error"
date: 2011-07-25
forum: General Help
---

### Post by nd456 on 2011-07-25
Hello, i was running a minecraft server on ubuntu when it crashed and now im unable to start the shell script...
The error code was as follows:
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0x00b91541, pid=18683, tid=3031927664
#
# JRE version: 6.0_22-b22
# Java VM: OpenJDK Client VM (20.0-b11 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.10.1
# Distribution: Ubuntu Natty (development branch), package 6b22-1.10.1-0ubuntu1
# Problematic frame:
# C  [libzip.so+0x4541]  Java_java_util_zip_ZipEntry_initFields+0xfa1
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x08c00400):  JavaThread "Server thread" [_thread_in_native, id=18704, stack(0xb4b28000,0xb4b79000)]

siginfo:si_signo=SIGBUS: si_errno=0, si_code=2 (BUS_ADRERR), si_addr=0xb4be00be

Registers:
EAX=0x08b50f28, EBX=0x00b93ff4, ECX=0xb4700010, EDX=0xb4200000
ESP=0xb4b765b0, EBP=0xb4b765f8, ESI=0xb4be00a1, EDI=0xb42dd748
EIP=0x00b91541, EFLAGS=0x00010282, CR2=0xb4be00be

Top of Stack: (sp=0xb4b765b0)
0xb4b765b0:   00000030 08b50f28 b4b765d8 00e17c20
0xb4b765c0:   08b50fe0 00000019 08c04748 00e17bfc
0xb4b765d0:   0101fff4 b42dd748 08b50f28 00b91950
0xb4b765e0:   08b50fe0 08c04750 00b914fd 00b93ff4
0xb4b765f0:   08b52758 08b50f28 b4b76638 00b91f22
0xb4b76600:   0b75cfa8 b4b7668a 08c00400 00000000
0xb4b76610:   00000000 d7985162 08cc4eb0 d1b452a3
0xb4b76620:   08af2738 b577be14 00000019 00b93ff4 

Instructions: (pc=0x00b91541)
0x00b91521:   00 c7 00 00 00 00 00 c7 40 24 00 00 00 00 c7 40
0x00b91531:   20 00 00 00 00 8b 45 e0 8b 36 2b 70 1c 03 70 10
0x00b91541:   0f b6 56 1d 0f b6 46 1c c1 e2 08 09 c2 89 55 e4
0x00b91551:   0f b6 4e 1e 88 4d d7 0f b6 46 1f 88 45 d6 0f b6 

Register to memory mapping:

EAX=0x08b50f28 is an unknown value
EBX=0x00b93ff4: <offset 0x6ff4> in /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so at 0x00b8d000
ECX=0xb4700010 is an unknown value
EDX=0xb4200000 is an unknown value
ESP=0xb4b765b0 is pointing into the stack for thread: 0x08c00400
EBP=0xb4b765f8 is pointing into the stack for thread: 0x08c00400
ESI=0xb4be00a1 is an unknown value
EDI=0xb42dd748 is an unknown value


Stack: [0xb4b28000,0xb4b79000],  sp=0xb4b765b0,  free space=313k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libzip.so+0x4541]  Java_java_util_zip_ZipEntry_initFields+0xfa1
C  [libzip.so+0x4f22]  ZIP_GetEntry+0xb2
C  [libzip.so+0x2fdd]  Java_java_util_zip_ZipFile_getEntry+0xfd
J  java.util.zip.ZipFile.getEntry(JLjava/lang/String;Z)J
J  java.util.zip.ZipFile.getEntry(Ljava/lang/String;)Ljava/util/zip/ZipEntry;
V  [libjvm.so+0x20a6a2]  JavaCalls::call_helper(JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x262
V  [libjvm.so+0x3044b9]  os::os_exception_wrapper(void (*)(JavaValue*, methodHandle*, JavaCallArguments*, Thread*), JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x19
V  [libjvm.so+0x209b9f]  JavaCalls::call(JavaValue*, methodHandle, JavaCallArguments*, Thread*)+0x2f
V  [libjvm.so+0x23e6fe]  JVM_DoPrivileged+0x1fe
C  [libjava.so+0x9d2a]  Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedExceptionAction_2Ljava_security_AccessControlContext_2+0x3a
J  java.security.AccessController.doPrivileged(Ljava/security/PrivilegedExceptionAction;Ljava/security/AccessControlContext;)Ljava/lang/Object;
J  java.net.URLClassLoader.findClass(Ljava/lang/String;)Ljava/lang/Class;
V  [libjvm.so+0x20a6a2]  JavaCalls::call_helper(JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x262
V  [libjvm.so+0x3044b9]  os::os_exception_wrapper(void (*)(JavaValue*, methodHandle*, JavaCallArguments*, Thread*), JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x19
V  [libjvm.so+0x209b9f]  JavaCalls::call(JavaValue*, methodHandle, JavaCallArguments*, Thread*)+0x2f
V  [libjvm.so+0x20a01a]  JavaCalls::call_virtual(JavaValue*, KlassHandle, symbolHandle, symbolHandle, JavaCallArguments*, Thread*)+0xea
V  [libjvm.so+0x20a112]  JavaCalls::call_virtual(JavaValue*, Handle, KlassHandle, symbolHandle, symbolHandle, Handle, Thread*)+0x62
V  [libjvm.so+0x37f39f]  SystemDictionary::load_instance_class(symbolHandle, Handle, Thread*)+0x52f
V  [libjvm.so+0x37db0d]  SystemDictionary::resolve_instance_class_or_null(symbolHandle, Handle, Handle, Thread*)+0x70d
V  [libjvm.so+0x37e334]  SystemDictionary::resolve_or_null(symbolHandle, Handle, Handle, Thread*)+0x44
V  [libjvm.so+0x37f900]  SystemDictionary::resolve_or_fail(symbolHandle, Handle, Handle, bool, Thread*)+0x30
V  [libjvm.so+0x335ac0]  get_mirror_from_signature(methodHandle, SignatureStream*, Thread*)+0xd0
V  [libjvm.so+0x335c5d]  Reflection::get_parameter_types(methodHandle, int, oopDesc**, Thread*)+0x16d
V  [libjvm.so+0x33686c]  Reflection::new_constructor(methodHandle, Thread*)+0xec
V  [libjvm.so+0x2405bf]  JVM_GetClassDeclaredConstructors+0x27f
j  java.lang.Class.getDeclaredConstructors0(Z)[Ljava/lang/reflect/Constructor;+0
J  java.lang.Class.privateGetDeclaredConstructors(Z)[Ljava/lang/reflect/Constructor;
j  net.minecraft.server.EntitySheep.q()V+33
j  net.minecraft.server.EntityLiving.die(Lnet/minecraft/server/Entity;)V+45
J  net.minecraft.server.EntityLiving.damageEntity(Lnet/minecraft/server/Entity;I)Z
j  net.minecraft.server.EntityWolf.a(Lnet/minecraft/server/Entity;F)V+258
J  net.minecraft.server.EntityCreature.c_()V
v  ~StubRoutines::call_stub
V  [libjvm.so+0x20a6a2]  JavaCalls::call_helper(JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x262
V  [libjvm.so+0x3044b9]  os::os_exception_wrapper(void (*)(JavaValue*, methodHandle*, JavaCallArguments*, Thread*), JavaValue*, methodHandle*, JavaCallArguments*, Thread*)+0x19
V  [libjvm.so+0x209b9f]  JavaCalls::call(JavaValue*, methodHandle, JavaCallArguments*, Thread*)+0x2f
V  [libjvm.so+0x20a01a]  JavaCalls::call_virtual(JavaValue*, KlassHandle, symbolHandle, symbolHandle, JavaCallArguments*, Thread*)+0xea
V  [libjvm.so+0x20a178]  JavaCalls::call_virtual(JavaValue*, Handle, KlassHandle, symbolHandle, symbolHandle, Thread*)+0x58
V  [libjvm.so+0x23b5df]  thread_entry(JavaThread*, Thread*)+0x7f
V  [libjvm.so+0x3af16c]  JavaThread::thread_main_inner()+0x6c
V  [libjvm.so+0x3af249]  JavaThread::run()+0xc9
V  [libjvm.so+0x3025a1]  java_start(Thread*)+0x121
C  [libpthread.so.0+0x5e99]  start_thread+0xd9

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
J  java.util.zip.ZipFile.getEntry(JLjava/lang/String;Z)J
J  java.util.zip.ZipFile.getEntry(Ljava/lang/String;)Ljava/util/zip/ZipEntry;
J  java.util.jar.JarFile.getEntry(Ljava/lang/String;)Ljava/util/zip/ZipEntry;
J  sun.misc.URLClassPath$JarLoader.getResource(Ljava/lang/String;Z)Lsun/misc/Resource;
J  sun.misc.URLClassPath.getResource(Ljava/lang/String;Z)Lsun/misc/Resource;
J  java.net.URLClassLoader$1.run()Ljava/lang/Object;
v  ~StubRoutines::call_stub
J  java.security.AccessController.doPrivileged(Ljava/security/PrivilegedExceptionAction;Ljava/security/AccessControlContext;)Ljava/lang/Object;
J  java.net.URLClassLoader.findClass(Ljava/lang/String;)Ljava/lang/Class;
J  java.lang.ClassLoader.loadClass(Ljava/lang/String;Z)Ljava/lang/Class;
J  sun.misc.Launcher$AppClassLoader.loadClass(Ljava/lang/String;Z)Ljava/lang/Class;
J  java.lang.ClassLoader.loadClass(Ljava/lang/String;)Ljava/lang/Class;
v  ~StubRoutines::call_stub
j  java.lang.Class.getDeclaredConstructors0(Z)[Ljava/lang/reflect/Constructor;+0
J  java.lang.Class.privateGetDeclaredConstructors(Z)[Ljava/lang/reflect/Constructor;
J  java.lang.Class.getConstructor0([Ljava/lang/Class;I)Ljava/lang/reflect/Constructor;
J  org.bukkit.Material.getNewData(B)Lorg/bukkit/material/MaterialData;
J  org.bukkit.inventory.ItemStack.createData(B)V
J  org.bukkit.inventory.ItemStack.<init>(IISLjava/lang/Byte;)V
j  org.bukkit.inventory.ItemStack.<init>(Lorg/bukkit/Material;ISLjava/lang/Byte;)V+9
j  net.minecraft.server.EntitySheep.q()V+33
j  net.minecraft.server.EntityLiving.die(Lnet/minecraft/server/Entity;)V+45
J  net.minecraft.server.EntityLiving.damageEntity(Lnet/minecraft/server/Entity;I)Z
j  net.minecraft.server.EntitySheep.damageEntity(Lnet/minecraft/server/Entity;I)Z+3
j  net.minecraft.server.EntityWolf.a(Lnet/minecraft/server/Entity;F)V+258
J  net.minecraft.server.EntityCreature.c_()V
J  net.minecraft.server.EntityWolf.c_()V
J  net.minecraft.server.EntityLiving.v()V
J  net.minecraft.server.EntityWolf.v()V
J  net.minecraft.server.EntityLiving.m_()V
J  net.minecraft.server.EntityWolf.m_()V
J  net.minecraft.server.World.entityJoinedWorld(Lnet/minecraft/server/Entity;Z)V
J  net.minecraft.server.WorldServer.entityJoinedWorld(Lnet/minecraft/server/Entity;Z)V
J  net.minecraft.server.World.cleanUp()V
J  net.minecraft.server.MinecraftServer.h()V
J  net.minecraft.server.MinecraftServer.run()V
j  net.minecraft.server.ThreadServerApplication.run()V+4
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0bd0d000 JavaThread "Connection #11 write thread" [_thread_blocked, id=26513, stack(0xb43d6000,0xb4427000)]
  0x0bd0c800 JavaThread "Connection #11 read thread" [_thread_in_native, id=26512, stack(0xb3faf000,0xb4000000)]
  0x0b77c400 JavaThread "Connection #10 write thread" [_thread_blocked, id=26248, stack(0xb44c9000,0xb451a000)]
  0x0bccc800 JavaThread "Connection #10 read thread" [_thread_in_native, id=26247, stack(0xb451a000,0xb456b000)]
  0x0bcbbc00 JavaThread "com.google.common.base.internal.Finalizer" daemon [_thread_blocked, id=18720, stack(0xb45bc000,0xb460d000)]
  0x0bcb7c00 JavaThread "pool-1-thread-1" [_thread_blocked, id=18718, stack(0xb460d000,0xb465e000)]
  0x0bc97c00 JavaThread "com.mchange.v2.async.ThreadPoolAsynchronousRunner$PoolThread-#2" daemon [_thread_blocked, id=18717, stack(0xb465e000,0xb46af000)]
  0x08d5b400 JavaThread "com.mchange.v2.async.ThreadPoolAsynchronousRunner$PoolThread-#1" daemon [_thread_blocked, id=18716, stack(0xb46af000,0xb4700000)]
  0x0bc86800 JavaThread "com.mchange.v2.async.ThreadPoolAsynchronousRunner$PoolThread-#0" daemon [_thread_blocked, id=18715, stack(0xb4802000,0xb4853000)]
  0x0bc88800 JavaThread "Timer-0" daemon [_thread_blocked, id=18714, stack(0xb4853000,0xb48a4000)]
  0x0bc7d000 JavaThread "H2 Log Writer BIGBROTHER" daemon [_thread_blocked, id=18713, stack(0xb48a4000,0xb48f5000)]
  0x0bc5f800 JavaThread "H2 File Lock Watchdog /home/andy/Desktop/Server/1.7.3/plugins/BigBrother/bigbrother.lock.db" daemon [_thread_blocked, id=18712, stack(0xb48f5000,0xb4946000)]
  0x0bc4cc00 JavaThread "Thread-6" [_thread_blocked, id=18710, stack(0xb4997000,0xb49e8000)]
  0x08c10c00 JavaThread "Thread-5" [_thread_blocked, id=18707, stack(0xb4a32000,0xb4a83000)]
  0x08c02000 JavaThread "Listen thread" [_thread_in_native, id=18706, stack(0xb4a83000,0xb4ad4000)]
  0x08c00c00 JavaThread "Thread-4" daemon [_thread_in_native, id=18705, stack(0xb4ad7000,0xb4b28000)]
  0x08af8000 JavaThread "DestroyJavaVM" [_thread_blocked, id=18685, stack(0xb7779000,0xb77ca000)]
=>0x08c00400 JavaThread "Server thread" [_thread_in_native, id=18704, stack(0xb4b28000,0xb4b79000)]
  0x08bf5c00 JavaThread "Thread-1" daemon [_thread_blocked, id=18694, stack(0xb4b79000,0xb4bca000)]
  0x08b32800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=18691, stack(0xb4cb2000,0xb4d03000)]
  0x08b30800 JavaThread "C1 CompilerThread0" daemon [_thread_blocked, id=18690, stack(0xb4d03000,0xb4d84000)]
  0x08b2f000 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=18689, stack(0xb4d84000,0xb4dd5000)]
  0x08b27800 JavaThread "Finalizer" daemon [_thread_blocked, id=18688, stack(0xb4fd6000,0xb5027000)]
  0x08b26000 JavaThread "Reference Handler" daemon [_thread_blocked, id=18687, stack(0xb5027000,0xb5078000)]

Other Threads:
  0x08b24400 VMThread [stack: 0xb5078000,0xb50f9000] [id=18686]
  0x08b3e800 WatcherThread [stack: 0xb4c31000,0xb4cb2000] [id=18692]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 368640K, used 103694K [0x449b0000, 0x5d9b0000, 0x5d9b0000)
  eden space 327680K,  22% used [0x449b0000, 0x490c4c28, 0x589b0000)
  from space 40960K,  75% used [0x5b1b0000, 0x5cfdecd0, 0x5d9b0000)
  to   space 40960K,   0% used [0x589b0000, 0x589b0000, 0x5b1b0000)
 tenured generation   total 819200K, used 496217K [0x5d9b0000, 0x8f9b0000, 0x8f9b0000)
   the space 819200K,  60% used [0x5d9b0000, 0x7be467b8, 0x7be46800, 0x8f9b0000)
 compacting perm gen  total 13056K, used 12905K [0x8f9b0000, 0x90670000, 0x939b0000)
   the space 13056K,  98% used [0x8f9b0000, 0x9064a5e0, 0x9064a600, 0x90670000)
    ro space 10240K,  73% used [0x939b0000, 0x9410f468, 0x9410f600, 0x943b0000)
    rw space 12288K,  60% used [0x943b0000, 0x94af9648, 0x94af9800, 0x94fb0000)

Code Cache  [0xb5779000, 0xb5c51000, 0xb7779000)
 total_blobs=2773 nmethods=2565 adapters=143 free_code_cache=28480960 largest_free_block=256

Dynamic libraries:
00110000-00117000 r-xp 00000000 08:01 263046     /lib/i386-linux-gnu/librt-2.13.so
00117000-00118000 r--p 00006000 08:01 263046     /lib/i386-linux-gnu/librt-2.13.so
00118000-00119000 rw-p 00007000 08:01 263046     /lib/i386-linux-gnu/librt-2.13.so
00119000-0012c000 r-xp 00000000 08:01 263017     /lib/i386-linux-gnu/libnsl-2.13.so
0012c000-0012d000 r--p 00012000 08:01 263017     /lib/i386-linux-gnu/libnsl-2.13.so
0012d000-0012e000 rw-p 00013000 08:01 263017     /lib/i386-linux-gnu/libnsl-2.13.so
0012e000-00130000 rw-p 00000000 00:00 0 
00130000-00139000 r-xp 00000000 08:01 263027     /lib/i386-linux-gnu/libnss_nis-2.13.so
00139000-0013a000 r--p 00008000 08:01 263027     /lib/i386-linux-gnu/libnss_nis-2.13.so
0013a000-0013b000 rw-p 00009000 08:01 263027     /lib/i386-linux-gnu/libnss_nis-2.13.so
0013b000-00145000 r-xp 00000000 08:01 263023     /lib/i386-linux-gnu/libnss_files-2.13.so
00145000-00146000 r--p 00009000 08:01 263023     /lib/i386-linux-gnu/libnss_files-2.13.so
00146000-00147000 rw-p 0000a000 08:01 263023     /lib/i386-linux-gnu/libnss_files-2.13.so
00147000-00149000 r-xp 00000000 08:01 262212     /lib/libnss_mdns4_minimal.so.2
00149000-0014a000 r--p 00001000 08:01 262212     /lib/libnss_mdns4_minimal.so.2
0014a000-0014b000 rw-p 00002000 08:01 262212     /lib/libnss_mdns4_minimal.so.2
0014b000-0015c000 r-xp 00000000 08:01 263044     /lib/i386-linux-gnu/libresolv-2.13.so
0015c000-0015d000 r--p 00010000 08:01 263044     /lib/i386-linux-gnu/libresolv-2.13.so
0015d000-0015e000 rw-p 00011000 08:01 263044     /lib/i386-linux-gnu/libresolv-2.13.so
0015e000-00160000 rw-p 00000000 00:00 0 
00160000-00168000 r-xp 00000000 08:01 4593915    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00168000-00169000 r--p 00007000 08:01 4593915    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00169000-0016a000 rw-p 00008000 08:01 4593915    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
0016d000-00170000 r-xp 00000000 08:01 4596640    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00170000-00171000 r--p 00002000 08:01 4596640    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00171000-00172000 rw-p 00003000 08:01 4596640    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00172000-00176000 r-xp 00000000 08:01 4591186    /usr/lib/libXtst.so.6.1.0
00176000-00177000 r--p 00003000 08:01 4591186    /usr/lib/libXtst.so.6.1.0
00177000-00178000 rw-p 00004000 08:01 4591186    /usr/lib/libXtst.so.6.1.0
00178000-0018f000 r-xp 00000000 08:01 4594041    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
0018f000-00190000 r--p 00016000 08:01 4594041    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00190000-00191000 rw-p 00017000 08:01 4594041    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00191000-00193000 r-xp 00000000 08:01 4593893    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00193000-00194000 r--p 00001000 08:01 4593893    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00194000-00195000 rw-p 00002000 08:01 4593893    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00195000-00199000 r-xp 00000000 08:01 4593901    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
00199000-0019a000 r--p 00003000 08:01 4593901    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0019a000-0019b000 rw-p 00004000 08:01 4593901    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
001ab000-001be000 r-xp 00000000 08:01 263060     /lib/i386-linux-gnu/libz.so.1.2.3.4
001be000-001bf000 r--p 00012000 08:01 263060     /lib/i386-linux-gnu/libz.so.1.2.3.4
001bf000-001c0000 rw-p 00013000 08:01 263060     /lib/i386-linux-gnu/libz.so.1.2.3.4
00206000-00229000 r-xp 00000000 08:01 4597129    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00229000-0022a000 r--p 00022000 08:01 4597129    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0022a000-0022c000 rw-p 00023000 08:01 4597129    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00244000-00259000 r-xp 00000000 08:01 263042     /lib/i386-linux-gnu/libpthread-2.13.so
00259000-0025a000 r--p 00015000 08:01 263042     /lib/i386-linux-gnu/libpthread-2.13.so
0025a000-0025b000 rw-p 00016000 08:01 263042     /lib/i386-linux-gnu/libpthread-2.13.so
0025b000-0025d000 rw-p 00000000 00:00 0 
0025d000-002a0000 r-xp 00000000 08:01 4597607    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
002a0000-002a1000 r--p 00042000 08:01 4597607    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
002a1000-002a3000 rw-p 00043000 08:01 4597607    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
002a3000-002a4000 rw-p 00000000 00:00 0 
002fb000-00455000 r-xp 00000000 08:01 262977     /lib/i386-linux-gnu/libc-2.13.so
00455000-00456000 ---p 0015a000 08:01 262977     /lib/i386-linux-gnu/libc-2.13.so
00456000-00458000 r--p 0015a000 08:01 262977     /lib/i386-linux-gnu/libc-2.13.so
00458000-00459000 rw-p 0015c000 08:01 262977     /lib/i386-linux-gnu/libc-2.13.so
00459000-0045c000 rw-p 00000000 00:00 0 
004a1000-004c5000 r-xp 00000000 08:01 263014     /lib/i386-linux-gnu/libm-2.13.so
004c5000-004c6000 r--p 00023000 08:01 263014     /lib/i386-linux-gnu/libm-2.13.so
004c6000-004c7000 rw-p 00024000 08:01 263014     /lib/i386-linux-gnu/libm-2.13.so
004d3000-004de000 r-xp 00000000 08:01 4597145    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
004de000-004df000 ---p 0000b000 08:01 4597145    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
004df000-004e0000 r--p 0000b000 08:01 4597145    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
004e0000-004e1000 rw-p 0000c000 08:01 4597145    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
004e1000-0056a000 r-xp 00000000 08:01 4596643    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
0056a000-0056b000 r--p 00088000 08:01 4596643    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
0056b000-00572000 rw-p 00089000 08:01 4596643    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00572000-00596000 rw-p 00000000 00:00 0 
005b8000-005ba000 r-xp 00000000 08:01 262987     /lib/i386-linux-gnu/libdl-2.13.so
005ba000-005bb000 r--p 00001000 08:01 262987     /lib/i386-linux-gnu/libdl-2.13.so
005bb000-005bc000 rw-p 00002000 08:01 262987     /lib/i386-linux-gnu/libdl-2.13.so
005f3000-0060d000 r-xp 00000000 08:01 263005     /lib/i386-linux-gnu/libgcc_s.so.1
0060d000-0060e000 r--p 00019000 08:01 263005     /lib/i386-linux-gnu/libgcc_s.so.1
0060e000-0060f000 rw-p 0001a000 08:01 263005     /lib/i386-linux-gnu/libgcc_s.so.1
00657000-00673000 r-xp 00000000 08:01 262964     /lib/i386-linux-gnu/ld-2.13.so
00673000-00674000 r--p 0001b000 08:01 262964     /lib/i386-linux-gnu/ld-2.13.so
00674000-00675000 rw-p 0001c000 08:01 262964     /lib/i386-linux-gnu/ld-2.13.so
0072f000-00735000 r-xp 00000000 08:01 263019     /lib/i386-linux-gnu/libnss_compat-2.13.so
00735000-00736000 r--p 00005000 08:01 263019     /lib/i386-linux-gnu/libnss_compat-2.13.so
00736000-00737000 rw-p 00006000 08:01 263019     /lib/i386-linux-gnu/libnss_compat-2.13.so
00750000-0082f000 r-xp 00000000 08:01 4594024    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
0082f000-00833000 r--p 000de000 08:01 4594024    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
00833000-00834000 rw-p 000e2000 08:01 4594024    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.14
00834000-0083b000 rw-p 00000000 00:00 0 
008d7000-008e4000 r-xp 00000000 08:01 4593903    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
008e4000-008e5000 r--p 0000c000 08:01 4593903    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
008e5000-008e6000 rw-p 0000d000 08:01 4593903    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0098d000-00993000 r-xp 00000000 08:01 4597137    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmanagement.so
00993000-00994000 r--p 00005000 08:01 4597137    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmanagement.so
00994000-00995000 rw-p 00006000 08:01 4597137    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libmanagement.so
009a5000-009ac000 r-xp 00000000 08:01 4597140    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
009ac000-009ad000 r--p 00006000 08:01 4597140    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
009ad000-009ae000 rw-p 00007000 08:01 4597140    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
009ba000-009be000 r-xp 00000000 08:01 263021     /lib/i386-linux-gnu/libnss_dns-2.13.so
009be000-009bf000 r--p 00004000 08:01 263021     /lib/i386-linux-gnu/libnss_dns-2.13.so
009bf000-009c0000 rw-p 00005000 08:01 263021     /lib/i386-linux-gnu/libnss_dns-2.13.so
00a12000-00a25000 r-xp 00000000 08:01 4597139    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00a25000-00a26000 r--p 00013000 08:01 4597139    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00a26000-00a27000 rw-p 00014000 08:01 4597139    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00a27000-00b3d000 r-xp 00000000 08:01 4593891    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00b3d000-00b3e000 ---p 00116000 08:01 4593891    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00b3e000-00b3f000 r--p 00116000 08:01 4593891    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00b3f000-00b41000 rw-p 00117000 08:01 4593891    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00b41000-00b42000 rw-p 00000000 00:00 0 
00b55000-00b62000 r-xp 00000000 08:01 4593909    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00b62000-00b63000 r--p 0000c000 08:01 4593909    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00b63000-00b64000 rw-p 0000d000 08:01 4593909    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00b8d000-00b93000 r-xp 00000000 08:01 4597146    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00b93000-00b94000 r--p 00005000 08:01 4597146    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00b94000-00b95000 rw-p 00006000 08:01 4597146    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00bce000-00bcf000 r-xp 00000000 00:00 0          [vdso]
00bcf000-01009000 r-xp 00000000 08:01 4595735    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01009000-01020000 r--p 0043a000 08:01 4595735    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01020000-0102d000 rw-p 00451000 08:01 4595735    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0102d000-01445000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 08:01 4597178    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:01 4597178    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:01 4597178    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08af1000-0cdf7000 rw-p 00000000 00:00 0          [heap]
449b0000-90670000 rw-p 00000000 00:00 0 
90670000-939b0000 rw-p 00000000 00:00 0 
939b0000-94110000 r--s 00001000 08:01 4597643    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94110000-943b0000 rw-p 00000000 00:00 0 
943b0000-94afa000 rw-p 00761000 08:01 4597643    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94afa000-94fb0000 rw-p 00000000 00:00 0 
94fb0000-950ac000 rw-p 00eab000 08:01 4597643    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
950ac000-953b0000 rw-p 00000000 00:00 0 
953b0000-953b8000 r-xs 00fa7000 08:01 4597643    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
953b8000-957b0000 rw-p 00000000 00:00 0 
afa00000-afafe000 rw-p 00000000 00:00 0 
afafe000-afb00000 ---p 00000000 00:00 0 
afb00000-afbfe000 rw-p 00000000 00:00 0 
afbfe000-afc00000 ---p 00000000 00:00 0 
afc00000-afcfe000 rw-p 00000000 00:00 0 
afcfe000-afd00000 ---p 00000000 00:00 0 
afe00000-afefe000 rw-p 00000000 00:00 0 
afefe000-aff00000 ---p 00000000 00:00 0 
aff00000-afffe000 rw-p 00000000 00:00 0 
afffe000-b0000000 ---p 00000000 00:00 0 
b0000000-b00fe000 rw-p 00000000 00:00 0 
b00fe000-b0100000 ---p 00000000 00:00 0 
b0100000-b01fe000 rw-p 00000000 00:00 0 
b01fe000-b0200000 ---p 00000000 00:00 0 
b0200000-b02fe000 rw-p 00000000 00:00 0 
b02fe000-b0300000 ---p 00000000 00:00 0 
b0300000-b03fe000 rw-p 00000000 00:00 0 
b03fe000-b0400000 ---p 00000000 00:00 0 
b0400000-b04fe000 rw-p 00000000 00:00 0 
b04fe000-b0500000 ---p 00000000 00:00 0 
b0600000-b06ff000 rw-p 00000000 00:00 0 
b06ff000-b0700000 ---p 00000000 00:00 0 
b0700000-b07fe000 rw-p 00000000 00:00 0 
b07fe000-b0800000 ---p 00000000 00:00 0 
b0800000-b08ff000 rw-p 00000000 00:00 0 
b08ff000-b0900000 ---p 00000000 00:00 0 
b0a00000-b0aff000 rw-p 00000000 00:00 0 
b0aff000-b0b00000 ---p 00000000 00:00 0 
b0c00000-b0cfe000 rw-p 00000000 00:00 0 
b0cfe000-b0d00000 ---p 00000000 00:00 0 
b0d00000-b0dfc000 rw-p 00000000 00:00 0 
b0dfc000-b0e00000 ---p 00000000 00:00 0 
b0e00000-b0efe000 rw-p 00000000 00:00 0 
b0efe000-b0f00000 ---p 00000000 00:00 0 
b0f00000-b0ffe000 rw-p 00000000 00:00 0 
b0ffe000-b1000000 ---p 00000000 00:00 0 
b1000000-b10fe000 rw-p 00000000 00:00 0 
b10fe000-b1100000 ---p 00000000 00:00 0 
b1100000-b11fe000 rw-p 00000000 00:00 0 
b11fe000-b1200000 ---p 00000000 00:00 0 
b1200000-b12fe000 rw-p 00000000 00:00 0 
b12fe000-b1300000 ---p 00000000 00:00 0 
b1300000-b13fe000 rw-p 00000000 00:00 0 
b13fe000-b1400000 ---p 00000000 00:00 0 
b1400000-b14fe000 rw-p 00000000 00:00 0 
b14fe000-b1500000 ---p 00000000 00:00 0 
b1500000-b15fe000 rw-p 00000000 00:00 0 
b15fe000-b1600000 ---p 00000000 00:00 0 
b1600000-b16fe000 rw-p 00000000 00:00 0 
b16fe000-b1700000 ---p 00000000 00:00 0 
b1800000-b18fe000 rw-p 00000000 00:00 0 
b18fe000-b1900000 ---p 00000000 00:00 0 
b1900000-b1a00000 rw-p 00000000 00:00 0 
b1a00000-b1aff000 rw-p 00000000 00:00 0 
b1aff000-b1b00000 ---p 00000000 00:00 0 
b1c00000-b1cf1000 rw-p 00000000 00:00 0 
b1cf1000-b1d00000 ---p 00000000 00:00 0 
b1d00000-b1dff000 rw-p 00000000 00:00 0 
b1dff000-b1e00000 ---p 00000000 00:00 0 
b1e00000-b1eff000 rw-p 00000000 00:00 0 
b1eff000-b1f00000 ---p 00000000 00:00 0 
b1f00000-b1ffe000 rw-p 00000000 00:00 0 
b1ffe000-b2000000 ---p 00000000 00:00 0 
b2000000-b2100000 rw-p 00000000 00:00 0 
b2200000-b22fe000 rw-p 00000000 00:00 0 
b22fe000-b2300000 ---p 00000000 00:00 0 
b2300000-b23f7000 rw-p 00000000 00:00 0 
b23f7000-b2400000 ---p 00000000 00:00 0 
b2400000-b2500000 rw-p 00000000 00:00 0 
b2600000-b26fd000 rw-p 00000000 00:00 0 
b26fd000-b2700000 ---p 00000000 00:00 0 
b2700000-b27fe000 rw-p 00000000 00:00 0 
b27fe000-b2800000 ---p 00000000 00:00 0 
b2800000-b28fe000 rw-p 00000000 00:00 0 
b28fe000-b2900000 ---p 00000000 00:00 0 
b2a00000-b2afa000 rw-p 00000000 00:00 0 
b2afa000-b2b00000 ---p 00000000 00:00 0 
b2c00000-b2cfe000 rw-p 00000000 00:00 0 
b2cfe000-b2d00000 ---p 00000000 00:00 0 
b2d00000-b2dfe000 rw-p 00000000 00:00 0 
b2dfe000-b2e00000 ---p 00000000 00:00 0 
b2e00000-b2efe000 rw-p 00000000 00:00 0 
b2efe000-b2f00000 ---p 00000000 00:00 0 
b2f00000-b3000000 rw-p 00000000 00:00 0 
b3000000-b31fd000 rw-p 00000000 00:00 0 
b31fd000-b3200000 ---p 00000000 00:00 0 
b3200000-b32fc000 rw-p 00000000 00:00 0 
b32fc000-b3300000 ---p 00000000 00:00 0 
b3400000-b34fe000 rw-p 00000000 00:00 0 
b34fe000-b3500000 ---p 00000000 00:00 0 
b3500000-b35fa000 rw-p 00000000 00:00 0 
b35fa000-b3600000 ---p 00000000 00:00 0 
b3600000-b3700000 rw-p 00000000 00:00 0 
b3800000-b38ff000 rw-p 00000000 00:00 0 
b38ff000-b3900000 ---p 00000000 00:00 0 
b3a00000-b3b00000 rw-p 00000000 00:00 0 
b3c00000-b3d00000 rw-p 00000000 00:00 0 
b3e00000-b3f00000 rw-p 00000000 00:00 0 
b3f5e000-b3f61000 ---p 00000000 00:00 0 
b3f61000-b3faf000 rw-p 00000000 00:00 0 
b3faf000-b3fb2000 ---p 00000000 00:00 0 
b3fb2000-b4000000 rw-p 00000000 00:00 0 
b4000000-b40f1000 rw-p 00000000 00:00 0 
b40f1000-b4100000 ---p 00000000 00:00 0 
b4100000-b41fe000 rw-p 00000000 00:00 0 
b41fe000-b4200000 ---p 00000000 00:00 0 
b4200000-b4300000 rw-p 00000000 00:00 0 
b4334000-b4337000 ---p 00000000 00:00 0 
b4337000-b4385000 rw-p 00000000 00:00 0 
b4385000-b4388000 ---p 00000000 00:00 0 
b4388000-b43d6000 rw-p 00000000 00:00 0 
b43d6000-b43d9000 ---p 00000000 00:00 0 
b43d9000-b4427000 rw-p 00000000 00:00 0 
b4427000-b442a000 ---p 00000000 00:00 0 
b442a000-b4478000 rw-p 00000000 00:00 0 
b4478000-b447b000 ---p 00000000 00:00 0 
b447b000-b44c9000 rw-p 00000000 00:00 0 
b44c9000-b44cc000 ---p 00000000 00:00 0 
b44cc000-b451a000 rw-p 00000000 00:00 0 
b451a000-b451d000 ---p 00000000 00:00 0 
b451d000-b456b000 rw-p 00000000 00:00 0 
b456b000-b456e000 ---p 00000000 00:00 0 
b456e000-b45bc000 rw-p 00000000 00:00 0 
b45bc000-b45bf000 ---p 00000000 00:00 0 
b45bf000-b460d000 rw-p 00000000 00:00 0 
b460d000-b4610000 ---p 00000000 00:00 0 
b4610000-b465e000 rw-p 00000000 00:00 0 
b465e000-b4661000 ---p 00000000 00:00 0 
b4661000-b46af000 rw-p 00000000 00:00 0 
b46af000-b46b2000 ---p 00000000 00:00 0 
b46b2000-b4700000 rw-p 00000000 00:00 0 
b4700000-b47ff000 rw-p 00000000 00:00 0 
b47ff000-b4800000 ---p 00000000 00:00 0 
b4802000-b4805000 ---p 00000000 00:00 0 
b4805000-b4853000 rw-p 00000000 00:00 0 
b4853000-b4856000 ---p 00000000 00:00 0 
b4856000-b48a4000 rw-p 00000000 00:00 0 
b48a4000-b48a7000 ---p 00000000 00:00 0 
b48a7000-b48f5000 rw-p 00000000 00:00 0 
b48f5000-b48f8000 ---p 00000000 00:00 0 
b48f8000-b4946000 rw-p 00000000 00:00 0 
b4946000-b4949000 ---p 00000000 00:00 0 
b4949000-b4997000 rw-p 00000000 00:00 0 
b4997000-b499a000 ---p 00000000 00:00 0 
b499a000-b49e8000 rw-p 00000000 00:00 0 
b49e8000-b49e9000 r--s 0003e000 08:01 669851     /home/andy/Desktop/Server/1.7.3/plugins/EssentialsGeoIP.jar
b49e9000-b49ea000 r--s 00001000 08:01 669850     /home/andy/Desktop/Server/1.7.3/plugins/EssentialsChat.jar
b49ea000-b49ec000 r--s 00007000 08:01 669797     /home/andy/Desktop/Server/1.7.3/plugins/VanishNoPickup.jar
b49ec000-b49f3000 r--s 00049000 08:01 669856     /home/andy/Desktop/Server/1.7.3/plugins/EssentialsXMPP.jar
b49f3000-b49f7000 r--s 00032000 08:01 669826     /home/andy/Desktop/Server/1.7.3/plugins/WorldGuard.jar
b49f7000-b49f8000 r--s 00010000 08:01 669852     /home/andy/Desktop/Server/1.7.3/plugins/EssentialsGroupBridge.jar
b49f8000-b49fa000 r--s 00024000 08:01 669853     /home/andy/Desktop/Server/1.7.3/plugins/EssentialsGroupManager.jar
b49fa000-b4a06000 r--s 00093000 08:01 669854     /home/andy/Desktop/Server/1.7.3/plugins/EssentialsProtect.jar
b4a06000-b4a07000 r--s 00001000 08:01 669855     /home/andy/Desktop/Server/1.7.3/plugins/EssentialsSpawn.jar
b4a07000-b4a0d000 r--s 000cb000 08:01 669849     /home/andy/Desktop/Server/1.7.3/plugins/Essentials.jar
b4a0d000-b4a16000 r--s 0006a000 08:01 669838     /home/andy/Desktop/Server/1.7.3/plugins/WorldEdit.jar
b4a16000-b4a1c000 r--s 00075000 08:01 1058118    /home/andy/Desktop/Server/1.7.3/lib/postgresql.jar
b4a1c000-b4a23000 r--s 000a5000 08:01 1058117    /home/andy/Desktop/Server/1.7.3/lib/mysql.jar
b4a23000-b4a2d000 r--s 00123000 08:01 1058116    /home/andy/Desktop/Server/1.7.3/lib/h2.jar
b4a2d000-b4a32000 r--s 00041000 08:01 923550     /home/andy/Desktop/Server/1.7.3/plugins/BigBrother.jar
b4a32000-b4a35000 ---p 00000000 00:00 0 
b4a35000-b4a83000 rw-p 00000000 00:00 0 
b4a83000-b4a86000 ---p 00000000 00:00 0 
b4a86000-b4ad4000 rw-p 00000000 00:00 0 
b4ad4000-b4ad7000 r--s 00077000 08:01 4588753    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar
b4ad7000-b4ada000 ---p 00000000 00:00 0 
b4ada000-b4b28000 rw-p 00000000 00:00 0 
b4b28000-b4b2b000 ---p 00000000 00:00 0 
b4b2b000-b4b79000 rw-p 00000000 00:00 0 
b4b79000-b4b7c000 ---p 00000000 00:00 0 
b4b7c000-b4bca000 rw-p 00000000 00:00 0 
b4bca000-b4bcd000 r--s 0000f000 08:01 4588756    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b4bcd000-b4bd5000 r--s 00066000 08:01 399383     /usr/share/java/gnome-java-bridge.jar
b4bd5000-b4c31000 r--s 007c1000 08:11 33         /Minecraft/Server/1.7.3/craftbukkit-0.0.1-SNAPSHOT.jar
b4c31000-b4c32000 ---p 00000000 00:00 0 
b4c32000-b4cb2000 rw-p 00000000 00:00 0 
b4cb2000-b4cb5000 ---p 00000000 00:00 0 
b4cb5000-b4d03000 rw-p 00000000 00:00 0 
b4d03000-b4d06000 ---p 00000000 00:00 0 
b4d06000-b4d84000 rw-p 00000000 00:00 0 
b4d84000-b4d87000 ---p 00000000 00:00 0 
b4d87000-b4dd5000 rw-p 00000000 00:00 0 
b4dd5000-b4dd6000 r--p 002a1000 08:01 4595408    /usr/lib/locale/locale-archive
b4dd6000-b4fd6000 r--p 00000000 08:01 4595408    /usr/lib/locale/locale-archive
b4fd6000-b4fd9000 ---p 00000000 00:00 0 
b4fd9000-b5027000 rw-p 00000000 00:00 0 
b5027000-b502a000 ---p 00000000 00:00 0 
b502a000-b5078000 rw-p 00000000 00:00 0 
b5078000-b5079000 ---p 00000000 00:00 0 
b5079000-b512c000 rw-p 00000000 00:00 0 
b512c000-b52bc000 r--s 037af000 08:01 4595490    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b52bc000-b52ca000 rw-p 00000000 00:00 0 
b52ca000-b52e4000 rw-p 00000000 00:00 0 
b52e4000-b56d4000 rw-p 00000000 00:00 0 
b56d4000-b56ed000 rw-p 00000000 00:00 0 
b56ed000-b570d000 rw-p 00000000 00:00 0 
b570d000-b5779000 rw-p 00000000 00:00 0 
b5779000-b5c51000 rwxp 00000000 00:00 0 
b5c51000-b7779000 rw-p 00000000 00:00 0 
b7779000-b777c000 ---p 00000000 00:00 0 
b777c000-b77d3000 rw-p 00000000 00:00 0 
b77d3000-b77db000 rw-s 00000000 08:01 923532     /tmp/hsperfdata_andy/18683
b77db000-b77dc000 rw-p 00000000 00:00 0 
b77dc000-b77dd000 r--p 00000000 00:00 0 
b77dd000-b77df000 rw-p 00000000 00:00 0 
bffba000-bffef000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xms1200M -Xmx1200M 
java_command: /media/PATRIOT/Minecraft/Server/1.7.3/craftbukkit-0.0.1-SNAPSHOT.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=andy
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3de6c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3de6c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x2fef60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x2fef60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x2fef60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x2fef60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x2fedd0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x301bc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x301bc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x301bc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x301bc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 11.04 (natty)
uname:Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
libc:glibc 2.13 NPTL 2.13 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 4096, AS infinity
load average:0.21 0.18 0.15

/proc/meminfo:
MemTotal:        1275276 kB
MemFree:           31148 kB
Buffers:             904 kB
Cached:            35876 kB
SwapCached:        25360 kB
Active:           594468 kB
Inactive:         600200 kB
Active(anon):     578272 kB
Inactive(anon):   585664 kB
Active(file):      16196 kB
Inactive(file):    14536 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:        392664 kB
HighFree:           2436 kB
LowTotal:         882612 kB
LowFree:           28712 kB
SwapTotal:       1307644 kB
SwapFree:        1191752 kB
Dirty:              2848 kB
Writeback:             0 kB
AnonPages:       1133596 kB
Mapped:            19708 kB
Shmem:              5904 kB
Slab:              21976 kB
SReclaimable:      11660 kB
SUnreclaim:        10316 kB
KernelStack:        2336 kB
PageTables:         5604 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1945280 kB
Committed_AS:    2601520 kB
VmallocTotal:     122880 kB
VmallocUsed:       37364 kB
VmallocChunk:      76284 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       32760 kB
DirectMap4M:      876544 kB


CPU:total 1 (1 cores per cpu, 1 threads per core) family 15 model 2 stepping 9, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 1275276k(31148k free), swap 1307644k(1191752k free)

vm_info: OpenJDK Client VM (20.0-b11) for linux-x86 JRE (1.6.0_22-b22), built on Apr  5 2011 14:20:06 by "buildd" with gcc 4.5.2

time: Mon Jul 25 23:27:07 2011
elapsed time: 5877 seconds

---

