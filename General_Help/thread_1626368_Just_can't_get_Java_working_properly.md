---
title: "Just can't get Java working properly"
date: 2010-11-20
forum: General Help
---

### Post by Tratz on 2010-11-20
I've been hammering at this for nearly 3 weeks and just can't figure it out. I can't get java applications to run properly in a lot of cases. I've tried completely removing Java and reinstalling it. I've tried removing Iced Tea and OpenJDK and installing Sun Java instead. I've done a complete, clean reinstall of Ubuntu. The symptoms of my problem never seem to change. Minecraft is the best example I can give you. As soon as the game loads (in the web or on the desktop alike) it closes abruptly. This is what's in the log file.

```

# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00900416, pid=5280, tid=1785957232
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (17.0-b16 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.1
# Distribution: Ubuntu 10.10, package 6b20-1.9.1-1ubuntu3
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x000014a0

Registers:
EAX=0x00000000, EBX=0x000014a0, ECX=0x000014c5, EDX=0x0000000b
ESP=0x6a738288, EBP=0x6a738294, ESI=0x00000020, EDI=0x0093fff4
EIP=0x00900416, CR2=0x00000004, EFLAGS=0x00200206

Top of Stack: (sp=0x6a738288)
0x6a738288:   00937990 0093fff4 04f04980 6a738398
0x6a738298:   04a1fa53 0000000b 00000000 00000000
0x6a7382a8:   00000000 00001000 00000000 00000000
0x6a7382b8:   00000000 00000000 00000000 7fffffff
0x6a7382c8:   fffffffe ffffffff ffffffff ffffffff
0x6a7382d8:   ffffffff ffffffff ffffffff ffffffff
0x6a7382e8:   ffffffff ffffffff ffffffff ffffffff
0x6a7382f8:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0x00900416)
0x00900406:   cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90 cd 80
0x00900416:   c3 00 2e 73 68 73 74 72 74 61 62 00 2e 68 61 73 

Stack: [0x6a728000,0x6a739000],  sp=0x6a738288,  free space=406a737cf0k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x416]  __kernel_vsyscall+0x2
C  [fglrx_dri.so+0x167ea53]
C  [libpthread.so.0+0x5cc9]


[error occurred during error reporting (printing target Java thread stack), id 0xb]


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 152896K, used 15537K [0x9f110000, 0xa9bb0000, 0xb4660000)
  eden space 131072K, 11% used [0x9f110000,0xa003c6e0,0xa7110000)
  from space 21824K, 0% used [0xa7110000,0xa7110000,0xa8660000)
  to   space 21824K, 0% used [0xa8660000,0xa8660000,0xa9bb0000)
 PSOldGen        total 349568K, used 12384K [0x74660000, 0x89bc0000, 0x9f110000)
  object space 349568K, 3% used [0x74660000,0x752782d8,0x89bc0000)
 PSPermGen       total 30720K, used 15525K [0x6c660000, 0x6e460000, 0x74660000)
  object space 30720K, 50% used [0x6c660000,0x6d589448,0x6e460000)

Dynamic libraries:
00110000-0011e000 r-xp 00000000 08:04 2231054    /usr/lib/libXext.so.6.4.0
0011e000-0011f000 r--p 0000d000 08:04 2231054    /usr/lib/libXext.so.6.4.0
0011f000-00120000 rw-p 0000e000 08:04 2231054    /usr/lib/libXext.so.6.4.0
00120000-0012c000 r-xp 00000000 08:04 2231062    /usr/lib/libXi.so.6.1.0
0012c000-0012d000 r--p 0000b000 08:04 2231062    /usr/lib/libXi.so.6.1.0
0012d000-0012e000 rw-p 0000c000 08:04 2231062    /usr/lib/libXi.so.6.1.0
0012e000-00146000 r-xp 00000000 08:04 2232003    /usr/lib/libxcb.so.1.1.0
00146000-00147000 r--p 00017000 08:04 2232003    /usr/lib/libxcb.so.1.1.0
00147000-00148000 rw-p 00018000 08:04 2232003    /usr/lib/libxcb.so.1.1.0
00148000-0014c000 r-xp 00000000 08:04 2231052    /usr/lib/libXdmcp.so.6.0.0
0014c000-0014d000 r--p 00003000 08:04 2231052    /usr/lib/libXdmcp.so.6.0.0
0014d000-0014e000 rw-p 00004000 08:04 2231052    /usr/lib/libXdmcp.so.6.0.0
0014e000-0014f000 r-xp 00000000 08:04 2240788    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
0014f000-00150000 r--p 00000000 08:04 2240788    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00150000-00151000 rw-p 00001000 08:04 2240788    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00153000-0015e000 r-xp 00000000 08:04 2240802    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
0015e000-0015f000 ---p 0000b000 08:04 2240802    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
0015f000-00160000 r--p 0000b000 08:04 2240802    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00160000-00161000 rw-p 0000c000 08:04 2240802    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00161000-00165000 r-xp 00000000 08:04 2231056    /usr/lib/libXfixes.so.3.1.0
00165000-00166000 r--p 00003000 08:04 2231056    /usr/lib/libXfixes.so.3.1.0
00166000-00167000 rw-p 00004000 08:04 2231056    /usr/lib/libXfixes.so.3.1.0
00167000-00169000 r-xp 00000000 08:04 1311210    /lib/libdl-2.12.1.so
00169000-0016a000 r--p 00001000 08:04 1311210    /lib/libdl-2.12.1.so
0016a000-0016b000 rw-p 00002000 08:04 1311210    /lib/libdl-2.12.1.so
0016b000-002c2000 r-xp 00000000 08:04 1311207    /lib/libc-2.12.1.so
002c2000-002c3000 ---p 00157000 08:04 1311207    /lib/libc-2.12.1.so
002c3000-002c5000 r--p 00157000 08:04 1311207    /lib/libc-2.12.1.so
002c5000-002c6000 rw-p 00159000 08:04 1311207    /lib/libc-2.12.1.so
002c6000-002c9000 rw-p 00000000 00:00 0 
002c9000-0034b000 r-xp 00000000 08:04 2240777    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
0034b000-0034c000 r--p 00081000 08:04 2240777    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
0034c000-00352000 rw-p 00082000 08:04 2240777    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00352000-00377000 rw-p 00000000 00:00 0 
00377000-0037f000 r-xp 00000000 08:04 2231048    /usr/lib/libXcursor.so.1.0.2
0037f000-00380000 r--p 00007000 08:04 2231048    /usr/lib/libXcursor.so.1.0.2
00380000-00381000 rw-p 00008000 08:04 2231048    /usr/lib/libXcursor.so.1.0.2
00381000-0038a000 r-xp 00000000 08:04 2240790    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
0038a000-0038b000 r--p 00008000 08:04 2240790    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
0038b000-0038c000 rw-p 00009000 08:04 2240790    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
0038c000-003a0000 r-xp 00000000 08:04 2240796    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
003a0000-003a1000 r--p 00013000 08:04 2240796    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
003a1000-003a2000 rw-p 00014000 08:04 2240796    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
003a2000-003a4000 r-xp 00000000 08:04 2231064    /usr/lib/libXinerama.so.1.0.0
003a4000-003a5000 r--p 00001000 08:04 2231064    /usr/lib/libXinerama.so.1.0.0
003a5000-003a6000 rw-p 00002000 08:04 2231064    /usr/lib/libXinerama.so.1.0.0
003a6000-003ca000 r-xp 00000000 08:04 1311211    /lib/libm-2.12.1.so
003ca000-003cb000 r--p 00023000 08:04 1311211    /lib/libm-2.12.1.so
003cb000-003cc000 rw-p 00024000 08:04 1311211    /lib/libm-2.12.1.so
003cc000-003f9000 r-xp 00000000 08:04 2240793    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
003f9000-003fa000 r--p 0002c000 08:04 2240793    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
003fa000-003fb000 rw-p 0002d000 08:04 2240793    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
003fb000-003fd000 rw-p 00000000 00:00 0 
003fd000-0040d000 r-xp 00000000 08:04 1311222    /lib/libresolv-2.12.1.so
0040d000-0040e000 r--p 00010000 08:04 1311222    /lib/libresolv-2.12.1.so
0040e000-0040f000 rw-p 00011000 08:04 1311222    /lib/libresolv-2.12.1.so
0040f000-00411000 rw-p 00000000 00:00 0 
00411000-00414000 r-xp 00000000 08:04 1705270    /home/tratz/.minecraft/bin/natives/libjinput-linux.so
00414000-00415000 r--p 00002000 08:04 1705270    /home/tratz/.minecraft/bin/natives/libjinput-linux.so
00415000-00416000 rw-p 00003000 08:04 1705270    /home/tratz/.minecraft/bin/natives/libjinput-linux.so
00418000-00421000 r-xp 00000000 08:04 1311218    /lib/libnss_nis-2.12.1.so
00421000-00422000 r--p 00008000 08:04 1311218    /lib/libnss_nis-2.12.1.so
00422000-00423000 rw-p 00009000 08:04 1311218    /lib/libnss_nis-2.12.1.so
00423000-00495000 r-xp 00000000 08:04 2228602    /usr/lib/libfreetype.so.6.6.0
00495000-00499000 r--p 00071000 08:04 2228602    /usr/lib/libfreetype.so.6.6.0
00499000-0049a000 rw-p 00075000 08:04 2228602    /usr/lib/libfreetype.so.6.6.0
0049a000-004a0000 r-xp 00000000 08:04 2231074    /usr/lib/libXrandr.so.2.2.0
004a0000-004a1000 r--p 00005000 08:04 2231074    /usr/lib/libXrandr.so.2.2.0
004a1000-004a2000 rw-p 00006000 08:04 2231074    /usr/lib/libXrandr.so.2.2.0
004a7000-004ea000 r-xp 00000000 08:04 2241272    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
004ea000-004eb000 r--p 00042000 08:04 2241272    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
004eb000-004ed000 rw-p 00043000 08:04 2241272    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
004ed000-004ee000 rw-p 00000000 00:00 0 
004ee000-00607000 r-xp 00000000 08:04 2231037    /usr/lib/libX11.so.6.3.0
00607000-00608000 r--p 00118000 08:04 2231037    /usr/lib/libX11.so.6.3.0
00608000-0060a000 rw-p 00119000 08:04 2231037    /usr/lib/libX11.so.6.3.0
0060a000-0060b000 rw-p 00000000 00:00 0 
0060b000-00662000 r-xp 00000000 08:04 1705272    /home/tratz/.minecraft/bin/natives/liblwjgl.so
00662000-00663000 r--p 00056000 08:04 1705272    /home/tratz/.minecraft/bin/natives/liblwjgl.so
00663000-00664000 rw-p 00057000 08:04 1705272    /home/tratz/.minecraft/bin/natives/liblwjgl.so
00664000-00718000 r-xp 00000000 08:04 2239375    /usr/lib/libGL.so.1.2
00718000-00723000 rwxp 000b3000 08:04 2239375    /usr/lib/libGL.so.1.2
00723000-00728000 rwxp 00000000 00:00 0 
00728000-00759000 r-xp 00000000 08:04 2239377    /usr/lib/libatiadlxx.so
00759000-0075a000 rw-p 00030000 08:04 2239377    /usr/lib/libatiadlxx.so
0075a000-00799000 r-xp 00000000 08:04 2231801    /usr/lib/libpulse.so.0.12.2
00799000-0079a000 ---p 0003f000 08:04 2231801    /usr/lib/libpulse.so.0.12.2
0079a000-0079b000 r--p 0003f000 08:04 2231801    /usr/lib/libpulse.so.0.12.2
0079b000-0079c000 rw-p 00040000 08:04 2231801    /usr/lib/libpulse.so.0.12.2
0079c000-007a3000 r-xp 00000000 08:04 2231033    /usr/lib/libSM.so.6.0.1
007a3000-007a4000 r--p 00006000 08:04 2231033    /usr/lib/libSM.so.6.0.1
007a4000-007a5000 rw-p 00007000 08:04 2231033    /usr/lib/libSM.so.6.0.1
007a5000-007a8000 r-xp 00000000 08:04 2231991    /usr/lib/libxcb-atom.so.1.0.0
007a8000-007a9000 r--p 00002000 08:04 2231991    /usr/lib/libxcb-atom.so.1.0.0
007a9000-007aa000 rw-p 00003000 08:04 2231991    /usr/lib/libxcb-atom.so.1.0.0
007aa000-007ad000 r-xp 00000000 08:04 1310907    /lib/libuuid.so.1.3.0
007ad000-007ae000 r--p 00002000 08:04 1310907    /lib/libuuid.so.1.3.0
007ae000-007af000 rw-p 00003000 08:04 1310907    /lib/libuuid.so.1.3.0
007af000-007d5000 r-xp 00000000 08:04 2231960    /usr/lib/libvorbis.so.0.4.4
007d5000-007d6000 r--p 00025000 08:04 2231960    /usr/lib/libvorbis.so.0.4.4
007d6000-007d7000 rw-p 00026000 08:04 2231960    /usr/lib/libvorbis.so.0.4.4
007db000-007f0000 r-xp 00000000 08:04 2231012    /usr/lib/libICE.so.6.3.0
007f0000-007f1000 r--p 00014000 08:04 2231012    /usr/lib/libICE.so.6.3.0
007f1000-007f2000 rw-p 00015000 08:04 2231012    /usr/lib/libICE.so.6.3.0
007f2000-007f4000 rw-p 00000000 00:00 0 
007f4000-007f9000 r-xp 00000000 08:04 2231724    /usr/lib/libogg.so.0.7.0
007f9000-007fa000 r--p 00004000 08:04 2231724    /usr/lib/libogg.so.0.7.0
007fa000-007fb000 rw-p 00005000 08:04 2231724    /usr/lib/libogg.so.0.7.0
007fd000-0081f000 r-xp 00000000 08:04 2240786    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0081f000-00820000 r--p 00021000 08:04 2240786    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00820000-00822000 rw-p 00022000 08:04 2240786    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00836000-0083d000 r-xp 00000000 08:04 2240797    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
0083d000-0083e000 r--p 00006000 08:04 2240797    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
0083e000-0083f000 rw-p 00007000 08:04 2240797    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
0083f000-00887000 r-xp 00000000 08:04 2234077    /usr/lib/libpulsecommon-0.9.21.so
00887000-00888000 r--p 00047000 08:04 2234077    /usr/lib/libpulsecommon-0.9.21.so
00888000-00889000 rw-p 00048000 08:04 2234077    /usr/lib/libpulsecommon-0.9.21.so
00897000-008b1000 r-xp 00000000 08:04 1310799    /lib/libgcc_s.so.1
008b1000-008b2000 r--p 00019000 08:04 1310799    /lib/libgcc_s.so.1
008b2000-008b3000 rw-p 0001a000 08:04 1310799    /lib/libgcc_s.so.1
008b3000-008ed000 r-xp 00000000 08:04 1310777    /lib/libdbus-1.so.3.5.2
008ed000-008ee000 r--p 00039000 08:04 1310777    /lib/libdbus-1.so.3.5.2
008ee000-008ef000 rw-p 0003a000 08:04 1310777    /lib/libdbus-1.so.3.5.2
00900000-00901000 r-xp 00000000 00:00 0          [vdso]
00929000-0093e000 r-xp 00000000 08:04 1311221    /lib/libpthread-2.12.1.so
0093e000-0093f000 ---p 00015000 08:04 1311221    /lib/libpthread-2.12.1.so
0093f000-00940000 r--p 00015000 08:04 1311221    /lib/libpthread-2.12.1.so
00940000-00941000 rw-p 00016000 08:04 1311221    /lib/libpthread-2.12.1.so
00941000-00943000 rw-p 00000000 00:00 0 
00943000-0098d000 r-xp 00000000 08:04 2230999    /usr/lib/libFLAC.so.8.2.0
0098d000-0098e000 r--p 00049000 08:04 2230999    /usr/lib/libFLAC.so.8.2.0
0098e000-0098f000 rw-p 0004a000 08:04 2230999    /usr/lib/libFLAC.so.8.2.0
0099d000-009a1000 r-xp 00000000 08:04 2231082    /usr/lib/libXtst.so.6.1.0
009a1000-009a2000 r--p 00003000 08:04 2231082    /usr/lib/libXtst.so.6.1.0
009a2000-009a3000 rw-p 00004000 08:04 2231082    /usr/lib/libXtst.so.6.1.0
009d1000-009d8000 r-xp 00000000 08:04 1310909    /lib/libwrap.so.0.7.6
009d8000-009d9000 r--p 00006000 08:04 1310909    /lib/libwrap.so.0.7.6
009d9000-009da000 rw-p 00007000 08:04 1310909    /lib/libwrap.so.0.7.6
00a17000-00a1a000 r-xp 00000000 08:04 2240774    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00a1a000-00a1b000 r--p 00002000 08:04 2240774    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00a1b000-00a1c000 rw-p 00003000 08:04 2240774    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00a1c000-00a7d000 r-xp 00000000 08:04 2231868    /usr/lib/libsndfile.so.1.0.21
00a7d000-00a7e000 ---p 00061000 08:04 2231868    /usr/lib/libsndfile.so.1.0.21
00a7e000-00a7f000 r--p 00061000 08:04 2231868    /usr/lib/libsndfile.so.1.0.21
00a7f000-00a80000 rw-p 00062000 08:04 2231868    /usr/lib/libsndfile.so.1.0.21
00a80000-00a84000 rw-p 00000000 00:00 0 
00abb000-00ac3000 r-xp 00000000 08:04 2231076    /usr/lib/libXrender.so.1.3.0
00ac3000-00ac4000 r--p 00007000 08:04 2231076    /usr/lib/libXrender.so.1.3.0
00ac4000-00ac5000 rw-p 00008000 08:04 2231076    /usr/lib/libXrender.so.1.3.0
00ae6000-00af0000 r-xp 00000000 08:04 1311216    /lib/libnss_files-2.12.1.so
00af0000-00af1000 r--p 00009000 08:04 1311216    /lib/libnss_files-2.12.1.so
00af1000-00af2000 rw-p 0000a000 08:04 1311216    /lib/libnss_files-2.12.1.so
00af8000-00b3c000 r-xp 00000000 08:04 2240779    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00b3c000-00b3e000 r--p 00043000 08:04 2240779    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00b3e000-00b3f000 rw-p 00045000 08:04 2240779    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00b3f000-00b44000 rw-p 00000000 00:00 0 
00b54000-00b58000 r-xp 00000000 08:04 2232330    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
00b58000-00b59000 r--p 00003000 08:04 2232330    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
00b59000-00b5a000 rw-p 00004000 08:04 2232330    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
00b71000-00b78000 r-xp 00000000 08:04 1311223    /lib/librt-2.12.1.so
00b78000-00b79000 r--p 00006000 08:04 1311223    /lib/librt-2.12.1.so
00b79000-00b7a000 rw-p 00007000 08:04 1311223    /lib/librt-2.12.1.so
00bb9000-00bcc000 r-xp 00000000 08:04 1311213    /lib/libnsl-2.12.1.so
00bcc000-00bcd000 r--p 00012000 08:04 1311213    /lib/libnsl-2.12.1.so
00bcd000-00bce000 rw-p 00013000 08:04 1311213    /lib/libnsl-2.12.1.so
00bce000-00bd0000 rw-p 00000000 00:00 0 
00bd9000-00bec000 r-xp 00000000 08:04 1310914    /lib/libz.so.1.2.3.4
00bec000-00bed000 r--p 00012000 08:04 1310914    /lib/libz.so.1.2.3.4
00bed000-00bee000 rw-p 00013000 08:04 1310914    /lib/libz.so.1.2.3.4
00c08000-00c0a000 r-xp 00000000 08:04 2231041    /usr/lib/libXau.so.6.0.0
00c0a000-00c0b000 r--p 00001000 08:04 2231041    /usr/lib/libXau.so.6.0.0
00c0b000-00c0c000 rw-p 00002000 08:04 2231041    /usr/lib/libXau.so.6.0.0
00c0c000-00c31000 r-xp 00000000 08:04 1705274    /home/tratz/.minecraft/bin/natives/libopenal.so
00c31000-00c32000 rw-p 00025000 08:04 1705274    /home/tratz/.minecraft/bin/natives/libopenal.so
00c32000-00d1f000 rw-p 00000000 00:00 0 
00d27000-00d2d000 r-xp 00000000 08:04 2240803    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00d2d000-00d2e000 r--p 00005000 08:04 2240803    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00d2e000-00d2f000 rw-p 00006000 08:04 2240803    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00d56000-00d58000 r-xp 00000000 08:04 1310837    /lib/libnss_mdns4_minimal.so.2
00d58000-00d59000 r--p 00001000 08:04 1310837    /lib/libnss_mdns4_minimal.so.2
00d59000-00d5a000 rw-p 00002000 08:04 1310837    /lib/libnss_mdns4_minimal.so.2
00d96000-00d9d000 r-xp 00000000 08:04 2239650    /usr/lib/libatiuki.so.1.0
00d9d000-00d9e000 rw-p 00006000 08:04 2239650    /usr/lib/libatiuki.so.1.0
00d9e000-00da4000 r-xp 00000000 08:04 1311214    /lib/libnss_compat-2.12.1.so
00da4000-00da5000 r--p 00006000 08:04 1311214    /lib/libnss_compat-2.12.1.so
00da5000-00da6000 rw-p 00007000 08:04 1311214    /lib/libnss_compat-2.12.1.so
00dc4000-00dc5000 r-xp 00000000 08:04 2231035    /usr/lib/libX11-xcb.so.1.0.0
00dc5000-00dc6000 r--p 00000000 08:04 2231035    /usr/lib/libX11-xcb.so.1.0.0
00dc6000-00dc7000 rw-p 00001000 08:04 2231035    /usr/lib/libX11-xcb.so.1.0.0
00ddd000-00de1000 r-xp 00000000 08:04 1311215    /lib/libnss_dns-2.12.1.so
00de1000-00de2000 r--p 00004000 08:04 1311215    /lib/libnss_dns-2.12.1.so
00de2000-00de3000 rw-p 00005000 08:04 1311215    /lib/libnss_dns-2.12.1.so
00de3000-00ea3000 r-xp 00000000 08:04 2228467    /usr/lib/libasound.so.2.0.0
00ea3000-00ea4000 ---p 000c0000 08:04 2228467    /usr/lib/libasound.so.2.0.0
00ea4000-00ea8000 r--p 000c0000 08:04 2228467    /usr/lib/libasound.so.2.0.0
00ea8000-00ea9000 rw-p 000c4000 08:04 2228467    /usr/lib/libasound.so.2.0.0
00f40000-00f46000 r-xp 00000000 08:04 2240805    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00f46000-00f47000 r--p 00005000 08:04 2240805    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00f47000-00f48000 rw-p 00006000 08:04 2240805    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00fa5000-00fc1000 r-xp 00000000 08:04 1311201    /lib/ld-2.12.1.so
00fc1000-00fc2000 r--p 0001b000 08:04 1311201    /lib/ld-2.12.1.so
00fc2000-00fc3000 rw-p 0001c000 08:04 1311201    /lib/ld-2.12.1.so
00fc3000-01645000 r-xp 00000000 08:04 2240807    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
01645000-01646000 ---p 00682000 08:04 2240807    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
01646000-0168b000 r--p 00682000 08:04 2240807    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
0168b000-0169a000 rw-p 006c7000 08:04 2240807    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
0169a000-01aba000 rw-p 00000000 00:00 0 
01aba000-01c1f000 r-xp 00000000 08:04 2231962    /usr/lib/libvorbisenc.so.2.0.7
01c1f000-01c20000 ---p 00165000 08:04 2231962    /usr/lib/libvorbisenc.so.2.0.7
01c20000-01c31000 r--p 00165000 08:04 2231962    /usr/lib/libvorbisenc.so.2.0.7
01c31000-01c32000 rw-p 00176000 08:04 2231962    /usr/lib/libvorbisenc.so.2.0.7
033a1000-04db7000 r-xp 00000000 08:04 2239655    /usr/lib/dri/fglrx_dri.so
04db7000-04e7b000 rw-p 01a15000 08:04 2239655    /usr/lib/dri/fglrx_dri.so
04e7b000-04f06000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 08:04 2240835    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:04 2240835    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:04 2240835    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08542000-08dc7000 rw-p 00000000 00:00 0          [heap]
59100000-59121000 rw-p 00000000 00:00 0 
59121000-59200000 ---p 00000000 00:00 0 
592ac000-592af000 ---p 00000000 00:00 0 
592af000-592fd000 rw-p 00000000 00:00 0 
592fd000-592fe000 ---p 00000000 00:00 0 
592fe000-594fe000 rw-p 00000000 00:00 0 
594fe000-594ff000 ---p 00000000 00:00 0 
594ff000-596ff000 rw-p 00000000 00:00 0 
596ff000-59700000 ---p 00000000 00:00 0 
59700000-59900000 rw-p 00000000 00:00 0 
59900000-599d4000 rw-p 00000000 00:00 0 
599d4000-59a00000 ---p 00000000 00:00 0 
59a0d000-59a10000 ---p 00000000 00:00 0 
59a10000-59a5e000 rw-p 00000000 00:00 0 
59a5e000-59a61000 ---p 00000000 00:00 0 
59a61000-59aaf000 rw-p 00000000 00:00 0 
59aaf000-59ab2000 ---p 00000000 00:00 0 
59ab2000-59b00000 rw-p 00000000 00:00 0 
59b00000-59bfd000 rw-p 00000000 00:00 0 
59bfd000-59c00000 ---p 00000000 00:00 0 
59c00000-59cec000 rw-p 00000000 00:00 0 
59cec000-59d00000 ---p 00000000 00:00 0 
59d00000-59dfd000 rw-p 00000000 00:00 0 
59dfd000-59e00000 ---p 00000000 00:00 0 
59e00000-59efd000 rw-p 00000000 00:00 0 
59efd000-59f00000 ---p 00000000 00:00 0 
59f00000-59ffc000 rw-p 00000000 00:00 0 
59ffc000-5a000000 ---p 00000000 00:00 0 
5a017000-5a01a000 ---p 00000000 00:00 0 
5a01a000-640a8000 rw-p 00000000 00:00 0 
640a8000-640a9000 ---p 00000000 00:00 0 
640a9000-648a9000 rw-p 00000000 00:00 0 
648a9000-648aa000 ---p 00000000 00:00 0 
648aa000-650aa000 rw-p 00000000 00:00 0 
650aa000-690ab000 rw-s 00000000 00:10 39379      /dev/shm/pulse-shm-926210776
690ab000-690ae000 ---p 00000000 00:00 0 
690ae000-690fc000 rw-p 00000000 00:00 0 
690fc000-692fc000 rw-s 0c709000 00:05 9347       /dev/ati/card0
692fc000-693fc000 rw-s 0c705000 00:05 9347       /dev/ati/card0
693fc000-694fc000 rw-s 0c704000 00:05 9347       /dev/ati/card0
694fc000-695fc000 rw-s 0c703000 00:05 9347       /dev/ati/card0
695fc000-696fc000 rw-s 0c702000 00:05 9347       /dev/ati/card0
696fc000-697fc000 rw-s 0c701000 00:05 9347       /dev/ati/card0
697fc000-698fc000 rw-s 0c700000 00:05 9347       /dev/ati/card0
698fc000-699fc000 rw-s 0c6ff000 00:05 9347       /dev/ati/card0
699fc000-69afc000 rw-s 0c6fe000 00:05 9347       /dev/ati/card0
69afc000-6a400000 rw-p 00000000 00:00 0 
6a400000-6a4fd000 rw-p 00000000 00:00 0 
6a4fd000-6a500000 ---p 00000000 00:00 0 
6a500000-6a600000 rw-s 0c6fd000 00:05 9347       /dev/ati/card0
6a600000-6a6e4000 rw-p 00000000 00:00 0 
6a6e4000-6a700000 ---p 00000000 00:00 0 
6a728000-6a729000 ---p 00000000 00:00 0 
6a729000-6a739000 rw-p 00000000 00:00 0 
6a739000-6a73c000 ---p 00000000 00:00 0 
6a73c000-6a78a000 rw-p 00000000 00:00 0 
6a78a000-6a7ca000 rw-s 00014000 00:05 9347       /dev/ati/card0
6a7ca000-6a84a000 rw-p 00000000 00:00 0 
6a84a000-6af4a000 rw-s 00006000 00:05 9347       /dev/ati/card0
6af4a000-6af4d000 ---p 00000000 00:00 0 
6af4d000-6af9b000 rw-p 00000000 00:00 0 
6af9b000-6b000000 rw-s 00000000 00:04 4554779    /SYSV00000000 (deleted)
6b000000-6b0ee000 rw-p 00000000 00:00 0 
6b0ee000-6b100000 ---p 00000000 00:00 0 
6b104000-6b124000 rw-s feae0000 00:05 9347       /dev/ati/card0
6b124000-6b127000 ---p 00000000 00:00 0 
6b127000-6b175000 rw-p 00000000 00:00 0 
6b175000-6b178000 ---p 00000000 00:00 0 
6b178000-6b1c6000 rw-p 00000000 00:00 0 
6b1c6000-6b357000 rw-s 00000000 00:04 4522008    /SYSV00000000 (deleted)
6b357000-6b3bc000 rw-s 00000000 00:04 4489237    /SYSV00000000 (deleted)
6b3bc000-6b3bf000 ---p 00000000 00:00 0 
6b3bf000-6b40d000 rw-p 00000000 00:00 0 
6b40d000-6b410000 ---p 00000000 00:00 0 
6b410000-6b45e000 rw-p 00000000 00:00 0 
6b45e000-6b461000 ---p 00000000 00:00 0 
6b461000-6b4af000 rw-p 00000000 00:00 0 
6b4af000-6b4b2000 ---p 00000000 00:00 0 
6b4b2000-6b500000 rw-p 00000000 00:00 0 
6b500000-6b600000 rw-p 00000000 00:00 0 
6b609000-6b610000 r--s 00000000 08:04 2241308    /usr/lib/gconv/gconv-modules.cache
6b610000-6b611000 rw-s 00005000 00:05 9347       /dev/ati/card0
6b611000-6b613000 rw-s 00002000 00:05 9347       /dev/ati/card0
6b613000-6b61d000 r--s 00103000 08:04 1705267    /home/tratz/.minecraft/bin/minecraft.jar
6b61d000-6b620000 r--s 0001f000 08:04 1705266    /home/tratz/.minecraft/bin/lwjgl_util.jar
6b620000-6b625000 r--s 00033000 08:04 1705265    /home/tratz/.minecraft/bin/jinput.jar
6b625000-6b62e000 r--s 000ac000 08:04 1705264    /home/tratz/.minecraft/bin/lwjgl.jar
6b62e000-6b631000 r--s 00031000 08:04 2240736    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
6b631000-6b633000 r--s 00013000 08:04 2240751    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
6b633000-6b634000 r--s 00000000 08:04 2366477    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6b634000-6b63a000 r--s 00000000 08:04 2366474    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6b63a000-6b63c000 r--s 00000000 08:04 2366475    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6b63c000-6b63f000 r--s 00000000 08:04 2366484    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6b63f000-6b641000 r--s 00000000 08:04 2366463    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6b641000-6b642000 r--s 00000000 08:04 2366485    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6b642000-6b645000 r--s 00000000 08:04 2366471    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6b645000-6b646000 r--s 00000000 08:04 2366467    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6b646000-6b647000 r--s 00000000 08:04 2366460    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6b647000-6b648000 r--s 00000000 08:04 2366469    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6b648000-6b64c000 r--s 00000000 08:04 2366476    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6b64c000-6b653000 r--s 00000000 08:04 2366479    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6b653000-6b65e000 r--s 00000000 08:04 2366461    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6b65e000-6b661000 r--s 00000000 08:04 2366481    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6b661000-6b662000 r--s 00000000 08:04 2366465    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
6b662000-6b684000 r--s 00000000 08:04 2363144    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6b684000-6b68c000 r--s 00000000 08:04 2366480    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6b68c000-6b694000 r--s 00000000 08:04 1708417    /home/tratz/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6b694000-6b697000 r--s 00000000 08:04 2363145    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6b697000-6b698000 r--s 00000000 08:04 2366477    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6b698000-6b69e000 r--s 00000000 08:04 2366474    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6b69e000-6b6a0000 r--s 00000000 08:04 2366475    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6b6a0000-6b6a3000 r--s 00000000 08:04 2366484    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6b6a3000-6b6a5000 r--s 00000000 08:04 2366463    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6b6a5000-6b6a6000 r--s 00000000 08:04 2366485    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6b6a6000-6b6a9000 r--s 00000000 08:04 2366471    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6b6a9000-6b6aa000 r--s 00000000 08:04 2366467    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6b6aa000-6b6ab000 r--s 00000000 08:04 2366460    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6b6ab000-6b6ac000 r--s 00000000 08:04 2366469    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6b6ac000-6b6b0000 r--s 00000000 08:04 2366476    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6b6b0000-6b6b7000 r--s 00000000 08:04 2366479    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6b6b7000-6b6c2000 r--s 00000000 08:04 2366461    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6b6c2000-6b6c5000 r--s 00000000 08:04 2366481    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6b6c5000-6b6e7000 r--s 00000000 08:04 2363144    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6b6e7000-6b6ef000 r--s 00000000 08:04 2366480    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6b6ef000-6b6f7000 r--s 00000000 08:04 1708417    /home/tratz/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6b6f7000-6b6fa000 ---p 00000000 00:00 0 
6b6fa000-6b748000 rw-p 00000000 00:00 0 
6b748000-6b74e000 r--s 000fc000 08:04 2240758    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
6b74e000-6b752000 r--s 0007c000 08:04 2240752    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
6b752000-6b75a000 r--s 00066000 08:04 2635491    /usr/share/java/gnome-java-bridge.jar
6b75a000-6b75b000 ---p 00000000 00:00 0 
6b75b000-6b7db000 rw-p 00000000 00:00 0 
6b7db000-6b7de000 ---p 00000000 00:00 0 
6b7de000-6b82c000 rw-p 00000000 00:00 0 
6b82c000-6b82f000 ---p 00000000 00:00 0 
6b82f000-6b8ad000 rw-p 00000000 00:00 0 
6b8ad000-6b8b0000 ---p 00000000 00:00 0 
6b8b0000-6b92e000 rw-p 00000000 00:00 0 
6b92e000-6b931000 ---p 00000000 00:00 0 
6b931000-6b97f000 rw-p 00000000 00:00 0 
6b97f000-6ba9f000 r--p 00178000 08:04 2235493    /usr/lib/locale/locale-archive
6ba9f000-6bc9f000 r--p 00000000 08:04 2235493    /usr/lib/locale/locale-archive
6bc9f000-6bca2000 ---p 00000000 00:00 0 
6bca2000-6bcf0000 rw-p 00000000 00:00 0 
6bcf0000-6bcf1000 ---p 00000000 00:00 0 
6bcf1000-6bd71000 rw-p 00000000 00:00 0 
6bd71000-6bf00000 r--s 038ad000 08:04 2240766    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
6bf00000-6bff6000 rw-p 00000000 00:00 0 
6bff6000-6c000000 ---p 00000000 00:00 0 
6c000000-6c001000 r--p 00000000 00:00 0 
6c001000-6c002000 r--s 00000000 08:04 2366465    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
6c002000-6c005000 ---p 00000000 00:00 0 
6c005000-6c085000 rw-p 00000000 00:00 0 
6c085000-6c086000 ---p 00000000 00:00 0 
6c086000-6c106000 rw-p 00000000 00:00 0 
6c106000-6c107000 ---p 00000000 00:00 0 
6c107000-6c187000 rw-p 00000000 00:00 0 
6c187000-6c188000 ---p 00000000 00:00 0 
6c188000-6c208000 rw-p 00000000 00:00 0 
6c208000-6c209000 ---p 00000000 00:00 0 
6c209000-6c298000 rw-p 00000000 00:00 0 
6c298000-6c2c9000 rw-p 00000000 00:00 0 
6c2c9000-6c374000 rw-p 00000000 00:00 0 
6c374000-6c41f000 rw-p 00000000 00:00 0 
6c41f000-6c42e000 rw-p 00000000 00:00 0 
6c42e000-6c45f000 rw-p 00000000 00:00 0 
6c45f000-6c50a000 rw-p 00000000 00:00 0 
6c50a000-6c5b4000 rw-p 00000000 00:00 0 
6c5b4000-6c60a000 rw-p 00000000 00:00 0 
6c60a000-6c65f000 rw-p 00000000 00:00 0 
6c65f000-6e460000 rw-p 00000000 00:00 0 
6e460000-74660000 rw-p 00000000 00:00 0 
74660000-89bc0000 rw-p 00000000 00:00 0 
89bc0000-9f110000 rw-p 00000000 00:00 0 
9f110000-a9bb0000 rw-p 00000000 00:00 0 
a9bb0000-b4660000 rw-p 00000000 00:00 0 
b4660000-b4663000 r--s 00000000 08:04 2363145    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4663000-b4665000 r--s 0000b000 08:04 786493     /home/tratz/Downloads/Minecraft.jar
b4665000-b466e000 rw-p 00000000 00:00 0 
b466e000-b4725000 rw-p 00000000 00:00 0 
b4725000-b4965000 rwxp 00000000 00:00 0 
b4965000-b7725000 rw-p 00000000 00:00 0 
b7725000-b7728000 ---p 00000000 00:00 0 
b7728000-b7779000 rw-p 00000000 00:00 0 
b7779000-b777c000 r--s 0000f000 08:04 2240738    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b777c000-b777e000 r--s 0001d000 08:04 2240757    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
b777e000-b7783000 r--s 00044000 08:04 2240756    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
b7783000-b778b000 rw-s 00000000 08:04 793103     /tmp/hsperfdata_tratz/5280
b778b000-b778c000 rw-p 00000000 00:00 0 
b778c000-b778d000 r--p 00000000 00:00 0 
b778d000-b778f000 rw-p 00000000 00:00 0 
bfdda000-bfdfb000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xmx1024M -Xms512M 
java_command: net.minecraft.LauncherFrame
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=tratz
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x609690], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x609690], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x4e4570], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x4e4570], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x4e4570], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x4e4570], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x4e3c60], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x4e6410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x4e6410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x4e6410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x4e6410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.10 (maverick)
uname:Linux 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
libc:glibc 2.12.1 NPTL 2.12.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.46 0.55 0.54

CPU:total 4 (4 cores per cpu, 1 threads per core) family 16 model 2 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext, 3dnow, 3dnowext, lzcnt, sse4a

Memory: 4k page, physical 3095748k(553520k free), swap 3124220k(3124220k free)

vm_info: OpenJDK Server VM (17.0-b16) for linux-x86 JRE (1.6.0_20-b20), built on Oct 20 2010 18:30:59 by "buildd" with gcc 4.4.5

time: Sat Nov 20 05:38:21 2010
elapsed time: 20 seconds
```
I'm thinking "C  [+0x416]  __kernel_vsyscall+0x2" is important somehow. I can't seem to figure out what it means. I've tested this on a friend's laptop using the same (Ubuntu 10.10) and it works fine, no errors. I know other people are running their java fine. Can anyone help me out?

