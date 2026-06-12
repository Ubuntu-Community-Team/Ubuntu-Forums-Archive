---
title: "dvipng, invalid pointer error"
date: 2010-01-29
forum: General Help
---

### Post by migi on 2010-01-29
I'm using the lucid lynx development release. Running dvipng produces an invalid pointer error (see below). A quick search in launchpad found a confirmed bug for dvipng filed under TeXLive 2009 transition which seems to be relating to libkpathsea [https://bugs.launchpad.net/ubuntu/+source/dvipng/+bug/511502](https://bugs.launchpad.net/ubuntu/+source/dvipng/+bug/511502).

Now my question is, is this the very same bug, incompetence on my part or something I should report?

uname -a
Linux deepthought 2.6.32-6-generic #8-Ubuntu SMP Sat Nov 28 12:48:05 UTC 2009 i686 GNU/Linux

dvipng -d test.dvi 
This is dvipng 1.12 Copyright 2002-2008 Jan-Ake Larsson
OPEN FILE    test.dvi
@0 DVI START:    PRE 2 25400000/473628672 1000 (11841) ' TeX output 2010.01.29:1329'
  OPEN FILE:    '/var/lib/texmf/fonts/map/dvips/updmap/ps2pk.map'
  OPEN FILE:    '/usr/share/texmf-texlive/fonts/map/ttf2pk/config/ttfonts.map'
@42 PAGE START:    BOP 1 0 0 0 0 0 0 0 0 0 (1)[1
@87 DRAW CMD:    DOWN4 41484288
@92 DRAW CMD:    PUSH
@93 DRAW CMD:    DOWN4 -39649280
@98 DRAW CMD:    DOWN4 37683200
@103 DRAW CMD:    PUSH
@104 DRAW CMD:    DOWN4 -35389440
@109 DRAW CMD:    PUSH
@110 DRAW CMD:    RIGHT3 5046272
@114 DRAW CMD:    FNT_DEF1 7 1274110073 655360 655360 0 5 'cmr10'
  FONT 7:    New entry created
@135 DRAW CMD:    FONT_07
  FIND FONT:    cmr10 400*** glibc detected *** dvipng: free(): invalid pointer: 0x095374d1 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b5e1)[0x18f5e1]
