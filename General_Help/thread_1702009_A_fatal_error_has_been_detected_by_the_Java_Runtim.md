---
title: "A fatal error has been detected by the Java Runtime Environment:"
date: 2011-03-07
forum: General Help
---

### Post by clooless001 on 2011-03-07
I have been playing minecraft since the Alpha stage, and only recently got this problem.
I can only assume it is a Java error due to the error log I received.
I run Minecraft with:
```
 #!/bin/bash
killall ibus-daemon
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
ibus-daemon --xim &
disown
```And eventually the game will just hang, with no warning.
I get back the error log:

```
 #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb77c09c1, pid=2896, tid=3006315376
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Client VM (19.1-b02 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [libc.so.6+0x749c1]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x09c4e400):  JavaThread "Minecraft main thread" daemon [_thread_in_native, id=2920, stack(0xb32bb000,0xb330c000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000000

Registers:
EAX=0x00000000, EBX=0xb2616ff4, ECX=0x00000010, EDX=0x00000000
ESP=0xb330a0b8, EBP=0xb330a0d8, ESI=0x09ec9f70, EDI=0xb330a1ec
EIP=0xb77c09c1, CR2=0x00000000, EFLAGS=0x00010246

Register to memory mapping:

EAX=0x00000000
0x00000000 is pointing to unknown location

EBX=0xb2616ff4
0xb2616ff4: <offset 0x26cff4> in /usr/lib/dri/r300_dri.so at 0xb23aa000

ECX=0x00000010
0x00000010 is pointing to unknown location

EDX=0x00000000
0x00000000 is pointing to unknown location

ESP=0xb330a0b8
0xb330a0b8 is pointing into the stack for thread: 0x09c4e400
"Minecraft main thread" daemon prio=10 tid=0x09c4e400 nid=0xb68 runnable [0xb330a000]
   java.lang.Thread.State: RUNNABLE

EBP=0xb330a0d8
0xb330a0d8 is pointing into the stack for thread: 0x09c4e400
"Minecraft main thread" daemon prio=10 tid=0x09c4e400 nid=0xb68 runnable [0xb330a000]
   java.lang.Thread.State: RUNNABLE

ESI=0x09ec9f70
0x09ec9f70 is pointing to unknown location

EDI=0xb330a1ec
0xb330a1ec is pointing into the stack for thread: 0x09c4e400
"Minecraft main thread" daemon prio=10 tid=0x09c4e400 nid=0xb68 runnable [0xb330a000]
   java.lang.Thread.State: RUNNABLE


Top of Stack: (sp=0xb330a0b8)
0xb330a0b8:   0c89d6d8 b2447e6c b330a1ec 00000000
0xb330a0c8:   00000040 b2801bad 09ec82d0 b2616ff4
0xb330a0d8:   b330a248 b23e8248 b330a1ec 00000040
0xb330a0e8:   b25b6859 b25b690b 000000ee 00000006
0xb330a0f8:   b330a198 b2616ff4 09ec82d0 b330a1ec
0xb330a108:   b330a128 09ec82d0 09ec82d0 b25b6f1e
0xb330a118:   b330a148 b2802950 0a207310 00000003
0xb330a128:   b25b6e00 b280188a b247f084 b330a17c 

Instructions: (pc=0xb77c09c1)
0xb77c09b1:   1b 83 f2 01 75 02 aa 49 89 ca c1 e9 02 83 e2 03
0xb77c09c1:   69 c0 01 01 01 01 f3 ab 89 d1 f3 aa 8b 44 24 08 

Stack: [0xb32bb000,0xb330c000],  sp=0xb330a0b8,  free space=316k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libc.so.6+0x749c1]
C  [r300_dri.so+0x3e248]  r300SelectAndTranslateFragmentShader+0x48
C  [r300_dri.so+0x3a6c5]  r300UpdateShaders+0x35
C  [r300_dri.so+0x2be8d]
C  [r300_dri.so+0xe4d9f]  vbo_save_playback_vertex_list+0x2ff
C  [r300_dri.so+0x6b494]
C  [r300_dri.so+0x6efa9]  _mesa_CallLists+0x99
C  [r300_dri.so+0xd31ce]
C  [liblwjgl.so+0x44b85]  Java_org_lwjgl_opengl_GL11_nglCallLists+0x35
J  org.lwjgl.opengl.GL11.nglCallLists(IILjava/nio/Buffer;IJ)V
J  org.lwjgl.opengl.GL11.glCallLists(Ljava/nio/IntBuffer;)V
j  mh.b(F)V+286
j  net.minecraft.client.Minecraft.run()V+357
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub
V  [libjvm.so+0x23f671]
V  [libjvm.so+0x375498]
V  [libjvm.so+0x23eee5]
V  [libjvm.so+0x23efa8]
V  [libjvm.so+0x2c1737]
V  [libjvm.so+0x41f89f]
V  [libjvm.so+0x376a8e]
C  [libpthread.so.0+0x596e]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
J  org.lwjgl.opengl.GL11.nglCallLists(IILjava/nio/Buffer;IJ)V
J  org.lwjgl.opengl.GL11.glCallLists(Ljava/nio/IntBuffer;)V
J  pc.a()V
J  h.a(IIID)I
J  h.a(Liz;ID)I
j  mh.c(F)V+673
j  mh.b(F)V+286
j  net.minecraft.client.Minecraft.run()V+357
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0a2dc000 JavaThread "Thread-8" daemon [_thread_blocked, id=2923, stack(0xb2878000,0xb28c9000)]
=>0x09c4e400 JavaThread "Minecraft main thread" daemon [_thread_in_native, id=2920, stack(0xb32bb000,0xb330c000)]
  0x09bca800 JavaThread "Timer hack thread" daemon [_thread_blocked, id=2919, stack(0xb2827000,0xb2878000)]
  0x09b57000 JavaThread "DestroyJavaVM" [_thread_blocked, id=2897, stack(0xb6dd2000,0xb6e23000)]
  0xb3149000 JavaThread "TimerQueue" daemon [_thread_blocked, id=2913, stack(0xb30af000,0xb3100000)]
  0x09d62800 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=2909, stack(0xb3219000,0xb326a000)]
  0x09d61000 JavaThread "AWT-Shutdown" [_thread_blocked, id=2908, stack(0xb326a000,0xb32bb000)]
  0x09c77400 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=2906, stack(0xb4088000,0xb40d9000)]
  0x09c51000 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=2905, stack(0xb4102000,0xb4153000)]
  0x09b91c00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=2903, stack(0xb44c5000,0xb4516000)]
  0x09b90000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=2902, stack(0xb4516000,0xb4597000)]
  0x09b8e800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=2901, stack(0xb4597000,0xb45e8000)]
  0x09b86400 JavaThread "Finalizer" daemon [_thread_blocked, id=2900, stack(0xb462e000,0xb467f000)]
  0x09b84c00 JavaThread "Reference Handler" daemon [_thread_blocked, id=2899, stack(0xb467f000,0xb46d0000)]

Other Threads:
  0x09b7a800 VMThread [stack: 0xb489c000,0xb491d000] [id=2898]
  0x09b9dc00 WatcherThread [stack: 0xb4444000,0xb44c5000] [id=2904]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 157376K, used 115181K [0x4ece0000, 0x597a0000, 0x64230000)
  eden space 139904K,  82% used [0x4ece0000, 0x55d5b5e0, 0x57580000)
  from space 17472K,   0% used [0x57580000, 0x57580000, 0x58690000)
  to   space 17472K,   0% used [0x58690000, 0x58690000, 0x597a0000)
 tenured generation   total 349568K, used 42263K [0x64230000, 0x79790000, 0x8ece0000)
   the space 349568K,  12% used [0x64230000, 0x66b75ed8, 0x66b76000, 0x79790000)
 compacting perm gen  total 12288K, used 7334K [0x8ece0000, 0x8f8e0000, 0x92ce0000)
   the space 12288K,  59% used [0x8ece0000, 0x8f409a48, 0x8f409c00, 0x8f8e0000)
    ro space 10240K,  61% used [0x92ce0000, 0x93308a38, 0x93308c00, 0x936e0000)
    rw space 12288K,  60% used [0x936e0000, 0x93e18ec0, 0x93e19000, 0x942e0000)

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:01 6301512    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 6301512    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/bin/java
09b51000-0d6c6000 rwxp 00000000 00:00 0          [heap]
4ece0000-597a0000 rwxp 00000000 00:00 0 
597a0000-64230000 rwxp 00000000 00:00 0 
64230000-79790000 rwxp 00000000 00:00 0 
79790000-8ece0000 rwxp 00000000 00:00 0 
8ece0000-8f8e0000 rwxp 00000000 00:00 0 
8f8e0000-92ce0000 rwxp 00000000 00:00 0 
92ce0000-93309000 r-xs 00001000 08:01 6302264    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/client/classes.jsa
93309000-936e0000 rwxp 00000000 00:00 0 
936e0000-93e19000 rwxp 0062a000 08:01 6302264    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/client/classes.jsa
93e19000-942e0000 rwxp 00000000 00:00 0 
942e0000-943c1000 rwxp 00d63000 08:01 6302264    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/client/classes.jsa
943c1000-946e0000 rwxp 00000000 00:00 0 
946e0000-946e8000 r-xs 00e44000 08:01 6302264    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/client/classes.jsa
946e8000-94ae0000 rwxp 00000000 00:00 0 
add82000-add8a000 rwxs 12a46a000 00:05 3691      /dev/dri/card0
add8a000-add92000 rwxs 12a462000 00:05 3691      /dev/dri/card0
add92000-add9a000 rwxs 12a45a000 00:05 3691      /dev/dri/card0
add9a000-adda2000 rwxs 12a452000 00:05 3691      /dev/dri/card0
adda2000-addaa000 rwxs 12a44a000 00:05 3691      /dev/dri/card0
addaa000-addb2000 rwxs 12a442000 00:05 3691      /dev/dri/card0
addb2000-addba000 rwxs 12a43a000 00:05 3691      /dev/dri/card0
addba000-addc2000 rwxs 12a432000 00:05 3691      /dev/dri/card0
addc2000-addca000 rwxs 12a42a000 00:05 3691      /dev/dri/card0
addca000-addd2000 rwxs 12a422000 00:05 3691      /dev/dri/card0
addd2000-addda000 rwxs 12a3ed000 00:05 3691      /dev/dri/card0
addda000-adde2000 rwxs 12a3e5000 00:05 3691      /dev/dri/card0
adde2000-addea000 rwxs 12a3dd000 00:05 3691      /dev/dri/card0
addea000-addf2000 rwxs 12a3d5000 00:05 3691      /dev/dri/card0
addf2000-addfa000 rwxs 12a3cd000 00:05 3691      /dev/dri/card0
addfa000-ade02000 rwxs 12a3c5000 00:05 3691      /dev/dri/card0
ade02000-ade0a000 rwxs 12a41a000 00:05 3691      /dev/dri/card0
ade0a000-ade12000 rwxs 12a412000 00:05 3691      /dev/dri/card0
ade12000-ade1a000 rwxs 12a40a000 00:05 3691      /dev/dri/card0
ade1a000-ade22000 rwxs 12a402000 00:05 3691      /dev/dri/card0
ade22000-ade2a000 rwxs 12a3fa000 00:05 3691      /dev/dri/card0
ade2a000-ade32000 rwxs 12a3bc000 00:05 3691      /dev/dri/card0
ade32000-ade3a000 rwxs 12a3b4000 00:05 3691      /dev/dri/card0
ade3a000-ade42000 rwxs 12a3ac000 00:05 3691      /dev/dri/card0
ade42000-ade4a000 rwxs 12a3a4000 00:05 3691      /dev/dri/card0
ade4a000-ade52000 rwxs 12a39c000 00:05 3691      /dev/dri/card0
ade52000-ade5a000 rwxs 12a38c000 00:05 3691      /dev/dri/card0
ade5a000-ade62000 rwxs 12a37c000 00:05 3691      /dev/dri/card0
ade62000-ade6a000 rwxs 12a374000 00:05 3691      /dev/dri/card0
ade6a000-ade72000 rwxs 12a36c000 00:05 3691      /dev/dri/card0
ade72000-ade7a000 rwxs 128d32000 00:05 3691      /dev/dri/card0
ade7a000-ade82000 rwxs 128d2a000 00:05 3691      /dev/dri/card0
ade82000-ade8a000 rwxs 12a311000 00:05 3691      /dev/dri/card0
ade8a000-ade92000 rwxs 12a309000 00:05 3691      /dev/dri/card0
ade92000-ade9a000 rwxs 12a301000 00:05 3691      /dev/dri/card0
ade9a000-adea2000 rwxs 12a2f0000 00:05 3691      /dev/dri/card0
adea2000-adeaa000 rwxs 129c0e000 00:05 3691      /dev/dri/card0
adeaa000-adeb2000 rwxs 129c06000 00:05 3691      /dev/dri/card0
adeb2000-adeba000 rwxs 129bfe000 00:05 3691      /dev/dri/card0
adeba000-adec2000 rwxs 12a198000 00:05 3691      /dev/dri/card0
adec2000-adeca000 rwxs 12a190000 00:05 3691      /dev/dri/card0
adeca000-aded2000 rwxs 12a272000 00:05 3691      /dev/dri/card0
aded2000-adeda000 rwxs 12a26a000 00:05 3691      /dev/dri/card0
adeda000-adee2000 rwxs 12a262000 00:05 3691      /dev/dri/card0
adee2000-adeea000 rwxs 12a25a000 00:05 3691      /dev/dri/card0
adeea000-adef2000 rwxs 129d3c000 00:05 3691      /dev/dri/card0
adef2000-adefa000 rwxs 12a21a000 00:05 3691      /dev/dri/card0
adefa000-adf02000 rwxs 12a2e8000 00:05 3691      /dev/dri/card0
adf02000-adf0a000 rwxs 129d34000 00:05 3691      /dev/dri/card0
adf0a000-adf12000 rwxs 129c27000 00:05 3691      /dev/dri/card0
adf12000-adf1a000 rwxs 129c1f000 00:05 3691      /dev/dri/card0
adf1a000-adf22000 rwxs 129c17000 00:05 3691      /dev/dri/card0
adf22000-adf2a000 rwxs 129c47000 00:05 3691      /dev/dri/card0
adf2a000-adf32000 rwxs 12a03a000 00:05 3691      /dev/dri/card0
adf32000-adf3a000 rwxs 12a04a000 00:05 3691      /dev/dri/card0
adf3a000-adf42000 rwxs 12a042000 00:05 3691      /dev/dri/card0
adf42000-adf4a000 rwxs 12a1c4000 00:05 3691      /dev/dri/card0
adf4a000-adf52000 rwxs 12a232000 00:05 3691      /dev/dri/card0
adf52000-adf5a000 rwxs 12a22a000 00:05 3691      /dev/dri/card0
adf5a000-adf62000 rwxs 12a222000 00:05 3691      /dev/dri/card0
adf62000-adf6a000 rwxs 129fd4000 00:05 3691      /dev/dri/card0
adf6a000-adf72000 rwxs 129c2f000 00:05 3691      /dev/dri/card0
adf72000-adf7a000 rwxs 12a1b5000 00:05 3691      /dev/dri/card0
adf7a000-adf82000 rwxs 12a1ac000 00:05 3691      /dev/dri/card0
adf82000-adf8a000 rwxs 12a1a4000 00:05 3691      /dev/dri/card0
adf8a000-adf92000 rwxs 12a032000 00:05 3691      /dev/dri/card0
adf92000-adf9a000 rwxs 129c3f000 00:05 3691      /dev/dri/card0
adf9a000-adfa2000 rwxs 12a188000 00:05 3691      /dev/dri/card0
adfa2000-adfaa000 rwxs 12a180000 00:05 3691      /dev/dri/card0
adfaa000-adfb2000 rwxs 12a2ca000 00:05 3691      /dev/dri/card0
adfb2000-adfba000 rwxs 12a2c2000 00:05 3691      /dev/dri/card0
adfba000-adfc2000 rwxs 12a147000 00:05 3691      /dev/dri/card0
adfc2000-adfca000 rwxs 1298f2000 00:05 3691      /dev/dri/card0
adfca000-adfd2000 rwxs 12a136000 00:05 3691      /dev/dri/card0
adfd2000-adfda000 rwxs 12a12e000 00:05 3691      /dev/dri/card0
adfda000-adfe2000 rwxs 12a126000 00:05 3691      /dev/dri/card0
adfe2000-adfea000 rwxs 12a116000 00:05 3691      /dev/dri/card0
adfea000-adff2000 rwxs 12a10e000 00:05 3691      /dev/dri/card0
adff2000-adffa000 rwxs 129b37000 00:05 3691      /dev/dri/card0
adffa000-ae002000 rwxs 129fcc000 00:05 3691      /dev/dri/card0
ae002000-ae00a000 rwxs 12a106000 00:05 3691      /dev/dri/card0
ae00a000-ae012000 rwxs 12a202000 00:05 3691      /dev/dri/card0
ae012000-ae01a000 rwxs 12a06c000 00:05 3691      /dev/dri/card0
ae01a000-ae022000 rwxs 12a090000 00:05 3691      /dev/dri/card0
ae022000-ae02a000 rwxs 12a0c8000 00:05 3691      /dev/dri/card0
ae02a000-ae032000 rwxs 12a0c0000 00:05 3691      /dev/dri/card0
ae032000-ae03a000 rwxs 12a167000 00:05 3691      /dev/dri/card0
ae03a000-ae042000 rwxs 12a15f000 00:05 3691      /dev/dri/card0
ae042000-ae04a000 rwxs 12a20a000 00:05 3691      /dev/dri/card0
ae04a000-ae052000 rwxs 12a178000 00:05 3691      /dev/dri/card0
ae052000-ae05a000 rwxs 12a088000 00:05 3691      /dev/dri/card0
ae05a000-ae062000 rwxs 129dc6000 00:05 3691      /dev/dri/card0
ae062000-ae06a000 rwxs 12a05c000 00:05 3691      /dev/dri/card0
ae06a000-ae072000 rwxs 1292f6000 00:05 3691      /dev/dri/card0
ae072000-ae07a000 rwxs 12a2e0000 00:05 3691      /dev/dri/card0
ae07a000-ae082000 rwxs 12a0b8000 00:05 3691      /dev/dri/card0
ae082000-ae08a000 rwxs 12a0b0000 00:05 3691      /dev/dri/card0
ae08a000-ae092000 rwxs 129be5000 00:05 3691      /dev/dri/card0
ae092000-ae09a000 rwxs 12a1ed000 00:05 3691      /dev/dri/card0
ae09a000-ae0a2000 rwxs 129ba5000 00:05 3691      /dev/dri/card0
ae0a2000-ae0aa000 rwxs 129bad000 00:05 3691      /dev/dri/card0
ae0aa000-ae0b2000 rwxs 12a157000 00:05 3691      /dev/dri/card0
ae0b2000-ae0ba000 rwxs 12a14f000 00:05 3691      /dev/dri/card0
ae0ba000-ae0c2000 rwxs 129fc4000 00:05 3691      /dev/dri/card0
ae0c2000-ae0ca000 rwxs 129e1c000 00:05 3691      /dev/dri/card0
ae0ca000-ae0d2000 rwxs 12a080000 00:05 3691      /dev/dri/card0
ae0d2000-ae0da000 rwxs 12a078000 00:05 3691      /dev/dri/card0
ae0da000-ae0e2000 rwxs 12a022000 00:05 3691      /dev/dri/card0
ae0e2000-ae0ea000 rwxs 12a01a000 00:05 3691      /dev/dri/card0
ae0ea000-ae0f2000 rwxs 12a012000 00:05 3691      /dev/dri/card0
ae0f2000-ae0fa000 rwxs 129ffa000 00:05 3691      /dev/dri/card0
ae0fa000-ae102000 rwxs 12a170000 00:05 3691      /dev/dri/card0
ae102000-ae10a000 rwxs 12a2d8000 00:05 3691      /dev/dri/card0
ae10a000-ae112000 rwxs 12a0e9000 00:05 3691      /dev/dri/card0
ae112000-ae11a000 rwxs 12a0e1000 00:05 3691      /dev/dri/card0
ae11a000-ae122000 rwxs 129ff2000 00:05 3691      /dev/dri/card0
ae122000-ae12a000 rwxs 129fea000 00:05 3691      /dev/dri/card0
ae12a000-ae132000 rwxs 12a2f9000 00:05 3691      /dev/dri/card0
ae132000-ae13a000 rwxs 129fa4000 00:05 3691      /dev/dri/card0
ae13a000-ae142000 rwxs 129cdf000 00:05 3691      /dev/dri/card0
ae142000-ae14a000 rwxs 129f9c000 00:05 3691      /dev/dri/card0
ae14a000-ae152000 rwxs 129f94000 00:05 3691      /dev/dri/card0
ae152000-ae15a000 rwxs 129f8c000 00:05 3691      /dev/dri/card0
ae15a000-ae162000 rwxs 129f7c000 00:05 3691      /dev/dri/card0
ae162000-ae16a000 rwxs 129f74000 00:05 3691      /dev/dri/card0
ae16a000-ae172000 rwxs 129f6c000 00:05 3691      /dev/dri/card0
ae172000-ae17a000 rwxs 129f64000 00:05 3691      /dev/dri/card0
ae17a000-ae182000 rwxs 129f54000 00:05 3691      /dev/dri/card0
ae182000-ae18a000 rwxs 129f4c000 00:05 3691      /dev/dri/card0
ae18a000-ae192000 rwxs 129f44000 00:05 3691      /dev/dri/card0
ae192000-ae19a000 rwxs 129f3c000 00:05 3691      /dev/dri/card0
ae19a000-ae1a2000 rwxs 129f34000 00:05 3691      /dev/dri/card0
ae1a2000-ae1aa000 rwxs 129f2c000 00:05 3691      /dev/dri/card0
ae1aa000-ae1b2000 rwxs 129f24000 00:05 3691      /dev/dri/card0
ae1b2000-ae1ba000 rwxs 129f1c000 00:05 3691      /dev/dri/card0
ae1ba000-ae1c2000 rwxs 129f14000 00:05 3691      /dev/dri/card0
ae1c2000-ae1ca000 rwxs 129f0c000 00:05 3691      /dev/dri/card0
ae1ca000-ae1d2000 rwxs 129f04000 00:05 3691      /dev/dri/card0
ae1d2000-ae1da000 rwxs 129efc000 00:05 3691      /dev/dri/card0
ae1da000-ae1e2000 rwxs 129ef4000 00:05 3691      /dev/dri/card0
ae1e2000-ae1ea000 rwxs 129eec000 00:05 3691      /dev/dri/card0
ae1ea000-ae1f2000 rwxs 129ee4000 00:05 3691      /dev/dri/card0
ae1f2000-ae1fa000 rwxs 129edc000 00:05 3691      /dev/dri/card0
ae1fa000-ae202000 rwxs 129ed4000 00:05 3691      /dev/dri/card0
ae202000-ae20a000 rwxs 129ecc000 00:05 3691      /dev/dri/card0
ae20a000-ae212000 rwxs 129ec4000 00:05 3691      /dev/dri/card0
ae212000-ae21a000 rwxs 129ebc000 00:05 3691      /dev/dri/card0
ae21a000-ae222000 rwxs 129eb4000 00:05 3691      /dev/dri/card0
ae222000-ae22a000 rwxs 129eac000 00:05 3691      /dev/dri/card0
ae22a000-ae232000 rwxs 129ea4000 00:05 3691      /dev/dri/card0
ae232000-ae23a000 rwxs 129e9c000 00:05 3691      /dev/dri/card0
ae23a000-ae242000 rwxs 129e94000 00:05 3691      /dev/dri/card0
ae242000-ae24a000 rwxs 129e8c000 00:05 3691      /dev/dri/card0
ae24a000-ae252000 rwxs 129e84000 00:05 3691      /dev/dri/card0
ae252000-ae25a000 rwxs 129e7c000 00:05 3691      /dev/dri/card0
ae25a000-ae262000 rwxs 129e74000 00:05 3691      /dev/dri/card0
ae262000-ae26a000 rwxs 129e6c000 00:05 3691      /dev/dri/card0
ae26a000-ae272000 rwxs 129e64000 00:05 3691      /dev/dri/card0
ae272000-ae27a000 rwxs 129e5c000 00:05 3691      /dev/dri/card0
ae27a000-ae282000 rwxs 129e54000 00:05 3691      /dev/dri/card0
ae282000-ae28a000 rwxs 129e4c000 00:05 3691      /dev/dri/card0
ae28a000-ae292000 rwxs 129e44000 00:05 3691      /dev/dri/card0
ae292000-ae29a000 rwxs 129e3c000 00:05 3691      /dev/dri/card0
ae29a000-ae2a2000 rwxs 129e34000 00:05 3691      /dev/dri/card0
ae2a2000-ae2aa000 rwxs 129e24000 00:05 3691      /dev/dri/card0
ae2aa000-ae2b2000 rwxs 12a29a000 00:05 3691      /dev/dri/card0
ae2b2000-ae2ba000 rwxs 12a0a0000 00:05 3691      /dev/dri/card0
ae2ba000-ae2c2000 rwxs 12a098000 00:05 3691      /dev/dri/card0
ae2c2000-ae2ca000 rwxs 129e14000 00:05 3691      /dev/dri/card0
ae2ca000-ae2d2000 rwxs 129dfc000 00:05 3691      /dev/dri/card0
ae2d2000-ae2da000 rwxs 129d2c000 00:05 3691      /dev/dri/card0
ae2da000-ae2e2000 rwxs 129d24000 00:05 3691      /dev/dri/card0
ae2e2000-ae2ea000 rwxs 129de4000 00:05 3691      /dev/dri/card0
ae2ea000-ae2f2000 rwxs 12a00a000 00:05 3691      /dev/dri/card0
ae2f2000-ae2fa000 rwxs 12a002000 00:05 3691      /dev/dri/card0
ae2fa000-ae302000 rwxs 12a054000 00:05 3691      /dev/dri/card0
ae302000-ae30a000 rwxs 12a32e000 00:05 3691      /dev/dri/card0
ae30a000-ae312000 rwxs 129db6000 00:05 3691      /dev/dri/card0
ae312000-ae31a000 rwxs 129dae000 00:05 3691      /dev/dri/card0
ae31a000-ae322000 rwxs 129e2c000 00:05 3691      /dev/dri/card0
ae322000-ae32a000 rwxs 129da5000 00:05 3691      /dev/dri/card0
ae32a000-ae332000 rwxs 129d9d000 00:05 3691      /dev/dri/card0
ae332000-ae33a000 rwxs 129d95000 00:05 3691      /dev/dri/card0
ae33a000-ae342000 rwxs 129d8d000 00:05 3691      /dev/dri/card0
ae342000-ae34a000 rwxs 129d84000 00:05 3691      /dev/dri/card0
ae34a000-ae352000 rwxs 129d7c000 00:05 3691      /dev/dri/card0
ae352000-ae35a000 rwxs 129d74000 00:05 3691      /dev/dri/card0
ae35a000-ae362000 rwxs 129d6c000 00:05 3691      /dev/dri/card0
ae362000-ae36a000 rwxs 129d64000 00:05 3691      /dev/dri/card0
ae36a000-ae372000 rwxs 129d5c000 00:05 3691      /dev/dri/card0
ae372000-ae37a000 rwxs 129fbc000 00:05 3691      /dev/dri/card0
ae37a000-ae382000 rwxs 129d4c000 00:05 3691      /dev/dri/card0
ae382000-ae38a000 rwxs 129dd6000 00:05 3691      /dev/dri/card0
ae38a000-ae392000 rwxs 12a13f000 00:05 3691      /dev/dri/card0
ae392000-ae39a000 rwxs 12a292000 00:05 3691      /dev/dri/card0
ae39a000-ae3a2000 rwxs 129df4000 00:05 3691      /dev/dri/card0
ae3a2000-ae3aa000 rwxs 129cbf000 00:05 3691      /dev/dri/card0
ae3aa000-ae3b2000 rwxs 129d54000 00:05 3691      /dev/dri/card0
ae3b2000-ae3ba000 rwxs 129e0c000 00:05 3691      /dev/dri/card0
ae3ba000-ae3c2000 rwxs 129cb7000 00:05 3691      /dev/dri/card0
ae3c2000-ae3ca000 rwxs 12908a000 00:05 3691      /dev/dri/card0
ae3ca000-ae3d2000 rwxs 129082000 00:05 3691      /dev/dri/card0
ae3d2000-ae3da000 rwxs 129f5c000 00:05 3691      /dev/dri/card0
ae3da000-ae3e2000 rwxs 129072000 00:05 3691      /dev/dri/card0
ae3e2000-ae3ea000 rwxs 129ceb000 00:05 3691      /dev/dri/card0
ae3ea000-ae3f2000 rwxs 129f84000 00:05 3691      /dev/dri/card0
ae3f2000-ae3fa000 rwxs 129cd7000 00:05 3691      /dev/dri/card0
ae3fa000-ae402000 rwxs 129b3f000 00:05 3691      /dev/dri/card0
ae402000-ae40a000 rwxs 12972b000 00:05 3691      /dev/dri/card0
ae40a000-ae412000 rwxs 12a472000 00:05 3691      /dev/dri/card0
ae412000-ae41a000 rwxs 129dec000 00:05 3691      /dev/dri/card0
ae41a000-ae422000 rwxs 1298a2000 00:05 3691      /dev/dri/card0
ae422000-ae42a000 rwxs 129c6d000 00:05 3691      /dev/dri/card0
ae42a000-ae432000 rwxs 129c65000 00:05 3691      /dev/dri/card0
ae432000-ae43a000 rwxs 129ace000 00:05 3691      /dev/dri/card0
ae43a000-ae442000 rwxs 12a252000 00:05 3691      /dev/dri/card0
ae442000-ae44a000 rwxs 129c9d000 00:05 3691      /dev/dri/card0
ae44a000-ae452000 rwxs 1298fa000 00:05 3691      /dev/dri/card0
ae452000-ae45a000 rwxs 129d1c000 00:05 3691      /dev/dri/card0
ae45a000-ae462000 rwxs 129ade000 00:05 3691      /dev/dri/card0
ae462000-ae46a000 rwxs 1295a2000 00:05 3691      /dev/dri/card0
ae46a000-ae472000 rwxs 129e04000 00:05 3691      /dev/dri/card0
ae472000-ae47a000 rwxs 12a064000 00:05 3691      /dev/dri/card0
ae47a000-ae482000 rwxs 12989a000 00:05 3691      /dev/dri/card0
ae482000-ae48a000 rwxs 129b2f000 00:05 3691      /dev/dri/card0
ae48a000-ae492000 rwxs 129b27000 00:05 3691      /dev/dri/card0
ae492000-ae49a000 rwxs 129b1f000 00:05 3691      /dev/dri/card0
ae49a000-ae4a2000 rwxs 129b17000 00:05 3691      /dev/dri/card0
ae4a2000-ae4aa000 rwxs 129b6c000 00:05 3691      /dev/dri/card0
ae4aa000-ae4b2000 rwxs 129d14000 00:05 3691      /dev/dri/card0
ae4b2000-ae4ba000 rwxs 129d0c000 00:05 3691      /dev/dri/card0
ae4ba000-ae4c2000 rwxs 129c37000 00:05 3691      /dev/dri/card0
ae4c2000-ae4ca000 rwxs 1275a1000 00:05 3691      /dev/dri/card0
ae4ca000-ae4d2000 rwxs 129b06000 00:05 3691      /dev/dri/card0
ae4d2000-ae4da000 rwxs 129a30000 00:05 3691      /dev/dri/card0
ae4da000-ae4e2000 rwxs 12a0a8000 00:05 3691      /dev/dri/card0
ae4e2000-ae4ea000 rwxs 129bdd000 00:05 3691      /dev/dri/card0
ae4ea000-ae4f2000 rwxs 129ae6000 00:05 3691      /dev/dri/card0
ae4f2000-ae4fa000 rwxs 129ab1000 00:05 3691      /dev/dri/card0
ae4fa000-ae502000 rwxs 129ad6000 00:05 3691      /dev/dri/card0
ae502000-ae50a000 rwxs 1294d3000 00:05 3691      /dev/dri/card0
ae50a000-ae512000 rwxs 129ac6000 00:05 3691      /dev/dri/card0
ae512000-ae51a000 rwxs 129abe000 00:05 3691      /dev/dri/card0
ae51a000-ae522000 rwxs 129992000 00:05 3691      /dev/dri/card0
ae522000-ae52a000 rwxs 12998a000 00:05 3691      /dev/dri/card0
ae52a000-ae532000 rwxs 129982000 00:05 3691      /dev/dri/card0
ae532000-ae53a000 rwxs 129a18000 00:05 3691      /dev/dri/card0
ae53a000-ae542000 rwxs 129a10000 00:05 3691      /dev/dri/card0
ae542000-ae54a000 rwxs 129a08000 00:05 3691      /dev/dri/card0
ae54a000-ae552000 rwxs 12a2ba000 00:05 3691      /dev/dri/card0
ae552000-ae55a000 rwxs 129aa9000 00:05 3691      /dev/dri/card0
ae55a000-ae562000 rwxs 129aa1000 00:05 3691      /dev/dri/card0
ae562000-ae56a000 rwxs 129d04000 00:05 3691      /dev/dri/card0
ae56a000-ae572000 rwxs 129c7d000 00:05 3691      /dev/dri/card0
ae572000-ae57a000 rwxs 129a81000 00:05 3691      /dev/dri/card0
ae57a000-ae582000 rwxs 129b9d000 00:05 3691      /dev/dri/card0
ae582000-ae58a000 rwxs 129b95000 00:05 3691      /dev/dri/card0
ae58a000-ae592000 rwxs 129a40000 00:05 3691      /dev/dri/card0
ae592000-ae59a000 rwxs 129a38000 00:05 3691      /dev/dri/card0
ae59a000-ae5a2000 rwxs 129a28000 00:05 3691      /dev/dri/card0
ae5a2000-ae5aa000 rwxs 128650000 00:05 3691      /dev/dri/card0
ae5aa000-ae5b2000 rwxs 129a91000 00:05 3691      /dev/dri/card0
ae5b2000-ae5ba000 rwxs 129a20000 00:05 3691      /dev/dri/card0
ae5ba000-ae5c2000 rwxs 129b4f000 00:05 3691      /dev/dri/card0
ae5c2000-ae5ca000 rwxs 129b47000 00:05 3691      /dev/dri/card0
ae5ca000-ae5d2000 rwxs 129a99000 00:05 3691      /dev/dri/card0
ae5d2000-ae5da000 rwxs 12a2aa000 00:05 3691      /dev/dri/card0
ae5da000-ae5e2000 rwxs 129fdc000 00:05 3691      /dev/dri/card0
ae5e2000-ae5ea000 rwxs 127b2b000 00:05 3691      /dev/dri/card0
ae5ea000-ae5f2000 rwxs 129bd5000 00:05 3691      /dev/dri/card0
ae5f2000-ae5fa000 rwxs 129bcd000 00:05 3691      /dev/dri/card0
ae5fa000-ae602000 rwxs 128648000 00:05 3691      /dev/dri/card0
ae602000-ae60a000 rwxs 1299f4000 00:05 3691      /dev/dri/card0
ae60a000-ae612000 rwxs 1299ec000 00:05 3691      /dev/dri/card0
ae612000-ae61a000 rwxs 1299e3000 00:05 3691      /dev/dri/card0
ae61a000-ae622000 rwxs 1299db000 00:05 3691      /dev/dri/card0
ae622000-ae62a000 rwxs 12999a000 00:05 3691      /dev/dri/card0
ae62a000-ae632000 rwxs 1299cb000 00:05 3691      /dev/dri/card0
ae632000-ae63a000 rwxs 129bf6000 00:05 3691      /dev/dri/card0
ae63a000-ae642000 rwxs 1299ba000 00:05 3691      /dev/dri/card0
ae642000-ae64a000 rwxs 1299b2000 00:05 3691      /dev/dri/card0
ae64a000-ae652000 rwxs 12987a000 00:05 3691      /dev/dri/card0
ae652000-ae65a000 rwxs 12996a000 00:05 3691      /dev/dri/card0
ae65a000-ae662000 rwxs 129962000 00:05 3691      /dev/dri/card0
ae662000-ae66a000 rwxs 12995a000 00:05 3691      /dev/dri/card0
ae66a000-ae672000 rwxs 129952000 00:05 3691      /dev/dri/card0
ae672000-ae67a000 rwxs 1295d2000 00:05 3691      /dev/dri/card0
ae67a000-ae682000 rwxs 129115000 00:05 3691      /dev/dri/card0
ae682000-ae68a000 rwxs 12910d000 00:05 3691      /dev/dri/card0
ae68a000-ae692000 rwxs 1296b0000 00:05 3691      /dev/dri/card0
ae692000-ae69a000 rwxs 129bc5000 00:05 3691      /dev/dri/card0
ae69a000-ae6a2000 rwxs 1296c8000 00:05 3691      /dev/dri/card0
ae6a2000-ae6aa000 rwxs 127845000 00:05 3691      /dev/dri/card0
ae6aa000-ae6b2000 rwxs 12a11e000 00:05 3691      /dev/dri/card0
ae6b2000-ae6ba000 rwxs 129902000 00:05 3691      /dev/dri/card0
ae6ba000-ae6c2000 rwxs 1292e6000 00:05 3691      /dev/dri/card0
ae6c2000-ae6ca000 rwxs 1292de000 00:05 3691      /dev/dri/card0
ae6ca000-ae6d2000 rwxs 1292d6000 00:05 3691      /dev/dri/card0
ae6d2000-ae6da000 rwxs 12a02a000 00:05 3691      /dev/dri/card0
ae6da000-ae6e2000 rwxs 1298ea000 00:05 3691      /dev/dri/card0
ae6e2000-ae6ea000 rwxs 1299d3000 00:05 3691      /dev/dri/card0
ae6ea000-ae6f2000 rwxs 1298e2000 00:05 3691      /dev/dri/card0
ae6f2000-ae6fa000 rwxs 1298da000 00:05 3691      /dev/dri/card0
ae6fa000-ae702000 rwxs 129ccf000 00:05 3691      /dev/dri/card0
ae702000-ae70a000 rwxs 1298aa000 00:05 3691      /dev/dri/card0
ae70a000-ae712000 rwxs 1284e8000 00:05 3691      /dev/dri/card0
ae712000-ae71a000 rwxs 129fb4000 00:05 3691      /dev/dri/card0
ae71a000-ae722000 rwxs 12a1e4000 00:05 3691      /dev/dri/card0
ae722000-ae72a000 rwxs 12a1dc000 00:05 3691      /dev/dri/card0
ae72a000-ae732000 rwxs 12a1d4000 00:05 3691      /dev/dri/card0
ae732000-ae73a000 rwxs 12a1cc000 00:05 3691      /dev/dri/card0
ae73a000-ae742000 rwxs 129872000 00:05 3691      /dev/dri/card0
ae742000-ae74a000 rwxs 12986a000 00:05 3691      /dev/dri/card0
ae74a000-ae752000 rwxs 129862000 00:05 3691      /dev/dri/card0
ae752000-ae75a000 rwxs 12985a000 00:05 3691      /dev/dri/card0
ae75a000-ae762000 rwxs 129852000 00:05 3691      /dev/dri/card0
ae762000-ae76a000 rwxs 1296c0000 00:05 3691      /dev/dri/card0
ae76a000-ae772000 rwxs 129cc7000 00:05 3691      /dev/dri/card0
ae772000-ae77a000 rwxs 129dce000 00:05 3691      /dev/dri/card0
ae77a000-ae782000 rwxs 1298ba000 00:05 3691      /dev/dri/card0
ae782000-ae78a000 rwxs 129822000 00:05 3691      /dev/dri/card0
ae78a000-ae792000 rwxs 12981a000 00:05 3691      /dev/dri/card0
ae792000-ae79a000 rwxs 129812000 00:05 3691      /dev/dri/card0
ae79a000-ae7a2000 rwxs 12980a000 00:05 3691      /dev/dri/card0
ae7a2000-ae7aa000 rwxs 129802000 00:05 3691      /dev/dri/card0
ae7aa000-ae7b2000 rwxs 1297fa000 00:05 3691      /dev/dri/card0
ae7b2000-ae7ba000 rwxs 1297ad000 00:05 3691      /dev/dri/card0
ae7ba000-ae7c2000 rwxs 1297a5000 00:05 3691      /dev/dri/card0
ae7c2000-ae7ca000 rwxs 12979d000 00:05 3691      /dev/dri/card0
ae7ca000-ae7d2000 rwxs 129795000 00:05 3691      /dev/dri/card0
ae7d2000-ae7da000 rwxs 12978d000 00:05 3691      /dev/dri/card0
ae7da000-ae7e2000 rwxs 129785000 00:05 3691      /dev/dri/card0
ae7e2000-ae7ea000 rwxs 1297f2000 00:05 3691      /dev/dri/card0
ae7ea000-ae7f2000 rwxs 1297ea000 00:05 3691      /dev/dri/card0
ae7f2000-ae7fa000 rwxs 1297e2000 00:05 3691      /dev/dri/card0
ae7fa000-ae802000 rwxs 1297da000 00:05 3691      /dev/dri/card0
ae802000-ae80a000 rwxs 1297d2000 00:05 3691      /dev/dri/card0
ae80a000-ae812000 rwxs 1297ca000 00:05 3691      /dev/dri/card0
ae812000-ae81a000 rwxs 1297c2000 00:05 3691      /dev/dri/card0
ae81a000-ae822000 rwxs 1297ba000 00:05 3691      /dev/dri/card0
ae822000-ae82a000 rwxs 129774000 00:05 3691      /dev/dri/card0
ae82a000-ae832000 rwxs 1296e8000 00:05 3691      /dev/dri/card0
ae832000-ae83a000 rwxs 12984a000 00:05 3691      /dev/dri/card0
ae83a000-ae842000 rwxs 1296da000 00:05 3691      /dev/dri/card0
ae842000-ae852000 rwxs 1295aa000 00:05 3691      /dev/dri/card0
ae852000-ae85a000 rwxs 1298d2000 00:05 3691      /dev/dri/card0
ae85a000-ae862000 rwxs 1298ca000 00:05 3691      /dev/dri/card0
ae862000-ae86a000 rwxs 12a0f9000 00:05 3691      /dev/dri/card0
ae86a000-ae872000 rwxs 1296b8000 00:05 3691      /dev/dri/card0
ae872000-ae87a000 rwxs 129763000 00:05 3691      /dev/dri/card0
ae87a000-ae882000 rwxs 12a24a000 00:05 3691      /dev/dri/card0
ae882000-ae88a000 rwxs 12a242000 00:05 3691      /dev/dri/card0
ae88a000-ae892000 rwxs 12a23a000 00:05 3691      /dev/dri/card0
ae892000-ae89a000 rwxs 1296f0000 00:05 3691      /dev/dri/card0
ae89a000-ae8a2000 rwxs 129743000 00:05 3691      /dev/dri/card0
ae8a2000-ae8aa000 rwxs 1295ca000 00:05 3691      /dev/dri/card0
ae8aa000-ae8b2000 rwxs 129188000 00:05 3691      /dev/dri/card0
ae8b2000-ae8ba000 rwxs 129180000 00:05 3691      /dev/dri/card0
ae8ba000-ae8c2000 rwxs 1291f8000 00:05 3691      /dev/dri/card0
ae8c2000-ae8ca000 rwxs 12a2a2000 00:05 3691      /dev/dri/card0
ae8ca000-ae8d2000 rwxs 129723000 00:05 3691      /dev/dri/card0
ae8d2000-ae8da000 rwxs 12975b000 00:05 3691      /dev/dri/card0
ae8da000-ae8e2000 rwxs 12973b000 00:05 3691      /dev/dri/card0
ae8e2000-ae8ea000 rwxs 1296d1000 00:05 3691      /dev/dri/card0
ae8ea000-ae8f2000 rwxs 129733000 00:05 3691      /dev/dri/card0
ae8f2000-ae8fa000 rwxs 1296a8000 00:05 3691      /dev/dri/card0
ae8fa000-ae902000 rwxs 129650000 00:05 3691      /dev/dri/card0
ae902000-ae90a000 rwxs 12997a000 00:05 3691      /dev/dri/card0
ae90a000-ae912000 rwxs 129972000 00:05 3691      /dev/dri/card0
ae912000-ae91a000 rwxs 129689000 00:05 3691      /dev/dri/card0
ae91a000-ae922000 rwxs 129680000 00:05 3691      /dev/dri/card0
ae922000-ae92a000 rwxs 129671000 00:05 3691      /dev/dri/card0
ae92a000-ae932000 rwxs 12907a000 00:05 3691      /dev/dri/card0
ae932000-ae93a000 rwxs 129669000 00:05 3691      /dev/dri/card0
ae93a000-ae942000 rwxs 12a321000 00:05 3691      /dev/dri/card0
ae942000-ae94a000 rwxs 129658000 00:05 3691      /dev/dri/card0
ae94a000-ae952000 rwxs 12a1f5000 00:05 3691      /dev/dri/card0
ae952000-ae95a000 rwxs 129648000 00:05 3691      /dev/dri/card0
ae95a000-ae962000 rwxs 129640000 00:05 3691      /dev/dri/card0
ae962000-ae96a000 rwxs 129638000 00:05 3691      /dev/dri/card0
ae96a000-ae972000 rwxs 129630000 00:05 3691      /dev/dri/card0
ae972000-ae97a000 rwxs 129628000 00:05 3691      /dev/dri/card0
ae97a000-ae982000 rwxs 129620000 00:05 3691      /dev/dri/card0
ae982000-ae98a000 rwxs 129618000 00:05 3691      /dev/dri/card0
ae98a000-ae992000 rwxs 129122000 00:05 3691      /dev/dri/card0
ae992000-ae99a000 rwxs 1290f2000 00:05 3691      /dev/dri/card0
ae99a000-ae9a2000 rwxs 1290ea000 00:05 3691      /dev/dri/card0
ae9a2000-ae9aa000 rwxs 1290e2000 00:05 3691      /dev/dri/card0
ae9aa000-ae9b2000 rwxs 12905a000 00:05 3691      /dev/dri/card0
ae9b2000-ae9ba000 rwxs 129052000 00:05 3691      /dev/dri/card0
ae9ba000-ae9c2000 rwxs 129610000 00:05 3691      /dev/dri/card0
ae9c2000-ae9ca000 rwxs 129178000 00:05 3691      /dev/dri/card0
ae9ca000-ae9d2000 rwxs 12971b000 00:05 3691      /dev/dri/card0
ae9d2000-ae9da000 rwxs 1291f0000 00:05 3691      /dev/dri/card0
ae9da000-ae9e2000 rwxs 1292ee000 00:05 3691      /dev/dri/card0
ae9e2000-ae9ea000 rwxs 129842000 00:05 3691      /dev/dri/card0
ae9ea000-ae9f2000 rwxs 129c75000 00:05 3691      /dev/dri/card0
ae9f2000-ae9fa000 rwxs 12959a000 00:05 3691      /dev/dri/card0
ae9fa000-aea02000 rwxs 12a319000 00:05 3691      /dev/dri/card0
aea02000-aea0a000 rwxs 1295c2000 00:05 3691      /dev/dri/card0
aea0a000-aea12000 rwxs 129582000 00:05 3691      /dev/dri/card0
aea12000-aea1a000 rwxs 12957a000 00:05 3691      /dev/dri/card0
aea1a000-aea22000 rwxs 129572000 00:05 3691      /dev/dri/card0
aea22000-aea2a000 rwxs 12956a000 00:05 3691      /dev/dri/card0
aea2a000-aea32000 rwxs 129562000 00:05 3691      /dev/dri/card0
aea32000-aea3a000 rwxs 12955a000 00:05 3691      /dev/dri/card0
aea3a000-aea42000 rwxs 129552000 00:05 3691      /dev/dri/card0
aea42000-aea4a000 rwxs 12954a000 00:05 3691      /dev/dri/card0
aea4a000-aea52000 rwxs 129542000 00:05 3691      /dev/dri/card0
aea52000-aea5a000 rwxs 12953a000 00:05 3691      /dev/dri/card0
aea5a000-aea62000 rwxs 129532000 00:05 3691      /dev/dri/card0
aea62000-aea6a000 rwxs 12952a000 00:05 3691      /dev/dri/card0
aea6a000-aea72000 rwxs 129522000 00:05 3691      /dev/dri/card0
aea72000-aea7a000 rwxs 12951a000 00:05 3691      /dev/dri/card0
aea7a000-aea82000 rwxs 129512000 00:05 3691      /dev/dri/card0
aea82000-aea8a000 rwxs 12950a000 00:05 3691      /dev/dri/card0
aea8a000-aea92000 rwxs 129502000 00:05 3691      /dev/dri/card0
aea92000-aea9a000 rwxs 1294fa000 00:05 3691      /dev/dri/card0
aea9a000-aeaa2000 rwxs 1294f2000 00:05 3691      /dev/dri/card0
aeaa2000-aeaaa000 rwxs 1294ea000 00:05 3691      /dev/dri/card0
aeaaa000-aeab2000 rwxs 1294e2000 00:05 3691      /dev/dri/card0
aeab2000-aeaba000 rwxs 129bee000 00:05 3691      /dev/dri/card0
aeaba000-aeac2000 rwxs 129c8d000 00:05 3691      /dev/dri/card0
aeac2000-aeaca000 rwxs 1294ca000 00:05 3691      /dev/dri/card0
aeaca000-aead2000 rwxs 1294c2000 00:05 3691      /dev/dri/card0
aead2000-aeada000 rwxs 1294ba000 00:05 3691      /dev/dri/card0
aeada000-aeae2000 rwxs 1294b2000 00:05 3691      /dev/dri/card0
aeae2000-aeaea000 rwxs 129c85000 00:05 3691      /dev/dri/card0
aeaea000-aeaf2000 rwxs 129c5d000 00:05 3691      /dev/dri/card0
aeaf2000-aeafa000 rwxs 12948a000 00:05 3691      /dev/dri/card0
aeafa000-aeb02000 rwxs 129482000 00:05 3691      /dev/dri/card0
aeb02000-aeb0a000 rwxs 12947a000 00:05 3691      /dev/dri/card0
aeb0a000-aeb12000 rwxs 129472000 00:05 3691      /dev/dri/card0
aeb12000-aeb1a000 rwxs 12946a000 00:05 3691      /dev/dri/card0
aeb1a000-aeb22000 rwxs 129462000 00:05 3691      /dev/dri/card0
aeb22000-aeb2a000 rwxs 12945a000 00:05 3691      /dev/dri/card0
aeb2a000-aeb32000 rwxs 129452000 00:05 3691      /dev/dri/card0
aeb32000-aeb3a000 rwxs 12944a000 00:05 3691      /dev/dri/card0
aeb3a000-aeb42000 rwxs 129442000 00:05 3691      /dev/dri/card0
aeb42000-aeb4a000 rwxs 12943a000 00:05 3691      /dev/dri/card0
aeb4a000-aeb52000 rwxs 1293fd000 00:05 3691      /dev/dri/card0
aeb52000-aeb5a000 rwxs 1293f5000 00:05 3691      /dev/dri/card0
aeb5a000-aeb62000 rwxs 129432000 00:05 3691      /dev/dri/card0
aeb62000-aeb6a000 rwxs 12942a000 00:05 3691      /dev/dri/card0
aeb6a000-aeb72000 rwxs 129422000 00:05 3691      /dev/dri/card0
aeb72000-aeb7a000 rwxs 1293ed000 00:05 3691      /dev/dri/card0
aeb7a000-aeb82000 rwxs 1293e5000 00:05 3691      /dev/dri/card0
aeb82000-aeb8a000 rwxs 1293dd000 00:05 3691      /dev/dri/card0
aeb8a000-aeb92000 rwxs 1293d5000 00:05 3691      /dev/dri/card0
aeb92000-aeb9a000 rwxs 12941a000 00:05 3691      /dev/dri/card0
aeb9a000-aeba2000 rwxs 129412000 00:05 3691      /dev/dri/card0
aeba2000-aebaa000 rwxs 129405000 00:05 3691      /dev/dri/card0
aebaa000-aebb2000 rwxs 12977c000 00:05 3691      /dev/dri/card0
aebb2000-aebba000 rwxs 1293c5000 00:05 3691      /dev/dri/card0
aebba000-aebc2000 rwxs 1293bd000 00:05 3691      /dev/dri/card0
aebc2000-aebca000 rwxs 1293b5000 00:05 3691      /dev/dri/card0
aebca000-aebd2000 rwxs 1293ac000 00:05 3691      /dev/dri/card0
aebd2000-aebda000 rwxs 1293a4000 00:05 3691      /dev/dri/card0
aebda000-aebe2000 rwxs 12939c000 00:05 3691      /dev/dri/card0
aebe2000-aebea000 rwxs 129394000 00:05 3691      /dev/dri/card0
aebea000-aebf2000 rwxs 12938c000 00:05 3691      /dev/dri/card0
aebf2000-aebfa000 rwxs 12932e000 00:05 3691      /dev/dri/card0
aebfa000-aec02000 rwxs 129384000 00:05 3691      /dev/dri/card0
aec02000-aec0a000 rwxs 12937c000 00:05 3691      /dev/dri/card0
aec0a000-aec12000 rwxs 129374000 00:05 3691      /dev/dri/card0
aec12000-aec1a000 rwxs 129326000 00:05 3691      /dev/dri/card0
aec1a000-aec22000 rwxs 12931e000 00:05 3691      /dev/dri/card0
aec22000-aec2a000 rwxs 129316000 00:05 3691      /dev/dri/card0
aec2a000-aec32000 rwxs 12930e000 00:05 3691      /dev/dri/card0
aec32000-aec3a000 rwxs 129306000 00:05 3691      /dev/dri/card0
aec3a000-aec42000 rwxs 12936c000 00:05 3691      /dev/dri/card0
aec42000-aec4a000 rwxs 129364000 00:05 3691      /dev/dri/card0
aec4a000-aec52000 rwxs 12935c000 00:05 3691      /dev/dri/card0
aec52000-aec5a000 rwxs 129354000 00:05 3691      /dev/dri/card0
aec5a000-aec62000 rwxs 12934c000 00:05 3691      /dev/dri/card0
aec62000-aec6a000 rwxs 129344000 00:05 3691      /dev/dri/card0
aec6a000-aec72000 rwxs 12933c000 00:05 3691      /dev/dri/card0
aec72000-aec7a000 rwxs 128afe000 00:05 3691      /dev/dri/card0
aec7a000-aec82000 rwxs 1284f0000 00:05 3691      /dev/dri/card0
aec82000-aec8a000 rwxs 1292fe000 00:05 3691      /dev/dri/card0
aec8a000-aec92000 rwxs 129208000 00:05 3691      /dev/dri/card0
aec92000-aec9a000 rwxs 1280f0000 00:05 3691      /dev/dri/card0
aec9a000-aeca2000 rwxs 1280d8000 00:05 3691      /dev/dri/card0
aeca2000-aecaa000 rwxs 1280d0000 00:05 3691      /dev/dri/card0
aecaa000-aecb2000 rwxs 1280c8000 00:05 3691      /dev/dri/card0
aecb2000-aecc2000 rwxs 1292c6000 00:05 3691      /dev/dri/card0
aecc2000-aecca000 rwxs 1292be000 00:05 3691      /dev/dri/card0
aecca000-aecd2000 rwxs 1292b6000 00:05 3691      /dev/dri/card0
aecd2000-aecda000 rwxs 1292ae000 00:05 3691      /dev/dri/card0
aecda000-aece2000 rwxs 1292a6000 00:05 3691      /dev/dri/card0
aece2000-aecea000 rwxs 129252000 00:05 3691      /dev/dri/card0
aecea000-aecf2000 rwxs 12924a000 00:05 3691      /dev/dri/card0
aecf2000-aecfa000 rwxs 129242000 00:05 3691      /dev/dri/card0
aecfa000-aed02000 rwxs 129239000 00:05 3691      /dev/dri/card0
aed02000-aed0a000 rwxs 129231000 00:05 3691      /dev/dri/card0
aed0a000-aed12000 rwxs 129229000 00:05 3691      /dev/dri/card0
aed12000-aed1a000 rwxs 12929e000 00:05 3691      /dev/dri/card0
aed1a000-aed22000 rwxs 129296000 00:05 3691      /dev/dri/card0
aed22000-aed2a000 rwxs 12928e000 00:05 3691      /dev/dri/card0
aed2a000-aed32000 rwxs 129286000 00:05 3691      /dev/dri/card0
aed32000-aed3a000 rwxs 12927e000 00:05 3691      /dev/dri/card0
aed3a000-aed42000 rwxs 129276000 00:05 3691      /dev/dri/card0
aed42000-aed4a000 rwxs 12926e000 00:05 3691      /dev/dri/card0
aed4a000-aed52000 rwxs 129266000 00:05 3691      /dev/dri/card0
aed52000-aed5a000 rwxs 12925e000 00:05 3691      /dev/dri/card0
aed5a000-aed62000 rwxs 129220000 00:05 3691      /dev/dri/card0
aed62000-aed6a000 rwxs 129210000 00:05 3691      /dev/dri/card0
aed6a000-aed72000 rwxs 1280e8000 00:05 3691      /dev/dri/card0
aed72000-aed7a000 rwxs 1289ce000 00:05 3691      /dev/dri/card0
aed7a000-aed82000 rwxs 126f4f000 00:05 3691      /dev/dri/card0
aed82000-aed8a000 rwxs 129892000 00:05 3691      /dev/dri/card0
aed8a000-aed92000 rwxs 1285a8000 00:05 3691      /dev/dri/card0
aed92000-aed9a000 rwxs 1291e8000 00:05 3691      /dev/dri/card0
aed9a000-aeda2000 rwxs 1291e0000 00:05 3691      /dev/dri/card0
aeda2000-aedaa000 rwxs 1291d8000 00:05 3691      /dev/dri/card0
aedaa000-aedb2000 rwxs 1291d0000 00:05 3691      /dev/dri/card0
aedb2000-aedba000 rwxs 1291c8000 00:05 3691      /dev/dri/card0
aedba000-aedc2000 rwxs 1291c0000 00:05 3691      /dev/dri/card0
aedc2000-aedca000 rwxs 1291b8000 00:05 3691      /dev/dri/card0
aedca000-aedd2000 rwxs 1291b0000 00:05 3691      /dev/dri/card0
aedd2000-aedda000 rwxs 1291a8000 00:05 3691      /dev/dri/card0
aedda000-aede2000 rwxs 129198000 00:05 3691      /dev/dri/card0
aede2000-aedea000 rwxs 129190000 00:05 3691      /dev/dri/card0
aedea000-aedf2000 rwxs 129592000 00:05 3691      /dev/dri/card0
aedf2000-aedfa000 rwxs 129170000 00:05 3691      /dev/dri/card0
aedfa000-aee02000 rwxs 1289d6000 00:05 3691      /dev/dri/card0
aee02000-aee0a000 rwxs 129102000 00:05 3691      /dev/dri/card0
aee0a000-aee12000 rwxs 1296fb000 00:05 3691      /dev/dri/card0
aee12000-aee1a000 rwxs 129168000 00:05 3691      /dev/dri/card0
aee1a000-aee22000 rwxs 129160000 00:05 3691      /dev/dri/card0
aee22000-aee2a000 rwxs 129158000 00:05 3691      /dev/dri/card0
aee2a000-aee32000 rwxs 129150000 00:05 3691      /dev/dri/card0
aee32000-aee3a000 rwxs 129148000 00:05 3691      /dev/dri/card0
aee3a000-aee42000 rwxs 129140000 00:05 3691      /dev/dri/card0
aee42000-aee4a000 rwxs 129130000 00:05 3691      /dev/dri/card0
aee4a000-aee52000 rwxs 129603000 00:05 3691      /dev/dri/card0
aee52000-aee5a000 rwxs 1295fb000 00:05 3691      /dev/dri/card0
aee5a000-aee62000 rwxs 1295f3000 00:05 3691      /dev/dri/card0
aee62000-aee6a000 rwxs 1290da000 00:05 3691      /dev/dri/card0
aee6a000-aee72000 rwxs 1290d2000 00:05 3691      /dev/dri/card0
aee72000-aee7a000 rwxs 1290ca000 00:05 3691      /dev/dri/card0
aee7a000-aee82000 rwxs 1290c2000 00:05 3691      /dev/dri/card0
aee82000-aee8a000 rwxs 1290ba000 00:05 3691      /dev/dri/card0
aee8a000-aee92000 rwxs 1290b2000 00:05 3691      /dev/dri/card0
aee92000-aee9a000 rwxs 1290aa000 00:05 3691      /dev/dri/card0
aee9a000-aeea2000 rwxs 1290a2000 00:05 3691      /dev/dri/card0
aeea2000-aeeaa000 rwxs 12909a000 00:05 3691      /dev/dri/card0
aeeaa000-aeeb2000 rwxs 129092000 00:05 3691      /dev/dri/card0
aeeb2000-aeeba000 rwxs 129fac000 00:05 3691      /dev/dri/card0
aeeba000-aeec2000 rwxs 129cfc000 00:05 3691      /dev/dri/card0
aeec2000-aeeca000 rwxs 129cf4000 00:05 3691      /dev/dri/card0
aeeca000-aeed2000 rwxs 129cae000 00:05 3691      /dev/dri/card0
aeed2000-aeeda000 rwxs 129ca6000 00:05 3691      /dev/dri/card0
aeeda000-aeee2000 rwxs 1295eb000 00:05 3691      /dev/dri/card0
aeee2000-aeeea000 rwxs 129200000 00:05 3691      /dev/dri/card0
aeeea000-aeef2000 rwxs 12904a000 00:05 3691      /dev/dri/card0
aeef2000-aeefa000 rwxs 129042000 00:05 3691      /dev/dri/card0
aeefa000-aef02000 rwxs 12903a000 00:05 3691      /dev/dri/card0
aef02000-aef0a000 rwxs 129032000 00:05 3691      /dev/dri/card0
aef0a000-aef12000 rwxs 12902a000 00:05 3691      /dev/dri/card0
aef12000-aef1a000 rwxs 129022000 00:05 3691      /dev/dri/card0
aef1a000-aef22000 rwxs 12901a000 00:05 3691      /dev/dri/card0
aef22000-aef2a000 rwxs 129012000 00:05 3691      /dev/dri/card0
aef2a000-aef32000 rwxs 12900a000 00:05 3691      /dev/dri/card0
aef32000-aef3a000 rwxs 129002000 00:05 3691      /dev/dri/card0
aef3a000-aef42000 rwxs 128ffa000 00:05 3691      /dev/dri/card0
aef42000-aef4a000 rwxs 128ff2000 00:05 3691      /dev/dri/card0
aef4a000-aef52000 rwxs 128fea000 00:05 3691      /dev/dri/card0
aef52000-aef5a000 rwxs 128fe2000 00:05 3691      /dev/dri/card0
aef5a000-aef62000 rwxs 128fda000 00:05 3691      /dev/dri/card0
aef62000-aef6a000 rwxs 128fd2000 00:05 3691      /dev/dri/card0
aef6a000-aef72000 rwxs 128fca000 00:05 3691      /dev/dri/card0
aef72000-aef7a000 rwxs 128fc2000 00:05 3691      /dev/dri/card0
aef7a000-aef82000 rwxs 128fba000 00:05 3691      /dev/dri/card0
aef82000-aef8a000 rwxs 128fb2000 00:05 3691      /dev/dri/card0
aef8a000-aef92000 rwxs 128faa000 00:05 3691      /dev/dri/card0
aef92000-aef9a000 rwxs 128fa2000 00:05 3691      /dev/dri/card0
aef9a000-aefa2000 rwxs 128f85000 00:05 3691      /dev/dri/card0
aefa2000-aefaa000 rwxs 128f7d000 00:05 3691      /dev/dri/card0
aefaa000-aefb2000 rwxs 128f75000 00:05 3691      /dev/dri/card0
aefb2000-aefba000 rwxs 128f6d000 00:05 3691      /dev/dri/card0
aefba000-aefc2000 rwxs 128f65000 00:05 3691      /dev/dri/card0
aefc2000-aefca000 rwxs 128f5d000 00:05 3691      /dev/dri/card0
aefca000-aefd2000 rwxs 128f9a000 00:05 3691      /dev/dri/card0
aefd2000-aefda000 rwxs 128f92000 00:05 3691      /dev/dri/card0
aefda000-aefe2000 rwxs 128f54000 00:05 3691      /dev/dri/card0
aefe2000-aefea000 rwxs 128f4c000 00:05 3691      /dev/dri/card0
aefec000-aeff4000 rwxs 128f42000 00:05 3691      /dev/dri/card0
aeff4000-af00a000 rwxs 128f2c000 00:05 3691      /dev/dri/card0
af00a000-af012000 rwxs 128f24000 00:05 3691      /dev/dri/card0
af012000-af01a000 rwxs 128f1c000 00:05 3691      /dev/dri/card0
af01a000-af022000 rwxs 128f14000 00:05 3691      /dev/dri/card0
af022000-af02a000 rwxs 128f0c000 00:05 3691      /dev/dri/card0
af02a000-af032000 rwxs 128f04000 00:05 3691      /dev/dri/card0
af032000-af03a000 rwxs 128efc000 00:05 3691      /dev/dri/card0
af03a000-af042000 rwxs 128ef4000 00:05 3691      /dev/dri/card0
af042000-af04a000 rwxs 128eec000 00:05 3691      /dev/dri/card0
af04a000-af052000 rwxs 128ee4000 00:05 3691      /dev/dri/card0
af052000-af05a000 rwxs 128edc000 00:05 3691      /dev/dri/card0
af05a000-af062000 rwxs 128ed4000 00:05 3691      /dev/dri/card0
af062000-af06a000 rwxs 128ecc000 00:05 3691      /dev/dri/card0
af06a000-af072000 rwxs 128ec4000 00:05 3691      /dev/dri/card0
af072000-af07a000 rwxs 128ebc000 00:05 3691      /dev/dri/card0
af07a000-af082000 rwxs 128eb4000 00:05 3691      /dev/dri/card0
af082000-af08a000 rwxs 128eac000 00:05 3691      /dev/dri/card0
af08a000-af092000 rwxs 128ea4000 00:05 3691      /dev/dri/card0
af092000-af09a000 rwxs 128e9c000 00:05 3691      /dev/dri/card0
af09a000-af0a2000 rwxs 128e6e000 00:05 3691      /dev/dri/card0
af0a2000-af0aa000 rwxs 128e66000 00:05 3691      /dev/dri/card0
af0aa000-af0b2000 rwxs 128e5e000 00:05 3691      /dev/dri/card0
af0b2000-af0ba000 rwxs 128e56000 00:05 3691      /dev/dri/card0
af0ba000-af0c2000 rwxs 128e4e000 00:05 3691      /dev/dri/card0
af0c2000-af0ca000 rwxs 128e46000 00:05 3691      /dev/dri/card0
af0ca000-af0d2000 rwxs 128e94000 00:05 3691      /dev/dri/card0
af0d2000-af0da000 rwxs 128e8c000 00:05 3691      /dev/dri/card0
af0da000-af0e2000 rwxs 128e84000 00:05 3691      /dev/dri/card0
af0e2000-af0ea000 rwxs 128e7c000 00:05 3691      /dev/dri/card0
af0ea000-af0f2000 rwxs 128e11000 00:05 3691      /dev/dri/card0
af0f2000-af0fa000 rwxs 128e09000 00:05 3691      /dev/dri/card0
af0fa000-af102000 rwxs 128e01000 00:05 3691      /dev/dri/card0
af102000-af10a000 rwxs 128df9000 00:05 3691      /dev/dri/card0
af10a000-af112000 rwxs 128df1000 00:05 3691      /dev/dri/card0
af112000-af11a000 rwxs 128de9000 00:05 3691      /dev/dri/card0
af11a000-af122000 rwxs 128e3e000 00:05 3691      /dev/dri/card0
af122000-af12a000 rwxs 128e36000 00:05 3691      /dev/dri/card0
af12a000-af132000 rwxs 128e2e000 00:05 3691      /dev/dri/card0
af132000-af13a000 rwxs 128e26000 00:05 3691      /dev/dri/card0
af13a000-af142000 rwxs 128e1e000 00:05 3691      /dev/dri/card0
af142000-af14a000 rwxs 128c4a000 00:05 3691      /dev/dri/card0
af14a000-af152000 rwxs 128c42000 00:05 3691      /dev/dri/card0
af152000-af15a000 rwxs 128c3a000 00:05 3691      /dev/dri/card0
af15a000-af162000 rwxs 128c32000 00:05 3691      /dev/dri/card0
af162000-af16a000 rwxs 128c2a000 00:05 3691      /dev/dri/card0
af16a000-af172000 rwxs 128c22000 00:05 3691      /dev/dri/card0
af172000-af17a000 rwxs 128de0000 00:05 3691      /dev/dri/card0
af17a000-af182000 rwxs 12a2b2000 00:05 3691      /dev/dri/card0
af182000-af18a000 rwxs 128dcb000 00:05 3691      /dev/dri/card0
af18a000-af192000 rwxs 128dc3000 00:05 3691      /dev/dri/card0
af192000-af19a000 rwxs 128dbb000 00:05 3691      /dev/dri/card0
af19a000-af1a2000 rwxs 128db3000 00:05 3691      /dev/dri/card0
af1a2000-af1aa000 rwxs 128d7a000 00:05 3691      /dev/dri/card0
af1aa000-af1b2000 rwxs 128d72000 00:05 3691      /dev/dri/card0
af1b2000-af1ba000 rwxs 128d6a000 00:05 3691      /dev/dri/card0
af1ba000-af1c2000 rwxs 128d62000 00:05 3691      /dev/dri/card0
af1c2000-af1ca000 rwxs 128d5a000 00:05 3691      /dev/dri/card0
af1ca000-af1d2000 rwxs 128d52000 00:05 3691      /dev/dri/card0
af1d2000-af1da000 rwxs 128d4a000 00:05 3691      /dev/dri/card0
af1da000-af1e2000 rwxs 128d3a000 00:05 3691      /dev/dri/card0
af1e2000-af1ea000 rwxs 12a0f1000 00:05 3691      /dev/dri/card0
af1ea000-af1f2000 rwxs 128639000 00:05 3691      /dev/dri/card0
af1f2000-af1fa000 rwxs 128d22000 00:05 3691      /dev/dri/card0
af1fa000-af202000 rwxs 128d1a000 00:05 3691      /dev/dri/card0
af202000-af20a000 rwxs 128d12000 00:05 3691      /dev/dri/card0
af20a000-af212000 rwxs 128d0a000 00:05 3691      /dev/dri/card0
af212000-af21a000 rwxs 128d02000 00:05 3691      /dev/dri/card0
af21a000-af222000 rwxs 128cfa000 00:05 3691      /dev/dri/card0
af222000-af22a000 rwxs 128cf2000 00:05 3691      /dev/dri/card0
af22a000-af232000 rwxs 128cea000 00:05 3691      /dev/dri/card0
af232000-af23a000 rwxs 128ce2000 00:05 3691      /dev/dri/card0
af23a000-af242000 rwxs 128cda000 00:05 3691      /dev/dri/card0
af242000-af24a000 rwxs 128cd2000 00:05 3691      /dev/dri/card0
af24a000-af252000 rwxs 128cca000 00:05 3691      /dev/dri/card0
af252000-af25a000 rwxs 128cc2000 00:05 3691      /dev/dri/card0
af25a000-af262000 rwxs 128cba000 00:05 3691      /dev/dri/card0
af262000-af26a000 rwxs 128cb2000 00:05 3691      /dev/dri/card0
af26a000-af272000 rwxs 128caa000 00:05 3691      /dev/dri/card0
af272000-af27a000 rwxs 128ca2000 00:05 3691      /dev/dri/card0
af27a000-af282000 rwxs 128c9a000 00:05 3691      /dev/dri/card0
af282000-af28a000 rwxs 128c92000 00:05 3691      /dev/dri/card0
af28a000-af292000 rwxs 128c8a000 00:05 3691      /dev/dri/card0
af292000-af29a000 rwxs 128c82000 00:05 3691      /dev/dri/card0
af29a000-af2a2000 rwxs 128c7a000 00:05 3691      /dev/dri/card0
af2a2000-af2aa000 rwxs 128c72000 00:05 3691      /dev/dri/card0
af2aa000-af2b2000 rwxs 128c6a000 00:05 3691      /dev/dri/card0
af2b2000-af2ba000 rwxs 128c62000 00:05 3691      /dev/dri/card0
af2ba000-af2c2000 rwxs 128c5a000 00:05 3691      /dev/dri/card0
af2c2000-af2ca000 rwxs 128c52000 00:05 3691      /dev/dri/card0
af2ca000-af2d2000 rwxs 128dab000 00:05 3691      /dev/dri/card0
af2d2000-af2da000 rwxs 128da3000 00:05 3691      /dev/dri/card0
af2da000-af2e2000 rwxs 128d9b000 00:05 3691      /dev/dri/card0
af2e2000-af2ea000 rwxs 128d93000 00:05 3691      /dev/dri/card0
af2ea000-af2f2000 rwxs 128d8b000 00:05 3691      /dev/dri/card0
af2f2000-af2fa000 rwxs 128d83000 00:05 3691      /dev/dri/card0
af2fa000-af302000 rwxs 128c1a000 00:05 3691      /dev/dri/card0
af302000-af30a000 rwxs 128c12000 00:05 3691      /dev/dri/card0
af30a000-af312000 rwxs 128c0a000 00:05 3691      /dev/dri/card0
af312000-af31a000 rwxs 128c02000 00:05 3691      /dev/dri/card0
af31a000-af322000 rwxs 12a384000 00:05 3691      /dev/dri/card0
af322000-af32a000 rwxs 128bf2000 00:05 3691      /dev/dri/card0
af32a000-af332000 rwxs 128bea000 00:05 3691      /dev/dri/card0
af332000-af33a000 rwxs 12a35f000 00:05 3691      /dev/dri/card0
af33a000-af342000 rwxs 12a357000 00:05 3691      /dev/dri/card0
af342000-af34a000 rwxs 12a34f000 00:05 3691      /dev/dri/card0
af34a000-af352000 rwxs 12a347000 00:05 3691      /dev/dri/card0
af352000-af35a000 rwxs 12a33f000 00:05 3691      /dev/dri/card0
af35a000-af362000 rwxs 12a337000 00:05 3691      /dev/dri/card0
af362000-af36a000 rwxs 128bda000 00:05 3691      /dev/dri/card0
af36a000-af372000 rwxs 128bd2000 00:05 3691      /dev/dri/card0
af372000-af37a000 rwxs 128b94000 00:05 3691      /dev/dri/card0
af37a000-af382000 rwxs 12784d000 00:05 3691      /dev/dri/card0
af382000-af38a000 rwxs 128b0f000 00:05 3691      /dev/dri/card0
af38a000-af392000 rwxs 128b07000 00:05 3691      /dev/dri/card0
af392000-af39a000 rwxs 128b7d000 00:05 3691      /dev/dri/card0
af39a000-af3a2000 rwxs 128b75000 00:05 3691      /dev/dri/card0
af3a2000-af3aa000 rwxs 128b6c000 00:05 3691      /dev/dri/card0
af3aa000-af3b2000 rwxs 128b64000 00:05 3691      /dev/dri/card0
af3b2000-af3ba000 rwxs 128b5c000 00:05 3691      /dev/dri/card0
af3ba000-af3c2000 rwxs 1285f8000 00:05 3691      /dev/dri/card0
af3c2000-af3ca000 rwxs 1267c7000 00:05 3691      /dev/dri/card0
af3ca000-af3d2000 rwxs 128af6000 00:05 3691      /dev/dri/card0
af3d2000-af3da000 rwxs 128aee000 00:05 3691      /dev/dri/card0
af3da000-af3e2000 rwxs 128b34000 00:05 3691      /dev/dri/card0
af3e2000-af3ea000 rwxs 128b2c000 00:05 3691      /dev/dri/card0
af3ea000-af3f2000 rwxs 128b24000 00:05 3691      /dev/dri/card0
af3f2000-af3fa000 rwxs 128b1c000 00:05 3691      /dev/dri/card0
af3fa000-af402000 rwxs 128ac1000 00:05 3691      /dev/dri/card0
af402000-af40a000 rwxs 128ab9000 00:05 3691      /dev/dri/card0
af40a000-af412000 rwxs 128ab1000 00:05 3691      /dev/dri/card0
af412000-af41a000 rwxs 128aa9000 00:05 3691      /dev/dri/card0
af41a000-af422000 rwxs 128aa1000 00:05 3691      /dev/dri/card0
af422000-af42a000 rwxs 128a99000 00:05 3691      /dev/dri/card0
af42a000-af432000 rwxs 128ade000 00:05 3691      /dev/dri/card0
af432000-af43a000 rwxs 128ad6000 00:05 3691      /dev/dri/card0
af43a000-af442000 rwxs 128ace000 00:05 3691      /dev/dri/card0
af442000-af44a000 rwxs 128a90000 00:05 3691      /dev/dri/card0
af44a000-af452000 rwxs 128a88000 00:05 3691      /dev/dri/card0
af452000-af45a000 rwxs 128a22000 00:05 3691      /dev/dri/card0
af45a000-af462000 rwxs 128a1a000 00:05 3691      /dev/dri/card0
af462000-af46a000 rwxs 128a12000 00:05 3691      /dev/dri/card0
af46a000-af472000 rwxs 128a0a000 00:05 3691      /dev/dri/card0
af472000-af475000 rwxs 128a06000 00:05 3691      /dev/dri/card0
af475000-af47d000 rwxs 1289fe000 00:05 3691      /dev/dri/card0
af47d000-af485000 rwxs 128a80000 00:05 3691      /dev/dri/card0
af485000-af48d000 rwxs 128a78000 00:05 3691      /dev/dri/card0
af48d000-af495000 rwxs 128a70000 00:05 3691      /dev/dri/card0
af495000-af49d000 rwxs 128a68000 00:05 3691      /dev/dri/card0
af49d000-af4a5000 rwxs 128a60000 00:05 3691      /dev/dri/card0
af4a5000-af4ad000 rwxs 128a58000 00:05 3691      /dev/dri/card0
af4ad000-af4b5000 rwxs 128a50000 00:05 3691      /dev/dri/card0
af4b5000-af4bd000 rwxs 128a48000 00:05 3691      /dev/dri/card0
af4bd000-af4c5000 rwxs 128a40000 00:05 3691      /dev/dri/card0
af4c5000-af4cd000 rwxs 128a38000 00:05 3691      /dev/dri/card0
af4cd000-af4d5000 rwxs 128977000 00:05 3691      /dev/dri/card0
af4d5000-af4dd000 rwxs 128a30000 00:05 3691      /dev/dri/card0
af4dd000-af4e5000 rwxs 1288f0000 00:05 3691      /dev/dri/card0
af4e5000-af4ed000 rwxs 1288e8000 00:05 3691      /dev/dri/card0
af4ed000-af4f5000 rwxs 1288e0000 00:05 3691      /dev/dri/card0
af4f5000-af4fd000 rwxs 1289df000 00:05 3691      /dev/dri/card0
af502000-af505000 rwxs 12910a000 00:05 3691      /dev/dri/card0
af505000-af50d000 rwxs 1289f2000 00:05 3691      /dev/dri/card0
af50d000-af515000 rwxs 1288d8000 00:05 3691      /dev/dri/card0
af515000-af51d000 rwxs 1289e7000 00:05 3691      /dev/dri/card0
af51d000-af525000 rwxs 128be2000 00:05 3691      /dev/dri/card0
af525000-af52d000 rwxs 128966000 00:05 3691      /dev/dri/card0
af52d000-af535000 rwxs 12895e000 00:05 3691      /dev/dri/card0
af535000-af53d000 rwxs 128956000 00:05 3691      /dev/dri/card0
af53d000-af545000 rwxs 12894e000 00:05 3691      /dev/dri/card0
af545000-af54d000 rwxs 1289ac000 00:05 3691      /dev/dri/card0
af54d000-af555000 rwxs 1289a4000 00:05 3691      /dev/dri/card0
af555000-af55d000 rwxs 12899c000 00:05 3691      /dev/dri/card0
af55d000-af565000 rwxs 128994000 00:05 3691      /dev/dri/card0
af565000-af56d000 rwxs 12898c000 00:05 3691      /dev/dri/card0
af56d000-af575000 rwxs 128984000 00:05 3691      /dev/dri/card0
af575000-af57d000 rwxs 127201000 00:05 3691      /dev/dri/card0
af57d000-af585000 rwxs 128939000 00:05 3691      /dev/dri/card0
af585000-af58d000 rwxs 128931000 00:05 3691      /dev/dri/card0
af58d000-af595000 rwxs 128929000 00:05 3691      /dev/dri/card0
af595000-af59d000 rwxs 128921000 00:05 3691      /dev/dri/card0
af59d000-af5a5000 rwxs 128919000 00:05 3691      /dev/dri/card0
af5a5000-af5ad000 rwxs 128911000 00:05 3691      /dev/dri/card0
af5ad000-af5b0000 rwxs 127f63000 00:05 3691      /dev/dri/card0
af5b0000-af5b8000 rwxs 128946000 00:05 3691      /dev/dri/card0
af5b8000-af5c0000 rwxs 128908000 00:05 3691      /dev/dri/card0
af5c0000-af5c8000 rwxs 1288f8000 00:05 3691      /dev/dri/card0
af5c8000-af5d0000 rwxs 128d42000 00:05 3691      /dev/dri/card0
af5d0000-af5d8000 rwxs 1289c6000 00:05 3691      /dev/dri/card0
af5d8000-af5e0000 rwxs 1289bd000 00:05 3691      /dev/dri/card0
af5e0000-af5e8000 rwxs 1289b5000 00:05 3691      /dev/dri/card0
af5e8000-af5f0000 rwxs 1288d0000 00:05 3691      /dev/dri/card0
af5f0000-af5f8000 rwxs 1288c8000 00:05 3691      /dev/dri/card0
af5f8000-af600000 rwxs 1288c0000 00:05 3691      /dev/dri/card0
af600000-af608000 rwxs 1288b8000 00:05 3691      /dev/dri/card0
af608000-af610000 rwxs 1288b0000 00:05 3691      /dev/dri/card0
af610000-af618000 rwxs 1288a8000 00:05 3691      /dev/dri/card0
af618000-af620000 rwxs 1288a0000 00:05 3691      /dev/dri/card0
af620000-af628000 rwxs 128898000 00:05 3691      /dev/dri/card0
af628000-af630000 rwxs 128890000 00:05 3691      /dev/dri/card0
af630000-af638000 rwxs 128888000 00:05 3691      /dev/dri/card0
af638000-af640000 rwxs 128880000 00:05 3691      /dev/dri/card0
af640000-af648000 rwxs 128878000 00:05 3691      /dev/dri/card0
af648000-af650000 rwxs 128870000 00:05 3691      /dev/dri/card0
af650000-af658000 rwxs 128868000 00:05 3691      /dev/dri/card0
af658000-af660000 rwxs 128860000 00:05 3691      /dev/dri/card0
af660000-af668000 rwxs 128858000 00:05 3691      /dev/dri/card0
af668000-af670000 rwxs 128850000 00:05 3691      /dev/dri/card0
af670000-af678000 rwxs 128848000 00:05 3691      /dev/dri/card0
af678000-af680000 rwxs 128840000 00:05 3691      /dev/dri/card0
af680000-af688000 rwxs 128838000 00:05 3691      /dev/dri/card0
af688000-af690000 rwxs 128830000 00:05 3691      /dev/dri/card0
af690000-af698000 rwxs 128828000 00:05 3691      /dev/dri/card0
af698000-af6a0000 rwxs 128820000 00:05 3691      /dev/dri/card0
af6a0000-af6a8000 rwxs 128818000 00:05 3691      /dev/dri/card0
af6a8000-af6b0000 rwxs 128810000 00:05 3691      /dev/dri/card0
af6b0000-af6b8000 rwxs 128808000 00:05 3691      /dev/dri/card0
af6b8000-af6c0000 rwxs 128800000 00:05 3691      /dev/dri/card0
af6c0000-af6c8000 rwxs 1287f8000 00:05 3691      /dev/dri/card0
af6c8000-af6d0000 rwxs 1287f0000 00:05 3691      /dev/dri/card0
af6d0000-af6d8000 rwxs 1287e8000 00:05 3691      /dev/dri/card0
af6d8000-af6e0000 rwxs 1287e0000 00:05 3691      /dev/dri/card0
af6e0000-af6e8000 rwxs 1287d8000 00:05 3691      /dev/dri/card0
af6e8000-af6f0000 rwxs 1287d0000 00:05 3691      /dev/dri/card0
af6f0000-af6f8000 rwxs 1287c8000 00:05 3691      /dev/dri/card0
af6f8000-af700000 rwxs 1287c0000 00:05 3691      /dev/dri/card0
af700000-af708000 rwxs 1287b8000 00:05 3691      /dev/dri/card0
af708000-af710000 rwxs 1287b0000 00:05 3691      /dev/dri/card0
af710000-af718000 rwxs 1287a8000 00:05 3691      /dev/dri/card0
af718000-af720000 rwxs 1287a0000 00:05 3691      /dev/dri/card0
af720000-af728000 rwxs 128900000 00:05 3691      /dev/dri/card0
af728000-af730000 rwxs 128790000 00:05 3691      /dev/dri/card0
af730000-af738000 rwxs 128788000 00:05 3691      /dev/dri/card0
af738000-af740000 rwxs 128780000 00:05 3691      /dev/dri/card0
af740000-af748000 rwxs 128778000 00:05 3691      /dev/dri/card0
af748000-af750000 rwxs 128770000 00:05 3691      /dev/dri/card0
af750000-af758000 rwxs 128768000 00:05 3691      /dev/dri/card0
af758000-af760000 rwxs 128760000 00:05 3691      /dev/dri/card0
af760000-af768000 rwxs 128758000 00:05 3691      /dev/dri/card0
af768000-af770000 rwxs 128750000 00:05 3691      /dev/dri/card0
af770000-af778000 rwxs 128740000 00:05 3691      /dev/dri/card0
af778000-af780000 rwxs 12a394000 00:05 3691      /dev/dri/card0
af780000-af788000 rwxs 128731000 00:05 3691      /dev/dri/card0
af788000-af790000 rwxs 128729000 00:05 3691      /dev/dri/card0
af790000-af798000 rwxs 128720000 00:05 3691      /dev/dri/card0
af798000-af7a0000 rwxs 128718000 00:05 3691      /dev/dri/card0
af7a0000-af7a8000 rwxs 128710000 00:05 3691      /dev/dri/card0
af7a8000-af7b0000 rwxs 128708000 00:05 3691      /dev/dri/card0
af7b0000-af7b8000 rwxs 128700000 00:05 3691      /dev/dri/card0
af7b8000-af7c0000 rwxs 1286f8000 00:05 3691      /dev/dri/card0
af7c0000-af7c8000 rwxs 1286f0000 00:05 3691      /dev/dri/card0
af7c8000-af7d0000 rwxs 1286e8000 00:05 3691      /dev/dri/card0
af7d0000-af7d8000 rwxs 1286e0000 00:05 3691      /dev/dri/card0
af7d8000-af7e0000 rwxs 1286d8000 00:05 3691      /dev/dri/card0
af7e0000-af7e8000 rwxs 1286d0000 00:05 3691      /dev/dri/card0
af7e8000-af7f0000 rwxs 1286c8000 00:05 3691      /dev/dri/card0
af7f0000-af7f8000 rwxs 1286c0000 00:05 3691      /dev/dri/card0
af7f8000-af800000 rwxs 1286b8000 00:05 3691      /dev/dri/card0
af800000-af808000 rwxs 1286b0000 00:05 3691      /dev/dri/card0
af808000-af810000 rwxs 1286a8000 00:05 3691      /dev/dri/card0
af810000-af818000 rwxs 1286a0000 00:05 3691      /dev/dri/card0
af818000-af820000 rwxs 128698000 00:05 3691      /dev/dri/card0
af820000-af828000 rwxs 128690000 00:05 3691      /dev/dri/card0
af828000-af830000 rwxs 128680000 00:05 3691      /dev/dri/card0
af830000-af838000 rwxs 128631000 00:05 3691      /dev/dri/card0
af838000-af840000 rwxs 128628000 00:05 3691      /dev/dri/card0
af840000-af848000 rwxs 12a28a000 00:05 3691      /dev/dri/card0
af848000-af850000 rwxs 129660000 00:05 3691      /dev/dri/card0
af850000-af858000 rwxs 129713000 00:05 3691      /dev/dri/card0
af858000-af860000 rwxs 12970b000 00:05 3691      /dev/dri/card0
af860000-af868000 rwxs 12a282000 00:05 3691      /dev/dri/card0
af868000-af870000 rwxs 12a27a000 00:05 3691      /dev/dri/card0
af870000-af878000 rwxs 128674000 00:05 3691      /dev/dri/card0
af878000-af880000 rwxs 12866c000 00:05 3691      /dev/dri/card0
af880000-af888000 rwxs 12865f000 00:05 3691      /dev/dri/card0
af888000-af890000 rwxs 128620000 00:05 3691      /dev/dri/card0
af890000-af898000 rwxs 128618000 00:05 3691      /dev/dri/card0
af898000-af8a0000 rwxs 128610000 00:05 3691      /dev/dri/card0
af8a0000-af8a8000 rwxs 128608000 00:05 3691      /dev/dri/card0
af8a8000-af8b0000 rwxs 128600000 00:05 3691      /dev/dri/card0
af8b0000-af8b8000 rwxs 1285f0000 00:05 3691      /dev/dri/card0
af8b8000-af8c0000 rwxs 1291a0000 00:05 3691      /dev/dri/card0
af8c0000-af8c8000 rwxs 1285e8000 00:05 3691      /dev/dri/card0
af8c8000-af8d0000 rwxs 1285e0000 00:05 3691      /dev/dri/card0
af8d0000-af8d8000 rwxs 1285d8000 00:05 3691      /dev/dri/card0
af8d8000-af8e0000 rwxs 1285d0000 00:05 3691      /dev/dri/card0
af8e0000-af8e8000 rwxs 1285c8000 00:05 3691      /dev/dri/card0
af8e8000-af8f0000 rwxs 128218000 00:05 3691      /dev/dri/card0
af8f0000-af8f8000 rwxs 1285c0000 00:05 3691      /dev/dri/card0
af8f8000-af900000 rwxs 128bfa000 00:05 3691      /dev/dri/card0
af900000-af908000 rwxs 12851d000 00:05 3691      /dev/dri/card0
af908000-af910000 rwxs 1285a0000 00:05 3691      /dev/dri/card0
af910000-af918000 rwxs 128688000 00:05 3691      /dev/dri/card0
af918000-af920000 rwxs 128592000 00:05 3691      /dev/dri/card0
af920000-af928000 rwxs 12858a000 00:05 3691      /dev/dri/card0
af928000-af930000 rwxs 128581000 00:05 3691      /dev/dri/card0
af930000-af938000 rwxs 128579000 00:05 3691      /dev/dri/card0
af938000-af940000 rwxs 128571000 00:05 3691      /dev/dri/card0
af940000-af948000 rwxs 128569000 00:05 3691      /dev/dri/card0
af948000-af950000 rwxs 128561000 00:05 3691      /dev/dri/card0
af950000-af958000 rwxs 128559000 00:05 3691      /dev/dri/card0
af958000-af960000 rwxs 128551000 00:05 3691      /dev/dri/card0
af960000-af968000 rwxs 128548000 00:05 3691      /dev/dri/card0
af968000-af970000 rwxs 128540000 00:05 3691      /dev/dri/card0
af970000-af978000 rwxs 128538000 00:05 3691      /dev/dri/card0
af978000-af980000 rwxs 128530000 00:05 3691      /dev/dri/card0
af980000-af988000 rwxs 128528000 00:05 3691      /dev/dri/card0
af988000-af990000 rwxs 128515000 00:05 3691      /dev/dri/card0
af990000-af998000 rwxs 12850d000 00:05 3691      /dev/dri/card0
af998000-af9a0000 rwxs 1284f8000 00:05 3691      /dev/dri/card0
af9a0000-af9a8000 rwxs 1266c3000 00:05 3691      /dev/dri/card0
af9a8000-af9b0000 rwxs 1285b8000 00:05 3691      /dev/dri/card0
af9b0000-af9b8000 rwxs 128505000 00:05 3691      /dev/dri/card0
af9b8000-af9c0000 rwxs 12906a000 00:05 3691      /dev/dri/card0
af9c0000-af9c8000 rwxs 129062000 00:05 3691      /dev/dri/card0
af9c8000-af9d0000 rwxs 1284e0000 00:05 3691      /dev/dri/card0
af9d0000-af9d8000 rwxs 1284d8000 00:05 3691      /dev/dri/card0
af9d8000-af9e0000 rwxs 1284d0000 00:05 3691      /dev/dri/card0
af9e0000-af9e8000 rwxs 1284c8000 00:05 3691      /dev/dri/card0
af9e8000-af9f0000 rwxs 1284c0000 00:05 3691      /dev/dri/card0
af9f0000-af9f8000 rwxs 1284b8000 00:05 3691      /dev/dri/card0
af9f8000-afa00000 rwxs 1284b0000 00:05 3691      /dev/dri/card0
afa00000-afa08000 rwxs 1284a8000 00:05 3691      /dev/dri/card0
afa08000-afa10000 rwxs 1284a0000 00:05 3691      /dev/dri/card0
afa10000-afa18000 rwxs 128498000 00:05 3691      /dev/dri/card0
afa18000-afa20000 rwxs 128490000 00:05 3691      /dev/dri/card0
afa20000-afa28000 rwxs 128488000 00:05 3691      /dev/dri/card0
afa28000-afa30000 rwxs 128480000 00:05 3691      /dev/dri/card0
afa30000-afa38000 rwxs 128478000 00:05 3691      /dev/dri/card0
afa38000-afa40000 rwxs 128470000 00:05 3691      /dev/dri/card0
afa40000-afa48000 rwxs 128468000 00:05 3691      /dev/dri/card0
afa48000-afa50000 rwxs 128460000 00:05 3691      /dev/dri/card0
afa50000-afa58000 rwxs 128458000 00:05 3691      /dev/dri/card0
afa58000-afa60000 rwxs 128450000 00:05 3691      /dev/dri/card0
afa60000-afa68000 rwxs 128448000 00:05 3691      /dev/dri/card0
afa68000-afa70000 rwxs 128440000 00:05 3691      /dev/dri/card0
afa70000-afa78000 rwxs 128438000 00:05 3691      /dev/dri/card0
afa78000-afa80000 rwxs 128430000 00:05 3691      /dev/dri/card0
afa80000-afa88000 rwxs 128428000 00:05 3691      /dev/dri/card0
afa88000-afa90000 rwxs 128420000 00:05 3691      /dev/dri/card0
afa90000-afa98000 rwxs 128418000 00:05 3691      /dev/dri/card0
afa98000-afaa0000 rwxs 128410000 00:05 3691      /dev/dri/card0
afaa0000-afaa8000 rwxs 128408000 00:05 3691      /dev/dri/card0
afaa8000-afab0000 rwxs 128400000 00:05 3691      /dev/dri/card0
afab0000-afab8000 rwxs 1283f8000 00:05 3691      /dev/dri/card0
afab8000-afac0000 rwxs 1283f0000 00:05 3691      /dev/dri/card0
afac0000-afac8000 rwxs 1283e8000 00:05 3691      /dev/dri/card0
afac8000-afad0000 rwxs 1283b8000 00:05 3691      /dev/dri/card0
afad0000-afad8000 rwxs 1283b0000 00:05 3691      /dev/dri/card0
afad8000-afae0000 rwxs 1283a8000 00:05 3691      /dev/dri/card0
afae0000-afae8000 rwxs 1283a0000 00:05 3691      /dev/dri/card0
afae8000-afaf0000 rwxs 129a89000 00:05 3691      /dev/dri/card0
afaf0000-afaf8000 rwxs 128390000 00:05 3691      /dev/dri/card0
afaf8000-afb00000 rwxs 128388000 00:05 3691      /dev/dri/card0
afb00000-afb08000 rwxs 128380000 00:05 3691      /dev/dri/card0
afb08000-afb10000 rwxs 128378000 00:05 3691      /dev/dri/card0
afb10000-afb18000 rwxs 128370000 00:05 3691      /dev/dri/card0
afb18000-afb20000 rwxs 128368000 00:05 3691      /dev/dri/card0
afb20000-afb28000 rwxs 128360000 00:05 3691      /dev/dri/card0
afb28000-afb30000 rwxs 128358000 00:05 3691      /dev/dri/card0
afb30000-afb38000 rwxs 128350000 00:05 3691      /dev/dri/card0
afb38000-afb40000 rwxs 128348000 00:05 3691      /dev/dri/card0
afb40000-afb48000 rwxs 128340000 00:05 3691      /dev/dri/card0
afb48000-afb50000 rwxs 128338000 00:05 3691      /dev/dri/card0
afb50000-afb58000 rwxs 128330000 00:05 3691      /dev/dri/card0
afb58000-afb60000 rwxs 128328000 00:05 3691      /dev/dri/card0
afb60000-afb68000 rwxs 128320000 00:05 3691      /dev/dri/card0
afb68000-afb70000 rwxs 128318000 00:05 3691      /dev/dri/card0
afb70000-afb78000 rwxs 128310000 00:05 3691      /dev/dri/card0
afb78000-afb80000 rwxs 128308000 00:05 3691      /dev/dri/card0
afb80000-afb88000 rwxs 128300000 00:05 3691      /dev/dri/card0
afb88000-afb90000 rwxs 1282f8000 00:05 3691      /dev/dri/card0
afb90000-afb98000 rwxs 1282f0000 00:05 3691      /dev/dri/card0
afb98000-afba0000 rwxs 1282e8000 00:05 3691      /dev/dri/card0
afba0000-afba8000 rwxs 1282e0000 00:05 3691      /dev/dri/card0
afba8000-afbb0000 rwxs 1282d8000 00:05 3691      /dev/dri/card0
afbb0000-afbb8000 rwxs 1282d0000 00:05 3691      /dev/dri/card0
afbb8000-afbc0000 rwxs 1282c8000 00:05 3691      /dev/dri/card0
afbc0000-afbc8000 rwxs 1282c0000 00:05 3691      /dev/dri/card0
afbc8000-afbd0000 rwxs 1282b8000 00:05 3691      /dev/dri/card0
afbd0000-afbd8000 rwxs 1282b0000 00:05 3691      /dev/dri/card0
afbd8000-afbe0000 rwxs 128ae6000 00:05 3691      /dev/dri/card0
afbe0000-afbe8000 rwxs 1282a8000 00:05 3691      /dev/dri/card0
afbe8000-afbf0000 rwxs 129218000 00:05 3691      /dev/dri/card0
afbf0000-afbf8000 rwxs 128299000 00:05 3691      /dev/dri/card0
afbf8000-afc00000 rwxs 128291000 00:05 3691      /dev/dri/card0
afc00000-afc08000 rwxs 128289000 00:05 3691      /dev/dri/card0
afc08000-afc10000 rwxs 128280000 00:05 3691      /dev/dri/card0
afc10000-afc18000 rwxs 128278000 00:05 3691      /dev/dri/card0
afc18000-afc20000 rwxs 128270000 00:05 3691      /dev/dri/card0
afc20000-afc28000 rwxs 128258000 00:05 3691      /dev/dri/card0
afc28000-afc30000 rwxs 128250000 00:05 3691      /dev/dri/card0
afc30000-afc38000 rwxs 128248000 00:05 3691      /dev/dri/card0
afc38000-afc40000 rwxs 128240000 00:05 3691      /dev/dri/card0
afc40000-afc48000 rwxs 128238000 00:05 3691      /dev/dri/card0
afc48000-afc50000 rwxs 128230000 00:05 3691      /dev/dri/card0
afc50000-afc58000 rwxs 128220000 00:05 3691      /dev/dri/card0
afc58000-afc60000 rwxs 127d96000 00:05 3691      /dev/dri/card0
afc60000-afc68000 rwxs 128210000 00:05 3691      /dev/dri/card0
afc68000-afc70000 rwxs 128398000 00:05 3691      /dev/dri/card0
afc70000-afc78000 rwxs 128201000 00:05 3691      /dev/dri/card0
afc78000-afc80000 rwxs 127fb9000 00:05 3691      /dev/dri/card0
afc80000-afc88000 rwxs 127f02000 00:05 3691      /dev/dri/card0
afc88000-afc90000 rwxs 128b8c000 00:05 3691      /dev/dri/card0
afc90000-afc98000 rwxs 128198000 00:05 3691      /dev/dri/card0
afc98000-afca0000 rwxs 128190000 00:05 3691      /dev/dri/card0
afca0000-afca8000 rwxs 128188000 00:05 3691      /dev/dri/card0
afca8000-afcb0000 rwxs 128180000 00:05 3691      /dev/dri/card0
afcb0000-afcb8000 rwxs 1281f8000 00:05 3691      /dev/dri/card0
afcb8000-afcc0000 rwxs 1273be000 00:05 3691      /dev/dri/card0
afcc0000-afcc8000 rwxs 128097000 00:05 3691      /dev/dri/card0
afcc8000-afcd0000 rwxs 127855000 00:05 3691      /dev/dri/card0
afcd0000-afcd8000 rwxs 127f5b000 00:05 3691      /dev/dri/card0
afcd8000-afce0000 rwxs 128150000 00:05 3691      /dev/dri/card0
afce0000-afce8000 rwxs 127f53000 00:05 3691      /dev/dri/card0
afce8000-afcf0000 rwxs 1298c2000 00:05 3691      /dev/dri/card0
afcf0000-afcf8000 rwxs 129943000 00:05 3691      /dev/dri/card0
afcf8000-afd00000 rwxs 12993b000 00:05 3691      /dev/dri/card0
afd00000-afd08000 rwxs 129932000 00:05 3691      /dev/dri/card0
afd08000-afd10000 rwxs 128178000 00:05 3691      /dev/dri/card0
afd10000-afd18000 rwxs 127b4b000 00:05 3691      /dev/dri/card0
afd18000-afd20000 rwxs 128077000 00:05 3691      /dev/dri/card0
afd20000-afd28000 rwxs 12992a000 00:05 3691      /dev/dri/card0
afd28000-afd30000 rwxs 129dbe000 00:05 3691      /dev/dri/card0
afd30000-afd38000 rwxs 129922000 00:05 3691      /dev/dri/card0
afd38000-afd40000 rwxs 12991a000 00:05 3691      /dev/dri/card0
afd40000-afd48000 rwxs 12958a000 00:05 3691      /dev/dri/card0
afd48000-afd50000 rwxs 1281e8000 00:05 3691      /dev/dri/card0
afd50000-afd58000 rwxs 1281e0000 00:05 3691      /dev/dri/card0
afd58000-afd60000 rwxs 1281d8000 00:05 3691      /dev/dri/card0
afd60000-afd68000 rwxs 1281d0000 00:05 3691      /dev/dri/card0
afd68000-afd70000 rwxs 1281c8000 00:05 3691      /dev/dri/card0
afd70000-afd78000 rwxs 1281c0000 00:05 3691      /dev/dri/card0
afd78000-afd80000 rwxs 1281b8000 00:05 3691      /dev/dri/card0
afd80000-afd88000 rwxs 1281b0000 00:05 3691      /dev/dri/card0
afd88000-afd90000 rwxs 127e9a000 00:05 3691      /dev/dri/card0
afd90000-afd98000 rwxs 127ff1000 00:05 3691      /dev/dri/card0
afd98000-afda0000 rwxs 1280a7000 00:05 3691      /dev/dri/card0
afda0000-afda8000 rwxs 128121000 00:05 3691      /dev/dri/card0
afda8000-afdb0000 rwxs 128148000 00:05 3691      /dev/dri/card0
afdb0000-afdb8000 rwxs 12809f000 00:05 3691      /dev/dri/card0
afdb8000-afdc0000 rwxs 127f4b000 00:05 3691      /dev/dri/card0
afdc0000-afdc8000 rwxs 127f12000 00:05 3691      /dev/dri/card0
afdc8000-afdd0000 rwxs 127e92000 00:05 3691      /dev/dri/card0
afdd0000-afdd8000 rwxs 129912000 00:05 3691      /dev/dri/card0
afdd8000-afde0000 rwxs 127a37000 00:05 3691      /dev/dri/card0
afde0000-afde8000 rwxs 127d6d000 00:05 3691      /dev/dri/card0
afde8000-afdf0000 rwxs 12990a000 00:05 3691      /dev/dri/card0
afdf0000-afdf8000 rwxs 127a1f000 00:05 3691      /dev/dri/card0
afdf8000-afe00000 rwxs 127957000 00:05 3691      /dev/dri/card0
afe00000-afe08000 rwxs 127fd1000 00:05 3691      /dev/dri/card0
afe08000-afe10000 rwxs 128108000 00:05 3691      /dev/dri/card0
afe10000-afe18000 rwxs 12788f000 00:05 3691      /dev/dri/card0
afe18000-afe20000 rwxs 129c95000 00:05 3691      /dev/dri/card0
afe20000-afe28000 rwxs 129bbd000 00:05 3691      /dev/dri/card0
afe28000-afe30000 rwxs 127be1000 00:05 3691      /dev/dri/card0
afe30000-afe38000 rwxs 127db6000 00:05 3691      /dev/dri/card0
afe38000-afe40000 rwxs 127dae000 00:05 3691      /dev/dri/card0
afe40000-afe48000 rwxs 127da6000 00:05 3691      /dev/dri/card0
afe48000-afe50000 rwxs 127eca000 00:05 3691      /dev/dri/card0
afe50000-afe58000 rwxs 127ec2000 00:05 3691      /dev/dri/card0
afe58000-afe60000 rwxs 127ea2000 00:05 3691      /dev/dri/card0
afe60000-afe68000 rwxs 1293cd000 00:05 3691      /dev/dri/card0
afe68000-afe70000 rwxs 127c38000 00:05 3691      /dev/dri/card0
afe70000-afe78000 rwxs 127e82000 00:05 3691      /dev/dri/card0
afe78000-afe80000 rwxs 1281a8000 00:05 3691      /dev/dri/card0
afe80000-afe88000 rwxs 128170000 00:05 3691      /dev/dri/card0
afe88000-afe90000 rwxs 127eba000 00:05 3691      /dev/dri/card0
afe90000-afe98000 rwxs 127eb2000 00:05 3691      /dev/dri/card0
afe98000-afea0000 rwxs 127eaa000 00:05 3691      /dev/dri/card0
afea0000-afea8000 rwxs 127d9e000 00:05 3691      /dev/dri/card0
afea8000-afeb0000 rwxs 127d86000 00:05 3691      /dev/dri/card0
afeb0000-afeb8000 rwxs 127f0a000 00:05 3691      /dev/dri/card0
afeb8000-afec0000 rwxs 1281a0000 00:05 3691      /dev/dri/card0
afec0000-afec8000 rwxs 128158000 00:05 3691      /dev/dri/card0
afec8000-afed0000 rwxs 127fe1000 00:05 3691      /dev/dri/card0
afed0000-afed8000 rwxs 127eea000 00:05 3691      /dev/dri/card0
afed8000-afee0000 rwxs 127e3a000 00:05 3691      /dev/dri/card0
afee0000-afee8000 rwxs 1280c0000 00:05 3691      /dev/dri/card0
afee8000-afef0000 rwxs 127bb9000 00:05 3691      /dev/dri/card0
afef0000-afef8000 rwxs 127d2d000 00:05 3691      /dev/dri/card0
afef8000-aff00000 rwxs 127d25000 00:05 3691      /dev/dri/card0
aff00000-aff08000 rwxs 127d1d000 00:05 3691      /dev/dri/card0
aff08000-aff10000 rwxs 127d15000 00:05 3691      /dev/dri/card0
aff10000-aff18000 rwxs 127d0d000 00:05 3691      /dev/dri/card0
aff18000-aff20000 rwxs 127d05000 00:05 3691      /dev/dri/card0
aff20000-aff28000 rwxs 1281f0000 00:05 3691      /dev/dri/card0
aff28000-aff30000 rwxs 128228000 00:05 3691      /dev/dri/card0
aff30000-aff38000 rwxs 127b03000 00:05 3691      /dev/dri/card0
aff38000-aff40000 rwxs 127f72000 00:05 3691      /dev/dri/card0
aff40000-aff48000 rwxs 127d55000 00:05 3691      /dev/dri/card0
aff48000-aff50000 rwxs 12806f000 00:05 3691      /dev/dri/card0
aff50000-aff58000 rwxs 12794f000 00:05 3691      /dev/dri/card0
aff58000-aff60000 rwxs 127bc9000 00:05 3691      /dev/dri/card0
aff60000-aff68000 rwxs 127d65000 00:05 3691      /dev/dri/card0
aff68000-aff70000 rwxs 127d5d000 00:05 3691      /dev/dri/card0
aff70000-aff78000 rwxs 12808f000 00:05 3691      /dev/dri/card0
aff78000-aff80000 rwxs 127fd9000 00:05 3691      /dev/dri/card0
aff80000-aff88000 rwxs 127775000 00:05 3691      /dev/dri/card0
aff88000-aff90000 rwxs 1253b0000 00:05 3691      /dev/dri/card0
aff90000-aff98000 rwxs 127bf1000 00:05 3691      /dev/dri/card0
aff98000-affa0000 rwxs 1280b8000 00:05 3691      /dev/dri/card0
affa0000-affa8000 rwxs 127e4a000 00:05 3691      /dev/dri/card0
affa8000-affb0000 rwxs 127e42000 00:05 3691      /dev/dri/card0
affb0000-affb8000 rwxs 127a8d000 00:05 3691      /dev/dri/card0
affb8000-affc0000 rwxs 128067000 00:05 3691      /dev/dri/card0
affc0000-affc8000 rwxs 128087000 00:05 3691      /dev/dri/card0
affc8000-affd0000 rwxs 12807f000 00:05 3691      /dev/dri/card0
affd0000-affd8000 rwxs 127e7a000 00:05 3691      /dev/dri/card0
affd8000-affe0000 rwxs 127c57000 00:05 3691      /dev/dri/card0
affe0000-affe8000 rwxs 1279c7000 00:05 3691      /dev/dri/card0
affe8000-afff0000 rwxs 127d7e000 00:05 3691      /dev/dri/card0
afff0000-afff8000 rwxs 127de6000 00:05 3691      /dev/dri/card0
afff8000-b0000000 rwxs 127bb1000 00:05 3691      /dev/dri/card0
b0000000-b0008000 rwxs 127c4f000 00:05 3691      /dev/dri/card0
b0008000-b0010000 rwxs 127b13000 00:05 3691      /dev/dri/card0
b0010000-b0018000 rwxs 127a75000 00:05 3691      /dev/dri/card0
b0018000-b0020000 rwxs 127a6d000 00:05 3691      /dev/dri/card0
b0020000-b0028000 rwxs 127aeb000 00:05 3691      /dev/dri/card0
b0028000-b0030000 rwxs 127ae3000 00:05 3691      /dev/dri/card0
b0030000-b0038000 rwxs 127a65000 00:05 3691      /dev/dri/card0
b0038000-b0040000 rwxs 127e72000 00:05 3691      /dev/dri/card0
b0040000-b0048000 rwxs 12777d000 00:05 3691      /dev/dri/card0
b0048000-b0050000 rwxs 12781d000 00:05 3691      /dev/dri/card0
b0050000-b0058000 rwxs 127b93000 00:05 3691      /dev/dri/card0
b0058000-b0060000 rwxs 127ba9000 00:05 3691      /dev/dri/card0
b0060000-b0068000 rwxs 127dde000 00:05 3691      /dev/dri/card0
b0068000-b0070000 rwxs 127cb0000 00:05 3691      /dev/dri/card0
b0070000-b0078000 rwxs 127f43000 00:05 3691      /dev/dri/card0
b0078000-b0080000 rwxs 127835000 00:05 3691      /dev/dri/card0
b0080000-b0088000 rwxs 127dd6000 00:05 3691      /dev/dri/card0
b0088000-b0090000 rwxs 127dbe000 00:05 3691      /dev/dri/card0
b0090000-b0098000 rwxs 127b33000 00:05 3691      /dev/dri/card0
b0098000-b00a0000 rwxs 128131000 00:05 3691      /dev/dri/card0
b00a0000-b00a8000 rwxs 12783d000 00:05 3691      /dev/dri/card0
b00a8000-b00b0000 rwxs 127df7000 00:05 3691      /dev/dri/card0
b00b0000-b00b8000 rwxs 12776d000 00:05 3691      /dev/dri/card0
b00b8000-b00c0000 rwxs 127b0b000 00:05 3691      /dev/dri/card0
b00c0000-b00c8000 rwxs 127bf9000 00:05 3691      /dev/dri/card0
b00c8000-b00d0000 rwxs 127adb000 00:05 3691      /dev/dri/card0
b00d0000-b00d8000 rwxs 127b8b000 00:05 3691      /dev/dri/card0
b00d8000-b00e0000 rwxs 127b83000 00:05 3691      /dev/dri/card0
b00e0000-b00e8000 rwxs 127b7b000 00:05 3691      /dev/dri/card0
b00e8000-b00f0000 rwxs 12782d000 00:05 3691      /dev/dri/card0
b00f0000-b00f8000 rwxs 1272ef000 00:05 3691      /dev/dri/card0
b00f8000-b0100000 rwxs 127bd9000 00:05 3691      /dev/dri/card0
b0100000-b0108000 rwxs 127b63000 00:05 3691      /dev/dri/card0
b0108000-b0110000 rwxs 127aad000 00:05 3691      /dev/dri/card0
b0110000-b0118000 rwxs 127dce000 00:05 3691      /dev/dri/card0
b0118000-b0120000 rwxs 127dc6000 00:05 3691      /dev/dri/card0
b0120000-b0128000 rwxs 127825000 00:05 3691      /dev/dri/card0
b0128000-b0130000 rwxs 128129000 00:05 3691      /dev/dri/card0
b0130000-b0138000 rwxs 127a85000 00:05 3691      /dev/dri/card0
b0138000-b0140000 rwxs 127def000 00:05 3691      /dev/dri/card0
b0140000-b0148000 rwxs 127b5b000 00:05 3691      /dev/dri/card0
b0148000-b0150000 rwxs 127b73000 00:05 3691      /dev/dri/card0
b0150000-b0158000 rwxs 12805f000 00:05 3691      /dev/dri/card0
b0158000-b0160000 rwxs 127d76000 00:05 3691      /dev/dri/card0
b0160000-b0168000 rwxs 127b23000 00:05 3691      /dev/dri/card0
b0168000-b0170000 rwxs 127a7d000 00:05 3691      /dev/dri/card0
b0170000-b0178000 rwxs 127ca8000 00:05 3691      /dev/dri/card0
b0178000-b0180000 rwxs 127d3d000 00:05 3691      /dev/dri/card0
b0180000-b0188000 rwxs 127755000 00:05 3691      /dev/dri/card0
b0188000-b0190000 rwxs 127d35000 00:05 3691      /dev/dri/card0
b0190000-b0198000 rwxs 128057000 00:05 3691      /dev/dri/card0
b0198000-b01a0000 rwxs 127aa5000 00:05 3691      /dev/dri/card0
b01a0000-b01a8000 rwxs 127c47000 00:05 3691      /dev/dri/card0
b01a8000-b01b0000 rwxs 127d4d000 00:05 3691      /dev/dri/card0
b01b0000-b01b8000 rwxs 12795f000 00:05 3691      /dev/dri/card0
b01b8000-b01c0000 rwxs 128118000 00:05 3691      /dev/dri/card0
b01c0000-b01c8000 rwxs 128110000 00:05 3691      /dev/dri/card0
b01c8000-b01d0000 rwxs 128168000 00:05 3691      /dev/dri/card0
b01d0000-b01d8000 rwxs 127f3b000 00:05 3691      /dev/dri/card0
b01d8000-b01e0000 rwxs 127e0d000 00:05 3691      /dev/dri/card0
b01e0000-b01e8000 rwxs 127c09000 00:05 3691      /dev/dri/card0
b01e8000-b01f0000 rwxs 127897000 00:05 3691      /dev/dri/card0
b01f0000-b01f8000 rwxs 127c87000 00:05 3691      /dev/dri/card0
b01f8000-b0200000 rwxs 127ad3000 00:05 3691      /dev/dri/card0
b0200000-b0208000 rwxs 12775d000 00:05 3691      /dev/dri/card0
b0208000-b0210000 rwxs 127e62000 00:05 3691      /dev/dri/card0
b0210000-b0218000 rwxs 127c2f000 00:05 3691      /dev/dri/card0
b0218000-b0220000 rwxs 127d45000 00:05 3691      /dev/dri/card0
b0220000-b0228000 rwxs 127b53000 00:05 3691      /dev/dri/card0
b0228000-b0230000 rwxs 127fc1000 00:05 3691      /dev/dri/card0
b0230000-b0238000 rwxs 127c01000 00:05 3691      /dev/dri/card0
b0238000-b0240000 rwxs 1273c6000 00:05 3691      /dev/dri/card0
b0240000-b0248000 rwxs 127bc1000 00:05 3691      /dev/dri/card0
b0248000-b0250000 rwxs 127f33000 00:05 3691      /dev/dri/card0
b0250000-b0258000 rwxs 127f22000 00:05 3691      /dev/dri/card0
b0258000-b0260000 rwxs 127fa9000 00:05 3691      /dev/dri/card0
b0260000-b0268000 rwxs 127947000 00:05 3691      /dev/dri/card0
b0268000-b0270000 rwxs 127a48000 00:05 3691      /dev/dri/card0
b0270000-b0278000 rwxs 127f99000 00:05 3691      /dev/dri/card0
b0278000-b0280000 rwxs 12793f000 00:05 3691      /dev/dri/card0
b0280000-b0288000 rwxs 12792f000 00:05 3691      /dev/dri/card0
b0288000-b0290000 rwxs 127927000 00:05 3691      /dev/dri/card0
b0290000-b0298000 rwxs 12790f000 00:05 3691      /dev/dri/card0
b0298000-b02a0000 rwxs 1278ff000 00:05 3691      /dev/dri/card0
b02a0000-b02a8000 rwxs 127fe9000 00:05 3691      /dev/dri/card0
b02a8000-b02b0000 rwxs 1278ef000 00:05 3691      /dev/dri/card0
b02b0000-b02b8000 rwxs 1278df000 00:05 3691      /dev/dri/card0
b02b8000-b02c0000 rwxs 1278d7000 00:05 3691      /dev/dri/card0
b02c0000-b02c8000 rwxs 1278cf000 00:05 3691      /dev/dri/card0
b02c8000-b02d0000 rwxs 1278c7000 00:05 3691      /dev/dri/card0
b02d0000-b02d8000 rwxs 1278bf000 00:05 3691      /dev/dri/card0
b02d8000-b02e0000 rwxs 1278b7000 00:05 3691      /dev/dri/card0
b02e0000-b02e8000 rwxs 127c7f000 00:05 3691      /dev/dri/card0
b02e8000-b02f0000 rwxs 127887000 00:05 3691      /dev/dri/card0
b02f0000-b02f8000 rwxs 12787f000 00:05 3691      /dev/dri/card0
b02f8000-b0300000 rwxs 127795000 00:05 3691      /dev/dri/card0
b0300000-b0308000 rwxs 1278af000 00:05 3691      /dev/dri/card0
b0308000-b0310000 rwxs 1278a7000 00:05 3691      /dev/dri/card0
b0310000-b0318000 rwxs 12789f000 00:05 3691      /dev/dri/card0
b0318000-b0320000 rwxs 127866000 00:05 3691      /dev/dri/card0
b0320000-b0328000 rwxs 12785e000 00:05 3691      /dev/dri/card0
b0328000-b0330000 rwxs 12779d000 00:05 3691      /dev/dri/card0
b0330000-b0338000 rwxs 127af3000 00:05 3691      /dev/dri/card0
b0338000-b0340000 rwxs 127e6a000 00:05 3691      /dev/dri/card0
b0340000-b0348000 rwxs 127be9000 00:05 3691      /dev/dri/card0
b0348000-b0350000 rwxs 127e5a000 00:05 3691      /dev/dri/card0
b0350000-b0358000 rwxs 127a27000 00:05 3691      /dev/dri/card0
b0358000-b0360000 rwxs 127f91000 00:05 3691      /dev/dri/card0
b0360000-b0368000 rwxs 127b43000 00:05 3691      /dev/dri/card0
b0368000-b0370000 rwxs 127e8a000 00:05 3691      /dev/dri/card0
b0370000-b0378000 rwxs 12780d000 00:05 3691      /dev/dri/card0
b0378000-b0380000 rwxs 127805000 00:05 3691      /dev/dri/card0
b0380000-b0388000 rwxs 1277fd000 00:05 3691      /dev/dri/card0
b0388000-b0390000 rwxs 1277f5000 00:05 3691      /dev/dri/card0
b0390000-b0398000 rwxs 1277ed000 00:05 3691      /dev/dri/card0
b0398000-b03a0000 rwxs 1277e5000 00:05 3691      /dev/dri/card0
b03a0000-b03a8000 rwxs 1277dd000 00:05 3691      /dev/dri/card0
b03a8000-b03b0000 rwxs 1277d5000 00:05 3691      /dev/dri/card0
b03b0000-b03b8000 rwxs 1277cd000 00:05 3691      /dev/dri/card0
b03b8000-b03c0000 rwxs 12791f000 00:05 3691      /dev/dri/card0
b03c0000-b03c8000 rwxs 127917000 00:05 3691      /dev/dri/card0
b03c8000-b03d0000 rwxs 12786f000 00:05 3691      /dev/dri/card0
b03d0000-b03d8000 rwxs 1277bd000 00:05 3691      /dev/dri/card0
b03d8000-b03e0000 rwxs 1277a5000 00:05 3691      /dev/dri/card0
b03e0000-b03e8000 rwxs 1279df000 00:05 3691      /dev/dri/card0
b03e8000-b03f0000 rwxs 12778d000 00:05 3691      /dev/dri/card0
b03f0000-b03f8000 rwxs 126f1f000 00:05 3691      /dev/dri/card0
b03f8000-b0400000 rwxs 127785000 00:05 3691      /dev/dri/card0
b0400000-b0408000 rwxs 127907000 00:05 3691      /dev/dri/card0
b0408000-b0410000 rwxs 127b3b000 00:05 3691      /dev/dri/card0
b0410000-b0418000 rwxs 12796f000 00:05 3691      /dev/dri/card0
b0418000-b0420000 rwxs 127765000 00:05 3691      /dev/dri/card0
b0420000-b0428000 rwxs 1279e7000 00:05 3691      /dev/dri/card0
b0428000-b0430000 rwxs 1279d0000 00:05 3691      /dev/dri/card0
b0430000-b0438000 rwxs 127f2b000 00:05 3691      /dev/dri/card0
b0438000-b0440000 rwxs 127745000 00:05 3691      /dev/dri/card0
b0440000-b0448000 rwxs 12773d000 00:05 3691      /dev/dri/card0
b0448000-b0450000 rwxs 127735000 00:05 3691      /dev/dri/card0
b0450000-b0458000 rwxs 12772d000 00:05 3691      /dev/dri/card0
b0458000-b0460000 rwxs 1276b2000 00:05 3691      /dev/dri/card0
b0460000-b0468000 rwxs 127710000 00:05 3691      /dev/dri/card0
b0468000-b0470000 rwxs 127708000 00:05 3691      /dev/dri/card0
b0470000-b0478000 rwxs 127700000 00:05 3691      /dev/dri/card0
b0478000-b0480000 rwxs 1277b5000 00:05 3691      /dev/dri/card0
b0480000-b0488000 rwxs 1276f0000 00:05 3691      /dev/dri/card0
b0488000-b0490000 rwxs 127acb000 00:05 3691      /dev/dri/card0
b0490000-b0498000 rwxs 12771d000 00:05 3691      /dev/dri/card0
b0498000-b04a0000 rwxs 1276bf000 00:05 3691      /dev/dri/card0
b04a0000-b04a8000 rwxs 1276aa000 00:05 3691      /dev/dri/card0
b04a8000-b04b0000 rwxs 1280b0000 00:05 3691      /dev/dri/card0
b04b0000-b04b8000 rwxs 127699000 00:05 3691      /dev/dri/card0
b04b8000-b04c0000 rwxs 127691000 00:05 3691      /dev/dri/card0
b04c0000-b04c8000 rwxs 1276df000 00:05 3691      /dev/dri/card0
b04c8000-b04d0000 rwxs 1276d7000 00:05 3691      /dev/dri/card0
b04d0000-b04d8000 rwxs 127639000 00:05 3691      /dev/dri/card0
b04d8000-b04e0000 rwxs 1276cf000 00:05 3691      /dev/dri/card0
b04e0000-b04e8000 rwxs 1276c7000 00:05 3691      /dev/dri/card0
b04e8000-b04f0000 rwxs 127689000 00:05 3691      /dev/dri/card0
b04f0000-b04f8000 rwxs 127681000 00:05 3691      /dev/dri/card0
b04f8000-b0500000 rwxs 127679000 00:05 3691      /dev/dri/card0
b0500000-b0508000 rwxs 127671000 00:05 3691      /dev/dri/card0
b0508000-b0510000 rwxs 127669000 00:05 3691      /dev/dri/card0
b0510000-b0518000 rwxs 127661000 00:05 3691      /dev/dri/card0
b0518000-b0520000 rwxs 127659000 00:05 3691      /dev/dri/card0
b0520000-b0528000 rwxs 127651000 00:05 3691      /dev/dri/card0
b0528000-b0530000 rwxs 127649000 00:05 3691      /dev/dri/card0
b0530000-b0538000 rwxs 127641000 00:05 3691      /dev/dri/card0
b0538000-b0540000 rwxs 127631000 00:05 3691      /dev/dri/card0
b0540000-b0548000 rwxs 127629000 00:05 3691      /dev/dri/card0
b0548000-b0550000 rwxs 127621000 00:05 3691      /dev/dri/card0
b0550000-b0558000 rwxs 127619000 00:05 3691      /dev/dri/card0
b0558000-b0560000 rwxs 127611000 00:05 3691      /dev/dri/card0
b0560000-b0568000 rwxs 127609000 00:05 3691      /dev/dri/card0
b0568000-b0570000 rwxs 127fa1000 00:05 3691      /dev/dri/card0
b0570000-b0578000 rwxs 127fc9000 00:05 3691      /dev/dri/card0
b0578000-b0580000 rwxs 127bd1000 00:05 3691      /dev/dri/card0
b0580000-b0588000 rwxs 1272df000 00:05 3691      /dev/dri/card0
b0588000-b0590000 rwxs 12800a000 00:05 3691      /dev/dri/card0
b0590000-b0598000 rwxs 128002000 00:05 3691      /dev/dri/card0
b0598000-b05a0000 rwxs 127b6b000 00:05 3691      /dev/dri/card0
b05a0000-b05a8000 rwxs 127a2f000 00:05 3691      /dev/dri/card0
b05a8000-b05b0000 rwxs 12774d000 00:05 3691      /dev/dri/card0
b05b0000-b05b8000 rwxs 1275c1000 00:05 3691      /dev/dri/card0
b05b8000-b05c0000 rwxs 1275b2000 00:05 3691      /dev/dri/card0
b05c0000-b05c8000 rwxs 1275a9000 00:05 3691      /dev/dri/card0
b05c8000-b05d0000 rwxs 127725000 00:05 3691      /dev/dri/card0
b05d0000-b05d8000 rwxs 129bb5000 00:05 3691      /dev/dri/card0
b05d8000-b05e0000 rwxs 127599000 00:05 3691      /dev/dri/card0
b05e0000-b05e8000 rwxs 127591000 00:05 3691      /dev/dri/card0
b05e8000-b05f0000 rwxs 127589000 00:05 3691      /dev/dri/card0
b05f0000-b05f8000 rwxs 127581000 00:05 3691      /dev/dri/card0
b05f8000-b0600000 rwxs 127579000 00:05 3691      /dev/dri/card0
b0600000-b0608000 rwxs 127561000 00:05 3691      /dev/dri/card0
b0608000-b0610000 rwxs 127eda000 00:05 3691      /dev/dri/card0
b0610000-b0618000 rwxs 127ed2000 00:05 3691      /dev/dri/card0
b0618000-b0620000 rwxs 1274a6000 00:05 3691      /dev/dri/card0
b0620000-b0628000 rwxs 12749e000 00:05 3691      /dev/dri/card0
b0628000-b0630000 rwxs 127496000 00:05 3691      /dev/dri/card0
b0630000-b0638000 rwxs 127551000 00:05 3691      /dev/dri/card0
b0638000-b0640000 rwxs 127549000 00:05 3691      /dev/dri/card0
b0640000-b0648000 rwxs 127541000 00:05 3691      /dev/dri/card0
b0648000-b0650000 rwxs 127539000 00:05 3691      /dev/dri/card0
b0650000-b0658000 rwxs 127a17000 00:05 3691      /dev/dri/card0
b0658000-b0660000 rwxs 1274c6000 00:05 3691      /dev/dri/card0
b0660000-b0668000 rwxs 1274be000 00:05 3691      /dev/dri/card0
b0668000-b0670000 rwxs 1274b6000 00:05 3691      /dev/dri/card0
b0670000-b0678000 rwxs 127559000 00:05 3691      /dev/dri/card0
b0678000-b0680000 rwxs 127475000 00:05 3691      /dev/dri/card0
b0680000-b0688000 rwxs 12746d000 00:05 3691      /dev/dri/card0
b0688000-b0690000 rwxs 1277c5000 00:05 3691      /dev/dri/card0
b0690000-b0698000 rwxs 127434000 00:05 3691      /dev/dri/card0
b0698000-b06a0000 rwxs 12742c000 00:05 3691      /dev/dri/card0
b06a0000-b06a8000 rwxs 127424000 00:05 3691      /dev/dri/card0
b06a8000-b06b0000 rwxs 12741c000 00:05 3691      /dev/dri/card0
b06b0000-b06b8000 rwxs 127414000 00:05 3691      /dev/dri/card0
b06b8000-b06c0000 rwxs 12740c000 00:05 3691      /dev/dri/card0
b06c0000-b06c8000 rwxs 1273de000 00:05 3691      /dev/dri/card0
b06c8000-b06d0000 rwxs 1273d6000 00:05 3691      /dev/dri/card0
b06d0000-b06d8000 rwxs 1273ce000 00:05 3691      /dev/dri/card0
b06d8000-b06e0000 rwxs 127967000 00:05 3691      /dev/dri/card0
b06e0000-b06e8000 rwxs 127a0f000 00:05 3691      /dev/dri/card0
b06e8000-b06f0000 rwxs 1273b6000 00:05 3691      /dev/dri/card0
b06f0000-b06f8000 rwxs 127403000 00:05 3691      /dev/dri/card0
b06f8000-b0700000 rwxs 1274ae000 00:05 3691      /dev/dri/card0
b0700000-b0708000 rwxs 127efa000 00:05 3691      /dev/dri/card0
b0708000-b0710000 rwxs 127d8e000 00:05 3691      /dev/dri/card0
b0710000-b0718000 rwxs 1273ad000 00:05 3691      /dev/dri/card0
b0718000-b0720000 rwxs 1273a5000 00:05 3691      /dev/dri/card0
b0720000-b0728000 rwxs 12739d000 00:05 3691      /dev/dri/card0
b0728000-b0730000 rwxs 127395000 00:05 3691      /dev/dri/card0
b0730000-b0738000 rwxs 12738d000 00:05 3691      /dev/dri/card0
b0738000-b0740000 rwxs 127384000 00:05 3691      /dev/dri/card0
b0740000-b0748000 rwxs 12737c000 00:05 3691      /dev/dri/card0
b0748000-b0750000 rwxs 127374000 00:05 3691      /dev/dri/card0
b0750000-b0758000 rwxs 12736c000 00:05 3691      /dev/dri/card0
b0758000-b0760000 rwxs 127364000 00:05 3691      /dev/dri/card0
b0760000-b0768000 rwxs 12735c000 00:05 3691      /dev/dri/card0
b0768000-b0770000 rwxs 127354000 00:05 3691      /dev/dri/card0
b0770000-b0778000 rwxs 12734b000 00:05 3691      /dev/dri/card0
b0778000-b0780000 rwxs 128140000 00:05 3691      /dev/dri/card0
b0780000-b0788000 rwxs 127937000 00:05 3691      /dev/dri/card0
b0788000-b0790000 rwxs 127fb1000 00:05 3691      /dev/dri/card0
b0790000-b0798000 rwxs 127327000 00:05 3691      /dev/dri/card0
b0798000-b07a0000 rwxs 1278e7000 00:05 3691      /dev/dri/card0
b07a0000-b07a8000 rwxs 12677e000 00:05 3691      /dev/dri/card0
b07a8000-b07b0000 rwxs 126776000 00:05 3691      /dev/dri/card0
b07b0000-b07b8000 rwxs 12672f000 00:05 3691      /dev/dri/card0
b07b8000-b07c0000 rwxs 126727000 00:05 3691      /dev/dri/card0
b07c0000-b07c8000 rwxs 1272c7000 00:05 3691      /dev/dri/card0
b07c8000-b07d0000 rwxs 1272bf000 00:05 3691      /dev/dri/card0
b07d0000-b07d8000 rwxs 12a212000 00:05 3691      /dev/dri/card0
b07d8000-b07e0000 rwxs 128b54000 00:05 3691      /dev/dri/card0
b07e0000-b07e8000 rwxs 128b4c000 00:05 3691      /dev/dri/card0
b07e8000-b07f0000 rwxs 128b44000 00:05 3691      /dev/dri/card0
b07f0000-b07f8000 rwxs 1251aa000 00:05 3691      /dev/dri/card0
b07f8000-b0800000 rwxs 1271f9000 00:05 3691      /dev/dri/card0
b0800000-b0808000 rwxs 12729f000 00:05 3691      /dev/dri/card0
b0808000-b0810000 rwxs 127297000 00:05 3691      /dev/dri/card0
b0810000-b0818000 rwxs 12728f000 00:05 3691      /dev/dri/card0
b0818000-b0820000 rwxs 127287000 00:05 3691      /dev/dri/card0
b0820000-b0828000 rwxs 12727f000 00:05 3691      /dev/dri/card0
b0828000-b0830000 rwxs 127277000 00:05 3691      /dev/dri/card0
b0830000-b0838000 rwxs 12748d000 00:05 3691      /dev/dri/card0
b0838000-b0840000 rwxs 127485000 00:05 3691      /dev/dri/card0
b0840000-b0848000 rwxs 12747d000 00:05 3691      /dev/dri/card0
b0848000-b0850000 rwxs 127523000 00:05 3691      /dev/dri/card0
b0850000-b0858000 rwxs 12751b000 00:05 3691      /dev/dri/card0
b0858000-b0860000 rwxs 127513000 00:05 3691      /dev/dri/card0
b0860000-b0868000 rwxs 12750b000 00:05 3691      /dev/dri/card0
b0868000-b0870000 rwxs 127503000 00:05 3691      /dev/dri/card0
b0870000-b0878000 rwxs 1274fb000 00:05 3691      /dev/dri/card0
b0878000-b0880000 rwxs 12731f000 00:05 3691      /dev/dri/card0
b0880000-b0888000 rwxs 127317000 00:05 3691      /dev/dri/card0
b0888000-b0890000 rwxs 12730f000 00:05 3691      /dev/dri/card0
b0890000-b0898000 rwxs 127307000 00:05 3691      /dev/dri/card0
b0898000-b08a0000 rwxs 126f2f000 00:05 3691      /dev/dri/card0
b08a0000-b08a8000 rwxs 127ffa000 00:05 3691      /dev/dri/card0
b08a8000-b08b0000 rwxs 1272e7000 00:05 3691      /dev/dri/card0
b08b0000-b08b8000 rwxs 1272d7000 00:05 3691      /dev/dri/card0
b08b8000-b08c0000 rwxs 1272cf000 00:05 3691      /dev/dri/card0
b08c0000-b08c8000 rwxs 127afb000 00:05 3691      /dev/dri/card0
b08c8000-b08d0000 rwxs 127157000 00:05 3691      /dev/dri/card0
b08d0000-b08d8000 rwxs 12714f000 00:05 3691      /dev/dri/card0
b08d8000-b08e0000 rwxs 1274f2000 00:05 3691      /dev/dri/card0
b08e0000-b08e8000 rwxs 1274ea000 00:05 3691      /dev/dri/card0
b08e8000-b08f0000 rwxs 1271e0000 00:05 3691      /dev/dri/card0
b08f0000-b08f8000 rwxs 1271d8000 00:05 3691      /dev/dri/card0
b08f8000-b0900000 rwxs 1271d0000 00:05 3691      /dev/dri/card0
b0900000-b0908000 rwxs 1271c8000 00:05 3691      /dev/dri/card0
b0908000-b0910000 rwxs 1271c0000 00:05 3691      /dev/dri/card0
b0910000-b0918000 rwxs 1271b8000 00:05 3691      /dev/dri/card0
b0918000-b0920000 rwxs 1271b0000 00:05 3691      /dev/dri/card0
b0920000-b0928000 rwxs 1283e0000 00:05 3691      /dev/dri/card0
b0928000-b0930000 rwxs 1283d8000 00:05 3691      /dev/dri/card0
b0930000-b0938000 rwxs 1283d0000 00:05 3691      /dev/dri/card0
b0938000-b0940000 rwxs 1283c8000 00:05 3691      /dev/dri/card0
b0940000-b0948000 rwxs 1283c0000 00:05 3691      /dev/dri/card0
b0948000-b0950000 rwxs 1272ff000 00:05 3691      /dev/dri/card0
b0950000-b0958000 rwxs 127072000 00:05 3691      /dev/dri/card0
b0958000-b0960000 rwxs 12706a000 00:05 3691      /dev/dri/card0
b0960000-b0968000 rwxs 127062000 00:05 3691      /dev/dri/card0
b0968000-b0970000 rwxs 12705a000 00:05 3691      /dev/dri/card0
b0970000-b0978000 rwxs 127052000 00:05 3691      /dev/dri/card0
b0978000-b0980000 rwxs 12704a000 00:05 3691      /dev/dri/card0
b0980000-b0988000 rwxs 12703e000 00:05 3691      /dev/dri/card0
b0988000-b0990000 rwxs 127036000 00:05 3691      /dev/dri/card0
b0990000-b0998000 rwxs 12702e000 00:05 3691      /dev/dri/card0
b0998000-b09a0000 rwxs 127026000 00:05 3691      /dev/dri/card0
b09a0000-b09a8000 rwxs 12701e000 00:05 3691      /dev/dri/card0
b09a8000-b09b0000 rwxs 127016000 00:05 3691      /dev/dri/card0
b09b0000-b09b8000 rwxs 12700e000 00:05 3691      /dev/dri/card0
b09b8000-b09c0000 rwxs 127006000 00:05 3691      /dev/dri/card0
b09c0000-b09c8000 rwxs 126ffe000 00:05 3691      /dev/dri/card0
b09c8000-b09d0000 rwxs 126ff6000 00:05 3691      /dev/dri/card0
b09d0000-b09d8000 rwxs 126fee000 00:05 3691      /dev/dri/card0
b09d8000-b09e0000 rwxs 126fe5000 00:05 3691      /dev/dri/card0
b09e0000-b09e8000 rwxs 126fdd000 00:05 3691      /dev/dri/card0
b09e8000-b09f0000 rwxs 126fd5000 00:05 3691      /dev/dri/card0
b09f0000-b09f8000 rwxs 126fcd000 00:05 3691      /dev/dri/card0
b09f8000-b0a00000 rwxs 126fc5000 00:05 3691      /dev/dri/card0
b0a00000-b0a57000 rwxp 00000000 00:00 0 
b0a57000-b0b00000 ---p 00000000 00:00 0 
b0b00000-b0b08000 rwxs 126fbd000 00:05 3691      /dev/dri/card0
b0b08000-b0b10000 rwxs 127147000 00:05 3691      /dev/dri/card0
b0b10000-b0b18000 rwxs 12713f000 00:05 3691      /dev/dri/card0
b0b18000-b0b20000 rwxs 127137000 00:05 3691      /dev/dri/card0
b0b20000-b0b28000 rwxs 12710d000 00:05 3691      /dev/dri/card0
b0b28000-b0b30000 rwxs 127105000 00:05 3691      /dev/dri/card0
b0b30000-b0b38000 rwxs 126f57000 00:05 3691      /dev/dri/card0
b0b38000-b0b40000 rwxs 1290fa000 00:05 3691      /dev/dri/card0
b0b40000-b0b48000 rwxs 1295ba000 00:05 3691      /dev/dri/card0
b0b48000-b0b50000 rwxs 1272f7000 00:05 3691      /dev/dri/card0
b0b50000-b0b58000 rwxs 129138000 00:05 3691      /dev/dri/card0
b0b58000-b0b60000 rwxs 128b3c000 00:05 3691      /dev/dri/card0
b0b60000-b0b68000 rwxs 126f06000 00:05 3691      /dev/dri/card0
b0b68000-b0b70000 rwxs 126efe000 00:05 3691      /dev/dri/card0
b0b70000-b0b78000 rwxs 126ef6000 00:05 3691      /dev/dri/card0
b0b78000-b0b80000 rwxs 126eee000 00:05 3691      /dev/dri/card0
b0b80000-b0b88000 rwxs 126ee6000 00:05 3691      /dev/dri/card0
b0b88000-b0b90000 rwxs 126edd000 00:05 3691      /dev/dri/card0
b0b90000-b0b98000 rwxs 126ed5000 00:05 3691      /dev/dri/card0
b0b98000-b0ba0000 rwxs 126ecd000 00:05 3691      /dev/dri/card0
b0ba0000-b0ba8000 rwxs 126ec5000 00:05 3691      /dev/dri/card0
b0ba8000-b0bb0000 rwxs 126ebd000 00:05 3691      /dev/dri/card0
b0bb0000-b0bb8000 rwxs 126eb5000 00:05 3691      /dev/dri/card0
b0bb8000-b0bc0000 rwxs 126ead000 00:05 3691      /dev/dri/card0
b0bc0000-b0bc8000 rwxs 126e58000 00:05 3691      /dev/dri/card0
b0bc8000-b0bd0000 rwxs 126e50000 00:05 3691      /dev/dri/card0
b0bd0000-b0bd8000 rwxs 126e48000 00:05 3691      /dev/dri/card0
b0bd8000-b0be0000 rwxs 126e40000 00:05 3691      /dev/dri/card0
b0be0000-b0be8000 rwxs 126e38000 00:05 3691      /dev/dri/card0
b0be8000-b0bf0000 rwxs 126e30000 00:05 3691      /dev/dri/card0
b0bf0000-b0bf8000 rwxs 126e27000 00:05 3691      /dev/dri/card0
b0bf8000-b0c00000 rwxs 126e1f000 00:05 3691      /dev/dri/card0
b0c00000-b0c08000 rwxs 126e17000 00:05 3691      /dev/dri/card0
b0c08000-b0c10000 rwxs 126e0f000 00:05 3691      /dev/dri/card0
b0c10000-b0c18000 rwxs 126e07000 00:05 3691      /dev/dri/card0
b0c18000-b0c20000 rwxs 126dff000 00:05 3691      /dev/dri/card0
b0c20000-b0c28000 rwxs 126df7000 00:05 3691      /dev/dri/card0
b0c28000-b0c30000 rwxs 126def000 00:05 3691      /dev/dri/card0
b0c30000-b0c38000 rwxs 126de7000 00:05 3691      /dev/dri/card0
b0c38000-b0c40000 rwxs 126ddf000 00:05 3691      /dev/dri/card0
b0c40000-b0c48000 rwxs 126dd7000 00:05 3691      /dev/dri/card0
b0c48000-b0c50000 rwxs 126dc7000 00:05 3691      /dev/dri/card0
b0c50000-b0c58000 rwxs 126dbf000 00:05 3691      /dev/dri/card0
b0c58000-b0c60000 rwxs 126db3000 00:05 3691      /dev/dri/card0
b0c60000-b0c68000 rwxs 126dab000 00:05 3691      /dev/dri/card0
b0c68000-b0c70000 rwxs 126da3000 00:05 3691      /dev/dri/card0
b0c70000-b0c78000 rwxs 126d9b000 00:05 3691      /dev/dri/card0
b0c78000-b0c80000 rwxs 126d93000 00:05 3691      /dev/dri/card0
b0c80000-b0c88000 rwxs 126d8b000 00:05 3691      /dev/dri/card0
b0c88000-b0c90000 rwxs 126d52000 00:05 3691      /dev/dri/card0
b0c90000-b0c98000 rwxs 126d49000 00:05 3691      /dev/dri/card0
b0c98000-b0ca0000 rwxs 126d41000 00:05 3691      /dev/dri/card0
b0ca0000-b0ca8000 rwxs 126d39000 00:05 3691      /dev/dri/card0
b0ca8000-b0cb0000 rwxs 126d31000 00:05 3691      /dev/dri/card0
b0cb0000-b0cb8000 rwxs 126d29000 00:05 3691      /dev/dri/card0
b0cb8000-b0cc0000 rwxs 126d83000 00:05 3691      /dev/dri/card0
b0cc0000-b0cc8000 rwxs 126d7b000 00:05 3691      /dev/dri/card0
b0cc8000-b0cd0000 rwxs 126d73000 00:05 3691      /dev/dri/card0
b0cd0000-b0cd8000 rwxs 126d5e000 00:05 3691      /dev/dri/card0
b0cd8000-b0ce0000 rwxs 126d6b000 00:05 3691      /dev/dri/card0
b0ce0000-b0ce8000 rwxs 126d20000 00:05 3691      /dev/dri/card0
b0ce8000-b0cf0000 rwxs 126d18000 00:05 3691      /dev/dri/card0
b0cf0000-b0cf8000 rwxs 126d0f000 00:05 3691      /dev/dri/card0
b0cf8000-b0d00000 rwxs 126d07000 00:05 3691      /dev/dri/card0
b0d00000-b0d08000 rwxs 126cff000 00:05 3691      /dev/dri/card0
b0d08000-b0d10000 rwxs 126cf7000 00:05 3691      /dev/dri/card0
b0d10000-b0d18000 rwxs 126954000 00:05 3691      /dev/dri/card0
b0d18000-b0d20000 rwxs 126cb3000 00:05 3691      /dev/dri/card0
b0d20000-b0d28000 rwxs 126c9a000 00:05 3691      /dev/dri/card0
b0d28000-b0d30000 rwxs 127465000 00:05 3691      /dev/dri/card0
b0d30000-b0d38000 rwxs 12745d000 00:05 3691      /dev/dri/card0
b0d38000-b0d40000 rwxs 126cef000 00:05 3691      /dev/dri/card0
b0d40000-b0d48000 rwxs 126ce7000 00:05 3691      /dev/dri/card0
b0d48000-b0d50000 rwxs 126cdf000 00:05 3691      /dev/dri/card0
b0d50000-b0d58000 rwxs 126cd7000 00:05 3691      /dev/dri/card0
b0d58000-b0d60000 rwxs 126cbf000 00:05 3691      /dev/dri/card0
b0d60000-b0d68000 rwxs 12744c000 00:05 3691      /dev/dri/card0
b0d68000-b0d70000 rwxs 127444000 00:05 3691      /dev/dri/card0
b0d70000-b0d78000 rwxs 12743c000 00:05 3691      /dev/dri/card0
b0d78000-b0d80000 rwxs 126c42000 00:05 3691      /dev/dri/card0
b0d80000-b0d88000 rwxs 126c3a000 00:05 3691      /dev/dri/card0
b0d88000-b0d90000 rwxs 126c32000 00:05 3691      /dev/dri/card0
b0d90000-b0d98000 rwxs 126c2a000 00:05 3691      /dev/dri/card0
b0d98000-b0da0000 rwxs 126c22000 00:05 3691      /dev/dri/card0
b0da0000-b0da8000 rwxs 126c68000 00:05 3691      /dev/dri/card0
b0da8000-b0db0000 rwxs 126c60000 00:05 3691      /dev/dri/card0
b0db0000-b0db8000 rwxs 126c58000 00:05 3691      /dev/dri/card0
b0db8000-b0dc0000 rwxs 126be4000 00:05 3691      /dev/dri/card0
b0dc0000-b0dc8000 rwxs 126bdc000 00:05 3691      /dev/dri/card0
b0dc8000-b0dd0000 rwxs 126bd4000 00:05 3691      /dev/dri/card0
b0dd0000-b0dd8000 rwxs 126bcc000 00:05 3691      /dev/dri/card0
b0dd8000-b0de0000 rwxs 126bc4000 00:05 3691      /dev/dri/card0
b0de0000-b0de8000 rwxs 126c1a000 00:05 3691      /dev/dri/card0
b0de8000-b0df0000 rwxs 126c12000 00:05 3691      /dev/dri/card0
b0df0000-b0df8000 rwxs 126c0a000 00:05 3691      /dev/dri/card0
b0df8000-b0e00000 rwxs 126c02000 00:05 3691      /dev/dri/card0
b0e00000-b0e08000 rwxs 126bfa000 00:05 3691      /dev/dri/card0
b0e08000-b0e10000 rwxs 126bbc000 00:05 3691      /dev/dri/card0
b0e10000-b0e18000 rwxs 126bb4000 00:05 3691      /dev/dri/card0
b0e18000-b0e20000 rwxs 126bac000 00:05 3691      /dev/dri/card0
b0e20000-b0e28000 rwxs 126ba4000 00:05 3691      /dev/dri/card0
b0e28000-b0e30000 rwxs 126b9b000 00:05 3691      /dev/dri/card0
b0e30000-b0e38000 rwxs 126b93000 00:05 3691      /dev/dri/card0
b0e38000-b0e40000 rwxs 126b8b000 00:05 3691      /dev/dri/card0
b0e40000-b0e48000 rwxs 126b83000 00:05 3691      /dev/dri/card0
b0e48000-b0e50000 rwxs 126b7a000 00:05 3691      /dev/dri/card0
b0e50000-b0e58000 rwxs 126b72000 00:05 3691      /dev/dri/card0
b0e58000-b0e60000 rwxs 126b6a000 00:05 3691      /dev/dri/card0
b0e60000-b0e68000 rwxs 126b62000 00:05 3691      /dev/dri/card0
b0e68000-b0e70000 rwxs 126b59000 00:05 3691      /dev/dri/card0
b0e70000-b0e78000 rwxs 126b51000 00:05 3691      /dev/dri/card0
b0e78000-b0e80000 rwxs 126b43000 00:05 3691      /dev/dri/card0
b0e80000-b0e88000 rwxs 126b3b000 00:05 3691      /dev/dri/card0
b0e88000-b0e90000 rwxs 126b33000 00:05 3691      /dev/dri/card0
b0e90000-b0e98000 rwxs 126b2b000 00:05 3691      /dev/dri/card0
b0e98000-b0ea0000 rwxs 126b23000 00:05 3691      /dev/dri/card0
b0ea0000-b0ea8000 rwxs 126b1b000 00:05 3691      /dev/dri/card0
b0ea8000-b0eb0000 rwxs 126aed000 00:05 3691      /dev/dri/card0
b0eb0000-b0eb8000 rwxs 126ae5000 00:05 3691      /dev/dri/card0
b0eb8000-b0ec0000 rwxs 126add000 00:05 3691      /dev/dri/card0
b0ec0000-b0ec8000 rwxs 126ad5000 00:05 3691      /dev/dri/card0
b0ec8000-b0ed0000 rwxs 126acd000 00:05 3691      /dev/dri/card0
b0ed0000-b0ed8000 rwxs 126ac5000 00:05 3691      /dev/dri/card0
b0ed8000-b0ee0000 rwxs 126b13000 00:05 3691      /dev/dri/card0
b0ee0000-b0ee8000 rwxs 126b0b000 00:05 3691      /dev/dri/card0
b0ee8000-b0ef0000 rwxs 126b03000 00:05 3691      /dev/dri/card0
b0ef0000-b0ef8000 rwxs 126afb000 00:05 3691      /dev/dri/card0
b0ef8000-b0f00000 rwxs 126abc000 00:05 3691      /dev/dri/card0
b0f00000-b0f08000 rwxs 126ab4000 00:05 3691      /dev/dri/card0
b0f08000-b0f10000 rwxs 126aab000 00:05 3691      /dev/dri/card0
b0f10000-b0f18000 rwxs 126aa3000 00:05 3691      /dev/dri/card0
b0f18000-b0f20000 rwxs 126a9b000 00:05 3691      /dev/dri/card0
b0f20000-b0f28000 rwxs 126a93000 00:05 3691      /dev/dri/card0
b0f28000-b0f30000 rwxs 126a8b000 00:05 3691      /dev/dri/card0
b0f30000-b0f38000 rwxs 126a83000 00:05 3691      /dev/dri/card0
b0f38000-b0f40000 rwxs 126a7b000 00:05 3691      /dev/dri/card0
b0f40000-b0f48000 rwxs 129d44000 00:05 3691      /dev/dri/card0
b0f48000-b0f50000 rwxs 12983a000 00:05 3691      /dev/dri/card0
b0f50000-b0f58000 rwxs 129832000 00:05 3691      /dev/dri/card0
b0f58000-b0f60000 rwxs 12982a000 00:05 3691      /dev/dri/card0
b0f60000-b0f68000 rwxs 129c4f000 00:05 3691      /dev/dri/card0
b0f68000-b0f70000 rwxs 126a73000 00:05 3691      /dev/dri/card0
b0f70000-b0f78000 rwxs 1298b2000 00:05 3691      /dev/dri/card0
b0f78000-b0f80000 rwxs 126a6b000 00:05 3691      /dev/dri/card0
b0f80000-b0f88000 rwxs 126a63000 00:05 3691      /dev/dri/card0
b0f88000-b0f90000 rwxs 126a5b000 00:05 3691      /dev/dri/card0
b0f90000-b0f98000 rwxs 126a53000 00:05 3691      /dev/dri/card0
b0f98000-b0fa0000 rwxs 126a14000 00:05 3691      /dev/dri/card0
b0fa0000-b0fa8000 rwxs 126a0c000 00:05 3691      /dev/dri/card0
b0fa8000-b0fb0000 rwxs 129753000 00:05 3691      /dev/dri/card0
b0fb0000-b0fb8000 rwxs 12974b000 00:05 3691      /dev/dri/card0
b0fb8000-b0fc0000 rwxs 1269f3000 00:05 3691      /dev/dri/card0
b0fc0000-b0fc8000 rwxs 1269eb000 00:05 3691      /dev/dri/card0
b0fc8000-b0fd0000 rwxs 1269e3000 00:05 3691      /dev/dri/card0
b0fd0000-b0fd8000 rwxs 1269db000 00:05 3691      /dev/dri/card0
b0fd8000-b0fe0000 rwxs 1269d3000 00:05 3691      /dev/dri/card0
b0fe0000-b0fe8000 rwxs 1269cb000 00:05 3691      /dev/dri/card0
b0fe8000-b0ff0000 rwxs 1269c3000 00:05 3691      /dev/dri/card0
b0ff0000-b0ff8000 rwxs 1269a3000 00:05 3691      /dev/dri/card0
b0ff8000-b1000000 rwxs 1269bb000 00:05 3691      /dev/dri/card0
b1000000-b1008000 rwxs 1269b3000 00:05 3691      /dev/dri/card0
b1008000-b1010000 rwxs 1269ab000 00:05 3691      /dev/dri/card0
b1010000-b1018000 rwxs 12697b000 00:05 3691      /dev/dri/card0
b1018000-b1020000 rwxs 1295e3000 00:05 3691      /dev/dri/card0
b1020000-b1028000 rwxs 126993000 00:05 3691      /dev/dri/card0
b1028000-b1030000 rwxs 12698b000 00:05 3691      /dev/dri/card0
b1030000-b1038000 rwxs 126983000 00:05 3691      /dev/dri/card0
b1038000-b1040000 rwxs 126973000 00:05 3691      /dev/dri/card0
b1040000-b1048000 rwxs 12696b000 00:05 3691      /dev/dri/card0
b1048000-b1050000 rwxs 126963000 00:05 3691      /dev/dri/card0
b1050000-b1058000 rwxs 126cab000 00:05 3691      /dev/dri/card0
b1058000-b1060000 rwxs 126ca3000 00:05 3691      /dev/dri/card0
b1060000-b1068000 rwxs 12694b000 00:05 3691      /dev/dri/card0
b1068000-b1070000 rwxs 126943000 00:05 3691      /dev/dri/card0
b1070000-b1078000 rwxs 126938000 00:05 3691      /dev/dri/card0
b1078000-b1080000 rwxs 12687f000 00:05 3691      /dev/dri/card0
b1080000-b1088000 rwxs 126906000 00:05 3691      /dev/dri/card0
b1088000-b1090000 rwxs 1268e6000 00:05 3691      /dev/dri/card0
b1090000-b1098000 rwxs 126ccf000 00:05 3691      /dev/dri/card0
b1098000-b10a0000 rwxs 1268b8000 00:05 3691      /dev/dri/card0
b10a0000-b10a8000 rwxs 1268af000 00:05 3691      /dev/dri/card0
b10a8000-b10b0000 rwxs 1295db000 00:05 3691      /dev/dri/card0
b10b0000-b10b8000 rwxs 12689f000 00:05 3691      /dev/dri/card0
b10b8000-b10c0000 rwxs 126897000 00:05 3691      /dev/dri/card0
b10c0000-b10c8000 rwxs 12688f000 00:05 3691      /dev/dri/card0
b10c8000-b10d0000 rwxs 126887000 00:05 3691      /dev/dri/card0
b10d0000-b10d8000 rwxs 126cc7000 00:05 3691      /dev/dri/card0
b10d8000-b10e0000 rwxs 126877000 00:05 3691      /dev/dri/card0
b10e0000-b10e8000 rwxs 12686f000 00:05 3691      /dev/dri/card0
b10e8000-b10f0000 rwxs 126867000 00:05 3691      /dev/dri/card0
b10f0000-b10f8000 rwxs 12685f000 00:05 3691      /dev/dri/card0
b10f8000-b1100000 rwxs 126857000 00:05 3691      /dev/dri/card0
b1100000-b1108000 rwxs 12684f000 00:05 3691      /dev/dri/card0
b1108000-b1110000 rwxs 126847000 00:05 3691      /dev/dri/card0
b1110000-b1118000 rwxs 12683f000 00:05 3691      /dev/dri/card0
b1118000-b1120000 rwxs 126837000 00:05 3691      /dev/dri/card0
b1120000-b1128000 rwxs 12682f000 00:05 3691      /dev/dri/card0
b1128000-b1130000 rwxs 126827000 00:05 3691      /dev/dri/card0
b1130000-b1138000 rwxs 12681f000 00:05 3691      /dev/dri/card0
b1138000-b1140000 rwxs 126817000 00:05 3691      /dev/dri/card0
b1140000-b1148000 rwxs 12680f000 00:05 3691      /dev/dri/card0
b1148000-b1150000 rwxs 12988a000 00:05 3691      /dev/dri/card0
b1150000-b1158000 rwxs 129882000 00:05 3691      /dev/dri/card0
b1158000-b1160000 rwxs 1267f7000 00:05 3691      /dev/dri/card0
b1160000-b1168000 rwxs 1267ef000 00:05 3691      /dev/dri/card0
b1168000-b1170000 rwxs 1267e7000 00:05 3691      /dev/dri/card0
b1170000-b1178000 rwxs 1267df000 00:05 3691      /dev/dri/card0
b1178000-b1180000 rwxs 1267d7000 00:05 3691      /dev/dri/card0
b1180000-b1188000 rwxs 1267cf000 00:05 3691      /dev/dri/card0
b1188000-b1190000 rwxs 126792000 00:05 3691      /dev/dri/card0
b1190000-b1198000 rwxs 12678a000 00:05 3691      /dev/dri/card0
b1198000-b11a0000 rwxs 12691f000 00:05 3691      /dev/dri/card0
b11a0000-b11a8000 rwxs 1268fe000 00:05 3691      /dev/dri/card0
b11a8000-b11b0000 rwxs 1268f6000 00:05 3691      /dev/dri/card0
b11b0000-b11b8000 rwxs 1268ee000 00:05 3691      /dev/dri/card0
b11b8000-b11c0000 rwxs 128268000 00:05 3691      /dev/dri/card0
b11c0000-b11c8000 rwxs 128260000 00:05 3691      /dev/dri/card0
b11c8000-b11d0000 rwxs 127ee2000 00:05 3691      /dev/dri/card0
b11d0000-b11d8000 rwxs 1267af000 00:05 3691      /dev/dri/card0
b11d8000-b11e0000 rwxs 1267a7000 00:05 3691      /dev/dri/card0
b11e0000-b11e8000 rwxs 12679f000 00:05 3691      /dev/dri/card0
b11e8000-b11f0000 rwxs 126917000 00:05 3691      /dev/dri/card0
b11f0000-b11f8000 rwxs 12690e000 00:05 3691      /dev/dri/card0
b11f8000-b1200000 rwxs 127571000 00:05 3691      /dev/dri/card0
b1200000-b1208000 rwxs 127569000 00:05 3691      /dev/dri/card0
b1208000-b1210000 rwxs 129b5f000 00:05 3691      /dev/dri/card0
b1210000-b1218000 rwxs 129b57000 00:05 3691      /dev/dri/card0
b1218000-b1220000 rwxs 1272a7000 00:05 3691      /dev/dri/card0
b1220000-b1228000 rwxs 12671f000 00:05 3691      /dev/dri/card0
b1228000-b1230000 rwxs 126717000 00:05 3691      /dev/dri/card0
b1230000-b1238000 rwxs 12670c000 00:05 3691      /dev/dri/card0
b1238000-b1240000 rwxs 126704000 00:05 3691      /dev/dri/card0
b1240000-b1248000 rwxs 126739000 00:05 3691      /dev/dri/card0
b1248000-b1250000 rwxs 1266fb000 00:05 3691      /dev/dri/card0
b1250000-b1258000 rwxs 1266f3000 00:05 3691      /dev/dri/card0
b1258000-b1260000 rwxs 1267bf000 00:05 3691      /dev/dri/card0
b1260000-b1268000 rwxs 1267b7000 00:05 3691      /dev/dri/card0
b1268000-b1270000 rwxs 126f27000 00:05 3691      /dev/dri/card0
b1270000-b1278000 rwxs 1266d3000 00:05 3691      /dev/dri/card0
b1278000-b1280000 rwxs 1266cb000 00:05 3691      /dev/dri/card0
b1280000-b1288000 rwxs 1285b0000 00:05 3691      /dev/dri/card0
b1288000-b1290000 rwxs 126f47000 00:05 3691      /dev/dri/card0
b1290000-b1298000 rwxs 129703000 00:05 3691      /dev/dri/card0
b1298000-b12a0000 rwxs 12699b000 00:05 3691      /dev/dri/card0
b12a0000-b12a8000 rwxs 1280e0000 00:05 3691      /dev/dri/card0
b12a8000-b12b0000 rwxs 1252b1000 00:05 3691      /dev/dri/card0
b12b0000-b12b8000 rwxs 12666e000 00:05 3691      /dev/dri/card0
b12b8000-b12c0000 rwxs 12667f000 00:05 3691      /dev/dri/card0
b12c0000-b12c8000 rwxs 126677000 00:05 3691      /dev/dri/card0
b12c8000-b12d0000 rwxs 126666000 00:05 3691      /dev/dri/card0
b12d0000-b12d8000 rwxs 126656000 00:05 3691      /dev/dri/card0
b12d8000-b12e0000 rwxs 126698000 00:05 3691      /dev/dri/card0
b12e0000-b12e8000 rwxs 1268a7000 00:05 3691      /dev/dri/card0
b12e8000-b12f0000 rwxs 1272b7000 00:05 3691      /dev/dri/card0
b12f0000-b12f8000 rwxs 12665e000 00:05 3691      /dev/dri/card0
b12f8000-b1300000 rwxs 1265dd000 00:05 3691      /dev/dri/card0
b1300000-b13fd000 rwxp 00000000 00:00 0 
b13fd000-b1400000 ---p 00000000 00:00 0 
b1403000-b140b000 rwxs 126f3f000 00:05 3691      /dev/dri/card0
b140b000-b1413000 rwxs 126635000 00:05 3691      /dev/dri/card0
b1413000-b141b000 rwxs 1270fd000 00:05 3691      /dev/dri/card0
b141b000-b1423000 rwxs 1270f5000 00:05 3691      /dev/dri/card0
b1423000-b142b000 rwxs 1270ed000 00:05 3691      /dev/dri/card0
b142b000-b1433000 rwxs 126f37000 00:05 3691      /dev/dri/card0
b1433000-b143b000 rwxs 1272af000 00:05 3691      /dev/dri/card0
b143b000-b1443000 rwxs 1265fe000 00:05 3691      /dev/dri/card0
b1443000-b144b000 rwxs 1265f6000 00:05 3691      /dev/dri/card0
b144b000-b1453000 rwxs 1265ed000 00:05 3691      /dev/dri/card0
b1453000-b145b000 rwxs 1265e5000 00:05 3691      /dev/dri/card0
b145b000-b145e000 ---p 00000000 00:00 0 
b145e000-b14ac000 rwxp 00000000 00:00 0 
b14ac000-b14b4000 rwxs 1270e5000 00:05 3691      /dev/dri/card0
b14b4000-b14bc000 rwxs 1265d5000 00:05 3691      /dev/dri/card0
b14bc000-b1512000 rwxs 12520b000 00:05 3691      /dev/dri/card0
b1512000-b1568000 rwxs 1251b5000 00:05 3691      /dev/dri/card0
b1569000-b1571000 rwxs 127ef2000 00:05 3691      /dev/dri/card0
b1571000-b1579000 rwxs 1253a8000 00:05 3691      /dev/dri/card0
b1579000-b1581000 rwxs 1265cd000 00:05 3691      /dev/dri/card0
b1581000-b1589000 rwxs 1265c5000 00:05 3691      /dev/dri/card0
b1589000-b158a000 rwxs 1259ac000 00:05 3691      /dev/dri/card0
b158b000-b1593000 rwxs 1265bd000 00:05 3691      /dev/dri/card0
b1593000-b159b000 rwxs 1265b5000 00:05 3691      /dev/dri/card0
b159b000-b15f1000 rwxs 125352000 00:05 3691      /dev/dri/card0
b15f1000-b1647000 rwxs 124c3c000 00:05 3691      /dev/dri/card0
b1647000-b164f000 rwxs 12599e000 00:05 3691      /dev/dri/card0
b164f000-b1657000 rwxs 125996000 00:05 3691      /dev/dri/card0
b1657000-b165f000 rwxs 127e52000 00:05 3691      /dev/dri/card0
b165f000-b1667000 rwxs 127815000 00:05 3691      /dev/dri/card0
b1667000-b167d000 rwxs 125978000 00:05 3691      /dev/dri/card0
b167e000-b1686000 rwxs 12587e000 00:05 3691      /dev/dri/card0
b1686000-b1e88000 rwxp 00000000 00:00 0 
b1e88000-b1e9e000 rwxs 12578c000 00:05 3691      /dev/dri/card0
b1e9e000-b23aa000 rwxp 00000000 00:00 0 
b23aa000-b2613000 r-xp 00000000 08:01 6296477    /usr/lib/dri/r300_dri.so
b2613000-b2617000 r-xp 00269000 08:01 6296477    /usr/lib/dri/r300_dri.so
b2617000-b2619000 rwxp 0026d000 08:01 6296477    /usr/lib/dri/r300_dri.so
b2619000-b2628000 rwxp 00000000 00:00 0 
b2628000-b2631000 r-xp 00000000 08:01 8519746    /lib/libdrm.so.2.4.0
b2631000-b2632000 r-xp 00008000 08:01 8519746    /lib/libdrm.so.2.4.0
b2632000-b2633000 rwxp 00009000 08:01 8519746    /lib/libdrm.so.2.4.0
b2633000-b268d000 r-xp 00000000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
b268d000-b2692000 r-xp 00059000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
b2692000-b2697000 rwxp 0005e000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
b2697000-b2698000 rwxp 00000000 00:00 0 
b269a000-b26a2000 rwxs 12598e000 00:05 3691      /dev/dri/card0
b26a2000-b26a5000 r-xp 00000000 08:01 8142941    /home/ben/.minecraft/bin/natives/libjinput-linux.so
b26a5000-b26a6000 r-xp 00002000 08:01 8142941    /home/ben/.minecraft/bin/natives/libjinput-linux.so
b26a6000-b26a7000 rwxp 00003000 08:01 8142941    /home/ben/.minecraft/bin/natives/libjinput-linux.so
b26a7000-b26fe000 r-xp 00000000 08:01 8142943    /home/ben/.minecraft/bin/natives/liblwjgl.so
b26fe000-b26ff000 r-xp 00056000 08:01 8142943    /home/ben/.minecraft/bin/natives/liblwjgl.so
b26ff000-b2700000 rwxp 00057000 08:01 8142943    /home/ben/.minecraft/bin/natives/liblwjgl.so
b2700000-b27fd000 rwxp 00000000 00:00 0 
b27fd000-b2800000 ---p 00000000 00:00 0 
b2800000-b2803000 r-xp 00000000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
b2803000-b2804000 r-xp 00002000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
b2804000-b2805000 rwxp 00003000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
b2805000-b2809000 r-xp 00000000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
b2809000-b280a000 r-xp 00003000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
b280a000-b280b000 rwxp 00004000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
b280b000-b2816000 r-xs 00127000 08:01 8142926    /home/ben/.minecraft/bin/minecraft.jar
b2816000-b2819000 r-xs 0001f000 08:01 8142925    /home/ben/.minecraft/bin/lwjgl_util.jar
b2819000-b281e000 r-xs 00033000 08:01 8142924    /home/ben/.minecraft/bin/jinput.jar
b281e000-b2827000 r-xs 000ac000 08:01 8142923    /home/ben/.minecraft/bin/lwjgl.jar
b2827000-b282a000 ---p 00000000 00:00 0 
b282a000-b2878000 rwxp 00000000 00:00 0 
b2878000-b287b000 ---p 00000000 00:00 0 
b287b000-b28c9000 rwxp 00000000 00:00 0 
b28c9000-b2a5a000 rwxs 00000000 00:04 2621461    /SYSV00000000 (deleted)
b2a5e000-b2cca000 rwxp 00000000 00:00 0 
b2cca000-b2d2a000 rwxs 00000000 00:04 1867790    /SYSV00000000 (deleted)
b2d2e000-b2d31000 rwxs 1289fb000 00:05 3691      /dev/dri/card0
b2d31000-b2d39000 rwxs 1265ad000 00:05 3691      /dev/dri/card0
b2d39000-b2d41000 rwxs 1265a5000 00:05 3691      /dev/dri/card0
b2d41000-b2d49000 rwxs 12659d000 00:05 3691      /dev/dri/card0
b2d49000-b2d51000 rwxs 126595000 00:05 3691      /dev/dri/card0
b2d51000-b2d59000 rwxs 12658d000 00:05 3691      /dev/dri/card0
b2d59000-b2d61000 rwxs 126585000 00:05 3691      /dev/dri/card0
b2d61000-b2d69000 rwxs 12657d000 00:05 3691      /dev/dri/card0
b2d69000-b2d71000 rwxs 126575000 00:05 3691      /dev/dri/card0
b2d71000-b2d79000 rwxs 12711a000 00:05 3691      /dev/dri/card0
b2d79000-b2d81000 rwxs 126565000 00:05 3691      /dev/dri/card0
b2d81000-b2d89000 rwxs 12655d000 00:05 3691      /dev/dri/card0
b2d89000-b2d91000 rwxs 12549f000 00:05 3691      /dev/dri/card0
b2d91000-b2d99000 rwxs 125497000 00:05 3691      /dev/dri/card0
b2d99000-b2da1000 rwxs 12548f000 00:05 3691      /dev/dri/card0
b2da1000-b2da9000 rwxs 1254bc000 00:05 3691      /dev/dri/card0
b2da9000-b2db1000 rwxs 1254b4000 00:05 3691      /dev/dri/card0
b2db1000-b2db9000 rwxs 1254ac000 00:05 3691      /dev/dri/card0
b2db9000-b2dc1000 rwxs 125425000 00:05 3691      /dev/dri/card0
b2dc1000-b2dc9000 rwxs 127877000 00:05 3691      /dev/dri/card0
b2dc9000-b2dd1000 rwxs 1277ad000 00:05 3691      /dev/dri/card0
b2dd1000-b2dd9000 rwxs 128748000 00:05 3691      /dev/dri/card0
b2dd9000-b2de1000 rwxs 128798000 00:05 3691      /dev/dri/card0
b2de1000-b2de9000 rwxs 1251a2000 00:05 3691      /dev/dri/card0
b2de9000-b2df1000 rwxs 12519a000 00:05 3691      /dev/dri/card0
b2df1000-b2df9000 rwxs 127f6a000 00:05 3691      /dev/dri/card0
b2df9000-b2e01000 rwxs 127f1a000 00:05 3691      /dev/dri/card0
b2e01000-b2e09000 rwxs 128160000 00:05 3691      /dev/dri/card0
b2e09000-b2e11000 rwxs 1264d5000 00:05 3691      /dev/dri/card0
b2e11000-b2e67000 rwxs 126507000 00:05 3691      /dev/dri/card0
b2e67000-b2ebd000 rwxs 125439000 00:05 3691      /dev/dri/card0
b2ebd000-b2ec5000 rwxs 125192000 00:05 3691      /dev/dri/card0
b2ec5000-b2ecd000 rwxs 125186000 00:05 3691      /dev/dri/card0
b2ecd000-b2ed5000 rwxs 12517e000 00:05 3691      /dev/dri/card0
b2ed5000-b2edd000 rwxs 1252a9000 00:05 3691      /dev/dri/card0
b2edd000-b2ee5000 rwxs 1252a1000 00:05 3691      /dev/dri/card0
b2ee5000-b2eed000 rwxs 125299000 00:05 3691      /dev/dri/card0
b2eed000-b2ef5000 rwxs 125291000 00:05 3691      /dev/dri/card0
b2ef5000-b2efd000 rwxs 125289000 00:05 3691      /dev/dri/card0
b2efd000-b2f05000 rwxs 125176000 00:05 3691      /dev/dri/card0
b2f05000-b2f0d000 rwxs 125281000 00:05 3691      /dev/dri/card0
b2f0d000-b2f15000 rwxs 125279000 00:05 3691      /dev/dri/card0
b2f15000-b2f18000 ---p 00000000 00:00 0 
b2f18000-b2f66000 rwxp 00000000 00:00 0 
b2f66000-b2f6e000 rwxs 125271000 00:05 3691      /dev/dri/card0
b2f6e000-b2f76000 rwxs 125269000 00:05 3691      /dev/dri/card0
b2f76000-b2f7e000 rwxs 125261000 00:05 3691      /dev/dri/card0
b2f7e000-b2f86000 rwxs 1253db000 00:05 3691      /dev/dri/card0
b2f86000-b2f8e000 rwxs 125415000 00:05 3691      /dev/dri/card0
b2f8e000-b2f96000 rwxs 12540d000 00:05 3691      /dev/dri/card0
b2f96000-b2f9e000 rwxs 125405000 00:05 3691      /dev/dri/card0
b2f9e000-b2fa6000 rwxs 124a79000 00:05 3691      /dev/dri/card0
b2fa6000-b2fae000 rwxs 124a71000 00:05 3691      /dev/dri/card0
b2fae000-b2fb6000 rwxs 1253d0000 00:05 3691      /dev/dri/card0
b2fb6000-b2fbe000 rwxs 1253c8000 00:05 3691      /dev/dri/card0
b2fbe000-b2fc6000 rwxs 1253c0000 00:05 3691      /dev/dri/card0
b2fc6000-b2fce000 rwxs 1253b8000 00:05 3691      /dev/dri/card0
b2fce000-b2fd6000 rwxs 1256e0000 00:05 3691      /dev/dri/card0
b2fd6000-b2fde000 rwxs 1256d0000 00:05 3691      /dev/dri/card0
b2fde000-b2fe6000 rwxs 1258c3000 00:05 3691      /dev/dri/card0
b2fe6000-b2fee000 rwxs 12a0d9000 00:05 3691      /dev/dri/card0
b2fee000-b2ff6000 rwxs 1258bb000 00:05 3691      /dev/dri/card0
b2ff6000-b2ffe000 rwxs 1256ef000 00:05 3691      /dev/dri/card0
b2ffe000-b3006000 rwxs 12a0d1000 00:05 3691      /dev/dri/card0
b3006000-b300e000 rwxs 125802000 00:05 3691      /dev/dri/card0
b300e000-b3016000 rwxs 1259ad000 00:05 3691      /dev/dri/card0
b3016000-b301e000 rwxs 1257f5000 00:05 3691      /dev/dri/card0
b301e000-b3026000 rwxs 1253f5000 00:05 3691      /dev/dri/card0
b3026000-b302e000 rwxs 1257ed000 00:05 3691      /dev/dri/card0
b302e000-b3036000 rwxs 1253ed000 00:05 3691      /dev/dri/card0
b3036000-b303e000 rwxs 1257ce000 00:05 3691      /dev/dri/card0
b303e000-b3046000 rwxs 1257c6000 00:05 3691      /dev/dri/card0
b3046000-b304e000 rwxs 1257b6000 00:05 3691      /dev/dri/card0
b304e000-b3056000 rwxs 1257a2000 00:05 3691      /dev/dri/card0
b3056000-b305e000 rwxs 1257ae000 00:05 3691      /dev/dri/card0
b305e000-b3061000 ---p 00000000 00:00 0 
b3061000-b30af000 rwxp 00000000 00:00 0 
b30af000-b30b2000 ---p 00000000 00:00 0 
b30b2000-b3100000 rwxp 00000000 00:00 0 
b3100000-b31fe000 rwxp 00000000 00:00 0 
b31fe000-b3200000 ---p 00000000 00:00 0 
b3200000-b3202000 rwxs 1257ac000 00:05 3691      /dev/dri/card0
b3202000-b3204000 rwxs 1257aa000 00:05 3691      /dev/dri/card0
b3204000-b3208000 r-xp 00000000 08:01 8651802    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
b3208000-b3209000 r-xp 00004000 08:01 8651802    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
b3209000-b320a000 rwxp 00005000 08:01 8651802    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
b320a000-b320b000 rwxs 1259aa000 00:05 3691      /dev/dri/card0
b320c000-b320f000 r-xs 000cb000 08:01 6301466    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/ext/localedata.jar
b320f000-b3212000 r-xs 00027000 08:01 6301467    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/ext/sunjce_provider.jar
b3212000-b3219000 r-xs 00094000 08:01 6291738    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/jsse.jar
b3219000-b321c000 ---p 00000000 00:00 0 
b321c000-b326a000 rwxp 00000000 00:00 0 
b326a000-b326d000 ---p 00000000 00:00 0 
b326d000-b32bb000 rwxp 00000000 00:00 0 
b32bb000-b32be000 ---p 00000000 00:00 0 
b32be000-b330c000 rwxp 00000000 00:00 0 
b330c000-b331d000 r-xp 00000000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b331d000-b331e000 r-xp 00011000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b331e000-b331f000 rwxp 00012000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b331f000-b3329000 r-xp 00000000 08:01 8519861    /lib/libudev.so.0.6.1
b3329000-b332a000 r-xp 00009000 08:01 8519861    /lib/libudev.so.0.6.1
b332a000-b332b000 rwxp 0000a000 08:01 8519861    /lib/libudev.so.0.6.1
b332b000-b333f000 r-xp 00000000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
b333f000-b3340000 r-xp 00013000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
b3340000-b3341000 rwxp 00014000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
b3341000-b3365000 r-xp 00000000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
b3365000-b3366000 r-xp 00023000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
b3366000-b3367000 rwxp 00024000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
b3367000-b339e000 r-xp 00000000 08:01 8519741    /lib/libdbus-1.so.3.4.0
b339e000-b339f000 r-xp 00036000 08:01 8519741    /lib/libdbus-1.so.3.4.0
b339f000-b33a0000 rwxp 00037000 08:01 8519741    /lib/libdbus-1.so.3.4.0
b33a0000-b33d9000 r-xp 00000000 08:01 6294870    /usr/lib/libibus.so.1.0.0
b33d9000-b33da000 r-xp 00039000 08:01 6294870    /usr/lib/libibus.so.1.0.0
b33da000-b33db000 rwxp 0003a000 08:01 6294870    /usr/lib/libibus.so.1.0.0
b33db000-b33dd000 r-xp 00000000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
b33dd000-b33de000 r-xp 00001000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
b33de000-b33df000 rwxp 00002000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
b33df000-b33e2000 r-xs 00013000 08:01 6291739    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/jce.jar
b33e2000-b33ea000 r-xs 00115000 08:01 6301642    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/resources.jar
b33ea000-b33ef000 r-xp 00000000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
b33ef000-b33f0000 r-xp 00004000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
b33f0000-b33f1000 rwxp 00005000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
b33f1000-b3489000 r-xp 00000000 08:01 7212737    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b3489000-b348b000 r-xp 00000000 08:01 6299250    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b348b000-b348c000 r-xp 00001000 08:01 6299250    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b348c000-b348d000 rwxp 00002000 08:01 6299250    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b348d000-b3494000 r-xp 00000000 08:01 6301562    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libnio.so
b3494000-b3495000 rwxp 00006000 08:01 6301562    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libnio.so
b3495000-b34a9000 r-xp 00000000 08:01 6301605    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libnet.so
b34a9000-b34aa000 rwxp 00013000 08:01 6301605    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libnet.so
b34aa000-b34ab000 r-xs 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b34ab000-b34b1000 r-xs 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b34b1000-b34b3000 r-xs 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b34b3000-b34b6000 r-xs 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b34b6000-b34b7000 r-xs 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b34b7000-b34ba000 r-xs 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b34ba000-b34bb000 r-xs 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b34bb000-b34bc000 r-xs 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b34bc000-b34bd000 r-xs 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b34bd000-b34c1000 r-xs 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b34c1000-b34c4000 r-xs 00000000 08:01 4594875    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b34c4000-b34cf000 r-xs 00000000 08:01 4587570    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b34cf000-b34d2000 r-xs 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b34d2000-b34d3000 r-xs 00000000 08:01 4587573    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b34d3000-b34db000 r-xs 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b34db000-b3501000 r-xp 00000000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b3501000-b3502000 r-xp 00025000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b3502000-b3503000 rwxp 00026000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b3503000-b350a000 r-xp 00000000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
b350a000-b350b000 r-xp 00006000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
b350b000-b350c000 rwxp 00007000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
b350c000-b3519000 r-xp 00000000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
b3519000-b351a000 r-xp 0000c000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
b351a000-b351b000 rwxp 0000d000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
b351b000-b3520000 r-xp 00000000 08:01 6295038    /usr/lib/libogg.so.0.6.0
b3520000-b3521000 r-xp 00004000 08:01 6295038    /usr/lib/libogg.so.0.6.0
b3521000-b3522000 rwxp 00005000 08:01 6295038    /usr/lib/libogg.so.0.6.0
b3522000-b3549000 r-xp 00000000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
b3549000-b354a000 r-xp 00026000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
b354a000-b354b000 rwxp 00027000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
b354b000-b3552000 r-xp 00000000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
b3552000-b3553000 r-xp 00006000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
b3553000-b3554000 rwxp 00007000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
b3554000-b3562000 r-xp 00000000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
b3562000-b3563000 r-xp 0000d000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
b3563000-b3564000 rwxp 0000e000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
b3564000-b3567000 r-xp 00000000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
b3567000-b3568000 r-xp 00003000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
b3568000-b3569000 rwxp 00004000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
b3569000-b356a000 r-xp 00000000 08:01 6301565    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libjawt.so
b356a000-b356b000 rwxp 00000000 08:01 6301565    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libjawt.so
b356b000-b356d000 r-xp 00000000 08:01 7736411    /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
b356d000-b3575000 r-xs 00000000 08:01 8143416    /home/ben/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b3575000-b3578000 r-xs 00000000 08:01 4587581    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b3578000-b357c000 r-xp 00000000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b357c000-b357d000 ---p 00004000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b357d000-b357e000 r-xp 00004000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b357e000-b357f000 rwxp 00005000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b357f000-b369d000 r-xp 00000000 08:01 6299152    /usr/lib/locale/en_GB.utf8/LC_COLLATE
b369d000-b36c1000 r-xp 00000000 08:01 8519756    /lib/libexpat.so.1.5.2
b36c1000-b36c3000 r-xp 00024000 08:01 8519756    /lib/libexpat.so.1.5.2
b36c3000-b36c4000 rwxp 00026000 08:01 8519756    /lib/libexpat.so.1.5.2
b36c4000-b36dd000 r-xp 00000000 08:01 8519845    /lib/libselinux.so.1
b36dd000-b36de000 r-xp 00018000 08:01 8519845    /lib/libselinux.so.1
b36de000-b36df000 rwxp 00019000 08:01 8519845    /lib/libselinux.so.1
b36df000-b36ef000 r-xp 00000000 08:01 8651815    /lib/tls/i686/cmov/libresolv-2.11.1.so
b36ef000-b36f0000 r-xp 00010000 08:01 8651815    /lib/tls/i686/cmov/libresolv-2.11.1.so
b36f0000-b36f1000 rwxp 00011000 08:01 8651815    /lib/tls/i686/cmov/libresolv-2.11.1.so
b36f1000-b36f3000 rwxp 00000000 00:00 0 
b36f3000-b3722000 r-xp 00000000 08:01 8519821    /lib/libpcre.so.3.12.1
b3722000-b3723000 r-xp 0002e000 08:01 8519821    /lib/libpcre.so.3.12.1
b3723000-b3724000 rwxp 0002f000 08:01 8519821    /lib/libpcre.so.3.12.1
b3724000-b372a000 r-xp 00000000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
b372a000-b372b000 r-xp 00005000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
b372b000-b372c000 rwxp 00006000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
b372c000-b374f000 r-xp 00000000 08:01 8519833    /lib/libpng12.so.0.42.0
b374f000-b3750000 r-xp 00022000 08:01 8519833    /lib/libpng12.so.0.42.0
b3750000-b3751000 rwxp 00023000 08:01 8519833    /lib/libpng12.so.0.42.0
b3751000-b3765000 r-xp 00000000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
b3765000-b3766000 r-xp 00013000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
b3766000-b3767000 rwxp 00014000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
b3767000-b376f000 r-xp 00000000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
b376f000-b3770000 r-xp 00007000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
b3770000-b3771000 rwxp 00008000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
b3771000-b37e4000 r-xp 00000000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
b37e4000-b37e5000 ---p 00073000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
b37e5000-b37e6000 r-xp 00073000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
b37e6000-b37e7000 rwxp 00074000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
b37e7000-b37e8000 rwxp 00000000 00:00 0 
b37e8000-b383f000 r-xp 00000000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
b383f000-b3841000 r-xp 00057000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
b3841000-b3842000 rwxp 00059000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
b3842000-b390a000 r-xp 00000000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
b390a000-b390b000 r-xp 000c7000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
b390b000-b390c000 rwxp 000c8000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
b390c000-b3949000 r-xp 00000000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
b3949000-b394a000 r-xp 0003c000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
b394a000-b394b000 rwxp 0003d000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
b394b000-b3979000 r-xp 00000000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
b3979000-b397a000 r-xp 0002d000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
b397a000-b397b000 rwxp 0002e000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
b397b000-b398e000 r-xp 00000000 08:01 8519878    /lib/libz.so.1.2.3.3
b398e000-b398f000 r-xp 00012000 08:01 8519878    /lib/libz.so.1.2.3.3
b398f000-b3990000 rwxp 00013000 08:01 8519878    /lib/libz.so.1.2.3.3
b3990000-b3a01000 r-xp 00000000 08:01 6294614    /usr/lib/libfreetype.so.6.3.22
b3a01000-b3a05000 r-xp 00070000 08:01 6294614    /usr/lib/libfreetype.so.6.3.22
b3a05000-b3a06000 rwxp 00074000 08:01 6294614    /usr/lib/libfreetype.so.6.3.22
b3a06000-b3a46000 r-xp 00000000 08:01 6295055    /usr/lib/libpango-1.0.so.0.2800.0
b3a46000-b3a47000 ---p 00040000 08:01 6295055    /usr/lib/libpango-1.0.so.0.2800.0
b3a47000-b3a48000 r-xp 00040000 08:01 6295055    /usr/lib/libpango-1.0.so.0.2800.0
b3a48000-b3a49000 rwxp 00041000 08:01 6295055    /usr/lib/libpango-1.0.so.0.2800.0
b3a49000-b3a6e000 r-xp 00000000 08:01 6295059    /usr/lib/libpangoft2-1.0.so.0.2800.0
b3a6e000-b3a6f000 r-xp 00024000 08:01 6295059    /usr/lib/libpangoft2-1.0.so.0.2800.0
b3a6f000-b3a70000 rwxp 00025000 08:01 6295059    /usr/lib/libpangoft2-1.0.so.0.2800.0
b3a70000-b3b0a000 r-xp 00000000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
b3b0a000-b3b0b000 ---p 0009a000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
b3b0b000-b3b0c000 r-xp 0009a000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
b3b0c000-b3b0d000 rwxp 0009b000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
b3b0d000-b3b0e000 rwxp 00000000 00:00 0 
b3b0e000-b3b85000 r-xp 00000000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
b3b85000-b3b87000 r-xp 00076000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
b3b87000-b3b88000 rwxp 00078000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
b3b88000-b3c1b000 r-xp 00000000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
b3c1b000-b3c1d000 r-xp 00093000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
b3c1d000-b3c1e000 rwxp 00095000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
b3c1e000-b3feb000 r-xp 00000000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
b3feb000-b3fef000 r-xp 003cd000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
b3fef000-b3ff1000 rwxp 003d1000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
b3ff1000-b3ff3000 rwxp 00000000 00:00 0 
b3ff3000-b3ff4000 r-xs 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b3ff4000-b3ffa000 r-xs 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b3ffa000-b3ffc000 r-xs 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b3ffc000-b3fff000 r-xs 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b3fff000-b4000000 r-xs 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4000000-b4003000 r-xs 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4003000-b4004000 r-xs 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4004000-b4005000 r-xs 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4005000-b4006000 r-xs 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4006000-b400a000 r-xs 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b400a000-b400d000 r-xs 00000000 08:01 4594875    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b400d000-b4018000 r-xs 00000000 08:01 4587570    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4018000-b4020000 r-xs 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4020000-b4021000 rwxs 1294d2000 00:05 3691      /dev/dri/card0
b4021000-b4022000 r-xp 00000000 08:01 7736499    /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
b4022000-b4025000 r-xp 00000000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
b4025000-b4026000 r-xp 00002000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
b4026000-b4027000 rwxp 00003000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
b4027000-b402b000 r-xp 00000000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
b402b000-b402c000 r-xp 00003000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
b402c000-b402d000 rwxp 00004000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
b402d000-b4030000 r-xp 00000000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
b4030000-b4031000 r-xp 00002000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
b4031000-b4032000 rwxp 00003000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
b4032000-b404b000 r-xp 00000000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
b404b000-b404c000 ---p 00019000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
b404c000-b404d000 r-xp 00019000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
b404d000-b404e000 rwxp 0001a000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
b404e000-b4050000 r-xp 00000000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
b4050000-b4051000 r-xp 00001000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
b4051000-b4052000 rwxp 00002000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
b4052000-b4054000 r-xp 00000000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
b4054000-b4055000 r-xp 00001000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
b4055000-b4056000 rwxp 00002000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
b4056000-b4060000 r-xp 00000000 08:01 6295057    /usr/lib/libpangocairo-1.0.so.0.2800.0
b4060000-b4061000 r-xp 00009000 08:01 6295057    /usr/lib/libpangocairo-1.0.so.0.2800.0
b4061000-b4062000 rwxp 0000a000 08:01 6295057    /usr/lib/libpangocairo-1.0.so.0.2800.0
b4062000-b407a000 r-xp 00000000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
b407a000-b407b000 r-xp 00017000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
b407b000-b407c000 rwxp 00018000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
b407c000-b4082000 r-xp 00000000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
b4082000-b4083000 r-xp 00005000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
b4083000-b4084000 rwxp 00006000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
b4084000-b4086000 r-xp 00000000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
b4086000-b4087000 r-xp 00001000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
b4087000-b4088000 rwxp 00002000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
b4088000-b408b000 ---p 00000000 00:00 0 
b408b000-b40d9000 rwxp 00000000 00:00 0 
b40d9000-b40dd000 r-xp 00000000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
b40dd000-b40de000 r-xp 00003000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
b40de000-b40df000 rwxp 00004000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
b40df000-b40e7000 r-xp 00000000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
b40e7000-b40e8000 r-xp 00007000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
b40e8000-b40e9000 rwxp 00008000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
b40e9000-b40f1000 r-xp 00000000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
b40f1000-b40f2000 r-xp 00007000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
b40f2000-b40f3000 rwxp 00008000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
b40f3000-b40f7000 r-xp 00000000 08:01 7736453    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20-properties.mo
b40f7000-b40f9000 r-xp 00000000 08:01 7736454    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20.mo
b40f9000-b40fa000 r-xp 00000000 08:01 6299158    /usr/lib/locale/en_GB.utf8/LC_NUMERIC
b40fa000-b40fb000 r-xp 00000000 08:01 6299161    /usr/lib/locale/en_GB.utf8/LC_TIME
b40fb000-b40fc000 r-xp 00000000 08:01 6425958    /usr/lib/locale/en_GB.utf8/LC_MONETARY
b40fc000-b40fd000 r-xp 00000000 08:01 6299162    /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b40fd000-b40fe000 r-xp 00000000 08:01 6299125    /usr/lib/locale/en_GB.utf8/LC_PAPER
b40fe000-b40ff000 r-xp 00000000 08:01 6299157    /usr/lib/locale/en_GB.utf8/LC_NAME
b40ff000-b4100000 r-xp 00000000 08:01 6425959    /usr/lib/locale/en_GB.utf8/LC_ADDRESS
b4100000-b4101000 r-xp 00000000 08:01 6425960    /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
b4101000-b4102000 r-xp 00000000 08:01 6299121    /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
b4102000-b4105000 ---p 00000000 00:00 0 
b4105000-b4153000 rwxp 00000000 00:00 0 
b4153000-b41cc000 r-xp 00000000 08:01 6301607    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libfontmanager.so
b41cc000-b41d6000 rwxp 00078000 08:01 6301607    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libfontmanager.so
b41d6000-b41db000 rwxp 00000000 00:00 0 
b41db000-b41df000 r-xp 00000000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
b41df000-b41e0000 r-xp 00003000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
b41e0000-b41e1000 rwxp 00004000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
b41e1000-b41e3000 r-xp 00000000 08:01 6294314    /usr/lib/libXau.so.6.0.0
b41e3000-b41e4000 r-xp 00001000 08:01 6294314    /usr/lib/libXau.so.6.0.0
b41e4000-b41e5000 rwxp 00002000 08:01 6294314    /usr/lib/libXau.so.6.0.0
b41e5000-b41fd000 r-xp 00000000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
b41fd000-b41fe000 r-xp 00017000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
b41fe000-b41ff000 rwxp 00018000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
b41ff000-b420b000 r-xp 00000000 08:01 6294335    /usr/lib/libXi.so.6.1.0
b420b000-b420c000 r-xp 0000c000 08:01 6294335    /usr/lib/libXi.so.6.1.0
b420c000-b420d000 rwxp 0000d000 08:01 6294335    /usr/lib/libXi.so.6.1.0
b420d000-b4211000 r-xp 00000000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
b4211000-b4212000 r-xp 00003000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
b4212000-b4213000 rwxp 00004000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
b4213000-b432c000 r-xp 00000000 08:01 6294310    /usr/lib/libX11.so.6.3.0
b432c000-b432d000 r-xp 00118000 08:01 6294310    /usr/lib/libX11.so.6.3.0
b432d000-b432f000 rwxp 00119000 08:01 6294310    /usr/lib/libX11.so.6.3.0
b432f000-b4330000 rwxp 00000000 00:00 0 
b4330000-b433e000 r-xp 00000000 08:01 6294327    /usr/lib/libXext.so.6.4.0
b433e000-b433f000 r-xp 0000d000 08:01 6294327    /usr/lib/libXext.so.6.4.0
b433f000-b4340000 rwxp 0000e000 08:01 6294327    /usr/lib/libXext.so.6.4.0
b4340000-b4341000 r-xp 00000000 08:01 6425961    /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
b4341000-b4344000 r-xs 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4344000-b434c000 r-xs 00000000 08:01 8143416    /home/ben/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b434c000-b434f000 r-xs 00000000 08:01 4587581    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b434f000-b4392000 r-xp 00000000 08:01 6301594    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/xawt/libmawt.so
b4392000-b4394000 rwxp 00043000 08:01 6301594    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/xawt/libmawt.so
b4394000-b4395000 rwxp 00000000 00:00 0 
b4395000-b4419000 r-xp 00000000 08:01 6301561    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libawt.so
b4419000-b4420000 rwxp 00084000 08:01 6301561    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libawt.so
b4420000-b4444000 rwxp 00000000 00:00 0 
b4444000-b4445000 ---p 00000000 00:00 0 
b4445000-b44c5000 rwxp 00000000 00:00 0 
b44c5000-b44c8000 ---p 00000000 00:00 0 
b44c8000-b4516000 rwxp 00000000 00:00 0 
b4516000-b4519000 ---p 00000000 00:00 0 
b4519000-b4597000 rwxp 00000000 00:00 0 
b4597000-b459a000 ---p 00000000 00:00 0 
b459a000-b45e8000 rwxp 00000000 00:00 0 
b45e8000-b45ef000 r-xs 00000000 08:01 6298079    /usr/lib/gconv/gconv-modules.cache
b45ef000-b462e000 r-xp 00000000 08:01 6422939    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b462e000-b4631000 ---p 00000000 00:00 0 
b4631000-b467f000 rwxp 00000000 00:00 0 
b467f000-b4682000 ---p 00000000 00:00 0 
b4682000-b4704000 rwxp 00000000 00:00 0 
b4704000-b489c000 r-xs 03027000 08:01 6301626    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/rt.jar
b489c000-b489d000 ---p 00000000 00:00 0 
b489d000-b4924000 rwxp 00000000 00:00 0 
b4924000-b493e000 rwxp 00000000 00:00 0 
b493e000-b49e9000 rwxp 00000000 00:00 0 
b49e9000-b4a94000 rwxp 00000000 00:00 0 
b4a94000-b4aea000 rwxp 00000000 00:00 0 
b4aea000-b4b3e000 rwxp 00000000 00:00 0 
b4b3e000-b4bea000 rwxp 00000000 00:00 0 
b4bea000-b4c94000 rwxp 00000000 00:00 0 
b4c94000-b4c9a000 rwxp 00000000 00:00 0 
b4c9a000-b4cb4000 rwxp 00000000 00:00 0 
b4cb4000-b4cce000 rwxp 00000000 00:00 0 
b4cce000-b4d40000 rwxp 00000000 00:00 0 
b4d40000-b50a0000 rwxp 00000000 00:00 0 
b50a0000-b6d40000 rwxp 00000000 00:00 0 
b6d40000-b6d4f000 r-xp 00000000 08:01 6301563    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libzip.so
b6d4f000-b6d51000 rwxp 0000e000 08:01 6301563    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libzip.so
b6d51000-b6d5b000 r-xp 00000000 08:01 8651804    /lib/tls/i686/cmov/libnss_files-2.11.1.so
b6d5b000-b6d5c000 r-xp 00009000 08:01 8651804    /lib/tls/i686/cmov/libnss_files-2.11.1.so
b6d5c000-b6d5d000 rwxp 0000a000 08:01 8651804    /lib/tls/i686/cmov/libnss_files-2.11.1.so
b6d5d000-b6d65000 r-xp 00000000 08:01 8651808    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b6d65000-b6d66000 r-xp 00007000 08:01 8651808    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b6d66000-b6d67000 rwxp 00008000 08:01 8651808    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b6d67000-b6d6d000 r-xp 00000000 08:01 8651800    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b6d6d000-b6d6e000 r-xp 00006000 08:01 8651800    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b6d6e000-b6d6f000 rwxp 00007000 08:01 8651800    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b6d6f000-b6d76000 rwxp 00000000 00:00 0 
b6d76000-b6d7e000 rwxs 00000000 08:01 262197     /tmp/hsperfdata_ben/2896
b6d7e000-b6d91000 r-xp 00000000 08:01 8651798    /lib/tls/i686/cmov/libnsl-2.11.1.so
b6d91000-b6d92000 r-xp 00012000 08:01 8651798    /lib/tls/i686/cmov/libnsl-2.11.1.so
b6d92000-b6d93000 rwxp 00013000 08:01 8651798    /lib/tls/i686/cmov/libnsl-2.11.1.so
b6d93000-b6d9b000 rwxp 00000000 00:00 0 
b6d9b000-b6da1000 r-xp 00000000 08:01 6301581    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/native_threads/libhpi.so
b6da1000-b6da2000 rwxp 00006000 08:01 6301581    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/native_threads/libhpi.so
b6da2000-b6da3000 rwxp 00000000 00:00 0 
b6da3000-b6da4000 r-xp 00000000 00:00 0 
b6da4000-b6dc7000 r-xp 00000000 08:01 6301558    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libjava.so
b6dc7000-b6dc9000 rwxp 00023000 08:01 6301558    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libjava.so
b6dc9000-b6dd0000 r-xp 00000000 08:01 8651817    /lib/tls/i686/cmov/librt-2.11.1.so
b6dd0000-b6dd1000 r-xp 00006000 08:01 8651817    /lib/tls/i686/cmov/librt-2.11.1.so
b6dd1000-b6dd2000 rwxp 00007000 08:01 8651817    /lib/tls/i686/cmov/librt-2.11.1.so
b6dd2000-b6dd5000 ---p 00000000 00:00 0 
b6dd5000-b6e23000 rwxp 00000000 00:00 0 
b6e23000-b6e47000 r-xp 00000000 08:01 8651795    /lib/tls/i686/cmov/libm-2.11.1.so
b6e47000-b6e48000 r-xp 00023000 08:01 8651795    /lib/tls/i686/cmov/libm-2.11.1.so
b6e48000-b6e49000 rwxp 00024000 08:01 8651795    /lib/tls/i686/cmov/libm-2.11.1.so
b6e49000-b730b000 r-xp 00000000 08:01 6301574    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/client/libjvm.so
b730b000-b732e000 rwxp 004c2000 08:01 6301574    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/client/libjvm.so
b732e000-b774c000 rwxp 00000000 00:00 0 
b774c000-b789f000 r-xp 00000000 08:01 8651787    /lib/tls/i686/cmov/libc-2.11.1.so
b789f000-b78a0000 ---p 00153000 08:01 8651787    /lib/tls/i686/cmov/libc-2.11.1.so
b78a0000-b78a2000 r-xp 00153000 08:01 8651787    /lib/tls/i686/cmov/libc-2.11.1.so
b78a2000-b78a3000 rwxp 00155000 08:01 8651787    /lib/tls/i686/cmov/libc-2.11.1.so
b78a3000-b78a6000 rwxp 00000000 00:00 0 
b78a6000-b78a8000 r-xp 00000000 08:01 8651793    /lib/tls/i686/cmov/libdl-2.11.1.so
b78a8000-b78a9000 r-xp 00001000 08:01 8651793    /lib/tls/i686/cmov/libdl-2.11.1.so
b78a9000-b78aa000 rwxp 00002000 08:01 8651793    /lib/tls/i686/cmov/libdl-2.11.1.so
b78aa000-b78b1000 r-xp 00000000 08:01 6301567    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/jli/libjli.so
b78b1000-b78b3000 rwxp 00006000 08:01 6301567    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/jli/libjli.so
b78b3000-b78c8000 r-xp 00000000 08:01 8651813    /lib/tls/i686/cmov/libpthread-2.11.1.so
b78c8000-b78c9000 r-xp 00014000 08:01 8651813    /lib/tls/i686/cmov/libpthread-2.11.1.so
b78c9000-b78ca000 rwxp 00015000 08:01 8651813    /lib/tls/i686/cmov/libpthread-2.11.1.so
b78ca000-b78cc000 rwxp 00000000 00:00 0 
b78cc000-b78cd000 r-xs 00000000 08:01 4587573    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b78cd000-b78cf000 r-xs 00014000 08:11 18         /media/Backup/minecraft.jar
b78cf000-b78da000 r-xp 00000000 08:01 6301592    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libverify.so
b78da000-b78db000 rwxp 0000b000 08:01 6301592    /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libverify.so
b78db000-b78dd000 rwxp 00000000 00:00 0 
b78dd000-b78de000 r-xp 00000000 00:00 0          [vdso]
b78de000-b78f9000 r-xp 00000000 08:01 8519705    /lib/ld-2.11.1.so
b78f9000-b78fa000 r-xp 0001a000 08:01 8519705    /lib/ld-2.11.1.so
b78fa000-b78fb000 rwxp 0001b000 08:01 8519705    /lib/ld-2.11.1.so
bfbeb000-bfc00000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xmx1024M -Xms512M 
java_command: net.minecraft.LauncherFrame
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=ben
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.24/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x452e10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x452e10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x374120], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x374120], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x374120], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x377100], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x376ce0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x376ce0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x376ce0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x376ce0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:2.38 1.89 2.04

/proc/meminfo:
MemTotal:        2061712 kB
MemFree:          596028 kB
Buffers:           84844 kB
Cached:           812244 kB
SwapCached:            0 kB
Active:           852680 kB
Inactive:         488604 kB
Active(anon):     454040 kB
Inactive(anon):       16 kB
Active(file):     398640 kB
Inactive(file):   488588 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       1187784 kB
HighFree:           1736 kB
LowTotal:         873928 kB
LowFree:          594292 kB
SwapTotal:       6036472 kB
SwapFree:        6036472 kB
Dirty:               424 kB
Writeback:             0 kB
AnonPages:        444256 kB
Mapped:            90012 kB
Shmem:              9816 kB
Slab:              42092 kB
SReclaimable:      30608 kB
SUnreclaim:        11484 kB
KernelStack:        2000 kB
PageTables:         4884 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7067328 kB
Committed_AS:    1369832 kB
VmallocTotal:     122880 kB
VmallocUsed:       19872 kB
VmallocChunk:      97276 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       94200 kB
DirectMap4M:      815104 kB


CPU:total 1 (1 cores per cpu, 1 threads per core) family 6 model 10 stepping 0, cmov, cx8, fxsr, mmx, sse, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 2061712k(596028k free), swap 6036472k(6036472k free)

vm_info: Java HotSpot(TM) Client VM (19.1-b02) for linux-x86 JRE (1.6.0_24-b07), built on Feb  2 2011 17:10:45 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Mon Mar  7 13:14:51 2011
elapsed time: 153 seconds

```Any help appreciated, i have already tried removing/reinstalling Java, i have tried on both Java JDK and JRE and nothing works ..

Thanks in advance.

EDIT: Fixed typo.

---

### Post by clooless001 on 2011-03-07
Also, any other game based in java freezes or whitescreens ... Not as fast as minecraft closes but, eventually...

Please help :C

---

### Post by Kirboosy on 2011-03-07
Thats really strange. Have you tried purging Java and reinstalling it? (yes purging is a little different than uninstalling Java. Purging removes everything)

---

### Post by clooless001 on 2011-03-07
I have tried purging, i have purged both the JDK and the JRE separately and together ..

Thanks for any help you can give :)

---

### Post by Kirboosy on 2011-03-07
What command are you using to run the .jar?

---

### Post by clooless001 on 2011-03-07
```
 #!/bin/bash
killall ibus-daemon
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
ibus-daemon --xim &
disown
```as a text file and "Run" it (Executable text file, I remembered!)

EDIT: I've also tried right clicking "minecraft.Jar" and selecting "Open with Sun Java 6 Runtime" which also causes it to crash eventually...

---

### Post by Kirboosy on 2011-03-07
Try running this in a terminal...
```
java -jar /path/to/minecraft.jar
```In my case it would be
```
java -jar /home/caboose885/Downloads/minecraft.jar
```

---

### Post by clooless001 on 2011-03-07
```
 ben@ben-desktop:~$ java -jar /media/Backup/minecraft.jar
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    ... 1 more
28
Setting user: TehPwnMonster, -7703164929612705322
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

INSTANCE.absAxesIDs is only 63 long, so 63 not contained
Linux plugin claims to have found 1 controllers
143 recipes
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGILL (0x4) at pc=0x0171cdde, pid=3938, tid=3027573616
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Client VM (19.0-b09 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.7-0ubuntu1~10.04.1
# Problematic frame:
# V  [libjvm.so+0x75edde]
#
# An error report file with more information is saved as:
# /home/ben/hs_err_pid3938.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted

```

As we speak i am attempting to install a windows version of java to run through wine, see if it works like that...

---

### Post by Kirboosy on 2011-03-07
Ok. Backup your minecraft world data (/home/clooless001/.minecraft/worlds is where its stored) Then once you have everything backed up delete the .minecraft folder and delete the minecraft.jar file. 

Download the .jar file and see what happens.

---

### Post by clooless001 on 2011-03-07
How shall i run it? With my executable text file, or with the previous command?

---

### Post by Kirboosy on 2011-03-07
Try my way first but if that doesn't work by all means try your way.

I'm not even sure if it will fix anything but its worth a shot.

---

### Post by clooless001 on 2011-03-07
```
ben@ben-desktop:~$ java -jar /media/Backup/minecraft.jar
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    ... 1 more
28
Setting user: TehPwnMonster, 1471542751443432294
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

INSTANCE.absAxesIDs is only 63 long, so 63 not contained
Linux plugin claims to have found 1 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

143 recipes
java.lang.NullPointerException
    at bb.a(SourceFile:44)
    at al.a(SourceFile:80)
    at al.a(SourceFile:28)
    at pd.a(SourceFile:119)
    at df.a(SourceFile:52)
    at cn.b(SourceFile:93)
    at mh.c(SourceFile:574)
    at mh.b(SourceFile:487)
    at net.minecraft.client.Minecraft.run(SourceFile:694)
    at java.lang.Thread.run(Thread.java:636)
Stopping!

```

Then i just get a black screen.... :S

---

### Post by clooless001 on 2011-03-07
Using my executable text file also causes my game to freeze and the screen to go black...

Running 
```
 java -Xmx1024M -Xms512M -cp /media/Backup/minecraft.jar net.minecraft.LauncherFrame 
```

(As suggested on the Minecraft website)
Also gives me:
```
 ben@ben-desktop:~$ java -Xmx1024M -Xms512M -cp /media/Backup/minecraft.jar net.minecraft.LauncherFrame
28
Setting user: TehPwnMonster, -3960712795435370067
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

INSTANCE.absAxesIDs is only 63 long, so 63 not contained
Linux plugin claims to have found 1 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

143 recipes
java.lang.NullPointerException
    at bb.a(SourceFile:44)
    at al.a(SourceFile:80)
    at al.a(SourceFile:28)
    at pd.a(SourceFile:119)
    at df.a(SourceFile:52)
    at cn.b(SourceFile:93)
    at mh.c(SourceFile:574)
    at mh.b(SourceFile:487)
    at net.minecraft.client.Minecraft.run(SourceFile:694)
    at java.lang.Thread.run(Thread.java:636)
Stopping!


``` and a black screen...

---

### Post by Kirboosy on 2011-03-07
I honestly have no idea why thats happening. I thought purging java and rebooting would fix it easily but I guess I was wrong.


Did you recently download an update for java?

---

### Post by clooless001 on 2011-03-08
Nope, I only just installed it onto this hard drive...

---

### Post by clooless001 on 2011-03-08
I hope there is someone out there who can help :(

---

### Post by clooless001 on 2011-03-10
Bump

Still have the problem, massively frustrating!

---

### Post by clooless001 on 2011-03-11
This will be my last post as no-one is replying.
I have found some error logs in my home folder from when Java has crashed whilst running Runescape.
As you can see, each log has a different "Problematic frame" and the run time can vary greatly (Found at the bottom of each log)
I would greatly appreciate any help.

P.S. I will be posting logs separately, posting 4 logs makes my Firefox freeze somewhat ridiculous.

```
 #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x001849c1, pid=7321, tid=3027327856
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Client VM (19.0-b09 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.7-0ubuntu1~10.04.1
# Problematic frame:
# C  [libc.so.6+0x749c1]
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x091c4c00):  JavaThread "Minecraft main thread" daemon [_thread_in_native, id=7351, stack(0xb46c5000,0xb4716000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000000

Registers:
EAX=0x00000000, EBX=0x019cfff4, ECX=0x00000010, EDX=0x00000000
ESP=0xb4714548, EBP=0xb4714568, ESI=0x08e9cd00, EDI=0xb471467c
EIP=0x001849c1, CR2=0x00000000, EFLAGS=0x00210246

Register to memory mapping:

EAX=0x00000000
0x00000000 is pointing to unknown location

EBX=0x019cfff4
0x019cfff4: <offset 0x26cff4> in /usr/lib/dri/r300_dri.so at 0x01763000

ECX=0x00000010
0x00000010 is pointing to unknown location

EDX=0x00000000
0x00000000 is pointing to unknown location

ESP=0xb4714548
0xb4714548 is pointing into the stack for thread: 0x091c4c00
"Minecraft main thread" daemon prio=10 tid=0x091c4c00 nid=0x1cb7 runnable [0xb4714000]
   java.lang.Thread.State: RUNNABLE

EBP=0xb4714568
0xb4714568 is pointing into the stack for thread: 0x091c4c00
"Minecraft main thread" daemon prio=10 tid=0x091c4c00 nid=0x1cb7 runnable [0xb4714000]
   java.lang.Thread.State: RUNNABLE

ESI=0x08e9cd00
0x08e9cd00 is pointing to unknown location

EDI=0xb471467c
0xb471467c is pointing into the stack for thread: 0x091c4c00
"Minecraft main thread" daemon prio=10 tid=0x091c4c00 nid=0x1cb7 runnable [0xb4714000]
   java.lang.Thread.State: RUNNABLE


Top of Stack: (sp=0xb4714548)
0xb4714548:   0c533be0 01800e6c b471467c 00000000
0xb4714558:   00000040 00b58bad 08e13780 019cfff4
0xb4714568:   b47146d8 017a1248 b471467c 00000040
0xb4714578:   b4714598 0181aefc 00000020 00000006
0xb4714588:   b4714628 019cfff4 08e9cd00 b471467c
0xb4714598:   b47146d8 08e13780 09134698 b47145fc
0xb47145a8:   00000010 00b59950 0910fab8 00000003
0xb47145b8:   0196fe00 00b5888a 0000013e 0196f859 

Instructions: (pc=0x001849c1)
0x001849b1:   1b 83 f2 01 75 02 aa 49 89 ca c1 e9 02 83 e2 03
0x001849c1:   69 c0 01 01 01 01 f3 ab 89 d1 f3 aa 8b 44 24 08 

Stack: [0xb46c5000,0xb4716000],  sp=0xb4714548,  free space=317k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libc.so.6+0x749c1]
C  [r300_dri.so+0x3e248]  r300SelectAndTranslateFragmentShader+0x48
C  [r300_dri.so+0x3a6c5]  r300UpdateShaders+0x35
C  [r300_dri.so+0x2be8d]
C  [r300_dri.so+0xdc761]
C  [r300_dri.so+0xd3447]
C  [liblwjgl.so+0x4556d]  Java_org_lwjgl_opengl_GL11_nglDrawArrays+0x1d
J  org.lwjgl.opengl.GL11.nglDrawArrays(IIIJ)V
J  kv.a()V
j  mh.b(F)V+286
j  net.minecraft.client.Minecraft.run()V+357
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub
V  [libjvm.so+0x209a92]
V  [libjvm.so+0x30a609]
V  [libjvm.so+0x2089cf]
V  [libjvm.so+0x20951a]
V  [libjvm.so+0x209678]
V  [libjvm.so+0x253e41]
V  [libjvm.so+0x3bb43c]
V  [libjvm.so+0x3bb502]
V  [libjvm.so+0x311051]
C  [libpthread.so.0+0x596e]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
J  org.lwjgl.opengl.GL11.nglDrawArrays(IIIJ)V
J  kv.a()V
J  bw.a(Lqk;I)V
J  al.a(Lfs;DDDFF)V
J  al.a(Lom;DDDFF)V
J  pd.a(Lom;DDDFF)V
J  pd.a(Lom;F)V
J  h.a(Lay;Ltl;F)V
j  mh.c(F)V+421
j  mh.b(F)V+286
j  net.minecraft.client.Minecraft.run()V+357
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x095b5000 JavaThread "Thread-9" daemon [_thread_blocked, id=7354, stack(0xb4acc000,0xb4b1d000)]
=>0x091c4c00 JavaThread "Minecraft main thread" daemon [_thread_in_native, id=7351, stack(0xb46c5000,0xb4716000)]
  0x091bd000 JavaThread "Timer hack thread" daemon [_thread_blocked, id=7350, stack(0xb4674000,0xb46c5000)]
  0x08d7b000 JavaThread "DestroyJavaVM" [_thread_blocked, id=7322, stack(0xb7721000,0xb7772000)]
  0x0908cc00 JavaThread "TimerQueue" daemon [_thread_blocked, id=7344, stack(0xb4b1d000,0xb4b6e000)]
  0x08fc5c00 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=7340, stack(0xb4b75000,0xb4bc6000)]
  0x08fc5400 JavaThread "AWT-Shutdown" [_thread_blocked, id=7339, stack(0xb4e2e000,0xb4e7f000)]
  0x08ebdc00 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=7333, stack(0xb4e7f000,0xb4ed0000)]
  0x08e6f400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=7332, stack(0xb4f66000,0xb4fb7000)]
  0x08db7000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=7328, stack(0xb5047000,0xb5098000)]
  0x08db5000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=7327, stack(0xb5098000,0xb5119000)]
  0x08db3800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=7326, stack(0xb5119000,0xb516a000)]
  0x08dab800 JavaThread "Finalizer" daemon [_thread_blocked, id=7325, stack(0xb51b0000,0xb5201000)]
  0x08daa000 JavaThread "Reference Handler" daemon [_thread_blocked, id=7324, stack(0xb5201000,0xb5252000)]

Other Threads:
  0x08da8400 VMThread [stack: 0xb5252000,0xb52d3000] [id=7323]
  0x08dc3000 WatcherThread [stack: 0xb4fc6000,0xb5047000] [id=7329]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 30272K, used 3578K [0x6f940000, 0x71a10000, 0x7a3e0000)
  eden space 26944K,   1% used [0x6f940000, 0x6f9c16d8, 0x71390000)
  from space 3328K,  91% used [0x716d0000, 0x719cd2c0, 0x71a10000)
  to   space 3328K,   0% used [0x71390000, 0x71390000, 0x716d0000)
 tenured generation   total 67096K, used 52308K [0x7a3e0000, 0x7e566000, 0x8f940000)
   the space 67096K,  77% used [0x7a3e0000, 0x7d6f5328, 0x7d6f5400, 0x7e566000)
 compacting perm gen  total 12288K, used 8521K [0x8f940000, 0x90540000, 0x93940000)
   the space 12288K,  69% used [0x8f940000, 0x90192600, 0x90192600, 0x90540000)
    ro space 10240K,  73% used [0x93940000, 0x94098710, 0x94098800, 0x94340000)
    rw space 12288K,  60% used [0x94340000, 0x94a80f20, 0x94a81000, 0x94f40000)

Dynamic libraries:
00110000-00263000 r-xp 00000000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00263000-00264000 ---p 00153000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00264000-00266000 r--p 00153000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00266000-00267000 rw-p 00155000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00267000-0026a000 rw-p 00000000 00:00 0 
0026a000-0028e000 r-xp 00000000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
0028e000-0028f000 r--p 00023000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
0028f000-00290000 rw-p 00024000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
00290000-002b4000 r-xp 00000000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
002b4000-002b5000 r--p 00023000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
002b5000-002b7000 rw-p 00024000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
002b7000-002be000 r-xp 00000000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
002be000-002bf000 r--p 00006000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
002bf000-002c0000 rw-p 00007000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
002c0000-002c7000 r-xp 00000000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
002c7000-002c8000 r--p 00006000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
002c8000-002c9000 rw-p 00007000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
002c9000-002d1000 r-xp 00000000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
002d1000-002d2000 r--p 00007000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
002d2000-002d3000 rw-p 00008000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
002d3000-002d7000 r-xp 00000000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
002d7000-002d8000 r--p 00003000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
002d8000-002d9000 rw-p 00004000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
002d9000-002e5000 r-xp 00000000 08:01 6294335    /usr/lib/libXi.so.6.1.0
002e5000-002e6000 r--p 0000c000 08:01 6294335    /usr/lib/libXi.so.6.1.0
002e6000-002e7000 rw-p 0000d000 08:01 6294335    /usr/lib/libXi.so.6.1.0
002e7000-002ff000 r-xp 00000000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
002ff000-00300000 r--p 00017000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00300000-00301000 rw-p 00018000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00301000-00303000 r-xp 00000000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00303000-00304000 r--p 00001000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00304000-00305000 rw-p 00002000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00305000-00309000 r-xp 00000000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
00309000-0030a000 r--p 00003000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
0030a000-0030b000 rw-p 00004000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
0030b000-00328000 r-xp 00000000 08:01 8519763    /lib/libgcc_s.so.1
00328000-00329000 r--p 0001c000 08:01 8519763    /lib/libgcc_s.so.1
00329000-0032a000 rw-p 0001d000 08:01 8519763    /lib/libgcc_s.so.1
0032a000-00332000 r-xp 00000000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00332000-00333000 r--p 00007000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00333000-00334000 rw-p 00008000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00334000-00336000 r-xp 00000000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
00336000-00337000 r--p 00001000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
00337000-00338000 rw-p 00002000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
00338000-0033e000 r-xp 00000000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
0033e000-0033f000 r--p 00005000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
0033f000-00340000 rw-p 00006000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
00340000-00342000 r-xp 00000000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
00342000-00343000 r--p 00001000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
00343000-00344000 rw-p 00002000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
00344000-00346000 r-xp 00000000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
00346000-00347000 r--p 00001000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
00347000-00348000 rw-p 00002000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
00349000-00355000 r-xp 00000000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00355000-00356000 r--p 0000b000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00356000-00357000 rw-p 0000c000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00357000-00470000 r-xp 00000000 08:01 6294310    /usr/lib/libX11.so.6.3.0
00470000-00471000 r--p 00118000 08:01 6294310    /usr/lib/libX11.so.6.3.0
00471000-00473000 rw-p 00119000 08:01 6294310    /usr/lib/libX11.so.6.3.0
00473000-00474000 rw-p 00000000 00:00 0 
00474000-004e5000 r-xp 00000000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
004e5000-004e9000 r--p 00070000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
004e9000-004ea000 rw-p 00074000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
004ea000-0057d000 r-xp 00000000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
0057d000-0057f000 r--p 00093000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
0057f000-00580000 rw-p 00095000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
00580000-00598000 r-xp 00000000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00598000-00599000 r--p 00017000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00599000-0059a000 rw-p 00018000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
0059a000-005a4000 r-xp 00000000 08:01 6292566    /usr/lib/libpangocairo-1.0.so.0.2800.0
005a4000-005a5000 r--p 00009000 08:01 6292566    /usr/lib/libpangocairo-1.0.so.0.2800.0
005a5000-005a6000 rw-p 0000a000 08:01 6292566    /usr/lib/libpangocairo-1.0.so.0.2800.0
005a6000-005bf000 r-xp 00000000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
005bf000-005c0000 ---p 00019000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
005c0000-005c1000 r--p 00019000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
005c1000-005c2000 rw-p 0001a000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
005c2000-005c5000 r-xp 00000000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
005c5000-005c6000 r--p 00002000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
005c6000-005c7000 rw-p 00003000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
005c7000-005cb000 r-xp 00000000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
005cb000-005cc000 r--p 00003000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
005cc000-005cd000 rw-p 00004000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
005cd000-005d5000 r-xp 00000000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
005d5000-005d6000 r--p 00007000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
005d6000-005d7000 rw-p 00008000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
005d7000-005da000 r-xp 00000000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
005da000-005db000 r--p 00002000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
005db000-005dc000 rw-p 00003000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
005dc000-005e4000 r-xp 00000000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
005e4000-005e5000 r--p 00007000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
005e5000-005e6000 rw-p 00008000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
005e6000-0065d000 r-xp 00000000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
0065d000-0065f000 r--p 00076000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
0065f000-00660000 rw-p 00078000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
00660000-00685000 r-xp 00000000 08:01 6293458    /usr/lib/libpangoft2-1.0.so.0.2800.0
00685000-00686000 r--p 00024000 08:01 6293458    /usr/lib/libpangoft2-1.0.so.0.2800.0
00686000-00687000 rw-p 00025000 08:01 6293458    /usr/lib/libpangoft2-1.0.so.0.2800.0
00687000-0068a000 r-xp 00000000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
0068a000-0068b000 r--p 00003000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
0068b000-0068c000 rw-p 00004000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
0068c000-00711000 r-xp 00000000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00711000-00712000 r--p 00084000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00712000-00718000 rw-p 00085000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00718000-0073d000 rw-p 00000000 00:00 0 
0073d000-00743000 r-xp 00000000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
00743000-00744000 r--p 00005000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
00744000-00745000 rw-p 00006000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
00745000-00747000 r-xp 00000000 08:01 6293464    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00747000-00748000 r--p 00001000 08:01 6293464    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00748000-00749000 rw-p 00002000 08:01 6293464    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
0074b000-0075e000 r-xp 00000000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
0075e000-0075f000 r--p 00012000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
0075f000-00760000 rw-p 00013000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00760000-00762000 rw-p 00000000 00:00 0 
00762000-007a2000 r-xp 00000000 08:01 6292277    /usr/lib/libpango-1.0.so.0.2800.0
007a2000-007a3000 ---p 00040000 08:01 6292277    /usr/lib/libpango-1.0.so.0.2800.0
007a3000-007a4000 r--p 00040000 08:01 6292277    /usr/lib/libpango-1.0.so.0.2800.0
007a4000-007a5000 rw-p 00041000 08:01 6292277    /usr/lib/libpango-1.0.so.0.2800.0
007a5000-007d3000 r-xp 00000000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
007d3000-007d4000 r--p 0002d000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
007d4000-007d5000 rw-p 0002e000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
007d5000-007d9000 r-xp 00000000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
007d9000-007da000 ---p 00004000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
007da000-007db000 r--p 00004000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
007db000-007dc000 rw-p 00005000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
007dc000-007e3000 r-xp 00000000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
007e3000-007e4000 r--p 00006000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
007e4000-007e5000 rw-p 00007000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
007e7000-007e8000 r-xp 00000000 00:00 0          [vdso]
007e8000-00825000 r-xp 00000000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
00825000-00826000 r--p 0003c000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
00826000-00827000 rw-p 0003d000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
00827000-0083b000 r-xp 00000000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
0083b000-0083c000 r--p 00013000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
0083c000-0083d000 rw-p 00014000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
0083d000-0084d000 r-xp 00000000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
0084d000-0084e000 r--p 00010000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
0084e000-0084f000 rw-p 00011000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
0084f000-00851000 rw-p 00000000 00:00 0 
00851000-00856000 r-xp 00000000 08:01 6295038    /usr/lib/libogg.so.0.6.0
00856000-00857000 r--p 00004000 08:01 6295038    /usr/lib/libogg.so.0.6.0
00857000-00858000 rw-p 00005000 08:01 6295038    /usr/lib/libogg.so.0.6.0
00858000-00859000 r-xp 00000000 08:01 6299066    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00859000-0085a000 r--p 00000000 08:01 6299066    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
0085a000-0085b000 rw-p 00001000 08:01 6299066    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
0085b000-00861000 r-xp 00000000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00861000-00862000 r--p 00006000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00862000-00863000 rw-p 00007000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00863000-00886000 r-xp 00000000 08:01 8519833    /lib/libpng12.so.0.42.0
00886000-00887000 r--p 00022000 08:01 8519833    /lib/libpng12.so.0.42.0
00887000-00888000 rw-p 00023000 08:01 8519833    /lib/libpng12.so.0.42.0
00888000-008a1000 r-xp 00000000 08:01 8519845    /lib/libselinux.so.1
008a1000-008a2000 r--p 00018000 08:01 8519845    /lib/libselinux.so.1
008a2000-008a3000 rw-p 00019000 08:01 8519845    /lib/libselinux.so.1
008a3000-008b0000 r-xp 00000000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
008b0000-008b1000 r--p 0000c000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
008b1000-008b2000 rw-p 0000d000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
008b2000-008b5000 r-xp 00000000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
008b5000-008b6000 r--p 00003000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
008b6000-008b7000 rw-p 00004000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
008b7000-0090e000 r-xp 00000000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
0090e000-00910000 r--p 00057000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
00910000-00911000 rw-p 00059000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
00911000-00935000 r-xp 00000000 08:01 8519756    /lib/libexpat.so.1.5.2
00935000-00937000 r--p 00024000 08:01 8519756    /lib/libexpat.so.1.5.2
00937000-00938000 rw-p 00026000 08:01 8519756    /lib/libexpat.so.1.5.2
00938000-0093f000 r-xp 00000000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
0093f000-00940000 r--p 00006000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
00940000-00941000 rw-p 00007000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
00941000-00985000 r-xp 00000000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00985000-00987000 r--p 00043000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00987000-00988000 rw-p 00045000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00988000-0098d000 rw-p 00000000 00:00 0 
0098d000-0099b000 r-xp 00000000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
0099b000-0099c000 r--p 0000d000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
0099c000-0099d000 rw-p 0000e000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
0099d000-009a4000 r-xp 00000000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
009a4000-009a5000 r--p 00006000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
009a5000-009a6000 rw-p 00007000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
009a6000-009ab000 r-xp 00000000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
009ab000-009ac000 r--p 00004000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
009ac000-009ad000 rw-p 00005000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
009af000-009ca000 r-xp 00000000 08:01 8519683    /lib/ld-2.11.1.so
009ca000-009cb000 r--p 0001a000 08:01 8519683    /lib/ld-2.11.1.so
009cb000-009cc000 rw-p 0001b000 08:01 8519683    /lib/ld-2.11.1.so
009cc000-009fb000 r-xp 00000000 08:01 8519821    /lib/libpcre.so.3.12.1
009fb000-009fc000 r--p 0002e000 08:01 8519821    /lib/libpcre.so.3.12.1
009fc000-009fd000 rw-p 0002f000 08:01 8519821    /lib/libpcre.so.3.12.1
009fd000-009ff000 r-xp 00000000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
009ff000-00a00000 r--p 00001000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
00a00000-00a01000 rw-p 00002000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
00a01000-00a0b000 r-xp 00000000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00a0b000-00a0c000 r--p 00009000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00a0c000-00a0d000 rw-p 0000a000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00a0d000-00a34000 r-xp 00000000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00a34000-00a35000 r--p 00026000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00a35000-00a36000 rw-p 00027000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00a36000-00a5c000 r-xp 00000000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
00a5c000-00a5d000 r--p 00025000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
00a5d000-00a5e000 rw-p 00026000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
00a5e000-00a72000 r-xp 00000000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00a72000-00a73000 r--p 00013000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00a73000-00a74000 rw-p 00014000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00a74000-00a78000 r-xp 00000000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00a78000-00a79000 r--p 00004000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00a79000-00a7a000 rw-p 00005000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00a7a000-00a7c000 r-xp 00000000 08:01 6291780    /usr/lib/libplds4.so
00a7c000-00a7d000 r--p 00001000 08:01 6291780    /usr/lib/libplds4.so
00a7d000-00a7e000 rw-p 00002000 08:01 6291780    /usr/lib/libplds4.so
00a7e000-00a8c000 r-xp 00000000 08:01 6294327    /usr/lib/libXext.so.6.4.0
00a8c000-00a8d000 r--p 0000d000 08:01 6294327    /usr/lib/libXext.so.6.4.0
00a8d000-00a8e000 rw-p 0000e000 08:01 6294327    /usr/lib/libXext.so.6.4.0
00a8e000-00b28000 r-xp 00000000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
00b28000-00b29000 ---p 0009a000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
00b29000-00b2a000 r--p 0009a000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
00b2a000-00b2b000 rw-p 0009b000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
00b2b000-00b2c000 rw-p 00000000 00:00 0 
00b2c000-00b50000 r-xp 00000000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
00b50000-00b51000 r--p 00023000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
00b51000-00b52000 rw-p 00024000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
00b52000-00b55000 r-xp 00000000 08:01 6291779    /usr/lib/libplc4.so
00b55000-00b56000 r--p 00002000 08:01 6291779    /usr/lib/libplc4.so
00b56000-00b57000 rw-p 00003000 08:01 6291779    /usr/lib/libplc4.so
00b57000-00b5a000 r-xp 00000000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
00b5a000-00b5b000 r--p 00002000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
00b5b000-00b5c000 rw-p 00003000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
00b5c000-00b71000 r-xp 00000000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
00b71000-00b72000 r--p 00014000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
00b72000-00b73000 rw-p 00015000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
00b73000-00b75000 rw-p 00000000 00:00 0 
00b75000-00bae000 r-xp 00000000 08:01 6294870    /usr/lib/libibus.so.1.0.0
00bae000-00baf000 r--p 00039000 08:01 6294870    /usr/lib/libibus.so.1.0.0
00baf000-00bb0000 rw-p 0003a000 08:01 6294870    /usr/lib/libibus.so.1.0.0
00bb3000-00bb7000 r-xp 00000000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
00bb7000-00bb8000 r--p 00003000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
00bb8000-00bb9000 rw-p 00004000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
00bb9000-00bfe000 r-xp 00000000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00bfe000-00bff000 r--p 00044000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00bff000-00c01000 rw-p 00045000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00c01000-00c02000 rw-p 00000000 00:00 0 
00c02000-00c06000 r-xp 00000000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
00c06000-00c07000 r--p 00003000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
00c07000-00c08000 rw-p 00004000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
00c0b000-00c0d000 r-xp 00000000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00c0d000-00c0e000 r--p 00001000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00c0e000-00c0f000 rw-p 00002000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00c11000-00c18000 r-xp 00000000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
00c18000-00c19000 r--p 00006000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
00c19000-00c1a000 rw-p 00007000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
00c1a000-00c2e000 r-xp 00000000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
00c2e000-00c2f000 r--p 00013000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
00c2f000-00c30000 rw-p 00014000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
00c33000-00c46000 r-xp 00000000 08:01 8519878    /lib/libz.so.1.2.3.3
00c46000-00c47000 r--p 00012000 08:01 8519878    /lib/libz.so.1.2.3.3
00c47000-00c48000 rw-p 00013000 08:01 8519878    /lib/libz.so.1.2.3.3
00c48000-0109b000 r-xp 00000000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0109b000-0109c000 ---p 00453000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0109c000-010b3000 r--p 00453000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
010b3000-010c0000 rw-p 0046a000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
010c0000-014dc000 rw-p 00000000 00:00 0 
014dc000-014ed000 r-xp 00000000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
014ed000-014ee000 r--p 00011000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
014ee000-014ef000 rw-p 00012000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
015d8000-0164b000 r-xp 00000000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
0164b000-0164c000 ---p 00073000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
0164c000-0164d000 r--p 00073000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
0164d000-0164e000 rw-p 00074000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
0164e000-0164f000 rw-p 00000000 00:00 0 
0164f000-0175d000 r-xp 00000000 08:01 6296556    /usr/lib/libnss3.so
0175d000-0175e000 ---p 0010e000 08:01 6296556    /usr/lib/libnss3.so
0175e000-01761000 r--p 0010e000 08:01 6296556    /usr/lib/libnss3.so
01761000-01763000 rw-p 00111000 08:01 6296556    /usr/lib/libnss3.so
01763000-019cc000 r-xp 00000000 08:01 6296477    /usr/lib/dri/r300_dri.so
019cc000-019d0000 r--p 00269000 08:01 6296477    /usr/lib/dri/r300_dri.so
019d0000-019d2000 rw-p 0026d000 08:01 6296477    /usr/lib/dri/r300_dri.so
019d2000-019e1000 rw-p 00000000 00:00 0 
01a6b000-01ab3000 r-xp 00000000 08:01 6295024    /usr/lib/nss/libfreebl3.so
01ab3000-01ab4000 r--p 00047000 08:01 6295024    /usr/lib/nss/libfreebl3.so
01ab4000-01ab5000 rw-p 00048000 08:01 6295024    /usr/lib/nss/libfreebl3.so
01ab5000-01ab9000 rw-p 00000000 00:00 0 
02392000-023a0000 r-xp 00000000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
023a0000-023a1000 r--p 0000d000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
023a1000-023a2000 rw-p 0000e000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
028b1000-028e6000 r-xp 00000000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
028e6000-028e7000 r--p 00035000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
028e7000-028e8000 rw-p 00036000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
02c2b000-02c2e000 r-xp 00000000 08:01 8142926    /home/ben/.minecraft/bin/natives/libjinput-linux.so
02c2e000-02c2f000 r--p 00002000 08:01 8142926    /home/ben/.minecraft/bin/natives/libjinput-linux.so
02c2f000-02c30000 rw-p 00003000 08:01 8142926    /home/ben/.minecraft/bin/natives/libjinput-linux.so
02fb9000-02ff0000 r-xp 00000000 08:01 8519733    /lib/libdbus-1.so.3.4.0
02ff0000-02ff1000 r--p 00036000 08:01 8519733    /lib/libdbus-1.so.3.4.0
02ff1000-02ff2000 rw-p 00037000 08:01 8519733    /lib/libdbus-1.so.3.4.0
03384000-03399000 r-xp 00000000 08:01 6296555    /usr/lib/libnssutil3.so
03399000-0339c000 r--p 00014000 08:01 6296555    /usr/lib/libnssutil3.so
0339c000-0339d000 rw-p 00017000 08:01 6296555    /usr/lib/libnssutil3.so
048c4000-0498c000 r-xp 00000000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
0498c000-0498d000 r--p 000c7000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
0498d000-0498e000 rw-p 000c8000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
04c20000-04c7a000 r-xp 00000000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
04c7a000-04c7f000 r--p 00059000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
04c7f000-04c84000 rwxp 0005e000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
04c84000-04c85000 rwxp 00000000 00:00 0 
05200000-05209000 r-xp 00000000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
05209000-0520a000 r--p 00008000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
0520a000-0520b000 rw-p 00009000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
0571e000-05aeb000 r-xp 00000000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
05aeb000-05aef000 r--p 003cd000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
05aef000-05af1000 rw-p 003d1000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
05af1000-05af3000 rw-p 00000000 00:00 0 
062c1000-062ca000 r-xp 00000000 08:01 8519746    /lib/libdrm.so.2.4.0
062ca000-062cb000 r--p 00008000 08:01 8519746    /lib/libdrm.so.2.4.0
062cb000-062cc000 rw-p 00009000 08:01 8519746    /lib/libdrm.so.2.4.0
06896000-068c7000 r-xp 00000000 08:01 6291778    /usr/lib/libnspr4.so
068c7000-068c8000 r--p 00030000 08:01 6291778    /usr/lib/libnspr4.so
068c8000-068c9000 rw-p 00031000 08:01 6291778    /usr/lib/libnspr4.so
068c9000-068cb000 rw-p 00000000 00:00 0 
069d2000-069dc000 r-xp 00000000 08:01 8519740    /lib/libudev.so.0.6.1
069dc000-069dd000 r--p 00009000 08:01 8519740    /lib/libudev.so.0.6.1
069dd000-069de000 rw-p 0000a000 08:01 8519740    /lib/libudev.so.0.6.1
071a9000-071d7000 r-xp 00000000 08:01 6299071    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
071d7000-071d8000 r--p 0002d000 08:01 6299071    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
071d8000-071d9000 rw-p 0002e000 08:01 6299071    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
071d9000-071db000 rw-p 00000000 00:00 0 
07384000-073db000 r-xp 00000000 08:01 8142931    /home/ben/.minecraft/bin/natives/liblwjgl.so
073db000-073dc000 r--p 00056000 08:01 8142931    /home/ben/.minecraft/bin/natives/liblwjgl.so
073dc000-073dd000 rw-p 00057000 08:01 8142931    /home/ben/.minecraft/bin/natives/liblwjgl.so
08048000-08051000 r-xp 00000000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08569000-085e9000 r-xp 00000000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
085e9000-085ea000 r--p 0007f000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
085ea000-085eb000 rw-p 00080000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
085eb000-085ec000 rw-p 00000000 00:00 0 
08d75000-0c842000 rw-p 00000000 00:00 0          [heap]
6f940000-71a10000 rw-p 00000000 00:00 0 
71a10000-7a3e0000 rw-p 00000000 00:00 0 
7a3e0000-7e566000 rw-p 00000000 00:00 0 
7e566000-8f940000 rw-p 00000000 00:00 0 
8f940000-90540000 rw-p 00000000 00:00 0 
90540000-93940000 rw-p 00000000 00:00 0 
93940000-94099000 r--s 00001000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94099000-94340000 rw-p 00000000 00:00 0 
94340000-94a81000 rw-p 0075a000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94a81000-94f40000 rw-p 00000000 00:00 0 
94f40000-9503b000 rw-p 00e9b000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
9503b000-95340000 rw-p 00000000 00:00 0 
95340000-95348000 r-xs 00f96000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
95348000-95740000 rw-p 00000000 00:00 0 
af3e2000-af3ea000 rw-s 15b6e1000 00:05 3408      /dev/dri/card0
af3ea000-af3f2000 rw-s 15b6d9000 00:05 3408      /dev/dri/card0
af3f2000-af3fa000 rw-s 15b6d1000 00:05 3408      /dev/dri/card0
af3fa000-af402000 rw-s 15b6c9000 00:05 3408      /dev/dri/card0
af402000-af412000 rw-s 15b691000 00:05 3408      /dev/dri/card0
af412000-af422000 rw-s 15b681000 00:05 3408      /dev/dri/card0
af422000-af432000 rw-s 15b671000 00:05 3408      /dev/dri/card0
af432000-af43a000 rw-s 15b417000 00:05 3408      /dev/dri/card0
af43a000-af442000 rw-s 15b5ff000 00:05 3408      /dev/dri/card0
af442000-af44a000 rw-s 15b5ef000 00:05 3408      /dev/dri/card0
af44a000-af452000 rw-s 15b5e7000 00:05 3408      /dev/dri/card0
af452000-af45a000 rw-s 15b5df000 00:05 3408      /dev/dri/card0
af45a000-af462000 rw-s 15b5d7000 00:05 3408      /dev/dri/card0
af462000-af46a000 rw-s 15b614000 00:05 3408      /dev/dri/card0
af46a000-af472000 rw-s 15b60c000 00:05 3408      /dev/dri/card0
af472000-af482000 rw-s 15b5c6000 00:05 3408      /dev/dri/card0
af482000-af48a000 rw-s 15b598000 00:05 3408      /dev/dri/card0
af48a000-af492000 rw-s 15b590000 00:05 3408      /dev/dri/card0
af492000-af49a000 rw-s 15b588000 00:05 3408      /dev/dri/card0
af49a000-af4a2000 rw-s 15b6a1000 00:05 3408      /dev/dri/card0
af4a2000-af4b2000 rw-s 15b568000 00:05 3408      /dev/dri/card0
af4b2000-af4ba000 rw-s 15b4a9000 00:05 3408      /dev/dri/card0
af4ba000-af4c2000 rw-s 15b4a1000 00:05 3408      /dev/dri/card0
af4c2000-af4ca000 rw-s 15b499000 00:05 3408      /dev/dri/card0
af4ca000-af4d2000 rw-s 15b489000 00:05 3408      /dev/dri/card0
af4d2000-af4da000 rw-s 158cb3000 00:05 3408      /dev/dri/card0
af4da000-af4e2000 rw-s 15b533000 00:05 3408      /dev/dri/card0
af4e2000-af4ea000 rw-s 15b52b000 00:05 3408      /dev/dri/card0
af4ea000-af4f2000 rw-s 15b523000 00:05 3408      /dev/dri/card0
af4f2000-af4fa000 rw-s 15b51b000 00:05 3408      /dev/dri/card0
af4fa000-af502000 rw-s 15b644000 00:05 3408      /dev/dri/card0
af502000-af50a000 rw-s 15b63c000 00:05 3408      /dev/dri/card0
af50a000-af512000 rw-s 15b440000 00:05 3408      /dev/dri/card0
af512000-af51a000 rw-s 15b476000 00:05 3408      /dev/dri/card0
af51a000-af522000 rw-s 15b438000 00:05 3408      /dev/dri/card0
af522000-af52a000 rw-s 15b491000 00:05 3408      /dev/dri/card0
af52a000-af532000 rw-s 15b580000 00:05 3408      /dev/dri/card0
af532000-af53a000 rw-s 15b560000 00:05 3408      /dev/dri/card0
af54a000-af552000 rw-s 15b354000 00:05 3408      /dev/dri/card0
af552000-af55a000 rw-s 15b34c000 00:05 3408      /dev/dri/card0
af55a000-af562000 rw-s 15b430000 00:05 3408      /dev/dri/card0
af562000-af56a000 rw-s 15b05e000 00:05 3408      /dev/dri/card0
af56a000-af572000 rw-s 15b558000 00:05 3408      /dev/dri/card0
af572000-af57a000 rw-s 15b550000 00:05 3408      /dev/dri/card0
af57a000-af582000 rw-s 15b2cc000 00:05 3408      /dev/dri/card0
af582000-af58a000 rw-s 15b2c4000 00:05 3408      /dev/dri/card0
af58a000-af592000 rw-s 15b428000 00:05 3408      /dev/dri/card0
af592000-af59a000 rw-s 15b40f000 00:05 3408      /dev/dri/card0
af59a000-af5a2000 rw-s 159b8e000 00:05 3408      /dev/dri/card0
af5a2000-af5aa000 rw-s 15b344000 00:05 3408      /dev/dri/card0
af5ba000-af5c2000 rw-s 15b407000 00:05 3408      /dev/dri/card0
af5c2000-af5ca000 rw-s 15b3ff000 00:05 3408      /dev/dri/card0
af5ca000-af5d2000 rw-s 15b634000 00:05 3408      /dev/dri/card0
af5d2000-af5da000 rw-s 15b450000 00:05 3408      /dev/dri/card0
af5da000-af5e2000 rw-s 15ab13000 00:05 3408      /dev/dri/card0
af5e2000-af5ea000 rw-s 15ab0b000 00:05 3408      /dev/dri/card0
af5ea000-af5f2000 rw-s 15ab03000 00:05 3408      /dev/dri/card0
af5f2000-af5fa000 rw-s 15aafb000 00:05 3408      /dev/dri/card0
af5fa000-af602000 rw-s 15aabd000 00:05 3408      /dev/dri/card0
af602000-af60a000 rw-s 15aab5000 00:05 3408      /dev/dri/card0
af60a000-af612000 rw-s 15aaad000 00:05 3408      /dev/dri/card0
af612000-af61a000 rw-s 1565af000 00:05 3408      /dev/dri/card0
af61a000-af622000 rw-s 15ae8b000 00:05 3408      /dev/dri/card0
af622000-af62a000 rw-s 15a9d7000 00:05 3408      /dev/dri/card0
af62a000-af632000 rw-s 15ae83000 00:05 3408      /dev/dri/card0
af632000-af63a000 rw-s 15aaa5000 00:05 3408      /dev/dri/card0
af63a000-af642000 rw-s 15aa9d000 00:05 3408      /dev/dri/card0
af642000-af64a000 rw-s 15b3f7000 00:05 3408      /dev/dri/card0
af64a000-af652000 rw-s 15af1c000 00:05 3408      /dev/dri/card0
af652000-af65a000 rw-s 15b2bc000 00:05 3408      /dev/dri/card0
af65a000-af662000 rw-s 15a91d000 00:05 3408      /dev/dri/card0
af662000-af66a000 rw-s 15a915000 00:05 3408      /dev/dri/card0
af66a000-af672000 rw-s 15a90d000 00:05 3408      /dev/dri/card0
af672000-af67a000 rw-s 15aa95000 00:05 3408      /dev/dri/card0
af67a000-af682000 rw-s 15a8f5000 00:05 3408      /dev/dri/card0
af682000-af68a000 rw-s 15a6bf000 00:05 3408      /dev/dri/card0
af68a000-af692000 rw-s 159a34000 00:05 3408      /dev/dri/card0
af692000-af69a000 rw-s 15a8ed000 00:05 3408      /dev/dri/card0
af69a000-af6a2000 rw-s 15a9df000 00:05 3408      /dev/dri/card0
af6a2000-af6aa000 rw-s 157f8c000 00:05 3408      /dev/dri/card0
af6aa000-af6b2000 rw-s 15b46e000 00:05 3408      /dev/dri/card0
af6b2000-af6ba000 rw-s 15a9ae000 00:05 3408      /dev/dri/card0
af6ba000-af6c2000 rw-s 15aa8d000 00:05 3408      /dev/dri/card0
af6c2000-af6ca000 rw-s 15b466000 00:05 3408      /dev/dri/card0
af6ca000-af6d2000 rw-s 15b3ed000 00:05 3408      /dev/dri/card0
af6d2000-af6da000 rw-s 159a2c000 00:05 3408      /dev/dri/card0
af6da000-af6e2000 rw-s 15a51f000 00:05 3408      /dev/dri/card0
af6e2000-af6ea000 rw-s 15a517000 00:05 3408      /dev/dri/card0
af6ea000-af6f2000 rw-s 15b3e5000 00:05 3408      /dev/dri/card0
af6f2000-af6fa000 rw-s 15b3c4000 00:05 3408      /dev/dri/card0
af6fa000-af702000 rw-s 15ac8e000 00:05 3408      /dev/dri/card0
af702000-af70a000 rw-s 15a905000 00:05 3408      /dev/dri/card0
af70a000-af712000 rw-s 15af88000 00:05 3408      /dev/dri/card0
af712000-af71a000 rw-s 15ac86000 00:05 3408      /dev/dri/card0
af71a000-af722000 rw-s 15a798000 00:05 3408      /dev/dri/card0
af722000-af72a000 rw-s 15b3dd000 00:05 3408      /dev/dri/card0
af72a000-af732000 rw-s 15b0ce000 00:05 3408      /dev/dri/card0
af732000-af73a000 rw-s 15a0b0000 00:05 3408      /dev/dri/card0
af73a000-af742000 rw-s 15b2b4000 00:05 3408      /dev/dri/card0
af742000-af74a000 rw-s 15affe000 00:05 3408      /dev/dri/card0
af74a000-af752000 rw-s 15b066000 00:05 3408      /dev/dri/card0
af752000-af75a000 rw-s 15864c000 00:05 3408      /dev/dri/card0
af75a000-af762000 rw-s 15b3bc000 00:05 3408      /dev/dri/card0
af762000-af76a000 rw-s 15b334000 00:05 3408      /dev/dri/card0
af76a000-af772000 rw-s 15b3b4000 00:05 3408      /dev/dri/card0
af772000-af77a000 rw-s 159dab000 00:05 3408      /dev/dri/card0
af77a000-af782000 rw-s 15a72f000 00:05 3408      /dev/dri/card0
af782000-af78a000 rw-s 15b548000 00:05 3408      /dev/dri/card0
af78a000-af792000 rw-s 15a7ad000 00:05 3408      /dev/dri/card0
af792000-af79a000 rw-s 15b38c000 00:05 3408      /dev/dri/card0
af79a000-af7a2000 rw-s 15a8fd000 00:05 3408      /dev/dri/card0
af7a2000-af7aa000 rw-s 15b384000 00:05 3408      /dev/dri/card0
af7aa000-af7b2000 rw-s 15ac3c000 00:05 3408      /dev/dri/card0
af7b2000-af7ba000 rw-s 155aeb000 00:05 3408      /dev/dri/card0
af7ba000-af7c2000 rw-s 15b2ac000 00:05 3408      /dev/dri/card0
af7c2000-af7ca000 rw-s 15b1f9000 00:05 3408      /dev/dri/card0
af7ca000-af7d2000 rw-s 15b4ea000 00:05 3408      /dev/dri/card0
af7d2000-af7da000 rw-s 15b47e000 00:05 3408      /dev/dri/card0
af7da000-af7e2000 rw-s 15b2a4000 00:05 3408      /dev/dri/card0
af7e2000-af7ea000 rw-s 15b26c000 00:05 3408      /dev/dri/card0
af7ea000-af7f2000 rw-s 15b314000 00:05 3408      /dev/dri/card0
af7f2000-af7fa000 rw-s 15a65b000 00:05 3408      /dev/dri/card0
af7fa000-af802000 rw-s 159edf000 00:05 3408      /dev/dri/card0
af802000-af80a000 rw-s 15a7bd000 00:05 3408      /dev/dri/card0
af80a000-af812000 rw-s 159c46000 00:05 3408      /dev/dri/card0
af812000-af81a000 rw-s 15a5e4000 00:05 3408      /dev/dri/card0
af81a000-af822000 rw-s 159ff0000 00:05 3408      /dev/dri/card0
af822000-af82a000 rw-s 15af14000 00:05 3408      /dev/dri/card0
af82a000-af832000 rw-s 15a62d000 00:05 3408      /dev/dri/card0
af832000-af83a000 rw-s 15a0a1000 00:05 3408      /dev/dri/card0
af83a000-af842000 rw-s 159dd3000 00:05 3408      /dev/dri/card0
af842000-af84a000 rw-s 15a5da000 00:05 3408      /dev/dri/card0
af84a000-af852000 rw-s 15a653000 00:05 3408      /dev/dri/card0
af852000-af85a000 rw-s 158860000 00:05 3408      /dev/dri/card0
af85a000-af862000 rw-s 15a956000 00:05 3408      /dev/dri/card0
af862000-af86a000 rw-s 15ad76000 00:05 3408      /dev/dri/card0
af86a000-af872000 rw-s 15b540000 00:05 3408      /dev/dri/card0
af872000-af87a000 rw-s 159fe8000 00:05 3408      /dev/dri/card0
af87a000-af882000 rw-s 159c8e000 00:05 3408      /dev/dri/card0
af882000-af88a000 rw-s 159c86000 00:05 3408      /dev/dri/card0
af88a000-af892000 rw-s 159c7e000 00:05 3408      /dev/dri/card0
af892000-af89a000 rw-s 159c76000 00:05 3408      /dev/dri/card0
af89a000-af8a2000 rw-s 1543e8000 00:05 3408      /dev/dri/card0
af8a2000-af8aa000 rw-s 15a554000 00:05 3408      /dev/dri/card0
af8aa000-af8b2000 rw-s 15b254000 00:05 3408      /dev/dri/card0
af8b2000-af8ba000 rw-s 15b4c9000 00:05 3408      /dev/dri/card0
af8ba000-af8c2000 rw-s 15b4c1000 00:05 3408      /dev/dri/card0
af8c2000-af8ca000 rw-s 15b3ac000 00:05 3408      /dev/dri/card0
af8ca000-af8d2000 rw-s 15a57c000 00:05 3408      /dev/dri/card0
af8d2000-af8da000 rw-s 15a574000 00:05 3408      /dev/dri/card0
af8da000-af8e2000 rw-s 15a56c000 00:05 3408      /dev/dri/card0
af8e2000-af8ea000 rw-s 15a564000 00:05 3408      /dev/dri/card0
af8ea000-af8f2000 rw-s 15af0c000 00:05 3408      /dev/dri/card0
af8f2000-af8fa000 rw-s 15a845000 00:05 3408      /dev/dri/card0
af8fa000-af902000 rw-s 159a3c000 00:05 3408      /dev/dri/card0
af902000-af90a000 rw-s 15a83d000 00:05 3408      /dev/dri/card0
af90a000-af912000 rw-s 15b4fa000 00:05 3408      /dev/dri/card0
af912000-af91a000 rw-s 15a1e4000 00:05 3408      /dev/dri/card0
af93a000-af942000 rw-s 15ab53000 00:05 3408      /dev/dri/card0
af942000-af94a000 rw-s 15a768000 00:05 3408      /dev/dri/card0
af94a000-af952000 rw-s 15a020000 00:05 3408      /dev/dri/card0
af952000-af95a000 rw-s 159a9e000 00:05 3408      /dev/dri/card0
af95a000-af962000 rw-s 159e4d000 00:05 3408      /dev/dri/card0
af962000-af96a000 rw-s 15a498000 00:05 3408      /dev/dri/card0
af96a000-af972000 rw-s 1578ac000 00:05 3408      /dev/dri/card0
af972000-af97a000 rw-s 15a480000 00:05 3408      /dev/dri/card0
af97a000-af982000 rw-s 1590b8000 00:05 3408      /dev/dri/card0
af982000-af98a000 rw-s 15a276000 00:05 3408      /dev/dri/card0
af98a000-af992000 rw-s 159c4e000 00:05 3408      /dev/dri/card0
af992000-af99a000 rw-s 15a673000 00:05 3408      /dev/dri/card0
af99a000-af9a2000 rw-s 159f36000 00:05 3408      /dev/dri/card0
af9a2000-af9aa000 rw-s 15a216000 00:05 3408      /dev/dri/card0
af9aa000-af9b2000 rw-s 15af9e000 00:05 3408      /dev/dri/card0
af9b2000-af9ba000 rw-s 15a5fc000 00:05 3408      /dev/dri/card0
af9ba000-af9c2000 rw-s 15ac76000 00:05 3408      /dev/dri/card0
af9c2000-af9ca000 rw-s 15b513000 00:05 3408      /dev/dri/card0
af9ca000-af9d2000 rw-s 15a1a0000 00:05 3408      /dev/dri/card0
af9e2000-af9ea000 rw-s 158e50000 00:05 3408      /dev/dri/card0
af9ea000-af9f2000 rw-s 159489000 00:05 3408      /dev/dri/card0
af9f2000-af9fa000 rw-s 158e58000 00:05 3408      /dev/dri/card0
af9fa000-afa02000 rw-s 158a9f000 00:05 3408      /dev/dri/card0
afa02000-afa0a000 rw-s 15a16a000 00:05 3408      /dev/dri/card0
afa0a000-afa12000 rw-s 15a162000 00:05 3408      /dev/dri/card0
afa12000-afa1a000 rw-s 15a158000 00:05 3408      /dev/dri/card0
afa1a000-afa22000 rw-s 15b4e2000 00:05 3408      /dev/dri/card0
afa22000-afa2a000 rw-s 15a1d4000 00:05 3408      /dev/dri/card0
afa2a000-afa32000 rw-s 1596c2000 00:05 3408      /dev/dri/card0
afa32000-afa3a000 rw-s 1596ba000 00:05 3408      /dev/dri/card0
afa3a000-afa42000 rw-s 15a139000 00:05 3408      /dev/dri/card0
afa42000-afa4a000 rw-s 15b284000 00:05 3408      /dev/dri/card0
afa4a000-afa52000 rw-s 15a20c000 00:05 3408      /dev/dri/card0
afa52000-afa5a000 rw-s 15ad6e000 00:05 3408      /dev/dri/card0
afa5a000-afa62000 rw-s 159f0d000 00:05 3408      /dev/dri/card0
afa62000-afa6a000 rw-s 15a0f8000 00:05 3408      /dev/dri/card0
afa6a000-afa72000 rw-s 15a010000 00:05 3408      /dev/dri/card0
afa72000-afa7a000 rw-s 153be8000 00:05 3408      /dev/dri/card0
afa7a000-afa82000 rw-s 153be0000 00:05 3408      /dev/dri/card0
afa82000-afa8a000 rw-s 15a0d8000 00:05 3408      /dev/dri/card0
afa8a000-afa92000 rw-s 15a84d000 00:05 3408      /dev/dri/card0
afa92000-afa9a000 rw-s 159efa000 00:05 3408      /dev/dri/card0
afa9a000-afaa2000 rw-s 15ae7b000 00:05 3408      /dev/dri/card0
afaa2000-afaaa000 rw-s 15b4f2000 00:05 3408      /dev/dri/card0
afaaa000-afab2000 rw-s 159ee7000 00:05 3408      /dev/dri/card0
afab2000-afaba000 rw-s 159f05000 00:05 3408      /dev/dri/card0
afaba000-afac2000 rw-s 15ae73000 00:05 3408      /dev/dri/card0
afac2000-afaca000 rw-s 15af04000 00:05 3408      /dev/dri/card0
afaca000-afad2000 rw-s 15a150000 00:05 3408      /dev/dri/card0
afad2000-afada000 rw-s 159cc6000 00:05 3408      /dev/dri/card0
afada000-afae2000 rw-s 159cbe000 00:05 3408      /dev/dri/card0
afae2000-afaea000 rw-s 15969a000 00:05 3408      /dev/dri/card0
afaea000-afaf2000 rw-s 157f84000 00:05 3408      /dev/dri/card0
afaf2000-afafa000 rw-s 159ef2000 00:05 3408      /dev/dri/card0
afafa000-afb02000 rw-s 15a835000 00:05 3408      /dev/dri/card0
afb02000-afb0a000 rw-s 159e0c000 00:05 3408      /dev/dri/card0
afb0a000-afb12000 rw-s 158500000 00:05 3408      /dev/dri/card0
afb12000-afb1a000 rw-s 1584f8000 00:05 3408      /dev/dri/card0
afb1a000-afb22000 rw-s 15b578000 00:05 3408      /dev/dri/card0
afb22000-afb2a000 rw-s 15a81d000 00:05 3408      /dev/dri/card0
afb2a000-afb32000 rw-s 15a82d000 00:05 3408      /dev/dri/card0
afb32000-afb3a000 rw-s 15a825000 00:05 3408      /dev/dri/card0
afb3a000-afb42000 rw-s 15a780000 00:05 3408      /dev/dri/card0
afb42000-afb4a000 rw-s 159fb1000 00:05 3408      /dev/dri/card0
afb4a000-afb52000 rw-s 159fa9000 00:05 3408      /dev/dri/card0
afb52000-afb5a000 rw-s 159fa1000 00:05 3408      /dev/dri/card0
afb5a000-afb62000 rw-s 159f99000 00:05 3408      /dev/dri/card0
afb62000-afb6a000 rw-s 159f80000 00:05 3408      /dev/dri/card0
afb6a000-afb72000 rw-s 1584c6000 00:05 3408      /dev/dri/card0
afb72000-afb7a000 rw-s 159e28000 00:05 3408      /dev/dri/card0
afb7a000-afb82000 rw-s 159e20000 00:05 3408      /dev/dri/card0
afb82000-afb8a000 rw-s 159e18000 00:05 3408      /dev/dri/card0
afb8a000-afb92000 rw-s 15a996000 00:05 3408      /dev/dri/card0
afb92000-afb9a000 rw-s 15b45e000 00:05 3408      /dev/dri/card0
afb9a000-afba2000 rw-s 159f3e000 00:05 3408      /dev/dri/card0
afba2000-afbaa000 rw-s 15b41f000 00:05 3408      /dev/dri/card0
afbaa000-afbb2000 rw-s 15a966000 00:05 3408      /dev/dri/card0
afbb2000-afbba000 rw-s 15b1bc000 00:05 3408      /dev/dri/card0
afbba000-afbc2000 rw-s 159ed7000 00:05 3408      /dev/dri/card0
afbc2000-afbca000 rw-s 15a778000 00:05 3408      /dev/dri/card0
afbca000-afbd2000 rw-s 159980000 00:05 3408      /dev/dri/card0
afbd2000-afbda000 rw-s 159c0a000 00:05 3408      /dev/dri/card0
afbda000-afbe2000 rw-s 158510000 00:05 3408      /dev/dri/card0
afbe2000-afbea000 rw-s 158508000 00:05 3408      /dev/dri/card0
afbea000-afbf2000 rw-s 159bf6000 00:05 3408      /dev/dri/card0
afbf2000-afbfa000 rw-s 15a770000 00:05 3408      /dev/dri/card0
afbfa000-afc02000 rw-s 15a8dd000 00:05 3408      /dev/dri/card0
afc02000-afc0a000 rw-s 15a040000 00:05 3408      /dev/dri/card0
afc0a000-afc12000 rw-s 15a038000 00:05 3408      /dev/dri/card0
afc12000-afc1a000 rw-s 15b5be000 00:05 3408      /dev/dri/card0
afc1a000-afc22000 rw-s 15b4da000 00:05 3408      /dev/dri/card0
afc22000-afc2a000 rw-s 15a028000 00:05 3408      /dev/dri/card0
afc2a000-afc32000 rw-s 15a0c8000 00:05 3408      /dev/dri/card0
afc32000-afc3a000 rw-s 159561000 00:05 3408      /dev/dri/card0
afc3a000-afc42000 rw-s 15b4d2000 00:05 3408      /dev/dri/card0
afc42000-afc4a000 rw-s 15b4b9000 00:05 3408      /dev/dri/card0
afc4a000-afc52000 rw-s 15b4b1000 00:05 3408      /dev/dri/card0
afc52000-afc5a000 rw-s 159d14000 00:05 3408      /dev/dri/card0
afc5a000-afc62000 rw-s 15a26e000 00:05 3408      /dev/dri/card0
afc62000-afc6a000 rw-s 15aa5e000 00:05 3408      /dev/dri/card0
afc6a000-afc72000 rw-s 1593e2000 00:05 3408      /dev/dri/card0
afc72000-afc7a000 rw-s 158e86000 00:05 3408      /dev/dri/card0
afc7a000-afc82000 rw-s 15b0c6000 00:05 3408      /dev/dri/card0
afc82000-afc8a000 rw-s 15870a000 00:05 3408      /dev/dri/card0
afc8a000-afc92000 rw-s 158702000 00:05 3408      /dev/dri/card0
afc92000-afc9a000 rw-s 159922000 00:05 3408      /dev/dri/card0
afc9a000-afca2000 rw-s 15a4ce000 00:05 3408      /dev/dri/card0
afca2000-afcaa000 rw-s 15995a000 00:05 3408      /dev/dri/card0
afcaa000-afcb2000 rw-s 15a508000 00:05 3408      /dev/dri/card0
afcb2000-afcba000 rw-s 159f5e000 00:05 3408      /dev/dri/card0
afcba000-afcc2000 rw-s 15a530000 00:05 3408      /dev/dri/card0
afcc2000-afcca000 rw-s 159ca6000 00:05 3408      /dev/dri/card0
afcca000-afcd2000 rw-s 15b1cc000 00:05 3408      /dev/dri/card0
afcd2000-afcda000 rw-s 15b0b2000 00:05 3408      /dev/dri/card0
afcda000-afce2000 rw-s 15a7c5000 00:05 3408      /dev/dri/card0
afce2000-afcea000 rw-s 158fe6000 00:05 3408      /dev/dri/card0
afcea000-afcf2000 rw-s 15b30c000 00:05 3408      /dev/dri/card0
afcf2000-afcfa000 rw-s 1593da000 00:05 3408      /dev/dri/card0
afcfa000-afd02000 rw-s 15ae6b000 00:05 3408      /dev/dri/card0
afd02000-afd0a000 rw-s 15b33c000 00:05 3408      /dev/dri/card0
afd0a000-afd12000 rw-s 15af80000 00:05 3408      /dev/dri/card0
afd12000-afd1a000 rw-s 15aefb000 00:05 3408      /dev/dri/card0
afd1a000-afd22000 rw-s 159c6e000 00:05 3408      /dev/dri/card0
afd22000-afd2a000 rw-s 15a527000 00:05 3408      /dev/dri/card0
afd2a000-afd32000 rw-s 15b29c000 00:05 3408      /dev/dri/card0
afd32000-afd3a000 rw-s 158ec7000 00:05 3408      /dev/dri/card0
afd3a000-afd42000 rw-s 157a1a000 00:05 3408      /dev/dri/card0
afd42000-afd4a000 rw-s 159d6e000 00:05 3408      /dev/dri/card0
afd4a000-afd52000 rw-s 15b214000 00:05 3408      /dev/dri/card0
afd52000-afd5a000 rw-s 15b304000 00:05 3408      /dev/dri/card0
afd5a000-afd62000 rw-s 15a1cc000 00:05 3408      /dev/dri/card0
afd62000-afd6a000 rw-s 15b27c000 00:05 3408      /dev/dri/card0
afd6a000-afd72000 rw-s 15903e000 00:05 3408      /dev/dri/card0
afd72000-afd7a000 rw-s 159bce000 00:05 3408      /dev/dri/card0
afd7a000-afd82000 rw-s 159bc6000 00:05 3408      /dev/dri/card0
afd82000-afd8a000 rw-s 159bbe000 00:05 3408      /dev/dri/card0
afd8a000-afd92000 rw-s 159bb6000 00:05 3408      /dev/dri/card0
afd92000-afd9a000 rw-s 159bae000 00:05 3408      /dev/dri/card0
afd9a000-afda2000 rw-s 159ba6000 00:05 3408      /dev/dri/card0
afda2000-afdaa000 rw-s 159b9e000 00:05 3408      /dev/dri/card0
afdaa000-afdb2000 rw-s 159b96000 00:05 3408      /dev/dri/card0
afdb2000-afdba000 rw-s 159f46000 00:05 3408      /dev/dri/card0
afdba000-afdc2000 rw-s 159b86000 00:05 3408      /dev/dri/card0
afdc2000-afdca000 rw-s 159b7e000 00:05 3408      /dev/dri/card0
afdca000-afdd2000 rw-s 159b76000 00:05 3408      /dev/dri/card0
afdd2000-afdda000 rw-s 159b6e000 00:05 3408      /dev/dri/card0
afdda000-afde2000 rw-s 159b66000 00:05 3408      /dev/dri/card0
afde2000-afdea000 rw-s 159b5e000 00:05 3408      /dev/dri/card0
afdea000-afdf2000 rw-s 159b56000 00:05 3408      /dev/dri/card0
afdf2000-afdfa000 rw-s 159b4e000 00:05 3408      /dev/dri/card0
afdfa000-afe02000 rw-s 159b46000 00:05 3408      /dev/dri/card0
afe02000-afe0a000 rw-s 159b3e000 00:05 3408      /dev/dri/card0
afe0a000-afe12000 rw-s 15a131000 00:05 3408      /dev/dri/card0
afe12000-afe22000 rw-s 15b1e9000 00:05 3408      /dev/dri/card0
afe22000-afe2a000 rw-s 159bde000 00:05 3408      /dev/dri/card0
afe2a000-afe32000 rw-s 159b0e000 00:05 3408      /dev/dri/card0
afe32000-afe3a000 rw-s 159b06000 00:05 3408      /dev/dri/card0
afe3a000-afe42000 rw-s 159afe000 00:05 3408      /dev/dri/card0
afe42000-afe4a000 rw-s 159af6000 00:05 3408      /dev/dri/card0
afe4a000-afe52000 rw-s 159aee000 00:05 3408      /dev/dri/card0
afe52000-afe5a000 rw-s 159ae6000 00:05 3408      /dev/dri/card0
afe5a000-afe62000 rw-s 159ade000 00:05 3408      /dev/dri/card0
afe62000-afe6a000 rw-s 159ad6000 00:05 3408      /dev/dri/card0
afe6a000-afe72000 rw-s 159ace000 00:05 3408      /dev/dri/card0
afe72000-afe7a000 rw-s 159ac6000 00:05 3408      /dev/dri/card0
afe7a000-afe82000 rw-s 159bd6000 00:05 3408      /dev/dri/card0
afe82000-afe8a000 rw-s 1590f9000 00:05 3408      /dev/dri/card0
afe8a000-afe92000 rw-s 158712000 00:05 3408      /dev/dri/card0
afe92000-afe9a000 rw-s 15a98e000 00:05 3408      /dev/dri/card0
afe9a000-afea2000 rw-s 15a986000 00:05 3408      /dev/dri/card0
afea2000-afeaa000 rw-s 159a96000 00:05 3408      /dev/dri/card0
afeaa000-afeb2000 rw-s 159a81000 00:05 3408      /dev/dri/card0
afeb2000-afeba000 rw-s 159a79000 00:05 3408      /dev/dri/card0
afeba000-afec2000 rw-s 159a71000 00:05 3408      /dev/dri/card0
afec2000-afeca000 rw-s 159a69000 00:05 3408      /dev/dri/card0
afeca000-afed2000 rw-s 159a61000 00:05 3408      /dev/dri/card0
afed2000-afeda000 rw-s 159a59000 00:05 3408      /dev/dri/card0
afeda000-afee2000 rw-s 159a8e000 00:05 3408      /dev/dri/card0
afee2000-afeea000 rw-s 158da0000 00:05 3408      /dev/dri/card0
afeea000-afef2000 rw-s 159073000 00:05 3408      /dev/dri/card0
afef2000-afefa000 rw-s 15906b000 00:05 3408      /dev/dri/card0
afefa000-aff02000 rw-s 1581f0000 00:05 3408      /dev/dri/card0
aff02000-aff0a000 rw-s 159cae000 00:05 3408      /dev/dri/card0
aff0a000-aff12000 rw-s 159499000 00:05 3408      /dev/dri/card0
aff12000-aff1a000 rw-s 1595a7000 00:05 3408      /dev/dri/card0
aff1a000-aff22000 rw-s 15a079000 00:05 3408      /dev/dri/card0
aff22000-aff2a000 rw-s 159d3c000 00:05 3408      /dev/dri/card0
aff2a000-aff32000 rw-s 15b22c000 00:05 3408      /dev/dri/card0
aff32000-aff3a000 rw-s 157c20000 00:05 3408      /dev/dri/card0
aff3a000-aff42000 rw-s 15ae9b000 00:05 3408      /dev/dri/card0
aff42000-aff4a000 rw-s 15ae63000 00:05 3408      /dev/dri/card0
aff4a000-aff52000 rw-s 15afee000 00:05 3408      /dev/dri/card0
aff52000-aff5a000 rw-s 15afde000 00:05 3408      /dev/dri/card0
aff5a000-aff62000 rw-s 15acb3000 00:05 3408      /dev/dri/card0
aff62000-aff6a000 rw-s 15b39c000 00:05 3408      /dev/dri/card0
aff6a000-aff72000 rw-s 15b3d5000 00:05 3408      /dev/dri/card0
aff72000-aff7a000 rw-s 15afd6000 00:05 3408      /dev/dri/card0
aff7a000-aff82000 rw-s 15b24c000 00:05 3408      /dev/dri/card0
aff82000-aff8a000 rw-s 15b06e000 00:05 3408      /dev/dri/card0
aff8a000-aff92000 rw-s 1599c0000 00:05 3408      /dev/dri/card0
aff92000-aff9a000 rw-s 1599b8000 00:05 3408      /dev/dri/card0
aff9a000-affa2000 rw-s 15a4de000 00:05 3408      /dev/dri/card0
affa2000-affaa000 rw-s 15a4d6000 00:05 3408      /dev/dri/card0
affaa000-affb2000 rw-s 15a204000 00:05 3408      /dev/dri/card0
affb2000-affba000 rw-s 15a008000 00:05 3408      /dev/dri/card0
affba000-affc2000 rw-s 157ea9000 00:05 3408      /dev/dri/card0
affc2000-affca000 rw-s 159f66000 00:05 3408      /dev/dri/card0
affca000-affd2000 rw-s 15b374000 00:05 3408      /dev/dri/card0
affd2000-affda000 rw-s 159952000 00:05 3408      /dev/dri/card0
affda000-affe2000 rw-s 15994a000 00:05 3408      /dev/dri/card0
affe2000-affea000 rw-s 159942000 00:05 3408      /dev/dri/card0
affea000-afff2000 rw-s 1599b0000 00:05 3408      /dev/dri/card0
afff2000-afffa000 rw-s 155c8a000 00:05 3408      /dev/dri/card0
afffa000-b0002000 rw-s 159f56000 00:05 3408      /dev/dri/card0
b0002000-b000a000 rw-s 15ae5b000 00:05 3408      /dev/dri/card0
b000a000-b0012000 rw-s 157894000 00:05 3408      /dev/dri/card0
b0012000-b001a000 rw-s 15a000000 00:05 3408      /dev/dri/card0
b001a000-b0022000 rw-s 159ce6000 00:05 3408      /dev/dri/card0
b0022000-b002a000 rw-s 15b32c000 00:05 3408      /dev/dri/card0
b002a000-b0032000 rw-s 15a018000 00:05 3408      /dev/dri/card0
b0032000-b003a000 rw-s 15a030000 00:05 3408      /dev/dri/card0
b003a000-b0042000 rw-s 15a55c000 00:05 3408      /dev/dri/card0
b0042000-b004a000 rw-s 159a24000 00:05 3408      /dev/dri/card0
b004a000-b0052000 rw-s 15990b000 00:05 3408      /dev/dri/card0
b0052000-b005a000 rw-s 159fb9000 00:05 3408      /dev/dri/card0
b005a000-b0062000 rw-s 15a1ed000 00:05 3408      /dev/dri/card0
b0062000-b006a000 rw-s 158986000 00:05 3408      /dev/dri/card0
b006a000-b0072000 rw-s 1599a8000 00:05 3408      /dev/dri/card0
b0072000-b007a000 rw-s 1597a9000 00:05 3408      /dev/dri/card0
b007a000-b0082000 rw-s 15a73f000 00:05 3408      /dev/dri/card0
b0082000-b008a000 rw-s 15b448000 00:05 3408      /dev/dri/card0
b008a000-b0092000 rw-s 15b62c000 00:05 3408      /dev/dri/card0
b0092000-b009a000 rw-s 1595b7000 00:05 3408      /dev/dri/card0
b009a000-b00a2000 rw-s 1595af000 00:05 3408      /dev/dri/card0
b00a2000-b00aa000 rw-s 159215000 00:05 3408      /dev/dri/card0
b00aa000-b00b2000 rw-s 158783000 00:05 3408      /dev/dri/card0
b00b2000-b00ba000 rw-s 159903000 00:05 3408      /dev/dri/card0
b00ba000-b00c2000 rw-s 1598fb000 00:05 3408      /dev/dri/card0
b00c2000-b00ca000 rw-s 15a86d000 00:05 3408      /dev/dri/card0
b00ca000-b00d2000 rw-s 15a048000 00:05 3408      /dev/dri/card0
b00d2000-b00da000 rw-s 159f4e000 00:05 3408      /dev/dri/card0
b00da000-b00e2000 rw-s 15b13e000 00:05 3408      /dev/dri/card0
b00e2000-b00ea000 rw-s 1595cf000 00:05 3408      /dev/dri/card0
b00ea000-b00f2000 rw-s 1595c0000 00:05 3408      /dev/dri/card0
b00f2000-b00fa000 rw-s 158f97000 00:05 3408      /dev/dri/card0
b00fa000-b0102000 rw-s 15a071000 00:05 3408      /dev/dri/card0
b0102000-b010a000 rw-s 1596d2000 00:05 3408      /dev/dri/card0
b010a000-b0112000 rw-s 158f87000 00:05 3408      /dev/dri/card0
b0112000-b011a000 rw-s 158f7f000 00:05 3408      /dev/dri/card0
b011a000-b0122000 rw-s 159978000 00:05 3408      /dev/dri/card0
b0122000-b012a000 rw-s 159587000 00:05 3408      /dev/dri/card0
b012a000-b0132000 rw-s 15a1a8000 00:05 3408      /dev/dri/card0
b0132000-b013a000 rw-s 15a625000 00:05 3408      /dev/dri/card0
b013a000-b0142000 rw-s 1593b1000 00:05 3408      /dev/dri/card0
b0142000-b014a000 rw-s 159569000 00:05 3408      /dev/dri/card0
b014a000-b0152000 rw-s 15a081000 00:05 3408      /dev/dri/card0
b0152000-b015a000 rw-s 159559000 00:05 3408      /dev/dri/card0
b015a000-b0162000 rw-s 15b36c000 00:05 3408      /dev/dri/card0
b0162000-b016a000 rw-s 1592ae000 00:05 3408      /dev/dri/card0
b016a000-b0172000 rw-s 159519000 00:05 3408      /dev/dri/card0
b0172000-b017a000 rw-s 159511000 00:05 3408      /dev/dri/card0
b017a000-b0182000 rw-s 159509000 00:05 3408      /dev/dri/card0
b0182000-b018a000 rw-s 159501000 00:05 3408      /dev/dri/card0
b018a000-b0192000 rw-s 1594f9000 00:05 3408      /dev/dri/card0
b0192000-b019a000 rw-s 1594f1000 00:05 3408      /dev/dri/card0
b019a000-b01a2000 rw-s 1594e9000 00:05 3408      /dev/dri/card0
b01a2000-b01aa000 rw-s 1594e1000 00:05 3408      /dev/dri/card0
b01aa000-b01b2000 rw-s 1594d9000 00:05 3408      /dev/dri/card0
b01b2000-b01ba000 rw-s 1594d1000 00:05 3408      /dev/dri/card0
b01ba000-b01c2000 rw-s 1594c9000 00:05 3408      /dev/dri/card0
b01c2000-b01ca000 rw-s 1594c1000 00:05 3408      /dev/dri/card0
b01ca000-b01d2000 rw-s 1594b9000 00:05 3408      /dev/dri/card0
b01d2000-b01da000 rw-s 1594b1000 00:05 3408      /dev/dri/card0
b01da000-b01e2000 rw-s 1594a9000 00:05 3408      /dev/dri/card0
b01e2000-b01ea000 rw-s 159451000 00:05 3408      /dev/dri/card0
b01ea000-b01f2000 rw-s 1594a1000 00:05 3408      /dev/dri/card0
b01f2000-b01fa000 rw-s 15b3cd000 00:05 3408      /dev/dri/card0
b01fa000-b0202000 rw-s 15ae53000 00:05 3408      /dev/dri/card0
b0202000-b020a000 rw-s 159481000 00:05 3408      /dev/dri/card0
b020a000-b0212000 rw-s 159479000 00:05 3408      /dev/dri/card0
b0212000-b021a000 rw-s 159471000 00:05 3408      /dev/dri/card0
b021a000-b0222000 rw-s 159469000 00:05 3408      /dev/dri/card0
b0222000-b022a000 rw-s 159459000 00:05 3408      /dev/dri/card0
b022a000-b0232000 rw-s 15b136000 00:05 3408      /dev/dri/card0
b0232000-b023a000 rw-s 159449000 00:05 3408      /dev/dri/card0
b023a000-b0242000 rw-s 1592a6000 00:05 3408      /dev/dri/card0
b0242000-b024a000 rw-s 15929e000 00:05 3408      /dev/dri/card0
b024a000-b0252000 rw-s 159cb6000 00:05 3408      /dev/dri/card0
b0252000-b025a000 rw-s 159f6e000 00:05 3408      /dev/dri/card0
b025a000-b0262000 rw-s 15acab000 00:05 3408      /dev/dri/card0
b0262000-b026a000 rw-s 15a1b9000 00:05 3408      /dev/dri/card0
b026a000-b0272000 rw-s 15b502000 00:05 3408      /dev/dri/card0
b0272000-b027a000 rw-s 1598b5000 00:05 3408      /dev/dri/card0
b027a000-b0282000 rw-s 159441000 00:05 3408      /dev/dri/card0
b0282000-b028a000 rw-s 1598ea000 00:05 3408      /dev/dri/card0
b028a000-b0292000 rw-s 1598e2000 00:05 3408      /dev/dri/card0
b0292000-b029a000 rw-s 1598a4000 00:05 3408      /dev/dri/card0
b029a000-b02a2000 rw-s 15989c000 00:05 3408      /dev/dri/card0
b02a2000-b02aa000 rw-s 159894000 00:05 3408      /dev/dri/card0
b02aa000-b02b2000 rw-s 15456f000 00:05 3408      /dev/dri/card0
b02b2000-b02ba000 rw-s 159884000 00:05 3408      /dev/dri/card0
b02ba000-b02c2000 rw-s 15987c000 00:05 3408      /dev/dri/card0
b02c2000-b02ca000 rw-s 159874000 00:05 3408      /dev/dri/card0
b02ca000-b02d2000 rw-s 155d62000 00:05 3408      /dev/dri/card0
b02d2000-b02da000 rw-s 154400000 00:05 3408      /dev/dri/card0
b02da000-b02e2000 rw-s 15985f000 00:05 3408      /dev/dri/card0
b02e2000-b02ea000 rw-s 158be4000 00:05 3408      /dev/dri/card0
b02ea000-b02f2000 rw-s 158bdc000 00:05 3408      /dev/dri/card0
b02f2000-b02fa000 rw-s 158bd4000 00:05 3408      /dev/dri/card0
b02fa000-b0302000 rw-s 15982e000 00:05 3408      /dev/dri/card0
b0302000-b030a000 rw-s 159e04000 00:05 3408      /dev/dri/card0
b030a000-b0312000 rw-s 15a7a5000 00:05 3408      /dev/dri/card0
b0312000-b031a000 rw-s 15a815000 00:05 3408      /dev/dri/card0
b031a000-b0322000 rw-s 15a68e000 00:05 3408      /dev/dri/card0
b0322000-b032a000 rw-s 159541000 00:05 3408      /dev/dri/card0
b032a000-b0332000 rw-s 15986c000 00:05 3408      /dev/dri/card0
b0332000-b033a000 rw-s 159dcb000 00:05 3408      /dev/dri/card0
b033a000-b0342000 rw-s 159a44000 00:05 3408      /dev/dri/card0
b0342000-b034a000 rw-s 15a737000 00:05 3408      /dev/dri/card0
b034a000-b0352000 rw-s 159dbc000 00:05 3408      /dev/dri/card0
b0352000-b035a000 rw-s 159370000 00:05 3408      /dev/dri/card0
b035a000-b0362000 rw-s 1593ea000 00:05 3408      /dev/dri/card0
b0362000-b036a000 rw-s 159368000 00:05 3408      /dev/dri/card0
b036a000-b0372000 rw-s 15981f000 00:05 3408      /dev/dri/card0
b0372000-b037a000 rw-s 159817000 00:05 3408      /dev/dri/card0
b037a000-b0382000 rw-s 15a478000 00:05 3408      /dev/dri/card0
b0382000-b038a000 rw-s 15b5b6000 00:05 3408      /dev/dri/card0
b038a000-b0392000 rw-s 15a470000 00:05 3408      /dev/dri/card0
b0392000-b039a000 rw-s 15a4b6000 00:05 3408      /dev/dri/card0
b039a000-b03a2000 rw-s 15ae1b000 00:05 3408      /dev/dri/card0
b03a2000-b03aa000 rw-s 159e64000 00:05 3408      /dev/dri/card0
b03aa000-b03b2000 rw-s 15a8be000 00:05 3408      /dev/dri/card0
b03b2000-b03ba000 rw-s 15af69000 00:05 3408      /dev/dri/card0
b03ba000-b03c2000 rw-s 15b036000 00:05 3408      /dev/dri/card0
b03c2000-b03ca000 rw-s 159788000 00:05 3408      /dev/dri/card0
b03ca000-b03d2000 rw-s 159780000 00:05 3408      /dev/dri/card0
b03d2000-b03da000 rw-s 159732000 00:05 3408      /dev/dri/card0
b03da000-b03e2000 rw-s 15972a000 00:05 3408      /dev/dri/card0
b03e2000-b03ea000 rw-s 159722000 00:05 3408      /dev/dri/card0
b03ea000-b03f2000 rw-s 15971a000 00:05 3408      /dev/dri/card0
b03f2000-b03fa000 rw-s 159712000 00:05 3408      /dev/dri/card0
b03fa000-b0402000 rw-s 15970a000 00:05 3408      /dev/dri/card0
b0402000-b040a000 rw-s 159702000 00:05 3408      /dev/dri/card0
b040a000-b0412000 rw-s 1596fa000 00:05 3408      /dev/dri/card0
b0412000-b041a000 rw-s 1596f2000 00:05 3408      /dev/dri/card0
b041a000-b0422000 rw-s 1596ea000 00:05 3408      /dev/dri/card0
b0422000-b042a000 rw-s 1596e2000 00:05 3408      /dev/dri/card0
b042a000-b0432000 rw-s 159036000 00:05 3408      /dev/dri/card0
b0432000-b043a000 rw-s 15ac0c000 00:05 3408      /dev/dri/card0
b043a000-b0442000 rw-s 15b12e000 00:05 3408      /dev/dri/card0
b0442000-b044a000 rw-s 159e45000 00:05 3408      /dev/dri/card0
b044a000-b0452000 rw-s 159e3d000 00:05 3408      /dev/dri/card0
b0452000-b045a000 rw-s 15a129000 00:05 3408      /dev/dri/card0
b045a000-b0462000 rw-s 15b5a0000 00:05 3408      /dev/dri/card0
b0462000-b046a000 rw-s 1596b2000 00:05 3408      /dev/dri/card0
b046a000-b0472000 rw-s 1584be000 00:05 3408      /dev/dri/card0
b0472000-b047a000 rw-s 159c3e000 00:05 3408      /dev/dri/card0
b047a000-b0482000 rw-s 15b294000 00:05 3408      /dev/dri/card0
b0482000-b048a000 rw-s 1595fc000 00:05 3408      /dev/dri/card0
b048a000-b0492000 rw-s 15789c000 00:05 3408      /dev/dri/card0
b0492000-b049a000 rw-s 15a6a0000 00:05 3408      /dev/dri/card0
b049a000-b04a2000 rw-s 15aecd000 00:05 3408      /dev/dri/card0
b04a2000-b04aa000 rw-s 15902e000 00:05 3408      /dev/dri/card0
b04aa000-b04b2000 rw-s 159026000 00:05 3408      /dev/dri/card0
b04b2000-b04ba000 rw-s 15901e000 00:05 3408      /dev/dri/card0
b04ba000-b04c2000 rw-s 159662000 00:05 3408      /dev/dri/card0
b04c2000-b04ca000 rw-s 15965a000 00:05 3408      /dev/dri/card0
b04ca000-b04d2000 rw-s 158ea6000 00:05 3408      /dev/dri/card0
b04d2000-b04da000 rw-s 15add7000 00:05 3408      /dev/dri/card0
b04da000-b04e2000 rw-s 15b25d000 00:05 3408      /dev/dri/card0
b04e2000-b04ea000 rw-s 15ae4b000 00:05 3408      /dev/dri/card0
b04ea000-b04f2000 rw-s 157c18000 00:05 3408      /dev/dri/card0
b04f2000-b04fa000 rw-s 1593d2000 00:05 3408      /dev/dri/card0
b04fa000-b0502000 rw-s 15a7b5000 00:05 3408      /dev/dri/card0
b0502000-b050a000 rw-s 15a61d000 00:05 3408      /dev/dri/card0
b050a000-b0512000 rw-s 1595ec000 00:05 3408      /dev/dri/card0
b0512000-b051a000 rw-s 1595e4000 00:05 3408      /dev/dri/card0
b051a000-b0522000 rw-s 1595dc000 00:05 3408      /dev/dri/card0
b0522000-b052a000 rw-s 157e4b000 00:05 3408      /dev/dri/card0
b052a000-b0532000 rw-s 1584ce000 00:05 3408      /dev/dri/card0
b0532000-b053a000 rw-s 158de9000 00:05 3408      /dev/dri/card0
b053a000-b0542000 rw-s 15a4f8000 00:05 3408      /dev/dri/card0
b0542000-b054a000 rw-s 15911a000 00:05 3408      /dev/dri/card0
b054a000-b0552000 rw-s 15920d000 00:05 3408      /dev/dri/card0
b0552000-b055a000 rw-s 159439000 00:05 3408      /dev/dri/card0
b055a000-b0562000 rw-s 15b126000 00:05 3408      /dev/dri/card0
b0562000-b056a000 rw-s 15b11e000 00:05 3408      /dev/dri/card0
b056a000-b0572000 rw-s 15a8d5000 00:05 3408      /dev/dri/card0
b0572000-b057a000 rw-s 159422000 00:05 3408      /dev/dri/card0
b057a000-b0582000 rw-s 159419000 00:05 3408      /dev/dri/card0
b0582000-b058a000 rw-s 1579e2000 00:05 3408      /dev/dri/card0
b058a000-b0592000 rw-s 1592c3000 00:05 3408      /dev/dri/card0
b0592000-b059a000 rw-s 15877b000 00:05 3408      /dev/dri/card0
b059a000-b05a2000 rw-s 15aec4000 00:05 3408      /dev/dri/card0
b05a2000-b05aa000 rw-s 159c5f000 00:05 3408      /dev/dri/card0
b05aa000-b05b2000 rw-s 159139000 00:05 3408      /dev/dri/card0
b05b2000-b05ba000 rw-s 15930e000 00:05 3408      /dev/dri/card0
b05ba000-b05c2000 rw-s 1596da000 00:05 3408      /dev/dri/card0
b05c2000-b05ca000 rw-s 158ab4000 00:05 3408      /dev/dri/card0
b05ca000-b05d2000 rw-s 15af96000 00:05 3408      /dev/dri/card0
b05d2000-b05da000 rw-s 159411000 00:05 3408      /dev/dri/card0
b05da000-b05e2000 rw-s 1593f9000 00:05 3408      /dev/dri/card0
b05e2000-b05ea000 rw-s 15b5ae000 00:05 3408      /dev/dri/card0
b05ea000-b05f2000 rw-s 159358000 00:05 3408      /dev/dri/card0
b05f2000-b05fa000 rw-s 1597c2000 00:05 3408      /dev/dri/card0
b05fa000-b0602000 rw-s 159461000 00:05 3408      /dev/dri/card0
b0602000-b060a000 rw-s 1597ba000 00:05 3408      /dev/dri/card0
b060a000-b0612000 rw-s 159cde000 00:05 3408      /dev/dri/card0
b0612000-b061a000 rw-s 158abc000 00:05 3408      /dev/dri/card0
b061a000-b0622000 rw-s 159652000 00:05 3408      /dev/dri/card0
b0622000-b062a000 rw-s 159316000 00:05 3408      /dev/dri/card0
b062a000-b0632000 rw-s 1597b1000 00:05 3408      /dev/dri/card0
b0632000-b063a000 rw-s 1592f9000 00:05 3408      /dev/dri/card0
b063a000-b0642000 rw-s 1592f1000 00:05 3408      /dev/dri/card0
b0642000-b064a000 rw-s 1592e9000 00:05 3408      /dev/dri/card0
b064a000-b0652000 rw-s 1592e1000 00:05 3408      /dev/dri/card0
b0652000-b065a000 rw-s 159431000 00:05 3408      /dev/dri/card0
b065a000-b0662000 rw-s 1593c9000 00:05 3408      /dev/dri/card0
b0662000-b066a000 rw-s 159340000 00:05 3408      /dev/dri/card0
b066a000-b0672000 rw-s 159338000 00:05 3408      /dev/dri/card0
b0672000-b067a000 rw-s 159330000 00:05 3408      /dev/dri/card0
b067a000-b0682000 rw-s 159328000 00:05 3408      /dev/dri/card0
b0682000-b068a000 rw-s 1593c1000 00:05 3408      /dev/dri/card0
b068a000-b0692000 rw-s 159409000 00:05 3408      /dev/dri/card0
b0692000-b069a000 rw-s 159401000 00:05 3408      /dev/dri/card0
b069a000-b06a2000 rw-s 159205000 00:05 3408      /dev/dri/card0
b06a2000-b06aa000 rw-s 159141000 00:05 3408      /dev/dri/card0
b06aa000-b06b2000 rw-s 158364000 00:05 3408      /dev/dri/card0
b06b2000-b06ba000 rw-s 1591f5000 00:05 3408      /dev/dri/card0
b06ba000-b06c2000 rw-s 15a1dc000 00:05 3408      /dev/dri/card0
b06c2000-b06ca000 rw-s 158e76000 00:05 3408      /dev/dri/card0
b06ca000-b06d2000 rw-s 1591fd000 00:05 3408      /dev/dri/card0
b06d2000-b06da000 rw-s 1590b0000 00:05 3408      /dev/dri/card0
b06da000-b06e2000 rw-s 15927d000 00:05 3408      /dev/dri/card0
b06e2000-b06ea000 rw-s 1593a9000 00:05 3408      /dev/dri/card0
b06ea000-b06f2000 rw-s 159350000 00:05 3408      /dev/dri/card0
b06f2000-b06fa000 rw-s 1593b9000 00:05 3408      /dev/dri/card0
b06fa000-b0702000 rw-s 157694000 00:05 3408      /dev/dri/card0
b0702000-b070a000 rw-s 1593a1000 00:05 3408      /dev/dri/card0
b070a000-b0712000 rw-s 159399000 00:05 3408      /dev/dri/card0
b0712000-b071a000 rw-s 159389000 00:05 3408      /dev/dri/card0
b071a000-b0722000 rw-s 159381000 00:05 3408      /dev/dri/card0
b0722000-b072a000 rw-s 15922d000 00:05 3408      /dev/dri/card0
b072a000-b0732000 rw-s 159225000 00:05 3408      /dev/dri/card0
b0732000-b073a000 rw-s 15921d000 00:05 3408      /dev/dri/card0
b073a000-b0742000 rw-s 159348000 00:05 3408      /dev/dri/card0
b0742000-b074a000 rw-s 159016000 00:05 3408      /dev/dri/card0
b074a000-b0752000 rw-s 15926e000 00:05 3408      /dev/dri/card0
b0752000-b075a000 rw-s 15af24000 00:05 3408      /dev/dri/card0
b075a000-b0762000 rw-s 15924d000 00:05 3408      /dev/dri/card0
b0762000-b076a000 rw-s 159245000 00:05 3408      /dev/dri/card0
b076a000-b0772000 rw-s 15923d000 00:05 3408      /dev/dri/card0
b0772000-b077a000 rw-s 15964a000 00:05 3408      /dev/dri/card0
b077a000-b0782000 rw-s 159642000 00:05 3408      /dev/dri/card0
b0782000-b078a000 rw-s 159255000 00:05 3408      /dev/dri/card0
b078a000-b0792000 rw-s 158fce000 00:05 3408      /dev/dri/card0
b0792000-b079a000 rw-s 159d66000 00:05 3408      /dev/dri/card0
b079a000-b07a2000 rw-s 1590f1000 00:05 3408      /dev/dri/card0
b07a2000-b07aa000 rw-s 1590e9000 00:05 3408      /dev/dri/card0
b07aa000-b07b2000 rw-s 15b5f7000 00:05 3408      /dev/dri/card0
b07b2000-b07ba000 rw-s 15a925000 00:05 3408      /dev/dri/card0
b07ba000-b07c2000 rw-s 15a5ad000 00:05 3408      /dev/dri/card0
b07c2000-b07ca000 rw-s 15a5a5000 00:05 3408      /dev/dri/card0
b07ca000-b07d2000 rw-s 15a4a9000 00:05 3408      /dev/dri/card0
b07d2000-b07da000 rw-s 15a4a1000 00:05 3408      /dev/dri/card0
b07da000-b07e2000 rw-s 159235000 00:05 3408      /dev/dri/card0
b07e2000-b07ea000 rw-s 159090000 00:05 3408      /dev/dri/card0
b07ea000-b07f2000 rw-s 15907c000 00:05 3408      /dev/dri/card0
b07f2000-b07fa000 rw-s 1597a1000 00:05 3408      /dev/dri/card0
b07fa000-b0802000 rw-s 159551000 00:05 3408      /dev/dri/card0
b0802000-b080a000 rw-s 158f06000 00:05 3408      /dev/dri/card0
b080a000-b0812000 rw-s 158e96000 00:05 3408      /dev/dri/card0
b0812000-b081a000 rw-s 158ebf000 00:05 3408      /dev/dri/card0
b081a000-b0822000 rw-s 15a9ff000 00:05 3408      /dev/dri/card0
b0822000-b082a000 rw-s 159778000 00:05 3408      /dev/dri/card0
b082a000-b0832000 rw-s 15973a000 00:05 3408      /dev/dri/card0
b0832000-b083a000 rw-s 158326000 00:05 3408      /dev/dri/card0
b083a000-b0842000 rw-s 158fee000 00:05 3408      /dev/dri/card0
b0842000-b084a000 rw-s 157ec9000 00:05 3408      /dev/dri/card0
b084a000-b0852000 rw-s 15a500000 00:05 3408      /dev/dri/card0
b0852000-b085a000 rw-s 15a548000 00:05 3408      /dev/dri/card0
b085a000-b0862000 rw-s 157a52000 00:05 3408      /dev/dri/card0
b0862000-b086a000 rw-s 15b6c1000 00:05 3408      /dev/dri/card0
b086a000-b0872000 rw-s 157ec1000 00:05 3408      /dev/dri/card0
b0872000-b087a000 rw-s 1591ad000 00:05 3408      /dev/dri/card0
b087a000-b0882000 rw-s 1591a5000 00:05 3408      /dev/dri/card0
b0882000-b088a000 rw-s 15b20c000 00:05 3408      /dev/dri/card0
b088a000-b0892000 rw-s 159131000 00:05 3408      /dev/dri/card0
b0892000-b089a000 rw-s 158fde000 00:05 3408      /dev/dri/card0
b089a000-b08a2000 rw-s 159129000 00:05 3408      /dev/dri/card0
b08a2000-b08aa000 rw-s 159266000 00:05 3408      /dev/dri/card0
b08aa000-b08b2000 rw-s 158f76000 00:05 3408      /dev/dri/card0
b08b2000-b08ba000 rw-s 158f6e000 00:05 3408      /dev/dri/card0
b08ba000-b08c2000 rw-s 158f66000 00:05 3408      /dev/dri/card0
b08c2000-b08ca000 rw-s 158f5e000 00:05 3408      /dev/dri/card0
b08ca000-b08d2000 rw-s 158f56000 00:05 3408      /dev/dri/card0
b08d2000-b08da000 rw-s 158f4e000 00:05 3408      /dev/dri/card0
b08da000-b08e2000 rw-s 158f46000 00:05 3408      /dev/dri/card0
b08e2000-b08ea000 rw-s 158f36000 00:05 3408      /dev/dri/card0
b08ea000-b08f2000 rw-s 158f2e000 00:05 3408      /dev/dri/card0
b08f2000-b08fa000 rw-s 158f26000 00:05 3408      /dev/dri/card0
b08fa000-b0902000 rw-s 158f1e000 00:05 3408      /dev/dri/card0
b0902000-b090a000 rw-s 158f16000 00:05 3408      /dev/dri/card0
b090a000-b0912000 rw-s 15897e000 00:05 3408      /dev/dri/card0
b0912000-b091a000 rw-s 15919d000 00:05 3408      /dev/dri/card0
b091a000-b0922000 rw-s 158f0e000 00:05 3408      /dev/dri/card0
b0922000-b092a000 rw-s 15831e000 00:05 3408      /dev/dri/card0
b092a000-b0932000 rw-s 154408000 00:05 3408      /dev/dri/card0
b0932000-b093a000 rw-s 1578a4000 00:05 3408      /dev/dri/card0
b093a000-b0942000 rw-s 159b1f000 00:05 3408      /dev/dri/card0
b0942000-b094a000 rw-s 158acc000 00:05 3408      /dev/dri/card0
b094a000-b0952000 rw-s 15b01e000 00:05 3408      /dev/dri/card0
b0952000-b095a000 rw-s 158fff000 00:05 3408      /dev/dri/card0
b095a000-b0962000 rw-s 15a058000 00:05 3408      /dev/dri/card0
b0962000-b096a000 rw-s 159ff8000 00:05 3408      /dev/dri/card0
b096a000-b0972000 rw-s 15af61000 00:05 3408      /dev/dri/card0
b0972000-b097a000 rw-s 157a2a000 00:05 3408      /dev/dri/card0
b097a000-b0982000 rw-s 1592d8000 00:05 3408      /dev/dri/card0
b0982000-b098a000 rw-s 158e8e000 00:05 3408      /dev/dri/card0
b098a000-b0992000 rw-s 153ca4000 00:05 3408      /dev/dri/card0
b0992000-b099a000 rw-s 15b2fc000 00:05 3408      /dev/dri/card0
b099a000-b09a2000 rw-s 1590a8000 00:05 3408      /dev/dri/card0
b09a2000-b09aa000 rw-s 158e6e000 00:05 3408      /dev/dri/card0
b09aa000-b09b2000 rw-s 15a099000 00:05 3408      /dev/dri/card0
b09b2000-b09ba000 rw-s 159320000 00:05 3408      /dev/dri/card0
b09ba000-b09c2000 rw-s 159088000 00:05 3408      /dev/dri/card0
b09c2000-b09ca000 rw-s 159112000 00:05 3408      /dev/dri/card0
b09ca000-b09d2000 rw-s 15a091000 00:05 3408      /dev/dri/card0
b09d2000-b09da000 rw-s 158ad4000 00:05 3408      /dev/dri/card0
b09da000-b09e2000 rw-s 158e37000 00:05 3408      /dev/dri/card0
b09e2000-b09ea000 rw-s 158e2f000 00:05 3408      /dev/dri/card0
b09ea000-b09f2000 rw-s 158e27000 00:05 3408      /dev/dri/card0
b09f2000-b09fa000 rw-s 158e1f000 00:05 3408      /dev/dri/card0
b09fa000-b0a02000 rw-s 158e16000 00:05 3408      /dev/dri/card0
b0a02000-b0a0a000 rw-s 158e0e000 00:05 3408      /dev/dri/card0
b0a0a000-b0a12000 rw-s 158e06000 00:05 3408      /dev/dri/card0
b0a12000-b0a1a000 rw-s 158dfe000 00:05 3408      /dev/dri/card0
b0a1a000-b0a22000 rw-s 158df6000 00:05 3408      /dev/dri/card0
b0a22000-b0a2a000 rw-s 158e46000 00:05 3408      /dev/dri/card0
b0a2a000-b0a32000 rw-s 158ac4000 00:05 3408      /dev/dri/card0
b0a32000-b0a3a000 rw-s 158de1000 00:05 3408      /dev/dri/card0
b0a3a000-b0a42000 rw-s 155c82000 00:05 3408      /dev/dri/card0
b0a42000-b0a4a000 rw-s 15b6b9000 00:05 3408      /dev/dri/card0
b0a4a000-b0a52000 rw-s 158da9000 00:05 3408      /dev/dri/card0
b0a52000-b0a5a000 rw-s 159098000 00:05 3408      /dev/dri/card0
b0a5a000-b0a62000 rw-s 158d98000 00:05 3408      /dev/dri/card0
b0a62000-b0a6a000 rw-s 158dce000 00:05 3408      /dev/dri/card0
b0a6a000-b0a72000 rw-s 158dc6000 00:05 3408      /dev/dri/card0
b0a72000-b0a7a000 rw-s 158dbe000 00:05 3408      /dev/dri/card0
b0a7a000-b0a82000 rw-s 158db6000 00:05 3408      /dev/dri/card0
b0a82000-b0a8a000 rw-s 158d78000 00:05 3408      /dev/dri/card0
b0a8a000-b0a92000 rw-s 158d70000 00:05 3408      /dev/dri/card0
b0a92000-b0a9a000 rw-s 158d68000 00:05 3408      /dev/dri/card0
b0a9a000-b0aa2000 rw-s 158d60000 00:05 3408      /dev/dri/card0
b0aa2000-b0aaa000 rw-s 158d58000 00:05 3408      /dev/dri/card0
b0aaa000-b0ab2000 rw-s 158d50000 00:05 3408      /dev/dri/card0
b0ab2000-b0aba000 rw-s 15b6b1000 00:05 3408      /dev/dri/card0
b0aba000-b0ac2000 rw-s 15b6a9000 00:05 3408      /dev/dri/card0
b0ac2000-b0aca000 rw-s 158e7e000 00:05 3408      /dev/dri/card0
b0aca000-b0ad2000 rw-s 158d48000 00:05 3408      /dev/dri/card0
b0ad2000-b0ada000 rw-s 158d40000 00:05 3408      /dev/dri/card0
b0ada000-b0ae2000 rw-s 158d38000 00:05 3408      /dev/dri/card0
b0ae2000-b0aea000 rw-s 158d90000 00:05 3408      /dev/dri/card0
b0aea000-b0af2000 rw-s 15a4c6000 00:05 3408      /dev/dri/card0
b0af2000-b0afa000 rw-s 15a4be000 00:05 3408      /dev/dri/card0
b0afa000-b0b02000 rw-s 158d30000 00:05 3408      /dev/dri/card0
b0b02000-b0b0a000 rw-s 158cf2000 00:05 3408      /dev/dri/card0
b0b0a000-b0b12000 rw-s 158cea000 00:05 3408      /dev/dri/card0
b0b12000-b0b1a000 rw-s 158ce2000 00:05 3408      /dev/dri/card0
b0b1a000-b0b22000 rw-s 158cda000 00:05 3408      /dev/dri/card0
b0b22000-b0b2a000 rw-s 158cd2000 00:05 3408      /dev/dri/card0
b0b2a000-b0b32000 rw-s 158cca000 00:05 3408      /dev/dri/card0
b0b32000-b0b3a000 rw-s 158cc2000 00:05 3408      /dev/dri/card0
b0b3a000-b0b42000 rw-s 15b324000 00:05 3408      /dev/dri/card0
b0b42000-b0b4a000 rw-s 15b31c000 00:05 3408      /dev/dri/card0
b0b4a000-b0b52000 rw-s 158cab000 00:05 3408      /dev/dri/card0
b0b52000-b0b5a000 rw-s 158ca2000 00:05 3408      /dev/dri/card0
b0b5a000-b0b62000 rw-s 158c9a000 00:05 3408      /dev/dri/card0
b0b62000-b0b6a000 rw-s 158c92000 00:05 3408      /dev/dri/card0
b0b6a000-b0b72000 rw-s 158c8a000 00:05 3408      /dev/dri/card0
b0b72000-b0b7a000 rw-s 158c82000 00:05 3408      /dev/dri/card0
b0b7a000-b0b82000 rw-s 158c7a000 00:05 3408      /dev/dri/card0
b0b82000-b0b8a000 rw-s 158c72000 00:05 3408      /dev/dri/card0
b0b8a000-b0b92000 rw-s 158c6a000 00:05 3408      /dev/dri/card0
b0b92000-b0b9a000 rw-s 158c62000 00:05 3408      /dev/dri/card0
b0b9a000-b0ba2000 rw-s 158c5a000 00:05 3408      /dev/dri/card0
b0ba2000-b0baa000 rw-s 158c52000 00:05 3408      /dev/dri/card0
b0baa000-b0bb2000 rw-s 158c4a000 00:05 3408      /dev/dri/card0
b0bb2000-b0bba000 rw-s 158c42000 00:05 3408      /dev/dri/card0
b0bba000-b0bc2000 rw-s 158c3a000 00:05 3408      /dev/dri/card0
b0bc2000-b0bca000 rw-s 158c32000 00:05 3408      /dev/dri/card0
b0bca000-b0bd2000 rw-s 158c2a000 00:05 3408      /dev/dri/card0
b0bd2000-b0bda000 rw-s 158c22000 00:05 3408      /dev/dri/card0
b0bda000-b0be2000 rw-s 158c1a000 00:05 3408      /dev/dri/card0
b0be2000-b0bea000 rw-s 158c12000 00:05 3408      /dev/dri/card0
b0bea000-b0bf2000 rw-s 158c0a000 00:05 3408      /dev/dri/card0
b0bf2000-b0bfa000 rw-s 158c02000 00:05 3408      /dev/dri/card0
b0bfa000-b0c02000 rw-s 158bfa000 00:05 3408      /dev/dri/card0
b0c02000-b0c0a000 rw-s 158bf2000 00:05 3408      /dev/dri/card0
b0c0a000-b0c12000 rw-s 159571000 00:05 3408      /dev/dri/card0
b0c12000-b0c1a000 rw-s 159857000 00:05 3408      /dev/dri/card0
b0c1a000-b0c22000 rw-s 15984f000 00:05 3408      /dev/dri/card0
b0c22000-b0c2a000 rw-s 157b89000 00:05 3408      /dev/dri/card0
b0c2a000-b0c32000 rw-s 15983e000 00:05 3408      /dev/dri/card0
b0c32000-b0c3a000 rw-s 159836000 00:05 3408      /dev/dri/card0
b0c3a000-b0c42000 rw-s 158bba000 00:05 3408      /dev/dri/card0
b0c42000-b0c4a000 rw-s 158bb2000 00:05 3408      /dev/dri/card0
b0c4a000-b0c52000 rw-s 158baa000 00:05 3408      /dev/dri/card0
b0c52000-b0c5a000 rw-s 158ba2000 00:05 3408      /dev/dri/card0
b0c5a000-b0c62000 rw-s 158b9a000 00:05 3408      /dev/dri/card0
b0c62000-b0c6a000 rw-s 158b92000 00:05 3408      /dev/dri/card0
b0c6a000-b0c72000 rw-s 158b8a000 00:05 3408      /dev/dri/card0
b0c72000-b0c7a000 rw-s 158b82000 00:05 3408      /dev/dri/card0
b0c7a000-b0c82000 rw-s 158b7a000 00:05 3408      /dev/dri/card0
b0c82000-b0c8a000 rw-s 158b72000 00:05 3408      /dev/dri/card0
b0c8a000-b0c92000 rw-s 158b6a000 00:05 3408      /dev/dri/card0
b0c92000-b0c9a000 rw-s 158b62000 00:05 3408      /dev/dri/card0
b0c9a000-b0ca2000 rw-s 158b5a000 00:05 3408      /dev/dri/card0
b0ca2000-b0caa000 rw-s 158b52000 00:05 3408      /dev/dri/card0
b0caa000-b0cb2000 rw-s 158b4a000 00:05 3408      /dev/dri/card0
b0cb2000-b0cba000 rw-s 158b42000 00:05 3408      /dev/dri/card0
b0cba000-b0cc2000 rw-s 158b3a000 00:05 3408      /dev/dri/card0
b0cc2000-b0cca000 rw-s 158b32000 00:05 3408      /dev/dri/card0
b0cca000-b0cd2000 rw-s 158b2a000 00:05 3408      /dev/dri/card0
b0cd2000-b0cda000 rw-s 158aec000 00:05 3408      /dev/dri/card0
b0cda000-b0ce2000 rw-s 158b16000 00:05 3408      /dev/dri/card0
b0ce2000-b0cea000 rw-s 158b0e000 00:05 3408      /dev/dri/card0
b0cea000-b0cf2000 rw-s 158b06000 00:05 3408      /dev/dri/card0
b0cf2000-b0cfa000 rw-s 158afe000 00:05 3408      /dev/dri/card0
b0cfa000-b0d02000 rw-s 158af6000 00:05 3408      /dev/dri/card0
b0d02000-b0d0a000 rw-s 158b22000 00:05 3408      /dev/dri/card0
b0d0a000-b0d12000 rw-s 158ae4000 00:05 3408      /dev/dri/card0
b0d12000-b0d1a000 rw-s 158adc000 00:05 3408      /dev/dri/card0
b0d1f000-b0d22000 rw-s 158dde000 00:05 3408      /dev/dri/card0
b0d22000-b0d2a000 rw-s 158fd6000 00:05 3408      /dev/dri/card0
b0d2a000-b0d32000 rw-s 15b087000 00:05 3408      /dev/dri/card0
b0d32000-b0d3a000 rw-s 15b394000 00:05 3408      /dev/dri/card0
b0d3a000-b0d42000 rw-s 15b1c4000 00:05 3408      /dev/dri/card0
b0d42000-b0d4a000 rw-s 15b234000 00:05 3408      /dev/dri/card0
b0d4a000-b0d5a000 rw-s 15b21c000 00:05 3408      /dev/dri/card0
b0d5a000-b0d62000 rw-s 158a96000 00:05 3408      /dev/dri/card0
b0d62000-b0d6a000 rw-s 158a8c000 00:05 3408      /dev/dri/card0
b0d6a000-b0d72000 rw-s 158a57000 00:05 3408      /dev/dri/card0
b0d72000-b0d7a000 rw-s 155414000 00:05 3408      /dev/dri/card0
b0d7a000-b0d82000 rw-s 158a84000 00:05 3408      /dev/dri/card0
b0d82000-b0d8a000 rw-s 158a7c000 00:05 3408      /dev/dri/card0
b0d8a000-b0d92000 rw-s 158a74000 00:05 3408      /dev/dri/card0
b0d92000-b0d9a000 rw-s 158a4f000 00:05 3408      /dev/dri/card0
b0d9a000-b0da2000 rw-s 158a47000 00:05 3408      /dev/dri/card0
b0da2000-b0daa000 rw-s 158a3f000 00:05 3408      /dev/dri/card0
b0daa000-b0db2000 rw-s 158a36000 00:05 3408      /dev/dri/card0
b0db2000-b0dba000 rw-s 158a2e000 00:05 3408      /dev/dri/card0
b0dba000-b0dc2000 rw-s 158a64000 00:05 3408      /dev/dri/card0
b0dc2000-b0dca000 rw-s 15788c000 00:05 3408      /dev/dri/card0
b0dca000-b0dd2000 rw-s 158a1e000 00:05 3408      /dev/dri/card0
b0dd2000-b0dda000 rw-s 158a16000 00:05 3408      /dev/dri/card0
b0dda000-b0de2000 rw-s 158a0e000 00:05 3408      /dev/dri/card0
b0de2000-b0dea000 rw-s 158a06000 00:05 3408      /dev/dri/card0
b0dea000-b0df2000 rw-s 1589fe000 00:05 3408      /dev/dri/card0
b0df2000-b0dfa000 rw-s 1589f6000 00:05 3408      /dev/dri/card0
b0dfa000-b0e02000 rw-s 155d00000 00:05 3408      /dev/dri/card0
b0e02000-b0e0a000 rw-s 1589e6000 00:05 3408      /dev/dri/card0
b0e0a000-b0e12000 rw-s 1589de000 00:05 3408      /dev/dri/card0
b0e12000-b0e1a000 rw-s 1589d6000 00:05 3408      /dev/dri/card0
b0e1a000-b0e22000 rw-s 1589ce000 00:05 3408      /dev/dri/card0
b0e22000-b0e2a000 rw-s 1589c6000 00:05 3408      /dev/dri/card0
b0e2a000-b0e32000 rw-s 1589be000 00:05 3408      /dev/dri/card0
b0e32000-b0e3a000 rw-s 1589b6000 00:05 3408      /dev/dri/card0
b0e3a000-b0e42000 rw-s 1589ae000 00:05 3408      /dev/dri/card0
b0e42000-b0e4a000 rw-s 1589a6000 00:05 3408      /dev/dri/card0
b0e4a000-b0e52000 rw-s 15899e000 00:05 3408      /dev/dri/card0
b0e52000-b0e5a000 rw-s 15958f000 00:05 3408      /dev/dri/card0
b0e5a000-b0e62000 rw-s 15875a000 00:05 3408      /dev/dri/card0
b0e62000-b0e6a000 rw-s 15957f000 00:05 3408      /dev/dri/card0
b0e6a000-b0e72000 rw-s 15a9f7000 00:05 3408      /dev/dri/card0
b0e72000-b0e7a000 rw-s 158966000 00:05 3408      /dev/dri/card0
b0e7a000-b0e82000 rw-s 15891a000 00:05 3408      /dev/dri/card0
b0e82000-b0e8a000 rw-s 158912000 00:05 3408      /dev/dri/card0
b0e8a000-b0e92000 rw-s 15890a000 00:05 3408      /dev/dri/card0
b0e92000-b0e9a000 rw-s 158901000 00:05 3408      /dev/dri/card0
b0e9a000-b0ea2000 rw-s 1588f8000 00:05 3408      /dev/dri/card0
b0ea2000-b0eaa000 rw-s 15895e000 00:05 3408      /dev/dri/card0
b0eaa000-b0eb2000 rw-s 1588f0000 00:05 3408      /dev/dri/card0
b0eb2000-b0eba000 rw-s 158956000 00:05 3408      /dev/dri/card0
b0eba000-b0ec2000 rw-s 15894e000 00:05 3408      /dev/dri/card0
b0ec2000-b0eca000 rw-s 158946000 00:05 3408      /dev/dri/card0
b0eca000-b0ed2000 rw-s 15893e000 00:05 3408      /dev/dri/card0
b0ed2000-b0eda000 rw-s 158936000 00:05 3408      /dev/dri/card0
b0eda000-b0ee2000 rw-s 15892e000 00:05 3408      /dev/dri/card0
b0ee2000-b0eea000 rw-s 1588e8000 00:05 3408      /dev/dri/card0
b0eea000-b0ef2000 rw-s 1588e0000 00:05 3408      /dev/dri/card0
b0ef2000-b0efa000 rw-s 1588d8000 00:05 3408      /dev/dri/card0
b0efa000-b0f02000 rw-s 1588d0000 00:05 3408      /dev/dri/card0
b0f02000-b0f0a000 rw-s 1588c8000 00:05 3408      /dev/dri/card0
b0f0a000-b0f12000 rw-s 1588c0000 00:05 3408      /dev/dri/card0
b0f12000-b0f1a000 rw-s 1588b8000 00:05 3408      /dev/dri/card0
b0f1a000-b0f22000 rw-s 1588b0000 00:05 3408      /dev/dri/card0
b0f22000-b0f2a000 rw-s 1588a8000 00:05 3408      /dev/dri/card0
b0f2a000-b0f32000 rw-s 1588a0000 00:05 3408      /dev/dri/card0
b0f32000-b0f3a000 rw-s 158898000 00:05 3408      /dev/dri/card0
b0f3a000-b0f42000 rw-s 158890000 00:05 3408      /dev/dri/card0
b0f42000-b0f4a000 rw-s 158888000 00:05 3408      /dev/dri/card0
b0f4a000-b0f52000 rw-s 157ff4000 00:05 3408      /dev/dri/card0
b0f52000-b0f5a000 rw-s 157fec000 00:05 3408      /dev/dri/card0
b0f5a000-b0f62000 rw-s 158880000 00:05 3408      /dev/dri/card0
b0f62000-b0f6a000 rw-s 158868000 00:05 3408      /dev/dri/card0
b0f6a000-b0f72000 rw-s 15aa17000 00:05 3408      /dev/dri/card0
b0f72000-b0f7a000 rw-s 158976000 00:05 3408      /dev/dri/card0
b0f7a000-b0f82000 rw-s 15896e000 00:05 3408      /dev/dri/card0
b0f82000-b0f8a000 rw-s 158858000 00:05 3408      /dev/dri/card0
b0f8a000-b0f92000 rw-s 158850000 00:05 3408      /dev/dri/card0
b0f92000-b0f9a000 rw-s 158838000 00:05 3408      /dev/dri/card0
b0f9a000-b0fa2000 rw-s 158828000 00:05 3408      /dev/dri/card0
b0fa2000-b0faa000 rw-s 158820000 00:05 3408      /dev/dri/card0
b0faa000-b0fb2000 rw-s 158810000 00:05 3408      /dev/dri/card0
b0fb2000-b0fba000 rw-s 158808000 00:05 3408      /dev/dri/card0
b0fba000-b0fc2000 rw-s 158800000 00:05 3408      /dev/dri/card0
b0fc2000-b0fca000 rw-s 1587f8000 00:05 3408      /dev/dri/card0
b0fca000-b0fd2000 rw-s 1587f0000 00:05 3408      /dev/dri/card0
b0fd2000-b0fda000 rw-s 158926000 00:05 3408      /dev/dri/card0
b0fda000-b0fe2000 rw-s 155cf8000 00:05 3408      /dev/dri/card0
b0fe2000-b0fea000 rw-s 153f74000 00:05 3408      /dev/dri/card0
b0fea000-b0ff2000 rw-s 1587d8000 00:05 3408      /dev/dri/card0
b0ff2000-b0ffa000 rw-s 1587d0000 00:05 3408      /dev/dri/card0
b0ffa000-b1002000 rw-s 1587c8000 00:05 3408      /dev/dri/card0
b1002000-b100a000 rw-s 1587b8000 00:05 3408      /dev/dri/card0
b100a000-b1012000 rw-s 1587b0000 00:05 3408      /dev/dri/card0
b1012000-b101a000 rw-s 157eb9000 00:05 3408      /dev/dri/card0
b101a000-b1022000 rw-s 1587a8000 00:05 3408      /dev/dri/card0
b1022000-b102a000 rw-s 158798000 00:05 3408      /dev/dri/card0
b102a000-b1032000 rw-s 158790000 00:05 3408      /dev/dri/card0
b1032000-b103a000 rw-s 159cd6000 00:05 3408      /dev/dri/card0
b103a000-b1042000 rw-s 15aa35000 00:05 3408      /dev/dri/card0
b1042000-b104a000 rw-s 15b2d4000 00:05 3408      /dev/dri/card0
b104a000-b1052000 rw-s 158752000 00:05 3408      /dev/dri/card0
b1052000-b105a000 rw-s 15874a000 00:05 3408      /dev/dri/card0
b105a000-b1062000 rw-s 158742000 00:05 3408      /dev/dri/card0
b1062000-b106a000 rw-s 158996000 00:05 3408      /dev/dri/card0
b106a000-b1072000 rw-s 158830000 00:05 3408      /dev/dri/card0
b1072000-b107a000 rw-s 15873a000 00:05 3408      /dev/dri/card0
b107a000-b1082000 rw-s 158732000 00:05 3408      /dev/dri/card0
b1082000-b108a000 rw-s 15872a000 00:05 3408      /dev/dri/card0
b108a000-b1092000 rw-s 158722000 00:05 3408      /dev/dri/card0
b1092000-b109a000 rw-s 15871a000 00:05 3408      /dev/dri/card0
b109a000-b10a2000 rw-s 159799000 00:05 3408      /dev/dri/card0
b10a2000-b10aa000 rw-s 159c9e000 00:05 3408      /dev/dri/card0
b10aa000-b10b2000 rw-s 15a050000 00:05 3408      /dev/dri/card0
b10b2000-b10ba000 rw-s 15876a000 00:05 3408      /dev/dri/card0
b10ba000-b10c2000 rw-s 15898e000 00:05 3408      /dev/dri/card0
b10c2000-b10ca000 rw-s 1586dd000 00:05 3408      /dev/dri/card0
b10ca000-b10d2000 rw-s 1586d5000 00:05 3408      /dev/dri/card0
b10d2000-b10da000 rw-s 1586cd000 00:05 3408      /dev/dri/card0
b10da000-b10e2000 rw-s 1586c5000 00:05 3408      /dev/dri/card0
b10e2000-b10ea000 rw-s 1586fa000 00:05 3408      /dev/dri/card0
b10ea000-b10f2000 rw-s 1586bc000 00:05 3408      /dev/dri/card0
b10f2000-b10fa000 rw-s 1586b4000 00:05 3408      /dev/dri/card0
b10fa000-b1102000 rw-s 1586ac000 00:05 3408      /dev/dri/card0
b1102000-b110a000 rw-s 1586a4000 00:05 3408      /dev/dri/card0
b110a000-b1112000 rw-s 15869c000 00:05 3408      /dev/dri/card0
b1112000-b111a000 rw-s 158694000 00:05 3408      /dev/dri/card0
b111a000-b1122000 rw-s 15868c000 00:05 3408      /dev/dri/card0
b1122000-b112a000 rw-s 158684000 00:05 3408      /dev/dri/card0
b112a000-b1132000 rw-s 15867c000 00:05 3408      /dev/dri/card0
b1132000-b113a000 rw-s 158674000 00:05 3408      /dev/dri/card0
b113a000-b1142000 rw-s 15866c000 00:05 3408      /dev/dri/card0
b1142000-b114a000 rw-s 158664000 00:05 3408      /dev/dri/card0
b114a000-b1152000 rw-s 15865c000 00:05 3408      /dev/dri/card0
b1152000-b115a000 rw-s 158654000 00:05 3408      /dev/dri/card0
b115a000-b1162000 rw-s 158762000 00:05 3408      /dev/dri/card0
b1162000-b116a000 rw-s 158644000 00:05 3408      /dev/dri/card0
b116a000-b1172000 rw-s 15863c000 00:05 3408      /dev/dri/card0
b1172000-b117a000 rw-s 158634000 00:05 3408      /dev/dri/card0
b117a000-b1182000 rw-s 15862c000 00:05 3408      /dev/dri/card0
b1182000-b118a000 rw-s 158624000 00:05 3408      /dev/dri/card0
b118a000-b1192000 rw-s 15861c000 00:05 3408      /dev/dri/card0
b1192000-b119a000 rw-s 158614000 00:05 3408      /dev/dri/card0
b119a000-b11a2000 rw-s 15860c000 00:05 3408      /dev/dri/card0
b11a2000-b11aa000 rw-s 158604000 00:05 3408      /dev/dri/card0
b11aa000-b11b2000 rw-s 1585fc000 00:05 3408      /dev/dri/card0
b11b2000-b11ba000 rw-s 1585f4000 00:05 3408      /dev/dri/card0
b11ba000-b11c2000 rw-s 1585ec000 00:05 3408      /dev/dri/card0
b11c2000-b11ca000 rw-s 1585e4000 00:05 3408      /dev/dri/card0
b11ca000-b11d2000 rw-s 1585dc000 00:05 3408      /dev/dri/card0
b11d2000-b11da000 rw-s 1585d4000 00:05 3408      /dev/dri/card0
b11da000-b11e2000 rw-s 1585cc000 00:05 3408      /dev/dri/card0
b11e2000-b11ea000 rw-s 1585c4000 00:05 3408      /dev/dri/card0
b11ea000-b11f2000 rw-s 1585bc000 00:05 3408      /dev/dri/card0
b11f2000-b11fa000 rw-s 1585b4000 00:05 3408      /dev/dri/card0
b11fa000-b1202000 rw-s 15764c000 00:05 3408      /dev/dri/card0
b1202000-b120a000 rw-s 1585ac000 00:05 3408      /dev/dri/card0
b120a000-b1212000 rw-s 15859c000 00:05 3408      /dev/dri/card0
b1212000-b121a000 rw-s 158594000 00:05 3408      /dev/dri/card0
b121a000-b1222000 rw-s 15858c000 00:05 3408      /dev/dri/card0
b1222000-b122a000 rw-s 158584000 00:05 3408      /dev/dri/card0
b122a000-b1232000 rw-s 15857c000 00:05 3408      /dev/dri/card0
b1232000-b123a000 rw-s 158574000 00:05 3408      /dev/dri/card0
b123a000-b1242000 rw-s 15856c000 00:05 3408      /dev/dri/card0
b1242000-b124a000 rw-s 158564000 00:05 3408      /dev/dri/card0
b124a000-b1252000 rw-s 15855c000 00:05 3408      /dev/dri/card0
b1252000-b125a000 rw-s 158554000 00:05 3408      /dev/dri/card0
b125a000-b1262000 rw-s 15854c000 00:05 3408      /dev/dri/card0
b1262000-b126a000 rw-s 158544000 00:05 3408      /dev/dri/card0
b126a000-b1272000 rw-s 15853c000 00:05 3408      /dev/dri/card0
b1272000-b127a000 rw-s 158534000 00:05 3408      /dev/dri/card0
b127a000-b1282000 rw-s 15852c000 00:05 3408      /dev/dri/card0
b1282000-b128a000 rw-s 15847e000 00:05 3408      /dev/dri/card0
b128a000-b1292000 rw-s 15851c000 00:05 3408      /dev/dri/card0
b1292000-b129a000 rw-s 159d5e000 00:05 3408      /dev/dri/card0
b129a000-b12a2000 rw-s 159d55000 00:05 3408      /dev/dri/card0
b12a2000-b12aa000 rw-s 15b116000 00:05 3408      /dev/dri/card0
b12aa000-b12b2000 rw-s 15529c000 00:05 3408      /dev/dri/card0
b12b2000-b12ba000 rw-s 159f91000 00:05 3408      /dev/dri/card0
b12ba000-b12c2000 rw-s 159f89000 00:05 3408      /dev/dri/card0
b12c2000-b12ca000 rw-s 159597000 00:05 3408      /dev/dri/card0
b12ca000-b12d2000 rw-s 15925e000 00:05 3408      /dev/dri/card0
b12d2000-b12da000 rw-s 159aa6000 00:05 3408      /dev/dri/card0
b12da000-b12e2000 rw-s 159046000 00:05 3408      /dev/dri/card0
b12e2000-b12ea000 rw-s 1584b6000 00:05 3408      /dev/dri/card0
b12ea000-b12f2000 rw-s 1584f0000 00:05 3408      /dev/dri/card0
b12f2000-b12fa000 rw-s 15a696000 00:05 3408      /dev/dri/card0
b12fa000-b1302000 rw-s 1584ae000 00:05 3408      /dev/dri/card0
b1302000-b130a000 rw-s 1584a6000 00:05 3408      /dev/dri/card0
b130a000-b1312000 rw-s 15849e000 00:05 3408      /dev/dri/card0
b1312000-b131a000 rw-s 158496000 00:05 3408      /dev/dri/card0
b131a000-b1322000 rw-s 15848e000 00:05 3408      /dev/dri/card0
b1322000-b132a000 rw-s 158486000 00:05 3408      /dev/dri/card0
b132a000-b1332000 rw-s 158476000 00:05 3408      /dev/dri/card0
b1332000-b133a000 rw-s 158458000 00:05 3408      /dev/dri/card0
b133a000-b1342000 rw-s 158450000 00:05 3408      /dev/dri/card0
b1342000-b134a000 rw-s 158448000 00:05 3408      /dev/dri/card0
b134a000-b1352000 rw-s 158440000 00:05 3408      /dev/dri/card0
b1352000-b135a000 rw-s 158438000 00:05 3408      /dev/dri/card0
b135a000-b1362000 rw-s 158430000 00:05 3408      /dev/dri/card0
b1362000-b136a000 rw-s 15846e000 00:05 3408      /dev/dri/card0
b136a000-b1372000 rw-s 158466000 00:05 3408      /dev/dri/card0
b1372000-b137a000 rw-s 158428000 00:05 3408      /dev/dri/card0
b137a000-b1382000 rw-s 15b624000 00:05 3408      /dev/dri/card0
b1382000-b138a000 rw-s 15a0c0000 00:05 3408      /dev/dri/card0
b138a000-b1392000 rw-s 1583fb000 00:05 3408      /dev/dri/card0
b1392000-b139a000 rw-s 1583f3000 00:05 3408      /dev/dri/card0
b139a000-b13a2000 rw-s 1583eb000 00:05 3408      /dev/dri/card0
b13a2000-b13aa000 rw-s 1583e3000 00:05 3408      /dev/dri/card0
b13aa000-b13b2000 rw-s 158420000 00:05 3408      /dev/dri/card0
b13b2000-b13ba000 rw-s 158418000 00:05 3408      /dev/dri/card0
b13ba000-b13c2000 rw-s 1583da000 00:05 3408      /dev/dri/card0
b13c2000-b13ca000 rw-s 1583d2000 00:05 3408      /dev/dri/card0
b13ca000-b13d2000 rw-s 1583ca000 00:05 3408      /dev/dri/card0
b13d2000-b13da000 rw-s 1583c2000 00:05 3408      /dev/dri/card0
b13da000-b13e2000 rw-s 1583ba000 00:05 3408      /dev/dri/card0
b13e2000-b13ea000 rw-s 1583a5000 00:05 3408      /dev/dri/card0
b13ea000-b13f2000 rw-s 15839d000 00:05 3408      /dev/dri/card0
b13f2000-b13fa000 rw-s 158395000 00:05 3408      /dev/dri/card0
b13fa000-b1402000 rw-s 15838d000 00:05 3408      /dev/dri/card0
b1402000-b140a000 rw-s 158385000 00:05 3408      /dev/dri/card0
b140a000-b1412000 rw-s 15837d000 00:05 3408      /dev/dri/card0
b1412000-b141a000 rw-s 1583b2000 00:05 3408      /dev/dri/card0
b141a000-b1422000 rw-s 158374000 00:05 3408      /dev/dri/card0
b1422000-b142a000 rw-s 1552ed000 00:05 3408      /dev/dri/card0
b142a000-b1432000 rw-s 1552e5000 00:05 3408      /dev/dri/card0
b1432000-b143a000 rw-s 1552dd000 00:05 3408      /dev/dri/card0
b143a000-b1442000 rw-s 1552d5000 00:05 3408      /dev/dri/card0
b1442000-b144a000 rw-s 1552cd000 00:05 3408      /dev/dri/card0
b144a000-b1452000 rw-s 1552c4000 00:05 3408      /dev/dri/card0
b1452000-b145a000 rw-s 159296000 00:05 3408      /dev/dri/card0
b145a000-b1462000 rw-s 15835c000 00:05 3408      /dev/dri/card0
b1462000-b146a000 rw-s 158354000 00:05 3408      /dev/dri/card0
b146a000-b1472000 rw-s 158316000 00:05 3408      /dev/dri/card0
b1472000-b147a000 rw-s 15830e000 00:05 3408      /dev/dri/card0
b147a000-b1482000 rw-s 158306000 00:05 3408      /dev/dri/card0
b1482000-b148a000 rw-s 1582fe000 00:05 3408      /dev/dri/card0
b148a000-b1492000 rw-s 1582f6000 00:05 3408      /dev/dri/card0
b1492000-b149a000 rw-s 1582ee000 00:05 3408      /dev/dri/card0
b149a000-b14a2000 rw-s 1582e6000 00:05 3408      /dev/dri/card0
b14a2000-b14aa000 rw-s 15ac1c000 00:05 3408      /dev/dri/card0
b14aa000-b14b2000 rw-s 158dd6000 00:05 3408      /dev/dri/card0
b14b2000-b14ba000 rw-s 15b08f000 00:05 3408      /dev/dri/card0
b14ba000-b14c2000 rw-s 15b2f4000 00:05 3408      /dev/dri/card0
b14c2000-b14ca000 rw-s 1582be000 00:05 3408      /dev/dri/card0
b14ca000-b14d2000 rw-s 1582b6000 00:05 3408      /dev/dri/card0
b14d2000-b14da000 rw-s 1582ae000 00:05 3408      /dev/dri/card0
b14da000-b14e2000 rw-s 1582a6000 00:05 3408      /dev/dri/card0
b14e2000-b14ea000 rw-s 15829e000 00:05 3408      /dev/dri/card0
b14ea000-b14f2000 rw-s 158296000 00:05 3408      /dev/dri/card0
b14f2000-b14fa000 rw-s 15828e000 00:05 3408      /dev/dri/card0
b14fa000-b1502000 rw-s 158286000 00:05 3408      /dev/dri/card0
b1502000-b150a000 rw-s 15827e000 00:05 3408      /dev/dri/card0
b150a000-b1512000 rw-s 15561c000 00:05 3408      /dev/dri/card0
b1512000-b151a000 rw-s 158250000 00:05 3408      /dev/dri/card0
b151a000-b1522000 rw-s 158248000 00:05 3408      /dev/dri/card0
b1522000-b152a000 rw-s 158240000 00:05 3408      /dev/dri/card0
b152a000-b1532000 rw-s 158238000 00:05 3408      /dev/dri/card0
b1532000-b153a000 rw-s 158230000 00:05 3408      /dev/dri/card0
b153a000-b1542000 rw-s 158228000 00:05 3408      /dev/dri/card0
b1542000-b154a000 rw-s 158276000 00:05 3408      /dev/dri/card0
b154a000-b1552000 rw-s 15826e000 00:05 3408      /dev/dri/card0
b1552000-b155a000 rw-s 158266000 00:05 3408      /dev/dri/card0
b155a000-b1562000 rw-s 15825e000 00:05 3408      /dev/dri/card0
b1562000-b156a000 rw-s 158220000 00:05 3408      /dev/dri/card0
b156a000-b1572000 rw-s 158218000 00:05 3408      /dev/dri/card0
b1572000-b157a000 rw-s 158210000 00:05 3408      /dev/dri/card0
b157a000-b1582000 rw-s 158208000 00:05 3408      /dev/dri/card0
b1582000-b158a000 rw-s 1581f8000 00:05 3408      /dev/dri/card0
b158a000-b1592000 rw-s 15b016000 00:05 3408      /dev/dri/card0
b1592000-b159a000 rw-s 1581e8000 00:05 3408      /dev/dri/card0
b159a000-b15a2000 rw-s 1581e0000 00:05 3408      /dev/dri/card0
b15a2000-b15aa000 rw-s 1581d8000 00:05 3408      /dev/dri/card0
b15aa000-b15b2000 rw-s 1581b6000 00:05 3408      /dev/dri/card0
b15b2000-b15b5000 rw-s 1581b3000 00:05 3408      /dev/dri/card0
b15b5000-b15bd000 rw-s 1581ab000 00:05 3408      /dev/dri/card0
b15bd000-b15c5000 rw-s 1581a3000 00:05 3408      /dev/dri/card0
b15c5000-b15cd000 rw-s 15819b000 00:05 3408      /dev/dri/card0
b15cd000-b15d5000 rw-s 158193000 00:05 3408      /dev/dri/card0
b15d5000-b15dd000 rw-s 15818b000 00:05 3408      /dev/dri/card0
b15dd000-b15e5000 rw-s 1581d0000 00:05 3408      /dev/dri/card0
b15e5000-b15ed000 rw-s 159529000 00:05 3408      /dev/dri/card0
b15ed000-b15f5000 rw-s 159521000 00:05 3408      /dev/dri/card0
b15f5000-b15fd000 rw-s 158182000 00:05 3408      /dev/dri/card0
b15fd000-b1605000 rw-s 15817a000 00:05 3408      /dev/dri/card0
b1605000-b160d000 rw-s 158172000 00:05 3408      /dev/dri/card0
b160d000-b1615000 rw-s 15816a000 00:05 3408      /dev/dri/card0
b1615000-b161d000 rw-s 158162000 00:05 3408      /dev/dri/card0
b161d000-b1625000 rw-s 15815a000 00:05 3408      /dev/dri/card0
b1625000-b162d000 rw-s 158152000 00:05 3408      /dev/dri/card0
b162d000-b1635000 rw-s 15814a000 00:05 3408      /dev/dri/card0
b1635000-b163d000 rw-s 158142000 00:05 3408      /dev/dri/card0
b163d000-b1645000 rw-s 15813a000 00:05 3408      /dev/dri/card0
b1645000-b164d000 rw-s 158132000 00:05 3408      /dev/dri/card0
b164d000-b1650000 rw-s 157f02000 00:05 3408      /dev/dri/card0
b1650000-b1658000 rw-s 15812a000 00:05 3408      /dev/dri/card0
b1658000-b1660000 rw-s 158122000 00:05 3408      /dev/dri/card0
b1660000-b1668000 rw-s 15811a000 00:05 3408      /dev/dri/card0
b1668000-b1670000 rw-s 158112000 00:05 3408      /dev/dri/card0
b1670000-b1678000 rw-s 15810a000 00:05 3408      /dev/dri/card0
b1678000-b1680000 rw-s 158102000 00:05 3408      /dev/dri/card0
b1680000-b1688000 rw-s 1580fa000 00:05 3408      /dev/dri/card0
b1688000-b1690000 rw-s 1580f2000 00:05 3408      /dev/dri/card0
b1690000-b1698000 rw-s 1580ea000 00:05 3408      /dev/dri/card0
b1698000-b16a0000 rw-s 1580e2000 00:05 3408      /dev/dri/card0
b16a0000-b16a8000 rw-s 1580da000 00:05 3408      /dev/dri/card0
b16a8000-b16b0000 rw-s 1580d2000 00:05 3408      /dev/dri/card0
b16b0000-b16b8000 rw-s 1580ca000 00:05 3408      /dev/dri/card0
b16b8000-b16c0000 rw-s 1580c2000 00:05 3408      /dev/dri/card0
b16c0000-b16c8000 rw-s 1580ba000 00:05 3408      /dev/dri/card0
b16c8000-b16d0000 rw-s 1580b2000 00:05 3408      /dev/dri/card0
b16d0000-b16d8000 rw-s 1580aa000 00:05 3408      /dev/dri/card0
b16d8000-b16e0000 rw-s 1580a2000 00:05 3408      /dev/dri/card0
b16e0000-b16e8000 rw-s 15809a000 00:05 3408      /dev/dri/card0
b16e8000-b16f0000 rw-s 158092000 00:05 3408      /dev/dri/card0
b16f0000-b16f8000 rw-s 15808a000 00:05 3408      /dev/dri/card0
b16f8000-b1700000 rw-s 158082000 00:05 3408      /dev/dri/card0
b1700000-b1708000 rw-s 158065000 00:05 3408      /dev/dri/card0
b1708000-b1710000 rw-s 15805d000 00:05 3408      /dev/dri/card0
b1710000-b1718000 rw-s 15a0f0000 00:05 3408      /dev/dri/card0
b1718000-b1720000 rw-s 15a4f0000 00:05 3408      /dev/dri/card0
b1720000-b1728000 rw-s 15a4e8000 00:05 3408      /dev/dri/card0
b1728000-b1730000 rw-s 15b2e5000 00:05 3408      /dev/dri/card0
b1730000-b1738000 rw-s 15807a000 00:05 3408      /dev/dri/card0
b1738000-b1740000 rw-s 158072000 00:05 3408      /dev/dri/card0
b1740000-b1748000 rw-s 158034000 00:05 3408      /dev/dri/card0
b1748000-b1750000 rw-s 15802c000 00:05 3408      /dev/dri/card0
b1750000-b1758000 rw-s 158024000 00:05 3408      /dev/dri/card0
b1758000-b1760000 rw-s 15801c000 00:05 3408      /dev/dri/card0
b1760000-b1768000 rw-s 158014000 00:05 3408      /dev/dri/card0
b1768000-b1770000 rw-s 15800c000 00:05 3408      /dev/dri/card0
b1770000-b1778000 rw-s 158004000 00:05 3408      /dev/dri/card0
b1778000-b1780000 rw-s 157ffc000 00:05 3408      /dev/dri/card0
b1780000-b1788000 rw-s 158878000 00:05 3408      /dev/dri/card0
b1788000-b1790000 rw-s 158870000 00:05 3408      /dev/dri/card0
b1790000-b1798000 rw-s 157fe4000 00:05 3408      /dev/dri/card0
b1798000-b17a0000 rw-s 15a6fa000 00:05 3408      /dev/dri/card0
b17a0000-b17a8000 rw-s 157fd4000 00:05 3408      /dev/dri/card0
b17a8000-b17b0000 rw-s 157fcc000 00:05 3408      /dev/dri/card0
b17b0000-b17b8000 rw-s 157fc4000 00:05 3408      /dev/dri/card0
b17b8000-b17c0000 rw-s 157fbc000 00:05 3408      /dev/dri/card0
b17c0000-b17c8000 rw-s 157fb4000 00:05 3408      /dev/dri/card0
b17c8000-b17d0000 rw-s 157f4f000 00:05 3408      /dev/dri/card0
b17d0000-b17d8000 rw-s 15afe6000 00:05 3408      /dev/dri/card0
b17d8000-b17e0000 rw-s 15ae93000 00:05 3408      /dev/dri/card0
b17e0000-b17e8000 rw-s 157f74000 00:05 3408      /dev/dri/card0
b17e8000-b17f0000 rw-s 157f27000 00:05 3408      /dev/dri/card0
b17f0000-b17f8000 rw-s 157fac000 00:05 3408      /dev/dri/card0
b17f8000-b1800000 rw-s 157fa4000 00:05 3408      /dev/dri/card0
b1800000-b1808000 rw-s 157f9c000 00:05 3408      /dev/dri/card0
b1808000-b1810000 rw-s 157c98000 00:05 3408      /dev/dri/card0
b1810000-b1818000 rw-s 157f65000 00:05 3408      /dev/dri/card0
b1818000-b1820000 rw-s 157f5d000 00:05 3408      /dev/dri/card0
b1820000-b1828000 rw-s 157f1f000 00:05 3408      /dev/dri/card0
b1828000-b1830000 rw-s 157ef9000 00:05 3408      /dev/dri/card0
b1830000-b1838000 rw-s 157ef1000 00:05 3408      /dev/dri/card0
b1838000-b1840000 rw-s 157ee9000 00:05 3408      /dev/dri/card0
b1840000-b1848000 rw-s 157ee1000 00:05 3408      /dev/dri/card0
b1848000-b1850000 rw-s 157ed9000 00:05 3408      /dev/dri/card0
b1850000-b1858000 rw-s 157ed1000 00:05 3408      /dev/dri/card0
b1858000-b1860000 rw-s 155e7e000 00:05 3408      /dev/dri/card0
b1860000-b1868000 rw-s 15aa3e000 00:05 3408      /dev/dri/card0
b1868000-b1870000 rw-s 15a97e000 00:05 3408      /dev/dri/card0
b1870000-b1878000 rw-s 15a976000 00:05 3408      /dev/dri/card0
b1878000-b1880000 rw-s 15a96e000 00:05 3408      /dev/dri/card0
b1880000-b1888000 rw-s 153cb3000 00:05 3408      /dev/dri/card0
b1888000-b1890000 rw-s 157e6c000 00:05 3408      /dev/dri/card0
b1890000-b1898000 rw-s 15a806000 00:05 3408      /dev/dri/card0
b1898000-b18a0000 rw-s 1587a0000 00:05 3408      /dev/dri/card0
b18a0000-b18a8000 rw-s 1591d6000 00:05 3408      /dev/dri/card0
b18a8000-b18b0000 rw-s 1591ce000 00:05 3408      /dev/dri/card0
b18b0000-b18b8000 rw-s 1591c6000 00:05 3408      /dev/dri/card0
b18b8000-b18c0000 rw-s 1591be000 00:05 3408      /dev/dri/card0
b18c0000-b18c8000 rw-s 1591b5000 00:05 3408      /dev/dri/card0
b18c8000-b18d0000 rw-s 157ea1000 00:05 3408      /dev/dri/card0
b18d0000-b18d8000 rw-s 157e99000 00:05 3408      /dev/dri/card0
b18d8000-b18e0000 rw-s 157e91000 00:05 3408      /dev/dri/card0
b18e0000-b18e8000 rw-s 157e89000 00:05 3408      /dev/dri/card0
b18e8000-b18f0000 rw-s 157e81000 00:05 3408      /dev/dri/card0
b18f0000-b18f8000 rw-s 157e43000 00:05 3408      /dev/dri/card0
b18f8000-b1900000 rw-s 157e3b000 00:05 3408      /dev/dri/card0
b1900000-b1908000 rw-s 157e33000 00:05 3408      /dev/dri/card0
b1908000-b1910000 rw-s 159db4000 00:05 3408      /dev/dri/card0
b1910000-b1918000 rw-s 15b2dd000 00:05 3408      /dev/dri/card0
b1918000-b1920000 rw-s 157e1b000 00:05 3408      /dev/dri/card0
b1920000-b1928000 rw-s 157e13000 00:05 3408      /dev/dri/card0
b1928000-b1930000 rw-s 157e0b000 00:05 3408      /dev/dri/card0
b1930000-b1938000 rw-s 157e02000 00:05 3408      /dev/dri/card0
b1938000-b1940000 rw-s 157dfa000 00:05 3408      /dev/dri/card0
b1940000-b1948000 rw-s 157df2000 00:05 3408      /dev/dri/card0
b1948000-b1950000 rw-s 157dea000 00:05 3408      /dev/dri/card0
b1950000-b1958000 rw-s 157de2000 00:05 3408      /dev/dri/card0
b1958000-b1960000 rw-s 157dda000 00:05 3408      /dev/dri/card0
b1960000-b1968000 rw-s 157dd2000 00:05 3408      /dev/dri/card0
b1968000-b1970000 rw-s 157dca000 00:05 3408      /dev/dri/card0
b1970000-b1978000 rw-s 15b28c000 00:05 3408      /dev/dri/card0
b1978000-b1980000 rw-s 157dba000 00:05 3408      /dev/dri/card0
b1980000-b1988000 rw-s 157db2000 00:05 3408      /dev/dri/card0
b1988000-b1990000 rw-s 157daa000 00:05 3408      /dev/dri/card0
b1990000-b1998000 rw-s 157da0000 00:05 3408      /dev/dri/card0
b1998000-b19a0000 rw-s 157c90000 00:05 3408      /dev/dri/card0
b19a0000-b19a8000 rw-s 157c88000 00:05 3408      /dev/dri/card0
b19a8000-b19b0000 rw-s 157c80000 00:05 3408      /dev/dri/card0
b19b0000-b19b8000 rw-s 157c78000 00:05 3408      /dev/dri/card0
b19b8000-b19c0000 rw-s 157c70000 00:05 3408      /dev/dri/card0
b19c0000-b19c8000 rw-s 157c68000 00:05 3408      /dev/dri/card0
b19c8000-b19d0000 rw-s 157d98000 00:05 3408      /dev/dri/card0
b19d0000-b19d8000 rw-s 157d90000 00:05 3408      /dev/dri/card0
b19d8000-b19e0000 rw-s 157d88000 00:05 3408      /dev/dri/card0
b19e0000-b19e8000 rw-s 157d80000 00:05 3408      /dev/dri/card0
b19e8000-b19f0000 rw-s 157d78000 00:05 3408      /dev/dri/card0
b19f0000-b19f8000 rw-s 157d70000 00:05 3408      /dev/dri/card0
b19f8000-b1a00000 rw-s 157d68000 00:05 3408      /dev/dri/card0
b1a00000-b1a08000 rw-s 157d60000 00:05 3408      /dev/dri/card0
b1a08000-b1a10000 rw-s 157d58000 00:05 3408      /dev/dri/card0
b1a10000-b1a18000 rw-s 157d50000 00:05 3408      /dev/dri/card0
b1a18000-b1a20000 rw-s 157d48000 00:05 3408      /dev/dri/card0
b1a20000-b1a28000 rw-s 157d40000 00:05 3408      /dev/dri/card0
b1a28000-b1a30000 rw-s 157d38000 00:05 3408      /dev/dri/card0
b1a30000-b1a38000 rw-s 157dc2000 00:05 3408      /dev/dri/card0
b1a38000-b1a40000 rw-s 15ac2e000 00:05 3408      /dev/dri/card0
b1a40000-b1a48000 rw-s 15b274000 00:05 3408      /dev/dri/card0
b1a48000-b1a50000 rw-s 158aac000 00:05 3408      /dev/dri/card0
b1a50000-b1a58000 rw-s 157d10000 00:05 3408      /dev/dri/card0
b1a58000-b1a60000 rw-s 157d08000 00:05 3408      /dev/dri/card0
b1a60000-b1a68000 rw-s 157d00000 00:05 3408      /dev/dri/card0
b1a68000-b1a70000 rw-s 157cf8000 00:05 3408      /dev/dri/card0
b1a70000-b1a78000 rw-s 157cf0000 00:05 3408      /dev/dri/card0
b1a78000-b1a80000 rw-s 157ce8000 00:05 3408      /dev/dri/card0
b1a80000-b1a88000 rw-s 157ce0000 00:05 3408      /dev/dri/card0
b1a88000-b1a90000 rw-s 157cd8000 00:05 3408      /dev/dri/card0
b1a90000-b1a98000 rw-s 157cd0000 00:05 3408      /dev/dri/card0
b1a98000-b1aa0000 rw-s 157cc8000 00:05 3408      /dev/dri/card0
b1aa0000-b1aa8000 rw-s 157f94000 00:05 3408      /dev/dri/card0
b1aa8000-b1ab0000 rw-s 15a9be000 00:05 3408      /dev/dri/card0
b1ab0000-b1ab8000 rw-s 15a9b6000 00:05 3408      /dev/dri/card0
b1ab8000-b1ac0000 rw-s 15ac9a000 00:05 3408      /dev/dri/card0
b1ac0000-b1ac8000 rw-s 1565b7000 00:05 3408      /dev/dri/card0
b1ac8000-b1ad0000 rw-s 157cb0000 00:05 3408      /dev/dri/card0
b1ad0000-b1ad8000 rw-s 157f7c000 00:05 3408      /dev/dri/card0
b1ad8000-b1ae0000 rw-s 157ca8000 00:05 3408      /dev/dri/card0
b1ae0000-b1ae8000 rw-s 157ca0000 00:05 3408      /dev/dri/card0
b1ae8000-b1af0000 rw-s 157c60000 00:05 3408      /dev/dri/card0
b1af0000-b1af8000 rw-s 157c58000 00:05 3408      /dev/dri/card0
b1af8000-b1b00000 rw-s 157c50000 00:05 3408      /dev/dri/card0
b1b00000-b1b08000 rw-s 157c48000 00:05 3408      /dev/dri/card0
b1b08000-b1b10000 rw-s 157c40000 00:05 3408      /dev/dri/card0
b1b10000-b1b18000 rw-s 157c38000 00:05 3408      /dev/dri/card0
b1b18000-b1b20000 rw-s 157c30000 00:05 3408      /dev/dri/card0
b1b20000-b1b28000 rw-s 157c28000 00:05 3408      /dev/dri/card0
b1b28000-b1b30000 rw-s 157c10000 00:05 3408      /dev/dri/card0
b1b30000-b1b38000 rw-s 157c08000 00:05 3408      /dev/dri/card0
b1b38000-b1b40000 rw-s 15b244000 00:05 3408      /dev/dri/card0
b1b40000-b1b48000 rw-s 15b23c000 00:05 3408      /dev/dri/card0
b1b48000-b1b50000 rw-s 1576ec000 00:05 3408      /dev/dri/card0
b1b50000-b1b58000 rw-s 157740000 00:05 3408      /dev/dri/card0
b1b58000-b1b60000 rw-s 157738000 00:05 3408      /dev/dri/card0
b1b60000-b1b68000 rw-s 157724000 00:05 3408      /dev/dri/card0
b1b68000-b1b70000 rw-s 157c00000 00:05 3408      /dev/dri/card0
b1b70000-b1b78000 rw-s 157bf8000 00:05 3408      /dev/dri/card0
b1b78000-b1b80000 rw-s 157bf0000 00:05 3408      /dev/dri/card0
b1b80000-b1b88000 rw-s 157be8000 00:05 3408      /dev/dri/card0
b1b88000-b1b90000 rw-s 157be0000 00:05 3408      /dev/dri/card0
b1b90000-b1b98000 rw-s 157bd8000 00:05 3408      /dev/dri/card0
b1b98000-b1ba0000 rw-s 157bb8000 00:05 3408      /dev/dri/card0
b1ba0000-b1ba8000 rw-s 157bb0000 00:05 3408      /dev/dri/card0
b1ba8000-b1bb0000 rw-s 15aef3000 00:05 3408      /dev/dri/card0
b1bb0000-b1bb8000 rw-s 15b07f000 00:05 3408      /dev/dri/card0
b1bb8000-b1bc0000 rw-s 157b98000 00:05 3408      /dev/dri/card0
b1bc0000-b1bc8000 rw-s 1598ac000 00:05 3408      /dev/dri/card0
b1bc8000-b1bd0000 rw-s 159846000 00:05 3408      /dev/dri/card0
b1bd0000-b1bd8000 rw-s 157b81000 00:05 3408      /dev/dri/card0
b1bd8000-b1be0000 rw-s 157b79000 00:05 3408      /dev/dri/card0
b1be0000-b1be8000 rw-s 157b71000 00:05 3408      /dev/dri/card0
b1be8000-b1bf0000 rw-s 157b68000 00:05 3408      /dev/dri/card0
b1bf0000-b1bf8000 rw-s 157b60000 00:05 3408      /dev/dri/card0
b1bf8000-b1c00000 rw-s 157b58000 00:05 3408      /dev/dri/card0
b1c00000-b1c08000 rw-s 157b50000 00:05 3408      /dev/dri/card0
b1c08000-b1c10000 rw-s 157b3a000 00:05 3408      /dev/dri/card0
b1c10000-b1c18000 rw-s 157b32000 00:05 3408      /dev/dri/card0
b1c18000-b1c20000 rw-s 157b2a000 00:05 3408      /dev/dri/card0
b1c20000-b1c28000 rw-s 157b22000 00:05 3408      /dev/dri/card0
b1c28000-b1c30000 rw-s 157b1a000 00:05 3408      /dev/dri/card0
b1c30000-b1c38000 rw-s 157b12000 00:05 3408      /dev/dri/card0
b1c38000-b1c40000 rw-s 157b48000 00:05 3408      /dev/dri/card0
b1c40000-b1c48000 rw-s 157b0a000 00:05 3408      /dev/dri/card0
b1c48000-b1c50000 rw-s 157b02000 00:05 3408      /dev/dri/card0
b1c50000-b1c58000 rw-s 157afa000 00:05 3408      /dev/dri/card0
b1c58000-b1c60000 rw-s 157af2000 00:05 3408      /dev/dri/card0
b1c60000-b1c68000 rw-s 157aea000 00:05 3408      /dev/dri/card0
b1c68000-b1c70000 rw-s 157ae2000 00:05 3408      /dev/dri/card0
b1c70000-b1c78000 rw-s 157ada000 00:05 3408      /dev/dri/card0
b1c78000-b1c80000 rw-s 157ad2000 00:05 3408      /dev/dri/card0
b1c80000-b1c88000 rw-s 157aca000 00:05 3408      /dev/dri/card0
b1c88000-b1c90000 rw-s 157ac2000 00:05 3408      /dev/dri/card0
b1c90000-b1c98000 rw-s 157aba000 00:05 3408      /dev/dri/card0
b1c98000-b1ca0000 rw-s 157ab2000 00:05 3408      /dev/dri/card0
b1ca0000-b1ca8000 rw-s 157aaa000 00:05 3408      /dev/dri/card0
b1ca8000-b1cb0000 rw-s 157aa2000 00:05 3408      /dev/dri/card0
b1cb0000-b1cb8000 rw-s 157a9a000 00:05 3408      /dev/dri/card0
b1cb8000-b1cc0000 rw-s 157a92000 00:05 3408      /dev/dri/card0
b1cc0000-b1cc8000 rw-s 157a8a000 00:05 3408      /dev/dri/card0
b1cc8000-b1cd0000 rw-s 157a82000 00:05 3408      /dev/dri/card0
b1cd0000-b1cd8000 rw-s 157a7a000 00:05 3408      /dev/dri/card0
b1cd8000-b1ce0000 rw-s 157a72000 00:05 3408      /dev/dri/card0
b1ce0000-b1ce8000 rw-s 157a6a000 00:05 3408      /dev/dri/card0
b1ce8000-b1cf0000 rw-s 157a62000 00:05 3408      /dev/dri/card0
b1cf0000-b1cf8000 rw-s 157a5a000 00:05 3408      /dev/dri/card0
b1cf8000-b1d00000 rw-s 157a22000 00:05 3408      /dev/dri/card0
b1d00000-b1d08000 rw-s 157a4a000 00:05 3408      /dev/dri/card0
b1d08000-b1d10000 rw-s 157a42000 00:05 3408      /dev/dri/card0
b1d10000-b1d18000 rw-s 157a3a000 00:05 3408      /dev/dri/card0
b1d18000-b1d20000 rw-s 157a32000 00:05 3408      /dev/dri/card0
b1d20000-b1d28000 rw-s 1579da000 00:05 3408      /dev/dri/card0
b1d28000-b1d30000 rw-s 1579a4000 00:05 3408      /dev/dri/card0
b1d30000-b1d38000 rw-s 159970000 00:05 3408      /dev/dri/card0
b1d38000-b1d40000 rw-s 1596ca000 00:05 3408      /dev/dri/card0
b1d40000-b1d48000 rw-s 159cce000 00:05 3408      /dev/dri/card0
b1d48000-b1d50000 rw-s 157994000 00:05 3408      /dev/dri/card0
b1d50000-b1d58000 rw-s 15798c000 00:05 3408      /dev/dri/card0
b1d58000-b1d60000 rw-s 157984000 00:05 3408      /dev/dri/card0
b1d60000-b1d68000 rw-s 15797c000 00:05 3408      /dev/dri/card0
b1d68000-b1d70000 rw-s 157a12000 00:05 3408      /dev/dri/card0
b1d70000-b1d78000 rw-s 157a0a000 00:05 3408      /dev/dri/card0
b1d78000-b1d80000 rw-s 157a02000 00:05 3408      /dev/dri/card0
b1d80000-b1d88000 rw-s 1579fa000 00:05 3408      /dev/dri/card0
b1d88000-b1d90000 rw-s 1579f2000 00:05 3408      /dev/dri/card0
b1d90000-b1d98000 rw-s 1579ea000 00:05 3408      /dev/dri/card0
b1d98000-b1da0000 rw-s 159549000 00:05 3408      /dev/dri/card0
b1da0000-b1da8000 rw-s 1579d2000 00:05 3408      /dev/dri/card0
b1da8000-b1db0000 rw-s 1579ca000 00:05 3408      /dev/dri/card0
b1db0000-b1db8000 rw-s 15928d000 00:05 3408      /dev/dri/card0
b1db8000-b1dc0000 rw-s 1579c2000 00:05 3408      /dev/dri/card0
b1dc0000-b1dc8000 rw-s 1579ba000 00:05 3408      /dev/dri/card0
b1dc8000-b1dd0000 rw-s 1579b2000 00:05 3408      /dev/dri/card0
b1dd0000-b1dd8000 rw-s 157974000 00:05 3408      /dev/dri/card0
b1dd8000-b1de0000 rw-s 15796c000 00:05 3408      /dev/dri/card0
b1de0000-b1de8000 rw-s 157964000 00:05 3408      /dev/dri/card0
b1de8000-b1df0000 rw-s 155fe6000 00:05 3408      /dev/dri/card0
b1df0000-b1df8000 rw-s 15795c000 00:05 3408      /dev/dri/card0
b1df8000-b1e00000 rw-s 157954000 00:05 3408      /dev/dri/card0
b1e00000-b1e08000 rw-s 15794c000 00:05 3408      /dev/dri/card0
b1e08000-b1e10000 rw-s 157944000 00:05 3408      /dev/dri/card0
b1e10000-b1e18000 rw-s 157934000 00:05 3408      /dev/dri/card0
b1e18000-b1e20000 rw-s 15792c000 00:05 3408      /dev/dri/card0
b1e20000-b1e28000 rw-s 157924000 00:05 3408      /dev/dri/card0
b1e28000-b1e30000 rw-s 15791c000 00:05 3408      /dev/dri/card0
b1e30000-b1e38000 rw-s 157914000 00:05 3408      /dev/dri/card0
b1e38000-b1e40000 rw-s 15790c000 00:05 3408      /dev/dri/card0
b1e40000-b1e48000 rw-s 157904000 00:05 3408      /dev/dri/card0
b1e48000-b1e50000 rw-s 1578fc000 00:05 3408      /dev/dri/card0
b1e50000-b1e58000 rw-s 1578f4000 00:05 3408      /dev/dri/card0
b1e58000-b1e60000 rw-s 1578ec000 00:05 3408      /dev/dri/card0
b1e60000-b1e68000 rw-s 1578e4000 00:05 3408      /dev/dri/card0
b1e68000-b1e70000 rw-s 1578dc000 00:05 3408      /dev/dri/card0
b1e70000-b1e78000 rw-s 1578d4000 00:05 3408      /dev/dri/card0
b1e78000-b1e80000 rw-s 1578cc000 00:05 3408      /dev/dri/card0
b1e80000-b1e88000 rw-s 1578c4000 00:05 3408      /dev/dri/card0
b1e88000-b1e90000 rw-s 1578bc000 00:05 3408      /dev/dri/card0
b1e90000-b1e98000 rw-s 1578b4000 00:05 3408      /dev/dri/card0
b1e98000-b1ea0000 rw-s 157846000 00:05 3408      /dev/dri/card0
b1ea0000-b1ea8000 rw-s 158773000 00:05 3408      /dev/dri/card0
b1ea8000-b1eb0000 rw-s 155f60000 00:05 3408      /dev/dri/card0
b1eb0000-b1eb8000 rw-s 155f58000 00:05 3408      /dev/dri/card0
b1eb8000-b1ec0000 rw-s 155f50000 00:05 3408      /dev/dri/card0
b1ec0000-b1ec8000 rw-s 15781e000 00:05 3408      /dev/dri/card0
b1ec8000-b1ed0000 rw-s 158f8f000 00:05 3408      /dev/dri/card0
b1ed0000-b1ed8000 rw-s 157fdc000 00:05 3408      /dev/dri/card0
b1ed8000-b1ee0000 rw-s 158a26000 00:05 3408      /dev/dri/card0
b1ee0000-b1ee8000 rw-s 159ecf000 00:05 3408      /dev/dri/card0
b1ee8000-b1ef0000 rw-s 159ec6000 00:05 3408      /dev/dri/card0
b1ef0000-b1ef8000 rw-s 15799c000 00:05 3408      /dev/dri/card0
b1ef8000-b1f00000 rw-s 15787c000 00:05 3408      /dev/dri/card0
b1f00000-b1f08000 rw-s 157874000 00:05 3408      /dev/dri/card0
b1f08000-b1f10000 rw-s 15786c000 00:05 3408      /dev/dri/card0
b1f10000-b1f18000 rw-s 157864000 00:05 3408      /dev/dri/card0
b1f18000-b1f20000 rw-s 15785c000 00:05 3408      /dev/dri/card0
b1f20000-b1f28000 rw-s 157854000 00:05 3408      /dev/dri/card0
b1f28000-b1f30000 rw-s 157816000 00:05 3408      /dev/dri/card0
b1f30000-b1f38000 rw-s 15780e000 00:05 3408      /dev/dri/card0
b1f38000-b1f40000 rw-s 157806000 00:05 3408      /dev/dri/card0
b1f40000-b1f48000 rw-s 1577fe000 00:05 3408      /dev/dri/card0
b1f48000-b1f50000 rw-s 158818000 00:05 3408      /dev/dri/card0
b1f50000-b1f58000 rw-s 1577ef000 00:05 3408      /dev/dri/card0
b1f58000-b1f60000 rw-s 1577e7000 00:05 3408      /dev/dri/card0
b1f60000-b1f68000 rw-s 1577de000 00:05 3408      /dev/dri/card0
b1f68000-b1f70000 rw-s 15771c000 00:05 3408      /dev/dri/card0
b1f70000-b1f78000 rw-s 1576ac000 00:05 3408      /dev/dri/card0
b1f78000-b1f80000 rw-s 1576a4000 00:05 3408      /dev/dri/card0
b1f80000-b1f88000 rw-s 15769c000 00:05 3408      /dev/dri/card0
b1f88000-b1f90000 rw-s 159391000 00:05 3408      /dev/dri/card0
b1f90000-b1f98000 rw-s 15768c000 00:05 3408      /dev/dri/card0
b1f98000-b1fa0000 rw-s 157684000 00:05 3408      /dev/dri/card0
b1fa0000-b1fa8000 rw-s 15767c000 00:05 3408      /dev/dri/card0
b1fa8000-b1fb0000 rw-s 157674000 00:05 3408      /dev/dri/card0
b1fb0000-b1fb8000 rw-s 157bd0000 00:05 3408      /dev/dri/card0
b1fb8000-b1fc0000 rw-s 157bc8000 00:05 3408      /dev/dri/card0
b1fc0000-b1fc8000 rw-s 1576c4000 00:05 3408      /dev/dri/card0
b1fc8000-b1fd0000 rw-s 15553d000 00:05 3408      /dev/dri/card0
b1fd0000-b1fd8000 rw-s 15576f000 00:05 3408      /dev/dri/card0
b1fd8000-b1fe0000 rw-s 157644000 00:05 3408      /dev/dri/card0
b1fe0000-b1fe8000 rw-s 15765c000 00:05 3408      /dev/dri/card0
b1fe8000-b1ff0000 rw-s 157634000 00:05 3408      /dev/dri/card0
b1ff0000-b1ff8000 rw-s 15762c000 00:05 3408      /dev/dri/card0
b1ff8000-b2000000 rw-s 157624000 00:05 3408      /dev/dri/card0
b2000000-b2008000 rw-s 15761c000 00:05 3408      /dev/dri/card0
b2008000-b2010000 rw-s 157614000 00:05 3408      /dev/dri/card0
b2010000-b2018000 rw-s 15760c000 00:05 3408      /dev/dri/card0
b2018000-b2020000 rw-s 157604000 00:05 3408      /dev/dri/card0
b2020000-b2028000 rw-s 1575fc000 00:05 3408      /dev/dri/card0
b2028000-b2030000 rw-s 1575f4000 00:05 3408      /dev/dri/card0
b2030000-b2038000 rw-s 1575ec000 00:05 3408      /dev/dri/card0
b2038000-b2040000 rw-s 1575e4000 00:05 3408      /dev/dri/card0
b2040000-b2048000 rw-s 1575dc000 00:05 3408      /dev/dri/card0
b2048000-b2050000 rw-s 1575d4000 00:05 3408      /dev/dri/card0
b2050000-b2058000 rw-s 1575cc000 00:05 3408      /dev/dri/card0
b2058000-b2060000 rw-s 1575c4000 00:05 3408      /dev/dri/card0
b2060000-b2068000 rw-s 1575bc000 00:05 3408      /dev/dri/card0
b2068000-b2070000 rw-s 1575b4000 00:05 3408      /dev/dri/card0
b2070000-b2078000 rw-s 1575ac000 00:05 3408      /dev/dri/card0
b2078000-b2080000 rw-s 1575a4000 00:05 3408      /dev/dri/card0
b2080000-b2088000 rw-s 15759c000 00:05 3408      /dev/dri/card0
b2088000-b2090000 rw-s 157594000 00:05 3408      /dev/dri/card0
b2090000-b2098000 rw-s 15758c000 00:05 3408      /dev/dri/card0
b2098000-b20a0000 rw-s 157584000 00:05 3408      /dev/dri/card0
b20a0000-b20a8000 rw-s 15757c000 00:05 3408      /dev/dri/card0
b20a8000-b20b0000 rw-s 157574000 00:05 3408      /dev/dri/card0
b20b0000-b20b8000 rw-s 15756c000 00:05 3408      /dev/dri/card0
b20b8000-b20c0000 rw-s 157564000 00:05 3408      /dev/dri/card0
b20c0000-b20c8000 rw-s 15755c000 00:05 3408      /dev/dri/card0
b20c8000-b20d0000 rw-s 157554000 00:05 3408      /dev/dri/card0
b20d0000-b20d8000 rw-s 15754c000 00:05 3408      /dev/dri/card0
b20d8000-b20e0000 rw-s 157544000 00:05 3408      /dev/dri/card0
b20e0000-b20e8000 rw-s 15753c000 00:05 3408      /dev/dri/card0
b20e8000-b20f0000 rw-s 157534000 00:05 3408      /dev/dri/card0
b20f0000-b20f8000 rw-s 15752c000 00:05 3408      /dev/dri/card0
b20f8000-b2100000 rw-s 157524000 00:05 3408      /dev/dri/card0
b2100000-b2108000 rw-s 15751c000 00:05 3408      /dev/dri/card0
b2108000-b2110000 rw-s 157514000 00:05 3408      /dev/dri/card0
b2110000-b2118000 rw-s 15750c000 00:05 3408      /dev/dri/card0
b2118000-b2120000 rw-s 157504000 00:05 3408      /dev/dri/card0
b2120000-b2128000 rw-s 156aa6000 00:05 3408      /dev/dri/card0
b2128000-b2130000 rw-s 156a9e000 00:05 3408      /dev/dri/card0
b2130000-b2138000 rw-s 156a96000 00:05 3408      /dev/dri/card0
b2138000-b2140000 rw-s 156a8e000 00:05 3408      /dev/dri/card0
b2140000-b2148000 rw-s 154465000 00:05 3408      /dev/dri/card0
b2148000-b2150000 rw-s 15445d000 00:05 3408      /dev/dri/card0
b2150000-b2158000 rw-s 154455000 00:05 3408      /dev/dri/card0
b2158000-b2160000 rw-s 15444d000 00:05 3408      /dev/dri/card0
b2160000-b2168000 rw-s 154df7000 00:05 3408      /dev/dri/card0
b2168000-b2170000 rw-s 154def000 00:05 3408      /dev/dri/card0
b2170000-b2178000 rw-s 154de6000 00:05 3408      /dev/dri/card0
b2178000-b2180000 rw-s 15959f000 00:05 3408      /dev/dri/card0
b2180000-b2190000 rw-s 15a538000 00:05 3408      /dev/dri/card0
b2190000-b2198000 rw-s 15ac14000 00:05 3408      /dev/dri/card0
b2198000-b21a0000 rw-s 154dbe000 00:05 3408      /dev/dri/card0
b21a0000-b21a8000 rw-s 154db6000 00:05 3408      /dev/dri/card0
b21a8000-b21b0000 rw-s 154dae000 00:05 3408      /dev/dri/card0
b21b0000-b21b8000 rw-s 154da6000 00:05 3408      /dev/dri/card0
b21b8000-b21c0000 rw-s 154d9e000 00:05 3408      /dev/dri/card0
b21c0000-b21c8000 rw-s 154d96000 00:05 3408      /dev/dri/card0
b21c8000-b21d0000 rw-s 154d8e000 00:05 3408      /dev/dri/card0
b21d0000-b21d8000 rw-s 154d86000 00:05 3408      /dev/dri/card0
b21d8000-b21e0000 rw-s 154d61000 00:05 3408      /dev/dri/card0
b21e0000-b21e8000 rw-s 154d59000 00:05 3408      /dev/dri/card0
b21e8000-b21f0000 rw-s 154d51000 00:05 3408      /dev/dri/card0
b21f0000-b21f8000 rw-s 154d49000 00:05 3408      /dev/dri/card0
b21f8000-b2200000 rw-s 154d40000 00:05 3408      /dev/dri/card0
b2200000-b22ae000 rw-p 00000000 00:00 0 
b22ae000-b2300000 ---p 00000000 00:00 0 
b2305000-b230d000 rw-s 154d38000 00:05 3408      /dev/dri/card0
b230d000-b2315000 rw-s 154d7e000 00:05 3408      /dev/dri/card0
b2315000-b231d000 rw-s 154d76000 00:05 3408      /dev/dri/card0
b231d000-b2325000 rw-s 157884000 00:05 3408      /dev/dri/card0
b2325000-b232d000 rw-s 154d30000 00:05 3408      /dev/dri/card0
b232d000-b2335000 rw-s 154d28000 00:05 3408      /dev/dri/card0
b2335000-b233d000 rw-s 154d20000 00:05 3408      /dev/dri/card0
b233d000-b2345000 rw-s 154d17000 00:05 3408      /dev/dri/card0
b2345000-b234d000 rw-s 154d0f000 00:05 3408      /dev/dri/card0
b234d000-b2355000 rw-s 154d07000 00:05 3408      /dev/dri/card0
b2355000-b235d000 rw-s 154cff000 00:05 3408      /dev/dri/card0
b235d000-b2365000 rw-s 154cf7000 00:05 3408      /dev/dri/card0
b2365000-b236d000 rw-s 154cef000 00:05 3408      /dev/dri/card0
b236d000-b2375000 rw-s 154ce7000 00:05 3408      /dev/dri/card0
b2375000-b237d000 rw-s 154cdf000 00:05 3408      /dev/dri/card0
b237d000-b2385000 rw-s 154cd7000 00:05 3408      /dev/dri/card0
b2385000-b238d000 rw-s 154ccf000 00:05 3408      /dev/dri/card0
b238d000-b2395000 rw-s 154cc7000 00:05 3408      /dev/dri/card0
b2395000-b239d000 rw-s 154cbf000 00:05 3408      /dev/dri/card0
b239d000-b23a5000 rw-s 154cb7000 00:05 3408      /dev/dri/card0
b23a5000-b23ad000 rw-s 154cae000 00:05 3408      /dev/dri/card0
b23ad000-b23b5000 rw-s 154ca6000 00:05 3408      /dev/dri/card0
b23b5000-b23bd000 rw-s 154c9e000 00:05 3408      /dev/dri/card0
b23bd000-b23c5000 rw-s 154c96000 00:05 3408      /dev/dri/card0
b23c5000-b23cd000 rw-s 154c8e000 00:05 3408      /dev/dri/card0
b23cd000-b23d5000 rw-s 154c86000 00:05 3408      /dev/dri/card0
b23d5000-b23dd000 rw-s 154c7e000 00:05 3408      /dev/dri/card0
b23dd000-b23e5000 rw-s 154c76000 00:05 3408      /dev/dri/card0
b23e5000-b23ed000 rw-s 154c6e000 00:05 3408      /dev/dri/card0
b23ed000-b23f5000 rw-s 1555ab000 00:05 3408      /dev/dri/card0
b23f5000-b23fd000 rw-s 155597000 00:05 3408      /dev/dri/card0
b23fd000-b2405000 rw-s 15558e000 00:05 3408      /dev/dri/card0
b2405000-b240d000 rw-s 155585000 00:05 3408      /dev/dri/card0
b240d000-b2415000 rw-s 15557d000 00:05 3408      /dev/dri/card0
b2415000-b241d000 rw-s 155575000 00:05 3408      /dev/dri/card0
b241d000-b2425000 rw-s 15556d000 00:05 3408      /dev/dri/card0
b2425000-b242d000 rw-s 1555a3000 00:05 3408      /dev/dri/card0
b242d000-b2435000 rw-s 155565000 00:05 3408      /dev/dri/card0
b2435000-b243d000 rw-s 15555d000 00:05 3408      /dev/dri/card0
b243d000-b2445000 rw-s 155555000 00:05 3408      /dev/dri/card0
b2445000-b244d000 rw-s 15554d000 00:05 3408      /dev/dri/card0
b244d000-b2455000 rw-s 155545000 00:05 3408      /dev/dri/card0
b2455000-b245d000 rw-s 1585a4000 00:05 3408      /dev/dri/card0
b245d000-b2465000 rw-s 155535000 00:05 3408      /dev/dri/card0
b2465000-b246d000 rw-s 15552d000 00:05 3408      /dev/dri/card0
b246d000-b2475000 rw-s 155525000 00:05 3408      /dev/dri/card0
b2475000-b247d000 rw-s 15551d000 00:05 3408      /dev/dri/card0
b247d000-b2485000 rw-s 155515000 00:05 3408      /dev/dri/card0
b2485000-b248d000 rw-s 15550d000 00:05 3408      /dev/dri/card0
b248d000-b2495000 rw-s 155505000 00:05 3408      /dev/dri/card0
b2495000-b249d000 rw-s 1554fd000 00:05 3408      /dev/dri/card0
b249d000-b24a5000 rw-s 1554f5000 00:05 3408      /dev/dri/card0
b24a5000-b24ad000 rw-s 1554ed000 00:05 3408      /dev/dri/card0
b24ad000-b24b5000 rw-s 1554e5000 00:05 3408      /dev/dri/card0
b24b5000-b24bd000 rw-s 1554dd000 00:05 3408      /dev/dri/card0
b24bd000-b24c5000 rw-s 1554d5000 00:05 3408      /dev/dri/card0
b24c5000-b24cd000 rw-s 1554cd000 00:05 3408      /dev/dri/card0
b24cd000-b24d5000 rw-s 1554c5000 00:05 3408      /dev/dri/card0
b24d5000-b24dd000 rw-s 1554bd000 00:05 3408      /dev/dri/card0
b24dd000-b24e5000 rw-s 1554b5000 00:05 3408      /dev/dri/card0
b24e5000-b24ed000 rw-s 1554ad000 00:05 3408      /dev/dri/card0
b24ed000-b24f5000 rw-s 15527a000 00:05 3408      /dev/dri/card0
b24f5000-b24fd000 rw-s 155272000 00:05 3408      /dev/dri/card0
b24fd000-b2505000 rw-s 1554a5000 00:05 3408      /dev/dri/card0
b2505000-b250d000 rw-s 15548d000 00:05 3408      /dev/dri/card0
b250d000-b2515000 rw-s 155485000 00:05 3408      /dev/dri/card0
b2515000-b251d000 rw-s 15547d000 00:05 3408      /dev/dri/card0
b251d000-b2525000 rw-s 155475000 00:05 3408      /dev/dri/card0
b2525000-b252d000 rw-s 15546d000 00:05 3408      /dev/dri/card0
b252d000-b2535000 rw-s 155465000 00:05 3408      /dev/dri/card0
b2535000-b253d000 rw-s 15545d000 00:05 3408      /dev/dri/card0
b253d000-b2545000 rw-s 155455000 00:05 3408      /dev/dri/card0
b2545000-b254d000 rw-s 15544d000 00:05 3408      /dev/dri/card0
b254d000-b2555000 rw-s 155445000 00:05 3408      /dev/dri/card0
b2555000-b255d000 rw-s 1589ee000 00:05 3408      /dev/dri/card0
b255d000-b2565000 rw-s 15543d000 00:05 3408      /dev/dri/card0
b2565000-b256d000 rw-s 155434000 00:05 3408      /dev/dri/card0
b256d000-b2575000 rw-s 15542c000 00:05 3408      /dev/dri/card0
b2575000-b257d000 rw-s 155424000 00:05 3408      /dev/dri/card0
b257d000-b2585000 rw-s 15541c000 00:05 3408      /dev/dri/card0
b2585000-b258d000 rw-s 15540c000 00:05 3408      /dev/dri/card0
b258d000-b2595000 rw-s 155404000 00:05 3408      /dev/dri/card0
b2595000-b259d000 rw-s 1553fc000 00:05 3408      /dev/dri/card0
b259d000-b25a5000 rw-s 1553f4000 00:05 3408      /dev/dri/card0
b25a5000-b25ad000 rw-s 1553ec000 00:05 3408      /dev/dri/card0
b25ad000-b25b5000 rw-s 1553e4000 00:05 3408      /dev/dri/card0
b25b5000-b25bd000 rw-s 1553dc000 00:05 3408      /dev/dri/card0
b25bd000-b25c5000 rw-s 1553d4000 00:05 3408      /dev/dri/card0
b25c5000-b25cd000 rw-s 1553cc000 00:05 3408      /dev/dri/card0
b25cd000-b25d5000 rw-s 1553c4000 00:05 3408      /dev/dri/card0
b25d5000-b25dd000 rw-s 1553bc000 00:05 3408      /dev/dri/card0
b25dd000-b25e5000 rw-s 1553b4000 00:05 3408      /dev/dri/card0
b25e5000-b25ed000 rw-s 1553ac000 00:05 3408      /dev/dri/card0
b25ed000-b25f5000 rw-s 1553a4000 00:05 3408      /dev/dri/card0
b25f5000-b25fd000 rw-s 15539c000 00:05 3408      /dev/dri/card0
b25fd000-b2605000 rw-s 155394000 00:05 3408      /dev/dri/card0
b2605000-b260d000 rw-s 15538c000 00:05 3408      /dev/dri/card0
b260d000-b2615000 rw-s 155384000 00:05 3408      /dev/dri/card0
b2615000-b261d000 rw-s 15537c000 00:05 3408      /dev/dri/card0
b261d000-b2625000 rw-s 155374000 00:05 3408      /dev/dri/card0
b2625000-b262d000 rw-s 15536c000 00:05 3408      /dev/dri/card0
b262d000-b2635000 rw-s 155364000 00:05 3408      /dev/dri/card0
b2635000-b263d000 rw-s 15535c000 00:05 3408      /dev/dri/card0
b263d000-b2645000 rw-s 155354000 00:05 3408      /dev/dri/card0
b2645000-b264d000 rw-s 15534c000 00:05 3408      /dev/dri/card0
b264d000-b2655000 rw-s 155344000 00:05 3408      /dev/dri/card0
b2655000-b265d000 rw-s 15533c000 00:05 3408      /dev/dri/card0
b265d000-b2665000 rw-s 155334000 00:05 3408      /dev/dri/card0
b2665000-b266d000 rw-s 15532c000 00:05 3408      /dev/dri/card0
b266d000-b2675000 rw-s 155324000 00:05 3408      /dev/dri/card0
b2675000-b267d000 rw-s 15531c000 00:05 3408      /dev/dri/card0
b267d000-b2685000 rw-s 155314000 00:05 3408      /dev/dri/card0
b2685000-b268d000 rw-s 15530c000 00:05 3408      /dev/dri/card0
b268d000-b2695000 rw-s 155304000 00:05 3408      /dev/dri/card0
b2695000-b269d000 rw-s 15836c000 00:05 3408      /dev/dri/card0
b269d000-b26a5000 rw-s 1552fa000 00:05 3408      /dev/dri/card0
b26a5000-b26ad000 rw-s 15834a000 00:05 3408      /dev/dri/card0
b26ad000-b26b5000 rw-s 158342000 00:05 3408      /dev/dri/card0
b26b5000-b26bd000 rw-s 15833a000 00:05 3408      /dev/dri/card0
b26bd000-b26c5000 rw-s 158332000 00:05 3408      /dev/dri/card0
b26c5000-b26cd000 rw-s 1590a0000 00:05 3408      /dev/dri/card0
b26cd000-b26d5000 rw-s 159360000 00:05 3408      /dev/dri/card0
b26d5000-b26dd000 rw-s 1552bc000 00:05 3408      /dev/dri/card0
b26dd000-b26e5000 rw-s 1552b4000 00:05 3408      /dev/dri/card0
b26e5000-b26ed000 rw-s 15a95e000 00:05 3408      /dev/dri/card0
b26ed000-b26f5000 rw-s 15a790000 00:05 3408      /dev/dri/card0
b26f5000-b26fd000 rw-s 158fc6000 00:05 3408      /dev/dri/card0
b26fd000-b2705000 rw-s 155294000 00:05 3408      /dev/dri/card0
b2705000-b270d000 rw-s 15528c000 00:05 3408      /dev/dri/card0
b270d000-b2715000 rw-s 155284000 00:05 3408      /dev/dri/card0
b2715000-b271d000 rw-s 158f3e000 00:05 3408      /dev/dri/card0
b271d000-b2725000 rw-s 155496000 00:05 3408      /dev/dri/card0
b2725000-b272d000 rw-s 1565c7000 00:05 3408      /dev/dri/card0
b272d000-b2735000 rw-s 158524000 00:05 3408      /dev/dri/card0
b2735000-b273d000 rw-s 15a0b8000 00:05 3408      /dev/dri/card0
b273d000-b2745000 rw-s 159c96000 00:05 3408      /dev/dri/card0
b2745000-b274d000 rw-s 1565a7000 00:05 3408      /dev/dri/card0
b274d000-b2755000 rw-s 153f85000 00:05 3408      /dev/dri/card0
b2755000-b275d000 rw-s 153f7d000 00:05 3408      /dev/dri/card0
b275d000-b2765000 rw-s 159379000 00:05 3408      /dev/dri/card0
b2765000-b276d000 rw-s 15659f000 00:05 3408      /dev/dri/card0
b276d000-b2775000 rw-s 156597000 00:05 3408      /dev/dri/card0
b2775000-b277d000 rw-s 15658f000 00:05 3408      /dev/dri/card0
b277d000-b2785000 rw-s 153f6c000 00:05 3408      /dev/dri/card0
b2785000-b278d000 rw-s 1587e1000 00:05 3408      /dev/dri/card0
b278d000-b2795000 rw-s 153f64000 00:05 3408      /dev/dri/card0
b2795000-b279d000 rw-s 1543cb000 00:05 3408      /dev/dri/card0
b279d000-b27a5000 rw-s 1543c3000 00:05 3408      /dev/dri/card0
b27a5000-b27ad000 rw-s 1543dd000 00:05 3408      /dev/dri/card0
b27ad000-b27b5000 rw-s 1543d5000 00:05 3408      /dev/dri/card0
b27b5000-b27bd000 rw-s 154428000 00:05 3408      /dev/dri/card0
b27bd000-b27c5000 rw-s 154420000 00:05 3408      /dev/dri/card0
b27c5000-b27cd000 rw-s 15b61c000 00:05 3408      /dev/dri/card0
b27cd000-b27d5000 rw-s 159ebe000 00:05 3408      /dev/dri/card0
b27d5000-b27dd000 rw-s 158eef000 00:05 3408      /dev/dri/card0
b27dd000-b27e5000 rw-s 158ee7000 00:05 3408      /dev/dri/card0
b27e5000-b27ed000 rw-s 158edf000 00:05 3408      /dev/dri/card0
b27ed000-b27f5000 rw-s 158ed7000 00:05 3408      /dev/dri/card0
b27f5000-b27fd000 rw-s 158ecf000 00:05 3408      /dev/dri/card0
b27fd000-b2805000 rw-s 15a069000 00:05 3408      /dev/dri/card0
b2805000-b280d000 rw-s 15a63e000 00:05 3408      /dev/dri/card0
b280d000-b2810000 rw-s 153c50000 00:05 3408      /dev/dri/card0
b2810000-b2818000 rw-s 153c48000 00:05 3408      /dev/dri/card0
b2818000-b2820000 rw-s 153c40000 00:05 3408      /dev/dri/card0
b2820000-b2828000 rw-s 153c38000 00:05 3408      /dev/dri/card0
b2828000-b2830000 rw-s 153c30000 00:05 3408      /dev/dri/card0
b2830000-b2838000 rw-s 15443e000 00:05 3408      /dev/dri/card0
b2838000-b2840000 rw-s 153c66000 00:05 3408      /dev/dri/card0
b2840000-b2848000 rw-s 153c28000 00:05 3408      /dev/dri/card0
b2848000-b2850000 rw-s 153c20000 00:05 3408      /dev/dri/card0
b2850000-b2858000 rw-s 153c18000 00:05 3408      /dev/dri/card0
b2858000-b2860000 rw-s 153c10000 00:05 3408      /dev/dri/card0
b2860000-b2868000 rw-s 153c08000 00:05 3408      /dev/dri/card0
b2868000-b2870000 rw-s 153c00000 00:05 3408      /dev/dri/card0
b2870000-b2878000 rw-s 153bf8000 00:05 3408      /dev/dri/card0
b2878000-b2880000 rw-s 153bf0000 00:05 3408      /dev/dri/card0
b2880000-b2888000 rw-s 15a0e8000 00:05 3408      /dev/dri/card0
b2888000-b2890000 rw-s 15a0e0000 00:05 3408      /dev/dri/card0
b2890000-b2898000 rw-s 153bd8000 00:05 3408      /dev/dri/card0
b2898000-b28a0000 rw-s 153bd0000 00:05 3408      /dev/dri/card0
b28a0000-b28a8000 rw-s 153bc8000 00:05 3408      /dev/dri/card0
b28a8000-b28b0000 rw-s 158d88000 00:05 3408      /dev/dri/card0
b28b0000-b28b8000 rw-s 158d80000 00:05 3408      /dev/dri/card0
b28b8000-b28c0000 rw-s 158d0b000 00:05 3408      /dev/dri/card0
b28c0000-b28c8000 rw-s 153cd7000 00:05 3408      /dev/dri/card0
b28c8000-b28d0000 rw-s 153d0a000 00:05 3408      /dev/dri/card0
b28d0000-b28d8000 rw-s 153d02000 00:05 3408      /dev/dri/card0
b28d8000-b28e0000 rw-s 153cc2000 00:05 3408      /dev/dri/card0
b28e0000-b28e8000 rw-s 15448f000 00:05 3408      /dev/dri/card0
b28e8000-b28f0000 rw-s 154555000 00:05 3408      /dev/dri/card0
b28f0000-b28f8000 rw-s 154566000 00:05 3408      /dev/dri/card0
b28f8000-b2900000 rw-s 15457f000 00:05 3408      /dev/dri/card0
b2900000-b2908000 rw-s 156080000 00:05 3408      /dev/dri/card0
b2908000-b2910000 rw-s 156078000 00:05 3408      /dev/dri/card0
b2910000-b2918000 rw-s 15606f000 00:05 3408      /dev/dri/card0
b2918000-b2920000 rw-s 156067000 00:05 3408      /dev/dri/card0
b2920000-b2928000 rw-s 15605f000 00:05 3408      /dev/dri/card0
b2928000-b2930000 rw-s 156057000 00:05 3408      /dev/dri/card0
b2930000-b2938000 rw-s 154577000 00:05 3408      /dev/dri/card0
b2938000-b2940000 rw-s 15a865000 00:05 3408      /dev/dri/card0
b2940000-b2948000 rw-s 15b1d4000 00:05 3408      /dev/dri/card0
b2948000-b2950000 rw-s 15b1b4000 00:05 3408      /dev/dri/card0
b2950000-b2958000 rw-s 15a85d000 00:05 3408      /dev/dri/card0
b2958000-b2960000 rw-s 15a855000 00:05 3408      /dev/dri/card0
b2960000-b2968000 rw-s 15b364000 00:05 3408      /dev/dri/card0
b2968000-b2970000 rw-s 15b35c000 00:05 3408      /dev/dri/card0
b2970000-b2978000 rw-s 15b00e000 00:05 3408      /dev/dri/card0
b2978000-b2980000 rw-s 15b006000 00:05 3408      /dev/dri/card0
b2980000-b2988000 rw-s 15604e000 00:05 3408      /dev/dri/card0
b2988000-b2990000 rw-s 156046000 00:05 3408      /dev/dri/card0
b2990000-b2998000 rw-s 15603e000 00:05 3408      /dev/dri/card0
b2998000-b29a0000 rw-s 156036000 00:05 3408      /dev/dri/card0
b29a0000-b29a8000 rw-s 15602e000 00:05 3408      /dev/dri/card0
b29a8000-b29b0000 rw-s 156026000 00:05 3408      /dev/dri/card0
b29b0000-b29b8000 rw-s 15601e000 00:05 3408      /dev/dri/card0
b29b8000-b29c0000 rw-s 156016000 00:05 3408      /dev/dri/card0
b29c0000-b29c8000 rw-s 15600e000 00:05 3408      /dev/dri/card0
b29c8000-b29d0000 rw-s 156006000 00:05 3408      /dev/dri/card0
b29d0000-b29d8000 rw-s 155ffe000 00:05 3408      /dev/dri/card0
b29d8000-b29e0000 rw-s 155ff6000 00:05 3408      /dev/dri/card0
b29e0000-b29e8000 rw-s 155fee000 00:05 3408      /dev/dri/card0
b29e8000-b29f0000 rw-s 15793c000 00:05 3408      /dev/dri/card0
b29f0000-b29f8000 rw-s 155fde000 00:05 3408      /dev/dri/card0
b29f8000-b2a00000 rw-s 155fd6000 00:05 3408      /dev/dri/card0
b2a00000-b2a08000 rw-s 155fce000 00:05 3408      /dev/dri/card0
b2a08000-b2a10000 rw-s 155fc6000 00:05 3408      /dev/dri/card0
b2a10000-b2a18000 rw-s 155fbe000 00:05 3408      /dev/dri/card0
b2a18000-b2a20000 rw-s 155fb6000 00:05 3408      /dev/dri/card0
b2a20000-b2a28000 rw-s 155fae000 00:05 3408      /dev/dri/card0
b2a28000-b2a30000 rw-s 155fa6000 00:05 3408      /dev/dri/card0
b2a30000-b2a38000 rw-s 155f9e000 00:05 3408      /dev/dri/card0
b2a38000-b2a40000 rw-s 155f96000 00:05 3408      /dev/dri/card0
b2a40000-b2a48000 rw-s 155f8e000 00:05 3408      /dev/dri/card0
b2a48000-b2a50000 rw-s 155f86000 00:05 3408      /dev/dri/card0
b2a50000-b2a58000 rw-s 155f7e000 00:05 3408      /dev/dri/card0
b2a58000-b2a60000 rw-s 155f76000 00:05 3408      /dev/dri/card0
b2a60000-b2a68000 rw-s 155f6e000 00:05 3408      /dev/dri/card0
b2a68000-b2a70000 rw-s 155f48000 00:05 3408      /dev/dri/card0
b2a70000-b2a78000 rw-s 155f40000 00:05 3408      /dev/dri/card0
b2a78000-b2a80000 rw-s 15783e000 00:05 3408      /dev/dri/card0
b2a80000-b2a88000 rw-s 157836000 00:05 3408      /dev/dri/card0
b2a88000-b2a90000 rw-s 15782e000 00:05 3408      /dev/dri/card0
b2a90000-b2a98000 rw-s 157826000 00:05 3408      /dev/dri/card0
b2a98000-b2aa0000 rw-s 155f38000 00:05 3408      /dev/dri/card0
b2aa0000-b2aa8000 rw-s 155f30000 00:05 3408      /dev/dri/card0
b2aa8000-b2ab0000 rw-s 155f28000 00:05 3408      /dev/dri/card0
b2ab0000-b2ab8000 rw-s 155f1f000 00:05 3408      /dev/dri/card0
b2ab8000-b2ac0000 rw-s 155f17000 00:05 3408      /dev/dri/card0
b2ac0000-b2ac8000 rw-s 155f0f000 00:05 3408      /dev/dri/card0
b2ac8000-b2ad0000 rw-s 155f06000 00:05 3408      /dev/dri/card0
b2ad0000-b2ad8000 rw-s 155efe000 00:05 3408      /dev/dri/card0
b2ad8000-b2ae0000 rw-s 155ef6000 00:05 3408      /dev/dri/card0
b2ae0000-b2ae8000 rw-s 155eee000 00:05 3408      /dev/dri/card0
b2ae8000-b2af0000 rw-s 155ee6000 00:05 3408      /dev/dri/card0
b2af0000-b2af8000 rw-s 155ede000 00:05 3408      /dev/dri/card0
b2af8000-b2b00000 rw-s 155ed6000 00:05 3408      /dev/dri/card0
b2b00000-b2b08000 rw-s 155ece000 00:05 3408      /dev/dri/card0
b2b08000-b2b10000 rw-s 155ec6000 00:05 3408      /dev/dri/card0
b2b10000-b2b18000 rw-s 155ebe000 00:05 3408      /dev/dri/card0
b2b18000-b2b20000 rw-s 155eb6000 00:05 3408      /dev/dri/card0
b2b20000-b2b28000 rw-s 155eae000 00:05 3408      /dev/dri/card0
b2b28000-b2b30000 rw-s 155ea6000 00:05 3408      /dev/dri/card0
b2b30000-b2b38000 rw-s 155e9e000 00:05 3408      /dev/dri/card0
b2b38000-b2b40000 rw-s 155e96000 00:05 3408      /dev/dri/card0
b2b40000-b2b48000 rw-s 155e8e000 00:05 3408      /dev/dri/card0
b2b48000-b2b50000 rw-s 155e86000 00:05 3408      /dev/dri/card0
b2b50000-b2b58000 rw-s 1595f4000 00:05 3408      /dev/dri/card0
b2b58000-b2b60000 rw-s 15a9ef000 00:05 3408      /dev/dri/card0
b2b60000-b2b68000 rw-s 155e6f000 00:05 3408      /dev/dri/card0
b2b68000-b2b70000 rw-s 155e66000 00:05 3408      /dev/dri/card0
b2b70000-b2b78000 rw-s 155e41000 00:05 3408      /dev/dri/card0
b2b78000-b2b80000 rw-s 155e39000 00:05 3408      /dev/dri/card0
b2b80000-b2b88000 rw-s 155e31000 00:05 3408      /dev/dri/card0
b2b88000-b2b90000 rw-s 155e29000 00:05 3408      /dev/dri/card0
b2b90000-b2b98000 rw-s 155e21000 00:05 3408      /dev/dri/card0
b2b98000-b2ba0000 rw-s 155e19000 00:05 3408      /dev/dri/card0
b2ba0000-b2ba8000 rw-s 155e5e000 00:05 3408      /dev/dri/card0
b2ba8000-b2bb0000 rw-s 155e56000 00:05 3408      /dev/dri/card0
b2bb0000-b2bb8000 rw-s 155e4e000 00:05 3408      /dev/dri/card0
b2bb8000-b2bc0000 rw-s 155e10000 00:05 3408      /dev/dri/card0
b2bc0000-b2bc8000 rw-s 155e08000 00:05 3408      /dev/dri/card0
b2bc8000-b2bd0000 rw-s 155e00000 00:05 3408      /dev/dri/card0
b2bd0000-b2bd8000 rw-s 155df8000 00:05 3408      /dev/dri/card0
b2bd8000-b2be0000 rw-s 155df0000 00:05 3408      /dev/dri/card0
b2be0000-b2be8000 rw-s 155de8000 00:05 3408      /dev/dri/card0
b2be8000-b2bf0000 rw-s 155de0000 00:05 3408      /dev/dri/card0
b2bf0000-b2bf8000 rw-s 155dd8000 00:05 3408      /dev/dri/card0
b2bf8000-b2c00000 rw-s 155dd0000 00:05 3408      /dev/dri/card0
b2c00000-b2c08000 rw-s 155dc8000 00:05 3408      /dev/dri/card0
b2c08000-b2c10000 rw-s 155dc0000 00:05 3408      /dev/dri/card0
b2c10000-b2c18000 rw-s 155db8000 00:05 3408      /dev/dri/card0
b2c18000-b2c20000 rw-s 155db0000 00:05 3408      /dev/dri/card0
b2c20000-b2c28000 rw-s 155da8000 00:05 3408      /dev/dri/card0
b2c28000-b2c30000 rw-s 155da0000 00:05 3408      /dev/dri/card0
b2c30000-b2c38000 rw-s 155d98000 00:05 3408      /dev/dri/card0
b2c38000-b2c40000 rw-s 155a5c000 00:05 3408      /dev/dri/card0
b2c40000-b2c48000 rw-s 155d90000 00:05 3408      /dev/dri/card0
b2c48000-b2c50000 rw-s 155d88000 00:05 3408      /dev/dri/card0
b2c50000-b2c58000 rw-s 15b50b000 00:05 3408      /dev/dri/card0
b2c58000-b2c60000 rw-s 158e9e000 00:05 3408      /dev/dri/card0
b2c60000-b2c68000 rw-s 155d5a000 00:05 3408      /dev/dri/card0
b2c68000-b2c70000 rw-s 155d79000 00:05 3408      /dev/dri/card0
b2c70000-b2c78000 rw-s 158bca000 00:05 3408      /dev/dri/card0
b2c78000-b2c80000 rw-s 158bc2000 00:05 3408      /dev/dri/card0
b2c80000-b2c88000 rw-s 155d52000 00:05 3408      /dev/dri/card0
b2c88000-b2c90000 rw-s 155d4a000 00:05 3408      /dev/dri/card0
b2c90000-b2c98000 rw-s 159dfc000 00:05 3408      /dev/dri/card0
b2c98000-b2ca0000 rw-s 155d38000 00:05 3408      /dev/dri/card0
b2ca0000-b2ca8000 rw-s 155d30000 00:05 3408      /dev/dri/card0
b2ca8000-b2cb0000 rw-s 155d28000 00:05 3408      /dev/dri/card0
b2cb0000-b2cb8000 rw-s 155d20000 00:05 3408      /dev/dri/card0
b2cb8000-b2cc0000 rw-s 155d18000 00:05 3408      /dev/dri/card0
b2cc0000-b2cc8000 rw-s 155d10000 00:05 3408      /dev/dri/card0
b2cc8000-b2cd0000 rw-s 155d08000 00:05 3408      /dev/dri/card0
b2cd0000-b2cd8000 rw-s 155cc3000 00:05 3408      /dev/dri/card0
b2cd8000-b2ce0000 rw-s 155cbb000 00:05 3408      /dev/dri/card0
b2ce0000-b2ce8000 rw-s 155cb3000 00:05 3408      /dev/dri/card0
b2ce8000-b2cf0000 rw-s 155cab000 00:05 3408      /dev/dri/card0
b2cf0000-b2cf8000 rw-s 155ca3000 00:05 3408      /dev/dri/card0
b2cf8000-b2d00000 rw-s 155c9b000 00:05 3408      /dev/dri/card0
b2d00000-b2d08000 rw-s 158a6c000 00:05 3408      /dev/dri/card0
b2d08000-b2d10000 rw-s 1587c0000 00:05 3408      /dev/dri/card0
b2d10000-b2d18000 rw-s 155cf0000 00:05 3408      /dev/dri/card0
b2d18000-b2d20000 rw-s 155ce8000 00:05 3408      /dev/dri/card0
b2d20000-b2d28000 rw-s 155ce0000 00:05 3408      /dev/dri/card0
b2d28000-b2d30000 rw-s 158848000 00:05 3408      /dev/dri/card0
b2d30000-b2d38000 rw-s 158840000 00:05 3408      /dev/dri/card0
b2d38000-b2d40000 rw-s 155c93000 00:05 3408      /dev/dri/card0
b2d40000-b2d48000 rw-s 15a089000 00:05 3408      /dev/dri/card0
b2d48000-b2d50000 rw-s 15910a000 00:05 3408      /dev/dri/card0
b2d50000-b2d58000 rw-s 155c7a000 00:05 3408      /dev/dri/card0
b2d58000-b2d60000 rw-s 155c72000 00:05 3408      /dev/dri/card0
b2d60000-b2d68000 rw-s 155c6a000 00:05 3408      /dev/dri/card0
b2d68000-b2d70000 rw-s 155c62000 00:05 3408      /dev/dri/card0
b2d70000-b2d78000 rw-s 155c5a000 00:05 3408      /dev/dri/card0
b2d78000-b2d80000 rw-s 155c52000 00:05 3408      /dev/dri/card0
b2d80000-b2d88000 rw-s 155c4a000 00:05 3408      /dev/dri/card0
b2d88000-b2d8b000 rw-s 154672000 00:05 3408      /dev/dri/card0
b2d8b000-b2d8e000 rw-s 15466f000 00:05 3408      /dev/dri/card0
b2d8e000-b2d96000 rw-s 154667000 00:05 3408      /dev/dri/card0
b2d96000-b2d9e000 rw-s 15465f000 00:05 3408      /dev/dri/card0
b2d9e000-b2da6000 rw-s 154657000 00:05 3408      /dev/dri/card0
b2da6000-b2dae000 rw-s 15464f000 00:05 3408      /dev/dri/card0
b2dae000-b2db6000 rw-s 154647000 00:05 3408      /dev/dri/card0
b2db6000-b2dbe000 rw-s 15463f000 00:05 3408      /dev/dri/card0
b2dbe000-b2dc6000 rw-s 155c42000 00:05 3408      /dev/dri/card0
b2dc6000-b2dce000 rw-s 155c39000 00:05 3408      /dev/dri/card0
b2dce000-b2dd6000 rw-s 155c31000 00:05 3408      /dev/dri/card0
b2dd6000-b2dde000 rw-s 155c29000 00:05 3408      /dev/dri/card0
b2dde000-b2de6000 rw-s 155c21000 00:05 3408      /dev/dri/card0
b2de6000-b2dee000 rw-s 155c19000 00:05 3408      /dev/dri/card0
b2dee000-b2df6000 rw-s 155c11000 00:05 3408      /dev/dri/card0
b2df6000-b2dfe000 rw-s 155c09000 00:05 3408      /dev/dri/card0
b2dfe000-b2e06000 rw-s 155bd7000 00:05 3408      /dev/dri/card0
b2e06000-b2e0e000 rw-s 155bcf000 00:05 3408      /dev/dri/card0
b2e0e000-b2e16000 rw-s 155c00000 00:05 3408      /dev/dri/card0
b2e16000-b2e1e000 rw-s 155bf8000 00:05 3408      /dev/dri/card0
b2e1e000-b2e26000 rw-s 155bf0000 00:05 3408      /dev/dri/card0
b2e26000-b2e2e000 rw-s 155be8000 00:05 3408      /dev/dri/card0
b2e2e000-b2e36000 rw-s 155be0000 00:05 3408      /dev/dri/card0
b2e36000-b2e3e000 rw-s 154685000 00:05 3408      /dev/dri/card0
b2e3e000-b2e46000 rw-s 15467d000 00:05 3408      /dev/dri/card0
b2e46000-b2e4e000 rw-s 154675000 00:05 3408      /dev/dri/card0
b2e4e000-b2e56000 rw-s 154637000 00:05 3408      /dev/dri/card0
b2e56000-b2e5e000 rw-s 15462f000 00:05 3408      /dev/dri/card0
b2e5e000-b2e66000 rw-s 154627000 00:05 3408      /dev/dri/card0
b2e66000-b2e6e000 rw-s 15461f000 00:05 3408      /dev/dri/card0
b2e6e000-b2e76000 rw-s 154617000 00:05 3408      /dev/dri/card0
b2e76000-b2e7e000 rw-s 15460f000 00:05 3408      /dev/dri/card0
b2e7e000-b2e86000 rw-s 154607000 00:05 3408      /dev/dri/card0
b2e86000-b2e8e000 rw-s 1545ff000 00:05 3408      /dev/dri/card0
b2e8e000-b2e96000 rw-s 1545f7000 00:05 3408      /dev/dri/card0
b2e96000-b2e9e000 rw-s 1545ef000 00:05 3408      /dev/dri/card0
b2e9e000-b2ea6000 rw-s 154717000 00:05 3408      /dev/dri/card0
b2ea6000-b2eae000 rw-s 1547c6000 00:05 3408      /dev/dri/card0
b2eae000-b2eb6000 rw-s 1547be000 00:05 3408      /dev/dri/card0
b2eb6000-b2ebe000 rw-s 1547b6000 00:05 3408      /dev/dri/card0
b2ebe000-b2ec6000 rw-s 1547ae000 00:05 3408      /dev/dri/card0
b2ec6000-b2ece000 rw-s 1547a6000 00:05 3408      /dev/dri/card0
b2ece000-b2ed6000 rw-s 15479e000 00:05 3408      /dev/dri/card0
b2ed6000-b2ede000 rw-s 15470f000 00:05 3408      /dev/dri/card0
b2ede000-b2ee6000 rw-s 154707000 00:05 3408      /dev/dri/card0
b2ee6000-b2eee000 rw-s 1546ff000 00:05 3408      /dev/dri/card0
b2eee000-b2ef6000 rw-s 1546f7000 00:05 3408      /dev/dri/card0
b2ef6000-b2efe000 rw-s 1546ef000 00:05 3408      /dev/dri/card0
b2efe000-b2f06000 rw-s 1546e7000 00:05 3408      /dev/dri/card0
b2f06000-b2f0e000 rw-s 1546df000 00:05 3408      /dev/dri/card0
b2f0e000-b2f16000 rw-s 1546d7000 00:05 3408      /dev/dri/card0
b2f16000-b2f1e000 rw-s 1546cf000 00:05 3408      /dev/dri/card0
b2f1e000-b2f26000 rw-s 1546c7000 00:05 3408      /dev/dri/card0
b2f26000-b2f2e000 rw-s 1546bf000 00:05 3408      /dev/dri/card0
b2f2e000-b2f36000 rw-s 1546b7000 00:05 3408      /dev/dri/card0
b2f36000-b2f3e000 rw-s 1546af000 00:05 3408      /dev/dri/card0
b2f3e000-b2f46000 rw-s 1546a7000 00:05 3408      /dev/dri/card0
b2f46000-b2f4e000 rw-s 15469f000 00:05 3408      /dev/dri/card0
b2f4e000-b2f56000 rw-s 154697000 00:05 3408      /dev/dri/card0
b2f56000-b2f5e000 rw-s 15468f000 00:05 3408      /dev/dri/card0
b2f5e000-b2f66000 rw-s 154807000 00:05 3408      /dev/dri/card0
b2f66000-b2f6e000 rw-s 1547ff000 00:05 3408      /dev/dri/card0
b2f6e000-b2f76000 rw-s 1547f7000 00:05 3408      /dev/dri/card0
b2f76000-b2f7e000 rw-s 1547ef000 00:05 3408      /dev/dri/card0
b2f7e000-b2f86000 rw-s 1547e7000 00:05 3408      /dev/dri/card0
b2f86000-b2f8e000 rw-s 1547dc000 00:05 3408      /dev/dri/card0
b2f8e000-b2f96000 rw-s 1547d4000 00:05 3408      /dev/dri/card0
b2f96000-b2f9e000 rw-s 154796000 00:05 3408      /dev/dri/card0
b2f9e000-b2fa6000 rw-s 15478e000 00:05 3408      /dev/dri/card0
b2fa6000-b2fae000 rw-s 154786000 00:05 3408      /dev/dri/card0
b2fae000-b2fb6000 rw-s 15477e000 00:05 3408      /dev/dri/card0
b2fb6000-b2fbe000 rw-s 154776000 00:05 3408      /dev/dri/card0
b2fbe000-b2fc6000 rw-s 1559e7000 00:05 3408      /dev/dri/card0
b2fc6000-b2fce000 rw-s 155a01000 00:05 3408      /dev/dri/card0
b2fce000-b2fd6000 rw-s 1559f9000 00:05 3408      /dev/dri/card0
b2fd6000-b2fde000 rw-s 155a26000 00:05 3408      /dev/dri/card0
b2fde000-b2fe6000 rw-s 155a1e000 00:05 3408      /dev/dri/card0
b2fe6000-b2fee000 rw-s 155a16000 00:05 3408      /dev/dri/card0
b2fee000-b2ff6000 rw-s 153cf1000 00:05 3408      /dev/dri/card0
b2ff6000-b2ffe000 rw-s 155a54000 00:05 3408      /dev/dri/card0
b2ffe000-b3006000 rw-s 155a4c000 00:05 3408      /dev/dri/card0
b3006000-b300e000 rw-s 155a44000 00:05 3408      /dev/dri/card0
b300e000-b3016000 rw-s 155a3c000 00:05 3408      /dev/dri/card0
b3016000-b301e000 rw-s 155a34000 00:05 3408      /dev/dri/card0
b301e000-b3026000 rw-s 155b8f000 00:05 3408      /dev/dri/card0
b3026000-b302e000 rw-s 155891000 00:05 3408      /dev/dri/card0
b302e000-b3036000 rw-s 155767000 00:05 3408      /dev/dri/card0
b3036000-b303e000 rw-s 155634000 00:05 3408      /dev/dri/card0
b303e000-b3046000 rw-s 15562c000 00:05 3408      /dev/dri/card0
b3046000-b304e000 rw-s 155717000 00:05 3408      /dev/dri/card0
b304e000-b3056000 rw-s 15570f000 00:05 3408      /dev/dri/card0
b3056000-b305e000 rw-s 155707000 00:05 3408      /dev/dri/card0
b305e000-b3066000 rw-s 1556ff000 00:05 3408      /dev/dri/card0
b3066000-b306e000 rw-s 1556f7000 00:05 3408      /dev/dri/card0
b306e000-b30c4000 rw-s 154720000 00:05 3408      /dev/dri/card0
b30c4000-b311a000 rw-s 155698000 00:05 3408      /dev/dri/card0
b311a000-b3122000 rw-s 155624000 00:05 3408      /dev/dri/card0
b3122000-b312a000 rw-s 158200000 00:05 3408      /dev/dri/card0
b312a000-b3132000 rw-s 155614000 00:05 3408      /dev/dri/card0
b3132000-b313a000 rw-s 15560c000 00:05 3408      /dev/dri/card0
b313a000-b3190000 rw-s 155642000 00:05 3408      /dev/dri/card0
b3190000-b3198000 rw-s 1555fc000 00:05 3408      /dev/dri/card0
b3198000-b31a0000 rw-s 1555f2000 00:05 3408      /dev/dri/card0
b31a0000-b31a8000 rw-s 1555ea000 00:05 3408      /dev/dri/card0
b31a8000-b31b0000 rw-s 155b87000 00:05 3408      /dev/dri/card0
b31b0000-b31b8000 rw-s 155b7f000 00:05 3408      /dev/dri/card0
b31b8000-b31c0000 rw-s 1555e2000 00:05 3408      /dev/dri/card0
b31c0000-b31c8000 rw-s 1555da000 00:05 3408      /dev/dri/card0
b31c8000-b31d0000 rw-s 1555d2000 00:05 3408      /dev/dri/card0
b31d0000-b31d8000 rw-s 1555ca000 00:05 3408      /dev/dri/card0
b31d8000-b31e0000 rw-s 1555c2000 00:05 3408      /dev/dri/card0
b31e0000-b31e8000 rw-s 1555ba000 00:05 3408      /dev/dri/card0
b31e8000-b31f0000 rw-s 155b5f000 00:05 3408      /dev/dri/card0
b31f0000-b31f8000 rw-s 155b57000 00:05 3408      /dev/dri/card0
b31f8000-b3200000 rw-s 155bab000 00:05 3408      /dev/dri/card0
b3200000-b3300000 rw-p 00000000 00:00 0 
b3307000-b330f000 rw-s 155ba3000 00:05 3408      /dev/dri/card0
b330f000-b3317000 rw-s 155b4b000 00:05 3408      /dev/dri/card0
b3317000-b331f000 rw-s 155b43000 00:05 3408      /dev/dri/card0
b331f000-b3327000 rw-s 1577c6000 00:05 3408      /dev/dri/card0
b3327000-b332f000 rw-s 1577a8000 00:05 3408      /dev/dri/card0
b332f000-b3337000 rw-s 1577a0000 00:05 3408      /dev/dri/card0
b3337000-b333f000 rw-s 157798000 00:05 3408      /dev/dri/card0
b333f000-b3347000 rw-s 157790000 00:05 3408      /dev/dri/card0
b3347000-b334f000 rw-s 157788000 00:05 3408      /dev/dri/card0
b334f000-b3357000 rw-s 157780000 00:05 3408      /dev/dri/card0
b3357000-b335f000 rw-s 1577be000 00:05 3408      /dev/dri/card0
b335f000-b3367000 rw-s 1577b6000 00:05 3408      /dev/dri/card0
b3367000-b336f000 rw-s 157778000 00:05 3408      /dev/dri/card0
b336f000-b3377000 rw-s 157770000 00:05 3408      /dev/dri/card0
b3377000-b337f000 rw-s 157768000 00:05 3408      /dev/dri/card0
b337f000-b3387000 rw-s 157760000 00:05 3408      /dev/dri/card0
b3387000-b338f000 rw-s 157758000 00:05 3408      /dev/dri/card0
b338f000-b3397000 rw-s 157750000 00:05 3408      /dev/dri/card0
b3397000-b339f000 rw-s 157748000 00:05 3408      /dev/dri/card0
b339f000-b33a7000 rw-s 157bc0000 00:05 3408      /dev/dri/card0
b33a7000-b33af000 rw-s 157714000 00:05 3408      /dev/dri/card0
b33af000-b33b7000 rw-s 155889000 00:05 3408      /dev/dri/card0
b33b7000-b33bf000 rw-s 15766c000 00:05 3408      /dev/dri/card0
b33bf000-b33c7000 rw-s 157664000 00:05 3408      /dev/dri/card0
b33c7000-b33cf000 rw-s 155adb000 00:05 3408      /dev/dri/card0
b33cf000-b33d7000 rw-s 155ad3000 00:05 3408      /dev/dri/card0
b33d7000-b33df000 rw-s 155acb000 00:05 3408      /dev/dri/card0
b33df000-b33e7000 rw-s 155ac3000 00:05 3408      /dev/dri/card0
b33e7000-b33ef000 rw-s 155abb000 00:05 3408      /dev/dri/card0
b33ef000-b33f7000 rw-s 155ab3000 00:05 3408      /dev/dri/card0
b33f7000-b33ff000 rw-s 155aab000 00:05 3408      /dev/dri/card0
b33ff000-b3407000 rw-s 155aa3000 00:05 3408      /dev/dri/card0
b3407000-b340a000 ---p 00000000 00:00 0 
b340a000-b3458000 rw-p 00000000 00:00 0 
b3458000-b3460000 rw-s 155871000 00:05 3408      /dev/dri/card0
b3460000-b3468000 rw-s 1556ef000 00:05 3408      /dev/dri/card0
b3468000-b3470000 rw-s 155869000 00:05 3408      /dev/dri/card0
b3470000-b3478000 rw-s 155861000 00:05 3408      /dev/dri/card0
b3478000-b3480000 rw-s 15575f000 00:05 3408      /dev/dri/card0
b3480000-b3488000 rw-s 155757000 00:05 3408      /dev/dri/card0
b3488000-b3490000 rw-s 15574f000 00:05 3408      /dev/dri/card0
b3490000-b3498000 rw-s 155747000 00:05 3408      /dev/dri/card0
b3498000-b34a0000 rw-s 15573f000 00:05 3408      /dev/dri/card0
b34a0000-b34a8000 rw-s 1557fa000 00:05 3408      /dev/dri/card0
b34a8000-b34b0000 rw-s 1557f2000 00:05 3408      /dev/dri/card0
b34b0000-b34b8000 rw-s 1557ea000 00:05 3408      /dev/dri/card0
b34b8000-b34c0000 rw-s 155604000 00:05 3408      /dev/dri/card0
b34c0000-b34c8000 rw-s 155859000 00:05 3408      /dev/dri/card0
b34c8000-b34d0000 rw-s 1557e2000 00:05 3408      /dev/dri/card0
b34d0000-b34d8000 rw-s 1559d9000 00:05 3408      /dev/dri/card0
b34d8000-b34e0000 rw-s 1559d1000 00:05 3408      /dev/dri/card0
b34e0000-b34e8000 rw-s 155973000 00:05 3408      /dev/dri/card0
b34e8000-b34f0000 rw-s 1559c9000 00:05 3408      /dev/dri/card0
b34f0000-b34f8000 rw-s 15596b000 00:05 3408      /dev/dri/card0
b34f8000-b3500000 rw-s 155963000 00:05 3408      /dev/dri/card0
b3500000-b35fa000 rw-p 00000000 00:00 0 
b35fa000-b3600000 ---p 00000000 00:00 0 
b3607000-b360f000 rw-s 15595b000 00:05 3408      /dev/dri/card0
b360f000-b3617000 rw-s 155953000 00:05 3408      /dev/dri/card0
b3617000-b361f000 rw-s 1559c1000 00:05 3408      /dev/dri/card0
b361f000-b3627000 rw-s 15594b000 00:05 3408      /dev/dri/card0
b3627000-b362f000 rw-s 1559b9000 00:05 3408      /dev/dri/card0
b362f000-b3637000 rw-s 1559b1000 00:05 3408      /dev/dri/card0
b3637000-b363f000 rw-s 1559a9000 00:05 3408      /dev/dri/card0
b363f000-b3647000 rw-s 1559a1000 00:05 3408      /dev/dri/card0
b3647000-b364f000 rw-s 155999000 00:05 3408      /dev/dri/card0
b364f000-b3657000 rw-s 155991000 00:05 3408      /dev/dri/card0
b3657000-b365f000 rw-s 155989000 00:05 3408      /dev/dri/card0
b365f000-b3667000 rw-s 155981000 00:05 3408      /dev/dri/card0
b3667000-b366f000 rw-s 1544e7000 00:05 3408      /dev/dri/card0
b366f000-b3677000 rw-s 155204000 00:05 3408      /dev/dri/card0
b3677000-b367f000 rw-s 1551fc000 00:05 3408      /dev/dri/card0
b367f000-b3687000 rw-s 1551f4000 00:05 3408      /dev/dri/card0
b3687000-b368f000 rw-s 1551ec000 00:05 3408      /dev/dri/card0
b368f000-b3697000 rw-s 1551e4000 00:05 3408      /dev/dri/card0
b3697000-b369f000 rw-s 1551dc000 00:05 3408      /dev/dri/card0
b369f000-b36a7000 rw-s 1551d4000 00:05 3408      /dev/dri/card0
b36a7000-b36af000 rw-s 1551cc000 00:05 3408      /dev/dri/card0
b36af000-b36b7000 rw-s 15763c000 00:05 3408      /dev/dri/card0
b36b7000-b36bf000 rw-s 15770c000 00:05 3408      /dev/dri/card0
b36bf000-b36c7000 rw-s 155881000 00:05 3408      /dev/dri/card0
b36c7000-b36cf000 rw-s 157704000 00:05 3408      /dev/dri/card0
b36cf000-b36d7000 rw-s 155879000 00:05 3408      /dev/dri/card0
b36d7000-b36df000 rw-s 1577d6000 00:05 3408      /dev/dri/card0
b36df000-b36e7000 rw-s 1576fa000 00:05 3408      /dev/dri/card0
b36e7000-b36ef000 rw-s 1577ce000 00:05 3408      /dev/dri/card0
b36ef000-b36f7000 rw-s 155b1b000 00:05 3408      /dev/dri/card0
b36f7000-b36ff000 rw-s 157730000 00:05 3408      /dev/dri/card0
b36ff000-b3702000 ---p 00000000 00:00 0 
b3702000-b3750000 rw-p 00000000 00:00 0 
b3750000-b37a6000 rw-s 1558f5000 00:05 3408      /dev/dri/card0
b37a6000-b37fc000 rw-s 15589f000 00:05 3408      /dev/dri/card0
b37fd000-b3805000 rw-s 155b13000 00:05 3408      /dev/dri/card0
b3805000-b380d000 rw-s 155b0b000 00:05 3408      /dev/dri/card0
b380d000-b3815000 rw-s 155a95000 00:05 3408      /dev/dri/card0
b3815000-b381d000 rw-s 155b03000 00:05 3408      /dev/dri/card0
b381d000-b381e000 rw-s 1557e1000 00:05 3408      /dev/dri/card0
b381f000-b3827000 rw-s 157ba8000 00:05 3408      /dev/dri/card0
b3827000-b382f000 rw-s 157ba0000 00:05 3408      /dev/dri/card0
b382f000-b3885000 rw-s 155803000 00:05 3408      /dev/dri/card0
b3885000-b38db000 rw-s 155777000 00:05 3408      /dev/dri/card0
b38db000-b38e3000 rw-s 155737000 00:05 3408      /dev/dri/card0
b38e3000-b38eb000 rw-s 15572f000 00:05 3408      /dev/dri/card0
b38eb000-b40ed000 rw-p 00000000 00:00 0 
b40ed000-b4103000 rw-s 154471000 00:05 3408      /dev/dri/card0
b4103000-b460f000 rw-p 00000000 00:00 0 
b460f000-b4674000 rw-s 00000000 00:04 3637271    /SYSV00000000 (deleted)
b4674000-b4677000 ---p 00000000 00:00 0 
b4677000-b46c5000 rw-p 00000000 00:00 0 
b46c5000-b46c8000 ---p 00000000 00:00 0 
b46c8000-b4982000 rw-p 00000000 00:00 0 
b4987000-b498f000 rw-s 155727000 00:05 3408      /dev/dri/card0
b498f000-b49ef000 rw-s 00000000 00:04 1540120    /SYSV00000000 (deleted)
b49f1000-b49f9000 rw-s 15a788000 00:05 3408      /dev/dri/card0
b49f9000-b4a01000 rw-s 15b204000 00:05 3408      /dev/dri/card0
b4a01000-b4a17000 rw-s 1544f3000 00:05 3408      /dev/dri/card0
b4a18000-b4a20000 rw-s 154487000 00:05 3408      /dev/dri/card0
b4a20000-b4a2b000 r--s 00127000 08:01 8142923    /home/ben/.minecraft/bin/minecraft.jar
b4a2b000-b4a30000 r--s 00033000 08:01 8142921    /home/ben/.minecraft/bin/jinput.jar
b4a30000-b4a39000 r--s 000ac000 08:01 8142920    /home/ben/.minecraft/bin/lwjgl.jar
b4a3a000-b4a3b000 rw-s 1557cf000 00:05 3408      /dev/dri/card0
b4a3d000-b4a40000 r--s 0001f000 08:01 8142922    /home/ben/.minecraft/bin/lwjgl_util.jar
b4a40000-b4a43000 r--s 00038000 08:01 6294065    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
b4a43000-b4a46000 r--s 00077000 08:01 6294086    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar
b4a46000-b4a48000 rw-s 155a6b000 00:05 3408      /dev/dri/card0
b4a48000-b4a4a000 rw-s 155a69000 00:05 3408      /dev/dri/card0
b4a4b000-b4a53000 rw-s 155afb000 00:05 3408      /dev/dri/card0
b4a53000-b4a5b000 rw-s 155a8d000 00:05 3408      /dev/dri/card0
b4a5b000-b4a63000 rw-s 155a85000 00:05 3408      /dev/dri/card0
b4a63000-b4a6b000 rw-s 155a7d000 00:05 3408      /dev/dri/card0
b4a6b000-b4a73000 rw-s 155a75000 00:05 3408      /dev/dri/card0
b4a73000-b4a7b000 rw-s 1576e4000 00:05 3408      /dev/dri/card0
b4a7b000-b4a83000 rw-s 1576dc000 00:05 3408      /dev/dri/card0
b4a83000-b4a8b000 rw-s 1576d4000 00:05 3408      /dev/dri/card0
b4a8b000-b4a93000 rw-s 155a6d000 00:05 3408      /dev/dri/card0
b4a93000-b4a9b000 rw-s 1576cc000 00:05 3408      /dev/dri/card0
b4a9b000-b4aa3000 rw-s 155af3000 00:05 3408      /dev/dri/card0
b4aa3000-b4aab000 rw-s 1565bf000 00:05 3408      /dev/dri/card0
b4aab000-b4ab3000 rw-s 1576bc000 00:05 3408      /dev/dri/card0
b4ab3000-b4abb000 rw-s 157654000 00:05 3408      /dev/dri/card0
b4abb000-b4ac3000 rw-s 155ae3000 00:05 3408      /dev/dri/card0
b4ac3000-b4acb000 rw-s 1576b4000 00:05 3408      /dev/dri/card0
b4acb000-b4acc000 rw-s 158a9e000 00:05 3408      /dev/dri/card0
b4acc000-b4acf000 ---p 00000000 00:00 0 
b4acf000-b4b1d000 rw-p 00000000 00:00 0 
b4b1d000-b4b20000 ---p 00000000 00:00 0 
b4b20000-b4b6e000 rw-p 00000000 00:00 0 
b4b6e000-b4b71000 r--s 00031000 08:01 6294190    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
b4b71000-b4b75000 r--s 0007c000 08:01 6297725    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
b4b75000-b4b78000 ---p 00000000 00:00 0 
b4b78000-b4bc6000 rw-p 00000000 00:00 0 
b4bc6000-b4bc8000 r--s 00013000 08:01 6297724    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
b4bc8000-b4c60000 r--p 00000000 08:01 7212737    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4c60000-b4c61000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4c61000-b4c62000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4c62000-b4c68000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4c68000-b4c6a000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4c6a000-b4c6d000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4c6d000-b4c73000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4c73000-b4c74000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4c74000-b4c77000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4c77000-b4c78000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4c78000-b4c79000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4c79000-b4c7a000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4c7a000-b4c7e000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4c7e000-b4c82000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4c82000-b4c89000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4c89000-b4c94000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4c94000-b4c97000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4c97000-b4c98000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4c98000-b4ca0000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4ca0000-b4ca8000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4ca8000-b4cab000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4cab000-b4cad000 r--p 00000000 08:01 7736533    /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
b4cad000-b4cae000 r--p 00000000 08:01 7736950    /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
b4cae000-b4cb2000 r--p 00000000 08:01 7736408    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20-properties.mo
b4cb2000-b4cb4000 r--p 00000000 08:01 7736538    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20.mo
b4cb4000-b4cb5000 r--p 00000000 08:01 6422645    /usr/lib/locale/en_GB.utf8/LC_NUMERIC
b4cb5000-b4cb6000 r--p 00000000 08:01 6299161    /usr/lib/locale/en_GB.utf8/LC_TIME
b4cb6000-b4dd4000 r--p 00000000 08:01 6422639    /usr/lib/locale/en_GB.utf8/LC_COLLATE
b4dd4000-b4dd5000 r--p 00000000 08:01 6422600    /usr/lib/locale/en_GB.utf8/LC_MONETARY
b4dd5000-b4dd6000 r--p 00000000 08:01 6422649    /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b4dd6000-b4dd7000 r--p 00000000 08:01 6422646    /usr/lib/locale/en_GB.utf8/LC_PAPER
b4dd7000-b4dd8000 r--p 00000000 08:01 6422722    /usr/lib/locale/en_GB.utf8/LC_NAME
b4dd8000-b4dd9000 r--p 00000000 08:01 6422601    /usr/lib/locale/en_GB.utf8/LC_ADDRESS
b4dd9000-b4dda000 r--p 00000000 08:01 6422602    /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
b4dda000-b4ddb000 r--p 00000000 08:01 6422642    /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
b4ddb000-b4ddc000 r--p 00000000 08:01 6422603    /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
b4ddc000-b4ddf000 ---p 00000000 00:00 0 
b4ddf000-b4e2d000 rw-p 00000000 00:00 0 
b4e2d000-b4e2e000 r--p 00000000 00:00 0 
b4e2e000-b4e31000 ---p 00000000 00:00 0 
b4e31000-b4e7f000 rw-p 00000000 00:00 0 
b4e7f000-b4e82000 ---p 00000000 00:00 0 
b4e82000-b4ed0000 rw-p 00000000 00:00 0 
b4ed0000-b4ed1000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4ed1000-b4ed2000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4ed2000-b4ed8000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4ed8000-b4eda000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4eda000-b4edd000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4edd000-b4ee3000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4ee3000-b4ee4000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4ee4000-b4ee7000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4ee7000-b4ee8000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4ee8000-b4ee9000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4ee9000-b4eea000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4eea000-b4eee000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4eee000-b4ef2000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4ef2000-b4ef9000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4ef9000-b4f04000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4f04000-b4f07000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4f07000-b4f08000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4f08000-b4f10000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4f10000-b4f18000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4f18000-b4f1b000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4f1b000-b4f1c000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4f1c000-b4f1d000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4f1d000-b4f23000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4f23000-b4f25000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4f25000-b4f28000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4f28000-b4f2e000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4f2e000-b4f2f000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4f2f000-b4f32000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4f32000-b4f33000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4f33000-b4f34000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4f34000-b4f35000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4f35000-b4f39000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4f39000-b4f3d000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4f3d000-b4f44000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4f44000-b4f4f000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4f4f000-b4f52000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4f52000-b4f53000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4f53000-b4f5b000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4f5b000-b4f63000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4f63000-b4f66000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4f66000-b4f69000 ---p 00000000 00:00 0 
b4f69000-b4fb7000 rw-p 00000000 00:00 0 
b4fb7000-b4fbd000 r--s 000fc000 08:01 6297732    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
b4fbd000-b4fc6000 r--s 00065000 08:01 6692486    /usr/share/java/gnome-java-bridge.jar
b4fc6000-b4fc7000 ---p 00000000 00:00 0 
b4fc7000-b5047000 rw-p 00000000 00:00 0 
b5047000-b504a000 ---p 00000000 00:00 0 
b504a000-b5098000 rw-p 00000000 00:00 0 
b5098000-b509b000 ---p 00000000 00:00 0 
b509b000-b5119000 rw-p 00000000 00:00 0 
b5119000-b511c000 ---p 00000000 00:00 0 
b511c000-b516a000 rw-p 00000000 00:00 0 
b516a000-b5171000 r--s 00000000 08:01 6292678    /usr/lib/gconv/gconv-modules.cache
b5171000-b51b0000 r--p 00000000 08:01 6422640    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b51b0000-b51b3000 ---p 00000000 00:00 0 
b51b3000-b5201000 rw-p 00000000 00:00 0 
b5201000-b5204000 ---p 00000000 00:00 0 
b5204000-b5252000 rw-p 00000000 00:00 0 
b5252000-b5253000 ---p 00000000 00:00 0 
b5253000-b52d3000 rw-p 00000000 00:00 0 
b52d3000-b52d5000 r--s 0001d000 08:01 6297730    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
b52d5000-b52da000 r--s 00044000 08:01 6297729    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
b52da000-b530d000 rw-p 00000000 00:00 0 
b530d000-b549c000 r--s 038c2000 08:01 6297744    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b549c000-b54b0000 rw-p 00000000 00:00 0 
b54b0000-b54ca000 rw-p 00000000 00:00 0 
b54ca000-b54eb000 rw-p 00000000 00:00 0 
b54eb000-b5575000 rw-p 00000000 00:00 0 
b5575000-b5586000 rw-p 00000000 00:00 0 
b5586000-b55ca000 rw-p 00000000 00:00 0 
b55ca000-b55ec000 rw-p 00000000 00:00 0 
b55ec000-b5675000 rw-p 00000000 00:00 0 
b5675000-b567b000 rw-p 00000000 00:00 0 
b567b000-b5695000 rw-p 00000000 00:00 0 
b5695000-b56b1000 rw-p 00000000 00:00 0 
b56b1000-b5721000 rw-p 00000000 00:00 0 
b5721000-b5b01000 rwxp 00000000 00:00 0 
b5b01000-b7721000 rw-p 00000000 00:00 0 
b7721000-b7724000 ---p 00000000 00:00 0 
b7724000-b7774000 rw-p 00000000 00:00 0 
b7774000-b7777000 r--s 0000f000 08:01 6294240    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b7777000-b7779000 r--s 00014000 08:01 131085     /home/ben/Downloads/minecraft.jar
b7779000-b7781000 rw-s 00000000 08:01 262197     /tmp/hsperfdata_ben/7321
b7781000-b7782000 rw-p 00000000 00:00 0 
b7782000-b7783000 r--p 00000000 00:00 0 
b7783000-b7785000 rw-p 00000000 00:00 0 
bfb88000-bfbbd000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
java_command: /home/ben/Downloads/minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=ben
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3ea350], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3ea350], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30ca20], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.39 1.35 1.28

/proc/meminfo:
MemTotal:        2061692 kB
MemFree:          330696 kB
Buffers:          175672 kB
Cached:           866216 kB
SwapCached:            0 kB
Active:           986908 kB
Inactive:         605032 kB
Active(anon):     550408 kB
Inactive(anon):     7368 kB
Active(file):     436500 kB
Inactive(file):   597664 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       1187784 kB
HighFree:           1736 kB
LowTotal:         873908 kB
LowFree:          328960 kB
SwapTotal:       6036472 kB
SwapFree:        6036472 kB
Dirty:               532 kB
Writeback:             0 kB
AnonPages:        550064 kB
Mapped:           112788 kB
Shmem:              7728 kB
Slab:              46888 kB
SReclaimable:      34704 kB
SUnreclaim:        12184 kB
KernelStack:        2072 kB
PageTables:         5692 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7067316 kB
Committed_AS:    1251804 kB
VmallocTotal:     122880 kB
VmallocUsed:       19672 kB
VmallocChunk:      96764 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      106488 kB
DirectMap4M:      802816 kB


CPU:total 1 (1 cores per cpu, 1 threads per core) family 6 model 10 stepping 0, cmov, cx8, fxsr, mmx, sse, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 2061692k(330696k free), swap 6036472k(6036472k free)

vm_info: OpenJDK Client VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Feb 23 2011 19:53:10 by "buildd" with gcc 4.4.3

time: Fri Mar 11 09:14:20 2011
elapsed time: 235 seconds

```

---

### Post by clooless001 on 2011-03-11
```
 #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb5a2a1d7, pid=8910, tid=3025476464
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Client VM (19.0-b09 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.7-0ubuntu1~10.04.1
# Problematic frame:
# J  bb.c(Lom;DDDFF)V
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
#

---------------  T H R E A D  ---------------

Current thread (0x09726800):  JavaThread "Minecraft main thread" daemon [_thread_in_Java, id=8940, stack(0xb4501000,0xb4552000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000040

Registers:
EAX=0x0000000d, EBX=0x00000000, ECX=0x7c22f2c8, EDX=0x00000100
ESP=0xb4550860, EBP=0xb4550c44, ESI=0x000020e0, EDI=0x00000040
EIP=0xb5a2a1d7, CR2=0x00000040, EFLAGS=0x00010216

Register to memory mapping:

EAX=0x0000000d
0x0000000d is pointing to unknown location

EBX=0x00000000
0x00000000 is pointing to unknown location

ECX=0x7c22f2c8
ro 
 - klass: 'ro'

EDX=0x00000100
0x00000100 is pointing to unknown location

ESP=0xb4550860
0xb4550860 is pointing into the stack for thread: 0x09726800
"Minecraft main thread" daemon prio=10 tid=0x09726800 nid=0x22ec runnable [0x00000000]
   java.lang.Thread.State: RUNNABLE

EBP=0xb4550c44
0xb4550c44 is pointing into the stack for thread: 0x09726800
"Minecraft main thread" daemon prio=10 tid=0x09726800 nid=0x22ec runnable [0x00000000]
   java.lang.Thread.State: RUNNABLE

ESI=0x000020e0
0x000020e0 is pointing to unknown location

EDI=0x00000040
0x00000040 is pointing to unknown location


Top of Stack: (sp=0xb4550860)
0xb4550860:   00000040 ffffffa3 00000001 0168814a
0xb4550870:   00000000 08238230 b4550898 09356b85
0xb4550880:   00000012 00001405 0a0ee000 0168b036
0xb4550890:   09b3add0 b45508c8 b45508d8 b5906bc1
0xb45508a0:   09726918 b45508c8 00000012 00001405
0xb45508b0:   b45508e8 00000000 08238230 01657d2e
0xb45508c0:   00000000 b4550914 8ff65068 0935913d
0xb45508d0:   c2921eea c2833d71 7a870128 6fce0628 

Instructions: (pc=0xb5a2a1d7)
0xb5a2a1c7:   02 00 00 ba 00 01 00 00 3b d0 0f 86 2d 07 00 00
0xb5a2a1d7:   8b 5c 83 0c 8b 4c 24 7c 89 9c 24 b8 00 00 00 b8 

Stack: [0xb4501000,0xb4552000],  sp=0xb4550860,  free space=318k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
J  bb.c(Lom;DDDFF)V
j  mh.b(F)V+286
j  net.minecraft.client.Minecraft.run()V+357
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub
V  [libjvm.so+0x209a92]
V  [libjvm.so+0x30a609]
V  [libjvm.so+0x2089cf]
V  [libjvm.so+0x20951a]
V  [libjvm.so+0x209678]
V  [libjvm.so+0x253e41]
V  [libjvm.so+0x3bb43c]
V  [libjvm.so+0x3bb502]
V  [libjvm.so+0x311051]
C  [libpthread.so.0+0x596e]


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x09f49800 JavaThread "Thread-9" daemon [_thread_blocked, id=8943, stack(0xb4552000,0xb45a3000)]
=>0x09726800 JavaThread "Minecraft main thread" daemon [_thread_in_Java, id=8940, stack(0xb4501000,0xb4552000)]
  0x0999ac00 JavaThread "Timer hack thread" daemon [_thread_blocked, id=8939, stack(0xb4cc2000,0xb4d13000)]
  0x0998dc00 JavaThread "TimerQueue" daemon [_thread_blocked, id=8933, stack(0xb46cb000,0xb471c000)]
  0x096bd000 JavaThread "DestroyJavaVM" [_thread_blocked, id=8911, stack(0xb7708000,0xb7759000)]
  0x098e7400 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=8929, stack(0xb4a5c000,0xb4aad000)]
  0x098e6c00 JavaThread "AWT-Shutdown" [_thread_blocked, id=8928, stack(0xb4d13000,0xb4d64000)]
  0x097e3400 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=8922, stack(0xb4d64000,0xb4db5000)]
  0x097aec00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=8921, stack(0xb4f4d000,0xb4f9e000)]
  0x096f9000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=8917, stack(0xb502e000,0xb507f000)]
  0x096f7000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=8916, stack(0xb507f000,0xb5100000)]
  0x096f5800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=8915, stack(0xb5100000,0xb5151000)]
  0x096ed800 JavaThread "Finalizer" daemon [_thread_blocked, id=8914, stack(0xb5197000,0xb51e8000)]
  0x096ec000 JavaThread "Reference Handler" daemon [_thread_blocked, id=8913, stack(0xb51e8000,0xb5239000)]

Other Threads:
  0x096ea400 VMThread [stack: 0xb5239000,0xb52ba000] [id=8912]
  0x09705000 WatcherThread [stack: 0xb4fad000,0xb502e000] [id=8918]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 30144K, used 20708K [0x6f940000, 0x719f0000, 0x7a3e0000)
  eden space 26816K,  69% used [0x6f940000, 0x70b80798, 0x71370000)
  from space 3328K,  60% used [0x71370000, 0x71568c08, 0x716b0000)
  to   space 3328K,   0% used [0x716b0000, 0x716b0000, 0x719f0000)
 tenured generation   total 66900K, used 52787K [0x7a3e0000, 0x7e535000, 0x8f940000)
   the space 66900K,  78% used [0x7a3e0000, 0x7d76cdd8, 0x7d76ce00, 0x7e535000)
 compacting perm gen  total 12288K, used 8473K [0x8f940000, 0x90540000, 0x93940000)
   the space 12288K,  68% used [0x8f940000, 0x90186760, 0x90186800, 0x90540000)
    ro space 10240K,  73% used [0x93940000, 0x94098710, 0x94098800, 0x94340000)
    rw space 12288K,  60% used [0x94340000, 0x94a80f20, 0x94a81000, 0x94f40000)

Dynamic libraries:
00110000-00117000 r-xp 00000000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
00117000-00118000 r--p 00006000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
00118000-00119000 rw-p 00007000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
00119000-0013d000 r-xp 00000000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0013d000-0013e000 r--p 00023000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0013e000-00140000 rw-p 00024000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00140000-00146000 r-xp 00000000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00146000-00147000 r--p 00006000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00147000-00148000 rw-p 00007000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00148000-00152000 r-xp 00000000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00152000-00153000 r--p 00009000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00153000-00154000 rw-p 0000a000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00154000-001d9000 r-xp 00000000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001d9000-001da000 r--p 00084000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001da000-001e0000 rw-p 00085000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001e0000-00205000 rw-p 00000000 00:00 0 
00205000-0024a000 r-xp 00000000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0024a000-0024b000 r--p 00044000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0024b000-0024d000 rw-p 00045000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0024d000-0024e000 rw-p 00000000 00:00 0 
0024e000-00256000 r-xp 00000000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00256000-00257000 r--p 00007000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00257000-00258000 rw-p 00008000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00258000-00264000 r-xp 00000000 08:01 6294335    /usr/lib/libXi.so.6.1.0
00264000-00265000 r--p 0000c000 08:01 6294335    /usr/lib/libXi.so.6.1.0
00265000-00266000 rw-p 0000d000 08:01 6294335    /usr/lib/libXi.so.6.1.0
00266000-0027e000 r-xp 00000000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
0027e000-0027f000 r--p 00017000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
0027f000-00280000 rw-p 00018000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00280000-00282000 r-xp 00000000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00282000-00283000 r--p 00001000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00283000-00284000 rw-p 00002000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00284000-002a1000 r-xp 00000000 08:01 8519763    /lib/libgcc_s.so.1
002a1000-002a2000 r--p 0001c000 08:01 8519763    /lib/libgcc_s.so.1
002a2000-002a3000 rw-p 0001d000 08:01 8519763    /lib/libgcc_s.so.1
002a3000-002ab000 r-xp 00000000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
002ab000-002ac000 r--p 00007000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
002ac000-002ad000 rw-p 00008000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
002ad000-002af000 r-xp 00000000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
002af000-002b0000 r--p 00001000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
002b0000-002b1000 rw-p 00002000 08:01 6294337    /usr/lib/libXinerama.so.1.0.0
002b2000-002c0000 r-xp 00000000 08:01 6294327    /usr/lib/libXext.so.6.4.0
002c0000-002c1000 r--p 0000d000 08:01 6294327    /usr/lib/libXext.so.6.4.0
002c1000-002c2000 rw-p 0000e000 08:01 6294327    /usr/lib/libXext.so.6.4.0
002c2000-00333000 r-xp 00000000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
00333000-00337000 r--p 00070000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
00337000-00338000 rw-p 00074000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
00338000-0033c000 r-xp 00000000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
0033c000-0033d000 r--p 00003000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
0033d000-0033e000 rw-p 00004000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
0033e000-00340000 r-xp 00000000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
00340000-00341000 r--p 00001000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
00341000-00342000 rw-p 00002000 08:01 6294319    /usr/lib/libXcomposite.so.1.0.0
00342000-00344000 r-xp 00000000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
00344000-00345000 r--p 00001000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
00345000-00346000 rw-p 00002000 08:01 6294323    /usr/lib/libXdamage.so.1.1.0
00346000-00347000 r-xp 00000000 08:01 6299066    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00347000-00348000 r--p 00000000 08:01 6299066    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00348000-00349000 rw-p 00001000 08:01 6299066    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00349000-00355000 r-xp 00000000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00355000-00356000 r--p 0000b000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00356000-00357000 rw-p 0000c000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00357000-0036f000 r-xp 00000000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
0036f000-00370000 r--p 00017000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00370000-00371000 rw-p 00018000 08:01 6294654    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00371000-0037b000 r-xp 00000000 08:01 6292566    /usr/lib/libpangocairo-1.0.so.0.2800.0
0037b000-0037c000 r--p 00009000 08:01 6292566    /usr/lib/libpangocairo-1.0.so.0.2800.0
0037c000-0037d000 rw-p 0000a000 08:01 6292566    /usr/lib/libpangocairo-1.0.so.0.2800.0
0037d000-00396000 r-xp 00000000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
00396000-00397000 ---p 00019000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
00397000-00398000 r--p 00019000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
00398000-00399000 rw-p 0001a000 08:01 6294400    /usr/lib/libatk-1.0.so.0.3009.1
00399000-0039d000 r-xp 00000000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
0039d000-0039e000 r--p 00003000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
0039e000-0039f000 rw-p 00004000 08:01 6294805    /usr/lib/libgthread-2.0.so.0.2400.1
0039f000-003a7000 r-xp 00000000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
003a7000-003a8000 r--p 00007000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
003a8000-003a9000 rw-p 00008000 08:01 6294618    /usr/lib/libfusion-1.2.so.0.8.0
003a9000-003ac000 r-xp 00000000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
003ac000-003ad000 r--p 00003000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
003ad000-003ae000 rw-p 00004000 08:01 6294455    /usr/lib/libcanberra-gtk.so.0.1.5
003ae000-003b2000 r-xp 00000000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
003b2000-003b3000 r--p 00003000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
003b3000-003b4000 rw-p 00004000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
003b4000-003d9000 r-xp 00000000 08:01 6293458    /usr/lib/libpangoft2-1.0.so.0.2800.0
003d9000-003da000 r--p 00024000 08:01 6293458    /usr/lib/libpangoft2-1.0.so.0.2800.0
003da000-003db000 rw-p 00025000 08:01 6293458    /usr/lib/libpangoft2-1.0.so.0.2800.0
003dc000-003f1000 r-xp 00000000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
003f1000-003f2000 r--p 00014000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
003f2000-003f3000 rw-p 00015000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
003f3000-003f5000 rw-p 00000000 00:00 0 
003f5000-0050e000 r-xp 00000000 08:01 6294310    /usr/lib/libX11.so.6.3.0
0050e000-0050f000 r--p 00118000 08:01 6294310    /usr/lib/libX11.so.6.3.0
0050f000-00511000 rw-p 00119000 08:01 6294310    /usr/lib/libX11.so.6.3.0
00511000-00512000 rw-p 00000000 00:00 0 
00512000-0054f000 r-xp 00000000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
0054f000-00550000 r--p 0003c000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
00550000-00551000 rw-p 0003d000 08:01 6294721    /usr/lib/libgobject-2.0.so.0.2400.1
00551000-00575000 r-xp 00000000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
00575000-00576000 r--p 00023000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
00576000-00577000 rw-p 00024000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
00577000-005b7000 r-xp 00000000 08:01 6292277    /usr/lib/libpango-1.0.so.0.2800.0
005b7000-005b8000 ---p 00040000 08:01 6292277    /usr/lib/libpango-1.0.so.0.2800.0
005b8000-005b9000 r--p 00040000 08:01 6292277    /usr/lib/libpango-1.0.so.0.2800.0
005b9000-005ba000 rw-p 00041000 08:01 6292277    /usr/lib/libpango-1.0.so.0.2800.0
005ba000-005c0000 r-xp 00000000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
005c0000-005c1000 r--p 00005000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
005c1000-005c2000 rw-p 00006000 08:01 6295319    /usr/lib/libxcb-render.so.0.0.0
005c2000-005ca000 r-xp 00000000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
005ca000-005cb000 r--p 00007000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
005cb000-005cc000 rw-p 00008000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
005cc000-005e0000 r-xp 00000000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
005e0000-005e1000 r--p 00013000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
005e1000-005e2000 rw-p 00014000 08:01 6294541    /usr/lib/libdirect-1.2.so.0.8.0
005e2000-00605000 r-xp 00000000 08:01 8519833    /lib/libpng12.so.0.42.0
00605000-00606000 r--p 00022000 08:01 8519833    /lib/libpng12.so.0.42.0
00606000-00607000 rw-p 00023000 08:01 8519833    /lib/libpng12.so.0.42.0
00607000-0060b000 r-xp 00000000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0060b000-0060c000 ---p 00004000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0060c000-0060d000 r--p 00004000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0060d000-0060e000 rw-p 00005000 08:01 6298670    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
00610000-00612000 r-xp 00000000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00612000-00613000 r--p 00001000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00613000-00614000 rw-p 00002000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00614000-0066b000 r-xp 00000000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
0066b000-0066d000 r--p 00057000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
0066d000-0066e000 rw-p 00059000 08:01 6295085    /usr/lib/libpixman-1.so.0.16.4
0066e000-00681000 r-xp 00000000 08:01 8519878    /lib/libz.so.1.2.3.3
00681000-00682000 r--p 00012000 08:01 8519878    /lib/libz.so.1.2.3.3
00682000-00683000 rw-p 00013000 08:01 8519878    /lib/libz.so.1.2.3.3
00683000-00716000 r-xp 00000000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
00716000-00718000 r--p 00093000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
00718000-00719000 rw-p 00095000 08:01 6294652    /usr/lib/libgdk-x11-2.0.so.0.2000.1
00719000-00748000 r-xp 00000000 08:01 8519821    /lib/libpcre.so.3.12.1
00748000-00749000 r--p 0002e000 08:01 8519821    /lib/libpcre.so.3.12.1
00749000-0074a000 rw-p 0002f000 08:01 8519821    /lib/libpcre.so.3.12.1
0074a000-00763000 r-xp 00000000 08:01 8519845    /lib/libselinux.so.1
00763000-00764000 r--p 00018000 08:01 8519845    /lib/libselinux.so.1
00764000-00765000 rw-p 00019000 08:01 8519845    /lib/libselinux.so.1
00767000-0076d000 r-xp 00000000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
0076d000-0076e000 r--p 00005000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
0076e000-0076f000 rw-p 00006000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
0076f000-00771000 r-xp 00000000 08:01 6293464    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00771000-00772000 r--p 00001000 08:01 6293464    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00772000-00773000 rw-p 00002000 08:01 6293464    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00773000-0077a000 r-xp 00000000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
0077a000-0077b000 r--p 00006000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
0077b000-0077c000 rw-p 00007000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
0077c000-007f3000 r-xp 00000000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
007f3000-007f5000 r--p 00076000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
007f5000-007f6000 rw-p 00078000 08:01 6294447    /usr/lib/libcairo.so.2.10800.10
007f6000-00804000 r-xp 00000000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
00804000-00805000 r--p 0000d000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
00805000-00806000 rw-p 0000e000 08:01 6294457    /usr/lib/libcanberra.so.0.2.1
00806000-0080d000 r-xp 00000000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
0080d000-0080e000 r--p 00006000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
0080e000-0080f000 rw-p 00007000 08:01 6295284    /usr/lib/libvorbisfile.so.3.3.2
00811000-00812000 r-xp 00000000 00:00 0          [vdso]
00812000-00817000 r-xp 00000000 08:01 6295038    /usr/lib/libogg.so.0.6.0
00817000-00818000 r--p 00004000 08:01 6295038    /usr/lib/libogg.so.0.6.0
00818000-00819000 rw-p 00005000 08:01 6295038    /usr/lib/libogg.so.0.6.0
00819000-00826000 r-xp 00000000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
00826000-00827000 r--p 0000c000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
00827000-00828000 rw-p 0000d000 08:01 6295229    /usr/lib/libtdb.so.1.2.0
0082a000-0082e000 r-xp 00000000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
0082e000-0082f000 r--p 00003000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
0082f000-00830000 rw-p 00004000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
00830000-008ca000 r-xp 00000000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
008ca000-008cb000 ---p 0009a000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
008cb000-008cc000 r--p 0009a000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
008cc000-008cd000 rw-p 0009b000 08:01 6294667    /usr/lib/libgio-2.0.so.0.2400.1
008cd000-008ce000 rw-p 00000000 00:00 0 
008ce000-008d3000 r-xp 00000000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
008d3000-008d4000 r--p 00004000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
008d4000-008d5000 rw-p 00005000 08:01 6298634    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
008d6000-008dd000 r-xp 00000000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
008dd000-008de000 r--p 00006000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
008de000-008df000 rw-p 00007000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
008df000-008e6000 r-xp 00000000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
008e6000-008e7000 r--p 00006000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
008e7000-008e8000 rw-p 00007000 08:01 6294955    /usr/lib/libltdl.so.7.2.1
008eb000-008fb000 r-xp 00000000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
008fb000-008fc000 r--p 00010000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
008fc000-008fd000 rw-p 00011000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
008fd000-008ff000 rw-p 00000000 00:00 0 
008ff000-00913000 r-xp 00000000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00913000-00914000 r--p 00013000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00914000-00915000 rw-p 00014000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00915000-0091c000 r-xp 00000000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
0091c000-0091d000 r--p 00006000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
0091d000-0091e000 rw-p 00007000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
0091e000-00920000 r-xp 00000000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
00920000-00921000 r--p 00001000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
00921000-00922000 rw-p 00002000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
00925000-00940000 r-xp 00000000 08:01 8519683    /lib/ld-2.11.1.so
00940000-00941000 r--p 0001a000 08:01 8519683    /lib/ld-2.11.1.so
00941000-00942000 rw-p 0001b000 08:01 8519683    /lib/ld-2.11.1.so
00942000-00966000 r-xp 00000000 08:01 8519756    /lib/libexpat.so.1.5.2
00966000-00968000 r--p 00024000 08:01 8519756    /lib/libexpat.so.1.5.2
00968000-00969000 rw-p 00026000 08:01 8519756    /lib/libexpat.so.1.5.2
00969000-00973000 r-xp 00000000 08:01 8519740    /lib/libudev.so.0.6.1
00973000-00974000 r--p 00009000 08:01 8519740    /lib/libudev.so.0.6.1
00974000-00975000 rw-p 0000a000 08:01 8519740    /lib/libudev.so.0.6.1
00975000-00979000 r-xp 00000000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00979000-0097a000 r--p 00004000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
0097a000-0097b000 rw-p 00005000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
0097d000-009c1000 r-xp 00000000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
009c1000-009c3000 r--p 00043000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
009c3000-009c4000 rw-p 00045000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
009c4000-009c9000 rw-p 00000000 00:00 0 
009c9000-00a3c000 r-xp 00000000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
00a3c000-00a3d000 ---p 00073000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
00a3d000-00a3e000 r--p 00073000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
00a3e000-00a3f000 rw-p 00074000 08:01 6294543    /usr/lib/libdirectfb-1.2.so.0.8.0
00a3f000-00a40000 rw-p 00000000 00:00 0 
00a40000-00a67000 r-xp 00000000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00a67000-00a68000 r--p 00026000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00a68000-00a69000 rw-p 00027000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00a69000-00a6b000 r-xp 00000000 08:01 6291780    /usr/lib/libplds4.so
00a6b000-00a6c000 r--p 00001000 08:01 6291780    /usr/lib/libplds4.so
00a6c000-00a6d000 rw-p 00002000 08:01 6291780    /usr/lib/libplds4.so
00a6d000-00bc0000 r-xp 00000000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00bc0000-00bc1000 ---p 00153000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00bc1000-00bc3000 r--p 00153000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00bc3000-00bc4000 rw-p 00155000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00bc4000-00bc7000 rw-p 00000000 00:00 0 
00bc7000-00bed000 r-xp 00000000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
00bed000-00bee000 r--p 00025000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
00bee000-00bef000 rw-p 00026000 08:01 6298624    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
00bef000-00bf8000 r-xp 00000000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
00bf8000-00bf9000 r--p 00008000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
00bf9000-00bfa000 rw-p 00009000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
00bfa000-00bfd000 r-xp 00000000 08:01 6291779    /usr/lib/libplc4.so
00bfd000-00bfe000 r--p 00002000 08:01 6291779    /usr/lib/libplc4.so
00bfe000-00bff000 rw-p 00003000 08:01 6291779    /usr/lib/libplc4.so
00bff000-00c12000 r-xp 00000000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00c12000-00c13000 r--p 00012000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00c13000-00c14000 rw-p 00013000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00c14000-00c16000 rw-p 00000000 00:00 0 
00c16000-00c4f000 r-xp 00000000 08:01 6294870    /usr/lib/libibus.so.1.0.0
00c4f000-00c50000 r--p 00039000 08:01 6294870    /usr/lib/libibus.so.1.0.0
00c50000-00c51000 rw-p 0003a000 08:01 6294870    /usr/lib/libibus.so.1.0.0
00c51000-00c65000 r-xp 00000000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
00c65000-00c66000 r--p 00013000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
00c66000-00c67000 rw-p 00014000 08:01 6294854    /usr/lib/libgvfscommon.so.0.0.0
00c69000-00c6c000 r-xp 00000000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
00c6c000-00c6d000 r--p 00002000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
00c6d000-00c6e000 rw-p 00003000 08:01 6294685    /usr/lib/libgmodule-2.0.so.0.2400.1
00c6e000-00c92000 r-xp 00000000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
00c92000-00c93000 r--p 00023000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
00c93000-00c94000 rw-p 00024000 08:01 6298189    /usr/lib/gio/modules/libgvfsdbus.so
00c97000-00cc5000 r-xp 00000000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
00cc5000-00cc6000 r--p 0002d000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
00cc6000-00cc7000 rw-p 0002e000 08:01 6294606    /usr/lib/libfontconfig.so.1.4.4
00cc7000-00cd8000 r-xp 00000000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
00cd8000-00cd9000 r--p 00011000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
00cd9000-00cda000 rw-p 00012000 08:01 6298188    /usr/lib/gio/modules/libgioremote-volume-monitor.so
00cda000-00cde000 r-xp 00000000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
00cde000-00cdf000 r--p 00003000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
00cdf000-00ce0000 rw-p 00004000 08:01 6294367    /usr/lib/libXxf86vm.so.1.0.0
00ce0000-00ce3000 r-xp 00000000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
00ce3000-00ce4000 r--p 00002000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
00ce4000-00ce5000 rw-p 00003000 08:01 8519752    /lib/libdrm_radeon.so.1.0.0
00ce9000-00cec000 r-xp 00000000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
00cec000-00ced000 r--p 00002000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
00ced000-00cee000 rw-p 00003000 08:01 6295317    /usr/lib/libxcb-render-util.so.0.0.0
00cee000-00cfc000 r-xp 00000000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00cfc000-00cfd000 r--p 0000d000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00cfd000-00cfe000 rw-p 0000e000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00cfe000-00d13000 r-xp 00000000 08:01 6296555    /usr/lib/libnssutil3.so
00d13000-00d16000 r--p 00014000 08:01 6296555    /usr/lib/libnssutil3.so
00d16000-00d17000 rw-p 00017000 08:01 6296555    /usr/lib/libnssutil3.so
00d17000-00d1a000 r-xp 00000000 08:01 8142926    /home/ben/.minecraft/bin/natives/libjinput-linux.so
00d1a000-00d1b000 r--p 00002000 08:01 8142926    /home/ben/.minecraft/bin/natives/libjinput-linux.so
00d1b000-00d1c000 rw-p 00003000 08:01 8142926    /home/ben/.minecraft/bin/natives/libjinput-linux.so
00d1c000-00d1f000 r-xp 00000000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00d1f000-00d20000 r--p 00003000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00d20000-00d21000 rw-p 00004000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00d21000-01174000 r-xp 00000000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01174000-01175000 ---p 00453000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01175000-0118c000 r--p 00453000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0118c000-01199000 rw-p 0046a000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01199000-015b5000 rw-p 00000000 00:00 0 
015b5000-0181e000 r-xp 00000000 08:01 6296477    /usr/lib/dri/r300_dri.so
0181e000-01822000 r--p 00269000 08:01 6296477    /usr/lib/dri/r300_dri.so
01822000-01824000 rw-p 0026d000 08:01 6296477    /usr/lib/dri/r300_dri.so
01824000-01833000 rw-p 00000000 00:00 0 
01c34000-01c7c000 r-xp 00000000 08:01 6295024    /usr/lib/nss/libfreebl3.so
01c7c000-01c7d000 r--p 00047000 08:01 6295024    /usr/lib/nss/libfreebl3.so
01c7d000-01c7e000 rw-p 00048000 08:01 6295024    /usr/lib/nss/libfreebl3.so
01c7e000-01c82000 rw-p 00000000 00:00 0 
02fe6000-03066000 r-xp 00000000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
03066000-03067000 r--p 0007f000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
03067000-03068000 rw-p 00080000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
03068000-03069000 rw-p 00000000 00:00 0 
03903000-03934000 r-xp 00000000 08:01 6291778    /usr/lib/libnspr4.so
03934000-03935000 r--p 00030000 08:01 6291778    /usr/lib/libnspr4.so
03935000-03936000 rw-p 00031000 08:01 6291778    /usr/lib/libnspr4.so
03936000-03938000 rw-p 00000000 00:00 0 
03cf4000-03d29000 r-xp 00000000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
03d29000-03d2a000 r--p 00035000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
03d2a000-03d2b000 rw-p 00036000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
03ee4000-042b1000 r-xp 00000000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
042b1000-042b5000 r--p 003cd000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
042b5000-042b7000 rw-p 003d1000 08:01 6294809    /usr/lib/libgtk-x11-2.0.so.0.2000.1
042b7000-042b9000 rw-p 00000000 00:00 0 
05904000-0590d000 r-xp 00000000 08:01 8519746    /lib/libdrm.so.2.4.0
0590d000-0590e000 r--p 00008000 08:01 8519746    /lib/libdrm.so.2.4.0
0590e000-0590f000 rw-p 00009000 08:01 8519746    /lib/libdrm.so.2.4.0
05b54000-05b82000 r-xp 00000000 08:01 6299071    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
05b82000-05b83000 r--p 0002d000 08:01 6299071    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
05b83000-05b84000 rw-p 0002e000 08:01 6299071    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
05b84000-05b86000 rw-p 00000000 00:00 0 
06c7a000-06d88000 r-xp 00000000 08:01 6296556    /usr/lib/libnss3.so
06d88000-06d89000 ---p 0010e000 08:01 6296556    /usr/lib/libnss3.so
06d89000-06d8c000 r--p 0010e000 08:01 6296556    /usr/lib/libnss3.so
06d8c000-06d8e000 rw-p 00111000 08:01 6296556    /usr/lib/libnss3.so
06ef0000-06f27000 r-xp 00000000 08:01 8519733    /lib/libdbus-1.so.3.4.0
06f27000-06f28000 r--p 00036000 08:01 8519733    /lib/libdbus-1.so.3.4.0
06f28000-06f29000 rw-p 00037000 08:01 8519733    /lib/libdbus-1.so.3.4.0
08048000-08051000 r-xp 00000000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
081d8000-08232000 r-xp 00000000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
08232000-08237000 r--p 00059000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
08237000-0823c000 rwxp 0005e000 08:01 6299197    /usr/lib/mesa/libGL.so.1.2
0823c000-0823d000 rwxp 00000000 00:00 0 
08645000-0870d000 r-xp 00000000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
0870d000-0870e000 r--p 000c7000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
0870e000-0870f000 rw-p 000c8000 08:01 8519767    /lib/libglib-2.0.so.0.2400.1
09312000-09369000 r-xp 00000000 08:01 8142931    /home/ben/.minecraft/bin/natives/liblwjgl.so
09369000-0936a000 r--p 00056000 08:01 8142931    /home/ben/.minecraft/bin/natives/liblwjgl.so
0936a000-0936b000 rw-p 00057000 08:01 8142931    /home/ben/.minecraft/bin/natives/liblwjgl.so
096b7000-0d17b000 rw-p 00000000 00:00 0          [heap]
6f940000-719f0000 rw-p 00000000 00:00 0 
719f0000-7a3e0000 rw-p 00000000 00:00 0 
7a3e0000-7e535000 rw-p 00000000 00:00 0 
7e535000-8f940000 rw-p 00000000 00:00 0 
8f940000-90540000 rw-p 00000000 00:00 0 
90540000-93940000 rw-p 00000000 00:00 0 
93940000-94099000 r--s 00001000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94099000-94340000 rw-p 00000000 00:00 0 
94340000-94a81000 rw-p 0075a000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94a81000-94f40000 rw-p 00000000 00:00 0 
94f40000-9503b000 rw-p 00e9b000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
9503b000-95340000 rw-p 00000000 00:00 0 
95340000-95348000 r-xs 00f96000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
95348000-95740000 rw-p 00000000 00:00 0 
ad9ef000-ad9f7000 rw-s 1db52d000 00:05 3563      /dev/dri/card0
ad9f7000-ad9ff000 rw-s 1db525000 00:05 3563      /dev/dri/card0
ad9ff000-ada07000 rw-s 1db51d000 00:05 3563      /dev/dri/card0
ada07000-ada0f000 rw-s 1db515000 00:05 3563      /dev/dri/card0
ada0f000-ada17000 rw-s 1db50d000 00:05 3563      /dev/dri/card0
ada17000-ada1f000 rw-s 1db505000 00:05 3563      /dev/dri/card0
ada1f000-ada27000 rw-s 1db4fd000 00:05 3563      /dev/dri/card0
ada27000-ada2f000 rw-s 1db4f5000 00:05 3563      /dev/dri/card0
ada2f000-ada37000 rw-s 1db4ed000 00:05 3563      /dev/dri/card0
ada37000-ada3f000 rw-s 1db4e5000 00:05 3563      /dev/dri/card0
ada3f000-ada47000 rw-s 1db4dd000 00:05 3563      /dev/dri/card0
ada47000-ada4f000 rw-s 1db4d5000 00:05 3563      /dev/dri/card0
ada4f000-ada57000 rw-s 1db4cd000 00:05 3563      /dev/dri/card0
ada57000-ada5f000 rw-s 1db4c5000 00:05 3563      /dev/dri/card0
ada5f000-ada67000 rw-s 1db4bd000 00:05 3563      /dev/dri/card0
ada67000-ada6f000 rw-s 1db4b5000 00:05 3563      /dev/dri/card0
ada6f000-ada77000 rw-s 1db4ad000 00:05 3563      /dev/dri/card0
ada77000-ada7f000 rw-s 1db4a5000 00:05 3563      /dev/dri/card0
ada7f000-ada87000 rw-s 1db49d000 00:05 3563      /dev/dri/card0
ada87000-ada8f000 rw-s 1db495000 00:05 3563      /dev/dri/card0
ada8f000-ada97000 rw-s 1db48d000 00:05 3563      /dev/dri/card0
ada97000-ada9f000 rw-s 1db485000 00:05 3563      /dev/dri/card0
ada9f000-adaa7000 rw-s 1db47d000 00:05 3563      /dev/dri/card0
adaa7000-adaaf000 rw-s 1db475000 00:05 3563      /dev/dri/card0
adaaf000-adab7000 rw-s 1db46d000 00:05 3563      /dev/dri/card0
adab7000-adabf000 rw-s 1db465000 00:05 3563      /dev/dri/card0
adabf000-adac7000 rw-s 1db45d000 00:05 3563      /dev/dri/card0
adac7000-adacf000 rw-s 1db438000 00:05 3563      /dev/dri/card0
adacf000-adad7000 rw-s 1db430000 00:05 3563      /dev/dri/card0
adad7000-adadf000 rw-s 1db428000 00:05 3563      /dev/dri/card0
adadf000-adae7000 rw-s 1db420000 00:05 3563      /dev/dri/card0
adae7000-adaef000 rw-s 1db418000 00:05 3563      /dev/dri/card0
adaef000-adaf7000 rw-s 1db410000 00:05 3563      /dev/dri/card0
adaf7000-adaff000 rw-s 1db455000 00:05 3563      /dev/dri/card0
adaff000-adb07000 rw-s 1db44d000 00:05 3563      /dev/dri/card0
adb07000-adb0f000 rw-s 1db445000 00:05 3563      /dev/dri/card0
adb0f000-adb17000 rw-s 1db407000 00:05 3563      /dev/dri/card0
adb17000-adb1f000 rw-s 1db3ff000 00:05 3563      /dev/dri/card0
adb1f000-adb27000 rw-s 1db3f7000 00:05 3563      /dev/dri/card0
adb27000-adb2f000 rw-s 1db3ef000 00:05 3563      /dev/dri/card0
adb2f000-adb37000 rw-s 1db3e7000 00:05 3563      /dev/dri/card0
adb37000-adb3f000 rw-s 1db3df000 00:05 3563      /dev/dri/card0
adb3f000-adb47000 rw-s 1db3d7000 00:05 3563      /dev/dri/card0
adb47000-adb4f000 rw-s 1db3cf000 00:05 3563      /dev/dri/card0
adb4f000-adb57000 rw-s 1db3c7000 00:05 3563      /dev/dri/card0
adb57000-adb5f000 rw-s 1db3bf000 00:05 3563      /dev/dri/card0
adb5f000-adb67000 rw-s 1db3b7000 00:05 3563      /dev/dri/card0
adb67000-adb6f000 rw-s 1db3af000 00:05 3563      /dev/dri/card0
adb6f000-adb77000 rw-s 1db3a7000 00:05 3563      /dev/dri/card0
adb77000-adb7f000 rw-s 1db39f000 00:05 3563      /dev/dri/card0
adb7f000-adb87000 rw-s 1db397000 00:05 3563      /dev/dri/card0
adb87000-adb8f000 rw-s 1db38f000 00:05 3563      /dev/dri/card0
adb8f000-adb97000 rw-s 1db387000 00:05 3563      /dev/dri/card0
adb97000-adb9f000 rw-s 1db37f000 00:05 3563      /dev/dri/card0
adb9f000-adba7000 rw-s 1db377000 00:05 3563      /dev/dri/card0
adba7000-adbaf000 rw-s 1db33a000 00:05 3563      /dev/dri/card0
adbaf000-adbb7000 rw-s 1db331000 00:05 3563      /dev/dri/card0
adbb7000-adbbf000 rw-s 1db329000 00:05 3563      /dev/dri/card0
adbbf000-adbc7000 rw-s 1db321000 00:05 3563      /dev/dri/card0
adbc7000-adbcf000 rw-s 1db319000 00:05 3563      /dev/dri/card0
adbcf000-adbd7000 rw-s 1db311000 00:05 3563      /dev/dri/card0
adbd7000-adbdf000 rw-s 1db36f000 00:05 3563      /dev/dri/card0
adbdf000-adbe7000 rw-s 1db367000 00:05 3563      /dev/dri/card0
adbe7000-adbef000 rw-s 1db35f000 00:05 3563      /dev/dri/card0
adbef000-adbf7000 rw-s 1db357000 00:05 3563      /dev/dri/card0
adbf7000-adbff000 rw-s 1db34f000 00:05 3563      /dev/dri/card0
adbff000-adc07000 rw-s 1db347000 00:05 3563      /dev/dri/card0
adc07000-adc0f000 rw-s 1db309000 00:05 3563      /dev/dri/card0
adc0f000-adc17000 rw-s 1db301000 00:05 3563      /dev/dri/card0
adc17000-adc1f000 rw-s 1db2f9000 00:05 3563      /dev/dri/card0
adc1f000-adc27000 rw-s 1db2f1000 00:05 3563      /dev/dri/card0
adc27000-adc2f000 rw-s 1db2e9000 00:05 3563      /dev/dri/card0
adc2f000-adc37000 rw-s 1db2e1000 00:05 3563      /dev/dri/card0
adc37000-adc3f000 rw-s 1db2d9000 00:05 3563      /dev/dri/card0
adc3f000-adc47000 rw-s 1db2d1000 00:05 3563      /dev/dri/card0
adc47000-adc4f000 rw-s 1db2c9000 00:05 3563      /dev/dri/card0
adc4f000-adc57000 rw-s 1db2c1000 00:05 3563      /dev/dri/card0
adc57000-adc5f000 rw-s 1db2b9000 00:05 3563      /dev/dri/card0
adc5f000-adc67000 rw-s 1db2b1000 00:05 3563      /dev/dri/card0
adc67000-adc6f000 rw-s 1db2a9000 00:05 3563      /dev/dri/card0
adc6f000-adc77000 rw-s 1db2a1000 00:05 3563      /dev/dri/card0
adc77000-adc7f000 rw-s 1db299000 00:05 3563      /dev/dri/card0
adc7f000-adc87000 rw-s 1db291000 00:05 3563      /dev/dri/card0
adc87000-adc8f000 rw-s 1db289000 00:05 3563      /dev/dri/card0
adc8f000-adc97000 rw-s 1db281000 00:05 3563      /dev/dri/card0
adc97000-adc9f000 rw-s 1db279000 00:05 3563      /dev/dri/card0
adc9f000-adca7000 rw-s 1db271000 00:05 3563      /dev/dri/card0
adca7000-adcaf000 rw-s 1db269000 00:05 3563      /dev/dri/card0
adcaf000-adcb7000 rw-s 1db261000 00:05 3563      /dev/dri/card0
adcb7000-adcbf000 rw-s 1db259000 00:05 3563      /dev/dri/card0
adcbf000-adcc7000 rw-s 1db251000 00:05 3563      /dev/dri/card0
adcc7000-adccf000 rw-s 1db249000 00:05 3563      /dev/dri/card0
adccf000-adcd7000 rw-s 1db241000 00:05 3563      /dev/dri/card0
adcd7000-adcdf000 rw-s 1db239000 00:05 3563      /dev/dri/card0
adcdf000-adce7000 rw-s 1db231000 00:05 3563      /dev/dri/card0
adce7000-adcef000 rw-s 1db229000 00:05 3563      /dev/dri/card0
adcef000-adcf7000 rw-s 1db221000 00:05 3563      /dev/dri/card0
adcf7000-adcff000 rw-s 1db219000 00:05 3563      /dev/dri/card0
adcff000-add07000 rw-s 1db211000 00:05 3563      /dev/dri/card0
add07000-add0f000 rw-s 1db209000 00:05 3563      /dev/dri/card0
add0f000-add17000 rw-s 1db201000 00:05 3563      /dev/dri/card0
add17000-add1f000 rw-s 1db1d3000 00:05 3563      /dev/dri/card0
add1f000-add27000 rw-s 1db1cb000 00:05 3563      /dev/dri/card0
add27000-add2f000 rw-s 1db1c3000 00:05 3563      /dev/dri/card0
add2f000-add37000 rw-s 1db1bb000 00:05 3563      /dev/dri/card0
add37000-add3f000 rw-s 1db1b3000 00:05 3563      /dev/dri/card0
add3f000-add47000 rw-s 1db1ab000 00:05 3563      /dev/dri/card0
add47000-add4f000 rw-s 1db1f9000 00:05 3563      /dev/dri/card0
add4f000-add57000 rw-s 1db1f1000 00:05 3563      /dev/dri/card0
add57000-add5f000 rw-s 1db1e9000 00:05 3563      /dev/dri/card0
add5f000-add67000 rw-s 1db1e1000 00:05 3563      /dev/dri/card0
add67000-add6f000 rw-s 1db1a3000 00:05 3563      /dev/dri/card0
add6f000-add77000 rw-s 1db19b000 00:05 3563      /dev/dri/card0
add77000-add7f000 rw-s 1db193000 00:05 3563      /dev/dri/card0
add7f000-add87000 rw-s 1db18b000 00:05 3563      /dev/dri/card0
add87000-add8f000 rw-s 1db183000 00:05 3563      /dev/dri/card0
add8f000-add97000 rw-s 1db17b000 00:05 3563      /dev/dri/card0
add97000-add9f000 rw-s 1db173000 00:05 3563      /dev/dri/card0
add9f000-adda7000 rw-s 1db15e000 00:05 3563      /dev/dri/card0
adda7000-addaf000 rw-s 1db156000 00:05 3563      /dev/dri/card0
addaf000-addb7000 rw-s 1db14e000 00:05 3563      /dev/dri/card0
addb7000-addbf000 rw-s 1db146000 00:05 3563      /dev/dri/card0
addbf000-addc7000 rw-s 1db13e000 00:05 3563      /dev/dri/card0
addc7000-addcf000 rw-s 1db136000 00:05 3563      /dev/dri/card0
addcf000-addd7000 rw-s 1db16b000 00:05 3563      /dev/dri/card0
addd7000-adddf000 rw-s 1db12d000 00:05 3563      /dev/dri/card0
adddf000-adde7000 rw-s 1db125000 00:05 3563      /dev/dri/card0
adde7000-addef000 rw-s 1db11d000 00:05 3563      /dev/dri/card0
addef000-addf7000 rw-s 1db115000 00:05 3563      /dev/dri/card0
addf7000-addff000 rw-s 1db10d000 00:05 3563      /dev/dri/card0
addff000-ade07000 rw-s 1db105000 00:05 3563      /dev/dri/card0
ade07000-ade0f000 rw-s 1db0fd000 00:05 3563      /dev/dri/card0
ade0f000-ade17000 rw-s 1db0f5000 00:05 3563      /dev/dri/card0
ade17000-ade1f000 rw-s 1db0ed000 00:05 3563      /dev/dri/card0
ade1f000-ade27000 rw-s 1db0e5000 00:05 3563      /dev/dri/card0
ade27000-ade2f000 rw-s 1db0dd000 00:05 3563      /dev/dri/card0
ade2f000-ade37000 rw-s 1db0d5000 00:05 3563      /dev/dri/card0
ade37000-ade3f000 rw-s 1db0cd000 00:05 3563      /dev/dri/card0
ade3f000-ade47000 rw-s 1db0c5000 00:05 3563      /dev/dri/card0
ade47000-ade4f000 rw-s 1db0bd000 00:05 3563      /dev/dri/card0
ade4f000-ade57000 rw-s 1db0b5000 00:05 3563      /dev/dri/card0
ade57000-ade5f000 rw-s 1db0ad000 00:05 3563      /dev/dri/card0
ade5f000-ade67000 rw-s 1db0a5000 00:05 3563      /dev/dri/card0
ade67000-ade6f000 rw-s 1db09d000 00:05 3563      /dev/dri/card0
ade6f000-ade77000 rw-s 1db095000 00:05 3563      /dev/dri/card0
ade77000-ade7f000 rw-s 1db08d000 00:05 3563      /dev/dri/card0
ade7f000-ade87000 rw-s 1db085000 00:05 3563      /dev/dri/card0
ade87000-ade8f000 rw-s 1db07d000 00:05 3563      /dev/dri/card0
ade8f000-ade97000 rw-s 1db075000 00:05 3563      /dev/dri/card0
ade97000-ade9f000 rw-s 1db06d000 00:05 3563      /dev/dri/card0
ade9f000-adea7000 rw-s 1db065000 00:05 3563      /dev/dri/card0
adea7000-adeaf000 rw-s 1db05d000 00:05 3563      /dev/dri/card0
adeaf000-adeb7000 rw-s 1db055000 00:05 3563      /dev/dri/card0
adeb7000-adebf000 rw-s 1db04d000 00:05 3563      /dev/dri/card0
adebf000-adec7000 rw-s 1dafd8000 00:05 3563      /dev/dri/card0
adec7000-adecf000 rw-s 1dafd0000 00:05 3563      /dev/dri/card0
adecf000-aded7000 rw-s 1dafc8000 00:05 3563      /dev/dri/card0
aded7000-adedf000 rw-s 1dafc0000 00:05 3563      /dev/dri/card0
adedf000-adee7000 rw-s 1dafb8000 00:05 3563      /dev/dri/card0
adee7000-adeef000 rw-s 1dafb0000 00:05 3563      /dev/dri/card0
adeef000-adef7000 rw-s 1db045000 00:05 3563      /dev/dri/card0
adef7000-adeff000 rw-s 1db03d000 00:05 3563      /dev/dri/card0
adeff000-adf07000 rw-s 1db035000 00:05 3563      /dev/dri/card0
adf07000-adf0f000 rw-s 1db02d000 00:05 3563      /dev/dri/card0
adf0f000-adf17000 rw-s 1db025000 00:05 3563      /dev/dri/card0
adf17000-adf1f000 rw-s 1db01d000 00:05 3563      /dev/dri/card0
adf1f000-adf27000 rw-s 1db015000 00:05 3563      /dev/dri/card0
adf27000-adf2f000 rw-s 1db00d000 00:05 3563      /dev/dri/card0
adf2f000-adf37000 rw-s 1db005000 00:05 3563      /dev/dri/card0
adf37000-adf3f000 rw-s 1daffd000 00:05 3563      /dev/dri/card0
adf3f000-adf47000 rw-s 1daff5000 00:05 3563      /dev/dri/card0
adf47000-adf4f000 rw-s 1dafed000 00:05 3563      /dev/dri/card0
adf4f000-adf57000 rw-s 1dafe5000 00:05 3563      /dev/dri/card0
adf57000-adf5f000 rw-s 1dafa7000 00:05 3563      /dev/dri/card0
adf5f000-adf6f000 rw-s 1daf97000 00:05 3563      /dev/dri/card0
adf6f000-adf77000 rw-s 1daf8f000 00:05 3563      /dev/dri/card0
adf77000-adf7f000 rw-s 1daf87000 00:05 3563      /dev/dri/card0
adf7f000-adf87000 rw-s 1daf7f000 00:05 3563      /dev/dri/card0
adf87000-adf8f000 rw-s 1daf77000 00:05 3563      /dev/dri/card0
adf8f000-adf97000 rw-s 1daf6f000 00:05 3563      /dev/dri/card0
adf97000-adf9f000 rw-s 1daf67000 00:05 3563      /dev/dri/card0
adf9f000-adfa7000 rw-s 1daf5f000 00:05 3563      /dev/dri/card0
adfa7000-adfaf000 rw-s 1daf57000 00:05 3563      /dev/dri/card0
adfaf000-adfb7000 rw-s 1daf4f000 00:05 3563      /dev/dri/card0
adfb7000-adfbf000 rw-s 1daf47000 00:05 3563      /dev/dri/card0
adfbf000-adfc7000 rw-s 1daf3f000 00:05 3563      /dev/dri/card0
adfc7000-adfcf000 rw-s 1daf37000 00:05 3563      /dev/dri/card0
adfcf000-adfd7000 rw-s 1daf2f000 00:05 3563      /dev/dri/card0
adfd7000-adfdf000 rw-s 1daf27000 00:05 3563      /dev/dri/card0
adfdf000-adfe7000 rw-s 1daf1f000 00:05 3563      /dev/dri/card0
adfe7000-adfef000 rw-s 1daf17000 00:05 3563      /dev/dri/card0
adfef000-adff7000 rw-s 1daf0f000 00:05 3563      /dev/dri/card0
adff7000-adfff000 rw-s 1daf07000 00:05 3563      /dev/dri/card0
adfff000-ae007000 rw-s 1daeff000 00:05 3563      /dev/dri/card0
ae007000-ae00f000 rw-s 1daef7000 00:05 3563      /dev/dri/card0
ae00f000-ae017000 rw-s 1daeef000 00:05 3563      /dev/dri/card0
ae017000-ae01f000 rw-s 1daee7000 00:05 3563      /dev/dri/card0
ae01f000-ae027000 rw-s 1daedf000 00:05 3563      /dev/dri/card0
ae027000-ae02f000 rw-s 1daed7000 00:05 3563      /dev/dri/card0
ae02f000-ae037000 rw-s 1daecf000 00:05 3563      /dev/dri/card0
ae037000-ae03f000 rw-s 1daec7000 00:05 3563      /dev/dri/card0
ae03f000-ae047000 rw-s 1daebf000 00:05 3563      /dev/dri/card0
ae047000-ae04f000 rw-s 1daeb7000 00:05 3563      /dev/dri/card0
ae04f000-ae057000 rw-s 1daeaf000 00:05 3563      /dev/dri/card0
ae057000-ae05f000 rw-s 1daea7000 00:05 3563      /dev/dri/card0
ae05f000-ae067000 rw-s 1dae9f000 00:05 3563      /dev/dri/card0
ae067000-ae06f000 rw-s 1dae97000 00:05 3563      /dev/dri/card0
ae06f000-ae077000 rw-s 1dae87000 00:05 3563      /dev/dri/card0
ae077000-ae07f000 rw-s 1dae7f000 00:05 3563      /dev/dri/card0
ae07f000-ae087000 rw-s 1dae77000 00:05 3563      /dev/dri/card0
ae087000-ae08f000 rw-s 1dae6f000 00:05 3563      /dev/dri/card0
ae08f000-ae097000 rw-s 1dae67000 00:05 3563      /dev/dri/card0
ae097000-ae09f000 rw-s 1dae5f000 00:05 3563      /dev/dri/card0
ae09f000-ae0a7000 rw-s 1dae57000 00:05 3563      /dev/dri/card0
ae0a7000-ae0af000 rw-s 1dae4f000 00:05 3563      /dev/dri/card0
ae0af000-ae0b7000 rw-s 1dae47000 00:05 3563      /dev/dri/card0
ae0b7000-ae0bf000 rw-s 1dae3f000 00:05 3563      /dev/dri/card0
ae0bf000-ae0c7000 rw-s 1dae37000 00:05 3563      /dev/dri/card0
ae0c7000-ae0cf000 rw-s 1dae2f000 00:05 3563      /dev/dri/card0
ae0cf000-ae0d7000 rw-s 1dae27000 00:05 3563      /dev/dri/card0
ae0d7000-ae0df000 rw-s 1dae1f000 00:05 3563      /dev/dri/card0
ae0df000-ae0e7000 rw-s 1dae17000 00:05 3563      /dev/dri/card0
ae0e7000-ae0ef000 rw-s 1dae0f000 00:05 3563      /dev/dri/card0
ae0ef000-ae0f7000 rw-s 1dae07000 00:05 3563      /dev/dri/card0
ae0f7000-ae0ff000 rw-s 1dadff000 00:05 3563      /dev/dri/card0
ae0ff000-ae107000 rw-s 1dadf7000 00:05 3563      /dev/dri/card0
ae107000-ae10f000 rw-s 1dadef000 00:05 3563      /dev/dri/card0
ae10f000-ae117000 rw-s 1dade7000 00:05 3563      /dev/dri/card0
ae117000-ae11f000 rw-s 1daddf000 00:05 3563      /dev/dri/card0
ae11f000-ae127000 rw-s 1dadd7000 00:05 3563      /dev/dri/card0
ae127000-ae12f000 rw-s 1dadcf000 00:05 3563      /dev/dri/card0
ae12f000-ae137000 rw-s 1dadc7000 00:05 3563      /dev/dri/card0
ae137000-ae13f000 rw-s 1dadbf000 00:05 3563      /dev/dri/card0
ae13f000-ae147000 rw-s 1dadb7000 00:05 3563      /dev/dri/card0
ae147000-ae14f000 rw-s 1dadaf000 00:05 3563      /dev/dri/card0
ae14f000-ae157000 rw-s 1dada7000 00:05 3563      /dev/dri/card0
ae157000-ae15f000 rw-s 1dad9f000 00:05 3563      /dev/dri/card0
ae15f000-ae167000 rw-s 1dad97000 00:05 3563      /dev/dri/card0
ae167000-ae16f000 rw-s 1dad8f000 00:05 3563      /dev/dri/card0
ae16f000-ae177000 rw-s 1dad87000 00:05 3563      /dev/dri/card0
ae177000-ae17f000 rw-s 1dad7f000 00:05 3563      /dev/dri/card0
ae17f000-ae187000 rw-s 1dad77000 00:05 3563      /dev/dri/card0
ae187000-ae18f000 rw-s 1dad6f000 00:05 3563      /dev/dri/card0
ae18f000-ae197000 rw-s 1dad67000 00:05 3563      /dev/dri/card0
ae197000-ae19f000 rw-s 1dad5f000 00:05 3563      /dev/dri/card0
ae19f000-ae1a7000 rw-s 1dad57000 00:05 3563      /dev/dri/card0
ae1a7000-ae1af000 rw-s 1dad4f000 00:05 3563      /dev/dri/card0
ae1af000-ae1b7000 rw-s 1dad47000 00:05 3563      /dev/dri/card0
ae1b7000-ae1bf000 rw-s 1dad3f000 00:05 3563      /dev/dri/card0
ae1bf000-ae1c7000 rw-s 1dad37000 00:05 3563      /dev/dri/card0
ae1c7000-ae1cf000 rw-s 1dad2f000 00:05 3563      /dev/dri/card0
ae1cf000-ae1d7000 rw-s 1dad27000 00:05 3563      /dev/dri/card0
ae1d7000-ae1df000 rw-s 1dad1f000 00:05 3563      /dev/dri/card0
ae1df000-ae1e7000 rw-s 1dad17000 00:05 3563      /dev/dri/card0
ae1e7000-ae1ef000 rw-s 1dad0f000 00:05 3563      /dev/dri/card0
ae1ef000-ae1f7000 rw-s 1dad07000 00:05 3563      /dev/dri/card0
ae1f7000-ae1ff000 rw-s 1dacff000 00:05 3563      /dev/dri/card0
ae1ff000-ae207000 rw-s 1dacf7000 00:05 3563      /dev/dri/card0
ae207000-ae20f000 rw-s 1dacef000 00:05 3563      /dev/dri/card0
ae20f000-ae217000 rw-s 1dace7000 00:05 3563      /dev/dri/card0
ae217000-ae21f000 rw-s 1dac11000 00:05 3563      /dev/dri/card0
ae21f000-ae227000 rw-s 1dac09000 00:05 3563      /dev/dri/card0
ae227000-ae22f000 rw-s 1dac01000 00:05 3563      /dev/dri/card0
ae22f000-ae237000 rw-s 1dabf9000 00:05 3563      /dev/dri/card0
ae237000-ae23f000 rw-s 1dabf1000 00:05 3563      /dev/dri/card0
ae23f000-ae247000 rw-s 1dabe9000 00:05 3563      /dev/dri/card0
ae247000-ae257000 rw-s 1dacd7000 00:05 3563      /dev/dri/card0
ae257000-ae267000 rw-s 1dacc7000 00:05 3563      /dev/dri/card0
ae267000-ae26f000 rw-s 1dacbf000 00:05 3563      /dev/dri/card0
ae26f000-ae277000 rw-s 1dacb7000 00:05 3563      /dev/dri/card0
ae277000-ae27f000 rw-s 1dacaf000 00:05 3563      /dev/dri/card0
ae27f000-ae287000 rw-s 1daca7000 00:05 3563      /dev/dri/card0
ae287000-ae28f000 rw-s 1dac9f000 00:05 3563      /dev/dri/card0
ae28f000-ae297000 rw-s 1dac97000 00:05 3563      /dev/dri/card0
ae297000-ae29f000 rw-s 1dac8f000 00:05 3563      /dev/dri/card0
ae29f000-ae2a7000 rw-s 1dac87000 00:05 3563      /dev/dri/card0
ae2a7000-ae2af000 rw-s 1dac7f000 00:05 3563      /dev/dri/card0
ae2af000-ae2b7000 rw-s 1dac77000 00:05 3563      /dev/dri/card0
ae2b7000-ae2bf000 rw-s 1dac6f000 00:05 3563      /dev/dri/card0
ae2bf000-ae2c7000 rw-s 1dac67000 00:05 3563      /dev/dri/card0
ae2c7000-ae2cf000 rw-s 1dac5f000 00:05 3563      /dev/dri/card0
ae2cf000-ae2d7000 rw-s 1dac57000 00:05 3563      /dev/dri/card0
ae2d7000-ae2df000 rw-s 1dac4f000 00:05 3563      /dev/dri/card0
ae2df000-ae2e7000 rw-s 1dac47000 00:05 3563      /dev/dri/card0
ae2e7000-ae2ef000 rw-s 1dac3f000 00:05 3563      /dev/dri/card0
ae2ef000-ae2f7000 rw-s 1dac37000 00:05 3563      /dev/dri/card0
ae2f7000-ae2ff000 rw-s 1dac2f000 00:05 3563      /dev/dri/card0
ae2ff000-ae307000 rw-s 1dac27000 00:05 3563      /dev/dri/card0
ae307000-ae30f000 rw-s 1dac1f000 00:05 3563      /dev/dri/card0
ae30f000-ae317000 rw-s 1dabe1000 00:05 3563      /dev/dri/card0
ae317000-ae31f000 rw-s 1dae8f000 00:05 3563      /dev/dri/card0
ae31f000-ae327000 rw-s 1da917000 00:05 3563      /dev/dri/card0
ae327000-ae32f000 rw-s 1dabc9000 00:05 3563      /dev/dri/card0
ae32f000-ae337000 rw-s 1dabc1000 00:05 3563      /dev/dri/card0
ae337000-ae33f000 rw-s 1dabb9000 00:05 3563      /dev/dri/card0
ae33f000-ae347000 rw-s 1dabb1000 00:05 3563      /dev/dri/card0
ae347000-ae34f000 rw-s 1daba9000 00:05 3563      /dev/dri/card0
ae34f000-ae357000 rw-s 1daba1000 00:05 3563      /dev/dri/card0
ae357000-ae35f000 rw-s 1dab99000 00:05 3563      /dev/dri/card0
ae35f000-ae367000 rw-s 1dab91000 00:05 3563      /dev/dri/card0
ae367000-ae36f000 rw-s 1dab89000 00:05 3563      /dev/dri/card0
ae36f000-ae377000 rw-s 1dab81000 00:05 3563      /dev/dri/card0
ae377000-ae37f000 rw-s 1dab79000 00:05 3563      /dev/dri/card0
ae37f000-ae387000 rw-s 1dab71000 00:05 3563      /dev/dri/card0
ae387000-ae38f000 rw-s 1dab69000 00:05 3563      /dev/dri/card0
ae38f000-ae397000 rw-s 1dab61000 00:05 3563      /dev/dri/card0
ae397000-ae39f000 rw-s 1dab59000 00:05 3563      /dev/dri/card0
ae39f000-ae3a7000 rw-s 1dab51000 00:05 3563      /dev/dri/card0
ae3a7000-ae3af000 rw-s 1dab49000 00:05 3563      /dev/dri/card0
ae3af000-ae3b7000 rw-s 1dab41000 00:05 3563      /dev/dri/card0
ae3b7000-ae3bf000 rw-s 1dab39000 00:05 3563      /dev/dri/card0
ae3bf000-ae3c7000 rw-s 1dab31000 00:05 3563      /dev/dri/card0
ae3c7000-ae3cf000 rw-s 1dab29000 00:05 3563      /dev/dri/card0
ae3cf000-ae3d7000 rw-s 1dab21000 00:05 3563      /dev/dri/card0
ae3d7000-ae3df000 rw-s 1dab19000 00:05 3563      /dev/dri/card0
ae3df000-ae3e7000 rw-s 1dab11000 00:05 3563      /dev/dri/card0
ae3e7000-ae3ef000 rw-s 1dab09000 00:05 3563      /dev/dri/card0
ae3ef000-ae3f7000 rw-s 1dab01000 00:05 3563      /dev/dri/card0
ae3f7000-ae3ff000 rw-s 1daaf9000 00:05 3563      /dev/dri/card0
ae3ff000-ae407000 rw-s 1daab3000 00:05 3563      /dev/dri/card0
ae407000-ae40f000 rw-s 1daaab000 00:05 3563      /dev/dri/card0
ae40f000-ae417000 rw-s 1daaa3000 00:05 3563      /dev/dri/card0
ae417000-ae41f000 rw-s 1daa9b000 00:05 3563      /dev/dri/card0
ae41f000-ae427000 rw-s 1daa93000 00:05 3563      /dev/dri/card0
ae427000-ae42f000 rw-s 1daa8b000 00:05 3563      /dev/dri/card0
ae42f000-ae437000 rw-s 1daaf1000 00:05 3563      /dev/dri/card0
ae437000-ae43f000 rw-s 1daae9000 00:05 3563      /dev/dri/card0
ae43f000-ae447000 rw-s 1daae1000 00:05 3563      /dev/dri/card0
ae447000-ae44f000 rw-s 1daad9000 00:05 3563      /dev/dri/card0
ae44f000-ae457000 rw-s 1daad1000 00:05 3563      /dev/dri/card0
ae457000-ae45f000 rw-s 1daac9000 00:05 3563      /dev/dri/card0
ae45f000-ae467000 rw-s 1daac1000 00:05 3563      /dev/dri/card0
ae467000-ae46f000 rw-s 1daa83000 00:05 3563      /dev/dri/card0
ae46f000-ae477000 rw-s 1daa7b000 00:05 3563      /dev/dri/card0
ae477000-ae47f000 rw-s 1daa73000 00:05 3563      /dev/dri/card0
ae47f000-ae487000 rw-s 1daa6b000 00:05 3563      /dev/dri/card0
ae487000-ae48f000 rw-s 1daa63000 00:05 3563      /dev/dri/card0
ae48f000-ae497000 rw-s 1daa5b000 00:05 3563      /dev/dri/card0
ae497000-ae49f000 rw-s 1daa53000 00:05 3563      /dev/dri/card0
ae49f000-ae4a7000 rw-s 1daa4b000 00:05 3563      /dev/dri/card0
ae4a7000-ae4af000 rw-s 1daa43000 00:05 3563      /dev/dri/card0
ae4af000-ae4b7000 rw-s 1daa3b000 00:05 3563      /dev/dri/card0
ae4b7000-ae4bf000 rw-s 1daa33000 00:05 3563      /dev/dri/card0
ae4bf000-ae4c7000 rw-s 1daa2b000 00:05 3563      /dev/dri/card0
ae4c7000-ae4cf000 rw-s 1daa23000 00:05 3563      /dev/dri/card0
ae4cf000-ae4d7000 rw-s 1daa1b000 00:05 3563      /dev/dri/card0
ae4d7000-ae4df000 rw-s 1daa0b000 00:05 3563      /dev/dri/card0
ae4df000-ae4e7000 rw-s 1daa03000 00:05 3563      /dev/dri/card0
ae4e7000-ae4ef000 rw-s 1da9fb000 00:05 3563      /dev/dri/card0
ae4ef000-ae4f7000 rw-s 1da9f3000 00:05 3563      /dev/dri/card0
ae4f7000-ae4ff000 rw-s 1da9eb000 00:05 3563      /dev/dri/card0
ae4ff000-ae507000 rw-s 1da9e3000 00:05 3563      /dev/dri/card0
ae507000-ae50f000 rw-s 1da9db000 00:05 3563      /dev/dri/card0
ae50f000-ae517000 rw-s 1da9d3000 00:05 3563      /dev/dri/card0
ae517000-ae51f000 rw-s 1da9ae000 00:05 3563      /dev/dri/card0
ae51f000-ae527000 rw-s 1da9a6000 00:05 3563      /dev/dri/card0
ae527000-ae52f000 rw-s 1da99e000 00:05 3563      /dev/dri/card0
ae52f000-ae537000 rw-s 1da996000 00:05 3563      /dev/dri/card0
ae537000-ae53f000 rw-s 1da98e000 00:05 3563      /dev/dri/card0
ae53f000-ae547000 rw-s 1da986000 00:05 3563      /dev/dri/card0
ae547000-ae54f000 rw-s 1da9cb000 00:05 3563      /dev/dri/card0
ae54f000-ae557000 rw-s 1da9c3000 00:05 3563      /dev/dri/card0
ae557000-ae55f000 rw-s 1da9bb000 00:05 3563      /dev/dri/card0
ae55f000-ae567000 rw-s 1da949000 00:05 3563      /dev/dri/card0
ae567000-ae56f000 rw-s 1da941000 00:05 3563      /dev/dri/card0
ae56f000-ae577000 rw-s 1da937000 00:05 3563      /dev/dri/card0
ae577000-ae57f000 rw-s 1da92f000 00:05 3563      /dev/dri/card0
ae57f000-ae587000 rw-s 1da927000 00:05 3563      /dev/dri/card0
ae587000-ae58f000 rw-s 1da91f000 00:05 3563      /dev/dri/card0
ae58f000-ae597000 rw-s 1da97d000 00:05 3563      /dev/dri/card0
ae597000-ae59f000 rw-s 1da975000 00:05 3563      /dev/dri/card0
ae59f000-ae5a7000 rw-s 1da96d000 00:05 3563      /dev/dri/card0
ae5a7000-ae5af000 rw-s 1da965000 00:05 3563      /dev/dri/card0
ae5af000-ae5b7000 rw-s 1da95d000 00:05 3563      /dev/dri/card0
ae5b7000-ae5bf000 rw-s 1da955000 00:05 3563      /dev/dri/card0
ae5bf000-ae5cf000 rw-s 1da907000 00:05 3563      /dev/dri/card0
ae5cf000-ae5d7000 rw-s 1da8ff000 00:05 3563      /dev/dri/card0
ae5d7000-ae5df000 rw-s 1dabd2000 00:05 3563      /dev/dri/card0
ae5df000-ae5e7000 rw-s 1da8f7000 00:05 3563      /dev/dri/card0
ae5e7000-ae5ef000 rw-s 1da8ef000 00:05 3563      /dev/dri/card0
ae5ef000-ae5f7000 rw-s 1da8e7000 00:05 3563      /dev/dri/card0
ae5f7000-ae5ff000 rw-s 1da8df000 00:05 3563      /dev/dri/card0
ae5ff000-ae607000 rw-s 1da8d7000 00:05 3563      /dev/dri/card0
ae607000-ae60f000 rw-s 1da8cf000 00:05 3563      /dev/dri/card0
ae60f000-ae617000 rw-s 1da8c7000 00:05 3563      /dev/dri/card0
ae617000-ae61f000 rw-s 1da8bf000 00:05 3563      /dev/dri/card0
ae61f000-ae627000 rw-s 1da8b7000 00:05 3563      /dev/dri/card0
ae627000-ae62f000 rw-s 1da8af000 00:05 3563      /dev/dri/card0
ae62f000-ae637000 rw-s 1da8a7000 00:05 3563      /dev/dri/card0
ae637000-ae63f000 rw-s 1da89f000 00:05 3563      /dev/dri/card0
ae63f000-ae647000 rw-s 1da897000 00:05 3563      /dev/dri/card0
ae647000-ae64f000 rw-s 1da88f000 00:05 3563      /dev/dri/card0
ae64f000-ae657000 rw-s 1da887000 00:05 3563      /dev/dri/card0
ae657000-ae65f000 rw-s 1da87f000 00:05 3563      /dev/dri/card0
ae65f000-ae667000 rw-s 1da877000 00:05 3563      /dev/dri/card0
ae667000-ae66f000 rw-s 1da86f000 00:05 3563      /dev/dri/card0
ae66f000-ae677000 rw-s 1da867000 00:05 3563      /dev/dri/card0
ae677000-ae67f000 rw-s 1da85f000 00:05 3563      /dev/dri/card0
ae67f000-ae687000 rw-s 1da857000 00:05 3563      /dev/dri/card0
ae687000-ae68f000 rw-s 1da84f000 00:05 3563      /dev/dri/card0
ae68f000-ae697000 rw-s 1da847000 00:05 3563      /dev/dri/card0
ae697000-ae69f000 rw-s 1da83f000 00:05 3563      /dev/dri/card0
ae69f000-ae6a7000 rw-s 1da837000 00:05 3563      /dev/dri/card0
ae6a7000-ae6af000 rw-s 1da82f000 00:05 3563      /dev/dri/card0
ae6af000-ae6b7000 rw-s 1da827000 00:05 3563      /dev/dri/card0
ae6b7000-ae6bf000 rw-s 1da81f000 00:05 3563      /dev/dri/card0
ae6bf000-ae6c7000 rw-s 1da817000 00:05 3563      /dev/dri/card0
ae6c7000-ae6cf000 rw-s 1da80f000 00:05 3563      /dev/dri/card0
ae6cf000-ae6d7000 rw-s 1da807000 00:05 3563      /dev/dri/card0
ae6d7000-ae6df000 rw-s 1da7ff000 00:05 3563      /dev/dri/card0
ae6df000-ae6e7000 rw-s 1da7f7000 00:05 3563      /dev/dri/card0
ae6e7000-ae6ef000 rw-s 1da7ef000 00:05 3563      /dev/dri/card0
ae6ef000-ae6f7000 rw-s 1da7e7000 00:05 3563      /dev/dri/card0
ae6f7000-ae6ff000 rw-s 1da7df000 00:05 3563      /dev/dri/card0
ae6ff000-ae707000 rw-s 1da7d7000 00:05 3563      /dev/dri/card0
ae707000-ae70f000 rw-s 1da7cf000 00:05 3563      /dev/dri/card0
ae70f000-ae717000 rw-s 1da7c7000 00:05 3563      /dev/dri/card0
ae717000-ae71f000 rw-s 1da7bf000 00:05 3563      /dev/dri/card0
ae71f000-ae727000 rw-s 1da7b7000 00:05 3563      /dev/dri/card0
ae727000-ae72f000 rw-s 1da7af000 00:05 3563      /dev/dri/card0
ae72f000-ae737000 rw-s 1da7a7000 00:05 3563      /dev/dri/card0
ae737000-ae73f000 rw-s 1da79f000 00:05 3563      /dev/dri/card0
ae73f000-ae747000 rw-s 1da797000 00:05 3563      /dev/dri/card0
ae747000-ae74f000 rw-s 1da78f000 00:05 3563      /dev/dri/card0
ae74f000-ae757000 rw-s 1da787000 00:05 3563      /dev/dri/card0
ae757000-ae75f000 rw-s 1da77f000 00:05 3563      /dev/dri/card0
ae75f000-ae767000 rw-s 1da777000 00:05 3563      /dev/dri/card0
ae767000-ae76f000 rw-s 1da76f000 00:05 3563      /dev/dri/card0
ae76f000-ae777000 rw-s 1da767000 00:05 3563      /dev/dri/card0
ae777000-ae77f000 rw-s 1da75f000 00:05 3563      /dev/dri/card0
ae77f000-ae787000 rw-s 1da719000 00:05 3563      /dev/dri/card0
ae787000-ae78f000 rw-s 1da711000 00:05 3563      /dev/dri/card0
ae78f000-ae797000 rw-s 1da709000 00:05 3563      /dev/dri/card0
ae797000-ae79f000 rw-s 1da701000 00:05 3563      /dev/dri/card0
ae79f000-ae7a7000 rw-s 1da6f9000 00:05 3563      /dev/dri/card0
ae7a7000-ae7af000 rw-s 1da6f1000 00:05 3563      /dev/dri/card0
ae7af000-ae7b7000 rw-s 1da757000 00:05 3563      /dev/dri/card0
ae7b7000-ae7bf000 rw-s 1da74f000 00:05 3563      /dev/dri/card0
ae7bf000-ae7c7000 rw-s 1da747000 00:05 3563      /dev/dri/card0
ae7c7000-ae7cf000 rw-s 1da73f000 00:05 3563      /dev/dri/card0
ae7cf000-ae7d7000 rw-s 1da737000 00:05 3563      /dev/dri/card0
ae7d7000-ae7df000 rw-s 1da72f000 00:05 3563      /dev/dri/card0
ae7df000-ae7e7000 rw-s 1da721000 00:05 3563      /dev/dri/card0
ae7e7000-ae7ef000 rw-s 1da6e9000 00:05 3563      /dev/dri/card0
ae7ef000-ae7f7000 rw-s 1da6e1000 00:05 3563      /dev/dri/card0
ae7f7000-ae7ff000 rw-s 1da6d9000 00:05 3563      /dev/dri/card0
ae7ff000-ae807000 rw-s 1da6d1000 00:05 3563      /dev/dri/card0
ae807000-ae80f000 rw-s 1da6c9000 00:05 3563      /dev/dri/card0
ae80f000-ae817000 rw-s 1da6c1000 00:05 3563      /dev/dri/card0
ae817000-ae81f000 rw-s 1da6b9000 00:05 3563      /dev/dri/card0
ae81f000-ae827000 rw-s 1da6b1000 00:05 3563      /dev/dri/card0
ae827000-ae82f000 rw-s 1da6a9000 00:05 3563      /dev/dri/card0
ae82f000-ae837000 rw-s 1da6a1000 00:05 3563      /dev/dri/card0
ae837000-ae83f000 rw-s 1da699000 00:05 3563      /dev/dri/card0
ae83f000-ae847000 rw-s 1da691000 00:05 3563      /dev/dri/card0
ae847000-ae84f000 rw-s 1da689000 00:05 3563      /dev/dri/card0
ae84f000-ae857000 rw-s 1da681000 00:05 3563      /dev/dri/card0
ae857000-ae85f000 rw-s 1da679000 00:05 3563      /dev/dri/card0
ae85f000-ae867000 rw-s 1da671000 00:05 3563      /dev/dri/card0
ae867000-ae86f000 rw-s 1da63c000 00:05 3563      /dev/dri/card0
ae86f000-ae877000 rw-s 1da634000 00:05 3563      /dev/dri/card0
ae877000-ae87f000 rw-s 1da62c000 00:05 3563      /dev/dri/card0
ae87f000-ae887000 rw-s 1da624000 00:05 3563      /dev/dri/card0
ae887000-ae88f000 rw-s 1da61c000 00:05 3563      /dev/dri/card0
ae88f000-ae897000 rw-s 1da614000 00:05 3563      /dev/dri/card0
ae897000-ae89f000 rw-s 1da669000 00:05 3563      /dev/dri/card0
ae89f000-ae8a7000 rw-s 1da661000 00:05 3563      /dev/dri/card0
ae8a7000-ae8af000 rw-s 1da659000 00:05 3563      /dev/dri/card0
ae8af000-ae8b7000 rw-s 1da651000 00:05 3563      /dev/dri/card0
ae8b7000-ae8bf000 rw-s 1da649000 00:05 3563      /dev/dri/card0
ae8bf000-ae8c7000 rw-s 1da60b000 00:05 3563      /dev/dri/card0
ae8c7000-ae8cf000 rw-s 1da603000 00:05 3563      /dev/dri/card0
ae8cf000-ae8d7000 rw-s 1da5fb000 00:05 3563      /dev/dri/card0
ae8d7000-ae8df000 rw-s 1da2d5000 00:05 3563      /dev/dri/card0
ae8df000-ae8e7000 rw-s 1da5f3000 00:05 3563      /dev/dri/card0
ae8e7000-ae8ef000 rw-s 1da5eb000 00:05 3563      /dev/dri/card0
ae8ef000-ae8f7000 rw-s 1da5e3000 00:05 3563      /dev/dri/card0
ae8f7000-ae8ff000 rw-s 1da5db000 00:05 3563      /dev/dri/card0
ae8ff000-ae907000 rw-s 1da5d3000 00:05 3563      /dev/dri/card0
ae907000-ae90f000 rw-s 1da5cb000 00:05 3563      /dev/dri/card0
ae90f000-ae917000 rw-s 1da5c3000 00:05 3563      /dev/dri/card0
ae917000-ae91f000 rw-s 1da5bb000 00:05 3563      /dev/dri/card0
ae91f000-ae927000 rw-s 1da5b3000 00:05 3563      /dev/dri/card0
ae927000-ae92f000 rw-s 1da5ab000 00:05 3563      /dev/dri/card0
ae92f000-ae937000 rw-s 1da5a3000 00:05 3563      /dev/dri/card0
ae937000-ae93f000 rw-s 1da526000 00:05 3563      /dev/dri/card0
ae93f000-ae947000 rw-s 1da51e000 00:05 3563      /dev/dri/card0
ae947000-ae94f000 rw-s 1da516000 00:05 3563      /dev/dri/card0
ae94f000-ae957000 rw-s 1da50e000 00:05 3563      /dev/dri/card0
ae957000-ae95f000 rw-s 1da506000 00:05 3563      /dev/dri/card0
ae95f000-ae967000 rw-s 1da4fe000 00:05 3563      /dev/dri/card0
ae967000-ae96f000 rw-s 1da59b000 00:05 3563      /dev/dri/card0
ae96f000-ae977000 rw-s 1da593000 00:05 3563      /dev/dri/card0
ae977000-ae97f000 rw-s 1da58b000 00:05 3563      /dev/dri/card0
ae97f000-ae987000 rw-s 1da583000 00:05 3563      /dev/dri/card0
ae987000-ae98f000 rw-s 1da57b000 00:05 3563      /dev/dri/card0
ae98f000-ae997000 rw-s 1da573000 00:05 3563      /dev/dri/card0
ae997000-ae99f000 rw-s 1da56b000 00:05 3563      /dev/dri/card0
ae99f000-ae9a7000 rw-s 1da563000 00:05 3563      /dev/dri/card0
ae9a7000-ae9af000 rw-s 1da55b000 00:05 3563      /dev/dri/card0
ae9af000-ae9b7000 rw-s 1da2cd000 00:05 3563      /dev/dri/card0
ae9b7000-ae9bf000 rw-s 1da54e000 00:05 3563      /dev/dri/card0
ae9bf000-ae9c7000 rw-s 1da546000 00:05 3563      /dev/dri/card0
ae9c7000-ae9cf000 rw-s 1da53e000 00:05 3563      /dev/dri/card0
ae9cf000-ae9d7000 rw-s 1da4f5000 00:05 3563      /dev/dri/card0
ae9d7000-ae9df000 rw-s 1da4ed000 00:05 3563      /dev/dri/card0
ae9df000-ae9e7000 rw-s 1da4e5000 00:05 3563      /dev/dri/card0
ae9e7000-ae9ef000 rw-s 1da4dd000 00:05 3563      /dev/dri/card0
ae9ef000-ae9f7000 rw-s 1da4d5000 00:05 3563      /dev/dri/card0
ae9f7000-ae9ff000 rw-s 1da4cd000 00:05 3563      /dev/dri/card0
ae9ff000-aea07000 rw-s 1da4c5000 00:05 3563      /dev/dri/card0
aea07000-aea0f000 rw-s 1da4bd000 00:05 3563      /dev/dri/card0
aea0f000-aea17000 rw-s 1da4b5000 00:05 3563      /dev/dri/card0
aea17000-aea1f000 rw-s 1da4ad000 00:05 3563      /dev/dri/card0
aea1f000-aea27000 rw-s 1da4a5000 00:05 3563      /dev/dri/card0
aea27000-aea2f000 rw-s 1da49d000 00:05 3563      /dev/dri/card0
aea2f000-aea37000 rw-s 1da495000 00:05 3563      /dev/dri/card0
aea37000-aea3f000 rw-s 1da48d000 00:05 3563      /dev/dri/card0
aea3f000-aea47000 rw-s 1da485000 00:05 3563      /dev/dri/card0
aea47000-aea4f000 rw-s 1da47d000 00:05 3563      /dev/dri/card0
aea4f000-aea57000 rw-s 1da475000 00:05 3563      /dev/dri/card0
aea57000-aea5f000 rw-s 1da46d000 00:05 3563      /dev/dri/card0
aea5f000-aea67000 rw-s 1da465000 00:05 3563      /dev/dri/card0
aea67000-aea6f000 rw-s 1da45d000 00:05 3563      /dev/dri/card0
aea6f000-aea77000 rw-s 1da455000 00:05 3563      /dev/dri/card0
aea77000-aea7f000 rw-s 1da44d000 00:05 3563      /dev/dri/card0
aea7f000-aea87000 rw-s 1da445000 00:05 3563      /dev/dri/card0
aea87000-aea8f000 rw-s 1da43d000 00:05 3563      /dev/dri/card0
aea8f000-aea97000 rw-s 1da435000 00:05 3563      /dev/dri/card0
aea97000-aea9f000 rw-s 1da42d000 00:05 3563      /dev/dri/card0
aea9f000-aeaa7000 rw-s 1da425000 00:05 3563      /dev/dri/card0
aeaa7000-aeaaf000 rw-s 1da41d000 00:05 3563      /dev/dri/card0
aeaaf000-aeab7000 rw-s 1da415000 00:05 3563      /dev/dri/card0
aeab7000-aeabf000 rw-s 1da40d000 00:05 3563      /dev/dri/card0
aeabf000-aeac7000 rw-s 1da405000 00:05 3563      /dev/dri/card0
aeac7000-aeacf000 rw-s 1da3fd000 00:05 3563      /dev/dri/card0
aeacf000-aead7000 rw-s 1da3f5000 00:05 3563      /dev/dri/card0
aead7000-aeadf000 rw-s 1da3ed000 00:05 3563      /dev/dri/card0
aeadf000-aeae7000 rw-s 1da3e5000 00:05 3563      /dev/dri/card0
aeae7000-aeaef000 rw-s 1da3dd000 00:05 3563      /dev/dri/card0
aeaef000-aeaf7000 rw-s 1da3d5000 00:05 3563      /dev/dri/card0
aeaf7000-aeaff000 rw-s 1da3cd000 00:05 3563      /dev/dri/card0
aeaff000-aeb07000 rw-s 1da3c5000 00:05 3563      /dev/dri/card0
aeb07000-aeb0f000 rw-s 1da3bd000 00:05 3563      /dev/dri/card0
aeb0f000-aeb17000 rw-s 1da3b5000 00:05 3563      /dev/dri/card0
aeb17000-aeb1f000 rw-s 1da3ad000 00:05 3563      /dev/dri/card0
aeb1f000-aeb27000 rw-s 1da3a5000 00:05 3563      /dev/dri/card0
aeb27000-aeb2f000 rw-s 1da39d000 00:05 3563      /dev/dri/card0
aeb2f000-aeb37000 rw-s 1da395000 00:05 3563      /dev/dri/card0
aeb37000-aeb3f000 rw-s 1da38d000 00:05 3563      /dev/dri/card0
aeb3f000-aeb47000 rw-s 1da385000 00:05 3563      /dev/dri/card0
aeb47000-aeb4f000 rw-s 1da37d000 00:05 3563      /dev/dri/card0
aeb4f000-aeb52000 rw-s 1da0c9000 00:05 3563      /dev/dri/card0
aeb52000-aeb55000 rw-s 1da05e000 00:05 3563      /dev/dri/card0
aeb55000-aeb58000 rw-s 1da05b000 00:05 3563      /dev/dri/card0
aeb58000-aeb60000 rw-s 1da375000 00:05 3563      /dev/dri/card0
aeb60000-aeb68000 rw-s 1da36d000 00:05 3563      /dev/dri/card0
aeb68000-aeb70000 rw-s 1da365000 00:05 3563      /dev/dri/card0
aeb70000-aeb78000 rw-s 1da35d000 00:05 3563      /dev/dri/card0
aeb78000-aeb80000 rw-s 1da355000 00:05 3563      /dev/dri/card0
aeb80000-aeb88000 rw-s 1da34d000 00:05 3563      /dev/dri/card0
aeb88000-aeb90000 rw-s 1da345000 00:05 3563      /dev/dri/card0
aeb90000-aeb98000 rw-s 1da33d000 00:05 3563      /dev/dri/card0
aeb98000-aeba0000 rw-s 1da335000 00:05 3563      /dev/dri/card0
aeba0000-aeba8000 rw-s 1da32d000 00:05 3563      /dev/dri/card0
aeba8000-aebb0000 rw-s 1da325000 00:05 3563      /dev/dri/card0
aebb0000-aebb8000 rw-s 1da31d000 00:05 3563      /dev/dri/card0
aebb8000-aebc0000 rw-s 1da315000 00:05 3563      /dev/dri/card0
aebc0000-aebc8000 rw-s 1da30d000 00:05 3563      /dev/dri/card0
aebc8000-aebd0000 rw-s 1da305000 00:05 3563      /dev/dri/card0
aebd0000-aebd8000 rw-s 1da2fd000 00:05 3563      /dev/dri/card0
aebd8000-aebe0000 rw-s 1da268000 00:05 3563      /dev/dri/card0
aebe0000-aebe8000 rw-s 1da25f000 00:05 3563      /dev/dri/card0
aebe8000-aebf0000 rw-s 1da257000 00:05 3563      /dev/dri/card0
aebf0000-aebf8000 rw-s 1da24f000 00:05 3563      /dev/dri/card0
aebf8000-aec00000 rw-s 1da247000 00:05 3563      /dev/dri/card0
aec00000-aec08000 rw-s 1da23f000 00:05 3563      /dev/dri/card0
aec08000-aec10000 rw-s 1daa13000 00:05 3563      /dev/dri/card0
aec10000-aec18000 rw-s 1da2ee000 00:05 3563      /dev/dri/card0
aec18000-aec20000 rw-s 1da2e6000 00:05 3563      /dev/dri/card0
aec20000-aec28000 rw-s 1da2de000 00:05 3563      /dev/dri/card0
aec28000-aec30000 rw-s 1da536000 00:05 3563      /dev/dri/card0
aec30000-aec38000 rw-s 1da52e000 00:05 3563      /dev/dri/card0
aec38000-aec40000 rw-s 1da2c5000 00:05 3563      /dev/dri/card0
aec40000-aec48000 rw-s 1da2bd000 00:05 3563      /dev/dri/card0
aec48000-aec50000 rw-s 1da2b5000 00:05 3563      /dev/dri/card0
aec50000-aec58000 rw-s 1da2ad000 00:05 3563      /dev/dri/card0
aec58000-aec60000 rw-s 1da2a5000 00:05 3563      /dev/dri/card0
aec60000-aec68000 rw-s 1da29d000 00:05 3563      /dev/dri/card0
aec68000-aec70000 rw-s 1da295000 00:05 3563      /dev/dri/card0
aec70000-aec78000 rw-s 1da28d000 00:05 3563      /dev/dri/card0
aec78000-aec80000 rw-s 1da285000 00:05 3563      /dev/dri/card0
aec80000-aec88000 rw-s 1da27d000 00:05 3563      /dev/dri/card0
aec88000-aec90000 rw-s 1da275000 00:05 3563      /dev/dri/card0
aec90000-aec98000 rw-s 1da237000 00:05 3563      /dev/dri/card0
aec98000-aeca0000 rw-s 1da22f000 00:05 3563      /dev/dri/card0
aeca0000-aeca8000 rw-s 1da227000 00:05 3563      /dev/dri/card0
aeca8000-aecb0000 rw-s 1da21f000 00:05 3563      /dev/dri/card0
aecb0000-aecb8000 rw-s 1da217000 00:05 3563      /dev/dri/card0
aecb8000-aecc0000 rw-s 1da20f000 00:05 3563      /dev/dri/card0
aecc0000-aecc8000 rw-s 1da207000 00:05 3563      /dev/dri/card0
aecc8000-aecd0000 rw-s 1da1ff000 00:05 3563      /dev/dri/card0
aecd0000-aecd8000 rw-s 1da1f7000 00:05 3563      /dev/dri/card0
aecd8000-aece0000 rw-s 1da1ef000 00:05 3563      /dev/dri/card0
aece0000-aece8000 rw-s 1da1e7000 00:05 3563      /dev/dri/card0
aece8000-aecf0000 rw-s 1da1df000 00:05 3563      /dev/dri/card0
aecf0000-aecf8000 rw-s 1da1d7000 00:05 3563      /dev/dri/card0
aecf8000-aed00000 rw-s 1da1cf000 00:05 3563      /dev/dri/card0
aed00000-aed08000 rw-s 1da1c7000 00:05 3563      /dev/dri/card0
aed08000-aed10000 rw-s 1da1bf000 00:05 3563      /dev/dri/card0
aed10000-aed18000 rw-s 1da1b7000 00:05 3563      /dev/dri/card0
aed18000-aed20000 rw-s 1da1af000 00:05 3563      /dev/dri/card0
aed20000-aed28000 rw-s 1da1a7000 00:05 3563      /dev/dri/card0
aed28000-aed30000 rw-s 1da19f000 00:05 3563      /dev/dri/card0
aed30000-aed38000 rw-s 1da197000 00:05 3563      /dev/dri/card0
aed38000-aed40000 rw-s 1da18f000 00:05 3563      /dev/dri/card0
aed40000-aed48000 rw-s 1da187000 00:05 3563      /dev/dri/card0
aed48000-aed50000 rw-s 1da17f000 00:05 3563      /dev/dri/card0
aed50000-aed58000 rw-s 1da177000 00:05 3563      /dev/dri/card0
aed58000-aed60000 rw-s 1da16f000 00:05 3563      /dev/dri/card0
aed60000-aed68000 rw-s 1da167000 00:05 3563      /dev/dri/card0
aed68000-aed70000 rw-s 1da15f000 00:05 3563      /dev/dri/card0
aed70000-aed78000 rw-s 1da157000 00:05 3563      /dev/dri/card0
aed78000-aed80000 rw-s 1da14f000 00:05 3563      /dev/dri/card0
aed80000-aed88000 rw-s 1da147000 00:05 3563      /dev/dri/card0
aed88000-aed90000 rw-s 1da13f000 00:05 3563      /dev/dri/card0
aed90000-aed98000 rw-s 1da137000 00:05 3563      /dev/dri/card0
aed98000-aeda0000 rw-s 1da12f000 00:05 3563      /dev/dri/card0
aeda0000-aeda8000 rw-s 1da127000 00:05 3563      /dev/dri/card0
aeda8000-aedb0000 rw-s 1da11f000 00:05 3563      /dev/dri/card0
aedb0000-aedb8000 rw-s 1da117000 00:05 3563      /dev/dri/card0
aedb8000-aedc0000 rw-s 1da10f000 00:05 3563      /dev/dri/card0
aedc0000-aedc8000 rw-s 1da107000 00:05 3563      /dev/dri/card0
aedc8000-aedd0000 rw-s 1d5b81000 00:05 3563      /dev/dri/card0
aedd0000-aedd8000 rw-s 1da0b9000 00:05 3563      /dev/dri/card0
aedd8000-aede0000 rw-s 1da0b1000 00:05 3563      /dev/dri/card0
aede0000-aede8000 rw-s 1da0a9000 00:05 3563      /dev/dri/card0
aede8000-aedf0000 rw-s 1da0a1000 00:05 3563      /dev/dri/card0
aedf0000-aedf8000 rw-s 1da099000 00:05 3563      /dev/dri/card0
aedf8000-aee00000 rw-s 1da0ff000 00:05 3563      /dev/dri/card0
aee00000-aee08000 rw-s 1da0f7000 00:05 3563      /dev/dri/card0
aee08000-aee10000 rw-s 1da0ef000 00:05 3563      /dev/dri/card0
aee10000-aee18000 rw-s 1da0e7000 00:05 3563      /dev/dri/card0
aee18000-aee20000 rw-s 1da0df000 00:05 3563      /dev/dri/card0
aee20000-aee28000 rw-s 1da0d7000 00:05 3563      /dev/dri/card0
aee28000-aee30000 rw-s 1da0cf000 00:05 3563      /dev/dri/card0
aee30000-aee38000 rw-s 1da091000 00:05 3563      /dev/dri/card0
aee38000-aee40000 rw-s 1da089000 00:05 3563      /dev/dri/card0
aee40000-aee48000 rw-s 1da081000 00:05 3563      /dev/dri/card0
aee48000-aee50000 rw-s 1da079000 00:05 3563      /dev/dri/card0
aee50000-aee58000 rw-s 1da071000 00:05 3563      /dev/dri/card0
aee58000-aee60000 rw-s 1da069000 00:05 3563      /dev/dri/card0
aee60000-aee68000 rw-s 1da053000 00:05 3563      /dev/dri/card0
aee68000-aee70000 rw-s 1da04b000 00:05 3563      /dev/dri/card0
aee70000-aee78000 rw-s 1da043000 00:05 3563      /dev/dri/card0
aee78000-aee80000 rw-s 1da03b000 00:05 3563      /dev/dri/card0
aee80000-aee88000 rw-s 1da033000 00:05 3563      /dev/dri/card0
aee88000-aee90000 rw-s 1da02b000 00:05 3563      /dev/dri/card0
aee90000-aee98000 rw-s 1da061000 00:05 3563      /dev/dri/card0
aee98000-aeea0000 rw-s 1da023000 00:05 3563      /dev/dri/card0
aeea0000-aeea8000 rw-s 1da01b000 00:05 3563      /dev/dri/card0
aeea8000-aeeb0000 rw-s 1da013000 00:05 3563      /dev/dri/card0
aeeb0000-aeeb8000 rw-s 1da00b000 00:05 3563      /dev/dri/card0
aeeb8000-aeec0000 rw-s 1d9f9d000 00:05 3563      /dev/dri/card0
aeec0000-aeec8000 rw-s 1da003000 00:05 3563      /dev/dri/card0
aeec8000-aeed0000 rw-s 1d9fc6000 00:05 3563      /dev/dri/card0
aeed0000-aeed8000 rw-s 1d9fbe000 00:05 3563      /dev/dri/card0
aeed8000-aeee0000 rw-s 1d9fae000 00:05 3563      /dev/dri/card0
aeee0000-aeee8000 rw-s 1d9fa6000 00:05 3563      /dev/dri/card0
aeee8000-aeef0000 rw-s 1d9fb6000 00:05 3563      /dev/dri/card0
aeef0000-aeef8000 rw-s 1d9ffb000 00:05 3563      /dev/dri/card0
aeef8000-aef00000 rw-s 1d9ff3000 00:05 3563      /dev/dri/card0
aef00000-aef08000 rw-s 1d9feb000 00:05 3563      /dev/dri/card0
aef08000-aef10000 rw-s 1d9fe3000 00:05 3563      /dev/dri/card0
aef10000-aef18000 rw-s 1d9fdb000 00:05 3563      /dev/dri/card0
aef18000-aef20000 rw-s 1d9fd3000 00:05 3563      /dev/dri/card0
aef20000-aef28000 rw-s 1d9f95000 00:05 3563      /dev/dri/card0
aef28000-aef30000 rw-s 1d9f8d000 00:05 3563      /dev/dri/card0
aef30000-aef38000 rw-s 1d9f85000 00:05 3563      /dev/dri/card0
aef38000-aef40000 rw-s 1d9f7d000 00:05 3563      /dev/dri/card0
aef40000-aef48000 rw-s 1d9f75000 00:05 3563      /dev/dri/card0
aef48000-aef50000 rw-s 1d9f6d000 00:05 3563      /dev/dri/card0
aef50000-aef58000 rw-s 1d9f65000 00:05 3563      /dev/dri/card0
aef58000-aef60000 rw-s 1d9f5d000 00:05 3563      /dev/dri/card0
aef60000-aef68000 rw-s 1d9f55000 00:05 3563      /dev/dri/card0
aef68000-aef70000 rw-s 1d9f4d000 00:05 3563      /dev/dri/card0
aef70000-aef78000 rw-s 1d9f45000 00:05 3563      /dev/dri/card0
aef78000-aef80000 rw-s 1d9f3d000 00:05 3563      /dev/dri/card0
aef80000-aef88000 rw-s 1d9f35000 00:05 3563      /dev/dri/card0
aef88000-aef90000 rw-s 1d9f2d000 00:05 3563      /dev/dri/card0
aef90000-aef98000 rw-s 1d9f25000 00:05 3563      /dev/dri/card0
aef98000-aefa0000 rw-s 1d9ef8000 00:05 3563      /dev/dri/card0
aefa0000-aefa8000 rw-s 1d9ef0000 00:05 3563      /dev/dri/card0
aefa8000-aefb0000 rw-s 1d9ee8000 00:05 3563      /dev/dri/card0
aefb0000-aefb8000 rw-s 1d9ee0000 00:05 3563      /dev/dri/card0
aefb8000-aefc0000 rw-s 1d9ed7000 00:05 3563      /dev/dri/card0
aefc0000-aefc8000 rw-s 1d9ecf000 00:05 3563      /dev/dri/card0
aefc8000-aefd0000 rw-s 1d9f1d000 00:05 3563      /dev/dri/card0
aefd0000-aefd8000 rw-s 1d9f15000 00:05 3563      /dev/dri/card0
aefd8000-aefe0000 rw-s 1d9f0d000 00:05 3563      /dev/dri/card0
aefe0000-aefe8000 rw-s 1d9f05000 00:05 3563      /dev/dri/card0
aefe8000-aeff0000 rw-s 1d9ec7000 00:05 3563      /dev/dri/card0
aeff0000-aeff8000 rw-s 1d9ebf000 00:05 3563      /dev/dri/card0
aeff8000-af000000 rw-s 1d9eb7000 00:05 3563      /dev/dri/card0
af000000-af008000 rw-s 1d9eaf000 00:05 3563      /dev/dri/card0
af008000-af010000 rw-s 1d9ea7000 00:05 3563      /dev/dri/card0
af010000-af018000 rw-s 1d9e41000 00:05 3563      /dev/dri/card0
af018000-af020000 rw-s 1d9e39000 00:05 3563      /dev/dri/card0
af020000-af028000 rw-s 1d9e31000 00:05 3563      /dev/dri/card0
af028000-af030000 rw-s 1d9e29000 00:05 3563      /dev/dri/card0
af030000-af038000 rw-s 1d9e21000 00:05 3563      /dev/dri/card0
af038000-af040000 rw-s 1d9e19000 00:05 3563      /dev/dri/card0
af040000-af048000 rw-s 1d9e9f000 00:05 3563      /dev/dri/card0
af048000-af050000 rw-s 1d9e97000 00:05 3563      /dev/dri/card0
af050000-af058000 rw-s 1d9e8f000 00:05 3563      /dev/dri/card0
af058000-af060000 rw-s 1d9e87000 00:05 3563      /dev/dri/card0
af060000-af068000 rw-s 1d9e7f000 00:05 3563      /dev/dri/card0
af068000-af070000 rw-s 1d9e77000 00:05 3563      /dev/dri/card0
af070000-af078000 rw-s 1d9e6f000 00:05 3563      /dev/dri/card0
af078000-af080000 rw-s 1d9e67000 00:05 3563      /dev/dri/card0
af080000-af088000 rw-s 1d9e5f000 00:05 3563      /dev/dri/card0
af088000-af090000 rw-s 1d9e57000 00:05 3563      /dev/dri/card0
af090000-af098000 rw-s 1d9e4f000 00:05 3563      /dev/dri/card0
af098000-af0a0000 rw-s 1d9e11000 00:05 3563      /dev/dri/card0
af0a0000-af0a8000 rw-s 1d9e09000 00:05 3563      /dev/dri/card0
af0a8000-af0b0000 rw-s 1d9e01000 00:05 3563      /dev/dri/card0
af0b0000-af0b8000 rw-s 1d9df9000 00:05 3563      /dev/dri/card0
af0b8000-af0c0000 rw-s 1d9df1000 00:05 3563      /dev/dri/card0
af0c0000-af0c8000 rw-s 1d9de9000 00:05 3563      /dev/dri/card0
af0c8000-af0d0000 rw-s 1d9de1000 00:05 3563      /dev/dri/card0
af0d0000-af0d8000 rw-s 1d9dd9000 00:05 3563      /dev/dri/card0
af0d8000-af0e0000 rw-s 1d9dd1000 00:05 3563      /dev/dri/card0
af0e0000-af0e8000 rw-s 1d9dc9000 00:05 3563      /dev/dri/card0
af0e8000-af0f0000 rw-s 1d9dc1000 00:05 3563      /dev/dri/card0
af0f0000-af0f8000 rw-s 1d9db9000 00:05 3563      /dev/dri/card0
af0f8000-af100000 rw-s 1d9db1000 00:05 3563      /dev/dri/card0
af100000-af108000 rw-s 1d9da9000 00:05 3563      /dev/dri/card0
af108000-af110000 rw-s 1d9da1000 00:05 3563      /dev/dri/card0
af110000-af118000 rw-s 1d9d99000 00:05 3563      /dev/dri/card0
af118000-af120000 rw-s 1d9d91000 00:05 3563      /dev/dri/card0
af120000-af128000 rw-s 1d9d89000 00:05 3563      /dev/dri/card0
af128000-af130000 rw-s 1d9d81000 00:05 3563      /dev/dri/card0
af130000-af138000 rw-s 1d9d79000 00:05 3563      /dev/dri/card0
af138000-af140000 rw-s 1d9d71000 00:05 3563      /dev/dri/card0
af140000-af148000 rw-s 1d9d69000 00:05 3563      /dev/dri/card0
af148000-af150000 rw-s 1d9d61000 00:05 3563      /dev/dri/card0
af150000-af158000 rw-s 1d9d59000 00:05 3563      /dev/dri/card0
af158000-af160000 rw-s 1d9d51000 00:05 3563      /dev/dri/card0
af160000-af168000 rw-s 1d9d49000 00:05 3563      /dev/dri/card0
af168000-af170000 rw-s 1d9d41000 00:05 3563      /dev/dri/card0
af170000-af178000 rw-s 1d5bd5000 00:05 3563      /dev/dri/card0
af178000-af180000 rw-s 1d5bcd000 00:05 3563      /dev/dri/card0
af180000-af188000 rw-s 1d9c89000 00:05 3563      /dev/dri/card0
af188000-af190000 rw-s 1d9d39000 00:05 3563      /dev/dri/card0
af190000-af198000 rw-s 1d9d21000 00:05 3563      /dev/dri/card0
af198000-af1a0000 rw-s 1d9d19000 00:05 3563      /dev/dri/card0
af1a0000-af1a8000 rw-s 1d9d11000 00:05 3563      /dev/dri/card0
af1a8000-af1b0000 rw-s 1d9d09000 00:05 3563      /dev/dri/card0
af1b0000-af1b8000 rw-s 1d9d01000 00:05 3563      /dev/dri/card0
af1b8000-af1c0000 rw-s 1d9cf9000 00:05 3563      /dev/dri/card0
af1c0000-af1c8000 rw-s 1d9cf1000 00:05 3563      /dev/dri/card0
af1c8000-af1d0000 rw-s 1d9ce9000 00:05 3563      /dev/dri/card0
af1d0000-af1d8000 rw-s 1d9ce1000 00:05 3563      /dev/dri/card0
af1d8000-af1e0000 rw-s 1d9cd9000 00:05 3563      /dev/dri/card0
af1e0000-af1e8000 rw-s 1d9cd1000 00:05 3563      /dev/dri/card0
af1e8000-af1f0000 rw-s 1d9cc9000 00:05 3563      /dev/dri/card0
af1f0000-af1f8000 rw-s 1d9cc1000 00:05 3563      /dev/dri/card0
af1f8000-af200000 rw-s 1d9cb1000 00:05 3563      /dev/dri/card0
af200000-af208000 rw-s 1d9ca9000 00:05 3563      /dev/dri/card0
af208000-af210000 rw-s 1d9ca1000 00:05 3563      /dev/dri/card0
af210000-af218000 rw-s 1d9c99000 00:05 3563      /dev/dri/card0
af218000-af220000 rw-s 1d9c91000 00:05 3563      /dev/dri/card0
af220000-af228000 rw-s 1d9d31000 00:05 3563      /dev/dri/card0
af228000-af230000 rw-s 1d9c81000 00:05 3563      /dev/dri/card0
af230000-af238000 rw-s 1d9c79000 00:05 3563      /dev/dri/card0
af238000-af240000 rw-s 1d9c71000 00:05 3563      /dev/dri/card0
af240000-af248000 rw-s 1d9c69000 00:05 3563      /dev/dri/card0
af248000-af250000 rw-s 1d9c61000 00:05 3563      /dev/dri/card0
af250000-af258000 rw-s 1d9c59000 00:05 3563      /dev/dri/card0
af258000-af260000 rw-s 1d9c51000 00:05 3563      /dev/dri/card0
af260000-af268000 rw-s 1d9c49000 00:05 3563      /dev/dri/card0
af268000-af270000 rw-s 1d9c41000 00:05 3563      /dev/dri/card0
af270000-af278000 rw-s 1d9c39000 00:05 3563      /dev/dri/card0
af278000-af280000 rw-s 1d9c31000 00:05 3563      /dev/dri/card0
af280000-af288000 rw-s 1d9c29000 00:05 3563      /dev/dri/card0
af288000-af290000 rw-s 1d9c21000 00:05 3563      /dev/dri/card0
af290000-af298000 rw-s 1d9cb9000 00:05 3563      /dev/dri/card0
af298000-af2a0000 rw-s 1d9be4000 00:05 3563      /dev/dri/card0
af2a0000-af2a8000 rw-s 1d9bdc000 00:05 3563      /dev/dri/card0
af2a8000-af2b0000 rw-s 1d9b5d000 00:05 3563      /dev/dri/card0
af2b0000-af2b8000 rw-s 1d9bd4000 00:05 3563      /dev/dri/card0
af2b8000-af2c0000 rw-s 1d9bcc000 00:05 3563      /dev/dri/card0
af2c0000-af2c8000 rw-s 1d9bc4000 00:05 3563      /dev/dri/card0
af2c8000-af2d0000 rw-s 1d9bbc000 00:05 3563      /dev/dri/card0
af2d0000-af2d8000 rw-s 1d9c09000 00:05 3563      /dev/dri/card0
af2d8000-af2e0000 rw-s 1d9c01000 00:05 3563      /dev/dri/card0
af2e0000-af2e8000 rw-s 1d9bf9000 00:05 3563      /dev/dri/card0
af2e8000-af2f0000 rw-s 1d9bb3000 00:05 3563      /dev/dri/card0
af2f0000-af2f8000 rw-s 1d9b85000 00:05 3563      /dev/dri/card0
af2f8000-af300000 rw-s 1d9b7d000 00:05 3563      /dev/dri/card0
af300000-af308000 rw-s 1d9b75000 00:05 3563      /dev/dri/card0
af308000-af310000 rw-s 1d9b6d000 00:05 3563      /dev/dri/card0
af310000-af318000 rw-s 1d9b65000 00:05 3563      /dev/dri/card0
af318000-af320000 rw-s 1d9c11000 00:05 3563      /dev/dri/card0
af320000-af328000 rw-s 1d9bab000 00:05 3563      /dev/dri/card0
af328000-af330000 rw-s 1d9ba3000 00:05 3563      /dev/dri/card0
af330000-af338000 rw-s 1d9b9b000 00:05 3563      /dev/dri/card0
af338000-af340000 rw-s 1d9b93000 00:05 3563      /dev/dri/card0
af340000-af348000 rw-s 1d9b55000 00:05 3563      /dev/dri/card0
af348000-af350000 rw-s 1d9b4d000 00:05 3563      /dev/dri/card0
af350000-af358000 rw-s 1d9b45000 00:05 3563      /dev/dri/card0
af358000-af360000 rw-s 1d9b3d000 00:05 3563      /dev/dri/card0
af360000-af368000 rw-s 1d9b1f000 00:05 3563      /dev/dri/card0
af368000-af370000 rw-s 1d9b17000 00:05 3563      /dev/dri/card0
af370000-af378000 rw-s 1d9b0f000 00:05 3563      /dev/dri/card0
af378000-af380000 rw-s 1d9b07000 00:05 3563      /dev/dri/card0
af380000-af388000 rw-s 1d9aff000 00:05 3563      /dev/dri/card0
af388000-af390000 rw-s 1d9af7000 00:05 3563      /dev/dri/card0
af390000-af398000 rw-s 1d5b79000 00:05 3563      /dev/dri/card0
af398000-af3a0000 rw-s 1d9b2f000 00:05 3563      /dev/dri/card0
af3a0000-af3a8000 rw-s 1d9aef000 00:05 3563      /dev/dri/card0
af3a8000-af3b0000 rw-s 1d9ae7000 00:05 3563      /dev/dri/card0
af3b0000-af3b8000 rw-s 1d9adf000 00:05 3563      /dev/dri/card0
af3b8000-af3c0000 rw-s 1d9ad7000 00:05 3563      /dev/dri/card0
af3c0000-af3c8000 rw-s 1d9acf000 00:05 3563      /dev/dri/card0
af3c8000-af3d0000 rw-s 1d9ac7000 00:05 3563      /dev/dri/card0
af3d0000-af3d8000 rw-s 1d9abf000 00:05 3563      /dev/dri/card0
af3d8000-af3e0000 rw-s 1d9ab7000 00:05 3563      /dev/dri/card0
af3e0000-af3e8000 rw-s 1d9aaf000 00:05 3563      /dev/dri/card0
af3e8000-af3f0000 rw-s 1d9aa7000 00:05 3563      /dev/dri/card0
af3f0000-af3f8000 rw-s 1d9a9f000 00:05 3563      /dev/dri/card0
af3f8000-af400000 rw-s 1d9a97000 00:05 3563      /dev/dri/card0
af400000-af408000 rw-s 1d9a8f000 00:05 3563      /dev/dri/card0
af408000-af410000 rw-s 1d9a87000 00:05 3563      /dev/dri/card0
af410000-af418000 rw-s 1d9a7f000 00:05 3563      /dev/dri/card0
af418000-af420000 rw-s 1d9a77000 00:05 3563      /dev/dri/card0
af420000-af428000 rw-s 1d9a6f000 00:05 3563      /dev/dri/card0
af428000-af430000 rw-s 1d9a67000 00:05 3563      /dev/dri/card0
af430000-af438000 rw-s 1d9a5f000 00:05 3563      /dev/dri/card0
af438000-af440000 rw-s 1d9a57000 00:05 3563      /dev/dri/card0
af440000-af448000 rw-s 1d9a4f000 00:05 3563      /dev/dri/card0
af448000-af450000 rw-s 1d9a47000 00:05 3563      /dev/dri/card0
af450000-af458000 rw-s 1d9a3f000 00:05 3563      /dev/dri/card0
af458000-af460000 rw-s 1d9a37000 00:05 3563      /dev/dri/card0
af460000-af468000 rw-s 1d9a2f000 00:05 3563      /dev/dri/card0
af468000-af470000 rw-s 1d9a27000 00:05 3563      /dev/dri/card0
af470000-af478000 rw-s 1d9a1f000 00:05 3563      /dev/dri/card0
af478000-af480000 rw-s 1d9a17000 00:05 3563      /dev/dri/card0
af480000-af488000 rw-s 1d9a0f000 00:05 3563      /dev/dri/card0
af488000-af490000 rw-s 1d9a07000 00:05 3563      /dev/dri/card0
af490000-af498000 rw-s 1d99ff000 00:05 3563      /dev/dri/card0
af498000-af4a0000 rw-s 1d99f7000 00:05 3563      /dev/dri/card0
af4a0000-af4a8000 rw-s 1d99ef000 00:05 3563      /dev/dri/card0
af4a8000-af4b0000 rw-s 1d99e7000 00:05 3563      /dev/dri/card0
af4b0000-af4b8000 rw-s 1d99df000 00:05 3563      /dev/dri/card0
af4b8000-af4c0000 rw-s 1d99d7000 00:05 3563      /dev/dri/card0
af4c0000-af4c8000 rw-s 1d99cf000 00:05 3563      /dev/dri/card0
af4c8000-af4d0000 rw-s 1d99c7000 00:05 3563      /dev/dri/card0
af4d0000-af4d8000 rw-s 1d997b000 00:05 3563      /dev/dri/card0
af4d8000-af4e0000 rw-s 1d9973000 00:05 3563      /dev/dri/card0
af4e0000-af4e8000 rw-s 1d996a000 00:05 3563      /dev/dri/card0
af4e8000-af4f0000 rw-s 1d9962000 00:05 3563      /dev/dri/card0
af4f0000-af4f8000 rw-s 1d995a000 00:05 3563      /dev/dri/card0
af4f8000-af500000 rw-s 1d9952000 00:05 3563      /dev/dri/card0
af500000-af508000 rw-s 1d99bf000 00:05 3563      /dev/dri/card0
af508000-af510000 rw-s 1d99b7000 00:05 3563      /dev/dri/card0
af510000-af518000 rw-s 1d99af000 00:05 3563      /dev/dri/card0
af518000-af520000 rw-s 1d99a7000 00:05 3563      /dev/dri/card0
af520000-af528000 rw-s 1d999f000 00:05 3563      /dev/dri/card0
af528000-af530000 rw-s 1d9997000 00:05 3563      /dev/dri/card0
af530000-af538000 rw-s 1d998f000 00:05 3563      /dev/dri/card0
af538000-af540000 rw-s 1d9987000 00:05 3563      /dev/dri/card0
af540000-af548000 rw-s 1d9949000 00:05 3563      /dev/dri/card0
af548000-af550000 rw-s 1d9941000 00:05 3563      /dev/dri/card0
af550000-af558000 rw-s 1d9939000 00:05 3563      /dev/dri/card0
af558000-af560000 rw-s 1d95eb000 00:05 3563      /dev/dri/card0
af560000-af568000 rw-s 1d9929000 00:05 3563      /dev/dri/card0
af568000-af570000 rw-s 1d9921000 00:05 3563      /dev/dri/card0
af570000-af578000 rw-s 1d9919000 00:05 3563      /dev/dri/card0
af578000-af580000 rw-s 1d9911000 00:05 3563      /dev/dri/card0
af580000-af588000 rw-s 1d9909000 00:05 3563      /dev/dri/card0
af588000-af590000 rw-s 1d9901000 00:05 3563      /dev/dri/card0
af590000-af598000 rw-s 1d98f9000 00:05 3563      /dev/dri/card0
af598000-af5a0000 rw-s 1d98f1000 00:05 3563      /dev/dri/card0
af5a0000-af5a8000 rw-s 1d98e9000 00:05 3563      /dev/dri/card0
af5a8000-af5b0000 rw-s 1d98e1000 00:05 3563      /dev/dri/card0
af5b0000-af5b8000 rw-s 1d98d9000 00:05 3563      /dev/dri/card0
af5b8000-af5c0000 rw-s 1d98d1000 00:05 3563      /dev/dri/card0
af5c0000-af5c8000 rw-s 1d98c9000 00:05 3563      /dev/dri/card0
af5c8000-af5d0000 rw-s 1d98c1000 00:05 3563      /dev/dri/card0
af5d0000-af5d8000 rw-s 1d98b9000 00:05 3563      /dev/dri/card0
af5d8000-af5e0000 rw-s 1d98b1000 00:05 3563      /dev/dri/card0
af5e0000-af5e8000 rw-s 1d98a9000 00:05 3563      /dev/dri/card0
af5e8000-af5f0000 rw-s 1d98a1000 00:05 3563      /dev/dri/card0
af5f0000-af5f8000 rw-s 1d9899000 00:05 3563      /dev/dri/card0
af5f8000-af600000 rw-s 1d9891000 00:05 3563      /dev/dri/card0
af600000-af608000 rw-s 1d9889000 00:05 3563      /dev/dri/card0
af608000-af610000 rw-s 1d9881000 00:05 3563      /dev/dri/card0
af610000-af618000 rw-s 1d9879000 00:05 3563      /dev/dri/card0
af618000-af620000 rw-s 1d9871000 00:05 3563      /dev/dri/card0
af620000-af628000 rw-s 1d9869000 00:05 3563      /dev/dri/card0
af628000-af630000 rw-s 1d9861000 00:05 3563      /dev/dri/card0
af630000-af638000 rw-s 1d9859000 00:05 3563      /dev/dri/card0
af638000-af640000 rw-s 1d9851000 00:05 3563      /dev/dri/card0
af640000-af648000 rw-s 1d9849000 00:05 3563      /dev/dri/card0
af648000-af650000 rw-s 1d9841000 00:05 3563      /dev/dri/card0
af650000-af658000 rw-s 1d9839000 00:05 3563      /dev/dri/card0
af658000-af660000 rw-s 1d9831000 00:05 3563      /dev/dri/card0
af660000-af668000 rw-s 1d9829000 00:05 3563      /dev/dri/card0
af668000-af670000 rw-s 1d9821000 00:05 3563      /dev/dri/card0
af670000-af678000 rw-s 1d9819000 00:05 3563      /dev/dri/card0
af678000-af680000 rw-s 1d9811000 00:05 3563      /dev/dri/card0
af680000-af688000 rw-s 1d9809000 00:05 3563      /dev/dri/card0
af688000-af690000 rw-s 1d9801000 00:05 3563      /dev/dri/card0
af690000-af698000 rw-s 1d97f9000 00:05 3563      /dev/dri/card0
af698000-af6a0000 rw-s 1d97f1000 00:05 3563      /dev/dri/card0
af6a0000-af6a8000 rw-s 1d97e9000 00:05 3563      /dev/dri/card0
af6a8000-af6b0000 rw-s 1d97e1000 00:05 3563      /dev/dri/card0
af6b0000-af6b8000 rw-s 1d97d9000 00:05 3563      /dev/dri/card0
af6b8000-af6c0000 rw-s 1d97d1000 00:05 3563      /dev/dri/card0
af6c0000-af6c8000 rw-s 1d97c9000 00:05 3563      /dev/dri/card0
af6c8000-af6d0000 rw-s 1d97c1000 00:05 3563      /dev/dri/card0
af6d0000-af6d8000 rw-s 1d97b9000 00:05 3563      /dev/dri/card0
af6d8000-af6e0000 rw-s 1d97b1000 00:05 3563      /dev/dri/card0
af6e0000-af6e8000 rw-s 1d97a9000 00:05 3563      /dev/dri/card0
af6e8000-af6f0000 rw-s 1d97a1000 00:05 3563      /dev/dri/card0
af6f0000-af6f8000 rw-s 1d9799000 00:05 3563      /dev/dri/card0
af6f8000-af700000 rw-s 1d9791000 00:05 3563      /dev/dri/card0
af700000-af708000 rw-s 1d9789000 00:05 3563      /dev/dri/card0
af708000-af710000 rw-s 1d9781000 00:05 3563      /dev/dri/card0
af710000-af718000 rw-s 1d9779000 00:05 3563      /dev/dri/card0
af718000-af720000 rw-s 1d9761000 00:05 3563      /dev/dri/card0
af720000-af728000 rw-s 1d9759000 00:05 3563      /dev/dri/card0
af728000-af730000 rw-s 1d9751000 00:05 3563      /dev/dri/card0
af730000-af738000 rw-s 1d9749000 00:05 3563      /dev/dri/card0
af738000-af740000 rw-s 1d9741000 00:05 3563      /dev/dri/card0
af740000-af748000 rw-s 1d9739000 00:05 3563      /dev/dri/card0
af748000-af750000 rw-s 1d9731000 00:05 3563      /dev/dri/card0
af750000-af758000 rw-s 1d9729000 00:05 3563      /dev/dri/card0
af758000-af760000 rw-s 1d9721000 00:05 3563      /dev/dri/card0
af760000-af768000 rw-s 1d9719000 00:05 3563      /dev/dri/card0
af768000-af770000 rw-s 1d9711000 00:05 3563      /dev/dri/card0
af770000-af778000 rw-s 1d9709000 00:05 3563      /dev/dri/card0
af778000-af780000 rw-s 1d9701000 00:05 3563      /dev/dri/card0
af780000-af788000 rw-s 1d96f9000 00:05 3563      /dev/dri/card0
af788000-af790000 rw-s 1d96f1000 00:05 3563      /dev/dri/card0
af790000-af798000 rw-s 1d96e9000 00:05 3563      /dev/dri/card0
af798000-af7a0000 rw-s 1d96e1000 00:05 3563      /dev/dri/card0
af7a0000-af7a8000 rw-s 1d96d9000 00:05 3563      /dev/dri/card0
af7a8000-af7b0000 rw-s 1d9546000 00:05 3563      /dev/dri/card0
af7b0000-af7b8000 rw-s 1d9673000 00:05 3563      /dev/dri/card0
af7b8000-af7c0000 rw-s 1d966b000 00:05 3563      /dev/dri/card0
af7c0000-af7c8000 rw-s 1d9663000 00:05 3563      /dev/dri/card0
af7c8000-af7d0000 rw-s 1d9653000 00:05 3563      /dev/dri/card0
af7d0000-af7d8000 rw-s 1d964b000 00:05 3563      /dev/dri/card0
af7d8000-af7e0000 rw-s 1d96d1000 00:05 3563      /dev/dri/card0
af7e0000-af7e8000 rw-s 1d96c9000 00:05 3563      /dev/dri/card0
af7e8000-af7f0000 rw-s 1d96c1000 00:05 3563      /dev/dri/card0
af7f0000-af7f8000 rw-s 1d96b9000 00:05 3563      /dev/dri/card0
af7f8000-af800000 rw-s 1d96b1000 00:05 3563      /dev/dri/card0
af800000-af808000 rw-s 1d96a9000 00:05 3563      /dev/dri/card0
af808000-af810000 rw-s 1d96a1000 00:05 3563      /dev/dri/card0
af810000-af818000 rw-s 1d9699000 00:05 3563      /dev/dri/card0
af818000-af820000 rw-s 1d9691000 00:05 3563      /dev/dri/card0
af820000-af828000 rw-s 1d9689000 00:05 3563      /dev/dri/card0
af828000-af830000 rw-s 1d9681000 00:05 3563      /dev/dri/card0
af830000-af838000 rw-s 1d9643000 00:05 3563      /dev/dri/card0
af838000-af840000 rw-s 1d963b000 00:05 3563      /dev/dri/card0
af840000-af848000 rw-s 1d9633000 00:05 3563      /dev/dri/card0
af848000-af850000 rw-s 1d962b000 00:05 3563      /dev/dri/card0
af850000-af858000 rw-s 1d9623000 00:05 3563      /dev/dri/card0
af858000-af860000 rw-s 1d961b000 00:05 3563      /dev/dri/card0
af860000-af870000 rw-s 1d960b000 00:05 3563      /dev/dri/card0
af870000-af878000 rw-s 1d9603000 00:05 3563      /dev/dri/card0
af878000-af880000 rw-s 1d95fb000 00:05 3563      /dev/dri/card0
af880000-af888000 rw-s 1d95f3000 00:05 3563      /dev/dri/card0
af888000-af890000 rw-s 1d95e3000 00:05 3563      /dev/dri/card0
af890000-af898000 rw-s 1d95db000 00:05 3563      /dev/dri/card0
af898000-af8a0000 rw-s 1d9bf1000 00:05 3563      /dev/dri/card0
af8a0000-af8a8000 rw-s 1d95d0000 00:05 3563      /dev/dri/card0
af8a8000-af8b0000 rw-s 1d95c8000 00:05 3563      /dev/dri/card0
af8b0000-af8b8000 rw-s 1d95bb000 00:05 3563      /dev/dri/card0
af8b8000-af8c0000 rw-s 1d95b3000 00:05 3563      /dev/dri/card0
af8c0000-af8c8000 rw-s 1d9931000 00:05 3563      /dev/dri/card0
af8c8000-af8d0000 rw-s 1d95ab000 00:05 3563      /dev/dri/card0
af8d0000-af8d8000 rw-s 1d95a3000 00:05 3563      /dev/dri/card0
af8d8000-af8e0000 rw-s 1d959b000 00:05 3563      /dev/dri/card0
af8e0000-af8e8000 rw-s 1d9593000 00:05 3563      /dev/dri/card0
af8e8000-af8f0000 rw-s 1d958b000 00:05 3563      /dev/dri/card0
af8f0000-af8f8000 rw-s 1d9566000 00:05 3563      /dev/dri/card0
af8f8000-af900000 rw-s 1d955e000 00:05 3563      /dev/dri/card0
af900000-af908000 rw-s 1d954e000 00:05 3563      /dev/dri/card0
af908000-af910000 rw-s 1d965b000 00:05 3563      /dev/dri/card0
af910000-af918000 rw-s 1d953e000 00:05 3563      /dev/dri/card0
af918000-af920000 rw-s 1d9536000 00:05 3563      /dev/dri/card0
af920000-af928000 rw-s 1d9583000 00:05 3563      /dev/dri/card0
af928000-af930000 rw-s 1d957b000 00:05 3563      /dev/dri/card0
af930000-af938000 rw-s 1d9573000 00:05 3563      /dev/dri/card0
af938000-af940000 rw-s 1d9556000 00:05 3563      /dev/dri/card0
af940000-af948000 rw-s 1d952d000 00:05 3563      /dev/dri/card0
af948000-af950000 rw-s 1d9525000 00:05 3563      /dev/dri/card0
af950000-af958000 rw-s 1d951d000 00:05 3563      /dev/dri/card0
af958000-af960000 rw-s 1d9515000 00:05 3563      /dev/dri/card0
af960000-af968000 rw-s 1d950d000 00:05 3563      /dev/dri/card0
af968000-af970000 rw-s 1d9505000 00:05 3563      /dev/dri/card0
af970000-af978000 rw-s 1d94fd000 00:05 3563      /dev/dri/card0
af978000-af980000 rw-s 1d94f5000 00:05 3563      /dev/dri/card0
af980000-af988000 rw-s 1d94ed000 00:05 3563      /dev/dri/card0
af988000-af990000 rw-s 1d94e5000 00:05 3563      /dev/dri/card0
af990000-af998000 rw-s 1d94dd000 00:05 3563      /dev/dri/card0
af998000-af9a0000 rw-s 1d94d5000 00:05 3563      /dev/dri/card0
af9a0000-af9a8000 rw-s 1d94cd000 00:05 3563      /dev/dri/card0
af9a8000-af9b0000 rw-s 1d94c5000 00:05 3563      /dev/dri/card0
af9b0000-af9b8000 rw-s 1d94bd000 00:05 3563      /dev/dri/card0
af9b8000-af9c0000 rw-s 1d94b5000 00:05 3563      /dev/dri/card0
af9c0000-af9c8000 rw-s 1d94ad000 00:05 3563      /dev/dri/card0
af9c8000-af9d0000 rw-s 1d94a5000 00:05 3563      /dev/dri/card0
af9d0000-af9d8000 rw-s 1d949d000 00:05 3563      /dev/dri/card0
af9d8000-af9e0000 rw-s 1d9495000 00:05 3563      /dev/dri/card0
af9e0000-af9e8000 rw-s 1d948d000 00:05 3563      /dev/dri/card0
af9e8000-af9f0000 rw-s 1d9485000 00:05 3563      /dev/dri/card0
af9f0000-af9f8000 rw-s 1d947d000 00:05 3563      /dev/dri/card0
af9f8000-afa00000 rw-s 1d9475000 00:05 3563      /dev/dri/card0
afa00000-afa08000 rw-s 1d946d000 00:05 3563      /dev/dri/card0
afa08000-afa10000 rw-s 1d9465000 00:05 3563      /dev/dri/card0
afa10000-afa18000 rw-s 1d945d000 00:05 3563      /dev/dri/card0
afa18000-afa20000 rw-s 1d9455000 00:05 3563      /dev/dri/card0
afa20000-afa28000 rw-s 1d944d000 00:05 3563      /dev/dri/card0
afa28000-afa30000 rw-s 1d9445000 00:05 3563      /dev/dri/card0
afa30000-afa38000 rw-s 1d943d000 00:05 3563      /dev/dri/card0
afa38000-afa40000 rw-s 1d9435000 00:05 3563      /dev/dri/card0
afa40000-afa48000 rw-s 1d942d000 00:05 3563      /dev/dri/card0
afa48000-afa50000 rw-s 1d9425000 00:05 3563      /dev/dri/card0
afa50000-afa58000 rw-s 1d941d000 00:05 3563      /dev/dri/card0
afa58000-afa60000 rw-s 1d9415000 00:05 3563      /dev/dri/card0
afa60000-afa68000 rw-s 1d940d000 00:05 3563      /dev/dri/card0
afa68000-afa70000 rw-s 1d9405000 00:05 3563      /dev/dri/card0
afa70000-afa78000 rw-s 1d93fd000 00:05 3563      /dev/dri/card0
afa78000-afa80000 rw-s 1d93f5000 00:05 3563      /dev/dri/card0
afa80000-afa88000 rw-s 1d93ed000 00:05 3563      /dev/dri/card0
afa88000-afa90000 rw-s 1d93e5000 00:05 3563      /dev/dri/card0
afa90000-afa98000 rw-s 1d93dd000 00:05 3563      /dev/dri/card0
afa98000-afaa0000 rw-s 1d937f000 00:05 3563      /dev/dri/card0
afaa0000-afaa8000 rw-s 1d9377000 00:05 3563      /dev/dri/card0
afaa8000-afab0000 rw-s 1d936f000 00:05 3563      /dev/dri/card0
afab0000-afab8000 rw-s 1d9367000 00:05 3563      /dev/dri/card0
afab8000-afac0000 rw-s 1d935f000 00:05 3563      /dev/dri/card0
afac0000-afac8000 rw-s 1d9357000 00:05 3563      /dev/dri/card0
afac8000-afad0000 rw-s 1d93d5000 00:05 3563      /dev/dri/card0
afad0000-afad8000 rw-s 1d93cd000 00:05 3563      /dev/dri/card0
afad8000-afae0000 rw-s 1d93c5000 00:05 3563      /dev/dri/card0
afae0000-afae8000 rw-s 1d93bd000 00:05 3563      /dev/dri/card0
afae8000-afaf0000 rw-s 1d93b5000 00:05 3563      /dev/dri/card0
afaf0000-afaf8000 rw-s 1d93ad000 00:05 3563      /dev/dri/card0
afaf8000-afb00000 rw-s 1d93a5000 00:05 3563      /dev/dri/card0
afb00000-afb08000 rw-s 1d939d000 00:05 3563      /dev/dri/card0
afb08000-afb10000 rw-s 1d9395000 00:05 3563      /dev/dri/card0
afb10000-afb18000 rw-s 1d938d000 00:05 3563      /dev/dri/card0
afb18000-afb20000 rw-s 1d934f000 00:05 3563      /dev/dri/card0
afb20000-afb28000 rw-s 1d9347000 00:05 3563      /dev/dri/card0
afb28000-afb30000 rw-s 1d933f000 00:05 3563      /dev/dri/card0
afb30000-afb38000 rw-s 1d9337000 00:05 3563      /dev/dri/card0
afb38000-afb40000 rw-s 1d932f000 00:05 3563      /dev/dri/card0
afb40000-afb48000 rw-s 1d9327000 00:05 3563      /dev/dri/card0
afb48000-afb50000 rw-s 1d931f000 00:05 3563      /dev/dri/card0
afb50000-afb58000 rw-s 1d9317000 00:05 3563      /dev/dri/card0
afb58000-afb60000 rw-s 1d930f000 00:05 3563      /dev/dri/card0
afb60000-afb68000 rw-s 1d9307000 00:05 3563      /dev/dri/card0
afb68000-afb70000 rw-s 1d92f1000 00:05 3563      /dev/dri/card0
afb70000-afb78000 rw-s 1d92e9000 00:05 3563      /dev/dri/card0
afb78000-afb80000 rw-s 1d92e1000 00:05 3563      /dev/dri/card0
afb80000-afb88000 rw-s 1d92d9000 00:05 3563      /dev/dri/card0
afb88000-afb90000 rw-s 1d92d1000 00:05 3563      /dev/dri/card0
afb90000-afb98000 rw-s 1d92c9000 00:05 3563      /dev/dri/card0
afb98000-afba0000 rw-s 1d92ff000 00:05 3563      /dev/dri/card0
afba0000-afba8000 rw-s 1d92c1000 00:05 3563      /dev/dri/card0
afba8000-afbb0000 rw-s 1d92b9000 00:05 3563      /dev/dri/card0
afbb0000-afbb8000 rw-s 1d92b1000 00:05 3563      /dev/dri/card0
afbb8000-afbc0000 rw-s 1d92a9000 00:05 3563      /dev/dri/card0
afbc0000-afbc8000 rw-s 1d92a1000 00:05 3563      /dev/dri/card0
afbc8000-afbd0000 rw-s 1d9299000 00:05 3563      /dev/dri/card0
afbd0000-afbd8000 rw-s 1d9291000 00:05 3563      /dev/dri/card0
afbd8000-afbe0000 rw-s 1d9289000 00:05 3563      /dev/dri/card0
afbe0000-afbe8000 rw-s 1d9281000 00:05 3563      /dev/dri/card0
afbe8000-afbf0000 rw-s 1d9279000 00:05 3563      /dev/dri/card0
afbf0000-afbf8000 rw-s 1d9271000 00:05 3563      /dev/dri/card0
afbf8000-afc00000 rw-s 1d9269000 00:05 3563      /dev/dri/card0
afc00000-afc08000 rw-s 1d9261000 00:05 3563      /dev/dri/card0
afc08000-afc10000 rw-s 1d9259000 00:05 3563      /dev/dri/card0
afc10000-afc18000 rw-s 1d9251000 00:05 3563      /dev/dri/card0
afc18000-afc20000 rw-s 1d9249000 00:05 3563      /dev/dri/card0
afc20000-afc28000 rw-s 1d9241000 00:05 3563      /dev/dri/card0
afc28000-afc30000 rw-s 1d9239000 00:05 3563      /dev/dri/card0
afc30000-afc38000 rw-s 1d9231000 00:05 3563      /dev/dri/card0
afc38000-afc40000 rw-s 1d9229000 00:05 3563      /dev/dri/card0
afc40000-afc48000 rw-s 1d9221000 00:05 3563      /dev/dri/card0
afc48000-afc50000 rw-s 1d9219000 00:05 3563      /dev/dri/card0
afc50000-afc58000 rw-s 1d9211000 00:05 3563      /dev/dri/card0
afc58000-afc60000 rw-s 1d9209000 00:05 3563      /dev/dri/card0
afc60000-afc68000 rw-s 1d9201000 00:05 3563      /dev/dri/card0
afc68000-afc70000 rw-s 1d91f9000 00:05 3563      /dev/dri/card0
afc70000-afc78000 rw-s 1d91bc000 00:05 3563      /dev/dri/card0
afc78000-afc80000 rw-s 1d91b4000 00:05 3563      /dev/dri/card0
afc80000-afc88000 rw-s 1d91ac000 00:05 3563      /dev/dri/card0
afc88000-afc90000 rw-s 1d91a4000 00:05 3563      /dev/dri/card0
afc90000-afc98000 rw-s 1d919c000 00:05 3563      /dev/dri/card0
afc98000-afca0000 rw-s 1d9194000 00:05 3563      /dev/dri/card0
afca0000-afca8000 rw-s 1d91f1000 00:05 3563      /dev/dri/card0
afca8000-afcb0000 rw-s 1d91e9000 00:05 3563      /dev/dri/card0
afcb0000-afcb8000 rw-s 1d91e1000 00:05 3563      /dev/dri/card0
afcb8000-afcc0000 rw-s 1d91d9000 00:05 3563      /dev/dri/card0
afcc0000-afcc8000 rw-s 1d91d1000 00:05 3563      /dev/dri/card0
afcc8000-afcd0000 rw-s 1d91c9000 00:05 3563      /dev/dri/card0
afcd0000-afcd8000 rw-s 1d918b000 00:05 3563      /dev/dri/card0
afcd8000-afce0000 rw-s 1d9183000 00:05 3563      /dev/dri/card0
afce0000-afce8000 rw-s 1d917b000 00:05 3563      /dev/dri/card0
afce8000-afcf0000 rw-s 1d9173000 00:05 3563      /dev/dri/card0
afcf0000-afcf8000 rw-s 1d916b000 00:05 3563      /dev/dri/card0
afcf8000-afd00000 rw-s 1d9163000 00:05 3563      /dev/dri/card0
afd00000-afd08000 rw-s 1d915b000 00:05 3563      /dev/dri/card0
afd08000-afd10000 rw-s 1d9153000 00:05 3563      /dev/dri/card0
afd10000-afd18000 rw-s 1d914b000 00:05 3563      /dev/dri/card0
afd18000-afd20000 rw-s 1d9143000 00:05 3563      /dev/dri/card0
afd20000-afd28000 rw-s 1d913b000 00:05 3563      /dev/dri/card0
afd28000-afd30000 rw-s 1d9133000 00:05 3563      /dev/dri/card0
afd30000-afd38000 rw-s 1d912b000 00:05 3563      /dev/dri/card0
afd38000-afd40000 rw-s 1d9123000 00:05 3563      /dev/dri/card0
afd40000-afd48000 rw-s 1d911b000 00:05 3563      /dev/dri/card0
afd48000-afd50000 rw-s 1d9113000 00:05 3563      /dev/dri/card0
afd50000-afd58000 rw-s 1d910b000 00:05 3563      /dev/dri/card0
afd58000-afd60000 rw-s 1d9103000 00:05 3563      /dev/dri/card0
afd60000-afd68000 rw-s 1d90fb000 00:05 3563      /dev/dri/card0
afd68000-afd70000 rw-s 1d90f3000 00:05 3563      /dev/dri/card0
afd70000-afd78000 rw-s 1d90eb000 00:05 3563      /dev/dri/card0
afd78000-afd80000 rw-s 1d90e3000 00:05 3563      /dev/dri/card0
afd80000-afd88000 rw-s 1d90db000 00:05 3563      /dev/dri/card0
afd88000-afd90000 rw-s 1d90d3000 00:05 3563      /dev/dri/card0
afd90000-afd98000 rw-s 1d90cb000 00:05 3563      /dev/dri/card0
afd98000-afda0000 rw-s 1d90c3000 00:05 3563      /dev/dri/card0
afda0000-afda8000 rw-s 1d90bb000 00:05 3563      /dev/dri/card0
afda8000-afdb0000 rw-s 1d90b3000 00:05 3563      /dev/dri/card0
afdb0000-afdb8000 rw-s 1d90ab000 00:05 3563      /dev/dri/card0
afdb8000-afdc0000 rw-s 1d90a3000 00:05 3563      /dev/dri/card0
afdc0000-afdc8000 rw-s 1d909b000 00:05 3563      /dev/dri/card0
afdc8000-afdd0000 rw-s 1d9093000 00:05 3563      /dev/dri/card0
afdd0000-afdd8000 rw-s 1d908b000 00:05 3563      /dev/dri/card0
afdd8000-afde0000 rw-s 1d9083000 00:05 3563      /dev/dri/card0
afde0000-afde8000 rw-s 1d907b000 00:05 3563      /dev/dri/card0
afde8000-afdf0000 rw-s 1d9073000 00:05 3563      /dev/dri/card0
afdf0000-afdf8000 rw-s 1d906b000 00:05 3563      /dev/dri/card0
afdf8000-afe00000 rw-s 1d9063000 00:05 3563      /dev/dri/card0
afe00000-afe08000 rw-s 1d905b000 00:05 3563      /dev/dri/card0
afe08000-afe10000 rw-s 1d9053000 00:05 3563      /dev/dri/card0
afe10000-afe18000 rw-s 1d904b000 00:05 3563      /dev/dri/card0
afe18000-afe20000 rw-s 1d9043000 00:05 3563      /dev/dri/card0
afe20000-afe28000 rw-s 1d903b000 00:05 3563      /dev/dri/card0
afe28000-afe30000 rw-s 1d9033000 00:05 3563      /dev/dri/card0
afe30000-afe38000 rw-s 1d902b000 00:05 3563      /dev/dri/card0
afe38000-afe40000 rw-s 1d9023000 00:05 3563      /dev/dri/card0
afe40000-afe48000 rw-s 1d901b000 00:05 3563      /dev/dri/card0
afe48000-afe50000 rw-s 1d9013000 00:05 3563      /dev/dri/card0
afe50000-afe58000 rw-s 1d900b000 00:05 3563      /dev/dri/card0
afe58000-afe60000 rw-s 1d9003000 00:05 3563      /dev/dri/card0
afe60000-afe68000 rw-s 1d8f66000 00:05 3563      /dev/dri/card0
afe68000-afe70000 rw-s 1d8f5e000 00:05 3563      /dev/dri/card0
afe70000-afe78000 rw-s 1d8f56000 00:05 3563      /dev/dri/card0
afe78000-afe80000 rw-s 1d8f4e000 00:05 3563      /dev/dri/card0
afe80000-afe88000 rw-s 1d8f46000 00:05 3563      /dev/dri/card0
afe88000-afe90000 rw-s 1d8f3d000 00:05 3563      /dev/dri/card0
afe90000-afe98000 rw-s 1d8ffb000 00:05 3563      /dev/dri/card0
afe98000-afea0000 rw-s 1d8ff3000 00:05 3563      /dev/dri/card0
afea0000-afea8000 rw-s 1d8feb000 00:05 3563      /dev/dri/card0
afea8000-afeb0000 rw-s 1d8fe3000 00:05 3563      /dev/dri/card0
afeb0000-afeb8000 rw-s 1d8fdb000 00:05 3563      /dev/dri/card0
afeb8000-afec0000 rw-s 1d8fd3000 00:05 3563      /dev/dri/card0
afec0000-afec8000 rw-s 1d8fcb000 00:05 3563      /dev/dri/card0
afec8000-afed0000 rw-s 1d8fc3000 00:05 3563      /dev/dri/card0
afed0000-afed8000 rw-s 1d8fbb000 00:05 3563      /dev/dri/card0
afed8000-afee0000 rw-s 1d8fb3000 00:05 3563      /dev/dri/card0
afee0000-afee8000 rw-s 1d8fab000 00:05 3563      /dev/dri/card0
afee8000-afef0000 rw-s 1d8fa3000 00:05 3563      /dev/dri/card0
afef0000-afef8000 rw-s 1d8f9b000 00:05 3563      /dev/dri/card0
afef8000-aff00000 rw-s 1d8f93000 00:05 3563      /dev/dri/card0
aff00000-aff08000 rw-s 1d8f8b000 00:05 3563      /dev/dri/card0
aff08000-aff10000 rw-s 1d8f83000 00:05 3563      /dev/dri/card0
aff10000-aff18000 rw-s 1d8f7b000 00:05 3563      /dev/dri/card0
aff18000-aff20000 rw-s 1d8f73000 00:05 3563      /dev/dri/card0
aff20000-aff28000 rw-s 1d8f35000 00:05 3563      /dev/dri/card0
aff28000-aff30000 rw-s 1d8f2d000 00:05 3563      /dev/dri/card0
aff30000-aff38000 rw-s 1d8f25000 00:05 3563      /dev/dri/card0
aff38000-aff40000 rw-s 1d8f1d000 00:05 3563      /dev/dri/card0
aff40000-aff48000 rw-s 1d8f15000 00:05 3563      /dev/dri/card0
aff48000-aff50000 rw-s 1d8f0d000 00:05 3563      /dev/dri/card0
aff50000-aff58000 rw-s 1d8f05000 00:05 3563      /dev/dri/card0
aff58000-aff60000 rw-s 1d8ed7000 00:05 3563      /dev/dri/card0
aff60000-aff68000 rw-s 1d8ecf000 00:05 3563      /dev/dri/card0
aff68000-aff70000 rw-s 1d8ec7000 00:05 3563      /dev/dri/card0
aff70000-aff78000 rw-s 1d8ebf000 00:05 3563      /dev/dri/card0
aff78000-aff80000 rw-s 1d8eb7000 00:05 3563      /dev/dri/card0
aff80000-aff88000 rw-s 1d8eaf000 00:05 3563      /dev/dri/card0
aff88000-aff90000 rw-s 1d8efd000 00:05 3563      /dev/dri/card0
aff90000-aff98000 rw-s 1d8ef5000 00:05 3563      /dev/dri/card0
aff98000-affa0000 rw-s 1d8eed000 00:05 3563      /dev/dri/card0
affa0000-affa8000 rw-s 1d8ee5000 00:05 3563      /dev/dri/card0
affa8000-affb0000 rw-s 1d8ea7000 00:05 3563      /dev/dri/card0
affb0000-affb8000 rw-s 1d8e9f000 00:05 3563      /dev/dri/card0
affb8000-affc0000 rw-s 1d8e97000 00:05 3563      /dev/dri/card0
affc0000-affc8000 rw-s 1d8e8f000 00:05 3563      /dev/dri/card0
affc8000-affd0000 rw-s 1d8e87000 00:05 3563      /dev/dri/card0
affd0000-affd8000 rw-s 1d8e7f000 00:05 3563      /dev/dri/card0
affd8000-affe0000 rw-s 1d8e77000 00:05 3563      /dev/dri/card0
affe0000-affe8000 rw-s 1d8e5a000 00:05 3563      /dev/dri/card0
affe8000-afff0000 rw-s 1d8e52000 00:05 3563      /dev/dri/card0
afff0000-afff8000 rw-s 1d8e4a000 00:05 3563      /dev/dri/card0
afff8000-b0000000 rw-s 1d8e42000 00:05 3563      /dev/dri/card0
b0000000-b0008000 rw-s 1d8e3a000 00:05 3563      /dev/dri/card0
b0008000-b0010000 rw-s 1d8e32000 00:05 3563      /dev/dri/card0
b0010000-b0018000 rw-s 1d8e6f000 00:05 3563      /dev/dri/card0
b0018000-b0020000 rw-s 1d8e67000 00:05 3563      /dev/dri/card0
b0020000-b0028000 rw-s 1d8e29000 00:05 3563      /dev/dri/card0
b0028000-b0030000 rw-s 1d8e21000 00:05 3563      /dev/dri/card0
b0030000-b0038000 rw-s 1d8e19000 00:05 3563      /dev/dri/card0
b0038000-b0040000 rw-s 1d8e11000 00:05 3563      /dev/dri/card0
b0040000-b0048000 rw-s 1d8e09000 00:05 3563      /dev/dri/card0
b0048000-b0050000 rw-s 1d8df1000 00:05 3563      /dev/dri/card0
b0050000-b0058000 rw-s 1d8de9000 00:05 3563      /dev/dri/card0
b0058000-b0060000 rw-s 1d8de1000 00:05 3563      /dev/dri/card0
b0060000-b0068000 rw-s 1d8dd9000 00:05 3563      /dev/dri/card0
b0068000-b0070000 rw-s 1d8dd1000 00:05 3563      /dev/dri/card0
b0070000-b0078000 rw-s 1d8dc9000 00:05 3563      /dev/dri/card0
b0078000-b0080000 rw-s 1d8dc1000 00:05 3563      /dev/dri/card0
b0080000-b0088000 rw-s 1d8db9000 00:05 3563      /dev/dri/card0
b0088000-b0090000 rw-s 1d8e01000 00:05 3563      /dev/dri/card0
b0090000-b0098000 rw-s 1d8da9000 00:05 3563      /dev/dri/card0
b0098000-b00a0000 rw-s 1d8da1000 00:05 3563      /dev/dri/card0
b00a0000-b00a8000 rw-s 1d8d99000 00:05 3563      /dev/dri/card0
b00a8000-b00b0000 rw-s 1d8d91000 00:05 3563      /dev/dri/card0
b00b0000-b00b8000 rw-s 1d8d89000 00:05 3563      /dev/dri/card0
b00b8000-b00c0000 rw-s 1d8d81000 00:05 3563      /dev/dri/card0
b00c0000-b00c8000 rw-s 1d8d79000 00:05 3563      /dev/dri/card0
b00c8000-b00d0000 rw-s 1d8d71000 00:05 3563      /dev/dri/card0
b00d0000-b00d8000 rw-s 1d8d69000 00:05 3563      /dev/dri/card0
b00d8000-b00e0000 rw-s 1d8d61000 00:05 3563      /dev/dri/card0
b00e0000-b00e8000 rw-s 1d8d45000 00:05 3563      /dev/dri/card0
b00e8000-b00f0000 rw-s 1d8d3d000 00:05 3563      /dev/dri/card0
b00f0000-b00f8000 rw-s 1d8d35000 00:05 3563      /dev/dri/card0
b00f8000-b0100000 rw-s 1d8d2d000 00:05 3563      /dev/dri/card0
b0100000-b0108000 rw-s 1d8d24000 00:05 3563      /dev/dri/card0
b0108000-b0110000 rw-s 1d8d1c000 00:05 3563      /dev/dri/card0
b0110000-b0118000 rw-s 1d8d59000 00:05 3563      /dev/dri/card0
b0118000-b0120000 rw-s 1d8d51000 00:05 3563      /dev/dri/card0
b0120000-b0128000 rw-s 1d8d13000 00:05 3563      /dev/dri/card0
b0128000-b0130000 rw-s 1d8d0b000 00:05 3563      /dev/dri/card0
b0130000-b0138000 rw-s 1d8d03000 00:05 3563      /dev/dri/card0
b0138000-b0140000 rw-s 1d8cfb000 00:05 3563      /dev/dri/card0
b0140000-b0148000 rw-s 1d8cf3000 00:05 3563      /dev/dri/card0
b0148000-b0150000 rw-s 1d8ceb000 00:05 3563      /dev/dri/card0
b0150000-b0158000 rw-s 1d8ce3000 00:05 3563      /dev/dri/card0
b0158000-b0160000 rw-s 1d8db1000 00:05 3563      /dev/dri/card0
b0160000-b0168000 rw-s 1d8cd3000 00:05 3563      /dev/dri/card0
b0168000-b0170000 rw-s 1d8ccb000 00:05 3563      /dev/dri/card0
b0170000-b0178000 rw-s 1d8cc3000 00:05 3563      /dev/dri/card0
b0178000-b0180000 rw-s 1d8cbb000 00:05 3563      /dev/dri/card0
b0180000-b0188000 rw-s 1d8cb3000 00:05 3563      /dev/dri/card0
b0188000-b0190000 rw-s 1d8cab000 00:05 3563      /dev/dri/card0
b0190000-b0198000 rw-s 1d8ca3000 00:05 3563      /dev/dri/card0
b0198000-b01a0000 rw-s 1d8c9b000 00:05 3563      /dev/dri/card0
b01a0000-b01a8000 rw-s 1d8c93000 00:05 3563      /dev/dri/card0
b01a8000-b01b0000 rw-s 1d8c8b000 00:05 3563      /dev/dri/card0
b01b0000-b01b8000 rw-s 1d8c83000 00:05 3563      /dev/dri/card0
b01b8000-b01c0000 rw-s 1d8c55000 00:05 3563      /dev/dri/card0
b01c0000-b01c8000 rw-s 1d8c4d000 00:05 3563      /dev/dri/card0
b01c8000-b01d0000 rw-s 1d8c45000 00:05 3563      /dev/dri/card0
b01d0000-b01d8000 rw-s 1d8c3d000 00:05 3563      /dev/dri/card0
b01d8000-b01e0000 rw-s 1d8c35000 00:05 3563      /dev/dri/card0
b01e0000-b01e8000 rw-s 1d8c2d000 00:05 3563      /dev/dri/card0
b01e8000-b01f0000 rw-s 1d8c7b000 00:05 3563      /dev/dri/card0
b01f0000-b01f8000 rw-s 1d8c73000 00:05 3563      /dev/dri/card0
b01f8000-b0200000 rw-s 1d8c6b000 00:05 3563      /dev/dri/card0
b0200000-b0208000 rw-s 1d8c63000 00:05 3563      /dev/dri/card0
b0208000-b0210000 rw-s 1d8c25000 00:05 3563      /dev/dri/card0
b0210000-b0218000 rw-s 1d8c1d000 00:05 3563      /dev/dri/card0
b0218000-b0220000 rw-s 1d8c15000 00:05 3563      /dev/dri/card0
b0220000-b0228000 rw-s 1d8c0d000 00:05 3563      /dev/dri/card0
b0228000-b0230000 rw-s 1d8c05000 00:05 3563      /dev/dri/card0
b0230000-b0238000 rw-s 1d8bfd000 00:05 3563      /dev/dri/card0
b0238000-b0240000 rw-s 1d8bf5000 00:05 3563      /dev/dri/card0
b0240000-b0248000 rw-s 1d8bed000 00:05 3563      /dev/dri/card0
b0248000-b0250000 rw-s 1d8be5000 00:05 3563      /dev/dri/card0
b0250000-b0258000 rw-s 1d8bdd000 00:05 3563      /dev/dri/card0
b0258000-b0260000 rw-s 1d8bd5000 00:05 3563      /dev/dri/card0
b0260000-b0268000 rw-s 1d8bcd000 00:05 3563      /dev/dri/card0
b0268000-b0270000 rw-s 1d8bc5000 00:05 3563      /dev/dri/card0
b0270000-b0278000 rw-s 1d8bbd000 00:05 3563      /dev/dri/card0
b0278000-b0280000 rw-s 1d8b98000 00:05 3563      /dev/dri/card0
b0280000-b0288000 rw-s 1d8b90000 00:05 3563      /dev/dri/card0
b0288000-b0290000 rw-s 1d8b88000 00:05 3563      /dev/dri/card0
b0290000-b0298000 rw-s 1d8b80000 00:05 3563      /dev/dri/card0
b0298000-b02a0000 rw-s 1d8b78000 00:05 3563      /dev/dri/card0
b02a0000-b02a8000 rw-s 1d8b70000 00:05 3563      /dev/dri/card0
b02a8000-b02b0000 rw-s 1d8bb5000 00:05 3563      /dev/dri/card0
b02b0000-b02b8000 rw-s 1d8bad000 00:05 3563      /dev/dri/card0
b02b8000-b02c0000 rw-s 1d8ba5000 00:05 3563      /dev/dri/card0
b02c0000-b02c8000 rw-s 1d8b67000 00:05 3563      /dev/dri/card0
b02c8000-b02d0000 rw-s 1d8b5f000 00:05 3563      /dev/dri/card0
b02d0000-b02d8000 rw-s 1d8b57000 00:05 3563      /dev/dri/card0
b02d8000-b02e0000 rw-s 1d8b4f000 00:05 3563      /dev/dri/card0
b02e0000-b02e8000 rw-s 1d8b47000 00:05 3563      /dev/dri/card0
b02e8000-b02f0000 rw-s 1d8b3f000 00:05 3563      /dev/dri/card0
b02f0000-b02f8000 rw-s 1d8b37000 00:05 3563      /dev/dri/card0
b02f8000-b0300000 rw-s 1d8b2f000 00:05 3563      /dev/dri/card0
b0300000-b0308000 rw-s 1d8b27000 00:05 3563      /dev/dri/card0
b0308000-b0310000 rw-s 1d8b1f000 00:05 3563      /dev/dri/card0
b0310000-b0318000 rw-s 1d8b17000 00:05 3563      /dev/dri/card0
b0318000-b0320000 rw-s 1d8b0f000 00:05 3563      /dev/dri/card0
b0320000-b0328000 rw-s 1d8b07000 00:05 3563      /dev/dri/card0
b0328000-b0330000 rw-s 1d8aff000 00:05 3563      /dev/dri/card0
b0330000-b0338000 rw-s 1d8af7000 00:05 3563      /dev/dri/card0
b0338000-b0340000 rw-s 1d8aef000 00:05 3563      /dev/dri/card0
b0340000-b0348000 rw-s 1d8ae7000 00:05 3563      /dev/dri/card0
b0348000-b0350000 rw-s 1d8adf000 00:05 3563      /dev/dri/card0
b0350000-b0358000 rw-s 1d8ad7000 00:05 3563      /dev/dri/card0
b0358000-b0360000 rw-s 1d8acf000 00:05 3563      /dev/dri/card0
b0360000-b0368000 rw-s 1d8ac7000 00:05 3563      /dev/dri/card0
b0368000-b0370000 rw-s 1d8abf000 00:05 3563      /dev/dri/card0
b0370000-b0378000 rw-s 1d8ab7000 00:05 3563      /dev/dri/card0
b0378000-b0380000 rw-s 1d8aaf000 00:05 3563      /dev/dri/card0
b0380000-b0388000 rw-s 1d8aa7000 00:05 3563      /dev/dri/card0
b0388000-b0390000 rw-s 1d8a9f000 00:05 3563      /dev/dri/card0
b0390000-b0398000 rw-s 1d8a97000 00:05 3563      /dev/dri/card0
b0398000-b03a0000 rw-s 1d8a8f000 00:05 3563      /dev/dri/card0
b03a0000-b03a8000 rw-s 1d8a87000 00:05 3563      /dev/dri/card0
b03a8000-b03b0000 rw-s 1d8a7f000 00:05 3563      /dev/dri/card0
b03b0000-b03b8000 rw-s 1d8a77000 00:05 3563      /dev/dri/card0
b03b8000-b03c0000 rw-s 1d8a6f000 00:05 3563      /dev/dri/card0
b03c0000-b03c8000 rw-s 1d8a67000 00:05 3563      /dev/dri/card0
b03c8000-b03d0000 rw-s 1d8a5f000 00:05 3563      /dev/dri/card0
b03d0000-b03d8000 rw-s 1d8a57000 00:05 3563      /dev/dri/card0
b03d8000-b03e0000 rw-s 1d8a4f000 00:05 3563      /dev/dri/card0
b03e0000-b03e8000 rw-s 1d8a47000 00:05 3563      /dev/dri/card0
b03e8000-b03f0000 rw-s 1d8a3f000 00:05 3563      /dev/dri/card0
b03f0000-b03f8000 rw-s 1d8a37000 00:05 3563      /dev/dri/card0
b03f8000-b0400000 rw-s 1d8a2f000 00:05 3563      /dev/dri/card0
b0400000-b0408000 rw-s 1d8a27000 00:05 3563      /dev/dri/card0
b0408000-b0410000 rw-s 1d8a1f000 00:05 3563      /dev/dri/card0
b0410000-b0418000 rw-s 1d8a17000 00:05 3563      /dev/dri/card0
b0418000-b0420000 rw-s 1d8a0f000 00:05 3563      /dev/dri/card0
b0420000-b0428000 rw-s 1d8a07000 00:05 3563      /dev/dri/card0
b0428000-b0430000 rw-s 1d89ff000 00:05 3563      /dev/dri/card0
b0430000-b0438000 rw-s 1d89f7000 00:05 3563      /dev/dri/card0
b0438000-b0440000 rw-s 1d89ef000 00:05 3563      /dev/dri/card0
b0440000-b0448000 rw-s 1d89e7000 00:05 3563      /dev/dri/card0
b0448000-b0450000 rw-s 1d89df000 00:05 3563      /dev/dri/card0
b0450000-b0458000 rw-s 1d89d7000 00:05 3563      /dev/dri/card0
b0458000-b0460000 rw-s 1d89cf000 00:05 3563      /dev/dri/card0
b0460000-b0468000 rw-s 1d89c7000 00:05 3563      /dev/dri/card0
b0468000-b0470000 rw-s 1d89bf000 00:05 3563      /dev/dri/card0
b0470000-b0478000 rw-s 1d89b7000 00:05 3563      /dev/dri/card0
b0478000-b0480000 rw-s 1d89af000 00:05 3563      /dev/dri/card0
b0480000-b0488000 rw-s 1d89a7000 00:05 3563      /dev/dri/card0
b0488000-b0490000 rw-s 1d899f000 00:05 3563      /dev/dri/card0
b0490000-b0498000 rw-s 1d8961000 00:05 3563      /dev/dri/card0
b0498000-b04a0000 rw-s 1d8959000 00:05 3563      /dev/dri/card0
b04a0000-b04a8000 rw-s 1d8951000 00:05 3563      /dev/dri/card0
b04a8000-b04b0000 rw-s 1d8949000 00:05 3563      /dev/dri/card0
b04b0000-b04b8000 rw-s 1d9b27000 00:05 3563      /dev/dri/card0
b04b8000-b04c0000 rw-s 1da0c1000 00:05 3563      /dev/dri/card0
b04c0000-b04c8000 rw-s 1d8997000 00:05 3563      /dev/dri/card0
b04c8000-b04d0000 rw-s 1d898f000 00:05 3563      /dev/dri/card0
b04d0000-b04d8000 rw-s 1d8987000 00:05 3563      /dev/dri/card0
b04d8000-b04e0000 rw-s 1d897f000 00:05 3563      /dev/dri/card0
b04e0000-b04e8000 rw-s 1d8977000 00:05 3563      /dev/dri/card0
b04e8000-b04f0000 rw-s 1d896f000 00:05 3563      /dev/dri/card0
b04f0000-b04f8000 rw-s 1d8931000 00:05 3563      /dev/dri/card0
b04f8000-b0500000 rw-s 1d8929000 00:05 3563      /dev/dri/card0
b0500000-b0508000 rw-s 1d8921000 00:05 3563      /dev/dri/card0
b0508000-b0510000 rw-s 1d8919000 00:05 3563      /dev/dri/card0
b0510000-b0518000 rw-s 1d8911000 00:05 3563      /dev/dri/card0
b0518000-b0520000 rw-s 1d8909000 00:05 3563      /dev/dri/card0
b0520000-b0528000 rw-s 1d8901000 00:05 3563      /dev/dri/card0
b0528000-b0530000 rw-s 1d88f9000 00:05 3563      /dev/dri/card0
b0530000-b0538000 rw-s 1d88f1000 00:05 3563      /dev/dri/card0
b0538000-b0540000 rw-s 1d88ab000 00:05 3563      /dev/dri/card0
b0540000-b0548000 rw-s 1d88a3000 00:05 3563      /dev/dri/card0
b0548000-b0550000 rw-s 1d889b000 00:05 3563      /dev/dri/card0
b0550000-b0558000 rw-s 1d8893000 00:05 3563      /dev/dri/card0
b0558000-b0560000 rw-s 1d888b000 00:05 3563      /dev/dri/card0
b0560000-b0568000 rw-s 1d8883000 00:05 3563      /dev/dri/card0
b0568000-b0570000 rw-s 1d88e9000 00:05 3563      /dev/dri/card0
b0570000-b0578000 rw-s 1d88e1000 00:05 3563      /dev/dri/card0
b0578000-b0580000 rw-s 1d88d9000 00:05 3563      /dev/dri/card0
b0580000-b0588000 rw-s 1d88d1000 00:05 3563      /dev/dri/card0
b0588000-b0590000 rw-s 1d88c9000 00:05 3563      /dev/dri/card0
b0590000-b0598000 rw-s 1d88c1000 00:05 3563      /dev/dri/card0
b0598000-b05a0000 rw-s 1d88b3000 00:05 3563      /dev/dri/card0
b05a0000-b05a8000 rw-s 1d887b000 00:05 3563      /dev/dri/card0
b05a8000-b05b0000 rw-s 1d8873000 00:05 3563      /dev/dri/card0
b05b0000-b05b8000 rw-s 1d886b000 00:05 3563      /dev/dri/card0
b05b8000-b05c0000 rw-s 1d8863000 00:05 3563      /dev/dri/card0
b05c0000-b05c8000 rw-s 1d885b000 00:05 3563      /dev/dri/card0
b05c8000-b05d0000 rw-s 1d8853000 00:05 3563      /dev/dri/card0
b05d0000-b05d8000 rw-s 1d884b000 00:05 3563      /dev/dri/card0
b05d8000-b05e0000 rw-s 1d8843000 00:05 3563      /dev/dri/card0
b05e0000-b05e8000 rw-s 1d883b000 00:05 3563      /dev/dri/card0
b05e8000-b05f0000 rw-s 1d8833000 00:05 3563      /dev/dri/card0
b05f0000-b05f8000 rw-s 1d882b000 00:05 3563      /dev/dri/card0
b05f8000-b0600000 rw-s 1d8823000 00:05 3563      /dev/dri/card0
b0600000-b0608000 rw-s 1d881b000 00:05 3563      /dev/dri/card0
b0608000-b0610000 rw-s 1d8813000 00:05 3563      /dev/dri/card0
b0610000-b0618000 rw-s 1d880b000 00:05 3563      /dev/dri/card0
b0618000-b0620000 rw-s 1d8803000 00:05 3563      /dev/dri/card0
b0620000-b0628000 rw-s 1d87fb000 00:05 3563      /dev/dri/card0
b0628000-b0630000 rw-s 1d87f3000 00:05 3563      /dev/dri/card0
b0630000-b0638000 rw-s 1d87eb000 00:05 3563      /dev/dri/card0
b0638000-b0640000 rw-s 1d87e3000 00:05 3563      /dev/dri/card0
b0640000-b0648000 rw-s 1d87db000 00:05 3563      /dev/dri/card0
b0648000-b0650000 rw-s 1d87d3000 00:05 3563      /dev/dri/card0
b0650000-b0658000 rw-s 1d87cb000 00:05 3563      /dev/dri/card0
b0658000-b0660000 rw-s 1d87c3000 00:05 3563      /dev/dri/card0
b0660000-b0668000 rw-s 1d87bb000 00:05 3563      /dev/dri/card0
b0668000-b0670000 rw-s 1d87b3000 00:05 3563      /dev/dri/card0
b0670000-b0678000 rw-s 1d87ab000 00:05 3563      /dev/dri/card0
b0678000-b0680000 rw-s 1d87a3000 00:05 3563      /dev/dri/card0
b0680000-b0688000 rw-s 1d879b000 00:05 3563      /dev/dri/card0
b0688000-b0690000 rw-s 1d8793000 00:05 3563      /dev/dri/card0
b0690000-b0698000 rw-s 1d878b000 00:05 3563      /dev/dri/card0
b0698000-b06a0000 rw-s 1d8783000 00:05 3563      /dev/dri/card0
b06a0000-b06a8000 rw-s 1d877b000 00:05 3563      /dev/dri/card0
b06a8000-b06b0000 rw-s 1d874d000 00:05 3563      /dev/dri/card0
b06b0000-b06b8000 rw-s 1d8745000 00:05 3563      /dev/dri/card0
b06b8000-b06c0000 rw-s 1d873d000 00:05 3563      /dev/dri/card0
b06c0000-b06c8000 rw-s 1d8735000 00:05 3563      /dev/dri/card0
b06c8000-b06d0000 rw-s 1d872d000 00:05 3563      /dev/dri/card0
b06d0000-b06d8000 rw-s 1d8725000 00:05 3563      /dev/dri/card0
b06d8000-b06e0000 rw-s 1d8773000 00:05 3563      /dev/dri/card0
b06e0000-b06e8000 rw-s 1d876b000 00:05 3563      /dev/dri/card0
b06e8000-b06f0000 rw-s 1d8763000 00:05 3563      /dev/dri/card0
b06f0000-b06f8000 rw-s 1d875b000 00:05 3563      /dev/dri/card0
b06f8000-b0700000 rw-s 1d871d000 00:05 3563      /dev/dri/card0
b0700000-b0708000 rw-s 1d8715000 00:05 3563      /dev/dri/card0
b0708000-b0710000 rw-s 1d870d000 00:05 3563      /dev/dri/card0
b0710000-b0718000 rw-s 1d8705000 00:05 3563      /dev/dri/card0
b0718000-b0720000 rw-s 1d86fd000 00:05 3563      /dev/dri/card0
b0720000-b0728000 rw-s 1d86f5000 00:05 3563      /dev/dri/card0
b0728000-b0730000 rw-s 1d86ed000 00:05 3563      /dev/dri/card0
b0730000-b0738000 rw-s 1d86e5000 00:05 3563      /dev/dri/card0
b0738000-b0740000 rw-s 1d86dd000 00:05 3563      /dev/dri/card0
b0740000-b0748000 rw-s 1d86d5000 00:05 3563      /dev/dri/card0
b0748000-b0750000 rw-s 1d86cd000 00:05 3563      /dev/dri/card0
b0750000-b0758000 rw-s 1d86c5000 00:05 3563      /dev/dri/card0
b0758000-b0760000 rw-s 1d86bd000 00:05 3563      /dev/dri/card0
b0760000-b0768000 rw-s 1d86b5000 00:05 3563      /dev/dri/card0
b0768000-b0770000 rw-s 1d86ad000 00:05 3563      /dev/dri/card0
b0770000-b0778000 rw-s 1d86a5000 00:05 3563      /dev/dri/card0
b0778000-b0780000 rw-s 1d869d000 00:05 3563      /dev/dri/card0
b0780000-b0788000 rw-s 1d8695000 00:05 3563      /dev/dri/card0
b0788000-b0790000 rw-s 1d868d000 00:05 3563      /dev/dri/card0
b0790000-b0798000 rw-s 1d8685000 00:05 3563      /dev/dri/card0
b0798000-b07a0000 rw-s 1d867d000 00:05 3563      /dev/dri/card0
b07a0000-b07a8000 rw-s 1d8675000 00:05 3563      /dev/dri/card0
b07a8000-b07b0000 rw-s 1d866d000 00:05 3563      /dev/dri/card0
b07b0000-b07b8000 rw-s 1d8665000 00:05 3563      /dev/dri/card0
b07b8000-b07c0000 rw-s 1d865d000 00:05 3563      /dev/dri/card0
b07c0000-b07c8000 rw-s 1d8655000 00:05 3563      /dev/dri/card0
b07c8000-b07d0000 rw-s 1d864d000 00:05 3563      /dev/dri/card0
b07d0000-b07d8000 rw-s 1d8645000 00:05 3563      /dev/dri/card0
b07d8000-b07e0000 rw-s 1d863d000 00:05 3563      /dev/dri/card0
b07e0000-b07e8000 rw-s 1d8635000 00:05 3563      /dev/dri/card0
b07e8000-b07f0000 rw-s 1d862d000 00:05 3563      /dev/dri/card0
b07f0000-b07f8000 rw-s 1d8625000 00:05 3563      /dev/dri/card0
b07f8000-b0800000 rw-s 1d861d000 00:05 3563      /dev/dri/card0
b0800000-b0808000 rw-s 1d8615000 00:05 3563      /dev/dri/card0
b0808000-b0810000 rw-s 1d860d000 00:05 3563      /dev/dri/card0
b0810000-b0818000 rw-s 1d8605000 00:05 3563      /dev/dri/card0
b0818000-b0820000 rw-s 1d85fd000 00:05 3563      /dev/dri/card0
b0820000-b0828000 rw-s 1d85f5000 00:05 3563      /dev/dri/card0
b0828000-b0830000 rw-s 1d85ed000 00:05 3563      /dev/dri/card0
b0830000-b0838000 rw-s 1d85e5000 00:05 3563      /dev/dri/card0
b0838000-b0840000 rw-s 1d85dd000 00:05 3563      /dev/dri/card0
b0840000-b0848000 rw-s 1d85d5000 00:05 3563      /dev/dri/card0
b0848000-b0850000 rw-s 1d85cd000 00:05 3563      /dev/dri/card0
b0850000-b0858000 rw-s 1d85c5000 00:05 3563      /dev/dri/card0
b0858000-b0860000 rw-s 1d85bd000 00:05 3563      /dev/dri/card0
b0860000-b0868000 rw-s 1d85b5000 00:05 3563      /dev/dri/card0
b0868000-b0870000 rw-s 1d85ad000 00:05 3563      /dev/dri/card0
b0870000-b0878000 rw-s 1d85a5000 00:05 3563      /dev/dri/card0
b0878000-b0880000 rw-s 1d859d000 00:05 3563      /dev/dri/card0
b0880000-b0888000 rw-s 1d8595000 00:05 3563      /dev/dri/card0
b0888000-b0890000 rw-s 1d858d000 00:05 3563      /dev/dri/card0
b0890000-b0898000 rw-s 1d8585000 00:05 3563      /dev/dri/card0
b0898000-b08a0000 rw-s 1d857d000 00:05 3563      /dev/dri/card0
b08a0000-b08a8000 rw-s 1d8575000 00:05 3563      /dev/dri/card0
b08a8000-b08b0000 rw-s 1d8518000 00:05 3563      /dev/dri/card0
b08b0000-b08b8000 rw-s 1d8510000 00:05 3563      /dev/dri/card0
b08b8000-b08c0000 rw-s 1d8508000 00:05 3563      /dev/dri/card0
b08c0000-b08c8000 rw-s 1d8500000 00:05 3563      /dev/dri/card0
b08c8000-b08d0000 rw-s 1d84f8000 00:05 3563      /dev/dri/card0
b08d0000-b08d8000 rw-s 1d84f0000 00:05 3563      /dev/dri/card0
b08d8000-b08e0000 rw-s 1d856d000 00:05 3563      /dev/dri/card0
b08e0000-b08e8000 rw-s 1d8565000 00:05 3563      /dev/dri/card0
b08e8000-b08f0000 rw-s 1d855d000 00:05 3563      /dev/dri/card0
b08f0000-b08f8000 rw-s 1d8555000 00:05 3563      /dev/dri/card0
b08f8000-b0900000 rw-s 1d854d000 00:05 3563      /dev/dri/card0
b0900000-b0908000 rw-s 1d8545000 00:05 3563      /dev/dri/card0
b0908000-b0910000 rw-s 1d853d000 00:05 3563      /dev/dri/card0
b0910000-b0918000 rw-s 1d84e7000 00:05 3563      /dev/dri/card0
b0918000-b0920000 rw-s 1d8530000 00:05 3563      /dev/dri/card0
b0920000-b0928000 rw-s 1d8528000 00:05 3563      /dev/dri/card0
b0928000-b0930000 rw-s 1d8520000 00:05 3563      /dev/dri/card0
b0930000-b0938000 rw-s 1d84df000 00:05 3563      /dev/dri/card0
b0938000-b0940000 rw-s 1d84d7000 00:05 3563      /dev/dri/card0
b0940000-b0948000 rw-s 1d84cf000 00:05 3563      /dev/dri/card0
b0948000-b0950000 rw-s 1d84c7000 00:05 3563      /dev/dri/card0
b0950000-b0958000 rw-s 1d84bf000 00:05 3563      /dev/dri/card0
b0958000-b0960000 rw-s 1d84b7000 00:05 3563      /dev/dri/card0
b0960000-b0968000 rw-s 1d84af000 00:05 3563      /dev/dri/card0
b0968000-b0970000 rw-s 1d84a7000 00:05 3563      /dev/dri/card0
b0970000-b0978000 rw-s 1d849f000 00:05 3563      /dev/dri/card0
b0978000-b0980000 rw-s 1d8497000 00:05 3563      /dev/dri/card0
b0980000-b0988000 rw-s 1d848f000 00:05 3563      /dev/dri/card0
b0988000-b0990000 rw-s 1d8487000 00:05 3563      /dev/dri/card0
b0990000-b0998000 rw-s 1d847f000 00:05 3563      /dev/dri/card0
b0998000-b09a0000 rw-s 1d8477000 00:05 3563      /dev/dri/card0
b09a0000-b09a8000 rw-s 1d846f000 00:05 3563      /dev/dri/card0
b09a8000-b09b0000 rw-s 1d8467000 00:05 3563      /dev/dri/card0
b09b0000-b09b8000 rw-s 1d845f000 00:05 3563      /dev/dri/card0
b09b8000-b09c0000 rw-s 1d8457000 00:05 3563      /dev/dri/card0
b09c0000-b09c8000 rw-s 1d844f000 00:05 3563      /dev/dri/card0
b09c8000-b09d0000 rw-s 1d8447000 00:05 3563      /dev/dri/card0
b09d0000-b09d8000 rw-s 1d843f000 00:05 3563      /dev/dri/card0
b09d8000-b09e0000 rw-s 1d8437000 00:05 3563      /dev/dri/card0
b09e0000-b09e8000 rw-s 1d842f000 00:05 3563      /dev/dri/card0
b09e8000-b09f0000 rw-s 1d8427000 00:05 3563      /dev/dri/card0
b09f0000-b09f8000 rw-s 1d841f000 00:05 3563      /dev/dri/card0
b09f8000-b0a00000 rw-s 1d8417000 00:05 3563      /dev/dri/card0
b0a00000-b0a08000 rw-s 1d840f000 00:05 3563      /dev/dri/card0
b0a08000-b0a10000 rw-s 1d8407000 00:05 3563      /dev/dri/card0
b0a10000-b0a18000 rw-s 1d83ff000 00:05 3563      /dev/dri/card0
b0a18000-b0a20000 rw-s 1d83f7000 00:05 3563      /dev/dri/card0
b0a20000-b0a28000 rw-s 1d83ef000 00:05 3563      /dev/dri/card0
b0a28000-b0a30000 rw-s 1d83e7000 00:05 3563      /dev/dri/card0
b0a30000-b0a38000 rw-s 1d83df000 00:05 3563      /dev/dri/card0
b0a38000-b0a40000 rw-s 1d83d7000 00:05 3563      /dev/dri/card0
b0a40000-b0a48000 rw-s 1d83cf000 00:05 3563      /dev/dri/card0
b0a48000-b0a50000 rw-s 1d83c7000 00:05 3563      /dev/dri/card0
b0a50000-b0a58000 rw-s 1d83bf000 00:05 3563      /dev/dri/card0
b0a58000-b0a60000 rw-s 1d83b7000 00:05 3563      /dev/dri/card0
b0a60000-b0a68000 rw-s 1d83af000 00:05 3563      /dev/dri/card0
b0a68000-b0a70000 rw-s 1d83a7000 00:05 3563      /dev/dri/card0
b0a70000-b0a78000 rw-s 1d839f000 00:05 3563      /dev/dri/card0
b0a78000-b0a80000 rw-s 1d8397000 00:05 3563      /dev/dri/card0
b0a80000-b0a88000 rw-s 1d838f000 00:05 3563      /dev/dri/card0
b0a88000-b0a90000 rw-s 1d8387000 00:05 3563      /dev/dri/card0
b0a90000-b0a98000 rw-s 1d837f000 00:05 3563      /dev/dri/card0
b0a98000-b0aa0000 rw-s 1d8377000 00:05 3563      /dev/dri/card0
b0aa0000-b0aa8000 rw-s 1d8323000 00:05 3563      /dev/dri/card0
b0aa8000-b0ab0000 rw-s 1d831b000 00:05 3563      /dev/dri/card0
b0ab0000-b0ab8000 rw-s 1d8313000 00:05 3563      /dev/dri/card0
b0ab8000-b0ac0000 rw-s 1d830b000 00:05 3563      /dev/dri/card0
b0ac0000-b0ac8000 rw-s 1d8303000 00:05 3563      /dev/dri/card0
b0ac8000-b0ad0000 rw-s 1d82fa000 00:05 3563      /dev/dri/card0
b0ad0000-b0ad8000 rw-s 1d836f000 00:05 3563      /dev/dri/card0
b0ad8000-b0ae0000 rw-s 1d8367000 00:05 3563      /dev/dri/card0
b0ae0000-b0ae8000 rw-s 1d835f000 00:05 3563      /dev/dri/card0
b0ae8000-b0af0000 rw-s 1d8357000 00:05 3563      /dev/dri/card0
b0af0000-b0af8000 rw-s 1d834f000 00:05 3563      /dev/dri/card0
b0af8000-b0b00000 rw-s 1d8347000 00:05 3563      /dev/dri/card0
b0b00000-b0b08000 rw-s 1d833f000 00:05 3563      /dev/dri/card0
b0b08000-b0b10000 rw-s 1d8337000 00:05 3563      /dev/dri/card0
b0b10000-b0b18000 rw-s 1d832f000 00:05 3563      /dev/dri/card0
b0b18000-b0b20000 rw-s 1d82f1000 00:05 3563      /dev/dri/card0
b0b20000-b0b28000 rw-s 1d82e9000 00:05 3563      /dev/dri/card0
b0b28000-b0b30000 rw-s 1d82e1000 00:05 3563      /dev/dri/card0
b0b30000-b0b38000 rw-s 1d82d9000 00:05 3563      /dev/dri/card0
b0b38000-b0b40000 rw-s 1d82d1000 00:05 3563      /dev/dri/card0
b0b40000-b0b48000 rw-s 1d82c9000 00:05 3563      /dev/dri/card0
b0b48000-b0b50000 rw-s 1d82c1000 00:05 3563      /dev/dri/card0
b0b50000-b0b58000 rw-s 1d82b9000 00:05 3563      /dev/dri/card0
b0b58000-b0b60000 rw-s 1d82b1000 00:05 3563      /dev/dri/card0
b0b60000-b0b68000 rw-s 1d82a9000 00:05 3563      /dev/dri/card0
b0b68000-b0b70000 rw-s 1d82a1000 00:05 3563      /dev/dri/card0
b0b70000-b0b78000 rw-s 1d8299000 00:05 3563      /dev/dri/card0
b0b78000-b0b80000 rw-s 1d8291000 00:05 3563      /dev/dri/card0
b0b80000-b0b88000 rw-s 1d8289000 00:05 3563      /dev/dri/card0
b0b88000-b0b90000 rw-s 1d8281000 00:05 3563      /dev/dri/card0
b0b90000-b0b98000 rw-s 1d8279000 00:05 3563      /dev/dri/card0
b0b98000-b0ba0000 rw-s 1d8271000 00:05 3563      /dev/dri/card0
b0ba0000-b0ba8000 rw-s 1d8269000 00:05 3563      /dev/dri/card0
b0ba8000-b0bb0000 rw-s 1d8261000 00:05 3563      /dev/dri/card0
b0bb0000-b0bb8000 rw-s 1d8259000 00:05 3563      /dev/dri/card0
b0bb8000-b0bc0000 rw-s 1d8251000 00:05 3563      /dev/dri/card0
b0bc0000-b0bc8000 rw-s 1d8249000 00:05 3563      /dev/dri/card0
b0bc8000-b0bd0000 rw-s 1d8241000 00:05 3563      /dev/dri/card0
b0bd0000-b0bd8000 rw-s 1d8239000 00:05 3563      /dev/dri/card0
b0bd8000-b0be0000 rw-s 1d8231000 00:05 3563      /dev/dri/card0
b0be0000-b0be8000 rw-s 1d8229000 00:05 3563      /dev/dri/card0
b0be8000-b0bf0000 rw-s 1d8221000 00:05 3563      /dev/dri/card0
b0bf0000-b0bf8000 rw-s 1d81dc000 00:05 3563      /dev/dri/card0
b0bf8000-b0c00000 rw-s 1d81d4000 00:05 3563      /dev/dri/card0
b0c00000-b0c08000 rw-s 1d81cc000 00:05 3563      /dev/dri/card0
b0c08000-b0c10000 rw-s 1d81c4000 00:05 3563      /dev/dri/card0
b0c10000-b0c18000 rw-s 1d81bc000 00:05 3563      /dev/dri/card0
b0c18000-b0c20000 rw-s 1d81b4000 00:05 3563      /dev/dri/card0
b0c20000-b0c28000 rw-s 1d8219000 00:05 3563      /dev/dri/card0
b0c28000-b0c30000 rw-s 1d8211000 00:05 3563      /dev/dri/card0
b0c30000-b0c38000 rw-s 1d8209000 00:05 3563      /dev/dri/card0
b0c38000-b0c40000 rw-s 1d8201000 00:05 3563      /dev/dri/card0
b0c40000-b0c48000 rw-s 1d81f9000 00:05 3563      /dev/dri/card0
b0c48000-b0c50000 rw-s 1d81f1000 00:05 3563      /dev/dri/card0
b0c50000-b0c58000 rw-s 1d81e9000 00:05 3563      /dev/dri/card0
b0c58000-b0c60000 rw-s 1d81ab000 00:05 3563      /dev/dri/card0
b0c60000-b0c68000 rw-s 1d81a3000 00:05 3563      /dev/dri/card0
b0c68000-b0c70000 rw-s 1d819b000 00:05 3563      /dev/dri/card0
b0c70000-b0c78000 rw-s 1d8193000 00:05 3563      /dev/dri/card0
b0c78000-b0c80000 rw-s 1d818b000 00:05 3563      /dev/dri/card0
b0c80000-b0c88000 rw-s 1d8183000 00:05 3563      /dev/dri/card0
b0c88000-b0c90000 rw-s 1d817b000 00:05 3563      /dev/dri/card0
b0c90000-b0c98000 rw-s 1d8173000 00:05 3563      /dev/dri/card0
b0c98000-b0ca0000 rw-s 1d816b000 00:05 3563      /dev/dri/card0
b0ca0000-b0ca8000 rw-s 1d8163000 00:05 3563      /dev/dri/card0
b0ca8000-b0cb0000 rw-s 1d815b000 00:05 3563      /dev/dri/card0
b0cb0000-b0cb8000 rw-s 1d8153000 00:05 3563      /dev/dri/card0
b0cb8000-b0cc0000 rw-s 1d814b000 00:05 3563      /dev/dri/card0
b0cc0000-b0cc8000 rw-s 1d8143000 00:05 3563      /dev/dri/card0
b0cc8000-b0cd0000 rw-s 1d813b000 00:05 3563      /dev/dri/card0
b0cd0000-b0cd8000 rw-s 1d8133000 00:05 3563      /dev/dri/card0
b0cd8000-b0ce0000 rw-s 1d812b000 00:05 3563      /dev/dri/card0
b0ce0000-b0ce8000 rw-s 1d8123000 00:05 3563      /dev/dri/card0
b0ce8000-b0cf0000 rw-s 1d811b000 00:05 3563      /dev/dri/card0
b0cf0000-b0cf8000 rw-s 1d8113000 00:05 3563      /dev/dri/card0
b0cf8000-b0d00000 rw-s 1d810b000 00:05 3563      /dev/dri/card0
b0d00000-b0d08000 rw-s 1d8103000 00:05 3563      /dev/dri/card0
b0d08000-b0d10000 rw-s 1d80fb000 00:05 3563      /dev/dri/card0
b0d10000-b0d18000 rw-s 1d80f3000 00:05 3563      /dev/dri/card0
b0d18000-b0d20000 rw-s 1d80eb000 00:05 3563      /dev/dri/card0
b0d20000-b0d28000 rw-s 1d80e3000 00:05 3563      /dev/dri/card0
b0d28000-b0d30000 rw-s 1d80db000 00:05 3563      /dev/dri/card0
b0d30000-b0d38000 rw-s 1d80d3000 00:05 3563      /dev/dri/card0
b0d38000-b0d40000 rw-s 1d80cb000 00:05 3563      /dev/dri/card0
b0d40000-b0d48000 rw-s 1d80c3000 00:05 3563      /dev/dri/card0
b0d48000-b0d50000 rw-s 1d80bb000 00:05 3563      /dev/dri/card0
b0d50000-b0d58000 rw-s 1d807d000 00:05 3563      /dev/dri/card0
b0d58000-b0d60000 rw-s 1d8075000 00:05 3563      /dev/dri/card0
b0d60000-b0d68000 rw-s 1d806d000 00:05 3563      /dev/dri/card0
b0d68000-b0d70000 rw-s 1d8065000 00:05 3563      /dev/dri/card0
b0d70000-b0d78000 rw-s 1d805d000 00:05 3563      /dev/dri/card0
b0d78000-b0d80000 rw-s 1d8055000 00:05 3563      /dev/dri/card0
b0d80000-b0d88000 rw-s 1d80b3000 00:05 3563      /dev/dri/card0
b0d88000-b0d90000 rw-s 1d80ab000 00:05 3563      /dev/dri/card0
b0d90000-b0d98000 rw-s 1d80a3000 00:05 3563      /dev/dri/card0
b0d98000-b0da0000 rw-s 1d809b000 00:05 3563      /dev/dri/card0
b0da0000-b0da8000 rw-s 1d8093000 00:05 3563      /dev/dri/card0
b0da8000-b0db0000 rw-s 1d808b000 00:05 3563      /dev/dri/card0
b0db0000-b0db8000 rw-s 1d804d000 00:05 3563      /dev/dri/card0
b0db8000-b0dc0000 rw-s 1d8045000 00:05 3563      /dev/dri/card0
b0dc0000-b0dc8000 rw-s 1d803d000 00:05 3563      /dev/dri/card0
b0dc8000-b0dd0000 rw-s 1d8035000 00:05 3563      /dev/dri/card0
b0dd0000-b0dd8000 rw-s 1d802d000 00:05 3563      /dev/dri/card0
b0dd8000-b0de0000 rw-s 1d8025000 00:05 3563      /dev/dri/card0
b0de0000-b0de8000 rw-s 1d801d000 00:05 3563      /dev/dri/card0
b0de8000-b0df0000 rw-s 1d8015000 00:05 3563      /dev/dri/card0
b0df0000-b0df8000 rw-s 1d800d000 00:05 3563      /dev/dri/card0
b0df8000-b0e00000 rw-s 1d8005000 00:05 3563      /dev/dri/card0
b0e00000-b0e08000 rw-s 1d7ffd000 00:05 3563      /dev/dri/card0
b0e08000-b0e10000 rw-s 1d7ff5000 00:05 3563      /dev/dri/card0
b0e10000-b0e18000 rw-s 1d7fed000 00:05 3563      /dev/dri/card0
b0e18000-b0e20000 rw-s 1d7fe5000 00:05 3563      /dev/dri/card0
b0e20000-b0e28000 rw-s 1d7fdd000 00:05 3563      /dev/dri/card0
b0e28000-b0e30000 rw-s 1d7fd5000 00:05 3563      /dev/dri/card0
b0e30000-b0e38000 rw-s 1d7fcd000 00:05 3563      /dev/dri/card0
b0e38000-b0e40000 rw-s 1d7f6f000 00:05 3563      /dev/dri/card0
b0e40000-b0e48000 rw-s 1d7f67000 00:05 3563      /dev/dri/card0
b0e48000-b0e50000 rw-s 1d7f5f000 00:05 3563      /dev/dri/card0
b0e50000-b0e58000 rw-s 1d7f57000 00:05 3563      /dev/dri/card0
b0e58000-b0e60000 rw-s 1d7f4f000 00:05 3563      /dev/dri/card0
b0e60000-b0e68000 rw-s 1d7f47000 00:05 3563      /dev/dri/card0
b0e68000-b0e70000 rw-s 1d7fc5000 00:05 3563      /dev/dri/card0
b0e70000-b0e78000 rw-s 1d7fbd000 00:05 3563      /dev/dri/card0
b0e78000-b0e80000 rw-s 1d7fb5000 00:05 3563      /dev/dri/card0
b0e80000-b0e88000 rw-s 1d7fad000 00:05 3563      /dev/dri/card0
b0e88000-b0e90000 rw-s 1d7fa5000 00:05 3563      /dev/dri/card0
b0e90000-b0e98000 rw-s 1d7f9d000 00:05 3563      /dev/dri/card0
b0e98000-b0ea0000 rw-s 1d7f95000 00:05 3563      /dev/dri/card0
b0ea0000-b0ea8000 rw-s 1d7f8d000 00:05 3563      /dev/dri/card0
b0ea8000-b0eb0000 rw-s 1d7f85000 00:05 3563      /dev/dri/card0
b0eb0000-b0eb8000 rw-s 1d7f7d000 00:05 3563      /dev/dri/card0
b0eb8000-b0ec0000 rw-s 1d7f3f000 00:05 3563      /dev/dri/card0
b0ec0000-b0ec8000 rw-s 1d7f37000 00:05 3563      /dev/dri/card0
b0ec8000-b0ed0000 rw-s 1d7f2f000 00:05 3563      /dev/dri/card0
b0ed0000-b0ed8000 rw-s 1d7f27000 00:05 3563      /dev/dri/card0
b0ed8000-b0ee0000 rw-s 1d7f1f000 00:05 3563      /dev/dri/card0
b0ee0000-b0ee8000 rw-s 1d7f17000 00:05 3563      /dev/dri/card0
b0ee8000-b0ef0000 rw-s 1d7f0f000 00:05 3563      /dev/dri/card0
b0ef0000-b0ef8000 rw-s 1d7f07000 00:05 3563      /dev/dri/card0
b0ef8000-b0f00000 rw-s 1d7eff000 00:05 3563      /dev/dri/card0
b0f00000-b0f08000 rw-s 1d7ee9000 00:05 3563      /dev/dri/card0
b0f08000-b0f10000 rw-s 1d7ee1000 00:05 3563      /dev/dri/card0
b0f10000-b0f18000 rw-s 1d7ed9000 00:05 3563      /dev/dri/card0
b0f18000-b0f20000 rw-s 1d7ed1000 00:05 3563      /dev/dri/card0
b0f20000-b0f28000 rw-s 1d7ec9000 00:05 3563      /dev/dri/card0
b0f28000-b0f30000 rw-s 1d7ec1000 00:05 3563      /dev/dri/card0
b0f30000-b0f38000 rw-s 1d7ef7000 00:05 3563      /dev/dri/card0
b0f38000-b0f40000 rw-s 1d7eb9000 00:05 3563      /dev/dri/card0
b0f40000-b0f48000 rw-s 1d7eb1000 00:05 3563      /dev/dri/card0
b0f48000-b0f50000 rw-s 1d7ea9000 00:05 3563      /dev/dri/card0
b0f50000-b0f58000 rw-s 1d7ea1000 00:05 3563      /dev/dri/card0
b0f58000-b0f60000 rw-s 1d7e5c000 00:05 3563      /dev/dri/card0
b0f60000-b0f68000 rw-s 1d7e54000 00:05 3563      /dev/dri/card0
b0f68000-b0f70000 rw-s 1d7e4c000 00:05 3563      /dev/dri/card0
b0f70000-b0f78000 rw-s 1d7e44000 00:05 3563      /dev/dri/card0
b0f78000-b0f80000 rw-s 1d7e3c000 00:05 3563      /dev/dri/card0
b0f80000-b0f88000 rw-s 1d7e34000 00:05 3563      /dev/dri/card0
b0f88000-b0f90000 rw-s 1d7e99000 00:05 3563      /dev/dri/card0
b0f90000-b0f98000 rw-s 1d7e91000 00:05 3563      /dev/dri/card0
b0f98000-b0fa0000 rw-s 1d7e89000 00:05 3563      /dev/dri/card0
b0fa0000-b0fa8000 rw-s 1d7e81000 00:05 3563      /dev/dri/card0
b0fa8000-b0fb0000 rw-s 1d7e79000 00:05 3563      /dev/dri/card0
b0fb0000-b0fb8000 rw-s 1d7e71000 00:05 3563      /dev/dri/card0
b0fb8000-b0fc0000 rw-s 1d7e69000 00:05 3563      /dev/dri/card0
b0fc0000-b0fc8000 rw-s 1d7e2b000 00:05 3563      /dev/dri/card0
b0fc8000-b0fd0000 rw-s 1d7e23000 00:05 3563      /dev/dri/card0
b0fd0000-b0fd8000 rw-s 1d7e1b000 00:05 3563      /dev/dri/card0
b0fd8000-b0fe0000 rw-s 1d7e13000 00:05 3563      /dev/dri/card0
b0fe0000-b0fe8000 rw-s 1d7e0b000 00:05 3563      /dev/dri/card0
b0fe8000-b0ff0000 rw-s 1d7e03000 00:05 3563      /dev/dri/card0
b0ff0000-b0ff8000 rw-s 1d7dfb000 00:05 3563      /dev/dri/card0
b0ff8000-b1000000 rw-s 1d7df3000 00:05 3563      /dev/dri/card0
b1000000-b1008000 rw-s 1d7deb000 00:05 3563      /dev/dri/card0
b1008000-b1010000 rw-s 1d7de3000 00:05 3563      /dev/dri/card0
b1010000-b1018000 rw-s 1d7ddb000 00:05 3563      /dev/dri/card0
b1018000-b1020000 rw-s 1d7dd3000 00:05 3563      /dev/dri/card0
b1020000-b1028000 rw-s 1d7dcb000 00:05 3563      /dev/dri/card0
b1028000-b1030000 rw-s 1d7dc3000 00:05 3563      /dev/dri/card0
b1030000-b1038000 rw-s 1d7da5000 00:05 3563      /dev/dri/card0
b1038000-b1040000 rw-s 1d7d9d000 00:05 3563      /dev/dri/card0
b1040000-b1048000 rw-s 1d7d95000 00:05 3563      /dev/dri/card0
b1048000-b1050000 rw-s 1d7d8d000 00:05 3563      /dev/dri/card0
b1050000-b1058000 rw-s 1d7d85000 00:05 3563      /dev/dri/card0
b1058000-b1060000 rw-s 1d7d7d000 00:05 3563      /dev/dri/card0
b1060000-b1068000 rw-s 1d7dbb000 00:05 3563      /dev/dri/card0
b1068000-b1070000 rw-s 1d7db3000 00:05 3563      /dev/dri/card0
b1070000-b1078000 rw-s 1d7d75000 00:05 3563      /dev/dri/card0
b1078000-b1080000 rw-s 1d7d6d000 00:05 3563      /dev/dri/card0
b1080000-b1088000 rw-s 1d7d65000 00:05 3563      /dev/dri/card0
b1088000-b1090000 rw-s 1d7d5d000 00:05 3563      /dev/dri/card0
b1090000-b1098000 rw-s 1d7d55000 00:05 3563      /dev/dri/card0
b1098000-b10a0000 rw-s 1d7d4d000 00:05 3563      /dev/dri/card0
b10a0000-b10a8000 rw-s 1d7d45000 00:05 3563      /dev/dri/card0
b10a8000-b10b0000 rw-s 1d7d3d000 00:05 3563      /dev/dri/card0
b10b0000-b10b8000 rw-s 1d7d35000 00:05 3563      /dev/dri/card0
b10b8000-b10c0000 rw-s 1d7d2d000 00:05 3563      /dev/dri/card0
b10c0000-b10c8000 rw-s 1d7d25000 00:05 3563      /dev/dri/card0
b10c8000-b10d0000 rw-s 1d7d1d000 00:05 3563      /dev/dri/card0
b10d0000-b10d8000 rw-s 1d7d15000 00:05 3563      /dev/dri/card0
b10d8000-b10e0000 rw-s 1d7d0d000 00:05 3563      /dev/dri/card0
b10e0000-b10e8000 rw-s 1d7d05000 00:05 3563      /dev/dri/card0
b10e8000-b10f0000 rw-s 1d7cfd000 00:05 3563      /dev/dri/card0
b10f0000-b10f8000 rw-s 1d7cf5000 00:05 3563      /dev/dri/card0
b10f8000-b1100000 rw-s 1d7ced000 00:05 3563      /dev/dri/card0
b1100000-b1108000 rw-s 1d7ce5000 00:05 3563      /dev/dri/card0
b1108000-b1110000 rw-s 1d7cdd000 00:05 3563      /dev/dri/card0
b1110000-b1118000 rw-s 1d7cd5000 00:05 3563      /dev/dri/card0
b1118000-b1120000 rw-s 1d7ccd000 00:05 3563      /dev/dri/card0
b1120000-b1128000 rw-s 1d7cc5000 00:05 3563      /dev/dri/card0
b1128000-b1130000 rw-s 1d7cbd000 00:05 3563      /dev/dri/card0
b1130000-b1138000 rw-s 1d7cb5000 00:05 3563      /dev/dri/card0
b1138000-b1140000 rw-s 1d7cad000 00:05 3563      /dev/dri/card0
b1140000-b1148000 rw-s 1d7ca5000 00:05 3563      /dev/dri/card0
b1148000-b1150000 rw-s 1d7c9d000 00:05 3563      /dev/dri/card0
b1150000-b1158000 rw-s 1d7c95000 00:05 3563      /dev/dri/card0
b1158000-b1160000 rw-s 1d7c8d000 00:05 3563      /dev/dri/card0
b1160000-b1168000 rw-s 1d7c85000 00:05 3563      /dev/dri/card0
b1168000-b1170000 rw-s 1d7c7d000 00:05 3563      /dev/dri/card0
b1170000-b1178000 rw-s 1d7c75000 00:05 3563      /dev/dri/card0
b1178000-b1180000 rw-s 1d7c6d000 00:05 3563      /dev/dri/card0
b1180000-b1188000 rw-s 1d7c65000 00:05 3563      /dev/dri/card0
b1188000-b1190000 rw-s 1d7c28000 00:05 3563      /dev/dri/card0
b1190000-b1198000 rw-s 1d7c20000 00:05 3563      /dev/dri/card0
b1198000-b11a0000 rw-s 1d7c18000 00:05 3563      /dev/dri/card0
b11a0000-b11a8000 rw-s 1d7c10000 00:05 3563      /dev/dri/card0
b11a8000-b11b0000 rw-s 1d7c08000 00:05 3563      /dev/dri/card0
b11b0000-b11b8000 rw-s 1d7c00000 00:05 3563      /dev/dri/card0
b11b8000-b11c0000 rw-s 1d7c5d000 00:05 3563      /dev/dri/card0
b11c0000-b11c8000 rw-s 1d7c55000 00:05 3563      /dev/dri/card0
b11c8000-b11d0000 rw-s 1d7c4d000 00:05 3563      /dev/dri/card0
b11d0000-b11d8000 rw-s 1d7c45000 00:05 3563      /dev/dri/card0
b11d8000-b11e0000 rw-s 1d7c3d000 00:05 3563      /dev/dri/card0
b11e0000-b11e8000 rw-s 1d7c35000 00:05 3563      /dev/dri/card0
b11e8000-b11f0000 rw-s 1d7bf7000 00:05 3563      /dev/dri/card0
b11f0000-b11f8000 rw-s 1d7bef000 00:05 3563      /dev/dri/card0
b11f8000-b1200000 rw-s 1d7be7000 00:05 3563      /dev/dri/card0
b1200000-b1208000 rw-s 1d7bdf000 00:05 3563      /dev/dri/card0
b1208000-b1210000 rw-s 1d7bd7000 00:05 3563      /dev/dri/card0
b1210000-b1218000 rw-s 1d7bcf000 00:05 3563      /dev/dri/card0
b1218000-b1220000 rw-s 1d7bc7000 00:05 3563      /dev/dri/card0
b1220000-b1228000 rw-s 1d7bbf000 00:05 3563      /dev/dri/card0
b1228000-b1230000 rw-s 1d7bb7000 00:05 3563      /dev/dri/card0
b1230000-b1238000 rw-s 1d7baf000 00:05 3563      /dev/dri/card0
b1238000-b1240000 rw-s 1d7ba7000 00:05 3563      /dev/dri/card0
b1240000-b1248000 rw-s 1d7b9f000 00:05 3563      /dev/dri/card0
b1248000-b1250000 rw-s 1d7b97000 00:05 3563      /dev/dri/card0
b1250000-b1258000 rw-s 1d7b8f000 00:05 3563      /dev/dri/card0
b1258000-b1260000 rw-s 1d7b69000 00:05 3563      /dev/dri/card0
b1260000-b1268000 rw-s 1d7b61000 00:05 3563      /dev/dri/card0
b1268000-b1270000 rw-s 1d7b59000 00:05 3563      /dev/dri/card0
b1270000-b1278000 rw-s 1d7b51000 00:05 3563      /dev/dri/card0
b1278000-b1280000 rw-s 1d7b49000 00:05 3563      /dev/dri/card0
b1280000-b1288000 rw-s 1d7b41000 00:05 3563      /dev/dri/card0
b1288000-b1290000 rw-s 1d7b87000 00:05 3563      /dev/dri/card0
b1290000-b1298000 rw-s 1d7b7f000 00:05 3563      /dev/dri/card0
b1298000-b12a0000 rw-s 1d7b77000 00:05 3563      /dev/dri/card0
b12a0000-b12a8000 rw-s 1d7b39000 00:05 3563      /dev/dri/card0
b12a8000-b12b0000 rw-s 1d7b31000 00:05 3563      /dev/dri/card0
b12b0000-b12b8000 rw-s 1d7b29000 00:05 3563      /dev/dri/card0
b12b8000-b12c0000 rw-s 1d7b21000 00:05 3563      /dev/dri/card0
b12c0000-b12c8000 rw-s 1d7b19000 00:05 3563      /dev/dri/card0
b12c8000-b12d0000 rw-s 1d7b11000 00:05 3563      /dev/dri/card0
b12d0000-b12d8000 rw-s 1d7b09000 00:05 3563      /dev/dri/card0
b12d8000-b12e0000 rw-s 1d7b01000 00:05 3563      /dev/dri/card0
b12e0000-b12e8000 rw-s 1d7af9000 00:05 3563      /dev/dri/card0
b12e8000-b12f0000 rw-s 1d7af1000 00:05 3563      /dev/dri/card0
b12f0000-b12f8000 rw-s 1d7ae9000 00:05 3563      /dev/dri/card0
b12f8000-b1300000 rw-s 1d7ae1000 00:05 3563      /dev/dri/card0
b1300000-b1308000 rw-s 1d7ad9000 00:05 3563      /dev/dri/card0
b1308000-b1310000 rw-s 1d7ad1000 00:05 3563      /dev/dri/card0
b1310000-b1318000 rw-s 1d7ac9000 00:05 3563      /dev/dri/card0
b1318000-b1320000 rw-s 1d7ac1000 00:05 3563      /dev/dri/card0
b1320000-b1328000 rw-s 1d7ab9000 00:05 3563      /dev/dri/card0
b1328000-b1330000 rw-s 1d7ab1000 00:05 3563      /dev/dri/card0
b1330000-b1338000 rw-s 1d7aa9000 00:05 3563      /dev/dri/card0
b1338000-b1340000 rw-s 1d7aa1000 00:05 3563      /dev/dri/card0
b1340000-b1348000 rw-s 1d7a99000 00:05 3563      /dev/dri/card0
b1348000-b1350000 rw-s 1d7a91000 00:05 3563      /dev/dri/card0
b1350000-b1358000 rw-s 1d7a89000 00:05 3563      /dev/dri/card0
b1358000-b1360000 rw-s 1d7a81000 00:05 3563      /dev/dri/card0
b1360000-b1368000 rw-s 1d7a79000 00:05 3563      /dev/dri/card0
b1368000-b1370000 rw-s 1d7a71000 00:05 3563      /dev/dri/card0
b1370000-b1378000 rw-s 1d7a69000 00:05 3563      /dev/dri/card0
b1378000-b1380000 rw-s 1d7a61000 00:05 3563      /dev/dri/card0
b1380000-b1388000 rw-s 1d7a59000 00:05 3563      /dev/dri/card0
b1388000-b1390000 rw-s 1d7a51000 00:05 3563      /dev/dri/card0
b1390000-b1398000 rw-s 1d7a49000 00:05 3563      /dev/dri/card0
b1398000-b13a0000 rw-s 1d7a41000 00:05 3563      /dev/dri/card0
b13a0000-b13a8000 rw-s 1d7a39000 00:05 3563      /dev/dri/card0
b13a8000-b13b0000 rw-s 1d7a31000 00:05 3563      /dev/dri/card0
b13b0000-b13b8000 rw-s 1d7a29000 00:05 3563      /dev/dri/card0
b13b8000-b13c0000 rw-s 1d7a21000 00:05 3563      /dev/dri/card0
b13c0000-b13c8000 rw-s 1d7a19000 00:05 3563      /dev/dri/card0
b13c8000-b13d0000 rw-s 1d79e4000 00:05 3563      /dev/dri/card0
b13d0000-b13d8000 rw-s 1d79dc000 00:05 3563      /dev/dri/card0
b13d8000-b13e0000 rw-s 1d79d4000 00:05 3563      /dev/dri/card0
b13e0000-b13e8000 rw-s 1d79cc000 00:05 3563      /dev/dri/card0
b13e8000-b13f0000 rw-s 1d79c4000 00:05 3563      /dev/dri/card0
b13f0000-b13f8000 rw-s 1d79bc000 00:05 3563      /dev/dri/card0
b13f8000-b1400000 rw-s 1d7a11000 00:05 3563      /dev/dri/card0
b1400000-b1408000 rw-s 1d7a04000 00:05 3563      /dev/dri/card0
b1408000-b1410000 rw-s 1d79fc000 00:05 3563      /dev/dri/card0
b1410000-b1418000 rw-s 1d79f4000 00:05 3563      /dev/dri/card0
b1418000-b1420000 rw-s 1d79ec000 00:05 3563      /dev/dri/card0
b1420000-b1428000 rw-s 1d79b3000 00:05 3563      /dev/dri/card0
b1428000-b1430000 rw-s 1d79ab000 00:05 3563      /dev/dri/card0
b1430000-b1438000 rw-s 1d79a3000 00:05 3563      /dev/dri/card0
b1438000-b1440000 rw-s 1d799b000 00:05 3563      /dev/dri/card0
b1440000-b1448000 rw-s 1d7993000 00:05 3563      /dev/dri/card0
b1448000-b1450000 rw-s 1d798b000 00:05 3563      /dev/dri/card0
b1450000-b1458000 rw-s 1d7983000 00:05 3563      /dev/dri/card0
b1458000-b1460000 rw-s 1d7973000 00:05 3563      /dev/dri/card0
b1460000-b1468000 rw-s 1d796b000 00:05 3563      /dev/dri/card0
b1468000-b1470000 rw-s 1d7963000 00:05 3563      /dev/dri/card0
b1470000-b1478000 rw-s 1d795b000 00:05 3563      /dev/dri/card0
b1478000-b1480000 rw-s 1d7953000 00:05 3563      /dev/dri/card0
b1480000-b1488000 rw-s 1d794b000 00:05 3563      /dev/dri/card0
b1488000-b1490000 rw-s 1d7943000 00:05 3563      /dev/dri/card0
b1490000-b1498000 rw-s 1d793b000 00:05 3563      /dev/dri/card0
b1498000-b14a0000 rw-s 1d7933000 00:05 3563      /dev/dri/card0
b14a0000-b14a8000 rw-s 1d7914000 00:05 3563      /dev/dri/card0
b14a8000-b14b0000 rw-s 1d790c000 00:05 3563      /dev/dri/card0
b14b0000-b14b8000 rw-s 1d7902000 00:05 3563      /dev/dri/card0
b14b8000-b14c0000 rw-s 1d78fa000 00:05 3563      /dev/dri/card0
b14c0000-b14c8000 rw-s 1d78f2000 00:05 3563      /dev/dri/card0
b14c8000-b14d0000 rw-s 1d792b000 00:05 3563      /dev/dri/card0
b14d0000-b14d8000 rw-s 1d7923000 00:05 3563      /dev/dri/card0
b14d8000-b14e0000 rw-s 1d78e5000 00:05 3563      /dev/dri/card0
b14e0000-b14e8000 rw-s 1d78dd000 00:05 3563      /dev/dri/card0
b14e8000-b14f0000 rw-s 1d78d5000 00:05 3563      /dev/dri/card0
b14f0000-b14f8000 rw-s 1d78cd000 00:05 3563      /dev/dri/card0
b14f8000-b1500000 rw-s 1d78c5000 00:05 3563      /dev/dri/card0
b1500000-b1508000 rw-s 1d78bd000 00:05 3563      /dev/dri/card0
b1508000-b1510000 rw-s 1d78b5000 00:05 3563      /dev/dri/card0
b1510000-b1518000 rw-s 1d797b000 00:05 3563      /dev/dri/card0
b1518000-b1520000 rw-s 1d78a6000 00:05 3563      /dev/dri/card0
b1520000-b1528000 rw-s 1d789e000 00:05 3563      /dev/dri/card0
b1528000-b1530000 rw-s 1d7895000 00:05 3563      /dev/dri/card0
b1530000-b1538000 rw-s 1d788d000 00:05 3563      /dev/dri/card0
b1538000-b1540000 rw-s 1d7885000 00:05 3563      /dev/dri/card0
b1540000-b1548000 rw-s 1d787d000 00:05 3563      /dev/dri/card0
b1548000-b1550000 rw-s 1d7875000 00:05 3563      /dev/dri/card0
b1550000-b1558000 rw-s 1d786d000 00:05 3563      /dev/dri/card0
b1558000-b1560000 rw-s 1d7865000 00:05 3563      /dev/dri/card0
b1560000-b1568000 rw-s 1d785d000 00:05 3563      /dev/dri/card0
b1568000-b1570000 rw-s 1d7855000 00:05 3563      /dev/dri/card0
b1570000-b1578000 rw-s 1d784d000 00:05 3563      /dev/dri/card0
b1578000-b1580000 rw-s 1d7845000 00:05 3563      /dev/dri/card0
b1580000-b1588000 rw-s 1d783d000 00:05 3563      /dev/dri/card0
b1588000-b1590000 rw-s 1d7835000 00:05 3563      /dev/dri/card0
b1590000-b1598000 rw-s 1d782d000 00:05 3563      /dev/dri/card0
b1598000-b15a0000 rw-s 1d7825000 00:05 3563      /dev/dri/card0
b15a0000-b15a8000 rw-s 1d7719000 00:05 3563      /dev/dri/card0
b15a8000-b15b0000 rw-s 1d7711000 00:05 3563      /dev/dri/card0
b15b0000-b15b8000 rw-s 1d7709000 00:05 3563      /dev/dri/card0
b15b8000-b15c0000 rw-s 1d7701000 00:05 3563      /dev/dri/card0
b15c0000-b15c8000 rw-s 1d77eb000 00:05 3563      /dev/dri/card0
b15c8000-b15d0000 rw-s 1d77e3000 00:05 3563      /dev/dri/card0
b15d0000-b15d8000 rw-s 1d781d000 00:05 3563      /dev/dri/card0
b15d8000-b15e0000 rw-s 1d7813000 00:05 3563      /dev/dri/card0
b15e0000-b15e8000 rw-s 1d780b000 00:05 3563      /dev/dri/card0
b15e8000-b15f0000 rw-s 1d7803000 00:05 3563      /dev/dri/card0
b15f0000-b15f8000 rw-s 1d77fb000 00:05 3563      /dev/dri/card0
b15f8000-b1600000 rw-s 1d77f3000 00:05 3563      /dev/dri/card0
b1600000-b1608000 rw-s 1d77b7000 00:05 3563      /dev/dri/card0
b1608000-b1610000 rw-s 1d77af000 00:05 3563      /dev/dri/card0
b1610000-b1618000 rw-s 1d77a7000 00:05 3563      /dev/dri/card0
b1618000-b1620000 rw-s 1d779f000 00:05 3563      /dev/dri/card0
b1620000-b1628000 rw-s 1d7797000 00:05 3563      /dev/dri/card0
b1628000-b1630000 rw-s 1d778f000 00:05 3563      /dev/dri/card0
b1630000-b1638000 rw-s 1d7787000 00:05 3563      /dev/dri/card0
b1638000-b1640000 rw-s 1d777f000 00:05 3563      /dev/dri/card0
b1640000-b1648000 rw-s 1d7777000 00:05 3563      /dev/dri/card0
b1648000-b1650000 rw-s 1d776f000 00:05 3563      /dev/dri/card0
b1650000-b1658000 rw-s 1d7767000 00:05 3563      /dev/dri/card0
b1658000-b1660000 rw-s 1d775f000 00:05 3563      /dev/dri/card0
b1660000-b1668000 rw-s 1d7757000 00:05 3563      /dev/dri/card0
b1668000-b1670000 rw-s 1d774f000 00:05 3563      /dev/dri/card0
b1670000-b1678000 rw-s 1d7725000 00:05 3563      /dev/dri/card0
b1678000-b1680000 rw-s 1d77db000 00:05 3563      /dev/dri/card0
b1680000-b1688000 rw-s 1d77d3000 00:05 3563      /dev/dri/card0
b1688000-b1690000 rw-s 1d77c7000 00:05 3563      /dev/dri/card0
b1690000-b1698000 rw-s 1d77bf000 00:05 3563      /dev/dri/card0
b1698000-b16a0000 rw-s 1d76f9000 00:05 3563      /dev/dri/card0
b16a0000-b16a8000 rw-s 1d7747000 00:05 3563      /dev/dri/card0
b16a8000-b16b0000 rw-s 1d773f000 00:05 3563      /dev/dri/card0
b16b0000-b16b8000 rw-s 1d7737000 00:05 3563      /dev/dri/card0
b16b8000-b16c0000 rw-s 1d772f000 00:05 3563      /dev/dri/card0
b16c0000-b16c8000 rw-s 1d76f1000 00:05 3563      /dev/dri/card0
b16c8000-b16d0000 rw-s 1d76e9000 00:05 3563      /dev/dri/card0
b16d0000-b16d8000 rw-s 1d76e1000 00:05 3563      /dev/dri/card0
b16d8000-b16e0000 rw-s 1d76d9000 00:05 3563      /dev/dri/card0
b16e0000-b16e8000 rw-s 1d76d1000 00:05 3563      /dev/dri/card0
b16e8000-b16f0000 rw-s 1d76c9000 00:05 3563      /dev/dri/card0
b16f0000-b16f8000 rw-s 1d76c1000 00:05 3563      /dev/dri/card0
b16f8000-b1700000 rw-s 1d76b9000 00:05 3563      /dev/dri/card0
b1700000-b1708000 rw-s 1d76b1000 00:05 3563      /dev/dri/card0
b1708000-b1710000 rw-s 1d76a9000 00:05 3563      /dev/dri/card0
b1710000-b1718000 rw-s 1d7673000 00:05 3563      /dev/dri/card0
b1718000-b1720000 rw-s 1d766b000 00:05 3563      /dev/dri/card0
b1720000-b1728000 rw-s 1d7663000 00:05 3563      /dev/dri/card0
b1728000-b1730000 rw-s 1d765b000 00:05 3563      /dev/dri/card0
b1730000-b1738000 rw-s 1d7653000 00:05 3563      /dev/dri/card0
b1738000-b1740000 rw-s 1d764b000 00:05 3563      /dev/dri/card0
b1740000-b1748000 rw-s 1d76a1000 00:05 3563      /dev/dri/card0
b1748000-b1750000 rw-s 1d7699000 00:05 3563      /dev/dri/card0
b1750000-b1758000 rw-s 1d7691000 00:05 3563      /dev/dri/card0
b1758000-b1760000 rw-s 1d7689000 00:05 3563      /dev/dri/card0
b1760000-b1768000 rw-s 1d7681000 00:05 3563      /dev/dri/card0
b1768000-b1770000 rw-s 1d7643000 00:05 3563      /dev/dri/card0
b1770000-b1778000 rw-s 1d763b000 00:05 3563      /dev/dri/card0
b1778000-b1780000 rw-s 1d7633000 00:05 3563      /dev/dri/card0
b1780000-b1788000 rw-s 1d762b000 00:05 3563      /dev/dri/card0
b1788000-b1790000 rw-s 1d7623000 00:05 3563      /dev/dri/card0
b1790000-b1798000 rw-s 1d761b000 00:05 3563      /dev/dri/card0
b1798000-b17a0000 rw-s 1d7613000 00:05 3563      /dev/dri/card0
b17a0000-b17a8000 rw-s 1d75e1000 00:05 3563      /dev/dri/card0
b17a8000-b17b0000 rw-s 1d75d9000 00:05 3563      /dev/dri/card0
b17b0000-b17b8000 rw-s 1d75d1000 00:05 3563      /dev/dri/card0
b17b8000-b17c0000 rw-s 1d75c9000 00:05 3563      /dev/dri/card0
b17c0000-b17c8000 rw-s 1d75bd000 00:05 3563      /dev/dri/card0
b17c8000-b17d0000 rw-s 1d75b5000 00:05 3563      /dev/dri/card0
b17d0000-b17d8000 rw-s 1d760b000 00:05 3563      /dev/dri/card0
b17d8000-b17e0000 rw-s 1d7603000 00:05 3563      /dev/dri/card0
b17e0000-b17e8000 rw-s 1d75fb000 00:05 3563      /dev/dri/card0
b17e8000-b17f0000 rw-s 1d75f3000 00:05 3563      /dev/dri/card0
b17f0000-b17f8000 rw-s 1d75eb000 00:05 3563      /dev/dri/card0
b17f8000-b1800000 rw-s 1d75a1000 00:05 3563      /dev/dri/card0
b1800000-b1829000 rw-p 00000000 00:00 0 
b1829000-b1900000 ---p 00000000 00:00 0 
b1900000-b1908000 rw-s 1d7599000 00:05 3563      /dev/dri/card0
b1908000-b1910000 rw-s 1d7591000 00:05 3563      /dev/dri/card0
b1910000-b1918000 rw-s 1d7589000 00:05 3563      /dev/dri/card0
b1918000-b1920000 rw-s 1d7581000 00:05 3563      /dev/dri/card0
b1920000-b1928000 rw-s 1d7578000 00:05 3563      /dev/dri/card0
b1928000-b1930000 rw-s 1d75ad000 00:05 3563      /dev/dri/card0
b1930000-b1938000 rw-s 1d756f000 00:05 3563      /dev/dri/card0
b1938000-b1940000 rw-s 1d5b71000 00:05 3563      /dev/dri/card0
b1940000-b1948000 rw-s 1d7567000 00:05 3563      /dev/dri/card0
b1948000-b1950000 rw-s 1d755f000 00:05 3563      /dev/dri/card0
b1950000-b1958000 rw-s 1d7557000 00:05 3563      /dev/dri/card0
b1958000-b1960000 rw-s 1d754f000 00:05 3563      /dev/dri/card0
b1960000-b1968000 rw-s 1d7547000 00:05 3563      /dev/dri/card0
b1968000-b1970000 rw-s 1d5b69000 00:05 3563      /dev/dri/card0
b1970000-b1978000 rw-s 1d7513000 00:05 3563      /dev/dri/card0
b1978000-b1980000 rw-s 1d750b000 00:05 3563      /dev/dri/card0
b1980000-b1988000 rw-s 1d7503000 00:05 3563      /dev/dri/card0
b1988000-b1990000 rw-s 1d74f2000 00:05 3563      /dev/dri/card0
b1990000-b1998000 rw-s 1d74e9000 00:05 3563      /dev/dri/card0
b1998000-b19a0000 rw-s 1d753f000 00:05 3563      /dev/dri/card0
b19a0000-b19a8000 rw-s 1d7537000 00:05 3563      /dev/dri/card0
b19a8000-b19b0000 rw-s 1d752f000 00:05 3563      /dev/dri/card0
b19b0000-b19b8000 rw-s 1d7527000 00:05 3563      /dev/dri/card0
b19b8000-b19c0000 rw-s 1d751f000 00:05 3563      /dev/dri/card0
b19c0000-b19c8000 rw-s 1d74d9000 00:05 3563      /dev/dri/card0
b19c8000-b19d0000 rw-s 1d74d1000 00:05 3563      /dev/dri/card0
b19d0000-b19d8000 rw-s 1d74c9000 00:05 3563      /dev/dri/card0
b19d8000-b19e0000 rw-s 1d74c1000 00:05 3563      /dev/dri/card0
b19e0000-b19e8000 rw-s 1d74b9000 00:05 3563      /dev/dri/card0
b19e8000-b19f0000 rw-s 1d74ab000 00:05 3563      /dev/dri/card0
b19f0000-b19f8000 rw-s 1d74e1000 00:05 3563      /dev/dri/card0
b19f8000-b1a00000 rw-s 1d74a3000 00:05 3563      /dev/dri/card0
b1a00000-b1afa000 rw-p 00000000 00:00 0 
b1afa000-b1b00000 ---p 00000000 00:00 0 
b1b07000-b1b0f000 rw-s 1d749b000 00:05 3563      /dev/dri/card0
b1b0f000-b1b17000 rw-s 1d7493000 00:05 3563      /dev/dri/card0
b1b17000-b1b1f000 rw-s 1d748b000 00:05 3563      /dev/dri/card0
b1b1f000-b1b27000 rw-s 1d7483000 00:05 3563      /dev/dri/card0
b1b27000-b1b2f000 rw-s 1d747b000 00:05 3563      /dev/dri/card0
b1b2f000-b1b37000 rw-s 1d7473000 00:05 3563      /dev/dri/card0
b1b37000-b1b3f000 rw-s 1d746b000 00:05 3563      /dev/dri/card0
b1b3f000-b1b47000 rw-s 1d7463000 00:05 3563      /dev/dri/card0
b1b47000-b1b4f000 rw-s 1d745b000 00:05 3563      /dev/dri/card0
b1b4f000-b1b57000 rw-s 1d7453000 00:05 3563      /dev/dri/card0
b1b57000-b1b5f000 rw-s 1d7443000 00:05 3563      /dev/dri/card0
b1b5f000-b1b67000 rw-s 1d743b000 00:05 3563      /dev/dri/card0
b1b67000-b1b6f000 rw-s 1d7433000 00:05 3563      /dev/dri/card0
b1b6f000-b1b77000 rw-s 1d742b000 00:05 3563      /dev/dri/card0
b1b77000-b1b7f000 rw-s 1d7423000 00:05 3563      /dev/dri/card0
b1b7f000-b1b87000 rw-s 1d741b000 00:05 3563      /dev/dri/card0
b1b87000-b1b8f000 rw-s 1d7413000 00:05 3563      /dev/dri/card0
b1b8f000-b1b97000 rw-s 1d740b000 00:05 3563      /dev/dri/card0
b1b97000-b1b9f000 rw-s 1d7403000 00:05 3563      /dev/dri/card0
b1b9f000-b1ba7000 rw-s 1d73fb000 00:05 3563      /dev/dri/card0
b1ba7000-b1baf000 rw-s 1d73f3000 00:05 3563      /dev/dri/card0
b1baf000-b1bb7000 rw-s 1d73eb000 00:05 3563      /dev/dri/card0
b1bb7000-b1bbf000 rw-s 1d73e3000 00:05 3563      /dev/dri/card0
b1bbf000-b1bc7000 rw-s 1d73db000 00:05 3563      /dev/dri/card0
b1bc7000-b1bcf000 rw-s 1d73d3000 00:05 3563      /dev/dri/card0
b1bcf000-b1bd7000 rw-s 1d73cb000 00:05 3563      /dev/dri/card0
b1bd7000-b1bdf000 rw-s 1d73c3000 00:05 3563      /dev/dri/card0
b1bdf000-b1be7000 rw-s 1d73bb000 00:05 3563      /dev/dri/card0
b1be7000-b1bef000 rw-s 1d73b3000 00:05 3563      /dev/dri/card0
b1bef000-b1bf7000 rw-s 1d73ab000 00:05 3563      /dev/dri/card0
b1bf7000-b1bff000 rw-s 1d73a3000 00:05 3563      /dev/dri/card0
b1bff000-b1c07000 rw-s 1d739b000 00:05 3563      /dev/dri/card0
b1c07000-b1c0f000 rw-s 1d7393000 00:05 3563      /dev/dri/card0
b1c0f000-b1c17000 rw-s 1d738b000 00:05 3563      /dev/dri/card0
b1c17000-b1c1f000 rw-s 1d7383000 00:05 3563      /dev/dri/card0
b1c1f000-b1c27000 rw-s 1d737b000 00:05 3563      /dev/dri/card0
b1c27000-b1c2f000 rw-s 1d7373000 00:05 3563      /dev/dri/card0
b1c2f000-b1c37000 rw-s 1d736b000 00:05 3563      /dev/dri/card0
b1c37000-b1c3f000 rw-s 1d7363000 00:05 3563      /dev/dri/card0
b1c3f000-b1c47000 rw-s 1d735b000 00:05 3563      /dev/dri/card0
b1c47000-b1c4f000 rw-s 1d7353000 00:05 3563      /dev/dri/card0
b1c4f000-b1c57000 rw-s 1d734b000 00:05 3563      /dev/dri/card0
b1c57000-b1c5f000 rw-s 1d7343000 00:05 3563      /dev/dri/card0
b1c5f000-b1c67000 rw-s 1d733b000 00:05 3563      /dev/dri/card0
b1c67000-b1c6f000 rw-s 1d7333000 00:05 3563      /dev/dri/card0
b1c6f000-b1c77000 rw-s 1d732b000 00:05 3563      /dev/dri/card0
b1c77000-b1c7f000 rw-s 1d7323000 00:05 3563      /dev/dri/card0
b1c7f000-b1c87000 rw-s 1d731b000 00:05 3563      /dev/dri/card0
b1c87000-b1c8f000 rw-s 1d7313000 00:05 3563      /dev/dri/card0
b1c8f000-b1c97000 rw-s 1d730b000 00:05 3563      /dev/dri/card0
b1c97000-b1c9f000 rw-s 1d7303000 00:05 3563      /dev/dri/card0
b1c9f000-b1ca7000 rw-s 1d72fb000 00:05 3563      /dev/dri/card0
b1ca7000-b1caf000 rw-s 1d72a2000 00:05 3563      /dev/dri/card0
b1caf000-b1cb7000 rw-s 1d729a000 00:05 3563      /dev/dri/card0
b1cb7000-b1cbf000 rw-s 1d728f000 00:05 3563      /dev/dri/card0
b1cbf000-b1cc7000 rw-s 1d7287000 00:05 3563      /dev/dri/card0
b1cc7000-b1ccf000 rw-s 1d727d000 00:05 3563      /dev/dri/card0
b1ccf000-b1cd7000 rw-s 1d7275000 00:05 3563      /dev/dri/card0
b1cd7000-b1cdf000 rw-s 1d72f3000 00:05 3563      /dev/dri/card0
b1cdf000-b1ce7000 rw-s 1d72eb000 00:05 3563      /dev/dri/card0
b1ce7000-b1cef000 rw-s 1d72e3000 00:05 3563      /dev/dri/card0
b1cef000-b1cf7000 rw-s 1d72db000 00:05 3563      /dev/dri/card0
b1cf7000-b1cff000 rw-s 1d72d3000 00:05 3563      /dev/dri/card0
b1cff000-b1d07000 rw-s 1d72cb000 00:05 3563      /dev/dri/card0
b1d07000-b1d0f000 rw-s 1d72c3000 00:05 3563      /dev/dri/card0
b1d0f000-b1d17000 rw-s 1d72bb000 00:05 3563      /dev/dri/card0
b1d17000-b1d1f000 rw-s 1d72b3000 00:05 3563      /dev/dri/card0
b1d1f000-b1d27000 rw-s 1d72ab000 00:05 3563      /dev/dri/card0
b1d27000-b1d2f000 rw-s 1d726d000 00:05 3563      /dev/dri/card0
b1d2f000-b1d37000 rw-s 1d7265000 00:05 3563      /dev/dri/card0
b1d37000-b1d3f000 rw-s 1d725d000 00:05 3563      /dev/dri/card0
b1d3f000-b1d47000 rw-s 1d7255000 00:05 3563      /dev/dri/card0
b1d47000-b1d4f000 rw-s 1d724d000 00:05 3563      /dev/dri/card0
b1d4f000-b1d57000 rw-s 1d7245000 00:05 3563      /dev/dri/card0
b1d57000-b1d5f000 rw-s 1d723d000 00:05 3563      /dev/dri/card0
b1d5f000-b1d67000 rw-s 1d7235000 00:05 3563      /dev/dri/card0
b1d67000-b1d6f000 rw-s 1d722d000 00:05 3563      /dev/dri/card0
b1d6f000-b1d77000 rw-s 1d7225000 00:05 3563      /dev/dri/card0
b1d77000-b1d7f000 rw-s 1d721d000 00:05 3563      /dev/dri/card0
b1d7f000-b1d87000 rw-s 1d7215000 00:05 3563      /dev/dri/card0
b1d87000-b1d8f000 rw-s 1d720d000 00:05 3563      /dev/dri/card0
b1d8f000-b1d97000 rw-s 1d7205000 00:05 3563      /dev/dri/card0
b1d97000-b1d9f000 rw-s 1d71fd000 00:05 3563      /dev/dri/card0
b1d9f000-b1da7000 rw-s 1d71f5000 00:05 3563      /dev/dri/card0
b1da7000-b1daf000 rw-s 1d71ed000 00:05 3563      /dev/dri/card0
b1daf000-b1db7000 rw-s 1d71e5000 00:05 3563      /dev/dri/card0
b1db7000-b1dbf000 rw-s 1d71dd000 00:05 3563      /dev/dri/card0
b1dbf000-b1dc7000 rw-s 1d71d5000 00:05 3563      /dev/dri/card0
b1dc7000-b1dcf000 rw-s 1d71cd000 00:05 3563      /dev/dri/card0
b1dcf000-b1dd7000 rw-s 1d71c5000 00:05 3563      /dev/dri/card0
b1dd7000-b1ddf000 rw-s 1d71bd000 00:05 3563      /dev/dri/card0
b1ddf000-b1de7000 rw-s 1d71b5000 00:05 3563      /dev/dri/card0
b1de7000-b1def000 rw-s 1d71ad000 00:05 3563      /dev/dri/card0
b1def000-b1df7000 rw-s 1d71a5000 00:05 3563      /dev/dri/card0
b1df7000-b1dff000 rw-s 1d719d000 00:05 3563      /dev/dri/card0
b1dff000-b1e07000 rw-s 1d7195000 00:05 3563      /dev/dri/card0
b1e07000-b1e0f000 rw-s 1d718d000 00:05 3563      /dev/dri/card0
b1e0f000-b1e17000 rw-s 1d7185000 00:05 3563      /dev/dri/card0
b1e17000-b1e1f000 rw-s 1d717d000 00:05 3563      /dev/dri/card0
b1e1f000-b1e27000 rw-s 1d7175000 00:05 3563      /dev/dri/card0
b1e27000-b1e2f000 rw-s 1d716d000 00:05 3563      /dev/dri/card0
b1e2f000-b1e37000 rw-s 1d7165000 00:05 3563      /dev/dri/card0
b1e37000-b1e3f000 rw-s 1d715d000 00:05 3563      /dev/dri/card0
b1e3f000-b1e47000 rw-s 1d7155000 00:05 3563      /dev/dri/card0
b1e47000-b1e4f000 rw-s 1d714d000 00:05 3563      /dev/dri/card0
b1e4f000-b1e57000 rw-s 1d7145000 00:05 3563      /dev/dri/card0
b1e57000-b1e5f000 rw-s 1d713d000 00:05 3563      /dev/dri/card0
b1e5f000-b1e67000 rw-s 1d7135000 00:05 3563      /dev/dri/card0
b1e67000-b1e6f000 rw-s 1d712d000 00:05 3563      /dev/dri/card0
b1e6f000-b1e77000 rw-s 1d7125000 00:05 3563      /dev/dri/card0
b1e77000-b1e7f000 rw-s 1d711d000 00:05 3563      /dev/dri/card0
b1e7f000-b1e87000 rw-s 1d7115000 00:05 3563      /dev/dri/card0
b1e87000-b1e8f000 rw-s 1d710d000 00:05 3563      /dev/dri/card0
b1e8f000-b1e97000 rw-s 1d7105000 00:05 3563      /dev/dri/card0
b1e97000-b1e9f000 rw-s 1d70fd000 00:05 3563      /dev/dri/card0
b1e9f000-b1ea7000 rw-s 1d70f5000 00:05 3563      /dev/dri/card0
b1ea7000-b1eaf000 rw-s 1d6d73000 00:05 3563      /dev/dri/card0
b1eaf000-b1eb7000 rw-s 1d70ed000 00:05 3563      /dev/dri/card0
b1eb7000-b1ebf000 rw-s 1d70e5000 00:05 3563      /dev/dri/card0
b1ebf000-b1ec7000 rw-s 1d70dd000 00:05 3563      /dev/dri/card0
b1ec7000-b1ecf000 rw-s 1d70d5000 00:05 3563      /dev/dri/card0
b1ecf000-b1ed7000 rw-s 1d70cd000 00:05 3563      /dev/dri/card0
b1ed7000-b1edf000 rw-s 1d70c5000 00:05 3563      /dev/dri/card0
b1edf000-b1ee7000 rw-s 1d70b5000 00:05 3563      /dev/dri/card0
b1ee7000-b1eef000 rw-s 1d70ad000 00:05 3563      /dev/dri/card0
b1eef000-b1ef7000 rw-s 1d70a5000 00:05 3563      /dev/dri/card0
b1ef7000-b1eff000 rw-s 1d709d000 00:05 3563      /dev/dri/card0
b1eff000-b1f07000 rw-s 1d7095000 00:05 3563      /dev/dri/card0
b1f07000-b1f0f000 rw-s 1d708d000 00:05 3563      /dev/dri/card0
b1f0f000-b1f17000 rw-s 1d7085000 00:05 3563      /dev/dri/card0
b1f17000-b1f1f000 rw-s 1d707d000 00:05 3563      /dev/dri/card0
b1f1f000-b1f27000 rw-s 1d7075000 00:05 3563      /dev/dri/card0
b1f27000-b1f2f000 rw-s 1d706d000 00:05 3563      /dev/dri/card0
b1f2f000-b1f37000 rw-s 1d7065000 00:05 3563      /dev/dri/card0
b1f37000-b1f3f000 rw-s 1d705d000 00:05 3563      /dev/dri/card0
b1f3f000-b1f47000 rw-s 1d7055000 00:05 3563      /dev/dri/card0
b1f47000-b1f4f000 rw-s 1d704d000 00:05 3563      /dev/dri/card0
b1f4f000-b1f57000 rw-s 1d7045000 00:05 3563      /dev/dri/card0
b1f57000-b1f5f000 rw-s 1d703d000 00:05 3563      /dev/dri/card0
b1f5f000-b1f67000 rw-s 1d7035000 00:05 3563      /dev/dri/card0
b1f67000-b1f6f000 rw-s 1d702d000 00:05 3563      /dev/dri/card0
b1f6f000-b1f77000 rw-s 1d7025000 00:05 3563      /dev/dri/card0
b1f77000-b1f7f000 rw-s 1d701d000 00:05 3563      /dev/dri/card0
b1f7f000-b1f87000 rw-s 1d7015000 00:05 3563      /dev/dri/card0
b1f87000-b1f8f000 rw-s 1d700d000 00:05 3563      /dev/dri/card0
b1f8f000-b1f97000 rw-s 1d7005000 00:05 3563      /dev/dri/card0
b1f97000-b1f9f000 rw-s 1d6ffd000 00:05 3563      /dev/dri/card0
b1f9f000-b1fa7000 rw-s 1d6ff5000 00:05 3563      /dev/dri/card0
b1fa7000-b1faf000 rw-s 1d6fed000 00:05 3563      /dev/dri/card0
b1faf000-b1fb7000 rw-s 1d6fe5000 00:05 3563      /dev/dri/card0
b1fb7000-b1fbf000 rw-s 1d6fdd000 00:05 3563      /dev/dri/card0
b1fbf000-b1fc7000 rw-s 1d6fd5000 00:05 3563      /dev/dri/card0
b1fc7000-b1fcf000 rw-s 1d6fcd000 00:05 3563      /dev/dri/card0
b1fcf000-b1fd7000 rw-s 1d6fc5000 00:05 3563      /dev/dri/card0
b1fd7000-b1fdf000 rw-s 1d6fbd000 00:05 3563      /dev/dri/card0
b1fdf000-b1fe7000 rw-s 1d6fb5000 00:05 3563      /dev/dri/card0
b1fe7000-b1fef000 rw-s 1d6fad000 00:05 3563      /dev/dri/card0
b1fef000-b1ff7000 rw-s 1d6fa5000 00:05 3563      /dev/dri/card0
b1ff7000-b1fff000 rw-s 1d6f9d000 00:05 3563      /dev/dri/card0
b1fff000-b2007000 rw-s 1d6f95000 00:05 3563      /dev/dri/card0
b2007000-b200f000 rw-s 1d5f6c000 00:05 3563      /dev/dri/card0
b200f000-b2017000 rw-s 1d5f64000 00:05 3563      /dev/dri/card0
b2017000-b201f000 rw-s 1d6f6f000 00:05 3563      /dev/dri/card0
b201f000-b2027000 rw-s 1d6f67000 00:05 3563      /dev/dri/card0
b2027000-b202f000 rw-s 1d6f5f000 00:05 3563      /dev/dri/card0
b202f000-b2037000 rw-s 1d6f81000 00:05 3563      /dev/dri/card0
b2037000-b203f000 rw-s 1d6f8d000 00:05 3563      /dev/dri/card0
b203f000-b2047000 rw-s 1d6ef9000 00:05 3563      /dev/dri/card0
b2047000-b204f000 rw-s 1d6ef1000 00:05 3563      /dev/dri/card0
b204f000-b2057000 rw-s 1d6ee9000 00:05 3563      /dev/dri/card0
b2057000-b205f000 rw-s 1d6ee1000 00:05 3563      /dev/dri/card0
b205f000-b2067000 rw-s 1d6ed9000 00:05 3563      /dev/dri/card0
b2067000-b206f000 rw-s 1d6ed1000 00:05 3563      /dev/dri/card0
b206f000-b2077000 rw-s 1d6f4f000 00:05 3563      /dev/dri/card0
b2077000-b207f000 rw-s 1d6f47000 00:05 3563      /dev/dri/card0
b207f000-b2087000 rw-s 1d6f3f000 00:05 3563      /dev/dri/card0
b2087000-b208f000 rw-s 1d6f37000 00:05 3563      /dev/dri/card0
b208f000-b2097000 rw-s 1d6f2f000 00:05 3563      /dev/dri/card0
b2097000-b209f000 rw-s 1d6f27000 00:05 3563      /dev/dri/card0
b209f000-b20a7000 rw-s 1d6f1f000 00:05 3563      /dev/dri/card0
b20a7000-b20af000 rw-s 1d6f17000 00:05 3563      /dev/dri/card0
b20af000-b20b7000 rw-s 1d6f0f000 00:05 3563      /dev/dri/card0
b20b7000-b20bf000 rw-s 1d6f07000 00:05 3563      /dev/dri/card0
b20bf000-b20c7000 rw-s 1d6ec9000 00:05 3563      /dev/dri/card0
b20c7000-b20cf000 rw-s 1d6ec1000 00:05 3563      /dev/dri/card0
b20cf000-b20d7000 rw-s 1d6eb9000 00:05 3563      /dev/dri/card0
b20d7000-b20df000 rw-s 1d6eb1000 00:05 3563      /dev/dri/card0
b20df000-b20e7000 rw-s 1d6ea9000 00:05 3563      /dev/dri/card0
b20e7000-b20ef000 rw-s 1d6ea1000 00:05 3563      /dev/dri/card0
b20ef000-b20f7000 rw-s 1d6e99000 00:05 3563      /dev/dri/card0
b20f7000-b20ff000 rw-s 1d6e91000 00:05 3563      /dev/dri/card0
b20ff000-b2107000 rw-s 1d6e89000 00:05 3563      /dev/dri/card0
b2107000-b210f000 rw-s 1d6e81000 00:05 3563      /dev/dri/card0
b210f000-b2117000 rw-s 1d6e79000 00:05 3563      /dev/dri/card0
b2117000-b211f000 rw-s 1d6e71000 00:05 3563      /dev/dri/card0
b211f000-b2127000 rw-s 1d6e69000 00:05 3563      /dev/dri/card0
b2127000-b212f000 rw-s 1d6e61000 00:05 3563      /dev/dri/card0
b212f000-b2137000 rw-s 1d6e59000 00:05 3563      /dev/dri/card0
b2137000-b213f000 rw-s 1d6e51000 00:05 3563      /dev/dri/card0
b213f000-b2147000 rw-s 1d6e49000 00:05 3563      /dev/dri/card0
b2147000-b214f000 rw-s 1d6e41000 00:05 3563      /dev/dri/card0
b214f000-b2157000 rw-s 1d6e39000 00:05 3563      /dev/dri/card0
b2157000-b215f000 rw-s 1d6e31000 00:05 3563      /dev/dri/card0
b215f000-b2167000 rw-s 1d6e29000 00:05 3563      /dev/dri/card0
b2167000-b216f000 rw-s 1d6dfd000 00:05 3563      /dev/dri/card0
b216f000-b2177000 rw-s 1d6df5000 00:05 3563      /dev/dri/card0
b2177000-b217f000 rw-s 1d6ded000 00:05 3563      /dev/dri/card0
b217f000-b2187000 rw-s 1d6de4000 00:05 3563      /dev/dri/card0
b2187000-b218f000 rw-s 1d6ddc000 00:05 3563      /dev/dri/card0
b218f000-b2197000 rw-s 1d6dd4000 00:05 3563      /dev/dri/card0
b2197000-b219f000 rw-s 1d6e21000 00:05 3563      /dev/dri/card0
b219f000-b21a7000 rw-s 1d6e19000 00:05 3563      /dev/dri/card0
b21a7000-b21af000 rw-s 1d6e11000 00:05 3563      /dev/dri/card0
b21af000-b21b7000 rw-s 1d6e09000 00:05 3563      /dev/dri/card0
b21b7000-b21bf000 rw-s 1d6dcb000 00:05 3563      /dev/dri/card0
b21bf000-b21c7000 rw-s 1d6dc3000 00:05 3563      /dev/dri/card0
b21c7000-b21cf000 rw-s 1d6dbb000 00:05 3563      /dev/dri/card0
b21cf000-b21d7000 rw-s 1d6db3000 00:05 3563      /dev/dri/card0
b21d7000-b21df000 rw-s 1d6dab000 00:05 3563      /dev/dri/card0
b21df000-b21e7000 rw-s 1d6da3000 00:05 3563      /dev/dri/card0
b21e7000-b21ef000 rw-s 1d6d9b000 00:05 3563      /dev/dri/card0
b21ef000-b21f7000 rw-s 1d6d93000 00:05 3563      /dev/dri/card0
b21f7000-b21ff000 rw-s 1d6d8b000 00:05 3563      /dev/dri/card0
b21ff000-b2207000 rw-s 1d6d83000 00:05 3563      /dev/dri/card0
b2207000-b220f000 rw-s 1d6d7b000 00:05 3563      /dev/dri/card0
b220f000-b2217000 rw-s 1d6d00000 00:05 3563      /dev/dri/card0
b2217000-b221f000 rw-s 1d6cf8000 00:05 3563      /dev/dri/card0
b221f000-b2227000 rw-s 1d6cf0000 00:05 3563      /dev/dri/card0
b2227000-b222f000 rw-s 1d6ce8000 00:05 3563      /dev/dri/card0
b222f000-b2237000 rw-s 1d6ce0000 00:05 3563      /dev/dri/card0
b2237000-b223f000 rw-s 1d6cd8000 00:05 3563      /dev/dri/card0
b223f000-b2247000 rw-s 1d70bd000 00:05 3563      /dev/dri/card0
b2247000-b224f000 rw-s 1d6d6b000 00:05 3563      /dev/dri/card0
b224f000-b2257000 rw-s 1d6d63000 00:05 3563      /dev/dri/card0
b2257000-b225f000 rw-s 1d6d5b000 00:05 3563      /dev/dri/card0
b225f000-b2267000 rw-s 1d6d53000 00:05 3563      /dev/dri/card0
b2267000-b226f000 rw-s 1d6d4b000 00:05 3563      /dev/dri/card0
b226f000-b2277000 rw-s 1d6d43000 00:05 3563      /dev/dri/card0
b2277000-b227f000 rw-s 1d6d3b000 00:05 3563      /dev/dri/card0
b227f000-b2287000 rw-s 1d6d33000 00:05 3563      /dev/dri/card0
b2287000-b228f000 rw-s 1d6d2b000 00:05 3563      /dev/dri/card0
b228f000-b2297000 rw-s 1d6d23000 00:05 3563      /dev/dri/card0
b2297000-b229f000 rw-s 1d6d1b000 00:05 3563      /dev/dri/card0
b229f000-b22a7000 rw-s 1d6d13000 00:05 3563      /dev/dri/card0
b22a7000-b22af000 rw-s 1d6d0b000 00:05 3563      /dev/dri/card0
b22af000-b22b7000 rw-s 1d6ccd000 00:05 3563      /dev/dri/card0
b22b7000-b22bf000 rw-s 1d6cc5000 00:05 3563      /dev/dri/card0
b22bf000-b22c7000 rw-s 1d6cbd000 00:05 3563      /dev/dri/card0
b22c7000-b22cf000 rw-s 1d6cb5000 00:05 3563      /dev/dri/card0
b22cf000-b22d7000 rw-s 1d6cad000 00:05 3563      /dev/dri/card0
b22d7000-b22df000 rw-s 1d6ca5000 00:05 3563      /dev/dri/card0
b22df000-b22e7000 rw-s 1d6c9d000 00:05 3563      /dev/dri/card0
b22e7000-b22ef000 rw-s 1d6c95000 00:05 3563      /dev/dri/card0
b22ef000-b22f7000 rw-s 1d6c8d000 00:05 3563      /dev/dri/card0
b22f7000-b22ff000 rw-s 1d6c85000 00:05 3563      /dev/dri/card0
b22ff000-b2307000 rw-s 1d6c7d000 00:05 3563      /dev/dri/card0
b2307000-b230f000 rw-s 1d6c75000 00:05 3563      /dev/dri/card0
b230f000-b2317000 rw-s 1d6c6d000 00:05 3563      /dev/dri/card0
b2317000-b231f000 rw-s 1d6c65000 00:05 3563      /dev/dri/card0
b231f000-b2327000 rw-s 1d6c5d000 00:05 3563      /dev/dri/card0
b2327000-b232f000 rw-s 1d6c55000 00:05 3563      /dev/dri/card0
b232f000-b2337000 rw-s 1d6c4d000 00:05 3563      /dev/dri/card0
b2337000-b233f000 rw-s 1d6c45000 00:05 3563      /dev/dri/card0
b233f000-b2347000 rw-s 1d6c3d000 00:05 3563      /dev/dri/card0
b2347000-b234f000 rw-s 1d6c35000 00:05 3563      /dev/dri/card0
b234f000-b2357000 rw-s 1d6c00000 00:05 3563      /dev/dri/card0
b2357000-b235f000 rw-s 1d6bf8000 00:05 3563      /dev/dri/card0
b235f000-b2367000 rw-s 1d6bf0000 00:05 3563      /dev/dri/card0
b2367000-b236f000 rw-s 1d6be8000 00:05 3563      /dev/dri/card0
b236f000-b2377000 rw-s 1d6be0000 00:05 3563      /dev/dri/card0
b2377000-b237f000 rw-s 1d6bd8000 00:05 3563      /dev/dri/card0
b237f000-b2387000 rw-s 1d6c2d000 00:05 3563      /dev/dri/card0
b2387000-b238f000 rw-s 1d6c25000 00:05 3563      /dev/dri/card0
b238f000-b2397000 rw-s 1d6c1d000 00:05 3563      /dev/dri/card0
b2397000-b239f000 rw-s 1d6c15000 00:05 3563      /dev/dri/card0
b239f000-b23a7000 rw-s 1d6c0d000 00:05 3563      /dev/dri/card0
b23a7000-b23af000 rw-s 1d6bc0000 00:05 3563      /dev/dri/card0
b23af000-b23b7000 rw-s 1d6baa000 00:05 3563      /dev/dri/card0
b23b7000-b23bf000 rw-s 1d6bb8000 00:05 3563      /dev/dri/card0
b23bf000-b23c7000 rw-s 1d6ba2000 00:05 3563      /dev/dri/card0
b23c7000-b23cf000 rw-s 1d6b9a000 00:05 3563      /dev/dri/card0
b23cf000-b23d7000 rw-s 1d6bcf000 00:05 3563      /dev/dri/card0
b23d7000-b23df000 rw-s 1d6b91000 00:05 3563      /dev/dri/card0
b23df000-b23e7000 rw-s 1d6b89000 00:05 3563      /dev/dri/card0
b23e7000-b23ef000 rw-s 1d6b81000 00:05 3563      /dev/dri/card0
b23ef000-b23f7000 rw-s 1d6b79000 00:05 3563      /dev/dri/card0
b23f7000-b23ff000 rw-s 1d6b71000 00:05 3563      /dev/dri/card0
b23ff000-b2407000 rw-s 1d6b69000 00:05 3563      /dev/dri/card0
b2407000-b240f000 rw-s 1d6b4b000 00:05 3563      /dev/dri/card0
b240f000-b2417000 rw-s 1d6b43000 00:05 3563      /dev/dri/card0
b2417000-b241f000 rw-s 1d6b3b000 00:05 3563      /dev/dri/card0
b241f000-b2427000 rw-s 1d6b33000 00:05 3563      /dev/dri/card0
b2427000-b242f000 rw-s 1d6b2b000 00:05 3563      /dev/dri/card0
b242f000-b2437000 rw-s 1d6b23000 00:05 3563      /dev/dri/card0
b2437000-b243f000 rw-s 1d6b61000 00:05 3563      /dev/dri/card0
b243f000-b2447000 rw-s 1d6b59000 00:05 3563      /dev/dri/card0
b2447000-b244f000 rw-s 1d6b09000 00:05 3563      /dev/dri/card0
b244f000-b2457000 rw-s 1d6b01000 00:05 3563      /dev/dri/card0
b2457000-b245f000 rw-s 1d6af9000 00:05 3563      /dev/dri/card0
b245f000-b2467000 rw-s 1d6aed000 00:05 3563      /dev/dri/card0
b2467000-b246f000 rw-s 1d6ae5000 00:05 3563      /dev/dri/card0
b246f000-b2477000 rw-s 1d6add000 00:05 3563      /dev/dri/card0
b2477000-b247f000 rw-s 1d6b1b000 00:05 3563      /dev/dri/card0
b247f000-b2487000 rw-s 1d6b13000 00:05 3563      /dev/dri/card0
b2487000-b248f000 rw-s 1d6aab000 00:05 3563      /dev/dri/card0
b248f000-b2497000 rw-s 1d6aa3000 00:05 3563      /dev/dri/card0
b2497000-b249f000 rw-s 1d6a9b000 00:05 3563      /dev/dri/card0
b249f000-b24a7000 rw-s 1d6a93000 00:05 3563      /dev/dri/card0
b24a7000-b24af000 rw-s 1d6a87000 00:05 3563      /dev/dri/card0
b24af000-b24b7000 rw-s 1d6a7f000 00:05 3563      /dev/dri/card0
b24b7000-b24bf000 rw-s 1d6ad5000 00:05 3563      /dev/dri/card0
b24bf000-b24c7000 rw-s 1d6acd000 00:05 3563      /dev/dri/card0
b24c7000-b24cf000 rw-s 1d6ac5000 00:05 3563      /dev/dri/card0
b24cf000-b24d7000 rw-s 1d6abd000 00:05 3563      /dev/dri/card0
b24d7000-b24df000 rw-s 1d6ab5000 00:05 3563      /dev/dri/card0
b24df000-b24e7000 rw-s 1d6a77000 00:05 3563      /dev/dri/card0
b24e7000-b24ef000 rw-s 1d6a6f000 00:05 3563      /dev/dri/card0
b24ef000-b24f7000 rw-s 1d6a67000 00:05 3563      /dev/dri/card0
b24f7000-b24ff000 rw-s 1d6a5f000 00:05 3563      /dev/dri/card0
b24ff000-b2507000 rw-s 1d6a57000 00:05 3563      /dev/dri/card0
b2507000-b250f000 rw-s 1d6a4f000 00:05 3563      /dev/dri/card0
b250f000-b2517000 rw-s 1d6a32000 00:05 3563      /dev/dri/card0
b2517000-b251f000 rw-s 1d6a2a000 00:05 3563      /dev/dri/card0
b251f000-b2527000 rw-s 1d6a22000 00:05 3563      /dev/dri/card0
b2527000-b252f000 rw-s 1d6a1a000 00:05 3563      /dev/dri/card0
b252f000-b2537000 rw-s 1d6a12000 00:05 3563      /dev/dri/card0
b2537000-b253f000 rw-s 1d6a0a000 00:05 3563      /dev/dri/card0
b253f000-b2547000 rw-s 1d6a47000 00:05 3563      /dev/dri/card0
b2547000-b254f000 rw-s 1d6a3f000 00:05 3563      /dev/dri/card0
b254f000-b2557000 rw-s 1d6998000 00:05 3563      /dev/dri/card0
b2557000-b255f000 rw-s 1d6990000 00:05 3563      /dev/dri/card0
b255f000-b2567000 rw-s 1d6988000 00:05 3563      /dev/dri/card0
b2567000-b256f000 rw-s 1d697b000 00:05 3563      /dev/dri/card0
b256f000-b2577000 rw-s 1d6973000 00:05 3563      /dev/dri/card0
b2577000-b257f000 rw-s 1d696b000 00:05 3563      /dev/dri/card0
b257f000-b2587000 rw-s 1d6a01000 00:05 3563      /dev/dri/card0
b2587000-b258f000 rw-s 1d69f9000 00:05 3563      /dev/dri/card0
b258f000-b2597000 rw-s 1d69f1000 00:05 3563      /dev/dri/card0
b2597000-b259f000 rw-s 1d69e9000 00:05 3563      /dev/dri/card0
b259f000-b25a7000 rw-s 1d69e1000 00:05 3563      /dev/dri/card0
b25a7000-b25af000 rw-s 1d69d9000 00:05 3563      /dev/dri/card0
b25af000-b25b7000 rw-s 1d69d1000 00:05 3563      /dev/dri/card0
b25b7000-b25bf000 rw-s 1d69c9000 00:05 3563      /dev/dri/card0
b25bf000-b25c7000 rw-s 1d69c1000 00:05 3563      /dev/dri/card0
b25c7000-b25cf000 rw-s 1d69b9000 00:05 3563      /dev/dri/card0
b25cf000-b25d7000 rw-s 1d69b1000 00:05 3563      /dev/dri/card0
b25d7000-b25df000 rw-s 1d69a9000 00:05 3563      /dev/dri/card0
b25df000-b25e7000 rw-s 1d69a1000 00:05 3563      /dev/dri/card0
b25e7000-b25ef000 rw-s 1d68ee000 00:05 3563      /dev/dri/card0
b25ef000-b25f7000 rw-s 1d68e6000 00:05 3563      /dev/dri/card0
b25f7000-b25ff000 rw-s 1d68de000 00:05 3563      /dev/dri/card0
b25ff000-b2607000 rw-s 1d68d6000 00:05 3563      /dev/dri/card0
b2607000-b260f000 rw-s 1d68ce000 00:05 3563      /dev/dri/card0
b260f000-b2617000 rw-s 1d68c6000 00:05 3563      /dev/dri/card0
b2617000-b261f000 rw-s 1d6963000 00:05 3563      /dev/dri/card0
b261f000-b2627000 rw-s 1d695b000 00:05 3563      /dev/dri/card0
b2627000-b262f000 rw-s 1d6953000 00:05 3563      /dev/dri/card0
b262f000-b2637000 rw-s 1d694b000 00:05 3563      /dev/dri/card0
b2637000-b263f000 rw-s 1d6943000 00:05 3563      /dev/dri/card0
b263f000-b2647000 rw-s 1d693b000 00:05 3563      /dev/dri/card0
b2647000-b264f000 rw-s 1d6933000 00:05 3563      /dev/dri/card0
b264f000-b2657000 rw-s 1d692b000 00:05 3563      /dev/dri/card0
b2657000-b265f000 rw-s 1d6923000 00:05 3563      /dev/dri/card0
b265f000-b2667000 rw-s 1d691b000 00:05 3563      /dev/dri/card0
b2667000-b266f000 rw-s 1d6913000 00:05 3563      /dev/dri/card0
b266f000-b2677000 rw-s 1d690b000 00:05 3563      /dev/dri/card0
b2677000-b267f000 rw-s 1d6903000 00:05 3563      /dev/dri/card0
b267f000-b2687000 rw-s 1d68fb000 00:05 3563      /dev/dri/card0
b2687000-b268f000 rw-s 1d68bd000 00:05 3563      /dev/dri/card0
b268f000-b2697000 rw-s 1d68b5000 00:05 3563      /dev/dri/card0
b2697000-b269f000 rw-s 1d68ad000 00:05 3563      /dev/dri/card0
b269f000-b26a7000 rw-s 1d68a5000 00:05 3563      /dev/dri/card0
b26a7000-b26af000 rw-s 1d689d000 00:05 3563      /dev/dri/card0
b26af000-b26b7000 rw-s 1d6895000 00:05 3563      /dev/dri/card0
b26b7000-b26bf000 rw-s 1d688d000 00:05 3563      /dev/dri/card0
b26bf000-b26c7000 rw-s 1d6885000 00:05 3563      /dev/dri/card0
b26c7000-b26cf000 rw-s 1d687d000 00:05 3563      /dev/dri/card0
b26cf000-b26d7000 rw-s 1d6875000 00:05 3563      /dev/dri/card0
b26d7000-b26df000 rw-s 1d686d000 00:05 3563      /dev/dri/card0
b26df000-b26e7000 rw-s 1d6865000 00:05 3563      /dev/dri/card0
b26e7000-b26ef000 rw-s 1d685d000 00:05 3563      /dev/dri/card0
b26ef000-b26f7000 rw-s 1d6855000 00:05 3563      /dev/dri/card0
b26f7000-b26ff000 rw-s 1d684d000 00:05 3563      /dev/dri/card0
b26ff000-b2707000 rw-s 1d6845000 00:05 3563      /dev/dri/card0
b2707000-b270f000 rw-s 1d683d000 00:05 3563      /dev/dri/card0
b270f000-b2717000 rw-s 1d6835000 00:05 3563      /dev/dri/card0
b2717000-b271f000 rw-s 1d682d000 00:05 3563      /dev/dri/card0
b271f000-b2727000 rw-s 1d6825000 00:05 3563      /dev/dri/card0
b2727000-b272f000 rw-s 1d681d000 00:05 3563      /dev/dri/card0
b272f000-b2737000 rw-s 1d6815000 00:05 3563      /dev/dri/card0
b2737000-b273f000 rw-s 1d680d000 00:05 3563      /dev/dri/card0
b273f000-b2747000 rw-s 1d6805000 00:05 3563      /dev/dri/card0
b2747000-b274f000 rw-s 1d67fd000 00:05 3563      /dev/dri/card0
b274f000-b2757000 rw-s 1d67f5000 00:05 3563      /dev/dri/card0
b2757000-b275f000 rw-s 1d67ed000 00:05 3563      /dev/dri/card0
b275f000-b2767000 rw-s 1d67e5000 00:05 3563      /dev/dri/card0
b2767000-b276f000 rw-s 1d67dd000 00:05 3563      /dev/dri/card0
b276f000-b2777000 rw-s 1d67d5000 00:05 3563      /dev/dri/card0
b2777000-b277f000 rw-s 1d67cd000 00:05 3563      /dev/dri/card0
b277f000-b2787000 rw-s 1d67c5000 00:05 3563      /dev/dri/card0
b2787000-b278f000 rw-s 1d67bd000 00:05 3563      /dev/dri/card0
b278f000-b2797000 rw-s 1d67b5000 00:05 3563      /dev/dri/card0
b2797000-b279f000 rw-s 1d67ad000 00:05 3563      /dev/dri/card0
b279f000-b27a7000 rw-s 1d67a5000 00:05 3563      /dev/dri/card0
b27a7000-b27af000 rw-s 1d679d000 00:05 3563      /dev/dri/card0
b27af000-b27b7000 rw-s 1d6795000 00:05 3563      /dev/dri/card0
b27b7000-b27bf000 rw-s 1d678d000 00:05 3563      /dev/dri/card0
b27bf000-b27c7000 rw-s 1d6785000 00:05 3563      /dev/dri/card0
b27c7000-b27cf000 rw-s 1d677d000 00:05 3563      /dev/dri/card0
b27cf000-b27d7000 rw-s 1d6775000 00:05 3563      /dev/dri/card0
b27d7000-b27df000 rw-s 1d676d000 00:05 3563      /dev/dri/card0
b27df000-b27e7000 rw-s 1d6765000 00:05 3563      /dev/dri/card0
b27e7000-b27ef000 rw-s 1d675d000 00:05 3563      /dev/dri/card0
b27ef000-b27f7000 rw-s 1d6755000 00:05 3563      /dev/dri/card0
b27f7000-b27ff000 rw-s 1d674d000 00:05 3563      /dev/dri/card0
b27ff000-b2807000 rw-s 1d6745000 00:05 3563      /dev/dri/card0
b2807000-b280f000 rw-s 1d673d000 00:05 3563      /dev/dri/card0
b280f000-b2817000 rw-s 1d6735000 00:05 3563      /dev/dri/card0
b2817000-b281f000 rw-s 1d672d000 00:05 3563      /dev/dri/card0
b281f000-b2827000 rw-s 1d6725000 00:05 3563      /dev/dri/card0
b2827000-b282f000 rw-s 1d671d000 00:05 3563      /dev/dri/card0
b282f000-b2837000 rw-s 1d6715000 00:05 3563      /dev/dri/card0
b2837000-b283f000 rw-s 1d66f0000 00:05 3563      /dev/dri/card0
b283f000-b2847000 rw-s 1d66e8000 00:05 3563      /dev/dri/card0
b2847000-b284f000 rw-s 1d66e0000 00:05 3563      /dev/dri/card0
b284f000-b2857000 rw-s 1d66d8000 00:05 3563      /dev/dri/card0
b2857000-b285f000 rw-s 1d66d0000 00:05 3563      /dev/dri/card0
b285f000-b2867000 rw-s 1d66c8000 00:05 3563      /dev/dri/card0
b2867000-b286f000 rw-s 1d670d000 00:05 3563      /dev/dri/card0
b286f000-b2877000 rw-s 1d6705000 00:05 3563      /dev/dri/card0
b2877000-b287f000 rw-s 1d66fd000 00:05 3563      /dev/dri/card0
b287f000-b2887000 rw-s 1d66bf000 00:05 3563      /dev/dri/card0
b2887000-b288f000 rw-s 1d66b7000 00:05 3563      /dev/dri/card0
b288f000-b2897000 rw-s 1d66af000 00:05 3563      /dev/dri/card0
b2897000-b289f000 rw-s 1d66a7000 00:05 3563      /dev/dri/card0
b289f000-b28a7000 rw-s 1d669f000 00:05 3563      /dev/dri/card0
b28a7000-b28af000 rw-s 1d6697000 00:05 3563      /dev/dri/card0
b28af000-b28b7000 rw-s 1d668f000 00:05 3563      /dev/dri/card0
b28b7000-b28bf000 rw-s 1d6687000 00:05 3563      /dev/dri/card0
b28bf000-b28c7000 rw-s 1d667f000 00:05 3563      /dev/dri/card0
b28c7000-b28cf000 rw-s 1d6677000 00:05 3563      /dev/dri/card0
b28cf000-b28d7000 rw-s 1d666f000 00:05 3563      /dev/dri/card0
b28d7000-b28df000 rw-s 1d6667000 00:05 3563      /dev/dri/card0
b28df000-b28e7000 rw-s 1d665f000 00:05 3563      /dev/dri/card0
b28e7000-b28ef000 rw-s 1d6657000 00:05 3563      /dev/dri/card0
b28ef000-b28f7000 rw-s 1d664f000 00:05 3563      /dev/dri/card0
b28f7000-b28ff000 rw-s 1d6647000 00:05 3563      /dev/dri/card0
b28ff000-b2907000 rw-s 1d663f000 00:05 3563      /dev/dri/card0
b2907000-b290f000 rw-s 1d6637000 00:05 3563      /dev/dri/card0
b290f000-b2917000 rw-s 1d662f000 00:05 3563      /dev/dri/card0
b2917000-b291f000 rw-s 1d6627000 00:05 3563      /dev/dri/card0
b291f000-b2927000 rw-s 1d661f000 00:05 3563      /dev/dri/card0
b2927000-b292f000 rw-s 1d6617000 00:05 3563      /dev/dri/card0
b292f000-b2937000 rw-s 1d660f000 00:05 3563      /dev/dri/card0
b2937000-b293f000 rw-s 1d6607000 00:05 3563      /dev/dri/card0
b293f000-b2947000 rw-s 1d65ff000 00:05 3563      /dev/dri/card0
b2947000-b294f000 rw-s 1d65f7000 00:05 3563      /dev/dri/card0
b294f000-b2957000 rw-s 1d65ef000 00:05 3563      /dev/dri/card0
b2957000-b295f000 rw-s 1d65e7000 00:05 3563      /dev/dri/card0
b295f000-b2967000 rw-s 1d65df000 00:05 3563      /dev/dri/card0
b2967000-b296f000 rw-s 1d65d7000 00:05 3563      /dev/dri/card0
b296f000-b2977000 rw-s 1d6542000 00:05 3563      /dev/dri/card0
b2977000-b297f000 rw-s 1d653a000 00:05 3563      /dev/dri/card0
b297f000-b2987000 rw-s 1d6532000 00:05 3563      /dev/dri/card0
b2987000-b298f000 rw-s 1d652a000 00:05 3563      /dev/dri/card0
b298f000-b2997000 rw-s 1d6522000 00:05 3563      /dev/dri/card0
b2997000-b299f000 rw-s 1d651a000 00:05 3563      /dev/dri/card0
b299f000-b29a7000 rw-s 1d65cf000 00:05 3563      /dev/dri/card0
b29a7000-b29af000 rw-s 1d65c7000 00:05 3563      /dev/dri/card0
b29af000-b29b7000 rw-s 1d65bf000 00:05 3563      /dev/dri/card0
b29b7000-b29bf000 rw-s 1d65b7000 00:05 3563      /dev/dri/card0
b29bf000-b29c7000 rw-s 1d65af000 00:05 3563      /dev/dri/card0
b29c7000-b29cf000 rw-s 1d65a7000 00:05 3563      /dev/dri/card0
b29cf000-b29d7000 rw-s 1d659f000 00:05 3563      /dev/dri/card0
b29d7000-b29df000 rw-s 1d6597000 00:05 3563      /dev/dri/card0
b29df000-b29e7000 rw-s 1d658f000 00:05 3563      /dev/dri/card0
b29e7000-b29ef000 rw-s 1d6587000 00:05 3563      /dev/dri/card0
b29ef000-b29f7000 rw-s 1d657f000 00:05 3563      /dev/dri/card0
b29f7000-b29ff000 rw-s 1d6577000 00:05 3563      /dev/dri/card0
b29ff000-b2a07000 rw-s 1d656f000 00:05 3563      /dev/dri/card0
b2a07000-b2a0f000 rw-s 1d6567000 00:05 3563      /dev/dri/card0
b2a0f000-b2a17000 rw-s 1d655f000 00:05 3563      /dev/dri/card0
b2a17000-b2a1f000 rw-s 1d6557000 00:05 3563      /dev/dri/card0
b2a1f000-b2a27000 rw-s 1d654f000 00:05 3563      /dev/dri/card0
b2a27000-b2a2f000 rw-s 1d6504000 00:05 3563      /dev/dri/card0
b2a2f000-b2a37000 rw-s 1d64fc000 00:05 3563      /dev/dri/card0
b2a37000-b2a3f000 rw-s 1d64f4000 00:05 3563      /dev/dri/card0
b2a3f000-b2a47000 rw-s 1d64ec000 00:05 3563      /dev/dri/card0
b2a47000-b2a4f000 rw-s 1d64e4000 00:05 3563      /dev/dri/card0
b2a4f000-b2a57000 rw-s 1d64dc000 00:05 3563      /dev/dri/card0
b2a57000-b2a5f000 rw-s 1d6511000 00:05 3563      /dev/dri/card0
b2a5f000-b2a67000 rw-s 1d64d3000 00:05 3563      /dev/dri/card0
b2a67000-b2a6f000 rw-s 1d64cb000 00:05 3563      /dev/dri/card0
b2a6f000-b2a77000 rw-s 1d6487000 00:05 3563      /dev/dri/card0
b2a77000-b2a7f000 rw-s 1d647f000 00:05 3563      /dev/dri/card0
b2a7f000-b2a87000 rw-s 1d6477000 00:05 3563      /dev/dri/card0
b2a87000-b2a8f000 rw-s 1d646f000 00:05 3563      /dev/dri/card0
b2a8f000-b2a97000 rw-s 1d6467000 00:05 3563      /dev/dri/card0
b2a97000-b2a9f000 rw-s 1d645f000 00:05 3563      /dev/dri/card0
b2a9f000-b2aa7000 rw-s 1d64c3000 00:05 3563      /dev/dri/card0
b2aa7000-b2aaf000 rw-s 1d64bb000 00:05 3563      /dev/dri/card0
b2aaf000-b2ab7000 rw-s 1d64b3000 00:05 3563      /dev/dri/card0
b2ab7000-b2abf000 rw-s 1d64ab000 00:05 3563      /dev/dri/card0
b2abf000-b2ac7000 rw-s 1d64a3000 00:05 3563      /dev/dri/card0
b2ac7000-b2acf000 rw-s 1d649b000 00:05 3563      /dev/dri/card0
b2acf000-b2ad7000 rw-s 1d6493000 00:05 3563      /dev/dri/card0
b2ad7000-b2adf000 rw-s 1d6455000 00:05 3563      /dev/dri/card0
b2adf000-b2ae7000 rw-s 1d644d000 00:05 3563      /dev/dri/card0
b2ae7000-b2aef000 rw-s 1d6445000 00:05 3563      /dev/dri/card0
b2aef000-b2af2000 rw-s 1d6193000 00:05 3563      /dev/dri/card0
b2af2000-b2afa000 rw-s 1d643d000 00:05 3563      /dev/dri/card0
b2afa000-b2b02000 rw-s 1d6435000 00:05 3563      /dev/dri/card0
b2b02000-b2b0a000 rw-s 1d642d000 00:05 3563      /dev/dri/card0
b2b0a000-b2b12000 rw-s 1d6425000 00:05 3563      /dev/dri/card0
b2b12000-b2b1a000 rw-s 1d641d000 00:05 3563      /dev/dri/card0
b2b1a000-b2b22000 rw-s 1d6415000 00:05 3563      /dev/dri/card0
b2b22000-b2b2a000 rw-s 1d640d000 00:05 3563      /dev/dri/card0
b2b2a000-b2b32000 rw-s 1d6405000 00:05 3563      /dev/dri/card0
b2b32000-b2b3a000 rw-s 1d63fd000 00:05 3563      /dev/dri/card0
b2b3a000-b2b42000 rw-s 1d63f5000 00:05 3563      /dev/dri/card0
b2b42000-b2b4a000 rw-s 1d63ed000 00:05 3563      /dev/dri/card0
b2b4a000-b2b52000 rw-s 1d63e5000 00:05 3563      /dev/dri/card0
b2b52000-b2b5a000 rw-s 1d63dd000 00:05 3563      /dev/dri/card0
b2b5a000-b2b62000 rw-s 1d63d5000 00:05 3563      /dev/dri/card0
b2b62000-b2b6a000 rw-s 1d63cd000 00:05 3563      /dev/dri/card0
b2b6a000-b2b72000 rw-s 1d63c5000 00:05 3563      /dev/dri/card0
b2b72000-b2b7a000 rw-s 1d63bd000 00:05 3563      /dev/dri/card0
b2b7a000-b2b82000 rw-s 1d63b5000 00:05 3563      /dev/dri/card0
b2b82000-b2b8a000 rw-s 1d63ad000 00:05 3563      /dev/dri/card0
b2b8a000-b2b92000 rw-s 1d63a5000 00:05 3563      /dev/dri/card0
b2b92000-b2b9a000 rw-s 1d639d000 00:05 3563      /dev/dri/card0
b2b9a000-b2ba2000 rw-s 1d6395000 00:05 3563      /dev/dri/card0
b2ba2000-b2baa000 rw-s 1d638d000 00:05 3563      /dev/dri/card0
b2baa000-b2bb2000 rw-s 1d6385000 00:05 3563      /dev/dri/card0
b2bb2000-b2bba000 rw-s 1d637d000 00:05 3563      /dev/dri/card0
b2bba000-b2bc2000 rw-s 1d6375000 00:05 3563      /dev/dri/card0
b2bc2000-b2bca000 rw-s 1d636d000 00:05 3563      /dev/dri/card0
b2bca000-b2bd2000 rw-s 1d6365000 00:05 3563      /dev/dri/card0
b2bd2000-b2bda000 rw-s 1d635d000 00:05 3563      /dev/dri/card0
b2bda000-b2be2000 rw-s 1d6355000 00:05 3563      /dev/dri/card0
b2be2000-b2bea000 rw-s 1d6321000 00:05 3563      /dev/dri/card0
b2bea000-b2bf2000 rw-s 1d6319000 00:05 3563      /dev/dri/card0
b2bf2000-b2bfa000 rw-s 1d6311000 00:05 3563      /dev/dri/card0
b2bfa000-b2c02000 rw-s 1d6309000 00:05 3563      /dev/dri/card0
b2c02000-b2c0a000 rw-s 1d6301000 00:05 3563      /dev/dri/card0
b2c0a000-b2c12000 rw-s 1d62f9000 00:05 3563      /dev/dri/card0
b2c12000-b2c1a000 rw-s 1d634d000 00:05 3563      /dev/dri/card0
b2c1a000-b2c22000 rw-s 1d6345000 00:05 3563      /dev/dri/card0
b2c22000-b2c2a000 rw-s 1d633d000 00:05 3563      /dev/dri/card0
b2c2a000-b2c32000 rw-s 1d6335000 00:05 3563      /dev/dri/card0
b2c32000-b2c3a000 rw-s 1d632d000 00:05 3563      /dev/dri/card0
b2c3a000-b2c42000 rw-s 1d62ef000 00:05 3563      /dev/dri/card0
b2c42000-b2c4a000 rw-s 1d62e7000 00:05 3563      /dev/dri/card0
b2c4a000-b2c52000 rw-s 1d62df000 00:05 3563      /dev/dri/card0
b2c52000-b2c5a000 rw-s 1d62d7000 00:05 3563      /dev/dri/card0
b2c5a000-b2c62000 rw-s 1d62cf000 00:05 3563      /dev/dri/card0
b2c62000-b2c6a000 rw-s 1d62c7000 00:05 3563      /dev/dri/card0
b2c6a000-b2c72000 rw-s 1d62bf000 00:05 3563      /dev/dri/card0
b2c72000-b2c7a000 rw-s 1d62b7000 00:05 3563      /dev/dri/card0
b2c7a000-b2c82000 rw-s 1d62af000 00:05 3563      /dev/dri/card0
b2c82000-b2c8a000 rw-s 1d62a7000 00:05 3563      /dev/dri/card0
b2c8a000-b2c92000 rw-s 1d629f000 00:05 3563      /dev/dri/card0
b2c92000-b2c9a000 rw-s 1d6297000 00:05 3563      /dev/dri/card0
b2c9a000-b2ca2000 rw-s 1d628f000 00:05 3563      /dev/dri/card0
b2ca2000-b2caa000 rw-s 1d6287000 00:05 3563      /dev/dri/card0
b2caa000-b2cb2000 rw-s 1d627f000 00:05 3563      /dev/dri/card0
b2cb2000-b2cba000 rw-s 1d6277000 00:05 3563      /dev/dri/card0
b2cba000-b2cc2000 rw-s 1d6203000 00:05 3563      /dev/dri/card0
b2cc2000-b2cca000 rw-s 1d626f000 00:05 3563      /dev/dri/card0
b2cca000-b2cd2000 rw-s 1d6267000 00:05 3563      /dev/dri/card0
b2cd2000-b2cda000 rw-s 1d625f000 00:05 3563      /dev/dri/card0
b2cda000-b2ce2000 rw-s 1d6257000 00:05 3563      /dev/dri/card0
b2ce2000-b2cea000 rw-s 1d624f000 00:05 3563      /dev/dri/card0
b2cea000-b2cf2000 rw-s 1d61fb000 00:05 3563      /dev/dri/card0
b2cf2000-b2cfa000 rw-s 1d61f3000 00:05 3563      /dev/dri/card0
b2cfa000-b2d02000 rw-s 1d61eb000 00:05 3563      /dev/dri/card0
b2d02000-b2d0a000 rw-s 1d61e3000 00:05 3563      /dev/dri/card0
b2d0a000-b2d12000 rw-s 1d61db000 00:05 3563      /dev/dri/card0
b2d12000-b2d1a000 rw-s 1d6247000 00:05 3563      /dev/dri/card0
b2d1a000-b2d22000 rw-s 1d623f000 00:05 3563      /dev/dri/card0
b2d22000-b2d2a000 rw-s 1d6237000 00:05 3563      /dev/dri/card0
b2d2a000-b2d32000 rw-s 1d622f000 00:05 3563      /dev/dri/card0
b2d32000-b2d3a000 rw-s 1d6227000 00:05 3563      /dev/dri/card0
b2d3a000-b2d42000 rw-s 1d621f000 00:05 3563      /dev/dri/card0
b2d42000-b2d4a000 rw-s 1d6217000 00:05 3563      /dev/dri/card0
b2d4a000-b2d52000 rw-s 1d620f000 00:05 3563      /dev/dri/card0
b2d52000-b2d5a000 rw-s 1d61d1000 00:05 3563      /dev/dri/card0
b2d5a000-b2d62000 rw-s 1d61c9000 00:05 3563      /dev/dri/card0
b2d62000-b2d6a000 rw-s 1d61c1000 00:05 3563      /dev/dri/card0
b2d6a000-b2d72000 rw-s 1d618a000 00:05 3563      /dev/dri/card0
b2d72000-b2d7a000 rw-s 1d6182000 00:05 3563      /dev/dri/card0
b2d7a000-b2d82000 rw-s 1d6178000 00:05 3563      /dev/dri/card0
b2d82000-b2d85000 rw-s 1d6175000 00:05 3563      /dev/dri/card0
b2d85000-b2d8d000 rw-s 1d616d000 00:05 3563      /dev/dri/card0
b2d8d000-b2d95000 rw-s 1d6165000 00:05 3563      /dev/dri/card0
b2d95000-b2d9d000 rw-s 1d61b9000 00:05 3563      /dev/dri/card0
b2d9d000-b2da5000 rw-s 1d61b1000 00:05 3563      /dev/dri/card0
b2da5000-b2dad000 rw-s 1d61a9000 00:05 3563      /dev/dri/card0
b2dad000-b2db5000 rw-s 1d61a1000 00:05 3563      /dev/dri/card0
b2db5000-b2dbd000 rw-s 1d6199000 00:05 3563      /dev/dri/card0
b2dbd000-b2dc5000 rw-s 1d615b000 00:05 3563      /dev/dri/card0
b2dc5000-b2dcd000 rw-s 1d6153000 00:05 3563      /dev/dri/card0
b2dcd000-b2dd5000 rw-s 1d614b000 00:05 3563      /dev/dri/card0
b2dd5000-b2ddd000 rw-s 1d6143000 00:05 3563      /dev/dri/card0
b2ddd000-b2de5000 rw-s 1d613b000 00:05 3563      /dev/dri/card0
b2de5000-b2ded000 rw-s 1d6133000 00:05 3563      /dev/dri/card0
b2ded000-b2df5000 rw-s 1d612b000 00:05 3563      /dev/dri/card0
b2df5000-b2dfd000 rw-s 1d6123000 00:05 3563      /dev/dri/card0
b2dfd000-b2e05000 rw-s 1d611b000 00:05 3563      /dev/dri/card0
b2e05000-b2e0d000 rw-s 1d6113000 00:05 3563      /dev/dri/card0
b2e0d000-b2e15000 rw-s 1d610b000 00:05 3563      /dev/dri/card0
b2e15000-b2e1d000 rw-s 1d6103000 00:05 3563      /dev/dri/card0
b2e1d000-b2e25000 rw-s 1d60fb000 00:05 3563      /dev/dri/card0
b2e25000-b2e2d000 rw-s 1d60f3000 00:05 3563      /dev/dri/card0
b2e2d000-b2e35000 rw-s 1d60eb000 00:05 3563      /dev/dri/card0
b2e35000-b2e3d000 rw-s 1d60e3000 00:05 3563      /dev/dri/card0
b2e3d000-b2e45000 rw-s 1d60db000 00:05 3563      /dev/dri/card0
b2e45000-b2e4d000 rw-s 1d60d3000 00:05 3563      /dev/dri/card0
b2e4d000-b2e55000 rw-s 1d60cb000 00:05 3563      /dev/dri/card0
b2e55000-b2e5d000 rw-s 1d60c3000 00:05 3563      /dev/dri/card0
b2e5d000-b2e65000 rw-s 1d604a000 00:05 3563      /dev/dri/card0
b2e65000-b2e6d000 rw-s 1d603e000 00:05 3563      /dev/dri/card0
b2e6d000-b2e75000 rw-s 1d6036000 00:05 3563      /dev/dri/card0
b2e75000-b2e7d000 rw-s 1d602d000 00:05 3563      /dev/dri/card0
b2e7d000-b2e85000 rw-s 1d6025000 00:05 3563      /dev/dri/card0
b2e85000-b2e8d000 rw-s 1d601d000 00:05 3563      /dev/dri/card0
b2e8d000-b2e95000 rw-s 1d60bb000 00:05 3563      /dev/dri/card0
b2e95000-b2e9d000 rw-s 1d60b3000 00:05 3563      /dev/dri/card0
b2e9d000-b2ea5000 rw-s 1d60ab000 00:05 3563      /dev/dri/card0
b2ea5000-b2ead000 rw-s 1d60a3000 00:05 3563      /dev/dri/card0
b2ead000-b2eb5000 rw-s 1d609b000 00:05 3563      /dev/dri/card0
b2eb5000-b2ebd000 rw-s 1d6093000 00:05 3563      /dev/dri/card0
b2ebd000-b2ec5000 rw-s 1d608b000 00:05 3563      /dev/dri/card0
b2ec5000-b2ecd000 rw-s 1d6083000 00:05 3563      /dev/dri/card0
b2ecd000-b2ed5000 rw-s 1d607b000 00:05 3563      /dev/dri/card0
b2ed5000-b2edd000 rw-s 1d6073000 00:05 3563      /dev/dri/card0
b2edd000-b2ee5000 rw-s 1d606b000 00:05 3563      /dev/dri/card0
b2ee5000-b2eed000 rw-s 1d6063000 00:05 3563      /dev/dri/card0
b2eed000-b2ef5000 rw-s 1d605b000 00:05 3563      /dev/dri/card0
b2ef5000-b2efd000 rw-s 1d6053000 00:05 3563      /dev/dri/card0
b2efd000-b2f05000 rw-s 1d6015000 00:05 3563      /dev/dri/card0
b2f05000-b2f0d000 rw-s 1d600d000 00:05 3563      /dev/dri/card0
b2f0d000-b2f15000 rw-s 1d6005000 00:05 3563      /dev/dri/card0
b2f15000-b2f1d000 rw-s 1d5ffd000 00:05 3563      /dev/dri/card0
b2f1d000-b2f25000 rw-s 1d5ff5000 00:05 3563      /dev/dri/card0
b2f25000-b2f2d000 rw-s 1d5fed000 00:05 3563      /dev/dri/card0
b2f2d000-b2f35000 rw-s 1d5fe5000 00:05 3563      /dev/dri/card0
b2f35000-b2f3d000 rw-s 1d5fdd000 00:05 3563      /dev/dri/card0
b2f3d000-b2f45000 rw-s 1d5fd5000 00:05 3563      /dev/dri/card0
b2f45000-b2f4d000 rw-s 1d5fcd000 00:05 3563      /dev/dri/card0
b2f4d000-b2f55000 rw-s 1d5fc5000 00:05 3563      /dev/dri/card0
b2f55000-b2f5d000 rw-s 1d5fbd000 00:05 3563      /dev/dri/card0
b2f5d000-b2f65000 rw-s 1d5fb5000 00:05 3563      /dev/dri/card0
b2f65000-b2f6d000 rw-s 1d5fad000 00:05 3563      /dev/dri/card0
b2f6d000-b2f75000 rw-s 1d5fa5000 00:05 3563      /dev/dri/card0
b2f75000-b2f7d000 rw-s 1d5f9d000 00:05 3563      /dev/dri/card0
b2f7d000-b2f85000 rw-s 1d5f95000 00:05 3563      /dev/dri/card0
b2f85000-b2f8d000 rw-s 1d5f8d000 00:05 3563      /dev/dri/card0
b2f8d000-b2f95000 rw-s 1d5f85000 00:05 3563      /dev/dri/card0
b2f95000-b2f9d000 rw-s 1d5f7d000 00:05 3563      /dev/dri/card0
b2f9d000-b2fa5000 rw-s 1d5f75000 00:05 3563      /dev/dri/card0
b2fa7000-b2faf000 rw-s 1d6f79000 00:05 3563      /dev/dri/card0
b2faf000-b2fb7000 rw-s 1d6f57000 00:05 3563      /dev/dri/card0
b2fb7000-b2fbd000 rw-s 1d5f5d000 00:05 3563      /dev/dri/card0
b2fbd000-b2fc5000 rw-s 1d5f55000 00:05 3563      /dev/dri/card0
b2fc5000-b2fcd000 rw-s 1d5f4d000 00:05 3563      /dev/dri/card0
b2fcd000-b2fd5000 rw-s 1d5f45000 00:05 3563      /dev/dri/card0
b2fd5000-b2fdd000 rw-s 1d5f3d000 00:05 3563      /dev/dri/card0
b2fdd000-b2fe5000 rw-s 1d5f35000 00:05 3563      /dev/dri/card0
b2fe5000-b2fed000 rw-s 1d5f2d000 00:05 3563      /dev/dri/card0
b2fed000-b2ff5000 rw-s 1d5f25000 00:05 3563      /dev/dri/card0
b2ff5000-b2ffd000 rw-s 1d5f1d000 00:05 3563      /dev/dri/card0
b2ffd000-b3005000 rw-s 1d5f15000 00:05 3563      /dev/dri/card0
b3005000-b300d000 rw-s 1d5f0d000 00:05 3563      /dev/dri/card0
b300d000-b3015000 rw-s 1d5f05000 00:05 3563      /dev/dri/card0
b3015000-b301d000 rw-s 1d5efd000 00:05 3563      /dev/dri/card0
b301d000-b3025000 rw-s 1d5ef5000 00:05 3563      /dev/dri/card0
b3025000-b302d000 rw-s 1d5eed000 00:05 3563      /dev/dri/card0
b302d000-b3035000 rw-s 1d5ee5000 00:05 3563      /dev/dri/card0
b3035000-b303d000 rw-s 1d5bf6000 00:05 3563      /dev/dri/card0
b303d000-b3045000 rw-s 1d5e2d000 00:05 3563      /dev/dri/card0
b3045000-b304d000 rw-s 1d5e25000 00:05 3563      /dev/dri/card0
b304d000-b3055000 rw-s 1d5e1d000 00:05 3563      /dev/dri/card0
b3055000-b305d000 rw-s 1d5e15000 00:05 3563      /dev/dri/card0
b305d000-b30b3000 rw-s 1d5e8f000 00:05 3563      /dev/dri/card0
b30b3000-b3109000 rw-s 1d5e39000 00:05 3563      /dev/dri/card0
b3109000-b3111000 rw-s 1d8941000 00:05 3563      /dev/dri/card0
b3111000-b3119000 rw-s 1d8939000 00:05 3563      /dev/dri/card0
b3119000-b3121000 rw-s 1d744b000 00:05 3563      /dev/dri/card0
b3121000-b3129000 rw-s 1d74fa000 00:05 3563      /dev/dri/card0
b3129000-b3131000 rw-s 1d9d29000 00:05 3563      /dev/dri/card0
b3131000-b3139000 rw-s 1d9c19000 00:05 3563      /dev/dri/card0
b3139000-b318f000 rw-s 1d5dad000 00:05 3563      /dev/dri/card0
b318f000-b3197000 rw-s 1d5d5f000 00:05 3563      /dev/dri/card0
b3197000-b319f000 rw-s 1d5d57000 00:05 3563      /dev/dri/card0
b319f000-b31a7000 rw-s 1d5da5000 00:05 3563      /dev/dri/card0
b31a7000-b31af000 rw-s 1d5d9d000 00:05 3563      /dev/dri/card0
b31af000-b31b7000 rw-s 1d5d95000 00:05 3563      /dev/dri/card0
b31b7000-b31bf000 rw-s 1d5d25000 00:05 3563      /dev/dri/card0
b31bf000-b31c7000 rw-s 1d5d8d000 00:05 3563      /dev/dri/card0
b31c7000-b31cf000 rw-s 1d5d1d000 00:05 3563      /dev/dri/card0
b31cf000-b31d7000 rw-s 1d5d15000 00:05 3563      /dev/dri/card0
b31d7000-b31df000 rw-s 1d5d0d000 00:05 3563      /dev/dri/card0
b31df000-b31e7000 rw-s 1d5d01000 00:05 3563      /dev/dri/card0
b31e7000-b31ef000 rw-s 1d5cf9000 00:05 3563      /dev/dri/card0
b31ef000-b31f7000 rw-s 1d5d4f000 00:05 3563      /dev/dri/card0
b31f7000-b31ff000 rw-s 1d5d47000 00:05 3563      /dev/dri/card0
b31ff000-b3207000 rw-s 1d5d3f000 00:05 3563      /dev/dri/card0
b3207000-b320f000 rw-s 1d5d37000 00:05 3563      /dev/dri/card0
b320f000-b3217000 rw-s 1d5cc7000 00:05 3563      /dev/dri/card0
b3217000-b321f000 rw-s 1d5d2f000 00:05 3563      /dev/dri/card0
b321f000-b3227000 rw-s 1d5cbf000 00:05 3563      /dev/dri/card0
b3227000-b322f000 rw-s 1d5cb7000 00:05 3563      /dev/dri/card0
b322f000-b3237000 rw-s 1d5caf000 00:05 3563      /dev/dri/card0
b3237000-b323f000 rw-s 1d5ca3000 00:05 3563      /dev/dri/card0
b323f000-b3247000 rw-s 1d5c9b000 00:05 3563      /dev/dri/card0
b3247000-b324f000 rw-s 1d5cf1000 00:05 3563      /dev/dri/card0
b324f000-b3257000 rw-s 1d5ce9000 00:05 3563      /dev/dri/card0
b3257000-b325f000 rw-s 1d5ce1000 00:05 3563      /dev/dri/card0
b325f000-b3267000 rw-s 1d5cd9000 00:05 3563      /dev/dri/card0
b3267000-b326f000 rw-s 1d5cd1000 00:05 3563      /dev/dri/card0
b326f000-b3277000 rw-s 1d5c71000 00:05 3563      /dev/dri/card0
b3277000-b327f000 rw-s 1d5c69000 00:05 3563      /dev/dri/card0
b327f000-b3287000 rw-s 1d5c61000 00:05 3563      /dev/dri/card0
b3287000-b328f000 rw-s 1d5c59000 00:05 3563      /dev/dri/card0
b328f000-b3297000 rw-s 1d5c4d000 00:05 3563      /dev/dri/card0
b3297000-b329f000 rw-s 1d5c45000 00:05 3563      /dev/dri/card0
b329f000-b32a7000 rw-s 1d5c93000 00:05 3563      /dev/dri/card0
b32a7000-b32af000 rw-s 1d5c8b000 00:05 3563      /dev/dri/card0
b32af000-b32b7000 rw-s 1d5c83000 00:05 3563      /dev/dri/card0
b32b7000-b32bf000 rw-s 1d5c17000 00:05 3563      /dev/dri/card0
b32bf000-b32c7000 rw-s 1d5c7b000 00:05 3563      /dev/dri/card0
b32c7000-b32cf000 rw-s 1d5c3d000 00:05 3563      /dev/dri/card0
b32cf000-b32d7000 rw-s 1d5c1f000 00:05 3563      /dev/dri/card0
b32d7000-b32df000 rw-s 1d5c0f000 00:05 3563      /dev/dri/card0
b32df000-b32e2000 ---p 00000000 00:00 0 
b32e2000-b3330000 rw-p 00000000 00:00 0 
b3330000-b3338000 rw-s 1d5bff000 00:05 3563      /dev/dri/card0
b3338000-b3340000 rw-s 1d5e0d000 00:05 3563      /dev/dri/card0
b3340000-b3348000 rw-s 1d5e05000 00:05 3563      /dev/dri/card0
b3348000-b3350000 rw-s 1d5c30000 00:05 3563      /dev/dri/card0
b3350000-b3358000 rw-s 1d5bc5000 00:05 3563      /dev/dri/card0
b3358000-b3360000 rw-s 1d5c27000 00:05 3563      /dev/dri/card0
b3360000-b3368000 rw-s 1d5bbd000 00:05 3563      /dev/dri/card0
b3368000-b3370000 rw-s 1d5bb5000 00:05 3563      /dev/dri/card0
b3370000-b3378000 rw-s 1d5bad000 00:05 3563      /dev/dri/card0
b3378000-b3380000 rw-s 1d5ba5000 00:05 3563      /dev/dri/card0
b3380000-b3388000 rw-s 1d5bee000 00:05 3563      /dev/dri/card0
b3388000-b3390000 rw-s 1d5be6000 00:05 3563      /dev/dri/card0
b3390000-b3398000 rw-s 1d5b61000 00:05 3563      /dev/dri/card0
b3398000-b33a0000 rw-s 1d5b9d000 00:05 3563      /dev/dri/card0
b33a0000-b33a8000 rw-s 1d5bde000 00:05 3563      /dev/dri/card0
b33a8000-b33b0000 rw-s 1d5b95000 00:05 3563      /dev/dri/card0
b33b0000-b33b8000 rw-s 1d5b8d000 00:05 3563      /dev/dri/card0
b33b8000-b33c0000 rw-s 1d5d83000 00:05 3563      /dev/dri/card0
b33c0000-b33c8000 rw-s 1d5d7b000 00:05 3563      /dev/dri/card0
b33c8000-b33d0000 rw-s 1d5b59000 00:05 3563      /dev/dri/card0
b33d0000-b33d8000 rw-s 1d5d73000 00:05 3563      /dev/dri/card0
b33d8000-b33e0000 rw-s 1d5d6b000 00:05 3563      /dev/dri/card0
b33e0000-b33e8000 rw-s 1d5b01000 00:05 3563      /dev/dri/card0
b33e8000-b33f0000 rw-s 1d5b29000 00:05 3563      /dev/dri/card0
b33f0000-b33f8000 rw-s 1d5b51000 00:05 3563      /dev/dri/card0
b33f8000-b3400000 rw-s 1d5b49000 00:05 3563      /dev/dri/card0
b3400000-b34fa000 rw-p 00000000 00:00 0 
b34fa000-b3500000 ---p 00000000 00:00 0 
b3505000-b350d000 rw-s 1d5b41000 00:05 3563      /dev/dri/card0
b350d000-b3515000 rw-s 1d5b39000 00:05 3563      /dev/dri/card0
b3515000-b351d000 rw-s 1d5b31000 00:05 3563      /dev/dri/card0
b351d000-b3525000 rw-s 1d5b21000 00:05 3563      /dev/dri/card0
b3525000-b352d000 rw-s 1d5b19000 00:05 3563      /dev/dri/card0
b352d000-b3535000 rw-s 1d5b11000 00:05 3563      /dev/dri/card0
b3535000-b353d000 rw-s 1d5b09000 00:05 3563      /dev/dri/card0
b353d000-b3545000 rw-s 1d5af9000 00:05 3563      /dev/dri/card0
b3545000-b354d000 rw-s 1d5af1000 00:05 3563      /dev/dri/card0
b354d000-b3555000 rw-s 1d5ae9000 00:05 3563      /dev/dri/card0
b3555000-b355d000 rw-s 1d5add000 00:05 3563      /dev/dri/card0
b355d000-b3565000 rw-s 1d5ad5000 00:05 3563      /dev/dri/card0
b3565000-b356d000 rw-s 1d5acc000 00:05 3563      /dev/dri/card0
b356d000-b3575000 rw-s 1d5ac4000 00:05 3563      /dev/dri/card0
b3575000-b357d000 rw-s 1d5abc000 00:05 3563      /dev/dri/card0
b357d000-b3585000 rw-s 1d5ab4000 00:05 3563      /dev/dri/card0
b3585000-b358d000 rw-s 1d5a74000 00:05 3563      /dev/dri/card0
b358d000-b3595000 rw-s 1d5a63000 00:05 3563      /dev/dri/card0
b3595000-b359d000 rw-s 1d5a5b000 00:05 3563      /dev/dri/card0
b359d000-b35a5000 rw-s 1d5a4f000 00:05 3563      /dev/dri/card0
b35a5000-b35ad000 rw-s 1d5a47000 00:05 3563      /dev/dri/card0
b35ad000-b35b5000 rw-s 1d5a3e000 00:05 3563      /dev/dri/card0
b35b5000-b35bd000 rw-s 1d5a36000 00:05 3563      /dev/dri/card0
b35bd000-b35c5000 rw-s 1d5a6c000 00:05 3563      /dev/dri/card0
b35c5000-b35cd000 rw-s 1d8cdb000 00:05 3563      /dev/dri/card0
b35cd000-b35d5000 rw-s 1d8df9000 00:05 3563      /dev/dri/card0
b35d5000-b362b000 rw-s 1d4574000 00:05 3563      /dev/dri/card0
b362b000-b3681000 rw-s 1d451e000 00:05 3563      /dev/dri/card0
b3682000-b368a000 rw-s 1d5a2e000 00:05 3563      /dev/dri/card0
b368a000-b3692000 rw-s 1d5a26000 00:05 3563      /dev/dri/card0
b3692000-b369a000 rw-s 1d5a1e000 00:05 3563      /dev/dri/card0
b369a000-b36a2000 rw-s 1d5a16000 00:05 3563      /dev/dri/card0
b36a2000-b36a3000 rw-s 1d44a5000 00:05 3563      /dev/dri/card0
b36a4000-b36ac000 rw-s 1d9771000 00:05 3563      /dev/dri/card0
b36ac000-b36b4000 rw-s 1d9769000 00:05 3563      /dev/dri/card0
b36b4000-b370a000 rw-s 1d44c8000 00:05 3563      /dev/dri/card0
b370a000-b3760000 rw-s 1d443c000 00:05 3563      /dev/dri/card0
b3760000-b3768000 rw-s 1d4421000 00:05 3563      /dev/dri/card0
b3768000-b3770000 rw-s 1d5a0a000 00:05 3563      /dev/dri/card0
b3770000-b3778000 rw-s 1d5a02000 00:05 3563      /dev/dri/card0
b3778000-b3f7a000 rw-p 00000000 00:00 0 
b3f7a000-b3f90000 rw-s 1d31d1000 00:05 3563      /dev/dri/card0
b3f90000-b449c000 rw-p 00000000 00:00 0 
b449c000-b4501000 rw-s 00000000 00:04 25853979   /SYSV00000000 (deleted)
b4501000-b4504000 ---p 00000000 00:00 0 
b4504000-b4552000 rw-p 00000000 00:00 0 
b4552000-b4555000 ---p 00000000 00:00 0 
b4555000-b45a3000 rw-p 00000000 00:00 0 
b45a3000-b45a6000 ---p 00000000 00:00 0 
b45a6000-b45f4000 rw-p 00000000 00:00 0 
b45fa000-b4602000 rw-s 1d59f9000 00:05 3563      /dev/dri/card0
b4602000-b460a000 rw-s 1d59f1000 00:05 3563      /dev/dri/card0
b460a000-b4612000 rw-s 1d59e9000 00:05 3563      /dev/dri/card0
b4612000-b461a000 rw-s 1d59e1000 00:05 3563      /dev/dri/card0
b461a000-b4622000 rw-s 1d5983000 00:05 3563      /dev/dri/card0
b4622000-b462a000 rw-s 1d597b000 00:05 3563      /dev/dri/card0
b462a000-b4632000 rw-s 1d5973000 00:05 3563      /dev/dri/card0
b4632000-b463a000 rw-s 1d5967000 00:05 3563      /dev/dri/card0
b463a000-b4642000 rw-s 1d595f000 00:05 3563      /dev/dri/card0
b4642000-b464a000 rw-s 1d59a1000 00:05 3563      /dev/dri/card0
b464a000-b4652000 rw-s 1d5999000 00:05 3563      /dev/dri/card0
b4652000-b465a000 rw-s 1d5957000 00:05 3563      /dev/dri/card0
b465a000-b4662000 rw-s 1d594f000 00:05 3563      /dev/dri/card0
b4662000-b466a000 rw-s 1d5946000 00:05 3563      /dev/dri/card0
b466a000-b4672000 rw-s 1d593e000 00:05 3563      /dev/dri/card0
b4672000-b467a000 rw-s 1d2404000 00:05 3563      /dev/dri/card0
b467a000-b467d000 ---p 00000000 00:00 0 
b467d000-b46cb000 rw-p 00000000 00:00 0 
b46cb000-b46ce000 ---p 00000000 00:00 0 
b46ce000-b4994000 rw-p 00000000 00:00 0 
b4999000-b49a1000 rw-s 1d4416000 00:05 3563      /dev/dri/card0
b49a1000-b4a01000 rw-s 00000000 00:04 23232540   /SYSV00000000 (deleted)
b4a01000-b4a04000 rw-s 1d5cab000 00:05 3563      /dev/dri/card0
b4a04000-b4a06000 rw-s 1d5c0d000 00:05 3563      /dev/dri/card0
b4a06000-b4a08000 rw-s 1d5c0b000 00:05 3563      /dev/dri/card0
b4a08000-b4a10000 rw-s 1d440e000 00:05 3563      /dev/dri/card0
b4a10000-b4a26000 rw-s 1d326a000 00:05 3563      /dev/dri/card0
b4a27000-b4a2f000 rw-s 1d3261000 00:05 3563      /dev/dri/card0
b4a2f000-b4a3a000 r--s 00127000 08:01 8142923    /home/ben/.minecraft/bin/minecraft.jar
b4a3a000-b4a3f000 r--s 00033000 08:01 8142921    /home/ben/.minecraft/bin/jinput.jar
b4a3f000-b4a48000 r--s 000ac000 08:01 8142920    /home/ben/.minecraft/bin/lwjgl.jar
b4a49000-b4a4a000 rw-s 1d4493000 00:05 3563      /dev/dri/card0
b4a4b000-b4a4c000 rw-s 1db40f000 00:05 3563      /dev/dri/card0
b4a4c000-b4a4f000 r--s 0001f000 08:01 8142922    /home/ben/.minecraft/bin/lwjgl_util.jar
b4a4f000-b4a52000 r--s 00038000 08:01 6294065    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
b4a52000-b4a55000 r--s 00077000 08:01 6294086    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar
b4a55000-b4a58000 r--s 00031000 08:01 6294190    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
b4a58000-b4a5c000 r--s 0007c000 08:01 6297725    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
b4a5c000-b4a5f000 ---p 00000000 00:00 0 
b4a5f000-b4aad000 rw-p 00000000 00:00 0 
b4aad000-b4aaf000 r--s 00013000 08:01 6297724    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
b4aaf000-b4b47000 r--p 00000000 08:01 7212737    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4b47000-b4b48000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4b48000-b4b49000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4b49000-b4b4f000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4b4f000-b4b51000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4b51000-b4b54000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4b54000-b4b5a000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4b5a000-b4b5b000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4b5b000-b4b5e000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4b5e000-b4b5f000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4b5f000-b4b60000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4b60000-b4b61000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4b61000-b4b65000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4b65000-b4b69000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4b69000-b4b70000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4b70000-b4b7b000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4b7b000-b4b7e000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4b7e000-b4b7f000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4b7f000-b4b87000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4b87000-b4b8f000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4b8f000-b4b92000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4b92000-b4b94000 r--p 00000000 08:01 7736533    /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
b4b94000-b4b95000 r--p 00000000 08:01 7736950    /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
b4b95000-b4b99000 r--p 00000000 08:01 7736408    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20-properties.mo
b4b99000-b4b9b000 r--p 00000000 08:01 7736538    /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20.mo
b4b9b000-b4b9c000 r--p 00000000 08:01 6422645    /usr/lib/locale/en_GB.utf8/LC_NUMERIC
b4b9c000-b4b9d000 r--p 00000000 08:01 6299161    /usr/lib/locale/en_GB.utf8/LC_TIME
b4b9d000-b4cbb000 r--p 00000000 08:01 6422639    /usr/lib/locale/en_GB.utf8/LC_COLLATE
b4cbb000-b4cbc000 r--p 00000000 08:01 6422600    /usr/lib/locale/en_GB.utf8/LC_MONETARY
b4cbc000-b4cbd000 r--p 00000000 08:01 6422649    /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b4cbd000-b4cbe000 r--p 00000000 08:01 6422646    /usr/lib/locale/en_GB.utf8/LC_PAPER
b4cbe000-b4cbf000 r--p 00000000 08:01 6422722    /usr/lib/locale/en_GB.utf8/LC_NAME
b4cbf000-b4cc0000 r--p 00000000 08:01 6422601    /usr/lib/locale/en_GB.utf8/LC_ADDRESS
b4cc0000-b4cc1000 r--p 00000000 08:01 6422602    /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
b4cc1000-b4cc2000 r--p 00000000 08:01 6422642    /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
b4cc2000-b4cc5000 ---p 00000000 00:00 0 
b4cc5000-b4d13000 rw-p 00000000 00:00 0 
b4d13000-b4d16000 ---p 00000000 00:00 0 
b4d16000-b4d64000 rw-p 00000000 00:00 0 
b4d64000-b4d67000 ---p 00000000 00:00 0 
b4d67000-b4db5000 rw-p 00000000 00:00 0 
b4db5000-b4db6000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4db6000-b4db7000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4db7000-b4dbd000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4dbd000-b4dbf000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4dbf000-b4dc2000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4dc2000-b4dc8000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4dc8000-b4dc9000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4dc9000-b4dcc000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4dcc000-b4dcd000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4dcd000-b4dce000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4dce000-b4dcf000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4dcf000-b4dd3000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4dd3000-b4dd7000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4dd7000-b4dde000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4dde000-b4de9000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4de9000-b4dec000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4dec000-b4ded000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4ded000-b4df5000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4df5000-b4dfd000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4dfd000-b4e00000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4e00000-b4ef9000 rw-p 00000000 00:00 0 
b4ef9000-b4f00000 ---p 00000000 00:00 0 
b4f00000-b4f01000 r--p 00000000 08:01 6422603    /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
b4f01000-b4f02000 r--p 00000000 00:00 0 
b4f02000-b4f03000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4f03000-b4f04000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4f04000-b4f0a000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4f0a000-b4f0c000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4f0c000-b4f0f000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4f0f000-b4f15000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4f15000-b4f16000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4f16000-b4f19000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4f19000-b4f1a000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4f1a000-b4f1b000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4f1b000-b4f1c000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4f1c000-b4f20000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4f20000-b4f24000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4f24000-b4f2b000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4f2b000-b4f36000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4f36000-b4f39000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4f39000-b4f3a000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4f3a000-b4f42000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4f42000-b4f4a000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4f4a000-b4f4d000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4f4d000-b4f50000 ---p 00000000 00:00 0 
b4f50000-b4f9e000 rw-p 00000000 00:00 0 
b4f9e000-b4fa4000 r--s 000fc000 08:01 6297732    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
b4fa4000-b4fad000 r--s 00065000 08:01 6692486    /usr/share/java/gnome-java-bridge.jar
b4fad000-b4fae000 ---p 00000000 00:00 0 
b4fae000-b502e000 rw-p 00000000 00:00 0 
b502e000-b5031000 ---p 00000000 00:00 0 
b5031000-b507f000 rw-p 00000000 00:00 0 
b507f000-b5082000 ---p 00000000 00:00 0 
b5082000-b5100000 rw-p 00000000 00:00 0 
b5100000-b5103000 ---p 00000000 00:00 0 
b5103000-b5151000 rw-p 00000000 00:00 0 
b5151000-b5158000 r--s 00000000 08:01 6292678    /usr/lib/gconv/gconv-modules.cache
b5158000-b5197000 r--p 00000000 08:01 6422640    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b5197000-b519a000 ---p 00000000 00:00 0 
b519a000-b51e8000 rw-p 00000000 00:00 0 
b51e8000-b51eb000 ---p 00000000 00:00 0 
b51eb000-b5239000 rw-p 00000000 00:00 0 
b5239000-b523a000 ---p 00000000 00:00 0 
b523a000-b52ba000 rw-p 00000000 00:00 0 
b52ba000-b52bc000 r--s 0001d000 08:01 6297730    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
b52bc000-b52c1000 r--s 00044000 08:01 6297729    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
b52c1000-b52f4000 rw-p 00000000 00:00 0 
b52f4000-b5483000 r--s 038c2000 08:01 6297744    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b5483000-b5497000 rw-p 00000000 00:00 0 
b5497000-b54b1000 rw-p 00000000 00:00 0 
b54b1000-b54d2000 rw-p 00000000 00:00 0 
b54d2000-b555c000 rw-p 00000000 00:00 0 
b555c000-b556d000 rw-p 00000000 00:00 0 
b556d000-b55b1000 rw-p 00000000 00:00 0 
b55b1000-b55d2000 rw-p 00000000 00:00 0 
b55d2000-b565c000 rw-p 00000000 00:00 0 
b565c000-b5662000 rw-p 00000000 00:00 0 
b5662000-b567c000 rw-p 00000000 00:00 0 
b567c000-b5696000 rw-p 00000000 00:00 0 
b5696000-b5708000 rw-p 00000000 00:00 0 
b5708000-b5a88000 rwxp 00000000 00:00 0 
b5a88000-b7708000 rw-p 00000000 00:00 0 
b7708000-b770b000 ---p 00000000 00:00 0 
b770b000-b775b000 rw-p 00000000 00:00 0 
b775b000-b775e000 r--s 0000f000 08:01 6294240    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b775e000-b7760000 r--s 00014000 08:01 131085     /home/ben/Downloads/minecraft.jar
b7760000-b7768000 rw-s 00000000 08:01 393278     /tmp/hsperfdata_ben/8910
b7768000-b7769000 rw-p 00000000 00:00 0 
b7769000-b776a000 r--p 00000000 00:00 0 
b776a000-b776c000 rw-p 00000000 00:00 0 
bfcfd000-bfd33000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
java_command: /home/ben/Downloads/minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=ben
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3ea350], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3ea350], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30ca20], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.35 1.54 1.83

/proc/meminfo:
MemTotal:        2061692 kB
MemFree:           18248 kB
Buffers:           80496 kB
Cached:          1382300 kB
SwapCached:            0 kB
Active:           965492 kB
Inactive:         914988 kB
Active(anon):     281240 kB
Inactive(anon):   147320 kB
Active(file):     684252 kB
Inactive(file):   767668 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       1187784 kB
HighFree:           8928 kB
LowTotal:         873908 kB
LowFree:            9320 kB
SwapTotal:       6036472 kB
SwapFree:        6036472 kB
Dirty:               496 kB
Writeback:             0 kB
AnonPages:        417748 kB
Mapped:           114960 kB
Shmem:             10828 kB
Slab:              45084 kB
SReclaimable:      29944 kB
SUnreclaim:        15140 kB
KernelStack:        2128 kB
PageTables:         6032 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7067316 kB
Committed_AS:    1127488 kB
VmallocTotal:     122880 kB
VmallocUsed:       19672 kB
VmallocChunk:      97276 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      360440 kB
DirectMap4M:      548864 kB


CPU:total 1 (1 cores per cpu, 1 threads per core) family 6 model 10 stepping 0, cmov, cx8, fxsr, mmx, sse, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 2061692k(18248k free), swap 6036472k(6036472k free)

vm_info: OpenJDK Client VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Feb 23 2011 19:53:10 by "buildd" with gcc 4.4.3

time: Thu Mar 10 22:16:13 2011
elapsed time: 150 seconds

```
```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x01094416, pid=11434, tid=3040463728
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Client VM (19.0-b09 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.7-0ubuntu1~10.04.1
# Problematic frame:
# V  [libjvm.so+0x17d416]
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
#

---------------  T H R E A D  ---------------

Current thread (0x08873400):  VMThread [stack: 0xb531c000,0xb539d000] [id=11439]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000005

Registers:
EAX=0x00000005, EBX=0x01381ff4, ECX=0x01376788, EDX=0xb539bdc0
ESP=0xb539b970, EBP=0xb539b988, ESI=0xb539bdc0, EDI=0x7cfca0c8
EIP=0x01094416, CR2=0x00000005, EFLAGS=0x00210212

Register to memory mapping:

EAX=0x00000005
0x00000005 is pointing to unknown location

EBX=0x01381ff4
0x01381ff4: <offset 0x46aff4> in /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so at 0x00f17000

ECX=0x01376788
0x01376788: _ZTV15FastScanClosure+0x8 in /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so at 0x00f17000

EDX=0xb539bdc0
0xb539bdc0 is pointing to unknown location

ESP=0xb539b970
0xb539b970 is pointing to unknown location

EBP=0xb539b988
0xb539b988 is pointing to unknown location

ESI=0xb539bdc0
0xb539bdc0 is pointing to unknown location

EDI=0x7cfca0c8
dt 
 - klass: 'dt'


Top of Stack: (sp=0xb539b970)
0xb539b970:   b539ba4c 7cfca088 b539b9b8 01381ff4
0xb539b980:   7cfca0cc b539ba4c b539b9b8 010f168b
0xb539b990:   b539bdc0 7cfca0c8 8fdbd4a0 8fdbd4a0
0xb539b9a0:   949fe108 7cfca0d0 8fdbd4b8 8fdbd4a8
0xb539b9b0:   7cfca0d8 b539ba4c b539ba18 01284799
0xb539b9c0:   8fdbd338 7cfca0a8 b539ba4c 8fdbd330
0xb539b9d0:   0a87cac0 b539ba18 00001880 00000007
0xb539b9e0:   b539b9fc 00000013 7cfca0a8 00000007 

Instructions: (pc=0x01094416)
0x01094406:   7d 0c 8b 75 08 8b 07 85 c0 74 3b 39 46 20 76 36
0x01094416:   8b 10 83 e2 03 83 fa 03 74 38 52 52 50 8b 4e 1c 

Stack: [0xb531c000,0xb539d000],  sp=0xb539b970,  free space=510k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x17d416]
V  [libjvm.so+0x1da68b]
V  [libjvm.so+0x36d799]
V  [libjvm.so+0x36ae87]
V  [libjvm.so+0x36ad72]
V  [libjvm.so+0xf4d7e]
V  [libjvm.so+0xf2ee2]
V  [libjvm.so+0xf3151]
V  [libjvm.so+0xf45ac]
V  [libjvm.so+0x1c7cbc]
V  [libjvm.so+0x1c8036]
V  [libjvm.so+0xf3d87]
V  [libjvm.so+0x1bec1d]
V  [libjvm.so+0x17de5a]
V  [libjvm.so+0x1c0a6a]
V  [libjvm.so+0x134554]
V  [libjvm.so+0x1bdc4d]
V  [libjvm.so+0x3eab1f]
V  [libjvm.so+0x3f1dd1]
V  [libjvm.so+0x3f08ea]
V  [libjvm.so+0x3f0f0c]
V  [libjvm.so+0x3f1241]
V  [libjvm.so+0x311051]
C  [libpthread.so.0+0x596e]

VM_Operation (0xb4ef6bc8): GenCollectForAllocation, mode: safepoint, requested by thread 0x08974c00


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x08908400 JavaThread "Thread-28" [_thread_blocked, id=11772, stack(0xb4baf000,0xb4c00000)]
  0x088d0000 JavaThread "Thread-27" [_thread_blocked, id=11771, stack(0xb4927000,0xb4978000)]
  0x08ba6800 JavaThread "RuneScape applet" [_thread_blocked, id=11770, stack(0xb456e000,0xb45bf000)]
  0x08963400 JavaThread "Thread-26" [_thread_blocked, id=11769, stack(0xb4d57000,0xb4da8000)]
  0x088cd400 JavaThread "Thread-25" [_thread_blocked, id=11768, stack(0xb4d06000,0xb4d57000)]
  0x088fec00 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=11767, stack(0xb4b0d000,0xb4b5e000)]
  0x088c8c00 JavaThread "AWT-Shutdown" [_thread_blocked, id=11766, stack(0xb483d000,0xb488e000)]
  0xb4c02400 JavaThread "Thread-11" [_thread_blocked, id=11471, stack(0xb4a1a000,0xb4a6b000)]
  0xb4c01c00 JavaThread "Thread-10" [_thread_blocked, id=11470, stack(0xb4a6b000,0xb4abc000)]
  0x089ee400 JavaThread "Thread-5" [_thread_blocked, id=11462, stack(0xb4da8000,0xb4df9000)]
  0x089ed000 JavaThread "Thread-4" [_thread_blocked, id=11461, stack(0xb4df9000,0xb4e4a000)]
  0x08846000 JavaThread "DestroyJavaVM" [_thread_blocked, id=11437, stack(0xb77eb000,0xb783c000)]
  0x089ec000 JavaThread "Thread-3" [_thread_in_native, id=11460, stack(0xb4e4a000,0xb4e9b000)]
  0x08974c00 JavaThread "Thread-2" [_thread_blocked, id=11458, stack(0xb4ea7000,0xb4ef8000)]
  0x08967c00 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=11453, stack(0xb4f49000,0xb4f9a000)]
  0x08929c00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=11452, stack(0xb5036000,0xb5087000)]
  0x08882000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=11448, stack(0xb5111000,0xb5162000)]
  0x08880000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=11446, stack(0xb5162000,0xb51e3000)]
  0x0887e800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=11444, stack(0xb51e3000,0xb5234000)]
  0x08876800 JavaThread "Finalizer" daemon [_thread_blocked, id=11443, stack(0xb527a000,0xb52cb000)]
  0x08875000 JavaThread "Reference Handler" daemon [_thread_blocked, id=11441, stack(0xb52cb000,0xb531c000)]

Other Threads:
=>0x08873400 VMThread [stack: 0xb531c000,0xb539d000] [id=11439]
  0x0888e000 WatcherThread [stack: 0xb5090000,0xb5111000] [id=11450]

VM state:at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0x08843f78] Threads_lock - owner thread: 0x08873400
[0x08844388] Heap_lock - owner thread: 0x08974c00

Heap
 def new generation   total 46592K, used 41472K [0x6f940000, 0x72bc0000, 0x7a3e0000)
  eden space 41472K, 100% used [0x6f940000, 0x721c0000, 0x721c0000)
  from space 5120K,   0% used [0x726c0000, 0x726c0000, 0x72bc0000)
  to   space 5120K,   0% used [0x721c0000, 0x721c2100, 0x726c0000)
 tenured generation   total 103312K, used 45977K [0x7a3e0000, 0x808c4000, 0x8f940000)
   the space 103312K,  44% used [0x7a3e0000, 0x7d0c6700, 0x7d0c6800, 0x808c4000)
 compacting perm gen  total 12288K, used 9273K [0x8f940000, 0x90540000, 0x93940000)
   the space 12288K,  75% used [0x8f940000, 0x9024e7b0, 0x9024e800, 0x90540000)
    ro space 10240K,  73% used [0x93940000, 0x94098710, 0x94098800, 0x94340000)
    rw space 12288K,  60% used [0x94340000, 0x94a80f20, 0x94a81000, 0x94f40000)

Dynamic libraries:
00110000-00125000 r-xp 00000000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
00125000-00126000 r--p 00014000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
00126000-00127000 rw-p 00015000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
00127000-00129000 rw-p 00000000 00:00 0 
00129000-00130000 r-xp 00000000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00130000-00131000 r--p 00006000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00131000-00132000 rw-p 00007000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00132000-001b7000 r-xp 00000000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001b7000-001b8000 r--p 00084000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001b8000-001be000 rw-p 00085000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001be000-001e3000 rw-p 00000000 00:00 0 
001e4000-001f2000 r-xp 00000000 08:01 6294327    /usr/lib/libXext.so.6.4.0
001f2000-001f3000 r--p 0000d000 08:01 6294327    /usr/lib/libXext.so.6.4.0
001f3000-001f4000 rw-p 0000e000 08:01 6294327    /usr/lib/libXext.so.6.4.0
001f4000-001f8000 r-xp 00000000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
001f8000-001f9000 r--p 00003000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
001f9000-001fa000 rw-p 00004000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
001fa000-00202000 r-xp 00000000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00202000-00203000 r--p 00007000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00203000-00204000 rw-p 00008000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00204000-00208000 r-xp 00000000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
00208000-00209000 r--p 00003000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
00209000-0020a000 rw-p 00004000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
0020a000-00218000 r-xp 00000000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00218000-00219000 r--p 0000d000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00219000-0021a000 rw-p 0000e000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0021a000-0022f000 r-xp 00000000 08:01 6296555    /usr/lib/libnssutil3.so
0022f000-00232000 r--p 00014000 08:01 6296555    /usr/lib/libnssutil3.so
00232000-00233000 rw-p 00017000 08:01 6296555    /usr/lib/libnssutil3.so
00233000-00235000 r-xp 00000000 08:01 6291780    /usr/lib/libplds4.so
00235000-00236000 r--p 00001000 08:01 6291780    /usr/lib/libplds4.so
00236000-00237000 rw-p 00002000 08:01 6291780    /usr/lib/libplds4.so
00237000-0024b000 r-xp 00000000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
0024b000-0024c000 r--p 00013000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
0024c000-0024d000 rw-p 00014000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
0024d000-0024f000 r-xp 00000000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
0024f000-00250000 r--p 00001000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
00250000-00251000 rw-p 00002000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
00251000-00255000 r-xp 00000000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00255000-00256000 r--p 00004000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00256000-00257000 rw-p 00005000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00257000-00260000 r-xp 00000000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
00260000-00261000 r--p 00008000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
00261000-00262000 rw-p 00009000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
00262000-00263000 r-xp 00000000 08:01 6299070    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsound.so
00263000-00264000 r--p 00000000 08:01 6299070    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsound.so
00264000-00265000 rw-p 00001000 08:01 6299070    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsound.so
00269000-00284000 r-xp 00000000 08:01 8519683    /lib/ld-2.11.1.so
00284000-00285000 r--p 0001a000 08:01 8519683    /lib/ld-2.11.1.so
00285000-00286000 rw-p 0001b000 08:01 8519683    /lib/ld-2.11.1.so
00286000-003d9000 r-xp 00000000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
003d9000-003da000 ---p 00153000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
003da000-003dc000 r--p 00153000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
003dc000-003dd000 rw-p 00155000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
003dd000-003e0000 rw-p 00000000 00:00 0 
003e0000-003f0000 r-xp 00000000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
003f0000-003f1000 r--p 00010000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
003f1000-003f2000 rw-p 00011000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
003f2000-003f4000 rw-p 00000000 00:00 0 
003f4000-003f7000 r-xp 00000000 08:01 8520571    /lib/libuuid.so.1.3.0
003f7000-003f8000 r--p 00002000 08:01 8520571    /lib/libuuid.so.1.3.0
003f8000-003f9000 rw-p 00003000 08:01 8520571    /lib/libuuid.so.1.3.0
003fd000-00410000 r-xp 00000000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00410000-00411000 r--p 00012000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00411000-00412000 rw-p 00013000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00412000-00414000 rw-p 00000000 00:00 0 
00414000-00445000 r-xp 00000000 08:01 6291778    /usr/lib/libnspr4.so
00445000-00446000 r--p 00030000 08:01 6291778    /usr/lib/libnspr4.so
00446000-00447000 rw-p 00031000 08:01 6291778    /usr/lib/libnspr4.so
00447000-00449000 rw-p 00000000 00:00 0 
00449000-00466000 r-xp 00000000 08:01 6299079    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
00466000-00467000 ---p 0001d000 08:01 6299079    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
00467000-00468000 r--p 0001d000 08:01 6299079    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
00468000-00469000 rw-p 0001e000 08:01 6299079    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
00469000-0046e000 rw-p 00000000 00:00 0 
0046e000-00475000 r-xp 00000000 08:01 8519873    /lib/libwrap.so.0.7.6
00475000-00476000 r--p 00006000 08:01 8519873    /lib/libwrap.so.0.7.6
00476000-00477000 rw-p 00007000 08:01 8519873    /lib/libwrap.so.0.7.6
0047b000-00485000 r-xp 00000000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00485000-00486000 r--p 00009000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00486000-00487000 rw-p 0000a000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00489000-00497000 r-xp 00000000 08:01 6301154    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsoundalsa.so
00497000-00498000 r--p 0000d000 08:01 6301154    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsoundalsa.so
00498000-00499000 rw-p 0000e000 08:01 6301154    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsoundalsa.so
00499000-0049e000 r-xp 00000000 08:01 6295038    /usr/lib/libogg.so.0.6.0
0049e000-0049f000 r--p 00004000 08:01 6295038    /usr/lib/libogg.so.0.6.0
0049f000-004a0000 rw-p 00005000 08:01 6295038    /usr/lib/libogg.so.0.6.0
004a0000-004a5000 r-xp 00000000 08:01 6295659    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
004a5000-004a6000 r--p 00004000 08:01 6295659    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
004a6000-004a7000 rw-p 00005000 08:01 6295659    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
004a7000-004ae000 r-xp 00000000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
004ae000-004af000 r--p 00006000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
004af000-004b0000 rw-p 00007000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
004b0000-004cf000 r-xp 00000000 08:01 6294923    /usr/lib/libjpeg.so.62.0.0
004cf000-004d0000 r--p 0001e000 08:01 6294923    /usr/lib/libjpeg.so.62.0.0
004d0000-004d1000 rw-p 0001f000 08:01 6294923    /usr/lib/libjpeg.so.62.0.0
004d9000-004e0000 r-xp 00000000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
004e0000-004e1000 r--p 00006000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
004e1000-004e2000 rw-p 00007000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
004e2000-00553000 r-xp 00000000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
00553000-00557000 r--p 00070000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
00557000-00558000 rw-p 00074000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
00558000-0056d000 r-xp 00000000 08:01 6294279    /usr/lib/libICE.so.6.3.0
0056d000-0056e000 r--p 00014000 08:01 6294279    /usr/lib/libICE.so.6.3.0
0056e000-0056f000 rw-p 00015000 08:01 6294279    /usr/lib/libICE.so.6.3.0
0056f000-00571000 rw-p 00000000 00:00 0 
00574000-0057a000 r-xp 00000000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
0057a000-0057b000 r--p 00006000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
0057b000-0057c000 rw-p 00007000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
0057c000-005b1000 r-xp 00000000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
005b1000-005b2000 r--p 00035000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
005b2000-005b3000 rw-p 00036000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
005b3000-005ea000 r-xp 00000000 08:01 8519733    /lib/libdbus-1.so.3.4.0
005ea000-005eb000 r--p 00036000 08:01 8519733    /lib/libdbus-1.so.3.4.0
005eb000-005ec000 rw-p 00037000 08:01 8519733    /lib/libdbus-1.so.3.4.0
005ee000-005fa000 r-xp 00000000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
005fa000-005fb000 r--p 0000b000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
005fb000-005fc000 rw-p 0000c000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
005fc000-00644000 r-xp 00000000 08:01 6295024    /usr/lib/nss/libfreebl3.so
00644000-00645000 r--p 00047000 08:01 6295024    /usr/lib/nss/libfreebl3.so
00645000-00646000 rw-p 00048000 08:01 6295024    /usr/lib/nss/libfreebl3.so
00646000-0064a000 rw-p 00000000 00:00 0 
00652000-0065a000 r-xp 00000000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
0065a000-0065b000 r--p 00007000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
0065b000-0065c000 rw-p 00008000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
0065c000-00667000 r-xp 00000000 08:01 6301155    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libpulse-java.so
00667000-00668000 r--p 0000a000 08:01 6301155    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libpulse-java.so
00668000-00669000 rw-p 0000b000 08:01 6301155    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libpulse-java.so
00678000-0067c000 r-xp 00000000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
0067c000-0067d000 r--p 00003000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
0067d000-0067e000 rw-p 00004000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
0067e000-006fe000 r-xp 00000000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
006fe000-006ff000 r--p 0007f000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
006ff000-00700000 rw-p 00080000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
00700000-00701000 rw-p 00000000 00:00 0 
00728000-0072e000 r-xp 00000000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
0072e000-0072f000 r--p 00005000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
0072f000-00730000 rw-p 00006000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
00730000-00757000 r-xp 00000000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00757000-00758000 r--p 00026000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00758000-00759000 rw-p 00027000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00759000-0076c000 r-xp 00000000 08:01 8519878    /lib/libz.so.1.2.3.3
0076c000-0076d000 r--p 00012000 08:01 8519878    /lib/libz.so.1.2.3.3
0076d000-0076e000 rw-p 00013000 08:01 8519878    /lib/libz.so.1.2.3.3
0076e000-007ae000 r-xp 00000000 08:01 6295132    /usr/lib/libpulse.so.0.12.2
007ae000-007af000 r--p 00040000 08:01 6295132    /usr/lib/libpulse.so.0.12.2
007af000-007b0000 rw-p 00041000 08:01 6295132    /usr/lib/libpulse.so.0.12.2
007ce000-007f2000 r-xp 00000000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
007f2000-007f3000 r--p 00023000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
007f3000-007f4000 rw-p 00024000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
007f4000-0083d000 r-xp 00000000 08:01 6295133    /usr/lib/libpulsecommon-0.9.21.so
0083d000-0083e000 r--p 00048000 08:01 6295133    /usr/lib/libpulsecommon-0.9.21.so
0083e000-0083f000 rw-p 00049000 08:01 6295133    /usr/lib/libpulsecommon-0.9.21.so
00844000-0084b000 r-xp 00000000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
0084b000-0084c000 r--p 00006000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
0084c000-0084d000 rw-p 00007000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
00853000-00855000 r-xp 00000000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00855000-00856000 r--p 00001000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00856000-00857000 rw-p 00002000 08:01 6294314    /usr/lib/libXau.so.6.0.0
00857000-008b8000 r-xp 00000000 08:01 6295192    /usr/lib/libsndfile.so.1.0.21
008b8000-008b9000 ---p 00061000 08:01 6295192    /usr/lib/libsndfile.so.1.0.21
008b9000-008ba000 r--p 00061000 08:01 6295192    /usr/lib/libsndfile.so.1.0.21
008ba000-008bb000 rw-p 00062000 08:01 6295192    /usr/lib/libsndfile.so.1.0.21
008bb000-008bf000 rw-p 00000000 00:00 0 
008cf000-008f3000 r-xp 00000000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
008f3000-008f4000 r--p 00023000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
008f4000-008f6000 rw-p 00024000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0092f000-00974000 r-xp 00000000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00974000-00975000 r--p 00044000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00975000-00977000 rw-p 00045000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00977000-00978000 rw-p 00000000 00:00 0 
0097a000-00981000 r-xp 00000000 08:01 6294308    /usr/lib/libSM.so.6.0.1
00981000-00982000 r--p 00006000 08:01 6294308    /usr/lib/libSM.so.6.0.1
00982000-00983000 rw-p 00007000 08:01 6294308    /usr/lib/libSM.so.6.0.1
009b6000-009b9000 r-xp 00000000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
009b9000-009ba000 r--p 00003000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
009ba000-009bb000 rw-p 00004000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
009bb000-00ad4000 r-xp 00000000 08:01 6294310    /usr/lib/libX11.so.6.3.0
00ad4000-00ad5000 r--p 00118000 08:01 6294310    /usr/lib/libX11.so.6.3.0
00ad5000-00ad7000 rw-p 00119000 08:01 6294310    /usr/lib/libX11.so.6.3.0
00ad7000-00ad8000 rw-p 00000000 00:00 0 
00ad8000-00b23000 r-xp 00000000 08:01 6294264    /usr/lib/libFLAC.so.8.2.0
00b23000-00b24000 r--p 0004a000 08:01 6294264    /usr/lib/libFLAC.so.8.2.0
00b24000-00b25000 rw-p 0004b000 08:01 6294264    /usr/lib/libFLAC.so.8.2.0
00b51000-00b95000 r-xp 00000000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00b95000-00b97000 r--p 00043000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00b97000-00b98000 rw-p 00045000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00b98000-00b9d000 rw-p 00000000 00:00 0 
00b9d000-00cab000 r-xp 00000000 08:01 6296556    /usr/lib/libnss3.so
00cab000-00cac000 ---p 0010e000 08:01 6296556    /usr/lib/libnss3.so
00cac000-00caf000 r--p 0010e000 08:01 6296556    /usr/lib/libnss3.so
00caf000-00cb1000 rw-p 00111000 08:01 6296556    /usr/lib/libnss3.so
00cc7000-00cca000 r-xp 00000000 08:01 6291779    /usr/lib/libplc4.so
00cca000-00ccb000 r--p 00002000 08:01 6291779    /usr/lib/libplc4.so
00ccb000-00ccc000 rw-p 00003000 08:01 6291779    /usr/lib/libplc4.so
00cea000-00cf2000 r-xp 00000000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00cf2000-00cf3000 r--p 00007000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00cf3000-00cf4000 rw-p 00008000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00d23000-00d2f000 r-xp 00000000 08:01 6294335    /usr/lib/libXi.so.6.1.0
00d2f000-00d30000 r--p 0000c000 08:01 6294335    /usr/lib/libXi.so.6.1.0
00d30000-00d31000 rw-p 0000d000 08:01 6294335    /usr/lib/libXi.so.6.1.0
00d31000-00df4000 r-xp 00000000 08:01 6294394    /usr/lib/libasound.so.2.0.0
00df4000-00df8000 r--p 000c2000 08:01 6294394    /usr/lib/libasound.so.2.0.0
00df8000-00df9000 rw-p 000c6000 08:01 6294394    /usr/lib/libasound.so.2.0.0
00dff000-00e17000 r-xp 00000000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00e17000-00e18000 r--p 00017000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00e18000-00e19000 rw-p 00018000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00e60000-00e62000 r-xp 00000000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00e62000-00e63000 r--p 00001000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00e63000-00e64000 rw-p 00002000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00e91000-00eae000 r-xp 00000000 08:01 8519763    /lib/libgcc_s.so.1
00eae000-00eaf000 r--p 0001c000 08:01 8519763    /lib/libgcc_s.so.1
00eaf000-00eb0000 rw-p 0001d000 08:01 8519763    /lib/libgcc_s.so.1
00f16000-00f17000 r-xp 00000000 00:00 0          [vdso]
00f17000-0136a000 r-xp 00000000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0136a000-0136b000 ---p 00453000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0136b000-01382000 r--p 00453000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01382000-0138f000 rw-p 0046a000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0138f000-017ab000 rw-p 00000000 00:00 0 
073a8000-07494000 r-xp 00000000 08:01 6295282    /usr/lib/libvorbisenc.so.2.0.6
07494000-07495000 ---p 000ec000 08:01 6295282    /usr/lib/libvorbisenc.so.2.0.6
07495000-074a3000 r--p 000ec000 08:01 6295282    /usr/lib/libvorbisenc.so.2.0.6
074a3000-074a4000 rw-p 000fa000 08:01 6295282    /usr/lib/libvorbisenc.so.2.0.6
08048000-08051000 r-xp 00000000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08840000-0a8a1000 rw-p 00000000 00:00 0          [heap]
6f940000-72bc0000 rw-p 00000000 00:00 0 
72bc0000-7a3e0000 rw-p 00000000 00:00 0 
7a3e0000-808c4000 rw-p 00000000 00:00 0 
808c4000-8f940000 rw-p 00000000 00:00 0 
8f940000-90540000 rw-p 00000000 00:00 0 
90540000-93940000 rw-p 00000000 00:00 0 
93940000-94099000 r--s 00001000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94099000-94340000 rw-p 00000000 00:00 0 
94340000-94a81000 rw-p 0075a000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94a81000-94f40000 rw-p 00000000 00:00 0 
94f40000-9503b000 rw-p 00e9b000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
9503b000-95340000 rw-p 00000000 00:00 0 
95340000-95348000 r-xs 00f96000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
95348000-95740000 rw-p 00000000 00:00 0 
af200000-af2ee000 rw-p 00000000 00:00 0 
af2ee000-af300000 ---p 00000000 00:00 0 
af300000-af349000 rw-p 00000000 00:00 0 
af349000-af400000 ---p 00000000 00:00 0 
af400000-af4f9000 rw-p 00000000 00:00 0 
af4f9000-af500000 ---p 00000000 00:00 0 
af500000-af5fc000 rw-p 00000000 00:00 0 
af5fc000-af600000 ---p 00000000 00:00 0 
af600000-af6fd000 rw-p 00000000 00:00 0 
af6fd000-af700000 ---p 00000000 00:00 0 
af700000-af800000 rw-p 00000000 00:00 0 
af800000-af900000 rw-p 00000000 00:00 0 
af94d000-af94e000 ---p 00000000 00:00 0 
af94e000-b014e000 rw-p 00000000 00:00 0 
b014e000-b414f000 rw-s 00000000 00:10 4027655    /dev/shm/pulse-shm-2755880854
b414f000-b456e000 rw-s 00000000 00:04 29327387   /SYSV00000000 (deleted)
b456e000-b4571000 ---p 00000000 00:00 0 
b4571000-b45bf000 rw-p 00000000 00:00 0 
b474a000-b474d000 ---p 00000000 00:00 0 
b474d000-b479b000 rw-p 00000000 00:00 0 
b479b000-b479e000 ---p 00000000 00:00 0 
b479e000-b47ec000 rw-p 00000000 00:00 0 
b47ec000-b47ef000 ---p 00000000 00:00 0 
b47ef000-b483d000 rw-p 00000000 00:00 0 
b483d000-b4840000 ---p 00000000 00:00 0 
b4840000-b488e000 rw-p 00000000 00:00 0 
b4927000-b492a000 ---p 00000000 00:00 0 
b492a000-b4978000 rw-p 00000000 00:00 0 
b4978000-b497b000 ---p 00000000 00:00 0 
b497b000-b49c9000 rw-p 00000000 00:00 0 
b49c9000-b49cc000 ---p 00000000 00:00 0 
b49cc000-b4a1a000 rw-p 00000000 00:00 0 
b4a1a000-b4a1d000 ---p 00000000 00:00 0 
b4a1d000-b4a6b000 rw-p 00000000 00:00 0 
b4a6b000-b4a6e000 ---p 00000000 00:00 0 
b4a6e000-b4abc000 rw-p 00000000 00:00 0 
b4abc000-b4abf000 ---p 00000000 00:00 0 
b4abf000-b4b0d000 rw-p 00000000 00:00 0 
b4b0d000-b4b10000 ---p 00000000 00:00 0 
b4b10000-b4b5e000 rw-p 00000000 00:00 0 
b4b5e000-b4b61000 ---p 00000000 00:00 0 
b4b61000-b4baf000 rw-p 00000000 00:00 0 
b4baf000-b4bb2000 ---p 00000000 00:00 0 
b4bb2000-b4c00000 rw-p 00000000 00:00 0 
b4c00000-b4cfc000 rw-p 00000000 00:00 0 
b4cfc000-b4d00000 ---p 00000000 00:00 0 
b4d04000-b4d06000 r--s 00007000 08:01 8143599    /home/ben/.icedteaplugin/cache/http/world80.runescape.com/loader-1288657538.jar
b4d06000-b4d09000 ---p 00000000 00:00 0 
b4d09000-b4d57000 rw-p 00000000 00:00 0 
b4d57000-b4d5a000 ---p 00000000 00:00 0 
b4d5a000-b4da8000 rw-p 00000000 00:00 0 
b4da8000-b4dab000 ---p 00000000 00:00 0 
b4dab000-b4df9000 rw-p 00000000 00:00 0 
b4df9000-b4dfc000 ---p 00000000 00:00 0 
b4dfc000-b4e4a000 rw-p 00000000 00:00 0 
b4e4a000-b4e4d000 ---p 00000000 00:00 0 
b4e4d000-b4e9b000 rw-p 00000000 00:00 0 
b4e9b000-b4e9e000 r--s 00038000 08:01 6294065    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
b4e9e000-b4ea0000 r--s 00013000 08:01 6297724    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
b4ea0000-b4ea3000 r--s 00031000 08:01 6294190    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
b4ea3000-b4ea7000 r--s 0007c000 08:01 6297725    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
b4ea7000-b4eaa000 ---p 00000000 00:00 0 
b4eaa000-b4ef8000 rw-p 00000000 00:00 0 
b4ef8000-b4efb000 ---p 00000000 00:00 0 
b4efb000-b4f49000 rw-p 00000000 00:00 0 
b4f49000-b4f4c000 ---p 00000000 00:00 0 
b4f4c000-b4f9a000 rw-p 00000000 00:00 0 
b4f9a000-b4fa0000 r--s 000fc000 08:01 6297732    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
b4fa0000-b4fa1000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4fa1000-b4fa2000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4fa2000-b4fa8000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4fa8000-b4faa000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4faa000-b4fad000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4fad000-b4fb3000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4fb3000-b4fb4000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4fb4000-b4fb7000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4fb7000-b4fb8000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4fb8000-b4fb9000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4fb9000-b4fba000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4fba000-b4fbe000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4fbe000-b4fc2000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4fc2000-b4fc9000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4fc9000-b4fd4000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4fd4000-b4fd7000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4fd7000-b4fd8000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4fd8000-b4fe0000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4fe0000-b4fe8000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4fe8000-b4feb000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4feb000-b4fec000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4fec000-b4fed000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4fed000-b4ff3000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4ff3000-b4ff5000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4ff5000-b4ff8000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4ff8000-b4ffe000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4ffe000-b4fff000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4fff000-b5002000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b5002000-b5003000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b5003000-b5004000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b5004000-b5005000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b5005000-b5009000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b5009000-b500d000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b500d000-b5014000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b5014000-b501f000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b501f000-b5022000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b5022000-b5023000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b5023000-b502b000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b502b000-b5033000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b5033000-b5036000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b5036000-b5039000 ---p 00000000 00:00 0 
b5039000-b5087000 rw-p 00000000 00:00 0 
b5087000-b5090000 r--s 00065000 08:01 6692486    /usr/share/java/gnome-java-bridge.jar
b5090000-b5091000 ---p 00000000 00:00 0 
b5091000-b5111000 rw-p 00000000 00:00 0 
b5111000-b5114000 ---p 00000000 00:00 0 
b5114000-b5162000 rw-p 00000000 00:00 0 
b5162000-b5165000 ---p 00000000 00:00 0 
b5165000-b51e3000 rw-p 00000000 00:00 0 
b51e3000-b51e6000 ---p 00000000 00:00 0 
b51e6000-b5234000 rw-p 00000000 00:00 0 
b5234000-b523b000 r--s 00000000 08:01 6292678    /usr/lib/gconv/gconv-modules.cache
b523b000-b527a000 r--p 00000000 08:01 6422640    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b527a000-b527d000 ---p 00000000 00:00 0 
b527d000-b52cb000 rw-p 00000000 00:00 0 
b52cb000-b52ce000 ---p 00000000 00:00 0 
b52ce000-b531c000 rw-p 00000000 00:00 0 
b531c000-b531d000 ---p 00000000 00:00 0 
b531d000-b539d000 rw-p 00000000 00:00 0 
b539d000-b539f000 r--s 0001d000 08:01 6297730    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
b539f000-b53a4000 r--s 00044000 08:01 6297729    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
b53a4000-b53d7000 rw-p 00000000 00:00 0 
b53d7000-b5566000 r--s 038c2000 08:01 6297744    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b5566000-b557a000 rw-p 00000000 00:00 0 
b557a000-b5594000 rw-p 00000000 00:00 0 
b5594000-b55c7000 rw-p 00000000 00:00 0 
b55c7000-b563f000 rw-p 00000000 00:00 0 
b563f000-b5659000 rw-p 00000000 00:00 0 
b5659000-b5694000 rw-p 00000000 00:00 0 
b5694000-b56c7000 rw-p 00000000 00:00 0 
b56c7000-b573f000 rw-p 00000000 00:00 0 
b573f000-b5745000 rw-p 00000000 00:00 0 
b5745000-b575f000 rw-p 00000000 00:00 0 
b575f000-b57a2000 rw-p 00000000 00:00 0 
b57a2000-b57eb000 rw-p 00000000 00:00 0 
b57eb000-b65ab000 rwxp 00000000 00:00 0 
b65ab000-b77eb000 rw-p 00000000 00:00 0 
b77eb000-b77ee000 ---p 00000000 00:00 0 
b77ee000-b783f000 rw-p 00000000 00:00 0 
b783f000-b7840000 r--p 00000000 00:00 0 
b7840000-b7843000 r--s 0000f000 08:01 6294240    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b7843000-b784b000 rw-s 00000000 08:01 393290     /tmp/hsperfdata_ben/11434
b784b000-b784c000 rw-p 00000000 00:00 0 
b784c000-b784d000 ---p 00000000 00:00 0 
b784d000-b784f000 rw-p 00000000 00:00 0 
bfe19000-bfe2e000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
java_command: sun.applet.PluginMain /tmp/icedteaplugin-ben/8841-icedteanp-plugin-to-appletviewer /tmp/icedteaplugin-ben/8841-icedteanp-appletviewer-to-plugin
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=ben
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3ea350], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3ea350], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30ca20], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.94 1.50 1.86

/proc/meminfo:
MemTotal:        2061692 kB
MemFree:           71740 kB
Buffers:           83284 kB
Cached:          1398888 kB
SwapCached:            0 kB
Active:          1014392 kB
Inactive:         906036 kB
Active(anon):     310460 kB
Inactive(anon):   137796 kB
Active(file):     703932 kB
Inactive(file):   768240 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       1187784 kB
HighFree:           8556 kB
LowTotal:         873908 kB
LowFree:           63184 kB
SwapTotal:       6036472 kB
SwapFree:        6036472 kB
Dirty:               404 kB
Writeback:             0 kB
AnonPages:        438276 kB
Mapped:           109884 kB
Shmem:              9996 kB
Slab:              43124 kB
SReclaimable:      32148 kB
SUnreclaim:        10976 kB
KernelStack:        2096 kB
PageTables:         5432 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7067316 kB
Committed_AS:    1110444 kB
VmallocTotal:     122880 kB
VmallocUsed:       19672 kB
VmallocChunk:      97276 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      360440 kB
DirectMap4M:      548864 kB


CPU:total 1 (1 cores per cpu, 1 threads per core) family 6 model 10 stepping 0, cmov, cx8, fxsr, mmx, sse, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 2061692k(71740k free), swap 6036472k(6036472k free)

vm_info: OpenJDK Client VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Feb 23 2011 19:53:10 by "buildd" with gcc 4.4.3

time: Thu Mar 10 23:13:23 2011
elapsed time: 2365 seconds

```

---

### Post by clooless001 on 2011-03-11
Last code ...
```
 #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x548ae830, pid=11777, tid=3033123696
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Client VM (19.0-b09 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.7-0ubuntu1~10.04.1
# Problematic frame:
# C  0x548ae830
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
#

---------------  T H R E A D  ---------------

Current thread (0x09962800):  JavaThread "Thread-30" daemon [_thread_in_Java, id=11880, stack(0xb4c4c000,0xb4c9d000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x548ae830

Registers:
EAX=0x00000000, EBX=0x000000c0, ECX=0x00000108, EDX=0x00000054
ESP=0xb4c9a7fc, EBP=0xb4c9a81c, ESI=0x90156576, EDI=0xb4c9a82c
EIP=0x548ae830, CR2=0x548ae830, EFLAGS=0x00210282

Register to memory mapping:

EAX=0x00000000
0x00000000 is pointing to unknown location

EBX=0x000000c0
0x000000c0 is pointing to unknown location

ECX=0x00000108
0x00000108 is pointing to unknown location

EDX=0x00000054
0x00000054 is pointing to unknown location

ESP=0xb4c9a7fc
0xb4c9a7fc is pointing into the stack for thread: 0x09962800
"Thread-30" daemon prio=10 tid=0x09962800 nid=0x2e68 runnable [0x00000000]
   java.lang.Thread.State: RUNNABLE

EBP=0xb4c9a81c
0xb4c9a81c is pointing into the stack for thread: 0x09962800
"Thread-30" daemon prio=10 tid=0x09962800 nid=0x2e68 runnable [0x00000000]
   java.lang.Thread.State: RUNNABLE

ESI=0x90156576
{constMethod} 
 - klass: {other class}
 - method:       0x901565b0 {method} 'a' '(Lha;)V' in 'l'
 - exceptions:   0x93940078
bci_from(0x90156576) = 22; print_codes():

EDI=0xb4c9a82c
0xb4c9a82c is pointing into the stack for thread: 0x09962800
"Thread-30" daemon prio=10 tid=0x09962800 nid=0x2e68 runnable [0x00000000]
   java.lang.Thread.State: RUNNABLE


Top of Stack: (sp=0xb4c9a7fc)
0xb4c9a7fc:   b4c9a7fc 90156573 b4c9a82c 9045f0f8
0xb4c9a80c:   00000000 901565b0 00000000 b4c9a830
0xb4c9a81c:   b4c9bf74 b623646e 00000000 7b9df068
0xb4c9a82c:   71563de8 00000000 00000002 7cbbb350
0xb4c9a83c:   00000080 00000016 00000087 000019e3
0xb4c9a84c:   0000000f 00000087 00000016 00000000
0xb4c9a85c:   7b9df068 ffffffea 46711003 47200000
0xb4c9a86c:   c4980000 471e0000 4607951d 90253398 

Instructions: (pc=0x548ae830)
0x548ae820:   
[error occurred during error reporting (printing registers, top of stack, instructions near pc), id 0xb]

Stack: [0xb4c4c000,0xb4c9d000],  sp=0xb4c9a7fc,  free space=313k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  0x548ae830
J  hi.a(ILha;)V
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub
V  [libjvm.so+0x209a92]
V  [libjvm.so+0x30a609]
V  [libjvm.so+0x2089cf]
V  [libjvm.so+0x20951a]
V  [libjvm.so+0x209678]
V  [libjvm.so+0x253e41]
V  [libjvm.so+0x3bb43c]
V  [libjvm.so+0x3bb502]
V  [libjvm.so+0x311051]
C  [libpthread.so.0+0x596e]


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x087ff400 JavaThread "Thread-37" daemon [_thread_blocked, id=11909, stack(0xb4b59000,0xb4baa000)]
  0x09afb000 JavaThread "Thread-36" daemon [_thread_in_native, id=11908, stack(0xb496f000,0xb49c0000)]
  0x09cdec00 JavaThread "Thread-32" daemon [_thread_blocked, id=11882, stack(0xb4e8f000,0xb4ee0000)]
  0x089a6800 JavaThread "Thread-31" daemon [_thread_blocked, id=11881, stack(0xb4cee000,0xb4d3f000)]
=>0x09962800 JavaThread "Thread-30" daemon [_thread_in_Java, id=11880, stack(0xb4c4c000,0xb4c9d000)]
  0x08953000 JavaThread "Thread-29" daemon [_thread_blocked, id=11879, stack(0xb4baa000,0xb4bfb000)]
  0x0897d000 JavaThread "Thread-23" [_thread_blocked, id=11866, stack(0xb4c9d000,0xb4cee000)]
  0x088de400 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=11865, stack(0xb4417000,0xb4468000)]
  0x089e0800 JavaThread "AWT-Shutdown" [_thread_blocked, id=11864, stack(0xb4a66000,0xb4ab7000)]
  0x0899dc00 JavaThread "Thread-10" [_thread_blocked, id=11804, stack(0xb4ab7000,0xb4b08000)]
  0x0899b000 JavaThread "Thread-9" [_thread_blocked, id=11803, stack(0xb4b08000,0xb4b59000)]
  0x08887000 JavaThread "Thread-5" [_thread_blocked, id=11796, stack(0xb4d3f000,0xb4d90000)]
  0x08885c00 JavaThread "Thread-4" [_thread_blocked, id=11795, stack(0xb4d90000,0xb4de1000)]
  0x086e2000 JavaThread "DestroyJavaVM" [_thread_blocked, id=11778, stack(0xb7782000,0xb77d3000)]
  0x08884c00 JavaThread "Thread-3" [_thread_in_native, id=11794, stack(0xb4de1000,0xb4e32000)]
  0x08810c00 JavaThread "Thread-2" [_thread_blocked, id=11792, stack(0xb4e3e000,0xb4e8f000)]
  0x08804000 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=11787, stack(0xb4ee0000,0xb4f31000)]
  0x087c5c00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=11786, stack(0xb4fcd000,0xb501e000)]
  0x0871e000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=11784, stack(0xb50a8000,0xb50f9000)]
  0x0871c000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=11783, stack(0xb50f9000,0xb517a000)]
  0x0871a800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=11782, stack(0xb517a000,0xb51cb000)]
  0x08712800 JavaThread "Finalizer" daemon [_thread_blocked, id=11781, stack(0xb5211000,0xb5262000)]
  0x08711000 JavaThread "Reference Handler" daemon [_thread_blocked, id=11780, stack(0xb5262000,0xb52b3000)]

Other Threads:
  0x0870f400 VMThread [stack: 0xb52b3000,0xb5334000] [id=11779]
  0x0872a000 WatcherThread [stack: 0xb5027000,0xb50a8000] [id=11785]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 28224K, used 24024K [0x6f940000, 0x717e0000, 0x7a3e0000)
  eden space 25088K,  83% used [0x6f940000, 0x70da6118, 0x711c0000)
  from space 3136K, 100% used [0x714d0000, 0x717e0000, 0x717e0000)
  to   space 3136K,   0% used [0x711c0000, 0x711c0000, 0x714d0000)
 tenured generation   total 62640K, used 54554K [0x7a3e0000, 0x7e10c000, 0x8f940000)
   the space 62640K,  87% used [0x7a3e0000, 0x7d926968, 0x7d926a00, 0x7e10c000)
 compacting perm gen  total 12288K, used 11427K [0x8f940000, 0x90540000, 0x93940000)
   the space 12288K,  93% used [0x8f940000, 0x90468f70, 0x90469000, 0x90540000)
    ro space 10240K,  73% used [0x93940000, 0x94098710, 0x94098800, 0x94340000)
    rw space 12288K,  60% used [0x94340000, 0x94a80f20, 0x94a81000, 0x94f40000)

Dynamic libraries:
00110000-00263000 r-xp 00000000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00263000-00264000 ---p 00153000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00264000-00266000 r--p 00153000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00266000-00267000 rw-p 00155000 08:01 8653396    /lib/tls/i686/cmov/libc-2.11.1.so
00267000-0026a000 rw-p 00000000 00:00 0 
0026a000-00271000 r-xp 00000000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00271000-00272000 r--p 00006000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00272000-00273000 rw-p 00007000 08:01 6299083    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00273000-00279000 r-xp 00000000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00279000-0027a000 r--p 00006000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
0027a000-0027b000 rw-p 00007000 08:01 8653403    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
0027b000-00300000 r-xp 00000000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00300000-00301000 r--p 00084000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00301000-00307000 rw-p 00085000 08:01 6299052    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00307000-0032c000 rw-p 00000000 00:00 0 
0032d000-00337000 r-xp 00000000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00337000-00338000 r--p 00009000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00338000-00339000 rw-p 0000a000 08:01 8653405    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00339000-0037d000 r-xp 00000000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
0037d000-0037f000 r--p 00043000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
0037f000-00380000 rw-p 00045000 08:01 6299054    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00380000-00385000 rw-p 00000000 00:00 0 
00385000-003f6000 r-xp 00000000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
003f6000-003fa000 r--p 00070000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
003fa000-003fb000 rw-p 00074000 08:01 6291967    /usr/lib/libfreetype.so.6.3.22
003fb000-00418000 r-xp 00000000 08:01 8519763    /lib/libgcc_s.so.1
00418000-00419000 r--p 0001c000 08:01 8519763    /lib/libgcc_s.so.1
00419000-0041a000 rw-p 0001d000 08:01 8519763    /lib/libgcc_s.so.1
0041a000-00422000 r-xp 00000000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00422000-00423000 r--p 00007000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00423000-00424000 rw-p 00008000 08:01 6294321    /usr/lib/libXcursor.so.1.0.2
00424000-00428000 r-xp 00000000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
00428000-00429000 r--p 00003000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
00429000-0042a000 rw-p 00004000 08:01 6294329    /usr/lib/libXfixes.so.3.1.0
0042a000-0042c000 r-xp 00000000 08:01 6291780    /usr/lib/libplds4.so
0042c000-0042d000 r--p 00001000 08:01 6291780    /usr/lib/libplds4.so
0042d000-0042e000 rw-p 00002000 08:01 6291780    /usr/lib/libplds4.so
0042e000-0045f000 r-xp 00000000 08:01 6291778    /usr/lib/libnspr4.so
0045f000-00460000 r--p 00030000 08:01 6291778    /usr/lib/libnspr4.so
00460000-00461000 rw-p 00031000 08:01 6291778    /usr/lib/libnspr4.so
00461000-00463000 rw-p 00000000 00:00 0 
00463000-00498000 r-xp 00000000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
00498000-00499000 r--p 00035000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
00499000-0049a000 rw-p 00036000 08:01 6296531    /usr/lib/nss/libsoftokn3.so
0049a000-004ae000 r-xp 00000000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
004ae000-004af000 r--p 00013000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
004af000-004b0000 rw-p 00014000 08:01 6299074    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
004b2000-004b6000 r-xp 00000000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
004b6000-004b7000 r--p 00003000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
004b7000-004b8000 rw-p 00004000 08:01 6294355    /usr/lib/libXtst.so.6.1.0
004b8000-004ba000 r-xp 00000000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
004ba000-004bb000 r--p 00001000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
004bb000-004bc000 rw-p 00002000 08:01 8519801    /lib/libnss_mdns4_minimal.so.2
004bc000-004cc000 r-xp 00000000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
004cc000-004cd000 r--p 00010000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
004cd000-004ce000 rw-p 00011000 08:01 8653411    /lib/tls/i686/cmov/libresolv-2.11.1.so
004ce000-004d0000 rw-p 00000000 00:00 0 
004d0000-004d7000 r-xp 00000000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
004d7000-004d8000 r--p 00006000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
004d8000-004d9000 rw-p 00007000 08:01 6299075    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
004d9000-004f6000 r-xp 00000000 08:01 6299079    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
004f6000-004f7000 ---p 0001d000 08:01 6299079    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
004f7000-004f8000 r--p 0001d000 08:01 6299079    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
004f8000-004f9000 rw-p 0001e000 08:01 6299079    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libunpack.so
004f9000-004fe000 rw-p 00000000 00:00 0 
004fe000-00504000 r-xp 00000000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
00504000-00505000 r--p 00005000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
00505000-00506000 rw-p 00006000 08:01 6294347    /usr/lib/libXrandr.so.2.2.0
00506000-0050f000 r-xp 00000000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
0050f000-00510000 r--p 00008000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
00510000-00511000 rw-p 00009000 08:01 6299068    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
00511000-00512000 r-xp 00000000 08:01 6299070    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsound.so
00512000-00513000 r--p 00000000 08:01 6299070    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsound.so
00513000-00514000 rw-p 00001000 08:01 6299070    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsound.so
00517000-0051a000 r-xp 00000000 08:01 8520571    /lib/libuuid.so.1.3.0
0051a000-0051b000 r--p 00002000 08:01 8520571    /lib/libuuid.so.1.3.0
0051b000-0051c000 rw-p 00003000 08:01 8520571    /lib/libuuid.so.1.3.0
00522000-00535000 r-xp 00000000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00535000-00536000 r--p 00012000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00536000-00537000 rw-p 00013000 08:01 8653402    /lib/tls/i686/cmov/libnsl-2.11.1.so
00537000-00539000 rw-p 00000000 00:00 0 
00539000-00547000 r-xp 00000000 08:01 6301154    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsoundalsa.so
00547000-00548000 r--p 0000d000 08:01 6301154    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsoundalsa.so
00548000-00549000 rw-p 0000e000 08:01 6301154    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjsoundalsa.so
00549000-00550000 r-xp 00000000 08:01 8519873    /lib/libwrap.so.0.7.6
00550000-00551000 r--p 00006000 08:01 8519873    /lib/libwrap.so.0.7.6
00551000-00552000 rw-p 00007000 08:01 8519873    /lib/libwrap.so.0.7.6
00554000-00599000 r-xp 00000000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
00599000-0059a000 r--p 00044000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0059a000-0059c000 rw-p 00045000 08:01 6301158    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0059c000-0059d000 rw-p 00000000 00:00 0 
0059d000-005dd000 r-xp 00000000 08:01 6295132    /usr/lib/libpulse.so.0.12.2
005dd000-005de000 r--p 00040000 08:01 6295132    /usr/lib/libpulse.so.0.12.2
005de000-005df000 rw-p 00041000 08:01 6295132    /usr/lib/libpulse.so.0.12.2
005df000-005f4000 r-xp 00000000 08:01 6294279    /usr/lib/libICE.so.6.3.0
005f4000-005f5000 r--p 00014000 08:01 6294279    /usr/lib/libICE.so.6.3.0
005f5000-005f6000 rw-p 00015000 08:01 6294279    /usr/lib/libICE.so.6.3.0
005f6000-005f8000 rw-p 00000000 00:00 0 
005f8000-00603000 r-xp 00000000 08:01 6301155    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libpulse-java.so
00603000-00604000 r--p 0000a000 08:01 6301155    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libpulse-java.so
00604000-00605000 rw-p 0000b000 08:01 6301155    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libpulse-java.so
0060d000-00611000 r-xp 00000000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
00611000-00612000 r--p 00003000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
00612000-00613000 rw-p 00004000 08:01 6294325    /usr/lib/libXdmcp.so.6.0.0
00613000-0065c000 r-xp 00000000 08:01 6295133    /usr/lib/libpulsecommon-0.9.21.so
0065c000-0065d000 r--p 00048000 08:01 6295133    /usr/lib/libpulsecommon-0.9.21.so
0065d000-0065e000 rw-p 00049000 08:01 6295133    /usr/lib/libpulsecommon-0.9.21.so
0065e000-00665000 r-xp 00000000 08:01 8143411    /home/ben/.jagex_cache_32/runescape/libjaclib.so
00665000-00666000 r--p 00006000 08:01 8143411    /home/ben/.jagex_cache_32/runescape/libjaclib.so
00666000-00667000 rw-p 00007000 08:01 8143411    /home/ben/.jagex_cache_32/runescape/libjaclib.so
0067a000-0068f000 r-xp 00000000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
0068f000-00690000 r--p 00014000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
00690000-00691000 rw-p 00015000 08:01 8653410    /lib/tls/i686/cmov/libpthread-2.11.1.so
00691000-00693000 rw-p 00000000 00:00 0 
006a3000-006eb000 r-xp 00000000 08:01 6295024    /usr/lib/nss/libfreebl3.so
006eb000-006ec000 r--p 00047000 08:01 6295024    /usr/lib/nss/libfreebl3.so
006ec000-006ed000 rw-p 00048000 08:01 6295024    /usr/lib/nss/libfreebl3.so
006ed000-006f1000 rw-p 00000000 00:00 0 
006ff000-0070d000 r-xp 00000000 08:01 6294327    /usr/lib/libXext.so.6.4.0
0070d000-0070e000 r--p 0000d000 08:01 6294327    /usr/lib/libXext.so.6.4.0
0070e000-0070f000 rw-p 0000e000 08:01 6294327    /usr/lib/libXext.so.6.4.0
0070f000-00770000 r-xp 00000000 08:01 6295192    /usr/lib/libsndfile.so.1.0.21
00770000-00771000 ---p 00061000 08:01 6295192    /usr/lib/libsndfile.so.1.0.21
00771000-00772000 r--p 00061000 08:01 6295192    /usr/lib/libsndfile.so.1.0.21
00772000-00773000 rw-p 00062000 08:01 6295192    /usr/lib/libsndfile.so.1.0.21
00773000-00777000 rw-p 00000000 00:00 0 
0077e000-00785000 r-xp 00000000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00785000-00786000 r--p 00006000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00786000-00787000 rw-p 00007000 08:01 6299081    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
007af000-008c8000 r-xp 00000000 08:01 6294310    /usr/lib/libX11.so.6.3.0
008c8000-008c9000 r--p 00118000 08:01 6294310    /usr/lib/libX11.so.6.3.0
008c9000-008cb000 rw-p 00119000 08:01 6294310    /usr/lib/libX11.so.6.3.0
008cb000-008cc000 rw-p 00000000 00:00 0 
008cc000-00903000 r-xp 00000000 08:01 8519733    /lib/libdbus-1.so.3.4.0
00903000-00904000 r--p 00036000 08:01 8519733    /lib/libdbus-1.so.3.4.0
00904000-00905000 rw-p 00037000 08:01 8519733    /lib/libdbus-1.so.3.4.0
0090a000-0090c000 r-xp 00000000 08:01 6294314    /usr/lib/libXau.so.6.0.0
0090c000-0090d000 r--p 00001000 08:01 6294314    /usr/lib/libXau.so.6.0.0
0090d000-0090e000 rw-p 00002000 08:01 6294314    /usr/lib/libXau.so.6.0.0
0090e000-00935000 r-xp 00000000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00935000-00936000 r--p 00026000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00936000-00937000 rw-p 00027000 08:01 6295280    /usr/lib/libvorbis.so.0.4.3
00958000-0095b000 r-xp 00000000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
0095b000-0095c000 r--p 00003000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
0095c000-0095d000 rw-p 00004000 08:01 6297758    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
0095d000-009a8000 r-xp 00000000 08:01 6294264    /usr/lib/libFLAC.so.8.2.0
009a8000-009a9000 r--p 0004a000 08:01 6294264    /usr/lib/libFLAC.so.8.2.0
009a9000-009aa000 rw-p 0004b000 08:01 6294264    /usr/lib/libFLAC.so.8.2.0
009c9000-009d5000 r-xp 00000000 08:01 6294335    /usr/lib/libXi.so.6.1.0
009d5000-009d6000 r--p 0000c000 08:01 6294335    /usr/lib/libXi.so.6.1.0
009d6000-009d7000 rw-p 0000d000 08:01 6294335    /usr/lib/libXi.so.6.1.0
009d9000-009de000 r-xp 00000000 08:01 6295038    /usr/lib/libogg.so.0.6.0
009de000-009df000 r--p 00004000 08:01 6295038    /usr/lib/libogg.so.0.6.0
009df000-009e0000 rw-p 00005000 08:01 6295038    /usr/lib/libogg.so.0.6.0
009f0000-009f7000 r-xp 00000000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
009f7000-009f8000 r--p 00006000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
009f8000-009f9000 rw-p 00007000 08:01 8653412    /lib/tls/i686/cmov/librt-2.11.1.so
00a43000-00a4f000 r-xp 00000000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00a4f000-00a50000 r--p 0000b000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00a50000-00a51000 rw-p 0000c000 08:01 6299080    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00a51000-00ad1000 r-xp 00000000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
00ad1000-00ad2000 r--p 0007f000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
00ad2000-00ad3000 rw-p 00080000 08:01 6295212    /usr/lib/libsqlite3.so.0.8.6
00ad3000-00ad4000 rw-p 00000000 00:00 0 
00b2a000-00b2b000 r-xp 00000000 00:00 0          [vdso]
00b86000-00baa000 r-xp 00000000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00baa000-00bab000 r--p 00023000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00bab000-00bad000 rw-p 00024000 08:01 6299064    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00c01000-00c19000 r-xp 00000000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00c19000-00c1a000 r--p 00017000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00c1a000-00c1b000 rw-p 00018000 08:01 6295321    /usr/lib/libxcb.so.1.1.0
00c76000-00c79000 r-xp 00000000 08:01 6291779    /usr/lib/libplc4.so
00c79000-00c7a000 r--p 00002000 08:01 6291779    /usr/lib/libplc4.so
00c7a000-00c7b000 rw-p 00003000 08:01 6291779    /usr/lib/libplc4.so
00c90000-00ca5000 r-xp 00000000 08:01 6296555    /usr/lib/libnssutil3.so
00ca5000-00ca8000 r--p 00014000 08:01 6296555    /usr/lib/libnssutil3.so
00ca8000-00ca9000 rw-p 00017000 08:01 6296555    /usr/lib/libnssutil3.so
00cae000-00cb6000 r-xp 00000000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00cb6000-00cb7000 r--p 00007000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00cb7000-00cb8000 rw-p 00008000 08:01 8653407    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00cb8000-00d7b000 r-xp 00000000 08:01 6294394    /usr/lib/libasound.so.2.0.0
00d7b000-00d7f000 r--p 000c2000 08:01 6294394    /usr/lib/libasound.so.2.0.0
00d7f000-00d80000 rw-p 000c6000 08:01 6294394    /usr/lib/libasound.so.2.0.0
00d93000-00d9b000 r-xp 00000000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00d9b000-00d9c000 r--p 00007000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00d9c000-00d9d000 rw-p 00008000 08:01 6294349    /usr/lib/libXrender.so.1.3.0
00db5000-00dd4000 r-xp 00000000 08:01 6294923    /usr/lib/libjpeg.so.62.0.0
00dd4000-00dd5000 r--p 0001e000 08:01 6294923    /usr/lib/libjpeg.so.62.0.0
00dd5000-00dd6000 rw-p 0001f000 08:01 6294923    /usr/lib/libjpeg.so.62.0.0
00dd9000-00dec000 r-xp 00000000 08:01 8519878    /lib/libz.so.1.2.3.3
00dec000-00ded000 r--p 00012000 08:01 8519878    /lib/libz.so.1.2.3.3
00ded000-00dee000 rw-p 00013000 08:01 8519878    /lib/libz.so.1.2.3.3
00df9000-00e00000 r-xp 00000000 08:01 6294308    /usr/lib/libSM.so.6.0.1
00e00000-00e01000 r--p 00006000 08:01 6294308    /usr/lib/libSM.so.6.0.1
00e01000-00e02000 rw-p 00007000 08:01 6294308    /usr/lib/libSM.so.6.0.1
00e3b000-00e5f000 r-xp 00000000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
00e5f000-00e60000 r--p 00023000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
00e60000-00e61000 rw-p 00024000 08:01 8653400    /lib/tls/i686/cmov/libm-2.11.1.so
00ea2000-00eb0000 r-xp 00000000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00eb0000-00eb1000 r--p 0000d000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00eb1000-00eb2000 rw-p 0000e000 08:01 6299062    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00ec4000-00ec8000 r-xp 00000000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00ec8000-00ec9000 r--p 00004000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00ec9000-00eca000 rw-p 00005000 08:01 8653404    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00ed4000-00ed6000 r-xp 00000000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00ed6000-00ed7000 r--p 00001000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00ed7000-00ed8000 rw-p 00002000 08:01 8653399    /lib/tls/i686/cmov/libdl-2.11.1.so
00f27000-00f42000 r-xp 00000000 08:01 8519683    /lib/ld-2.11.1.so
00f42000-00f43000 r--p 0001a000 08:01 8519683    /lib/ld-2.11.1.so
00f43000-00f44000 rw-p 0001b000 08:01 8519683    /lib/ld-2.11.1.so
00f44000-01397000 r-xp 00000000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01397000-01398000 ---p 00453000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01398000-013af000 r--p 00453000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
013af000-013bc000 rw-p 0046a000 08:01 6297751    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
013bc000-017d8000 rw-p 00000000 00:00 0 
0226c000-02358000 r-xp 00000000 08:01 6295282    /usr/lib/libvorbisenc.so.2.0.6
02358000-02359000 ---p 000ec000 08:01 6295282    /usr/lib/libvorbisenc.so.2.0.6
02359000-02367000 r--p 000ec000 08:01 6295282    /usr/lib/libvorbisenc.so.2.0.6
02367000-02368000 rw-p 000fa000 08:01 6295282    /usr/lib/libvorbisenc.so.2.0.6
04006000-04114000 r-xp 00000000 08:01 6296556    /usr/lib/libnss3.so
04114000-04115000 ---p 0010e000 08:01 6296556    /usr/lib/libnss3.so
04115000-04118000 r--p 0010e000 08:01 6296556    /usr/lib/libnss3.so
04118000-0411a000 rw-p 00111000 08:01 6296556    /usr/lib/libnss3.so
054c8000-055b1000 r-xp 00000000 08:01 6295219    /usr/lib/libstdc++.so.6.0.13
055b1000-055b2000 ---p 000e9000 08:01 6295219    /usr/lib/libstdc++.so.6.0.13
055b2000-055b6000 r--p 000e9000 08:01 6295219    /usr/lib/libstdc++.so.6.0.13
055b6000-055b7000 rw-p 000ed000 08:01 6295219    /usr/lib/libstdc++.so.6.0.13
055b7000-055be000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:01 6299113    /usr/lib/jvm/java-6-openjdk/jre/bin/java
086dc000-09d96000 rw-p 00000000 00:00 0          [heap]
6f940000-717e0000 rw-p 00000000 00:00 0 
717e0000-7a3e0000 rw-p 00000000 00:00 0 
7a3e0000-7e10c000 rw-p 00000000 00:00 0 
7e10c000-7e52c000 ---p 00000000 00:00 0 
7e52c000-8f940000 rw-p 00000000 00:00 0 
8f940000-90540000 rw-p 00000000 00:00 0 
90540000-905c0000 ---p 00000000 00:00 0 
905c0000-93940000 rw-p 00000000 00:00 0 
93940000-94099000 r--s 00001000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94099000-94340000 rw-p 00000000 00:00 0 
94340000-94a81000 rw-p 0075a000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94a81000-94f40000 rw-p 00000000 00:00 0 
94f40000-9503b000 rw-p 00e9b000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
9503b000-95340000 rw-p 00000000 00:00 0 
95340000-95348000 r-xs 00f96000 08:01 6301183    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
95348000-95740000 rw-p 00000000 00:00 0 
b3b00000-b3b96000 rw-p 00000000 00:00 0 
b3b96000-b3c00000 ---p 00000000 00:00 0 
b3d00000-b3dfc000 rw-p 00000000 00:00 0 
b3dfc000-b3e00000 ---p 00000000 00:00 0 
b3e00000-b3efe000 rw-p 00000000 00:00 0 
b3efe000-b3f00000 ---p 00000000 00:00 0 
b3f00000-b40f9000 rw-p 00000000 00:00 0 
b40f9000-b4100000 ---p 00000000 00:00 0 
b4100000-b41fa000 rw-p 00000000 00:00 0 
b41fa000-b4200000 ---p 00000000 00:00 0 
b4200000-b42fd000 rw-p 00000000 00:00 0 
b42fd000-b4300000 ---p 00000000 00:00 0 
b4300000-b43fd000 rw-p 00000000 00:00 0 
b43fd000-b4400000 ---p 00000000 00:00 0 
b4417000-b441a000 ---p 00000000 00:00 0 
b441a000-b4468000 rw-p 00000000 00:00 0 
b4468000-b4887000 rw-s 00000000 00:04 29491220   /SYSV00000000 (deleted)
b4887000-b488a000 ---p 00000000 00:00 0 
b488a000-b48d8000 rw-p 00000000 00:00 0 
b48d8000-b48db000 ---p 00000000 00:00 0 
b48db000-b4929000 rw-p 00000000 00:00 0 
b496f000-b4972000 ---p 00000000 00:00 0 
b4972000-b49c0000 rw-p 00000000 00:00 0 
b49c0000-b49c2000 r--s 00007000 08:01 8143630    /home/ben/.icedteaplugin/cache/http/world11.runescape.com/loader-1288657538.jar
b49c2000-b49c5000 ---p 00000000 00:00 0 
b49c5000-b4a13000 rw-p 00000000 00:00 0 
b4a13000-b4a15000 r--s 00007000 08:01 8142265    /home/ben/.icedteaplugin/cache/http/world81.runescape.com/loader-1288657538.jar
b4a15000-b4a18000 ---p 00000000 00:00 0 
b4a18000-b4a66000 rw-p 00000000 00:00 0 
b4a66000-b4a69000 ---p 00000000 00:00 0 
b4a69000-b4ab7000 rw-p 00000000 00:00 0 
b4ab7000-b4aba000 ---p 00000000 00:00 0 
b4aba000-b4b08000 rw-p 00000000 00:00 0 
b4b08000-b4b0b000 ---p 00000000 00:00 0 
b4b0b000-b4b59000 rw-p 00000000 00:00 0 
b4b59000-b4b5c000 ---p 00000000 00:00 0 
b4b5c000-b4baa000 rw-p 00000000 00:00 0 
b4baa000-b4bad000 ---p 00000000 00:00 0 
b4bad000-b4bfb000 rw-p 00000000 00:00 0 
b4bfb000-b4bfe000 ---p 00000000 00:00 0 
b4bfe000-b4c4c000 rw-p 00000000 00:00 0 
b4c4c000-b4c4f000 ---p 00000000 00:00 0 
b4c4f000-b4c9d000 rw-p 00000000 00:00 0 
b4c9d000-b4ca0000 ---p 00000000 00:00 0 
b4ca0000-b4cee000 rw-p 00000000 00:00 0 
b4cee000-b4cf1000 ---p 00000000 00:00 0 
b4cf1000-b4d3f000 rw-p 00000000 00:00 0 
b4d3f000-b4d42000 ---p 00000000 00:00 0 
b4d42000-b4d90000 rw-p 00000000 00:00 0 
b4d90000-b4d93000 ---p 00000000 00:00 0 
b4d93000-b4de1000 rw-p 00000000 00:00 0 
b4de1000-b4de4000 ---p 00000000 00:00 0 
b4de4000-b4e32000 rw-p 00000000 00:00 0 
b4e32000-b4e35000 r--s 00038000 08:01 6294065    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
b4e35000-b4e37000 r--s 00013000 08:01 6297724    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
b4e37000-b4e3a000 r--s 00031000 08:01 6294190    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
b4e3a000-b4e3e000 r--s 0007c000 08:01 6297725    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
b4e3e000-b4e41000 ---p 00000000 00:00 0 
b4e41000-b4e8f000 rw-p 00000000 00:00 0 
b4e8f000-b4e92000 ---p 00000000 00:00 0 
b4e92000-b4ee0000 rw-p 00000000 00:00 0 
b4ee0000-b4ee3000 ---p 00000000 00:00 0 
b4ee3000-b4f31000 rw-p 00000000 00:00 0 
b4f31000-b4f37000 r--s 000fc000 08:01 6297732    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
b4f37000-b4f38000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4f38000-b4f39000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4f39000-b4f3f000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4f3f000-b4f41000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4f41000-b4f44000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4f44000-b4f4a000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4f4a000-b4f4b000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4f4b000-b4f4e000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4f4e000-b4f4f000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4f4f000-b4f50000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4f50000-b4f51000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4f51000-b4f55000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4f55000-b4f59000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4f59000-b4f60000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4f60000-b4f6b000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4f6b000-b4f6e000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4f6e000-b4f6f000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4f6f000-b4f77000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4f77000-b4f7f000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4f7f000-b4f82000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4f82000-b4f83000 r--s 00000000 08:01 4592883    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4f83000-b4f84000 r--s 00000000 08:01 4587585    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4f84000-b4f8a000 r--s 00000000 08:01 4587582    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4f8a000-b4f8c000 r--s 00000000 08:01 4587583    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4f8c000-b4f8f000 r--s 00000000 08:01 4587592    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4f8f000-b4f95000 r--s 00000000 08:01 4592987    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4f95000-b4f96000 r--s 00000000 08:01 4587593    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4f96000-b4f99000 r--s 00000000 08:01 4587579    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4f99000-b4f9a000 r--s 00000000 08:01 4587575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4f9a000-b4f9b000 r--s 00000000 08:01 4587569    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4f9b000-b4f9c000 r--s 00000000 08:01 4587577    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4f9c000-b4fa0000 r--s 00000000 08:01 4587584    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4fa0000-b4fa4000 r--s 00000000 08:01 4593005    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4fa4000-b4fab000 r--s 00000000 08:01 4594878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4fab000-b4fb6000 r--s 00000000 08:01 4595308    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4fb6000-b4fb9000 r--s 00000000 08:01 4587589    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4fb9000-b4fba000 r--s 00000000 08:01 4592283    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4fba000-b4fc2000 r--s 00000000 08:01 4587588    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4fc2000-b4fca000 r--s 00000000 08:01 4593566    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4fca000-b4fcd000 r--s 00000000 08:01 4592826    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4fcd000-b4fd0000 ---p 00000000 00:00 0 
b4fd0000-b501e000 rw-p 00000000 00:00 0 
b501e000-b5027000 r--s 00065000 08:01 6692486    /usr/share/java/gnome-java-bridge.jar
b5027000-b5028000 ---p 00000000 00:00 0 
b5028000-b50a8000 rw-p 00000000 00:00 0 
b50a8000-b50ab000 ---p 00000000 00:00 0 
b50ab000-b50f9000 rw-p 00000000 00:00 0 
b50f9000-b50fc000 ---p 00000000 00:00 0 
b50fc000-b517a000 rw-p 00000000 00:00 0 
b517a000-b517d000 ---p 00000000 00:00 0 
b517d000-b51cb000 rw-p 00000000 00:00 0 
b51cb000-b51d2000 r--s 00000000 08:01 6292678    /usr/lib/gconv/gconv-modules.cache
b51d2000-b5211000 r--p 00000000 08:01 6422640    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b5211000-b5214000 ---p 00000000 00:00 0 
b5214000-b5262000 rw-p 00000000 00:00 0 
b5262000-b5265000 ---p 00000000 00:00 0 
b5265000-b52b3000 rw-p 00000000 00:00 0 
b52b3000-b52b4000 ---p 00000000 00:00 0 
b52b4000-b5334000 rw-p 00000000 00:00 0 
b5334000-b5336000 r--s 0001d000 08:01 6297730    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
b5336000-b533b000 r--s 00044000 08:01 6297729    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
b533b000-b536e000 rw-p 00000000 00:00 0 
b536e000-b54fd000 r--s 038c2000 08:01 6297744    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b54fd000-b5511000 rw-p 00000000 00:00 0 
b5511000-b552b000 rw-p 00000000 00:00 0 
b552b000-b554a000 rw-p 00000000 00:00 0 
b554a000-b554c000 ---p 00000000 00:00 0 
b554c000-b55d6000 rw-p 00000000 00:00 0 
b55d6000-b55e6000 rw-p 00000000 00:00 0 
b55e6000-b562b000 rw-p 00000000 00:00 0 
b562b000-b564a000 rw-p 00000000 00:00 0 
b564a000-b564c000 ---p 00000000 00:00 0 
b564c000-b56d6000 rw-p 00000000 00:00 0 
b56d6000-b56dc000 rw-p 00000000 00:00 0 
b56dc000-b56dd000 ---p 00000000 00:00 0 
b56dd000-b56f6000 rw-p 00000000 00:00 0 
b56f6000-b572e000 rw-p 00000000 00:00 0 
b572e000-b5782000 rw-p 00000000 00:00 0 
b5782000-b6282000 rwxp 00000000 00:00 0 
b6282000-b7782000 rw-p 00000000 00:00 0 
b7782000-b7785000 ---p 00000000 00:00 0 
b7785000-b77d6000 rw-p 00000000 00:00 0 
b77d6000-b77d7000 r--p 00000000 00:00 0 
b77d7000-b77da000 r--s 0000f000 08:01 6294240    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b77da000-b77e2000 rw-s 00000000 08:01 393290     /tmp/hsperfdata_ben/11777
b77e2000-b77e3000 rw-p 00000000 00:00 0 
b77e3000-b77e4000 r--p 00000000 00:00 0 
b77e4000-b77e6000 rw-p 00000000 00:00 0 
bfccc000-bfce1000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
java_command: sun.applet.PluginMain /tmp/icedteaplugin-ben/8841-icedteanp-plugin-to-appletviewer /tmp/icedteaplugin-ben/8841-icedteanp-appletviewer-to-plugin
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=ben
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3ea350], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3ea350], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30d370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30ca20], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30f590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.60 1.78 1.88

/proc/meminfo:
MemTotal:        2061692 kB
MemFree:          120656 kB
Buffers:           83684 kB
Cached:          1417672 kB
SwapCached:            0 kB
Active:          1002700 kB
Inactive:         869164 kB
Active(anon):     278472 kB
Inactive(anon):   101680 kB
Active(file):     724228 kB
Inactive(file):   767484 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       1187784 kB
HighFree:           1736 kB
LowTotal:         873908 kB
LowFree:          118920 kB
SwapTotal:       6036472 kB
SwapFree:        6036472 kB
Dirty:               156 kB
Writeback:             0 kB
AnonPages:        370580 kB
Mapped:           109752 kB
Shmem:              9588 kB
Slab:              43148 kB
SReclaimable:      32132 kB
SUnreclaim:        11016 kB
KernelStack:        2136 kB
PageTables:         5364 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7067316 kB
Committed_AS:    1024576 kB
VmallocTotal:     122880 kB
VmallocUsed:       19672 kB
VmallocChunk:      97276 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      360440 kB
DirectMap4M:      548864 kB


CPU:total 1 (1 cores per cpu, 1 threads per core) family 6 model 10 stepping 0, cmov, cx8, fxsr, mmx, sse, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 2061692k(120656k free), swap 6036472k(6036472k free)

vm_info: OpenJDK Client VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Feb 23 2011 19:53:10 by "buildd" with gcc 4.4.3

time: Thu Mar 10 23:19:35 2011
elapsed time: 340 seconds

```

---

