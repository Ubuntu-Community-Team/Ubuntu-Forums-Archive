---
title: "Java core dump (Minecraftserver)"
date: 2012-08-04
forum: General Help
---

### Post by DaFranz on 2012-08-04
Hi,

For the last 3 hours i am trying to get my minecraftserver working. I installed Java7 and downloaded the minecraftserver jar from minecraft.net . After executing the jar with "java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui" sometimes it stops after this:

> 2012-08-04 13:13:47 [INFO] Starting minecraft server version 1.3.1
2012-08-04 13:13:47 [INFO] Loading properties
2012-08-04 13:13:47 [WARNING] server.properties does not exist
2012-08-04 13:13:47 [INFO] Generating new properties file
2012-08-04 13:13:47 [INFO] Default game type: SURVIVAL
2012-08-04 13:13:47 [INFO] Generating keypair
2012-08-04 13:13:47 [INFO] Starting Minecraft server on *:25565
sometimes it goes on and start generating the world, but stops for example at 16%. I also got some error from java about core dump. I also tried to run it with java6, but there was no diffrence. I dont know what to try next, any help?

---

### Post by DaFranz on 2012-08-04
Sorry for double post, but some more information here.

What i did sofar:[INDENT] > - Reinstalled Ubuntu
- Adduser minecraft --no-create-home --disabled-login
- mkdir /opt/minecraft/server
- chown -R minecraft /opt/minecraft
- su minecraft
- cd /opt/minecraft/server
- wget "[http://dl.bukkit.org/downloads/craftbukkit/get/01249_1.2.5-R5.0/craftbukkit.jar](http://dl.bukkit.org/downloads/craftbukkit/get/01249_1.2.5-R5.0/craftbukkit.jar)" -O "craftbukkit.jar"
- script /dev/null
- screen -S minecraft
- java -Xmx1024M -Xms1024M -jar -craftbukkit.jar
 
System:
Ubuntu 12.04
4 GB Ram
QuadCore AMD Opteron
 
Java -version:
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.3) (6b24-1.11.3-1ubuntu0.12.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)Any hints what to do or what is wrong?[/INDENT]

---

### Post by DaFranz on 2012-08-04
Sometimes i get this Java error:
> root@h2057119:/opt/minecraft/server# ./start.sh
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00bc0b4e, pid=983, tid=3078183744
#
# JRE version: 6.0_24-b24
# Java VM: OpenJDK Client VM (20.0-b12 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.11.3
# Distribution: Ubuntu 12.04 LTS, package 6b24-1.11.3-1ubuntu0.12.04.1
# Problematic frame:
# V  [libjvm.so+0x4cb4e]  AccessFlags::atomic_set_bits(int)+0x3e
#
# An error report file with more information is saved as:
# /opt/minecraft/server/hs_err_pid983.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/ source/openjdk-6/]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/")
#
./start.sh: line 3:   983 Aborted                 (core dumped) java -Xmx1024M -Xms1024M -jar craftbukkit.jar

The log file form java for this is:

> #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00bc0b4e, pid=983, tid=3078183744
#
# JRE version: 6.0_24-b24
# Java VM: OpenJDK Client VM (20.0-b12 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.11.3
# Distribution: Ubuntu 12.04 LTS, package 6b24-1.11.3-1ubuntu0.12.04.1
# Problematic frame:
# V  [libjvm.so+0x4cb4e]  AccessFlags::atomic_set_bits(int)+0x3e
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/ source/openjdk-6/]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/")
#

---------------  T H R E A D  ---------------

