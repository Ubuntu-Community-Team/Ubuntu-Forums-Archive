---
title: "Qt Applications Suddenly Stopped Working"
date: 2012-04-30
forum: General Help
---

### Post by ve4cib on 2012-04-30
I've got a system running Xubuntu 11.10 that has suddenly developed problems running any Qt application.  Last week they were working fine, the computer was shut down cleanly the last time it was used, but as of today every Qt application I run has errors like this:

(Gtk applications (e.g. Geany) seem to work just fine.)

```

darwin@Jennifer:~/libdarwin/project/darwinviewer$ qtcreator
QGtkStyle was unable to detect the current GTK+ theme.
*** glibc detected *** qtcreator: malloc(): memory corruption: 0x096cb228 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6ff22)[0x699f22]
/lib/i386-linux-gnu/libc.so.6(+0x718be)[0x69b8be]
/lib/i386-linux-gnu/libc.so.6(__libc_malloc+0x68)[0x69d7f8]
/usr/lib/i386-linux-gnu/libXi.so.6(XIQueryDevice+0x150)[0x933930]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate21x11GetTouchDeviceInfoEv+0x46)[0xf2f4f6]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate24initializeMultitouch_sysEv+0x1b)[0xf2fadb]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate20initializeMultitouchEv+0xe6)[0xebc686]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate10initializeEv+0x1c5)[0xebc8e5]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate9constructEP9_XDisplaymm+0xf4)[0xebca54]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN12QApplicationC2ERiPPci+0x86)[0xebd346]
qtcreator[0x804e828]
qtcreator[0x804c318]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x643113]
qtcreator[0x804e63d]
======= Memory map: ========
00110000-00127000 r-xp 00000000 08:03 3615       /lib/i386-linux-gnu/libpthread-2.13.so
00127000-00128000 r--p 00016000 08:03 3615       /lib/i386-linux-gnu/libpthread-2.13.so
00128000-00129000 rw-p 00017000 08:03 3615       /lib/i386-linux-gnu/libpthread-2.13.so
00129000-0012b000 rw-p 00000000 00:00 0 
0012b000-00209000 r-xp 00000000 08:03 6608       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00209000-0020a000 ---p 000de000 08:03 6608       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
0020a000-0020e000 r--p 000de000 08:03 6608       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
0020e000-0020f000 rw-p 000e2000 08:03 6608       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
0020f000-00216000 rw-p 00000000 00:00 0 
00216000-00229000 r-xp 00000000 08:03 5490       /lib/i386-linux-gnu/libz.so.1.2.3.4
00229000-0022a000 r--p 00012000 08:03 5490       /lib/i386-linux-gnu/libz.so.1.2.3.4
0022a000-0022b000 rw-p 00013000 08:03 5490       /lib/i386-linux-gnu/libz.so.1.2.3.4
0022d000-00363000 r-xp 00000000 08:03 73620      /usr/lib/i386-linux-gnu/libQtNetwork.so.4.7.4
00363000-00364000 ---p 00136000 08:03 73620      /usr/lib/i386-linux-gnu/libQtNetwork.so.4.7.4
00364000-00367000 r--p 00136000 08:03 73620      /usr/lib/i386-linux-gnu/libQtNetwork.so.4.7.4
00367000-00369000 rw-p 00139000 08:03 73620      /usr/lib/i386-linux-gnu/libQtNetwork.so.4.7.4
00369000-00600000 r-xp 00000000 08:03 69484      /usr/lib/i386-linux-gnu/libQtCore.so.4.7.4
00600000-00607000 r--p 00296000 08:03 69484      /usr/lib/i386-linux-gnu/libQtCore.so.4.7.4
00607000-0060a000 rw-p 0029d000 08:03 69484      /usr/lib/i386-linux-gnu/libQtCore.so.4.7.4
0060a000-00628000 r-xp 00000000 08:03 1209       /lib/i386-linux-gnu/ld-2.13.so
00628000-00629000 r--p 0001d000 08:03 1209       /lib/i386-linux-gnu/ld-2.13.so
00629000-0062a000 rw-p 0001e000 08:03 1209       /lib/i386-linux-gnu/ld-2.13.so
0062a000-007a2000 r-xp 00000000 08:03 1214       /lib/i386-linux-gnu/libc-2.13.so
007a2000-007a4000 r--p 00178000 08:03 1214       /lib/i386-linux-gnu/libc-2.13.so
007a4000-007a5000 rw-p 0017a000 08:03 1214       /lib/i386-linux-gnu/libc-2.13.so
007a5000-007a8000 rw-p 00000000 00:00 0 
007a8000-007da000 r-xp 00000000 08:03 30094      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
007da000-007db000 ---p 00032000 08:03 30094      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
007db000-007dc000 r--p 00032000 08:03 30094      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
007dc000-007dd000 rw-p 00033000 08:03 30094      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
007dd000-007f5000 r-xp 00000000 08:03 40905      /usr/lib/i386-linux-gnu/libaudio.so.2.4
007f5000-007f6000 r--p 00017000 08:03 40905      /usr/lib/i386-linux-gnu/libaudio.so.2.4
007f6000-007f7000 rw-p 00018000 08:03 40905      /usr/lib/i386-linux-gnu/libaudio.so.2.4
007f7000-0081f000 r-xp 00000000 08:03 3809       /lib/i386-linux-gnu/libpng12.so.0.46.0
0081f000-00820000 r--p 00027000 08:03 3809       /lib/i386-linux-gnu/libpng12.so.0.46.0
00820000-00821000 rw-p 00028000 08:03 3809       /lib/i386-linux-gnu/libpng12.so.0.46.0
00821000-008b3000 r-xp 00000000 08:03 3754       /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
008b3000-008b7000 r--p 00091000 08:03 3754       /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
008b7000-008b8000 rw-p 00095000 08:03 3754       /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
008b8000-00905000 r-xp 00000000 08:03 1075       /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
00905000-00906000 r--p 0004d000 08:03 1075       /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
00906000-00907000 rw-p 0004e000 08:03 1075       /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
00907000-0090e000 r-xp 00000000 08:03 30874      /usr/lib/i386-linux-gnu/libSM.so.6.0.1
0090e000-0090f000 r--p 00006000 08:03 30874      /usr/lib/i386-linux-gnu/libSM.so.6.0.1
0090f000-00910000 rw-p 00007000 08:03 30874      /usr/lib/i386-linux-gnu/libSM.so.6.0.1
00910000-00926000 r-xp 00000000 08:03 30849      /usr/lib/i386-linux-gnu/libICE.so.6.3.0
00926000-00927000 r--p 00015000 08:03 30849      /usr/lib/i386-linux-gnu/libICE.so.6.3.0
00927000-00928000 rw-p 00016000 08:03 30849      /usr/lib/i386-linux-gnu/libICE.so.6.3.0
00928000-0092a000 rw-p 00000000 00:00 0 
0092a000-00938000 r-xp 00000000 08:03 30960      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00938000-00939000 r--p 0000d000 08:03 30960      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00939000-0093a000 rw-p 0000e000 08:03 30960      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
0093a000-00943000 r-xp 00000000 08:03 30384      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00943000-00944000 r--p 00008000 08:03 30384      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00944000-00945000 rw-p 00009000 08:03 30384      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00945000-0096d000 r-xp 00000000 08:03 1219       /lib/i386-linux-gnu/libm-2.13.so
0096d000-0096e000 r--p 00028000 08:03 1219       /lib/i386-linux-gnu/libm-2.13.so
0096e000-0096f000 rw-p 00029000 08:03 1219       /lib/i386-linux-gnu/libm-2.13.so
0096f000-00972000 r-xp 00000000 08:03 1218       /lib/i386-linux-gnu/libdl-2.13.so
00972000-00973000 r--p 00002000 08:03 1218       /lib/i386-linux-gnu/libdl-2.13.so
00973000-00974000 rw-p 00003000 08:03 1218       /lib/i386-linux-gnu/libdl-2.13.so
00974000-00978000 r-xp 00000000 08:03 1077       /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
00978000-00979000 r--p 00003000 08:03 1077       /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
00979000-0097a000 rw-p 00004000 08:03 1077       /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
0097a000-00981000 r-xp 00000000 08:03 3618       /lib/i386-linux-gnu/librt-2.13.so
00981000-00982000 r--p 00006000 08:03 3618       /lib/i386-linux-gnu/librt-2.13.so
00982000-00983000 rw-p 00007000 08:03 3618       /lib/i386-linux-gnu/librt-2.13.so
00983000-00985000 r-xp 00000000 08:03 30115      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00985000-00986000 r--p 00001000 08:03 30115      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00986000-00987000 rw-p 00002000 08:03 30115      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00987000-0098c000 r-xp 00000000 08:03 3991       /usr/lib/i386-linux-gnu/libffi.so.6.0.0
0098c000-0098d000 r--p 00004000 08:03 3991       /usr/lib/i386-linux-gnu/libffi.so.6.0.0
0098d000-0098e000 rw-p 00005000 08:03 3991       /usr/lib/i386-linux-gnu/libffi.so.6.0.0
0098e000-00992000 r-xp 00000000 08:03 7470       /lib/i386-linux-gnu/libuuid.so.1.3.0
00992000-00993000 r--p 00003000 08:03 7470       /lib/i386-linux-gnu/libuuid.so.1.3.0
00993000-00994000 rw-p 00004000 08:03 7470       /lib/i386-linux-gnu/libuuid.so.1.3.0
00994000-00999000 r-xp 00000000 08:03 30125      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
00999000-0099a000 r--p 00004000 08:03 30125      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0099a000-0099b000 rw-p 00005000 08:03 30125      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0099b000-0099e000 r-xp 00000000 08:03 77795      /usr/lib/i386-linux-gnu/gconv/UTF-16.so
0099e000-0099f000 r--p 00002000 08:03 77795      /usr/lib/i386-linux-gnu/gconv/UTF-16.so
0099f000-009a0000 rw-p 00003000 08:03 77795      /usr/lib/i386-linux-gnu/gconv/UTF-16.so
009a0000-009a7000 r-xp 00000000 08:03 30972      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
009a7000-009a8000 r--p 00006000 08:03 30972      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
009a8000-009a9000 rw-p 00007000 08:03 30972      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
009aa000-009c6000 r-xp 00000000 08:03 1061       /lib/i386-linux-gnu/libgcc_s.so.1
009c6000-009c7000 r--p 0001b000 08:03 1061       /lib/i386-linux-gnu/libgcc_s.so.1
009c7000-009c8000 rw-p 0001c000 08:03 1061       /lib/i386-linux-gnu/libgcc_s.so.1
009c8000-009ee000 r-xp 00000000 08:03 6535       /lib/i386-linux-gnu/libexpat.so.1.5.2
009ee000-009ef000 ---p 00026000 08:03 6535       /lib/i386-linux-gnu/libexpat.so.1.5.2
009ef000-009f1000 r--p 00026000 08:03 6535       /lib/i386-linux-gnu/libexpat.so.1.5.2
009f1000-009f2000 rw-p 00028000 08:03 6535       /lib/i386-linux-gnu/libexpat.so.1.5.2
009f2000-00a4a000 r-xp 00000000 08:03 30983      /usr/lib/i386-linux-gnu/libXt.so.6.0.0
00a4a000-00a4b000 r--p 00057000 08:03 30983      /usr/lib/i386-linux-gnu/libXt.so.6.0.0
00a4b000-00a4e000 rw-p 00058000 08:03 30983      /usr/lib/i386-linux-gnu/libXt.so.6.0.0
00a4e000-00a8b000 r-xp 00000000 08:03 2171       /lib/i386-linux-gnu/libpcre.so.3.12.1
00a8b000-00a8c000 r--p 0003c000 08:03 2171       /lib/i386-linux-gnu/libpcre.so.3.12.1
00a8c000-00a8d000 rw-p 0003d000 08:03 2171       /lib/i386-linux-gnu/libpcre.so.3.12.1
00a8d000-00a98000 r-xp 00000000 08:03 1226       /lib/i386-linux-gnu/libnss_files-2.13.so
00a98000-00a99000 r--p 0000a000 08:03 1226       /lib/i386-linux-gnu/libnss_files-2.13.so
00a99000-00a9a000 rw-p 0000b000 08:03 1226       /lib/i386-linux-gnu/libnss_files-2.13.so
00a9a000-00a9e000 r-xp 00000000 08:03 33106      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
00a9e000-00a9f000 r--p 00003000 08:03 33106      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
00a9f000-00aa0000 rw-p 00004000 08:03 33106      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
00aa0000-00aa2000 r-xp 00000000 08:03 33148      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
00aa2000-00aa3000 r--p 00001000 08:03 33148      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
00aa3000-00aa4000 rw-p 00002000 08:03 33148      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
00aa4000-00b9b000 r-xp 00000000 08:03 1089       /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
00b9b000-00b9c000 r--p 000f6000 08:03 1089       /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
00b9c000-00b9d000 rw-p 000f7000 08:03 1089       /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
00b9d000-00bba000 r-xp 00000000 08:03 30136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00bba000-00bbb000 r--p 0001c000 08:03 30136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00bbb000-00bbc000 rw-p 0001d000 08:03 30136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00bbc000-00bc5000 r-xp 00000000 08:03 33122      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00bc5000-00bc6000 r--p 00008000 08:03 33122      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00bc6000-00bc7000 rw-p 00009000 08:03 33122      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00bc7000-00bf3000 r-xp 00000000 08:03 7970       /usr/lib/libgconf-2.so.4.1.5
00bf3000-00bf4000 r--p 0002b000 08:03 7970       /usr/lib/libgconf-2.so.4.1.5
00bf4000-00bf5000 rw-p 0002c000 08:03 7970       /usr/lib/libgconf-2.so.4.1.5
00bf5000-00bf8000 r-xp 00000000 08:03 1076       /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00bf8000-00bf9000 r--p 00002000 08:03 1076       /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00bf9000-00bfa000 rw-p 00003000 08:03 1076       /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
00bfa000-00c16000 r-xp 00000000 08:03 4042       /lib/i386-linux-gnu/libselinux.so.1
00c16000-00c17000 r--p 0001b000 08:03 4042       /lib/i386-linux-gnu/libselinux.so.1
00c17000-00c18000 rw-p 0001c000 08:03 4042       /lib/i386-linux-gnu/libselinux.so.1
00c18000-00c1a000 r-xp 00000000 08:03 33095      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00c1a000-00c1b000 r--p 00001000 08:03 33095      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00c1b000-00c1c000 rw-p 00002000 08:03 33095      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00c1e000-00c2f000 r-xp 00000000 08:03 30366      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
00c2f000-00c30000 r--p 00010000 08:03 30366      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
00c30000-00c31000 rw-p 00011000 08:03 30366      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
00c31000-00c54000 r-xp 00000000 08:03 30406      /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
00c54000-00c55000 r--p 00022000 08:03 30406      /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
00c55000-00c56000 rw-p 00023000 08:03 30406      /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
00c58000-00c59000 r-xp 00000000 00:00 0          [vdso]
00c59000-00ca0000 r-xp 00000000 08:03 490        /lib/i386-linux-gnu/libdbus-1.so.3.5.7
00ca0000-00ca1000 r--p 00046000 08:03 490        /lib/i386-linux-gnu/libdbus-1.so.3.5.7
00ca1000-00ca2000 rw-p 00047000 08:03 490        /lib/i386-linux-gnu/libdbus-1.so.3.5.7
00ca2000-00cb5000 r-xp 00000000 08:03 3617       /lib/i386-linux-gnu/libresolv-2.13.so
00cb5000-00cb6000 r--p 00012000 08:03 3617       /lib/i386-linux-gnu/libresolv-2.13.so
00cb6000-00cb7000 rw-p 00013000 08:03 3617       /lib/i386-linux-gnu/libresolv-2.13.so
00cb7000-00cb9000 rw-p 00000000 00:00 0 
00cb9000-00cc4000 r-xp 00000000 08:03 33057      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
00cc4000-00cc5000 r--p 0000a000 08:03 33057      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
00cc5000-00cc6000 rw-p 0000b000 08:03 33057      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
00cc6000-00ce3000 r-xp 00000000 08:03 32865      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
00ce3000-00ce5000 r--p 0001c000 08:03 32865      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
00ce5000-00ce6000 rw-p 0001e000 08:03 32865      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
00ce6000-00d04000 r-xp 00000000 08:03 32952      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
00d04000-00d05000 r--p 0001d000 08:03 32952      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
00d05000-00d06000 rw-p 0001e000 08:03 32952      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
00d06000-00d08000 r-xp 00000000 08:03 33135      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
00d08000-00d09000 r--p 00001000 08:03 33135      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
00d09000-00d0a000 rw-p 00002000 08:03 33135      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
00d0a000-00d0c000 r-xp 00000000 08:03 30374      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00d0c000-00d0d000 r--p 00001000 08:03 30374      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00d0d000-00d0e000 rw-p 00002000 08:03 30374      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
00d0e000-00d16000 r-xp 00000000 08:03 30363      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00d16000-00d17000 r--p 00007000 08:03 30363      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00d17000-00d18000 rw-p 00008000 08:03 30363      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00d18000-00d1b000 r-xp 00000000 08:03 33545      /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
00d1b000-00d1c000 r--p 00002000 08:03 33545      /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
00d1c000-00d1d000 rw-p 00003000 08:03 33545      /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
00d1d000-00d29000 r-xp 00000000 08:03 31850      /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
00d29000-00d2a000 r--p 0000b000 08:03 31850      /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
00d2a000-00d2b000 rw-p 0000c000 08:03 31850      /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
00d2e000-00d5b000 r-xp 00000000 08:03 89645      /usr/lib/i386-linux-gnu/qtcreator/libExtensionSystem.so.1.0.0
00d5b000-00d5c000 r--p 0002d000 08:03 89645      /usr/lib/i386-linux-gnu/qtcreator/libExtensionSystem.so.1.0.0
00d5c000-00d5d000 rw-p 0002e000 08:03 89645      /usr/lib/i386-linux-gnu/qtcreator/libExtensionSystem.so.1.0.0
00d5d000-017f5000 r-xp 00000000 08:03 7297       /usr/lib/i386-linux-gnu/libQtGui.so.4.7.4
017f5000-01816000 r--p 00a97000 08:03 7297       /usr/lib/i386-linux-gnu/libQtGui.so.4.7.4
01816000-01820000 rw-p 00ab8000 08:03 7297       /usr/lib/i386-linux-gnu/libQtGui.so.4.7.4
01820000-01823000 rw-p 00000000 00:00 0 
01823000-018ce000 r-xp 00000000 08:03 33313      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
018ce000-018d0000 r--p 000ab000 08:03 33313      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
018d0000-018d1000 rw-p 000ad000 08:03 33313      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
018d1000-018e1000 r-xp 00000000 08:03 30128      /usr/lib/i386-linux-gnu/libtasn1.so.3.1.11
018e1000-018e2000 r--p 0000f000 08:03 30128      /usr/lib/i386-linux-gnu/libtasn1.so.3.1.11
018e2000-018e3000 rw-p 00010000 08:03 30128      /usr/lib/i386-linux-gnu/libtasn1.so.3.1.11
01cee000-01d98000 r-xp 00000000 08:03 2080       /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
01d98000-01d99000 ---p 000aa000 08:03 2080       /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
01d99000-01d9d000 r--p 000aa000 08:03 2080       /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
01d9d000-01d9e000 rw-p 000ae000 08:03 2080       /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
01e42000-01e6d000 r-xp 00000000 08:03 33058      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
01e6d000-01e6e000 r--p 0002a000 08:03 33058      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
01e6e000-01e6f000 rw-p 0002b000 08:03 33058      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
027ed000-02c4e000 r-xp 00000000 08:03 33312      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
02c4e000-02c52000 r--p 00461000 08:03 33312      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
02c52000-02c54000 rw-p 00465000 08:03 33312      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
02c54000-02c56000 rw-p 00000000 00:00 0 
032c6000-03344000 r-xp 00000000 08:03 30105      /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
03344000-03348000 r--p 0007d000 08:03 30105      /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
03348000-03349000 rw-p 00081000 08:03 30105      /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
03f00000-03f11000 r-xp 00000000 08:03 31869      /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
03f11000-03f12000 r--p 00010000 08:03 31869      /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
03f12000-03f13000 rw-p 00011000 08:03 31869      /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
0503a000-0503d000 r-xp 00000000 08:03 30097      /lib/i386-linux-gnu/libgpg-error.so.0.8.0
0503d000-0503e000 r--p 00002000 08:03 30097      /lib/i386-linux-gnu/libgpg-error.so.0.8.0
0503e000-0503f000 rw-p 00003000 08:03 30097      /lib/i386-linux-gnu/libgpg-error.so.0.8.0
052a2000-05369000 r-xp 00000000 08:03 30395      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
05369000-0536a000 r--p 000c7000 08:03 30395      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
0536a000-0536b000 rw-p 000c8000 08:03 30395      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
0536b000-0536d000 rw-p 00000000 00:00 0 
05c0e000-05d3f000 r-xp 00000000 08:03 30352      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
05d3f000-05d40000 ---p 00131000 08:03 30352      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
05d40000-05d41000 r--p 00131000 08:03 30352      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
05d41000-05d43000 rw-p 00132000 08:03 30352      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
05d43000-05d44000 rw-p 00000000 00:00 0 
06167000-062a9000 r-xp 00000000 08:03 1079       /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
062a9000-062ab000 r--p 00142000 08:03 1079       /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
062ab000-062ac000 rw-p 00144000 08:03 1079       /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
062ac000-062ad000 rw-p 00000000 00:00 0 
06f38000-06f3a000 r-xp 00000000 08:03 3623       /lib/i386-linux-gnu/libutil-2.13.so
06f3a000-06f3b000 r--p 00001000 08:03 3623       /lib/i386-linux-gnu/libutil-2.13.so
06f3b000-06f3c000 rw-p 00002000 08:03 3623       /lib/i386-linux-gnu/libutil-2.13.so
075e6000-0764b000 r-xp 00000000 08:03 48457      /usr/lib/libgnomevfs-2.so.0.2400.4
0764b000-0764d000 r--p 00064000 08:03 48457      /usr/lib/libgnomevfs-2.so.0.2400.4
0764d000-0764f000 rw-p 00066000 08:03 48457      /usr/lib/libgnomevfs-2.so.0.2400.4
07b7c000-07cc3000 r-xp 00000000 08:03 765        /usr/lib/libxml2.so.2.7.8
07cc3000-07cc7000 r--p 00147000 08:03 765        /usr/lib/libxml2.so.2.7.8
07cc7000-07cc8000 rw-p 0014b000 08:03 765        /usr/lib/libxml2.so.2.7.8
07cc8000-07cc9000 rw-p 00000000 00:00 0 
07f98000-0801a000 r-xp 00000000 08:03 30129      /lib/i386-linux-gnu/libgcrypt.so.11.7.0
0801a000-0801b000 r--p 00081000 08:03 30129      /lib/i386-linux-gnu/libgcrypt.so.11.7.0
0801b000-0801d000 rw-p 00082000 08:03 30129      /lib/i386-linux-gnu/libgcrypt.so.11.7.0
08048000-08054000 r-xp 00000000 08:03 89739      /usr/bin/qtcreator
08054000-08055000 r--p 0000b000 08:03 89739      /usr/bin/qtcreator
08055000-08056000 rw-p 0000c000 08:03 89739      /usr/bin/qtcreator
08d75000-08dbc000 r-xp 00000000 08:03 33056      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
08dbc000-08dbd000 r--p 00047000 08:03 33056      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
08dbd000-08dbe000 rw-p 00048000 08:03 33056      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
0966f000-096d4000 rw-p 00000000 00:00 0          [heap]
b7300000-b7321000 rw-p 00000000 00:00 0 
b7321000-b7400000 ---p 00000000 00:00 0 
b74df000-b74e5000 r--s 00000000 08:03 67459      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b74e5000-b74e7000 r--s 00000000 08:03 67487      /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b74e7000-b74ea000 r--s 00000000 08:03 67478      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b74ea000-b74ed000 r--s 00000000 08:03 67477      /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b74ed000-b74ee000 r--s 00000000 08:03 67476      /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b74ee000-b74f0000 r--s 00000000 08:03 67475      /var/cache/fontconfig/b5ea634b0fb353b8ea17632d1f9ef766-le32d4.cache-3
b74f0000-b74f4000 r--s 00000000 08:03 67474      /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b74f4000-b74f5000 r--s 00000000 08:03 67473      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b74f5000-b74f6000 r--s 00000000 08:03 67465      /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b74f6000-b74f7000 r--s 00000000 08:03 67464      /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b74f7000-b74fb000 r--s 00000000 08:03 67463      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b74fb000-b74ff000 r--s 00000000 08:03 67462      /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b74ff000-b7502000 r--s 00000000 08:03 67461      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b7502000-b750d000 r--s 00000000 08:03 67460      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b750d000-b7510000 r--s 00000000 08:03 67371      /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b7510000-b7511000 r--s 00000000 08:03 53176      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b7511000-b751e000 r--s 00000000 08:03 67369      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b751e000-b771e000 r--p 00000000 08:03 5675       /usr/lib/locale/locale-archive
b771e000-b7728000 rw-p 00000000 00:00 0 
b772e000-b7730000 r--s 00000000 08:03 936        /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b7730000-b7733000 r--s 00000000 08:03 67366      /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b7733000-b773a000 r--s 00000000 08:03 77437      /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b773a000-b773c000 rw-p 00000000 00:00 0 
bf9bf000-bf9e0000 rw-p 00000000 00:00 0          [stack]
Aborted

```

