---
title: "2 diffrent java bugs"
date: 2010-10-26
forum: General Help
---

### Post by l0c0dantes on 2010-10-26
Hello there. I am having 2 different java bugs. The first one is with yahoo games. I go to play a game of euchre. It loads the table select screen fine, but when I click to join a table, it only loads the add, not the additional applet.

The second one is regarding minecraft.It starts up fine, generates theworld no problems. but once it displays the water for a milisecond it crashes. It drops these bug reports in my home folder

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb77e2416, pid=5914, tid=2076179312
#
# JRE version: 6.0_21-b06
# Java VM: Java HotSpot(TM) Server VM (17.0-b16 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x0000171a

Registers:
EAX=0x00000000, EBX=0x0000171a, ECX=0x0000173b, EDX=0x0000000b
ESP=0x7bbff288, EBP=0x7bbff294, ESI=0x00000020, EDI=0xb77caff4
EIP=0xb77e2416, CR2=0x00000004, EFLAGS=0x00000202

Top of Stack: (sp=0x7bbff288)
0x7bbff288:   b77c2990 b77caff4 8e990880 7bbff398
0x7bbff298:   8e4ac8a3 0000000b 00000000 00000000
0x7bbff2a8:   00000000 00001000 00000000 00000000
0x7bbff2b8:   00000000 00000000 00000000 7fffffff
0x7bbff2c8:   fffffffe ffffffff ffffffff ffffffff
0x7bbff2d8:   ffffffff ffffffff ffffffff ffffffff
0x7bbff2e8:   ffffffff ffffffff ffffffff ffffffff
0x7bbff2f8:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb77e2416)
0xb77e2406:   cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90 cd 80
0xb77e2416:   c3 00 2e 73 68 73 74 72 74 61 62 00 2e 68 61 73 

Stack: [0x7bbef000,0x7bc00000],  sp=0x7bbff288,  free space=407bbfec10k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x416]  __kernel_vsyscall+0x2
C  [fglrx_dri.so+0x167e8a3]
C  [libpthread.so.0+0x5cc9]