Current thread (0xb7605400):  JavaThread "main" [_thread_in_vm, id=984, stack(0xb7745000,0xb7796000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=2 (SEGV_ACCERR), si_addr=0x93ccd4a8

Error accessing class data sharing archive. Mapped file inaccessible during execution,  possible disk/network problem.

Registers:
EAX=0x93ccd4ab, EBX=0x0109dff4, ECX=0x93ccd4a8, EDX=0x93ccd4ab
ESP=0xb7794aa4, EBP=0x010b0e04, ESI=0x93ccd4ab, EDI=0x00000000
EIP=0x00bc0b4e, EFLAGS=0x00010246, CR2=0x93ccd4a8

Top of Stack: (sp=0xb7794aa4)
0xb7794aa4:   0109dff4 b763dc68 b763a058 00000001
0xb7794ab4:   00cbfc30 93ccd4a8 01000000 b7794b20
0xb7794ac4:   00cbfbd8 0109dff4 00000000 b763dc68
0xb7794ad4:   00cc0958 b763a058 b763dc68 b7605e38
0xb7794ae4:   ffffffff 00000001 b7605e38 000000a9
0xb7794af4:   00f92a8c 00000000 00d5ae23 94190f10
0xb7794b04:   00cc08e8 0109dff4 b7605e38 ffffffff
0xb7794b14:   00cc0cfe b763a058 00000001 b7605e38 

Instructions: (pc=0x00bc0b4e)
0x00bc0b2e:   00 00 8b 11 8b 74 24 18 09 d6 83 7d 00 01 0f 9f
0x00bc0b3e:   c0 25 ff 00 00 00 89 c7 89 d0 83 ff 00 74 01 f0
0x00bc0b4e:   0f b1 31 39 c2 75 db 5b 5e 5f 5d c3 8d b6 00 00
0x00bc0b5e:   00 00 55 57 56 53 f7 54 24 18 e8 00 00 00 00 5b 

Register to memory mapping:

EAX=0x93ccd4ab is an oop
{symbol} 
 - klass: {other class}
EBX=0x0109dff4: <offset 0x529ff4> in /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so at 0x00b74000
ECX=0x93ccd4a8 is an oop
{symbol} 
 - klass: {other class}
EDX=0x93ccd4ab is an oop
{symbol} 
 - klass: {other class}
ESP=0xb7794aa4 is pointing into the stack for thread: 0xb7605400
EBP=0x010b0e04: <offset 0x53ce04> in /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so at 0x00b74000
ESI=0x93ccd4ab is an oop
{symbol} 
 - klass: {other class}
EDI=0x00000000 is an unknown value


Stack: [0xb7745000,0xb7796000],  sp=0xb7794aa4,  free space=318k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x4cb4e]  AccessFlags::atomic_set_bits(int)+0x3e

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  java.lang.String.hashCode()I+0
j  java.util.Hashtable.get(Ljava/lang/Object[IMG]http://forums.bukkit.org/smilies/winkanimated.gif[/IMG]Ljava/lang/Object;+6
j  java.util.Properties.getProperty(Ljava/lang/String[IMG]http://forums.bukkit.org/smilies/winkanimated.gif[/IMG]Ljava/lang/String;+2
j  java.lang.System.getProperty(Ljava/lang/String[IMG]http://forums.bukkit.org/smilies/winkanimated.gif[/IMG]Ljava/lang/String;+21
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0xb763c400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=990, stack(0xb4b54000,0xb4ba5000)]
  0xb763a400 JavaThread "C1 CompilerThread0" daemon [_thread_blocked, id=989, stack(0xb4ba5000,0xb4c26000)]
  0xb7638c00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=988, stack(0xb4c26000,0xb4c77000)]
  0xb7634800 JavaThread "Finalizer" daemon [_thread_blocked, id=987, stack(0xb4f18000,0xb4f69000)]
  0xb7633000 JavaThread "Reference Handler" daemon [_thread_blocked, id=986, stack(0xb4f69000,0xb4fba000)]
=>0xb7605400 JavaThread "main" [_thread_in_vm, id=984, stack(0xb7745000,0xb7796000)]

Other Threads:
  0xb7631400 VMThread [stack: 0xb4fba000,0xb503b000] [id=985]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0xb7603718] MethodCompileQueue_lock - owner thread: 0xb7605400

Heap
 def new generation   total 314560K, used 5592K [0x4f780000, 0x64cd0000, 0x64cd0000)
  eden space 279616K,   2% used [0x4f780000, 0x4fcf6160, 0x60890000)
  from space 34944K,   0% used [0x60890000, 0x60890000, 0x62ab0000)
  to   space 34944K,   0% used [0x62ab0000, 0x62ab0000, 0x64cd0000)
 tenured generation   total 699072K, used 0K [0x64cd0000, 0x8f780000, 0x8f780000)
   the space 699072K,   0% used [0x64cd0000, 0x64cd0000, 0x64cd0200, 0x8f780000)
 compacting perm gen  total 12288K, used 22K [0x8f780000, 0x90380000, 0x93780000)
   the space 12288K,   0% used [0x8f780000, 0x8f7858b8, 0x8f785a00, 0x90380000)
    ro space 10240K,  73% used [0x93780000, 0x93ee0cc8, 0x93ee0e00, 0x94180000)
    rw space 12288K,  60% used [0x94180000, 0x948ca478, 0x948ca600, 0x94d80000)

Code Cache  [0xb5600000, 0xb5648000, 0xb7600000)
 total_blobs=86 nmethods=0 adapters=55 free_code_cache=33265216 largest_free_block=128

Dynamic libraries:
00110000-0013a000 r-xp 00000000 00:3f 22603992                           /lib/i386-linux-gnu/libm-2.15.so
0013a000-0013b000 r--p 00029000 00:3f 22603992                           /lib/i386-linux-gnu/libm-2.15.so
0013b000-0013c000 rw-p 0002a000 00:3f 22603992                           /lib/i386-linux-gnu/libm-2.15.so
0013c000-00143000 r-xp 00000000 00:3f 22603976                           /lib/i386-linux-gnu/librt-2.15.so
00143000-00144000 r--p 00006000 00:3f 22603976                           /lib/i386-linux-gnu/librt-2.15.so
00144000-00145000 rw-p 00007000 00:3f 22603976                           /lib/i386-linux-gnu/librt-2.15.so
00145000-0014c000 r-xp 00000000 00:3f 22604063                           /lib/i386-linux-gnu/libnss_compat-2.15.so
0014c000-0014d000 r--p 00006000 00:3f 22604063                           /lib/i386-linux-gnu/libnss_compat-2.15.so
0014d000-0014e000 rw-p 00007000 00:3f 22604063                           /lib/i386-linux-gnu/libnss_compat-2.15.so
0014e000-00164000 r-xp 00000000 00:3f 22603977                           /lib/i386-linux-gnu/libnsl-2.15.so
00164000-00165000 r--p 00015000 00:3f 22603977                           /lib/i386-linux-gnu/libnsl-2.15.so
00165000-00166000 rw-p 00016000 00:3f 22603977                           /lib/i386-linux-gnu/libnsl-2.15.so
00166000-00168000 rw-p 00000000 00:00 0 
0016f000-0018b000 r-xp 00000000 00:3f 22604030                           /lib/i386-linux-gnu/libgcc_s.so.1
0018b000-0018c000 r--p 0001b000 00:3f 22604030                           /lib/i386-linux-gnu/libgcc_s.so.1
0018c000-0018d000 rw-p 0001c000 00:3f 22604030                           /lib/i386-linux-gnu/libgcc_s.so.1
0018d000-00197000 r-xp 00000000 00:3f 22604019                           /lib/i386-linux-gnu/libnss_nis-2.15.so
00197000-00198000 r--p 00009000 00:3f 22604019                           /lib/i386-linux-gnu/libnss_nis-2.15.so
00198000-00199000 rw-p 0000a000 00:3f 22604019                           /lib/i386-linux-gnu/libnss_nis-2.15.so
00199000-001a0000 r-xp 00000000 00:3f 22888978                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
001a0000-001a1000 r--p 00006000 00:3f 22888978                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
001a1000-001a2000 rw-p 00007000 00:3f 22888978                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
001c0000-001d7000 r-xp 00000000 00:3f 22604054                           /lib/i386-linux-gnu/libpthread-2.15.so
001d7000-001d8000 r--p 00016000 00:3f 22604054                           /lib/i386-linux-gnu/libpthread-2.15.so
001d8000-001d9000 rw-p 00017000 00:3f 22604054                           /lib/i386-linux-gnu/libpthread-2.15.so
001d9000-001db000 rw-p 00000000 00:00 0 
001db000-0037a000 r-xp 00000000 00:3f 22604013                           /lib/i386-linux-gnu/libc-2.15.so
0037a000-0037c000 r--p 0019f000 00:3f 22604013                           /lib/i386-linux-gnu/libc-2.15.so
0037c000-0037d000 rw-p 001a1000 00:3f 22604013                           /lib/i386-linux-gnu/libc-2.15.so
0037d000-00380000 rw-p 00000000 00:00 0 
00386000-003a6000 r-xp 00000000 00:3f 22604037                           /lib/i386-linux-gnu/ld-2.15.so
003a6000-003a7000 r--p 0001f000 00:3f 22604037                           /lib/i386-linux-gnu/ld-2.15.so
003a7000-003a8000 rw-p 00020000 00:3f 22604037                           /lib/i386-linux-gnu/ld-2.15.so
004a8000-004ce000 r-xp 00000000 00:3f 22888961                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
004ce000-004cf000 r--p 00025000 00:3f 22888961                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
004cf000-004d1000 rw-p 00026000 00:3f 22888961                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
00538000-00539000 r-xp 00000000 00:00 0                                  [vdso]
0053e000-00549000 r-xp 00000000 00:3f 22889121                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
00549000-0054a000 ---p 0000b000 00:3f 22889121                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
0054a000-0054b000 r--p 0000b000 00:3f 22889121                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
0054b000-0054c000 rw-p 0000c000 00:3f 22889121                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
007cb000-007d6000 r-xp 00000000 00:3f 22604023                           /lib/i386-linux-gnu/libnss_files-2.15.so
007d6000-007d7000 r--p 0000a000 00:3f 22604023                           /lib/i386-linux-gnu/libnss_files-2.15.so
007d7000-007d8000 rw-p 0000b000 00:3f 22604023                           /lib/i386-linux-gnu/libnss_files-2.15.so
00805000-00809000 r-xp 00000000 00:3f 22889114                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
00809000-0080a000 r--p 00003000 00:3f 22889114                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
0080a000-0080b000 rw-p 00004000 00:3f 22889114                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
00835000-00838000 r-xp 00000000 00:3f 22604082                           /lib/i386-linux-gnu/libdl-2.15.so
00838000-00839000 r--p 00002000 00:3f 22604082                           /lib/i386-linux-gnu/libdl-2.15.so
00839000-0083a000 rw-p 00003000 00:3f 22604082                           /lib/i386-linux-gnu/libdl-2.15.so
00982000-00a5a000 r-xp 00000000 00:3f 22702543                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00a5a000-00a5b000 ---p 000d8000 00:3f 22702543                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00a5b000-00a5f000 r--p 000d8000 00:3f 22702543                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00a5f000-00a60000 rw-p 000dc000 00:3f 22702543                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00a60000-00a67000 rw-p 00000000 00:00 0 
00b5e000-00b72000 r-xp 00000000 00:3f 22603987                           /lib/i386-linux-gnu/libz.so.1.2.3.4
00b72000-00b73000 r--p 00013000 00:3f 22603987                           /lib/i386-linux-gnu/libz.so.1.2.3.4
00b73000-00b74000 rw-p 00014000 00:3f 22603987                           /lib/i386-linux-gnu/libz.so.1.2.3.4
00b74000-01087000 r-xp 00000000 00:3f 22889104                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
01087000-0109e000 r--p 00512000 00:3f 22889104                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
0109e000-010ab000 rw-p 00529000 00:3f 22889104                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
010ab000-014c3000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 00:3f 22888925                           /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
08051000-08052000 r--p 00008000 00:3f 22888925                           /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
08052000-08053000 rw-p 00009000 00:3f 22888925                           /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
0924b000-0926c000 rw-p 00000000 00:00 0                                  [heap]
4f780000-90380000 rw-p 00000000 00:00 0 
90380000-93780000 rw-p 00000000 00:00 0 
93780000-93ee1000 r--s 00001000 00:3f 22888808                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
93ee1000-94180000 rw-p 00000000 00:00 0 
94180000-948cb000 rw-p 00762000 00:3f 22888808                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
948cb000-94d80000 rw-p 00000000 00:00 0 
94d80000-94e7c000 rw-p 00ead000 00:3f 22888808                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
94e7c000-95180000 rw-p 00000000 00:00 0 
95180000-95188000 r-xs 00fa9000 00:3f 22888808                            /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
95188000-95580000 rw-p 00000000 00:00 0 
b4b54000-b4b57000 ---p 00000000 00:00 0 
b4b57000-b4ba5000 rw-p 00000000 00:00 0 
b4ba5000-b4ba8000 ---p 00000000 00:00 0 
b4ba8000-b4c26000 rw-p 00000000 00:00 0 
b4c26000-b4c29000 ---p 00000000 00:00 0 
b4c29000-b4c77000 rw-p 00000000 00:00 0 
b4c77000-b4e00000 r--p 00000000 00:3f 22701826                           /usr/lib/locale/locale-archive
b4e00000-b4e21000 rw-p 00000000 00:00 0 
b4e21000-b4f00000 ---p 00000000 00:00 0 
b4f18000-b4f1b000 ---p 00000000 00:00 0 
b4f1b000-b4f69000 rw-p 00000000 00:00 0 
b4f69000-b4f6c000 ---p 00000000 00:00 0 
b4f6c000-b4fba000 rw-p 00000000 00:00 0 
b4fba000-b4fbb000 ---p 00000000 00:00 0 
b4fbb000-b506e000 rw-p 00000000 00:00 0 
b506e000-b51fe000 r--s 037bc000 00:3f 22888940                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/rt.jar
b51fe000-b555a000 rw-p 00000000 00:00 0 
b555a000-b5574000 rw-p 00000000 00:00 0 
b5574000-b5582000 rw-p 00000000 00:00 0 
b5582000-b5600000 rw-p 00000000 00:00 0 
b5600000-b5648000 rwxp 00000000 00:00 0 
b5648000-b764c000 rw-p 00000000 00:00 0 
b764c000-b7700000 ---p 00000000 00:00 0 
b770f000-b7723000 rw-p 00000000 00:00 0 
b7723000-b773d000 rw-p 00000000 00:00 0 
b773d000-b7745000 rw-s 00000000 00:3f 22922948                           /tmp/hsperfdata_root/983
b7745000-b7748000 ---p 00000000 00:00 0 
b7748000-b7799000 rw-p 00000000 00:00 0 
b779d000-b779e000 rw-p 00000000 00:00 0 
b779e000-b779f000 r--p 00000000 00:00 0 
b779f000-b77a1000 rw-p 00000000 00:00 0 
bfc18000-bfc4e000 rw-p 00000000 00:00 0                                  [stack]

VM Arguments:
jvm_args: -Xmx1024M -Xms1024M 
java_command: craftbukkit.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386:/usr/lib/jvm/java-6-openjdk-i386/jre/../lib/i386
SHELL=/bin/bash

Signal Handlers:
SIGSEGV: [libjvm.so+0x3e3530], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3e3530], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x300e50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x300e50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x300e50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x300e50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x300ce0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x303d80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x303d80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x303d80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x303d80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 12.04 (precise)
uname:Linux 2.6.32-042stab055.12 #1 SMP Wed May 23 16:07:36 MSD 2012 i686
libc:glibc 2.15 NPTL 2.15 
rlimit: STACK 10240k, CORE infinity, NPROC 127269, NOFILE 1024, AS infinity
load average:0.03 0.04 0.00