/lib/tls/i686/cmov/libc.so.6(+0x6ce38)[0x190e38]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x193efd]
/usr/lib/libkpathsea.so.4(+0x8d96)[0x118d96]
/usr/lib/libkpathsea.so.4(kpse_fontmap_lookup+0xf8)[0x1190f8]
/usr/lib/libkpathsea.so.4(kpse_find_file+0x2f7)[0x1152c7]
dvipng[0x804fa27]
dvipng[0x804ded6]
dvipng[0x804e060]
dvipng[0x8049edd]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x13abd6]
dvipng[0x8049d81]
======= Memory map: ========
00110000-00120000 r-xp 00000000 08:06 139097     /usr/lib/libkpathsea.so.4.0.0
00120000-00121000 r--p 0000f000 08:06 139097     /usr/lib/libkpathsea.so.4.0.0
00121000-00122000 rw-p 00010000 08:06 139097     /usr/lib/libkpathsea.so.4.0.0
00122000-00124000 rw-p 00000000 00:00 0 
00124000-00271000 r-xp 00000000 08:06 963        /lib/tls/i686/cmov/libc-2.11.1.so
00271000-00272000 ---p 0014d000 08:06 963        /lib/tls/i686/cmov/libc-2.11.1.so
00272000-00274000 r--p 0014d000 08:06 963        /lib/tls/i686/cmov/libc-2.11.1.so
00274000-00275000 rw-p 0014f000 08:06 963        /lib/tls/i686/cmov/libc-2.11.1.so
00275000-00278000 rw-p 00000000 00:00 0 
00278000-00294000 r-xp 00000000 08:06 561        /lib/libgcc_s.so.1
00294000-00295000 r--p 0001b000 08:06 561        /lib/libgcc_s.so.1
00295000-00296000 rw-p 0001c000 08:06 561        /lib/libgcc_s.so.1
003ac000-003bf000 r-xp 00000000 08:06 450        /lib/libz.so.1.2.3.3
003bf000-003c0000 r--p 00012000 08:06 450        /lib/libz.so.1.2.3.3
003c0000-003c1000 rw-p 00013000 08:06 450        /lib/libz.so.1.2.3.3
00657000-00676000 r-xp 00000000 08:06 146535     /usr/lib/libjpeg.so.62.0.0
00676000-00677000 r--p 0001e000 08:06 146535     /usr/lib/libjpeg.so.62.0.0
00677000-00678000 rw-p 0001f000 08:06 146535     /usr/lib/libjpeg.so.62.0.0
006c5000-00736000 r-xp 00000000 08:06 135827     /usr/lib/libfreetype.so.6.3.22
00736000-0073a000 r--p 00070000 08:06 135827     /usr/lib/libfreetype.so.6.3.22
0073a000-0073b000 rw-p 00074000 08:06 135827     /usr/lib/libfreetype.so.6.3.22
007a5000-007c9000 r-xp 00000000 08:06 1032       /lib/tls/i686/cmov/libm-2.11.1.so
007c9000-007ca000 r--p 00023000 08:06 1032       /lib/tls/i686/cmov/libm-2.11.1.so
007ca000-007cb000 rw-p 00024000 08:06 1032       /lib/tls/i686/cmov/libm-2.11.1.so
007f7000-00813000 r-xp 00000000 08:06 173269     /usr/lib/libgd.so.2.0.0
00813000-00814000 r--p 0001c000 08:06 173269     /usr/lib/libgd.so.2.0.0
00814000-00833000 rw-p 0001d000 08:06 173269     /usr/lib/libgd.so.2.0.0
00833000-00837000 rw-p 00000000 00:00 0 
00a05000-00a20000 r-xp 00000000 08:06 151        /lib/ld-2.11.1.so
00a20000-00a21000 r--p 0001a000 08:06 151        /lib/ld-2.11.1.so
00a21000-00a22000 rw-p 0001b000 08:06 151        /lib/ld-2.11.1.so
00d2d000-00d2e000 r-xp 00000000 00:00 0          [vdso]
00d41000-00d7f000 r-xp 00000000 08:06 133472     /usr/lib/libt1.so.5.1.2
00d7f000-00d80000 r--p 0003d000 08:06 133472     /usr/lib/libt1.so.5.1.2
00d80000-00d83000 rw-p 0003e000 08:06 133472     /usr/lib/libt1.so.5.1.2
00d83000-00d98000 rw-p 00000000 00:00 0 
00f65000-00f88000 r-xp 00000000 08:06 11125      /lib/libpng12.so.0.42.0
00f88000-00f89000 r--p 00022000 08:06 11125      /lib/libpng12.so.0.42.0
00f89000-00f8a000 rw-p 00023000 08:06 11125      /lib/libpng12.so.0.42.0
08048000-0805e000 r-xp 00000000 08:06 132583     /usr/bin/dvipng
0805e000-0805f000 r--p 00016000 08:06 132583     /usr/bin/dvipng
0805f000-08060000 rw-p 00017000 08:06 132583     /usr/bin/dvipng
08060000-08061000 rw-p 00000000 00:00 0 
09275000-0955a000 rw-p 00000000 00:00 0          [heap]
b7500000-b7521000 rw-p 00000000 00:00 0 
b7521000-b7600000 ---p 00000000 00:00 0 
b76fb000-b778e000 r--s 00000000 08:06 394786     /var/lib/texmf/fonts/map/dvips/updmap/ps2pk.map
b778e000-b7791000 rw-p 00000000 00:00 0 
b77a7000-b77a8000 rw-p 00000000 00:00 0 
b77a8000-b77a9000 r--s 00000000 08:06 833898     /usr/share/texmf-texlive/fonts/map/ttf2pk/config/ttfonts.map
b77a9000-b77ad000 rw-p 00000000 00:00 0 
bfc48000-bfc5d000 rw-p 00000000 00:00 0          [stack]
Aborted


Thank you, migi

---