[error occurred during error reporting (printing target Java thread stack), id 0xb]


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 34560K, used 12054K [0xa90e0000, 0xab5c0000, 0xb38e0000)
  eden space 31744K, 37% used [0xa90e0000,0xa9ca5b08,0xaafe0000)
  from space 2816K, 0% used [0xaafe0000,0xaafe0000,0xab2a0000)
  to   space 3008K, 0% used [0xab2d0000,0xab2d0000,0xab5c0000)
 PSOldGen        total 21504K, used 12041K [0x940e0000, 0x955e0000, 0xa90e0000)
  object space 21504K, 55% used [0x940e0000,0x94ca2530,0x955e0000)
 PSPermGen       total 32000K, used 14307K [0x900e0000, 0x92020000, 0x940e0000)
  object space 32000K, 44% used [0x900e0000,0x90ed8c50,0x92020000)

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:05 2359559    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/bin/java
08052000-08053000 rwxp 00009000 08:05 2359559    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/bin/java
0a02a000-0b01d000 rwxp 00000000 00:00 0          [heap]
7b600000-7b6f5000 rwxp 00000000 00:00 0 
7b6f5000-7b700000 ---p 00000000 00:00 0 
7b800000-7b8e0000 rwxp 00000000 00:00 0 
7b8e0000-7b900000 ---p 00000000 00:00 0 
7b9ee000-7b9ef000 ---p 00000000 00:00 0 
7b9ef000-7bbef000 rwxp 00000000 00:00 0 
7bbef000-7bbf0000 ---p 00000000 00:00 0 
7bbf0000-7bc00000 rwxp 00000000 00:00 0 
7bc00000-7bcfc000 rwxp 00000000 00:00 0 
7bcfc000-7bd00000 ---p 00000000 00:00 0 
7be00000-7befd000 rwxp 00000000 00:00 0 
7befd000-7bf00000 ---p 00000000 00:00 0 
7bf00000-7bffd000 rwxp 00000000 00:00 0 
7bffd000-7c000000 ---p 00000000 00:00 0 
7c000000-7c0fd000 rwxp 00000000 00:00 0 
7c0fd000-7c100000 ---p 00000000 00:00 0 
7c100000-7c1fd000 rwxp 00000000 00:00 0 
7c1fd000-7c200000 ---p 00000000 00:00 0 
7c200000-7c300000 rwxp 00000000 00:00 0 
7c321000-7c324000 ---p 00000000 00:00 0 
7c324000-863b2000 rwxp 00000000 00:00 0 
863b2000-863b3000 ---p 00000000 00:00 0 
863b3000-86bb3000 rwxp 00000000 00:00 0 
86bb3000-86bb4000 ---p 00000000 00:00 0 
86bb4000-873b4000 rwxp 00000000 00:00 0 
873b4000-8b3b5000 rwxs 00000000 00:10 30266      /dev/shm/pulse-shm-2092130515
8b3b5000-8b3db000 r-xp 00000000 08:05 2227608    /usr/lib/libvorbis.so.0.4.4
8b3db000-8b3dc000 r-xp 00025000 08:05 2227608    /usr/lib/libvorbis.so.0.4.4
8b3dc000-8b3dd000 rwxp 00026000 08:05 2227608    /usr/lib/libvorbis.so.0.4.4
8b3dd000-8b542000 r-xp 00000000 08:05 2227610    /usr/lib/libvorbisenc.so.2.0.7
8b542000-8b543000 ---p 00165000 08:05 2227610    /usr/lib/libvorbisenc.so.2.0.7
8b543000-8b554000 r-xp 00165000 08:05 2227610    /usr/lib/libvorbisenc.so.2.0.7
8b554000-8b555000 rwxp 00176000 08:05 2227610    /usr/lib/libvorbisenc.so.2.0.7
8b555000-8b59f000 r-xp 00000000 08:05 2226647    /usr/lib/libFLAC.so.8.2.0
8b59f000-8b5a0000 r-xp 00049000 08:05 2226647    /usr/lib/libFLAC.so.8.2.0
8b5a0000-8b5a1000 rwxp 0004a000 08:05 2226647    /usr/lib/libFLAC.so.8.2.0
8b5a1000-8b5db000 r-xp 00000000 08:05 1177401    /lib/libdbus-1.so.3.5.2
8b5db000-8b5dc000 r-xp 00039000 08:05 1177401    /lib/libdbus-1.so.3.5.2
8b5dc000-8b5dd000 rwxp 0003a000 08:05 1177401    /lib/libdbus-1.so.3.5.2
8b5dd000-8b63e000 r-xp 00000000 08:05 2227516    /usr/lib/libsndfile.so.1.0.21
8b63e000-8b63f000 ---p 00061000 08:05 2227516    /usr/lib/libsndfile.so.1.0.21
8b63f000-8b640000 r-xp 00061000 08:05 2227516    /usr/lib/libsndfile.so.1.0.21
8b640000-8b641000 rwxp 00062000 08:05 2227516    /usr/lib/libsndfile.so.1.0.21
8b641000-8b645000 rwxp 00000000 00:00 0 
8b645000-8b68d000 r-xp 00000000 08:05 2227457    /usr/lib/libpulsecommon-0.9.21.so
8b68d000-8b68e000 r-xp 00047000 08:05 2227457    /usr/lib/libpulsecommon-0.9.21.so
8b68e000-8b68f000 rwxp 00048000 08:05 2227457    /usr/lib/libpulsecommon-0.9.21.so
8b68f000-8b6ce000 r-xp 00000000 08:05 2227456    /usr/lib/libpulse.so.0.12.2
8b6ce000-8b6cf000 ---p 0003f000 08:05 2227456    /usr/lib/libpulse.so.0.12.2
8b6cf000-8b6d0000 r-xp 0003f000 08:05 2227456    /usr/lib/libpulse.so.0.12.2
8b6d0000-8b6d1000 rwxp 00040000 08:05 2227456    /usr/lib/libpulse.so.0.12.2
8b6d1000-8b791000 r-xp 00000000 08:05 2226759    /usr/lib/libasound.so.2.0.0
8b791000-8b792000 ---p 000c0000 08:05 2226759    /usr/lib/libasound.so.2.0.0
8b792000-8b796000 r-xp 000c0000 08:05 2226759    /usr/lib/libasound.so.2.0.0
8b796000-8b797000 rwxp 000c4000 08:05 2226759    /usr/lib/libasound.so.2.0.0
8b797000-8b7bc000 r-xp 00000000 08:05 1570801    /home/loco/.minecraft/bin/natives/libopenal.so
8b7bc000-8b7bd000 rwxp 00025000 08:05 1570801    /home/loco/.minecraft/bin/natives/libopenal.so
8b7bd000-8b8aa000 rwxp 00000000 00:00 0 
8b8aa000-8b8ad000 ---p 00000000 00:00 0 
8b8ad000-8b8fb000 rwxp 00000000 00:00 0 
8b8fb000-8b8fe000 r-xp 00000000 08:05 1570797    /home/loco/.minecraft/bin/natives/libjinput-linux.so
8b8fe000-8b8ff000 r-xp 00002000 08:05 1570797    /home/loco/.minecraft/bin/natives/libjinput-linux.so
8b8ff000-8b900000 rwxp 00003000 08:05 1570797    /home/loco/.minecraft/bin/natives/libjinput-linux.so
8b900000-8bb00000 rwxs e342d000 00:05 9151       /dev/ati/card0
8bb00000-8bc00000 rwxs 1031f000 00:05 9151       /dev/ati/card0
8bc00000-8bcf9000 rwxp 00000000 00:00 0 
8bcf9000-8bd00000 ---p 00000000 00:00 0 
8bd01000-8bd06000 r-xp 00000000 08:05 2227372    /usr/lib/libogg.so.0.7.0
8bd06000-8bd07000 r-xp 00004000 08:05 2227372    /usr/lib/libogg.so.0.7.0
8bd07000-8bd08000 rwxp 00005000 08:05 2227372    /usr/lib/libogg.so.0.7.0
8bd08000-8bd0f000 r-xp 00000000 08:05 1177533    /lib/libwrap.so.0.7.6
8bd0f000-8bd10000 r-xp 00006000 08:05 1177533    /lib/libwrap.so.0.7.6
8bd10000-8bd11000 rwxp 00007000 08:05 1177533    /lib/libwrap.so.0.7.6
8bd11000-8bd14000 r-xp 00000000 08:05 1177531    /lib/libuuid.so.1.3.0
8bd14000-8bd15000 r-xp 00002000 08:05 1177531    /lib/libuuid.so.1.3.0
8bd15000-8bd16000 rwxp 00003000 08:05 1177531    /lib/libuuid.so.1.3.0
8bd16000-8bd19000 r-xp 00000000 08:05 2227639    /usr/lib/libxcb-atom.so.1.0.0
8bd19000-8bd1a000 r-xp 00002000 08:05 2227639    /usr/lib/libxcb-atom.so.1.0.0
8bd1a000-8bd1b000 rwxp 00003000 08:05 2227639    /usr/lib/libxcb-atom.so.1.0.0
8bd1b000-8bd30000 r-xp 00000000 08:05 2226660    /usr/lib/libICE.so.6.3.0
8bd30000-8bd31000 r-xp 00014000 08:05 2226660    /usr/lib/libICE.so.6.3.0
8bd31000-8bd32000 rwxp 00015000 08:05 2226660    /usr/lib/libICE.so.6.3.0
8bd32000-8bd34000 rwxp 00000000 00:00 0 
8bd34000-8bd37000 ---p 00000000 00:00 0 
8bd37000-8c689000 rwxp 00000000 00:00 0 
8c689000-8c6c9000 rwxs 00013000 00:05 9151       /dev/ati/card0
8c6c9000-8c6fa000 r-xp 00000000 08:05 2234474    /usr/lib/fglrx/libatiadlxx.so
8c6fa000-8c6fb000 rwxp 00030000 08:05 2234474    /usr/lib/fglrx/libatiadlxx.so
8c700000-8c704000 r-xp 00000000 08:05 2227978    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
8c704000-8c705000 r-xp 00003000 08:05 2227978    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
8c705000-8c706000 rwxp 00004000 08:05 2227978    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
8c706000-8c70d000 r-xs 00000000 08:05 2230251    /usr/lib/gconv/gconv-modules.cache
8c70d000-8ce0d000 rwxs 00006000 00:05 9151       /dev/ati/card0
8ce0d000-8ce0e000 rwxs 00005000 00:05 9151       /dev/ati/card0
8ce0e000-8ce2e000 rwxs f5000000 00:05 9151       /dev/ati/card0
8ce2e000-8e843000 r-xp 00000000 08:05 2234468    /usr/lib/fglrx/dri/fglrx_dri.so
8e843000-8e907000 rwxp 01a15000 08:05 2234468    /usr/lib/fglrx/dri/fglrx_dri.so
8e907000-8e992000 rwxp 00000000 00:00 0 
8e992000-8e9ac000 r-xp 00000000 08:05 1177423    /lib/libgcc_s.so.1
8e9ac000-8e9ad000 r-xp 00019000 08:05 1177423    /lib/libgcc_s.so.1
8e9ad000-8e9ae000 rwxp 0001a000 08:05 1177423    /lib/libgcc_s.so.1
8e9ae000-8e9b5000 r-xp 00000000 08:05 2234466    /usr/lib/fglrx/libatiuki.so.1.0
8e9b5000-8e9b6000 rwxp 00006000 08:05 2234466    /usr/lib/fglrx/libatiuki.so.1.0
8e9b6000-8ea6a000 r-xp 00000000 08:05 2234470    /usr/lib/fglrx/libGL.so.1.2
8ea6a000-8ea75000 rwxp 000b3000 08:05 2234470    /usr/lib/fglrx/libGL.so.1.2
8ea75000-8ea7a000 rwxp 00000000 00:00 0 
8ea7a000-8ea80000 r-xp 00000000 08:05 2226722    /usr/lib/libXrandr.so.2.2.0
8ea80000-8ea81000 r-xp 00005000 08:05 2226722    /usr/lib/libXrandr.so.2.2.0
8ea81000-8ea82000 rwxp 00006000 08:05 2226722    /usr/lib/libXrandr.so.2.2.0
8ea82000-8ea89000 r-xp 00000000 08:05 2226681    /usr/lib/libSM.so.6.0.1
8ea89000-8ea8a000 r-xp 00006000 08:05 2226681    /usr/lib/libSM.so.6.0.1
8ea8a000-8ea8b000 rwxp 00007000 08:05 2226681    /usr/lib/libSM.so.6.0.1
8ea8b000-8ea8c000 r-xp 00000000 08:05 2226683    /usr/lib/libX11-xcb.so.1.0.0
8ea8c000-8ea8d000 r-xp 00000000 08:05 2226683    /usr/lib/libX11-xcb.so.1.0.0
8ea8d000-8ea8e000 rwxp 00001000 08:05 2226683    /usr/lib/libX11-xcb.so.1.0.0
8ea8e000-8ea90000 r-xp 00000000 08:05 2226712    /usr/lib/libXinerama.so.1.0.0
8ea90000-8ea91000 r-xp 00001000 08:05 2226712    /usr/lib/libXinerama.so.1.0.0
8ea91000-8ea92000 rwxp 00002000 08:05 2226712    /usr/lib/libXinerama.so.1.0.0
8ea92000-8ea94000 rwxs 00002000 00:05 9151       /dev/ati/card0
8ea94000-8eaeb000 r-xp 00000000 08:05 1570799    /home/loco/.minecraft/bin/natives/liblwjgl.so
8eaeb000-8eaec000 r-xp 00056000 08:05 1570799    /home/loco/.minecraft/bin/natives/liblwjgl.so
8eaec000-8eaed000 rwxp 00057000 08:05 1570799    /home/loco/.minecraft/bin/natives/liblwjgl.so
8eaed000-8eaf0000 ---p 00000000 00:00 0 
8eaf0000-8eb3e000 rwxp 00000000 00:00 0 
8eb3e000-8eba3000 rwxs 00000000 00:04 7471139    /SYSV00000000 (deleted)
8eba3000-8ebac000 r-xs 000d3000 08:05 1570794    /home/loco/.minecraft/bin/minecraft.jar
8ebac000-8ebaf000 ---p 00000000 00:00 0 
8ebaf000-8ebfd000 rwxp 00000000 00:00 0 
8ebfd000-8ec00000 ---p 00000000 00:00 0 
8ec00000-8ec4e000 rwxp 00000000 00:00 0 
8ec4e000-8ec51000 ---p 00000000 00:00 0 
8ec51000-8ec9f000 rwxp 00000000 00:00 0 
8ec9f000-8ecaf000 r-xp 00000000 08:05 1177501    /lib/libresolv-2.12.1.so
8ecaf000-8ecb0000 r-xp 00010000 08:05 1177501    /lib/libresolv-2.12.1.so
8ecb0000-8ecb1000 rwxp 00011000 08:05 1177501    /lib/libresolv-2.12.1.so
8ecb1000-8ecb3000 rwxp 00000000 00:00 0 
8ecb3000-8ee44000 rwxs 00000000 00:04 7438370    /SYSV00000000 (deleted)
8ee44000-8eea9000 rwxs 00000000 00:04 7405601    /SYSV00000000 (deleted)
8eea9000-8eeaf000 rwxs 00000000 00:04 7372821    /SYSV00000000 (deleted)
8eeaf000-8eeb2000 ---p 00000000 00:00 0 
8eeb2000-8ef00000 rwxp 00000000 00:00 0 
8ef00000-8f000000 rwxp 00000000 00:00 0 
8f003000-8f007000 r-xp 00000000 08:05 1177453    /lib/libnss_dns-2.12.1.so
8f007000-8f008000 r-xp 00004000 08:05 1177453    /lib/libnss_dns-2.12.1.so
8f008000-8f009000 rwxp 00005000 08:05 1177453    /lib/libnss_dns-2.12.1.so
8f00a000-8f00d000 r-xs 0001f000 08:05 1570793    /home/loco/.minecraft/bin/lwjgl_util.jar
8f00d000-8f012000 r-xs 00033000 08:05 1570792    /home/loco/.minecraft/bin/jinput.jar
8f012000-8f01b000 r-xs 000ac000 08:05 1570791    /home/loco/.minecraft/bin/lwjgl.jar
8f01b000-8f022000 r-xp 00000000 08:05 2359598    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libnio.so
8f022000-8f023000 rwxp 00006000 08:05 2359598    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libnio.so
8f023000-8f026000 ---p 00000000 00:00 0 
8f026000-8f074000 rwxp 00000000 00:00 0 
8f074000-8f075000 r-xs 00000000 08:05 794809     /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
8f075000-8f076000 r-xs 00000000 08:05 793813     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
8f076000-8f07c000 r-xs 00000000 08:05 793810     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
8f07c000-8f07e000 r-xs 00000000 08:05 793811     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
8f07e000-8f081000 r-xs 00000000 08:05 793820     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
8f081000-8f083000 r-xs 00000000 08:05 793799     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
8f083000-8f084000 r-xs 00000000 08:05 793821     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
8f084000-8f087000 r-xs 00000000 08:05 793807     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
8f087000-8f0a9000 r-xs 00000000 08:05 794831     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
8f0aa000-8f0ad000 ---p 00000000 00:00 0 
8f0ad000-8f0fb000 rwxp 00000000 00:00 0 
8f0fb000-8f10e000 r-xp 00000000 08:05 2359597    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libnet.so
8f10e000-8f10f000 rwxp 00013000 08:05 2359597    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libnet.so
8f10f000-8f112000 ---p 00000000 00:00 0 
8f112000-8f160000 rwxp 00000000 00:00 0 
8f160000-8f164000 r-xp 00000000 08:05 2226704    /usr/lib/libXfixes.so.3.1.0
8f164000-8f165000 r-xp 00003000 08:05 2226704    /usr/lib/libXfixes.so.3.1.0
8f165000-8f166000 rwxp 00004000 08:05 2226704    /usr/lib/libXfixes.so.3.1.0
8f166000-8f16e000 r-xp 00000000 08:05 2226724    /usr/lib/libXrender.so.1.3.0
8f16e000-8f16f000 r-xp 00007000 08:05 2226724    /usr/lib/libXrender.so.1.3.0
8f16f000-8f170000 rwxp 00008000 08:05 2226724    /usr/lib/libXrender.so.1.3.0
8f170000-8f178000 r-xp 00000000 08:05 2226696    /usr/lib/libXcursor.so.1.0.2
8f178000-8f179000 r-xp 00007000 08:05 2226696    /usr/lib/libXcursor.so.1.0.2
8f179000-8f17a000 rwxp 00008000 08:05 2226696    /usr/lib/libXcursor.so.1.0.2
8f17a000-8f17b000 r-xp 00000000 08:05 2359667    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libjawt.so
8f17b000-8f17c000 rwxp 00000000 08:05 2359667    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libjawt.so
8f17c000-8f17e000 r-xp 00000000 08:05 1177461    /lib/libnss_mdns4_minimal.so.2
8f17e000-8f17f000 r-xp 00001000 08:05 1177461    /lib/libnss_mdns4_minimal.so.2
8f17f000-8f180000 rwxp 00002000 08:05 1177461    /lib/libnss_mdns4_minimal.so.2
8f180000-8f183000 r-xs 00027000 08:05 2359511    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/ext/sunjce_provider.jar
8f183000-8f189000 r-xs 00092000 08:05 2359509    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/jsse.jar
8f189000-8f18c000 r-xs 00013000 08:05 2359514    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/jce.jar
8f18c000-8f20b000 r-xp 00000000 08:05 2359661    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libfontmanager.so
8f20b000-8f216000 rwxp 0007e000 08:05 2359661    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libfontmanager.so
8f216000-8f21a000 rwxp 00000000 00:00 0 
8f21a000-8f232000 r-xp 00000000 08:05 2227651    /usr/lib/libxcb.so.1.1.0
8f232000-8f233000 r-xp 00017000 08:05 2227651    /usr/lib/libxcb.so.1.1.0
8f233000-8f234000 rwxp 00018000 08:05 2227651    /usr/lib/libxcb.so.1.1.0
8f234000-8f34d000 r-xp 00000000 08:05 2226685    /usr/lib/libX11.so.6.3.0
8f34d000-8f34e000 r-xp 00118000 08:05 2226685    /usr/lib/libX11.so.6.3.0
8f34e000-8f350000 rwxp 00119000 08:05 2226685    /usr/lib/libX11.so.6.3.0
8f350000-8f351000 rwxp 00000000 00:00 0 
8f351000-8f3d5000 r-xp 00000000 08:05 2359609    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libawt.so
8f3d5000-8f3dc000 rwxp 00084000 08:05 2359609    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libawt.so
8f3dc000-8f400000 rwxp 00000000 00:00 0 
8f400000-8f500000 rwxp 00000000 00:00 0 
8f500000-8f504000 r-xs 00000000 08:05 793812     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
8f504000-8f50b000 r-xs 00000000 08:05 793815     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
8f50b000-8f54e000 r-xp 00000000 08:05 2359613    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/xawt/libmawt.so
8f54e000-8f550000 rwxp 00043000 08:05 2359613    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/xawt/libmawt.so
8f550000-8f551000 rwxp 00000000 00:00 0 
8f551000-8f554000 ---p 00000000 00:00 0 
8f554000-8f5a2000 rwxp 00000000 00:00 0 
8f5a2000-8f5a3000 ---p 00000000 00:00 0 
8f5a3000-8f623000 rwxp 00000000 00:00 0 
8f623000-8f626000 ---p 00000000 00:00 0 
8f626000-8f674000 rwxp 00000000 00:00 0 
8f674000-8f677000 ---p 00000000 00:00 0 
8f677000-8f6f5000 rwxp 00000000 00:00 0 
8f6f5000-8f6f8000 ---p 00000000 00:00 0 
8f6f8000-8f776000 rwxp 00000000 00:00 0 
8f776000-8f779000 ---p 00000000 00:00 0 
8f779000-8f7c7000 rwxp 00000000 00:00 0 
8f7c7000-8f9c7000 r-xp 00000000 08:05 2231141    /usr/lib/locale/locale-archive
8f9c7000-8f9ca000 ---p 00000000 00:00 0 
8f9ca000-8fa18000 rwxp 00000000 00:00 0 
8fa18000-8fa1b000 ---p 00000000 00:00 0 
8fa1b000-8fa69000 rwxp 00000000 00:00 0 
8fa69000-8fc00000 r-xs 03014000 08:05 2359815    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/rt.jar
8fc00000-8fd00000 rwxp 00000000 00:00 0 
8fd00000-8fd0b000 r-xs 00000000 08:05 793797     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
8fd0b000-8fd0e000 r-xs 00000000 08:05 793817     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
8fd0e000-8fd12000 r-xp 00000000 08:05 2226700    /usr/lib/libXdmcp.so.6.0.0
8fd12000-8fd13000 r-xp 00003000 08:05 2226700    /usr/lib/libXdmcp.so.6.0.0
8fd13000-8fd14000 rwxp 00004000 08:05 2226700    /usr/lib/libXdmcp.so.6.0.0
8fd14000-8fd20000 r-xp 00000000 08:05 2226710    /usr/lib/libXi.so.6.1.0
8fd20000-8fd21000 r-xp 0000b000 08:05 2226710    /usr/lib/libXi.so.6.1.0
8fd21000-8fd22000 rwxp 0000c000 08:05 2226710    /usr/lib/libXi.so.6.1.0
8fd22000-8fd30000 r-xp 00000000 08:05 2226702    /usr/lib/libXext.so.6.4.0
8fd30000-8fd31000 r-xp 0000d000 08:05 2226702    /usr/lib/libXext.so.6.4.0
8fd31000-8fd32000 rwxp 0000e000 08:05 2226702    /usr/lib/libXext.so.6.4.0
8fd32000-8fd33000 r-xs 00000000 08:05 793803     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
8fd33000-8fd34000 r-xs 00000000 08:05 793796     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
8fd34000-8fd3c000 r-xs 00000000 08:05 793816     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
8fd3c000-8fd44000 r-xs 00000000 08:05 794768     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
8fd44000-8fd45000 ---p 00000000 00:00 0 
8fd45000-8fdf9000 rwxp 00000000 00:00 0 
8fdf9000-8fdfa000 ---p 00000000 00:00 0 
8fdfa000-8fe7a000 rwxp 00000000 00:00 0 
8fe7a000-8fe7b000 ---p 00000000 00:00 0 
8fe7b000-8ff0b000 rwxp 00000000 00:00 0 
8ff0b000-8ff1b000 rwxp 00000000 00:00 0 
8ff1b000-8ff26000 rwxp 00000000 00:00 0 
8ff26000-8ffc3000 rwxp 00000000 00:00 0 
8ffc3000-8ffd3000 rwxp 00000000 00:00 0 
8ffd3000-8ffe3000 rwxp 00000000 00:00 0 
8ffe3000-8ffee000 rwxp 00000000 00:00 0 
8ffee000-9008b000 rwxp 00000000 00:00 0 
9008b000-9009e000 rwxp 00000000 00:00 0 
9009e000-900df000 rwxp 00000000 00:00 0 
900df000-92020000 rwxp 00000000 00:00 0 
92020000-940e0000 rwxp 00000000 00:00 0 
940e0000-955e0000 rwxp 00000000 00:00 0 
955e0000-a90e0000 rwxp 00000000 00:00 0 
a90e0000-ab5c0000 rwxp 00000000 00:00 0 
ab5c0000-b38e0000 rwxp 00000000 00:00 0 
b38e0000-b38e1000 r-xs 00000000 08:05 793805     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b38e1000-b38ea000 rwxp 00000000 00:00 0 
b38ea000-b39a1000 rwxp 00000000 00:00 0 
b39a1000-b3be1000 rwxp 00000000 00:00 0 
b3be1000-b69a1000 rwxp 00000000 00:00 0 
b69a1000-b69b0000 r-xp 00000000 08:05 2359593    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libzip.so
b69b0000-b69b2000 rwxp 0000e000 08:05 2359593    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libzip.so
b69b2000-b69bc000 r-xp 00000000 08:05 1177455    /lib/libnss_files-2.12.1.so
b69bc000-b69bd000 r-xp 00009000 08:05 1177455    /lib/libnss_files-2.12.1.so
b69bd000-b69be000 rwxp 0000a000 08:05 1177455    /lib/libnss_files-2.12.1.so
b69be000-b69c7000 r-xp 00000000 08:05 1177465    /lib/libnss_nis-2.12.1.so
b69c7000-b69c8000 r-xp 00008000 08:05 1177465    /lib/libnss_nis-2.12.1.so
b69c8000-b69c9000 rwxp 00009000 08:05 1177465    /lib/libnss_nis-2.12.1.so
b69c9000-b69cb000 r-xp 00000000 08:05 2226689    /usr/lib/libXau.so.6.0.0
b69cb000-b69cc000 r-xp 00001000 08:05 2226689    /usr/lib/libXau.so.6.0.0
b69cc000-b69cd000 rwxp 00002000 08:05 2226689    /usr/lib/libXau.so.6.0.0
b69cd000-b69d1000 r-xp 00000000 08:05 2226730    /usr/lib/libXtst.so.6.1.0
b69d1000-b69d2000 r-xp 00003000 08:05 2226730    /usr/lib/libXtst.so.6.1.0
b69d2000-b69d3000 rwxp 00004000 08:05 2226730    /usr/lib/libXtst.so.6.1.0
b69d3000-b69db000 rwxs 00000000 08:05 1962335    /tmp/hsperfdata_loco/5914
b69db000-b69ee000 r-xp 00000000 08:05 1177449    /lib/libnsl-2.12.1.so
b69ee000-b69ef000 r-xp 00012000 08:05 1177449    /lib/libnsl-2.12.1.so
b69ef000-b69f0000 rwxp 00013000 08:05 1177449    /lib/libnsl-2.12.1.so
b69f0000-b69f2000 rwxp 00000000 00:00 0 
b69f2000-b69f5000 r-xs 00000000 08:05 794830     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b69f5000-b69fb000 r-xp 00000000 08:05 1177451    /lib/libnss_compat-2.12.1.so
b69fb000-b69fc000 r-xp 00006000 08:05 1177451    /lib/libnss_compat-2.12.1.so
b69fc000-b69fd000 rwxp 00007000 08:05 1177451    /lib/libnss_compat-2.12.1.so
b69fd000-b6a03000 r-xp 00000000 08:05 2359578    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/native_threads/libhpi.so
b6a03000-b6a04000 rwxp 00006000 08:05 2359578    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/native_threads/libhpi.so
b6a04000-b6a27000 r-xp 00000000 08:05 2359590    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libjava.so
b6a27000-b6a29000 rwxp 00023000 08:05 2359590    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libjava.so
b6a29000-b6a30000 r-xp 00000000 08:05 1177503    /lib/librt-2.12.1.so
b6a30000-b6a31000 r-xp 00006000 08:05 1177503    /lib/librt-2.12.1.so
b6a31000-b6a32000 rwxp 00007000 08:05 1177503    /lib/librt-2.12.1.so
b6a32000-b6a35000 ---p 00000000 00:00 0 
b6a35000-b6a83000 rwxp 00000000 00:00 0 
b6a83000-b6aa7000 r-xp 00000000 08:05 1177438    /lib/libm-2.12.1.so
b6aa7000-b6aa8000 r-xp 00023000 08:05 1177438    /lib/libm-2.12.1.so
b6aa8000-b6aa9000 rwxp 00024000 08:05 1177438    /lib/libm-2.12.1.so
b6aa9000-b71d5000 r-xp 00000000 08:05 2359580    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/server/libjvm.so
b71d5000-b7228000 rwxp 0072c000 08:05 2359580    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/server/libjvm.so
b7228000-b7648000 rwxp 00000000 00:00 0 
b7648000-b779f000 r-xp 00000000 08:05 1177389    /lib/libc-2.12.1.so
b779f000-b77a0000 ---p 00157000 08:05 1177389    /lib/libc-2.12.1.so
b77a0000-b77a2000 r-xp 00157000 08:05 1177389    /lib/libc-2.12.1.so
b77a2000-b77a3000 rwxp 00159000 08:05 1177389    /lib/libc-2.12.1.so
b77a3000-b77a6000 rwxp 00000000 00:00 0 
b77a6000-b77a8000 r-xp 00000000 08:05 1177403    /lib/libdl-2.12.1.so
b77a8000-b77a9000 r-xp 00001000 08:05 1177403    /lib/libdl-2.12.1.so
b77a9000-b77aa000 rwxp 00002000 08:05 1177403    /lib/libdl-2.12.1.so
b77aa000-b77b1000 r-xp 00000000 08:05 2359592    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/jli/libjli.so
b77b1000-b77b3000 rwxp 00006000 08:05 2359592    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/jli/libjli.so
b77b3000-b77b4000 rwxp 00000000 00:00 0 
b77b4000-b77c9000 r-xp 00000000 08:05 1177497    /lib/libpthread-2.12.1.so
b77c9000-b77ca000 ---p 00015000 08:05 1177497    /lib/libpthread-2.12.1.so
b77ca000-b77cb000 r-xp 00015000 08:05 1177497    /lib/libpthread-2.12.1.so
b77cb000-b77cc000 rwxp 00016000 08:05 1177497    /lib/libpthread-2.12.1.so
b77cc000-b77ce000 rwxp 00000000 00:00 0 
b77ce000-b77cf000 r-xs 00000000 08:05 793801     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b77cf000-b77d1000 r-xs 0000b000 08:05 1962317    /home/loco/Downloads/Minecraft.jar
b77d1000-b77d2000 r-xp 002a1000 08:05 2231141    /usr/lib/locale/locale-archive
b77d2000-b77d3000 rwxp 00000000 00:00 0 
b77d3000-b77d4000 r-xp 00000000 00:00 0 
b77d4000-b77df000 r-xp 00000000 08:05 2359589    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libverify.so
b77df000-b77e0000 rwxp 0000b000 08:05 2359589    /usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/libverify.so
b77e0000-b77e2000 rwxp 00000000 00:00 0 
b77e2000-b77e3000 r-xp 00000000 00:00 0          [vdso]
b77e3000-b77ff000 r-xp 00000000 08:05 1177365    /lib/ld-2.12.1.so
b77ff000-b7800000 r-xp 0001b000 08:05 1177365    /lib/ld-2.12.1.so
b7800000-b7801000 rwxp 0001c000 08:05 1177365    /lib/ld-2.12.1.so
bfef2000-bff13000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
java_command: /home/loco/Downloads/Minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=loco
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.21/jre/../lib/i386
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

uname:Linux 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686
libc:glibc 2.12.1 NPTL 2.12.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.09 0.93 0.72

CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 15 stepping 11, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3

Memory: 4k page, physical 2059680k(51488k free), swap 4939772k(4939772k free)

vm_info: Java HotSpot(TM) Server VM (17.0-b16) for linux-x86 JRE (1.6.0_21-b06), built on Jun 22 2010 01:04:46 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Thu Oct 14 15:14:33 2010
elapsed time: 8 seconds

```

Thank you for any help you might be able to give me :)

---

### Post by l0c0dantes on 2010-10-28
Bump

---

### Post by Tratz on 2010-11-20
No one has an answer for this? My problem is very similar.

---