/proc/meminfo:
MemTotal:        4194304 kB
MemFree:         4003668 kB
Cached:           172412 kB
Active:            75204 kB
Inactive:         107928 kB
Active(anon):      10664 kB
Inactive(anon):       56 kB
Active(file):      64540 kB
Inactive(file):   107872 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                64 kB
Writeback:             0 kB
AnonPages:         10720 kB
Shmem:              2628 kB
Slab:               7412 kB
SReclaimable:       4640 kB
SUnreclaim:         2772 kB


CPU:total 1 (4 cores per cpu, 1 threads per core) family 16 model 4  stepping 2, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext,  3dnowpref, lzcnt, sse4a

Memory: 4k page, physical 4194304k(4003672k free), swap 0k(0k free)

vm_info: OpenJDK Client VM (20.0-b12) for linux-x86 JRE (1.6.0_24-b24), built on Jun 26 2012 22:38:21 by "buildd" with gcc 4.6.3

time: Sat Aug  4 21:21:17 2012
elapsed time: 0 seconds

---

### Post by zero2xiii on 2012-08-04
Hay,

Strange suggestion based on:

> # Problematic frame:
 # V [libjvm.so+0x4cb4e] AccessFlags::atomic_set_bits(int)+0x3e
> Error accessing class data sharing archive. Mapped file inaccessible during execution, possible disk/network problem.
> - Adduser minecraft --no-create-home --disabled-login