```

darwin@Jennifer:~/libdarwin/project/darwinviewer$ vlc
VLC media player 1.1.12 The Luggage (revision exported)
Warning: call to srand(1335813306)
Warning: call to rand()
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x82ce8fc] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
QGtkStyle was unable to detect the current GTK+ theme.
*** glibc detected *** vlc: malloc(): memory corruption: 0x083d08f8 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6ff22)[0x619f22]
/lib/i386-linux-gnu/libc.so.6(+0x718be)[0x61b8be]
/lib/i386-linux-gnu/libc.so.6(__libc_malloc+0x68)[0x61d7f8]
/usr/lib/i386-linux-gnu/libXi.so.6(XIQueryDevice+0x150)[0xa9c930]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate21x11GetTouchDeviceInfoEv+0x46)[0x5fc84f6]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate24initializeMultitouch_sysEv+0x1b)[0x5fc8adb]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate20initializeMultitouchEv+0xe6)[0x5f55686]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate10initializeEv+0x1c5)[0x5f558e5]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN19QApplicationPrivate9constructEP9_XDisplaymm+0xf4)[0x5f55a54]
/usr/lib/i386-linux-gnu/libQtGui.so.4(_ZN12QApplicationC1ERiPPcbi+0x91)[0x5f561a1]
/usr/lib/vlc/plugins/gui/libqt4_plugin.so(+0x6923e)[0x5bdc23e]
/lib/i386-linux-gnu/libpthread.so.0(+0x6d31)[0x48ad31]
/lib/i386-linux-gnu/libc.so.6(clone+0x5e)[0x67d46e]
======= Memory map: ========
00110000-00157000 r-xp 00000000 08:03 490        /lib/i386-linux-gnu/libdbus-1.so.3.5.7
00157000-00158000 r--p 00046000 08:03 490        /lib/i386-linux-gnu/libdbus-1.so.3.5.7
00158000-00159000 rw-p 00047000 08:03 490        /lib/i386-linux-gnu/libdbus-1.so.3.5.7
00159000-0015b000 r-xp 00000000 08:03 80137      /usr/lib/vlc/plugins/mmxext/libmemcpymmxext_plugin.so
0015b000-0015c000 r--p 00001000 08:03 80137      /usr/lib/vlc/plugins/mmxext/libmemcpymmxext_plugin.so
0015c000-0015d000 rw-p 00002000 08:03 80137      /usr/lib/vlc/plugins/mmxext/libmemcpymmxext_plugin.so
0015d000-00170000 r-xp 00000000 08:03 80058      /usr/lib/vlc/plugins/access/libaccess_bd_plugin.so
00170000-00171000 r--p 00012000 08:03 80058      /usr/lib/vlc/plugins/access/libaccess_bd_plugin.so
00171000-00172000 rw-p 00013000 08:03 80058      /usr/lib/vlc/plugins/access/libaccess_bd_plugin.so
00172000-00174000 r-xp 00000000 08:03 80049      /usr/lib/vlc/plugins/access/libaccess_mmap_plugin.so
00174000-00175000 r--p 00001000 08:03 80049      /usr/lib/vlc/plugins/access/libaccess_mmap_plugin.so
00175000-00176000 rw-p 00002000 08:03 80049      /usr/lib/vlc/plugins/access/libaccess_mmap_plugin.so
00176000-0017d000 r-xp 00000000 08:03 80056      /usr/lib/vlc/plugins/access/libzip_plugin.so
0017d000-0017e000 r--p 00006000 08:03 80056      /usr/lib/vlc/plugins/access/libzip_plugin.so
0017e000-0017f000 rw-p 00007000 08:03 80056      /usr/lib/vlc/plugins/access/libzip_plugin.so
0017f000-0018d000 r-xp 00000000 08:03 79889      /usr/lib/vlc/plugins/meta_engine/libtaglib_plugin.so
0018d000-0018e000 r--p 0000d000 08:03 79889      /usr/lib/vlc/plugins/meta_engine/libtaglib_plugin.so
0018e000-0018f000 rw-p 0000e000 08:03 79889      /usr/lib/vlc/plugins/meta_engine/libtaglib_plugin.so
0018f000-00191000 r-xp 00000000 08:03 79963      /usr/lib/vlc/plugins/control/libsignals_plugin.so
00191000-00192000 r--p 00001000 08:03 79963      /usr/lib/vlc/plugins/control/libsignals_plugin.so
00192000-00193000 rw-p 00002000 08:03 79963      /usr/lib/vlc/plugins/control/libsignals_plugin.so
00193000-00195000 r-xp 00000000 08:03 42049      /usr/lib/vlc/plugins/control/libglobalhotkeys_plugin.so
00195000-00196000 r--p 00002000 08:03 42049      /usr/lib/vlc/plugins/control/libglobalhotkeys_plugin.so
00196000-00197000 rw-p 00003000 08:03 42049      /usr/lib/vlc/plugins/control/libglobalhotkeys_plugin.so
00197000-0019c000 r-xp 00000000 08:03 30125      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0019c000-0019d000 r--p 00004000 08:03 30125      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0019d000-0019e000 rw-p 00005000 08:03 30125      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
0019e000-001b6000 r-xp 00000000 08:03 40905      /usr/lib/i386-linux-gnu/libaudio.so.2.4
001b6000-001b7000 r--p 00017000 08:03 40905      /usr/lib/i386-linux-gnu/libaudio.so.2.4
001b7000-001b8000 rw-p 00018000 08:03 40905      /usr/lib/i386-linux-gnu/libaudio.so.2.4
001b8000-001c9000 r-xp 00000000 08:03 30366      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
001c9000-001ca000 r--p 00010000 08:03 30366      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
001ca000-001cb000 rw-p 00011000 08:03 30366      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
001cc000-001d6000 r-xp 00000000 08:03 80055      /usr/lib/vlc/plugins/access/libdvdnav_plugin.so
001d6000-001d7000 ---p 0000a000 08:03 80055      /usr/lib/vlc/plugins/access/libdvdnav_plugin.so
001d7000-001d8000 r--p 0000a000 08:03 80055      /usr/lib/vlc/plugins/access/libdvdnav_plugin.so
001d8000-001d9000 rw-p 0000b000 08:03 80055      /usr/lib/vlc/plugins/access/libdvdnav_plugin.so
001d9000-001ef000 r-xp 00000000 08:03 30849      /usr/lib/i386-linux-gnu/libICE.so.6.3.0
001ef000-001f0000 r--p 00015000 08:03 30849      /usr/lib/i386-linux-gnu/libICE.so.6.3.0
001f0000-001f1000 rw-p 00016000 08:03 30849      /usr/lib/i386-linux-gnu/libICE.so.6.3.0
001f1000-001f3000 rw-p 00000000 00:00 0 
001f3000-001f7000 r-xp 00000000 08:03 1077       /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
001f7000-001f8000 r--p 00003000 08:03 1077       /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
001f8000-001f9000 rw-p 00004000 08:03 1077       /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
001f9000-001fc000 r-xp 00000000 08:03 1076       /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
001fc000-001fd000 r--p 00002000 08:03 1076       /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
001fd000-001fe000 rw-p 00003000 08:03 1076       /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
001fe000-00209000 r-xp 00000000 08:03 1226       /lib/i386-linux-gnu/libnss_files-2.13.so
00209000-0020a000 r--p 0000a000 08:03 1226       /lib/i386-linux-gnu/libnss_files-2.13.so
0020a000-0020b000 rw-p 0000b000 08:03 1226       /lib/i386-linux-gnu/libnss_files-2.13.so
0020b000-00210000 r-xp 00000000 08:03 3991       /usr/lib/i386-linux-gnu/libffi.so.6.0.0
00210000-00211000 r--p 00004000 08:03 3991       /usr/lib/i386-linux-gnu/libffi.so.6.0.0
00211000-00212000 rw-p 00005000 08:03 3991       /usr/lib/i386-linux-gnu/libffi.so.6.0.0
00212000-00216000 r-xp 00000000 08:03 7470       /lib/i386-linux-gnu/libuuid.so.1.3.0
00216000-00217000 r--p 00003000 08:03 7470       /lib/i386-linux-gnu/libuuid.so.1.3.0
00217000-00218000 rw-p 00004000 08:03 7470       /lib/i386-linux-gnu/libuuid.so.1.3.0
00218000-0021f000 r-xp 00000000 08:03 30972      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
0021f000-00220000 r--p 00006000 08:03 30972      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
00220000-00221000 rw-p 00007000 08:03 30972      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
00223000-00229000 r-xp 00000000 08:03 80126      /usr/lib/vlc/plugins/audio_output/libalsa_plugin.so
00229000-0022a000 r--p 00005000 08:03 80126      /usr/lib/vlc/plugins/audio_output/libalsa_plugin.so
0022a000-0022b000 rw-p 00006000 08:03 80126      /usr/lib/vlc/plugins/audio_output/libalsa_plugin.so
0022b000-00253000 r-xp 00000000 08:03 3809       /lib/i386-linux-gnu/libpng12.so.0.46.0
00253000-00254000 r--p 00027000 08:03 3809       /lib/i386-linux-gnu/libpng12.so.0.46.0
00254000-00255000 rw-p 00028000 08:03 3809       /lib/i386-linux-gnu/libpng12.so.0.46.0
00255000-00257000 r-xp 00000000 08:03 33095      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00257000-00258000 r--p 00001000 08:03 33095      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
00258000-00259000 rw-p 00002000 08:03 33095      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
0025b000-00264000 r-xp 00000000 08:03 33122      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00264000-00265000 r--p 00008000 08:03 33122      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00265000-00266000 rw-p 00009000 08:03 33122      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00266000-00288000 r-xp 00000000 08:03 59446      /usr/lib/libdvdread.so.4.1.3
00288000-00289000 r--p 00021000 08:03 59446      /usr/lib/libdvdread.so.4.1.3
00289000-0028a000 rw-p 00022000 08:03 59446      /usr/lib/libdvdread.so.4.1.3
0028a000-00295000 r-xp 00000000 08:03 33057      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
00295000-00296000 r--p 0000a000 08:03 33057      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
00296000-00297000 rw-p 0000b000 08:03 33057      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
00297000-00299000 r-xp 00000000 08:03 33135      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
00299000-0029a000 r--p 00001000 08:03 33135      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
0029a000-0029b000 rw-p 00002000 08:03 33135      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
0029d000-0029f000 r-xp 00000000 08:03 80152      /usr/lib/libxcb-keysyms.so.1.0.0
0029f000-002a0000 r--p 00001000 08:03 80152      /usr/lib/libxcb-keysyms.so.1.0.0
002a0000-002a1000 rw-p 00002000 08:03 80152      /usr/lib/libxcb-keysyms.so.1.0.0
002a1000-002a3000 r-xp 00000000 08:03 30374      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
002a3000-002a4000 r--p 00001000 08:03 30374      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
002a4000-002a5000 rw-p 00002000 08:03 30374      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
002a5000-002a8000 r-xp 00000000 08:03 33545      /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
002a8000-002a9000 r--p 00002000 08:03 33545      /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
002a9000-002aa000 rw-p 00003000 08:03 33545      /usr/lib/i386-linux-gnu/libavahi-glib.so.1.0.2
002aa000-002bd000 r-xp 00000000 08:03 5490       /lib/i386-linux-gnu/libz.so.1.2.3.4
002bd000-002be000 r--p 00012000 08:03 5490       /lib/i386-linux-gnu/libz.so.1.2.3.4
002be000-002bf000 rw-p 00013000 08:03 5490       /lib/i386-linux-gnu/libz.so.1.2.3.4
002bf000-002d2000 r-xp 00000000 08:03 3617       /lib/i386-linux-gnu/libresolv-2.13.so
002d2000-002d3000 r--p 00012000 08:03 3617       /lib/i386-linux-gnu/libresolv-2.13.so
002d3000-002d4000 rw-p 00013000 08:03 3617       /lib/i386-linux-gnu/libresolv-2.13.so
002d4000-002d6000 rw-p 00000000 00:00 0 
002d9000-003d2000 r-xp 00000000 08:03 73287      /usr/lib/libvlccore.so.4.0.3
003d2000-003d3000 ---p 000f9000 08:03 73287      /usr/lib/libvlccore.so.4.0.3
003d3000-003d8000 r--p 000f9000 08:03 73287      /usr/lib/libvlccore.so.4.0.3
003d8000-003d9000 rw-p 000fe000 08:03 73287      /usr/lib/libvlccore.so.4.0.3
003d9000-00426000 r-xp 00000000 08:03 1075       /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
00426000-00427000 r--p 0004d000 08:03 1075       /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
00427000-00428000 rw-p 0004e000 08:03 1075       /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
00428000-00430000 r-xp 00000000 08:03 30363      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00430000-00431000 r--p 00007000 08:03 30363      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00431000-00432000 rw-p 00008000 08:03 30363      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00432000-00434000 r-xp 00000000 08:03 3623       /lib/i386-linux-gnu/libutil-2.13.so
00434000-00435000 r--p 00001000 08:03 3623       /lib/i386-linux-gnu/libutil-2.13.so
00435000-00436000 rw-p 00002000 08:03 3623       /lib/i386-linux-gnu/libutil-2.13.so
00436000-00439000 r-xp 00000000 08:03 30097      /lib/i386-linux-gnu/libgpg-error.so.0.8.0
00439000-0043a000 r--p 00002000 08:03 30097      /lib/i386-linux-gnu/libgpg-error.so.0.8.0
0043a000-0043b000 rw-p 00003000 08:03 30097      /lib/i386-linux-gnu/libgpg-error.so.0.8.0
0043b000-0043d000 r-xp 00000000 08:03 79955      /usr/lib/vlc/plugins/stream_filter/libstream_filter_record_plugin.so
0043d000-0043e000 r--p 00001000 08:03 79955      /usr/lib/vlc/plugins/stream_filter/libstream_filter_record_plugin.so
0043e000-0043f000 rw-p 00002000 08:03 79955      /usr/lib/vlc/plugins/stream_filter/libstream_filter_record_plugin.so
0043f000-00465000 r-xp 00000000 08:03 6535       /lib/i386-linux-gnu/libexpat.so.1.5.2
00465000-00466000 ---p 00026000 08:03 6535       /lib/i386-linux-gnu/libexpat.so.1.5.2
00466000-00468000 r--p 00026000 08:03 6535       /lib/i386-linux-gnu/libexpat.so.1.5.2
00468000-00469000 rw-p 00028000 08:03 6535       /lib/i386-linux-gnu/libexpat.so.1.5.2
00469000-0047a000 r-xp 00000000 08:03 31869      /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
0047a000-0047b000 r--p 00010000 08:03 31869      /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
0047b000-0047c000 rw-p 00011000 08:03 31869      /usr/lib/i386-linux-gnu/libavahi-client.so.3.2.9
00484000-0049b000 r-xp 00000000 08:03 3615       /lib/i386-linux-gnu/libpthread-2.13.so
0049b000-0049c000 r--p 00016000 08:03 3615       /lib/i386-linux-gnu/libpthread-2.13.so
0049c000-0049d000 rw-p 00017000 08:03 3615       /lib/i386-linux-gnu/libpthread-2.13.so
0049d000-0049f000 rw-p 00000000 00:00 0 
0049f000-0058b000 r-xp 00000000 08:03 33495      /usr/lib/i386-linux-gnu/libasound.so.2.0.0
0058b000-0058f000 r--p 000eb000 08:03 33495      /usr/lib/i386-linux-gnu/libasound.so.2.0.0
0058f000-00590000 rw-p 000ef000 08:03 33495      /usr/lib/i386-linux-gnu/libasound.so.2.0.0
00590000-005a0000 r-xp 00000000 08:03 30128      /usr/lib/i386-linux-gnu/libtasn1.so.3.1.11
005a0000-005a1000 r--p 0000f000 08:03 30128      /usr/lib/i386-linux-gnu/libtasn1.so.3.1.11
005a1000-005a2000 rw-p 00010000 08:03 30128      /usr/lib/i386-linux-gnu/libtasn1.so.3.1.11
005aa000-00722000 r-xp 00000000 08:03 1214       /lib/i386-linux-gnu/libc-2.13.so
00722000-00724000 r--p 00178000 08:03 1214       /lib/i386-linux-gnu/libc-2.13.so
00724000-00725000 rw-p 0017a000 08:03 1214       /lib/i386-linux-gnu/libc-2.13.so
00725000-00728000 rw-p 00000000 00:00 0 
00728000-007af000 r-xp 00000000 08:03 48038      /usr/lib/libtag.so.1.7.0
007af000-007b0000 ---p 00087000 08:03 48038      /usr/lib/libtag.so.1.7.0
007b0000-007b2000 r--p 00087000 08:03 48038      /usr/lib/libtag.so.1.7.0
007b2000-007b3000 rw-p 00089000 08:03 48038      /usr/lib/libtag.so.1.7.0
007b3000-007d6000 r-xp 00000000 08:03 30406      /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
007d6000-007d7000 r--p 00022000 08:03 30406      /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
007d7000-007d8000 rw-p 00023000 08:03 30406      /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.0
007dd000-007e3000 r-xp 00000000 08:03 79957      /usr/lib/vlc/plugins/control/libhotkeys_plugin.so
007e3000-007e4000 r--p 00005000 08:03 79957      /usr/lib/vlc/plugins/control/libhotkeys_plugin.so
007e4000-007e5000 rw-p 00006000 08:03 79957      /usr/lib/vlc/plugins/control/libhotkeys_plugin.so
007f6000-007ff000 r-xp 00000000 08:03 30384      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
007ff000-00800000 r--p 00008000 08:03 30384      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00800000-00801000 rw-p 00009000 08:03 30384      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00801000-0083e000 r-xp 00000000 08:03 2171       /lib/i386-linux-gnu/libpcre.so.3.12.1
0083e000-0083f000 r--p 0003c000 08:03 2171       /lib/i386-linux-gnu/libpcre.so.3.12.1
0083f000-00840000 rw-p 0003d000 08:03 2171       /lib/i386-linux-gnu/libpcre.so.3.12.1
0084c000-0087e000 r-xp 00000000 08:03 30094      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
0087e000-0087f000 ---p 00032000 08:03 30094      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
0087f000-00880000 r--p 00032000 08:03 30094      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00880000-00881000 rw-p 00033000 08:03 30094      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00881000-0089d000 r-xp 00000000 08:03 4042       /lib/i386-linux-gnu/libselinux.so.1
0089d000-0089e000 r--p 0001b000 08:03 4042       /lib/i386-linux-gnu/libselinux.so.1
0089e000-0089f000 rw-p 0001c000 08:03 4042       /lib/i386-linux-gnu/libselinux.so.1
0089f000-008a6000 r-xp 00000000 08:03 30874      /usr/lib/i386-linux-gnu/libSM.so.6.0.1
008a6000-008a7000 r--p 00006000 08:03 30874      /usr/lib/i386-linux-gnu/libSM.so.6.0.1
008a7000-008a8000 rw-p 00007000 08:03 30874      /usr/lib/i386-linux-gnu/libSM.so.6.0.1
008a8000-008d4000 r-xp 00000000 08:03 7970       /usr/lib/libgconf-2.so.4.1.5
008d4000-008d5000 r--p 0002b000 08:03 7970       /usr/lib/libgconf-2.so.4.1.5
008d5000-008d6000 rw-p 0002c000 08:03 7970       /usr/lib/libgconf-2.so.4.1.5
008ea000-00900000 r-xp 00000000 08:03 79996      /usr/lib/vlc/plugins/demux/libplaylist_plugin.so
00900000-00901000 r--p 00015000 08:03 79996      /usr/lib/vlc/plugins/demux/libplaylist_plugin.so
00901000-00902000 rw-p 00016000 08:03 79996      /usr/lib/vlc/plugins/demux/libplaylist_plugin.so
00902000-0091f000 r-xp 00000000 08:03 32865      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
0091f000-00921000 r--p 0001c000 08:03 32865      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
00921000-00922000 rw-p 0001e000 08:03 32865      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
00922000-0094d000 r-xp 00000000 08:03 34092      /usr/lib/i386-linux-gnu/liblua5.1.so.0.0.0
0094d000-0094e000 ---p 0002b000 08:03 34092      /usr/lib/i386-linux-gnu/liblua5.1.so.0.0.0
0094e000-0094f000 r--p 0002b000 08:03 34092      /usr/lib/i386-linux-gnu/liblua5.1.so.0.0.0
0094f000-00950000 rw-p 0002c000 08:03 34092      /usr/lib/i386-linux-gnu/liblua5.1.so.0.0.0
0096c000-00981000 r-xp 00000000 08:03 59456      /usr/lib/libdvdnav.so.4.1.3
00981000-00982000 r--p 00014000 08:03 59456      /usr/lib/libdvdnav.so.4.1.3
00982000-00983000 rw-p 00015000 08:03 59456      /usr/lib/libdvdnav.so.4.1.3
00983000-009a1000 r-xp 00000000 08:03 32952      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
009a1000-009a2000 r--p 0001d000 08:03 32952      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
009a2000-009a3000 rw-p 0001e000 08:03 32952      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
009ad000-009c6000 r-xp 00000000 08:03 73300      /usr/lib/libvlc.so.5.2.1
009c6000-009c7000 r--p 00018000 08:03 73300      /usr/lib/libvlc.so.5.2.1
009c7000-009c8000 rw-p 00019000 08:03 73300      /usr/lib/libvlc.so.5.2.1
009cb000-009cf000 r-xp 00000000 08:03 33106      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
009cf000-009d0000 r--p 00003000 08:03 33106      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
009d0000-009d1000 rw-p 00004000 08:03 33106      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
009f4000-009f6000 r-xp 00000000 08:03 33148      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
009f6000-009f7000 r--p 00001000 08:03 33148      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
009f7000-009f8000 rw-p 00002000 08:03 33148      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
00a1d000-00a41000 r-xp 00000000 08:03 80092      /usr/lib/vlc/plugins/misc/liblua_plugin.so
00a41000-00a42000 r--p 00023000 08:03 80092      /usr/lib/vlc/plugins/misc/liblua_plugin.so
00a42000-00a43000 rw-p 00024000 08:03 80092      /usr/lib/vlc/plugins/misc/liblua_plugin.so
00a6a000-00a86000 r-xp 00000000 08:03 1061       /lib/i386-linux-gnu/libgcc_s.so.1
00a86000-00a87000 r--p 0001b000 08:03 1061       /lib/i386-linux-gnu/libgcc_s.so.1
00a87000-00a88000 rw-p 0001c000 08:03 1061       /lib/i386-linux-gnu/libgcc_s.so.1
00a93000-00aa1000 r-xp 00000000 08:03 30960      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00aa1000-00aa2000 r--p 0000d000 08:03 30960      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00aa2000-00aa3000 rw-p 0000e000 08:03 30960      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
00aa3000-00ace000 r-xp 00000000 08:03 33058      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
00ace000-00acf000 r--p 0002a000 08:03 33058      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
00acf000-00ad0000 rw-p 0002b000 08:03 33058      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
00ad1000-00ad4000 r-xp 00000000 08:03 79954      /usr/lib/vlc/plugins/stream_filter/libstream_filter_rar_plugin.so
00ad4000-00ad5000 r--p 00002000 08:03 79954      /usr/lib/vlc/plugins/stream_filter/libstream_filter_rar_plugin.so
00ad5000-00ad6000 rw-p 00003000 08:03 79954      /usr/lib/vlc/plugins/stream_filter/libstream_filter_rar_plugin.so
00ad6000-00b2e000 r-xp 00000000 08:03 30983      /usr/lib/i386-linux-gnu/libXt.so.6.0.0
00b2e000-00b2f000 r--p 00057000 08:03 30983      /usr/lib/i386-linux-gnu/libXt.so.6.0.0
00b2f000-00b32000 rw-p 00058000 08:03 30983      /usr/lib/i386-linux-gnu/libXt.so.6.0.0
00b45000-00b48000 r-xp 00000000 08:03 1218       /lib/i386-linux-gnu/libdl-2.13.so
00b48000-00b49000 r--p 00002000 08:03 1218       /lib/i386-linux-gnu/libdl-2.13.so
00b49000-00b4a000 rw-p 00003000 08:03 1218       /lib/i386-linux-gnu/libdl-2.13.so
00b59000-00b5d000 r-xp 00000000 08:03 80061      /usr/lib/vlc/plugins/access/libfilesystem_plugin.so
00b5d000-00b5e000 r--p 00003000 08:03 80061      /usr/lib/vlc/plugins/access/libfilesystem_plugin.so
00b5e000-00b5f000 rw-p 00004000 08:03 80061      /usr/lib/vlc/plugins/access/libfilesystem_plugin.so
00b65000-00b67000 r-xp 00000000 08:03 80082      /usr/lib/vlc/plugins/misc/libinhibit_plugin.so
00b67000-00b68000 r--p 00001000 08:03 80082      /usr/lib/vlc/plugins/misc/libinhibit_plugin.so
00b68000-00b69000 rw-p 00002000 08:03 80082      /usr/lib/vlc/plugins/misc/libinhibit_plugin.so
00b69000-00bb0000 r-xp 00000000 08:03 33056      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
00bb0000-00bb1000 r--p 00047000 08:03 33056      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
00bb1000-00bb2000 rw-p 00048000 08:03 33056      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
00bbc000-00bda000 r-xp 00000000 08:03 1209       /lib/i386-linux-gnu/ld-2.13.so
00bda000-00bdb000 r--p 0001d000 08:03 1209       /lib/i386-linux-gnu/ld-2.13.so
00bdb000-00bdc000 rw-p 0001e000 08:03 1209       /lib/i386-linux-gnu/ld-2.13.so
00be3000-00be5000 r-xp 00000000 08:03 80088      /usr/lib/vlc/plugins/misc/libxml_plugin.so
00be5000-00be6000 r--p 00001000 08:03 80088      /usr/lib/vlc/plugins/misc/libxml_plugin.so
00be6000-00be7000 rw-p 00002000 08:03 80088      /usr/lib/vlc/plugins/misc/libxml_plugin.so
00bed000-00bf9000 r-xp 00000000 08:03 31850      /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
00bf9000-00bfa000 r--p 0000b000 08:03 31850      /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
00bfa000-00bfb000 rw-p 0000c000 08:03 31850      /usr/lib/i386-linux-gnu/libavahi-common.so.3.5.3
00c33000-00c36000 r-xp 00000000 08:03 80125      /usr/lib/vlc/plugins/audio_output/liboss_plugin.so
00c36000-00c37000 r--p 00002000 08:03 80125      /usr/lib/vlc/plugins/audio_output/liboss_plugin.so
00c37000-00c38000 rw-p 00003000 08:03 80125      /usr/lib/vlc/plugins/audio_output/liboss_plugin.so
00c80000-00c81000 r-xp 00000000 00:00 0          [vdso]
00c8b000-00c8d000 r-xp 00000000 08:03 30115      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00c8d000-00c8e000 r--p 00001000 08:03 30115      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00c8e000-00c8f000 rw-p 00002000 08:03 30115      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00cc3000-00cc6000 r-xp 00000000 08:03 77795      /usr/lib/i386-linux-gnu/gconv/UTF-16.so
00cc6000-00cc7000 r--p 00002000 08:03 77795      /usr/lib/i386-linux-gnu/gconv/UTF-16.so
00cc7000-00cc8000 rw-p 00003000 08:03 77795      /usr/lib/i386-linux-gnu/gconv/UTF-16.so
00cf8000-00dd6000 r-xp 00000000 08:03 6608       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00dd6000-00dd7000 ---p 000de000 08:03 6608       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00dd7000-00ddb000 r--p 000de000 08:03 6608       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00ddb000-00ddc000 rw-p 000e2000 08:03 6608       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00ddc000-00de3000 rw-p 00000000 00:00 0 
00de3000-00e75000 r-xp 00000000 08:03 3754       /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
00e75000-00e79000 r--p 00091000 08:03 3754       /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
00e79000-00e7a000 rw-p 00095000 08:03 3754       /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
00e98000-00e9f000 r-xp 00000000 08:03 3618       /lib/i386-linux-gnu/librt-2.13.so
00e9f000-00ea0000 r--p 00006000 08:03 3618       /lib/i386-linux-gnu/librt-2.13.so
00ea0000-00ea1000 rw-p 00007000 08:03 3618       /lib/i386-linux-gnu/librt-2.13.so
00eb1000-00ece000 r-xp 00000000 08:03 30136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00ece000-00ecf000 r--p 0001c000 08:03 30136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00ecf000-00ed0000 rw-p 0001d000 08:03 30136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00ed1000-00ef9000 r-xp 00000000 08:03 1219       /lib/i386-linux-gnu/libm-2.13.so
00ef9000-00efa000 r--p 00028000 08:03 1219       /lib/i386-linux-gnu/libm-2.13.so
00efa000-00efb000 rw-p 00029000 08:03 1219       /lib/i386-linux-gnu/libm-2.13.so
00f4a000-00f4d000 r-xp 00000000 08:03 79953      /usr/lib/vlc/plugins/stream_filter/libdecomp_plugin.so
00f4d000-00f4e000 r--p 00002000 08:03 79953      /usr/lib/vlc/plugins/stream_filter/libdecomp_plugin.so
00f4e000-00f4f000 rw-p 00003000 08:03 79953      /usr/lib/vlc/plugins/stream_filter/libdecomp_plugin.so
00f4f000-01096000 r-xp 00000000 08:03 765        /usr/lib/libxml2.so.2.7.8
01096000-0109a000 r--p 00147000 08:03 765        /usr/lib/libxml2.so.2.7.8
0109a000-0109b000 rw-p 0014b000 08:03 765        /usr/lib/libxml2.so.2.7.8
0109b000-0109c000 rw-p 00000000 00:00 0 
0130d000-01372000 r-xp 00000000 08:03 48457      /usr/lib/libgnomevfs-2.so.0.2400.4
01372000-01374000 r--p 00064000 08:03 48457      /usr/lib/libgnomevfs-2.so.0.2400.4
01374000-01376000 rw-p 00066000 08:03 48457      /usr/lib/libgnomevfs-2.so.0.2400.4
014c4000-01606000 r-xp 00000000 08:03 1079       /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
01606000-01608000 r--p 00142000 08:03 1079       /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
01608000-01609000 rw-p 00144000 08:03 1079       /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
01609000-0160a000 rw-p 00000000 00:00 0 
0160a000-01a6b000 r-xp 00000000 08:03 33312      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
01a6b000-01a6f000 r--p 00461000 08:03 33312      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
01a6f000-01a71000 rw-p 00465000 08:03 33312      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
01a71000-01a73000 rw-p 00000000 00:00 0 
01eb2000-01f5d000 r-xp 00000000 08:03 33313      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
01f5d000-01f5f000 r--p 000ab000 08:03 33313      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
01f5f000-01f60000 rw-p 000ad000 08:03 33313      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
024d8000-0276f000 r-xp 00000000 08:03 69484      /usr/lib/i386-linux-gnu/libQtCore.so.4.7.4
0276f000-02776000 r--p 00296000 08:03 69484      /usr/lib/i386-linux-gnu/libQtCore.so.4.7.4
02776000-02779000 rw-p 0029d000 08:03 69484      /usr/lib/i386-linux-gnu/libQtCore.so.4.7.4
03420000-034a2000 r-xp 00000000 08:03 30129      /lib/i386-linux-gnu/libgcrypt.so.11.7.0
034a2000-034a3000 r--p 00081000 08:03 30129      /lib/i386-linux-gnu/libgcrypt.so.11.7.0
034a3000-034a5000 rw-p 00082000 08:03 30129      /lib/i386-linux-gnu/libgcrypt.so.11.7.0
03b21000-03c52000 r-xp 00000000 08:03 30352      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
03c52000-03c53000 ---p 00131000 08:03 30352      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
03c53000-03c54000 r--p 00131000 08:03 30352      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
03c54000-03c56000 rw-p 00132000 08:03 30352      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
03c56000-03c57000 rw-p 00000000 00:00 0 
03dbb000-03e39000 r-xp 00000000 08:03 30105      /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
03e39000-03e3d000 r--p 0007d000 08:03 30105      /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
03e3d000-03e3e000 rw-p 00081000 08:03 30105      /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
0464a000-04711000 r-xp 00000000 08:03 30395      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
04711000-04712000 r--p 000c7000 08:03 30395      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
04712000-04713000 rw-p 000c8000 08:03 30395      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
04713000-04715000 rw-p 00000000 00:00 0 
05b73000-05d81000 r-xp 00000000 08:03 42060      /usr/lib/vlc/plugins/gui/libqt4_plugin.so
05d81000-05d82000 ---p 0020e000 08:03 42060      /usr/lib/vlc/plugins/gui/libqt4_plugin.so
05d82000-05d8d000 r--p 0020e000 08:03 42060      /usr/lib/vlc/plugins/gui/libqt4_plugin.so
05d8d000-05d90000 rw-p 00219000 08:03 42060      /usr/lib/vlc/plugins/gui/libqt4_plugin.so
05df6000-0688e000 r-xp 00000000 08:03 7297       /usr/lib/i386-linux-gnu/libQtGui.so.4.7.4
0688e000-068af000 r--p 00a97000 08:03 7297       /usr/lib/i386-linux-gnu/libQtGui.so.4.7.4
068af000-068b9000 rw-p 00ab8000 08:03 7297       /usr/lib/i386-linux-gnu/libQtGui.so.4.7.4
068b9000-068bc000 rw-p 00000000 00:00 0 
06ee9000-06f93000 r-xp 00000000 08:03 2080       /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
06f93000-06f94000 ---p 000aa000 08:03 2080       /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
06f94000-06f98000 r--p 000aa000 08:03 2080       /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
06f98000-06f99000 rw-p 000ae000 08:03 2080       /usr/lib/i386-linux-gnu/libgnutls.so.26.16.14
07579000-07670000 r-xp 00000000 08:03 1089       /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
07670000-07671000 r--p 000f6000 08:03 1089       /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
07671000-07672000 rw-p 000f7000 08:03 1089       /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
08048000-0804a000 r-xp 00000000 08:03 79806      /usr/bin/vlc
0804a000-0804b000 r--p 00002000 08:03 79806      /usr/bin/vlc
0804b000-0804c000 rw-p 00003000 08:03 79806      /usr/bin/vlc
082ce000-083eb000 rw-p 00000000 00:00 0          [heap]
b72f8000-b72fe000 r--s 00000000 08:03 67459      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b72fe000-b72ff000 ---p 00000000 00:00 0 
b72ff000-b737f000 rw-p 00000000 00:00 0 
b737f000-b7380000 ---p 00000000 00:00 0 
b7380000-b7400000 rw-p 00000000 00:00 0 
b7400000-b7421000 rw-p 00000000 00:00 0 
b7421000-b7500000 ---p 00000000 00:00 0 
b7501000-b7504000 r--s 00000000 08:03 67478      /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b7504000-b7507000 r--s 00000000 08:03 67477      /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b7507000-b7508000 r--s 00000000 08:03 67476      /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b7508000-b750a000 r--s 00000000 08:03 67475      /var/cache/fontconfig/b5ea634b0fb353b8ea17632d1f9ef766-le32d4.cache-3
b750a000-b750e000 r--s 00000000 08:03 67474      /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b750e000-b750f000 r--s 00000000 08:03 67473      /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b750f000-b7510000 r--s 00000000 08:03 67465      /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b7510000-b7511000 r--s 00000000 08:03 67464      /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b7511000-b7515000 r--s 00000000 08:03 67463      /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b7515000-b7519000 r--s 00000000 08:03 67462      /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b7519000-b751c000 r--s 00000000 08:03 67461      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b751c000-b7527000 r--s 00000000 08:03 67460      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b7527000-b7534000 r--s 00000000 08:03 67369      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b7534000-b7535000 ---p 00000000 00:00 0 
b7535000-b75b5000 rw-p 00000000 00:00 0 
b75b5000-b77b5000 r--p 00000000 08:03 5675       /usr/lib/locale/locale-archive
b77b5000-b77b8000 rw-p 00000000 00:00 0 
b77b8000-b77ba000 r--s 00000000 08:03 67487      /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b77ba000-b77bd000 r--s 00000000 08:03 67371      /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b77bd000-b77be000 r--s 00000000 08:03 53176      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b77be000-b77c0000 r--s 00000000 08:03 936        /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b77c0000-b77c3000 r--s 00000000 08:03 67366      /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b77c3000-b77ca000 r--s 00000000 08:03 77437      /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b77ca000-b77cc000 rw-p 00000000 00:00 0 
bf934000-bf955000 rw-p 00000000 00:00 0          [stack]
Aborted

```