---

### Post by forestG on 2010-12-02
go to synaptic manager and uninstall all jdk you have. Then try this. 

go to oracle and download the latest java for linux.
(you can try both 32 and 64 bit versions if they exist. I do not remember that)

then copy java to the following folder : /usr/lib/jvm/java-xxx/
you can put it actually anywhere you like but that the default location.
create the folders if they are not there.

add the next line in you /etc/profile file.
export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.20/bin"


alternatively just install sun java from ubuntu and just add the above line at the end of your /etc/profile file. 

In order to edit the file you will need the following command
sudo gedit /etc/profile

---

### Post by kostkon on 2010-12-02
It seems that you're running it with OpenJDK and not Sun Java. Try giving the following command to make sure that Sun Java is set as the default jvm in your system:
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by Rasa1111 on 2010-12-02
Ive only ever used 'ubuntu-restricted-extras', 
to get JAVA installed and working properly.
Ive never just tried to install "JAVA" on its own.

and Ive not seen one issue where it did not work as it should. 
Though I dont play games of any kind.. 
So I wouldnt know anything about that.

but, using ubuntu-restricted-extras to get java, and just about every codec you could need,  has not failed me yet. 

Though i have read a lot about people having issues trying to install just 'JAVA'. 

 good luck

---

### Post by lykeion on 2010-12-03
@Tratz
One week and no feedback, has the problem been solved?
If not try to
1) Uninstall icedtea6-plugin and openjdk-6-jre
2) Install sun-java6-plugin and sun-java6-jre
3) Try to run game

If that doesn't do it it might have to do with the graphics driver (fglrx in your case).
The problem is discussed in the minecraft forums: [http://www.minecraftforum.net/viewtopic.php?f=17&t=29864](http://www.minecraftforum.net/viewtopic.php?f=17&t=29864)
And someone seem to have solved it with upgrading to Ubuntu 10.10, see: EDIT
Just dug a little deeper into this and it seems that someone got rid of the problem when updating to Ubuntu 10.10, see: [http://www.minecraftforum.net/viewtopic.php?f=17&t=34493](http://www.minecraftforum.net/viewtopic.php?f=17&t=34493)

@forestG
The sun java package in the repositories is up to date, so there's no need to go to oracle to download and install java.
Also there should be no need to set JAVA_HOME variable.

@Rasa111
ubuntu-restricted-extras will only install icedtea6-plugin/openjdk-6-jre, not sun-java6-plugin/sun-java6-jre.

---