Try running the server with sudo.

I have had simmilar issues, and sudo fixed mine. Albeight my server was running on a LAN, and I had a very strange environment set up for the server. (EDIT - Now I can edit my post haha. I remembered I had oracle installed and not IcedTea as well. So check my second post for recommendations regarding the java version itself)

It might not be safe, especialy if it is a public server. But at least then you know if it is a permission error, or some other error.

Cherz

---

### Post by zero2xiii on 2012-08-04
Hay,

Sorry about the second post but I cant seem to edit my other post... Weird.. hahaha computer must be tired :)...

Are you running a 32 or 64 bit ubuntu install? Cause I see all java refferences are 32bit:

> /usr/lib/jvm/java-6-openjdk-**i386**/jre/lib/**i386**/client/libjvm.so

However your architecture seems to be 64bit:
> 4 cores per cpu, 1 threads per core) family 16 model 4 stepping 2

I think you have a 32bit os installed based on:
> uname:Linux 2.6.32-042stab055.12 #1 SMP Wed May 23 16:07:36 MSD 2012 **i686**


Also I see you have the open Java installed (Iced Tea), have you tried the proprietry java?
> OpenJDK Runtime Environment (IcedTea6 1.11.3) (6b24-1.11.3-1ubuntu0.12.04.1)
 OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)