This computer does not have a monitor plugged into it most of the time.  We use VNC or SSH to connect to it.  At the same time this Qt error started I am also having issues connected via VNC (using Vino-Server for the VNC server, Vinagre as the client).  Plugging in an HDMI monitor results in a black screen; I don't know if the desktop is actually loading or not.  Booting from a USB live disc also results in the blank black screen.

To address the Qt problem I have tried uninstalling all Qt libraries and reinstalling them (via Synaptic), but that has not helped.  I have a bad feeling that it might be the HD going (it's a flash SSD though, and we've had this motherboard for less than a year).  Some Git project files were also corrupted, which may coroborate the suspicion that it's a fault with the HD.

Does anyone have any suggestions about how to diagnose this problem?  Or how I might go about fixing it if it's not a problem with the HD?

---

### Post by Toz on 2012-04-30
If you're concerned about file corruption, make sure that the theme's files at /usr/share/theme or ~/.gtkrc-2.0 and/or /etc/gtk-2.0/gtkrc (if they exist) have not been corrupted .

Otherwise...

What does your ~/.gtkrc-2.0 or /etc/gtk-2.0/gtkrc file say? If nothing, try adding:
```
gtk-theme-name="<THEME>"
```
...into a ~/.gtkrc-2.0 file where <THEME> is the name of the theme you want to use, 

_and/or_

Try running the following command:
```
gconftool-2 --set --type string /desktop/gnome/interface/gtk_theme <THEME>
```
...again where <THEME> is your theme name.

---

### Post by ve4cib on 2012-05-03
I checked the themes directory, and the themes were present.  I copied over the .gtkrc-2.0 file from a functioning installation, but that did not solve the problem.

Ultimately I just gave up and reinstalled the OS.  Rather than risk catching these little lingering errors it seemed better to just start from a clean install and keep an eye on this if this should ever happen again.

---

