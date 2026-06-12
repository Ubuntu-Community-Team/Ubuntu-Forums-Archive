---
title: "Mousetrap Game fail"
date: 2010-04-13
forum: General Help
---

### Post by qe2eqe on 2010-04-13
I wanted to try out 'Project Diaspora', and someone recommended I test 'mousetrap' (apt-get install mousetrap), which seems to have better support. Well, mousetrap fails. 

Heres this:
qe2@phenom:~/games/pdiaspora_client-beta-1.3.2$ mousetrap
*** buffer overflow detected ***: mousetrap terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xa5bed8]
/lib/tls/i686/cmov/libc.so.6[0xa5af10]
/lib/tls/i686/cmov/libc.so.6[0xa5a648]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x9e459e]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x60a)[0x9b814a]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0xa5a6fd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xa5a63d]
mousetrap[0x804b919]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x991b56]
mousetrap(__gxx_personality_v0+0x5d)[0x8049211]
======= Memory map: ========
00110000-001f6000 r-xp 00000000 08:14 8178231    /usr/lib/libstdc++.so.6.0.13
001f6000-001fa000 r--p 000e6000 08:14 8178231    /usr/lib/libstdc++.so.6.0.13
001fa000-001fb000 rw-p 000ea000 08:14 8178231    /usr/lib/libstdc++.so.6.0.13
001fb000-00202000 rw-p 00000000 00:00 0 
00202000-0021e000 r-xp 00000000 08:14 20095138   /lib/libgcc_s.so.1
0021e000-0021f000 r--p 0001b000 08:14 20095138   /lib/libgcc_s.so.1
0021f000-00220000 rw-p 0001c000 08:14 20095138   /lib/libgcc_s.so.1
00220000-00222000 r-xp 00000000 08:14 20094997   /lib/tls/i686/cmov/libdl-2.10.1.so
00222000-00223000 r--p 00001000 08:14 20094997   /lib/tls/i686/cmov/libdl-2.10.1.so
00223000-00224000 rw-p 00002000 08:14 20094997   /lib/tls/i686/cmov/libdl-2.10.1.so
00224000-0022b000 r-xp 00000000 08:14 8180179    /usr/lib/libvorbisfile.so.3.2.0
0022b000-0022c000 r--p 00006000 08:14 8180179    /usr/lib/libvorbisfile.so.3.2.0
0022c000-0022d000 rw-p 00007000 08:14 8180179    /usr/lib/libvorbisfile.so.3.2.0
0022d000-00237000 r-xp 00000000 08:14 8180223    /usr/lib/libesd.so.0.2.39
00237000-00238000 r--p 00009000 08:14 8180223    /usr/lib/libesd.so.0.2.39
00238000-00239000 rw-p 0000a000 08:14 8180223    /usr/lib/libesd.so.0.2.39
00239000-00251000 r-xp 00000000 08:14 8180525    /usr/lib/libaudio.so.2.4
00251000-00252000 r--p 00017000 08:14 8180525    /usr/lib/libaudio.so.2.4
00252000-00253000 rw-p 00018000 08:14 8180525    /usr/lib/libaudio.so.2.4
00253000-0025a000 r-xp 00000000 08:14 20095010   /lib/tls/i686/cmov/librt-2.10.1.so
0025a000-0025b000 r--p 00006000 08:14 20095010   /lib/tls/i686/cmov/librt-2.10.1.so
0025b000-0025c000 rw-p 00007000 08:14 20095010   /lib/tls/i686/cmov/librt-2.10.1.so
0025c000-00260000 r-xp 00000000 08:14 8180523    /usr/lib/libXtst.so.6.1.0
00260000-00261000 r--p 00004000 08:14 8180523    /usr/lib/libXtst.so.6.1.0
00261000-00262000 rw-p 00005000 08:14 8180523    /usr/lib/libXtst.so.6.1.0
00262000-00263000 r-xp 00000000 00:00 0          [vdso]
00263000-002a1000 r-xp 00000000 08:14 8182580    /usr/lib/libpulse.so.0.12.0
002a1000-002a2000 r--p 0003d000 08:14 8182580    /usr/lib/libpulse.so.0.12.0
002a2000-002a3000 rw-p 0003e000 08:14 8182580    /usr/lib/libpulse.so.0.12.0
002a3000-002aa000 r-xp 00000000 08:14 8179652    /usr/lib/libSM.so.6.0.0
002aa000-002ab000 r--p 00006000 08:14 8179652    /usr/lib/libSM.so.6.0.0
002ab000-002ac000 rw-p 00007000 08:14 8179652    /usr/lib/libSM.so.6.0.0
002ac000-002b1000 r-xp 00000000 08:14 8178001    /usr/lib/libgpm.so.2.0.0
002b1000-002b2000 r--p 00004000 08:14 8178001    /usr/lib/libgpm.so.2.0.0
002b2000-002b3000 rw-p 00005000 08:14 8178001    /usr/lib/libgpm.so.2.0.0
002b3000-002b8000 r-xp 00000000 08:14 8180492    /usr/lib/libogg.so.0.6.0
002b8000-002b9000 r--p 00004000 08:14 8180492    /usr/lib/libogg.so.0.6.0
002b9000-002ba000 rw-p 00005000 08:14 8180492    /usr/lib/libogg.so.0.6.0
002bc000-002d7000 r-xp 00000000 08:14 20096139   /lib/ld-2.10.1.so
002d7000-002d8000 r--p 0001a000 08:14 20096139   /lib/ld-2.10.1.so
002d8000-002d9000 rw-p 0001b000 08:14 20096139   /lib/ld-2.10.1.so
002d9000-00328000 r-xp 00000000 08:14 8179654    /usr/lib/libXt.so.6.0.0
00328000-00329000 r--p 0004f000 08:14 8179654    /usr/lib/libXt.so.6.0.0
00329000-0032c000 rw-p 00050000 08:14 8179654    /usr/lib/libXt.so.6.0.0
0032c000-00345000 r-xp 00000000 08:14 8182322    /usr/lib/libaa.so.1.0.4
00345000-00346000 ---p 00019000 08:14 8182322    /usr/lib/libaa.so.1.0.4
00346000-00347000 r--p 00019000 08:14 8182322    /usr/lib/libaa.so.1.0.4
00347000-00348000 rw-p 0001a000 08:14 8182322    /usr/lib/libaa.so.1.0.4
00348000-0034a000 rw-p 00000000 00:00 0 
0034a000-00366000 r-xp 00000000 08:14 8182331    /usr/lib/libcaca.so.0.99.16
00366000-00367000 r--p 0001b000 08:14 8182331    /usr/lib/libcaca.so.0.99.16
00367000-003ee000 rw-p 0001c000 08:14 8182331    /usr/lib/libcaca.so.0.99.16
003ee000-003f2000 rw-p 00000000 00:00 0 
003f2000-00406000 r-xp 00000000 08:14 20095126   /lib/libz.so.1.2.3.3
00406000-00407000 r--p 00013000 08:14 20095126   /lib/libz.so.1.2.3.3
00407000-00408000 rw-p 00014000 08:14 20095126   /lib/libz.so.1.2.3.3
0040a000-00445000 r-xp 00000000 08:14 14860697   /usr/lib/libsmpeg-0.4.so.0.1.4
00445000-00446000 r--p 0003a000 08:14 14860697   /usr/lib/libsmpeg-0.4.so.0.1.4
00446000-00447000 rw-p 0003b000 08:14 14860697   /usr/lib/libsmpeg-0.4.so.0.1.4
00447000-00463000 rw-p 00000000 00:00 0 
00463000-0047d000 r-xp 00000000 08:14 8180264    /usr/lib/libvorbis.so.0.4.0
0047d000-0047e000 r--p 00019000 08:14 8180264    /usr/lib/libvorbis.so.0.4.0
0047e000-0048c000 rw-p 0001a000 08:14 8180264    /usr/lib/libvorbis.so.0.4.0
0048c000-004d4000 r-xp 00000000 08:14 8182656    /usr/lib/libpulsecommon-0.9.19.so
004d4000-004d5000 r--p 00047000 08:14 8182656    /usr/lib/libpulsecommon-0.9.19.so
004d5000-004d6000 rw-p 00048000 08:14 8182656    /usr/lib/libpulsecommon-0.9.19.so
004d6000-004ed000 r-xp 00000000 08:14 8179650    /usr/lib/libICE.so.6.3.0
004ed000-004ee000 r--p 00016000 08:14 8179650    /usr/lib/libICE.so.6.3.0
004ee000-004ef000 rw-p 00017000 08:14 8179650    /usr/lib/libICE.so.6.3.0
004ef000-004f1000 rw-p 00000000 00:00 0 
004f1000-0050d000 r-xp 00000000 08:14 8179644    /usr/lib/libxcb.so.1.1.0
0050d000-0050e000 r--p 0001c000 08:14 8179644    /usr/lib/libxcb.so.1.1.0
0050e000-0050f000 rw-p 0001d000 08:14 8179644    /usr/lib/libxcb.so.1.1.0
0050f000-00512000 r-xp 00000000 08:14 20095123   /lib/libuuid.so.1.3.0
00512000-00513000 r--p 00002000 08:14 20095123   /lib/libuuid.so.1.3.0
00513000-00514000 rw-p 00003000 08:14 20095123   /lib/libuuid.so.1.3.0
00518000-0058b000 r-xp 00000000 08:14 14860385   /usr/lib/libSDL-1.2.so.0.11.2
0058b000-0058c000 r--p 00072000 08:14 14860385   /usr/lib/libSDL-1.2.so.0.11.2
0058c000-0058d000 rw-p 00073000 08:14 14860385   /usr/lib/libSDL-1.2.so.0.11.2
0058d000-005bc000 rw-p 00000000 00:00 0 
005be000-005d4000 r-xp 00000000 08:14 8180144    /usr/lib/libdirect-1.2.so.0.7.0
005d4000-005d5000 r--p 00015000 08:14 8180144    /usr/lib/libdirect-1.2.so.0.7.0
005d5000-005d6000 rw-p 00016000 08:14 8180144    /usr/lib/libdirect-1.2.so.0.7.0
005d6000-005e4000 r-xp 00000000 08:14 8179656    /usr/lib/libXext.so.6.4.0Aborted

---

### Post by polki@mac.com on 2010-04-13
I was curious so I installed it and it was all aboard the fail boat for me as well. Got the same backtrace too.
Sorry I can't be of any help

---