[http://thedaneshproject.com/posts/how-to-install-java-7-on-ubuntu-12-04-lts/](http://thedaneshproject.com/posts/how-to-install-java-7-on-ubuntu-12-04-lts/)
[http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/)

I installed the packages on my 12.04_64bit without following a tutorial by downloading the package from:
[http://java.com/en/download/manual.jsp?locale=en](http://java.com/en/download/manual.jsp?locale=en)

Another issue that might be pressent: If you have installed the oracle version the environment is still Icedtea. Have a look the section "**Choosing the default Java to use**" [here]("https://help.ubuntu.com/community/Java") on how to resolve the issue.


I think your problem might be java related other than privledges. So try installing oracle Java 7 and setting it as the default environment and try hosting the server again.

Hope this post is not TO confusing. :-k

Cherz,
Philip

---

### Post by DaFranz on 2012-08-04
Thx for responding. I started the server as root but still the same error occured, i also switched java versions many times and i get the same error with every version. Tomorrow i will try out installing java by downloading. But it is kinda strange sometimes it goes good till 20% of the map generation sometimes it failes before and somtimes it starts right after the execution of the jar. Can it be that it fails, because my VServer has no Swap ?

---

### Post by zero2xiii on 2012-08-05
> **DaFranz said:**
> Can it be that it fails, because my VServer has no Swap ?

I wont goes as far as to say no it wont be that, but I highly doubt it. As it is not a memory related error you get, rather a access error.

You might try giving the server some swap (Even if you just format a usb drive as swap and reboot the computer with the usb drive plugged in - it should auto mount the swap space and use it. Unless you have just dissabled swap allocation for this specific process, try allowing some swap space)

If you are concerned about it being a memory issue, try allocating more ram, I see you give 1gig, try giving lets say 1.5gig and see if it goes further (eg it fails now at about 25-30% instead of 10-15% earlier as an example).

If increasing the ram allocation increases the progression, try generating maps or other things before starting the server. I think this should be possible? Not sure, have a look at some documentation regarding minecraft servers.

You stated that you have tried different versions of java. Does this include 6 and 7? Both icedtea (open) and the Oracle (proprietary) versions of both? (4 versions in total).

Cherz

Just an after thought.
Read through this:
[http://www.minecraftforum.net/topic/420-tutorial-on-running-minecraft-on-a-dedicated-server/](http://www.minecraftforum.net/topic/420-tutorial-on-running-minecraft-on-a-dedicated-server/)

There is a decent discussion on some common errors and mistakes made in the hosting of servers and some configurations. I see you get an error:
> 2012-08-04 13:13:47 [WARNING] server.properties does not exist

So try creating a properties file and then try agian maybe.

Cherz again

---

### Post by DaFranz on 2012-08-05
The problem is that i cant give the server some swap, it is a rented vserver and the default installation doesnt generate swap. Also the command swapon is disabled for me :( At the moment i am trying every java out and writing down the differences, i also start the server with 3gig ram now. 

The server.properties warning is ok, this should happen upon the first start.

---

### Post by DaFranz on 2012-08-05
OpenJDK 6:
First start of the Server with 2GB Ram

> 2012-08-05 10:23:32 [INFO] Starting minecraft server version 1.3.1
2012-08-05 10:23:32 [INFO] Loading properties
2012-08-05 10:23:32 [WARNING] server.properties does not exist
2012-08-05 10:23:32 [INFO] Generating new properties file
2012-08-05 10:23:32 [INFO] Default game type: SURVIVAL
2012-08-05 10:23:32 [INFO] Generating keypair
2012-08-05 10:23:33 [INFO] Starting Minecraft server on *:25565
2012-08-05 10:23:34 [WARNING] Failed to load operators list: java.io.FileNotFoundException: ./ops.txt (No such file or directory)
2012-08-05 10:23:34 [WARNING] Failed to load white-list: java.io.FileNotFoundException: ./white-list.txt (No such file or directory)
2012-08-05 10:23:34 [INFO] Preparing level "world"
2012-08-05 10:23:35 [INFO] Preparing start region for level 0
2012-08-05 10:23:36 [INFO] Preparing spawn area: 3%
2012-08-05 10:23:37 [INFO] Preparing spawn area: 8%
2012-08-05 10:23:38 [INFO] Preparing spawn area: 12%
2012-08-05 10:23:39 [INFO] Preparing spawn area: 12%
2012-08-05 10:23:40 [INFO] Preparing spawn area: 16%
2012-08-05 10:23:41 [INFO] Preparing spawn area: 20%
2012-08-05 10:23:42 [INFO] Preparing spawn area: 24%
2012-08-05 10:23:43 [INFO] Preparing spawn area: 28%
2012-08-05 10:23:44 [INFO] Preparing spawn area: 32%
2012-08-05 10:23:45 [INFO] Preparing spawn area: 36%
2012-08-05 10:23:46 [INFO] Preparing spawn area: 40%
2012-08-05 10:23:47 [INFO] Preparing spawn area: 44%
2012-08-05 10:23:48 [INFO] Preparing spawn area: 48%
2012-08-05 10:23:49 [INFO] Preparing spawn area: 52%
This is the server.log, it says it prepared till 52% but the it prepared everything and i could also join the server. After joining Warning in the console "Can't keep it up". The server was rly lagging. But it just used 400M Ram so there is no need in more Ram, also the cpu is just at 0.3% .

Second start:
> root@h2057119:/opt/minecraft/server# sudo java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  Internal Error (nmethod.cpp:2175), pid=3075, tid=3078519616
#  guarantee(nm->_lock_count >= 0) failed: unmatched nmethod lock/unlock
#
# JRE version: 6.0_24-b24
# Java VM: OpenJDK Client VM (20.0-b12 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.11.3
# Distribution: Ubuntu 12.04 LTS, package 6b24-1.11.3-1ubuntu0.12.04.1
# An error report file with more information is saved as:
# /opt/minecraft/server/hs_err_pid3075.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
OpenJDK 7:
First start 2GB Ram, 500 used and 1.1% cpu usage.

Stoped here:
> root@h2057119:/opt/minecraft/server# sudo java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui
195 recipes
27 achievements
2012-08-05 10:36:35 [INFO] Starting minecraft server version 1.3.1
2012-08-05 10:36:35 [INFO] Loading properties
2012-08-05 10:36:35 [WARNING] server.properties does not exist
2012-08-05 10:36:35 [INFO] Generating new properties file
2012-08-05 10:36:35 [INFO] Default game type: SURVIVAL
2012-08-05 10:36:35 [INFO] Generating keypair
2012-08-05 10:36:36 [INFO] Starting Minecraft server on *:25565
2012-08-05 10:36:36 [WARNING] Failed to load operators list: java.io.FileNotFoundException: ./ops.txt (No such file or directory)
2012-08-05 10:36:36 [WARNING] Failed to load white-list: java.io.FileNotFoundException: ./white-list.txt (No such file or directory)
2012-08-05 10:36:36 [INFO] Preparing level "world"
Even with a pre generated world it stops at the same time.

Oracle Java 6:

I didnt figured out how to install this :(

Oracle Java 7:

First start with 2 GB Ram ended up in a fatal error after 1 second.

> root@h2057119:/opt/minecraft/server# sudo java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui
195 recipes
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  Internal Error (nmethod.cpp:2166), pid=5249, tid=3078302528
#  guarantee(nm->_lock_count >= 0) failed: unmatched nmethod lock/unlock
#
# JRE version: 7.0_05-b05
# Java VM: Java HotSpot(TM) Client VM (23.1-b03 mixed mode linux-x86 )
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# An error report file with more information is saved as:
# /opt/minecraft/server/hs_err_pid5249.log
#
# If you would like to submit a bug report, please visit:
#   [http://bugreport.sun.com/bugreport/crash.jsp](http://bugreport.sun.com/bugreport/crash.jsp)
#
I add the crash reports so u can have look into them. But i dont know what to do now, i tried everything.

---

### Post by DaFranz on 2012-08-05
Sorry for double post, but i forgot these 2 reports.

> #
# A fatal error has been detected by the Java Runtime Environment:
#
#  Internal Error (nmethod.cpp:2175), pid=3075, tid=3078519616
#  guarantee(nm->_lock_count >= 0) failed: unmatched nmethod lock/unlock
#
# JRE version: 6.0_24-b24
# Java VM: OpenJDK Client VM (20.0-b12 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.11.3
# Distribution: Ubuntu 12.04 LTS, package 6b24-1.11.3-1ubuntu0.12.04.1
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

---------------  T H R E A D  ---------------

Current thread (0xb7605400):  JavaThread "main" [_thread_in_vm, id=3076, stack(0xb7797000,0xb77e8000)]

Stack: [0xb7797000,0xb77e8000]
[error occurred during error reporting (printing stack bounds), id 0xb]


[error occurred during error reporting (printing native stack), id 0xb]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~RuntimeStub::resolve_opt_virtual_call
J  java.util.regex.Matcher.find()Z
j  java.util.regex.Pattern.split(Ljava/lang/CharSequence;I)[Ljava/lang/String;+31
j  java.lang.String.split(Ljava/lang/String;I)[Ljava/lang/String;+6
j  java.lang.String.split(Ljava/lang/String;)[Ljava/lang/String;+3
j  ak.a(Ljava/util/Properties;Ljava/lang/String;)V+78
j  ak.a(Ljava/lang/String;)V+24
j  ak.<init>(Ljava/lang/String;)V+21
j  ak.<clinit>()V+6
v  ~StubRoutines::call_stub
j  aj.<clinit>()V+0
v  ~StubRoutines::call_stub
j  rg.s()Ljava/lang/String;+22
j  ht.a([Lho;Ljava/lang/String;III)[Lho;+43
j  ht.c()V+13
j  rg.<clinit>()V+4074
v  ~StubRoutines::call_stub
j  aif.<clinit>()V+4720
v  ~StubRoutines::call_stub
j  ht.a(Ljava/lang/String;I)[Lho;+16
j  ht.<clinit>()V+549
v  ~StubRoutines::call_stub
j  net.minecraft.server.MinecraftServer.main([Ljava/lang/String;)V+0
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0xb763c400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=3082, stack(0xb4854000,0xb48a5000)]
  0xb763a400 JavaThread "C1 CompilerThread0" daemon [_thread_in_native, id=3081, stack(0xb48a5000,0xb4926000)]
  0xb7638c00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=3080, stack(0xb4926000,0xb4977000)]
  0xb7634800 JavaThread "Finalizer" daemon [_thread_blocked, id=3079, stack(0xb4c22000,0xb4c73000)]
  0xb7633000 JavaThread "Reference Handler" daemon [_thread_blocked, id=3078, stack(0xb4c73000,0xb4cc4000)]
=>0xb7605400 JavaThread "main" [_thread_in_vm, id=3076, stack(0xb7797000,0xb77e8000)]

Other Threads:
  0xb7631400 VMThread [stack: 0xb4cc4000,0xb4d45000] [id=3077]
  0xb763e800 WatcherThread [stack: 0xb47d3000,0xb4854000] [id=3083]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 629120K, used 11184K [0x0f780000, 0x3a220000, 0x3a220000)
  eden space 559232K,   2% used [0x0f780000, 0x1026c2a8, 0x319a0000)
  from space 69888K,   0% used [0x319a0000, 0x319a0000, 0x35de0000)
  to   space 69888K,   0% used [0x35de0000, 0x35de0000, 0x3a220000)
 tenured generation   total 1398144K, used 0K [0x3a220000, 0x8f780000, 0x8f780000)
   the space 1398144K,   0% used [0x3a220000, 0x3a220000, 0x3a220200, 0x8f780000)
 compacting perm gen  total 12288K, used 1168K [0x8f780000, 0x90380000, 0x93780000)
   the space 12288K,   9% used [0x8f780000, 0x8f8a4320, 0x8f8a4400, 0x90380000)
    ro space 10240K,  73% used [0x93780000, 0x93ee0cc8, 0x93ee0e00, 0x94180000)
    rw space 12288K,  60% used [0x94180000, 0x948ca478, 0x948ca600, 0x94d80000)

Code Cache  [0xb5600000, 0xb5698000, 0xb7600000)
 total_blobs=214 nmethods=73 adapters=77 free_code_cache=32955008 largest_free_block=64

Dynamic libraries:
00110000-001e8000 r-xp 00000000 00:4a 42418717                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
001e8000-001e9000 ---p 000d8000 00:4a 42418717                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
001e9000-001ed000 r--p 000d8000 00:4a 42418717                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
001ed000-001ee000 rw-p 000dc000 00:4a 42418717                           /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
001ee000-001f5000 rw-p 00000000 00:00 0 
001f5000-0021f000 r-xp 00000000 00:4a 42395372                           /lib/i386-linux-gnu/libm-2.15.so
0021f000-00220000 r--p 00029000 00:4a 42395372                           /lib/i386-linux-gnu/libm-2.15.so
00220000-00221000 rw-p 0002a000 00:4a 42395372                           /lib/i386-linux-gnu/libm-2.15.so
00221000-0023d000 r-xp 00000000 00:4a 42385507                           /lib/i386-linux-gnu/libgcc_s.so.1
0023d000-0023e000 r--p 0001b000 00:4a 42385507                           /lib/i386-linux-gnu/libgcc_s.so.1
0023e000-0023f000 rw-p 0001c000 00:4a 42385507                           /lib/i386-linux-gnu/libgcc_s.so.1
0023f000-0024a000 r-xp 00000000 00:4a 32399405                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
0024a000-0024b000 ---p 0000b000 00:4a 32399405                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
0024b000-0024c000 r--p 0000b000 00:4a 32399405                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
0024c000-0024d000 rw-p 0000c000 00:4a 32399405                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
0024d000-00263000 r-xp 00000000 00:4a 42395374                           /lib/i386-linux-gnu/libnsl-2.15.so
00263000-00264000 r--p 00015000 00:4a 42395374                           /lib/i386-linux-gnu/libnsl-2.15.so
00264000-00265000 rw-p 00016000 00:4a 42395374                           /lib/i386-linux-gnu/libnsl-2.15.so
00265000-00267000 rw-p 00000000 00:00 0 
00269000-0026c000 r-xp 00000000 00:4a 42395371                           /lib/i386-linux-gnu/libdl-2.15.so
0026c000-0026d000 r--p 00002000 00:4a 42395371                           /lib/i386-linux-gnu/libdl-2.15.so
0026d000-0026e000 rw-p 00003000 00:4a 42395371                           /lib/i386-linux-gnu/libdl-2.15.so
0026e000-00294000 r-xp 00000000 00:4a 32399369                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
00294000-00295000 r--p 00025000 00:4a 32399369                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
00295000-00297000 rw-p 00026000 00:4a 32399369                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
00297000-002a1000 r-xp 00000000 00:4a 42395379                           /lib/i386-linux-gnu/libnss_nis-2.15.so
002a1000-002a2000 r--p 00009000 00:4a 42395379                           /lib/i386-linux-gnu/libnss_nis-2.15.so
002a2000-002a3000 rw-p 0000a000 00:4a 42395379                           /lib/i386-linux-gnu/libnss_nis-2.15.so
00507000-0050e000 r-xp 00000000 00:4a 42395375                           /lib/i386-linux-gnu/libnss_compat-2.15.so
0050e000-0050f000 r--p 00006000 00:4a 42395375                           /lib/i386-linux-gnu/libnss_compat-2.15.so
0050f000-00510000 rw-p 00007000 00:4a 42395375                           /lib/i386-linux-gnu/libnss_compat-2.15.so
00564000-00703000 r-xp 00000000 00:4a 42395368                           /lib/i386-linux-gnu/libc-2.15.so
00703000-00705000 r--p 0019f000 00:4a 42395368                           /lib/i386-linux-gnu/libc-2.15.so
00705000-00706000 rw-p 001a1000 00:4a 42395368                           /lib/i386-linux-gnu/libc-2.15.so
00706000-00709000 rw-p 00000000 00:00 0 
00719000-00730000 r-xp 00000000 00:4a 42395382                           /lib/i386-linux-gnu/libpthread-2.15.so
00730000-00731000 r--p 00016000 00:4a 42395382                           /lib/i386-linux-gnu/libpthread-2.15.so
00731000-00732000 rw-p 00017000 00:4a 42395382                           /lib/i386-linux-gnu/libpthread-2.15.so
00732000-00734000 rw-p 00000000 00:00 0 
007fd000-007fe000 r-xp 00000000 00:00 0                                  [vdso]
00943000-0094a000 r-xp 00000000 00:4a 32399372                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
0094a000-0094b000 r--p 00006000 00:4a 32399372                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
0094b000-0094c000 rw-p 00007000 00:4a 32399372                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
00960000-0096b000 r-xp 00000000 00:4a 42395377                           /lib/i386-linux-gnu/libnss_files-2.15.so
0096b000-0096c000 r--p 0000a000 00:4a 42395377                           /lib/i386-linux-gnu/libnss_files-2.15.so
0096c000-0096d000 rw-p 0000b000 00:4a 42395377                           /lib/i386-linux-gnu/libnss_files-2.15.so
0097b000-0098f000 r-xp 00000000 00:4a 42385544                           /lib/i386-linux-gnu/libz.so.1.2.3.4
0098f000-00990000 r--p 00013000 00:4a 42385544                           /lib/i386-linux-gnu/libz.so.1.2.3.4
00990000-00991000 rw-p 00014000 00:4a 42385544                           /lib/i386-linux-gnu/libz.so.1.2.3.4
00a9b000-00aa2000 r-xp 00000000 00:4a 42395384                           /lib/i386-linux-gnu/librt-2.15.so
00aa2000-00aa3000 r--p 00006000 00:4a 42395384                           /lib/i386-linux-gnu/librt-2.15.so
00aa3000-00aa4000 rw-p 00007000 00:4a 42395384                           /lib/i386-linux-gnu/librt-2.15.so
00c70000-00c90000 r-xp 00000000 00:4a 42395365                           /lib/i386-linux-gnu/ld-2.15.so
00c90000-00c91000 r--p 0001f000 00:4a 42395365                           /lib/i386-linux-gnu/ld-2.15.so
00c91000-00c92000 rw-p 00020000 00:4a 42395365                           /lib/i386-linux-gnu/ld-2.15.so
00cd7000-00cdb000 r-xp 00000000 00:4a 32399398                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
00cdb000-00cdc000 r--p 00003000 00:4a 32399398                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
00cdc000-00cdd000 rw-p 00004000 00:4a 32399398                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
00cdd000-011f0000 r-xp 00000000 00:4a 32399388                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
011f0000-01207000 r--p 00512000 00:4a 32399388                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
01207000-01214000 rw-p 00529000 00:4a 32399388                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
01214000-0162c000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 00:4a 32384848                           /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
08051000-08052000 r--p 00008000 00:4a 32384848                           /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
08052000-08053000 rw-p 00009000 00:4a 32384848                           /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
09a8d000-09afe000 rw-p 00000000 00:00 0                                  [heap]
0f780000-90380000 rw-p 00000000 00:00 0 
90380000-93780000 rw-p 00000000 00:00 0 
93780000-93ee1000 r--s 00001000 00:4a 32399494                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
93ee1000-94180000 rw-p 00000000 00:00 0 
94180000-948cb000 rw-p 00762000 00:4a 32399494                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
948cb000-94d80000 rw-p 00000000 00:00 0 
94d80000-94e7c000 rw-p 00ead000 00:4a 32399494                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
94e7c000-95180000 rw-p 00000000 00:00 0 
95180000-95188000 r-xs 00fa9000 00:4a 32399494                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
95188000-95580000 rw-p 00000000 00:00 0 
b47c5000-b47d3000 r--s 001aa000 00:4a 32407557                           /opt/minecraft/server/minecraft_server.jar
b47d3000-b47d4000 ---p 00000000 00:00 0 
b47d4000-b4854000 rw-p 00000000 00:00 0 
b4854000-b4857000 ---p 00000000 00:00 0 
b4857000-b48a5000 rw-p 00000000 00:00 0 
b48a5000-b48a8000 ---p 00000000 00:00 0 
b48a8000-b4926000 rw-p 00000000 00:00 0 
b4926000-b4929000 ---p 00000000 00:00 0 
b4929000-b4977000 rw-p 00000000 00:00 0 
b4977000-b4b00000 r--p 00000000 00:4a 32343762                           /usr/lib/locale/locale-archive
b4b00000-b4b21000 rw-p 00000000 00:00 0 
b4b21000-b4c00000 ---p 00000000 00:00 0 
b4c01000-b4c08000 r--s 000fb000 00:4a 32384238                           /usr/lib/jvm/java-6-openjdk-common/jre/lib/resources.jar
b4c08000-b4c0a000 r--s 00001000 00:4a 32384236                           /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/dnsns.jar
b4c0a000-b4c0e000 r--s 00038000 00:4a 32384235                           /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/sunpkcs11.jar
b4c0e000-b4c11000 r--s 00031000 00:4a 32384233                           /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/sunjce_provider.jar
b4c11000-b4c14000 r--s 00077000 00:4a 32384234                           /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/localedata.jar
b4c14000-b4c22000 r--s 001aa000 00:4a 32407557                           /opt/minecraft/server/minecraft_server.jar
b4c22000-b4c25000 ---p 00000000 00:00 0 
b4c25000-b4c73000 rw-p 00000000 00:00 0 
b4c73000-b4c76000 ---p 00000000 00:00 0 
b4c76000-b4cc4000 rw-p 00000000 00:00 0 
b4cc4000-b4cc5000 ---p 00000000 00:00 0 
b4cc5000-b4d78000 rw-p 00000000 00:00 0 
b4d78000-b4f08000 r--s 037bc000 00:4a 32384855                           /usr/lib/jvm/java-6-openjdk-i386/jre/lib/rt.jar
b4f08000-b4f0f000 rw-p 00000000 00:00 0 
b4f0f000-b4f29000 rw-p 00000000 00:00 0 
b4f29000-b55da000 rw-p 00000000 00:00 0 
b55da000-b55f4000 rw-p 00000000 00:00 0 
b55f4000-b5600000 rw-p 00000000 00:00 0 
b5600000-b5698000 rwxp 00000000 00:00 0 
b5698000-b76b7000 rw-p 00000000 00:00 0 
b76b7000-b7700000 ---p 00000000 00:00 0 
b7702000-b7712000 rw-p 00000000 00:00 0 
b7712000-b778f000 rw-p 00000000 00:00 0 
b778f000-b7797000 rw-s 00000000 00:4a 32399493                           /tmp/hsperfdata_root/3075
b7797000-b779a000 ---p 00000000 00:00 0 
b779a000-b77eb000 rw-p 00000000 00:00 0 
b77eb000-b77ed000 r--s 0000f000 00:4a 32384232                           /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/pulse-java.jar
b77ed000-b77ee000 rw-p 00000000 00:00 0 
b77ee000-b77ef000 r--p 00000000 00:00 0 
b77ef000-b77f1000 rw-p 00000000 00:00 0 
bfc9a000-bfcd0000 rw-p 00000000 00:00 0                                  [stack]

VM Arguments:
jvm_args: -Xmx2048M -Xms2048M 
java_command: minecraft_server.jar nogui
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
USERNAME=root
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386:/usr/lib/jvm/java-6-openjdk-i386/jre/../lib/i386
SHELL=/bin/bash

Signal Handlers:
SIGSEGV: [libjvm.so+0x3e3530], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3e3530], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x300e50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x300e50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x300e50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x300e50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x300ce0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x303d80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x303d80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x303d80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x303d80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 12.04 (precise)
uname:Linux 2.6.32-042stab055.12 #1 SMP Wed May 23 16:07:36 MSD 2012 i686
libc:glibc 2.15 NPTL 2.15 
rlimit: STACK 10240k, CORE 0k, NPROC 127270, NOFILE 1024, AS infinity
load average:0.63 0.35 0.17

/proc/meminfo:
MemTotal:        4194304 kB
MemFree:         3810564 kB
Cached:           354624 kB
Active:           199404 kB
Inactive:         173580 kB
Active(anon):      18320 kB
Inactive(anon):       40 kB
Active(file):     181084 kB
Inactive(file):   173540 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                52 kB
Writeback:             0 kB
AnonPages:         18360 kB
Shmem:              2612 kB
Slab:              10680 kB
SReclaimable:       8280 kB
SUnreclaim:         2400 kB


CPU:total 1 (4 cores per cpu, 1 threads per core) family 16 model 2 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext, 3dnowpref, lzcnt, sse4a

Memory: 4k page, physical 4194304k(3810564k free), swap 0k(0k free)

vm_info: OpenJDK Client VM (20.0-b12) for linux-x86 JRE (1.6.0_24-b24), built on Jun 26 2012 22:38:21 by "buildd" with gcc 4.6.3

time: Sun Aug  5 12:26:09 2012
elapsed time: 0 seconds



Sorry cant post second, it tells my bb code limition ??

---

### Post by zero2xiii on 2012-08-05
Hay,

Interesting. Seems like something else might be the issue rather than the java then. Can't see that it is a memory error. However try starting with a lower memory dedication:

```
java -Xms256M -Xmx2048M -jar minecraft_server.jar nogui
```

A quick google with "**guarantee(nm->_lock_count >= 0) failed: unmatched nmethod lock/unlock"** gave [this result]("https://redmine.personalized-software.ie/projects/opensource/wiki/Java_openVZ_Futex_issue") that seems like it might have a relation to yours. There is a workaround but I am unsure if it will work for you. Give it a try.

Also a mine craft server with those specs should not be "lagging" according to the minecraft wiki on ubuntu a dual core system with 2 gig ram will be fine.

I suggest you stick to the java you actualy got the server to start atleast. And trouble shoot the slow response rather. It might lead you to the issue via a back alley, but I have a strong feeling it will be the same issue causing both.

I tried to duplicate the problem. No such luck. On ubuntu 12.04_64 with oracle 7 installed I ran your exact command and the server started up with no issues what so ever, I could also connect and play and had no lagging issues like you describe. This is on a core2due 1.8Ghz system with 2 gig ram installed with a 4gig swap space (which I disabled for testing purposes).

Cherz

---

### Post by DaFranz on 2012-08-05
I think i located the issue, after googling for hours i found a german post about the same problem with java at my hoster. I looks like that the kernel for 12.04 is a bit diffrent to the 10.04 kernel, so i installed ubuntu 10 , java and minecraft started minecraft and how i can see no problems ... . Looks like the problem is the kernel.

---

### Post by zero2xiii on 2012-08-05
Yes, it might be. As stated in the post I linked to aswell. They say it has been fixed in a certain kernel. I have Kernel Linux 3.2.0-24-generic installed. Never checked.

Well all the best.
Cherz:guitar:

---

### Post by jamesloon on 2013-03-31
I have that exact error report except mine will work (until a certain point) where the game just crashes (most frequently in the nether) and I came here to figure out how to enable core dumps for both the server and the console.

Also I noticed there was not any admin help here for a simple fix of enabling coredumps in ubuntu (searched for it to no a-vale)
EDIT: did not notice other pages looking through them now
EDIT 2: Nope still a problem and everything been updated to the most recent (LTS release update) but I might try lowering the memory allotment)

---

