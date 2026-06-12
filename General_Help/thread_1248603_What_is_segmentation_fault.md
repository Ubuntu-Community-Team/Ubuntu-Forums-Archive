---
title: "What is segmentation fault?"
date: 2009-08-24
forum: General Help
---

### Post by 4t0m1c_w07f on 2009-08-24
HI... I've received this error a few times since starting with ubuntu and I've never really known what it means... It's latest strike has been on my Heroes of Newerth game...

This is the crash log:

```
Signal: Segmentation fault

Backtrace:
./hon-x86 [0x804dafe]
[0xb7ffa410]
/usr/lib/libasound.so.2 [0xb6e73174]
/usr/lib/libasound.so.2(snd_pcm_poll_descriptors_revents+0x56) [0xb6e29436]
/usr/lib/libasound.so.2 [0xb6e2ef24]
/usr/lib/libasound.so.2(snd_pcm_wait+0x54) [0xb6e2f0c4]
/usr/lib/libasound.so.2 [0xb6e2f47d]
/usr/lib/libasound.so.2 [0xb6e73a45]
/usr/lib/libasound.so.2(snd_pcm_readi+0x54) [0xb6e29894]
/home/jared/HoN-32/libs-x86/libfmodex.so(_ZN4FMOD10OutputALSA12updateRecordEv+0x50) [0xb7036e50]
/home/jared/HoN-32/libs-x86/libfmodex.so(_ZN4FMOD6Thread8callbackEPv+0xed) [0xb7032fad]
/lib/tls/i686/cmov/libpthread.so.0 [0xb7fd54ff]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb773f49e]

Memory map:
08048000-08050000 r-xp 00000000 08:21 2514945    /home/jared/HoN-32/hon-x86
08050000-08051000 rwxp 00008000 08:21 2514945    /home/jared/HoN-32/hon-x86
08555000-0c0c1000 rwxp 08555000 00:00 0          [heap]
896e3000-898e3000 rwxs 30f43000 00:0f 39193      /dev/nvidia0
898e3000-89ae3000 rwxs 2ea03000 00:0f 39193      /dev/nvidia0
89ae3000-89ce3000 rwxs 2befd000 00:0f 39193      /dev/nvidia0
89ce3000-89ee3000 rwxs 30ef6000 00:0f 39193      /dev/nvidia0
89ff8000-8a1f8000 rwxs 30e8a000 00:0f 39193      /dev/nvidia0
8a1f8000-8a3f8000 rwxs 3558e000 00:0f 39193      /dev/nvidia0
8a463000-8a663000 rwxs 27315000 00:0f 39193      /dev/nvidia0
8a6e3000-8a7ef000 rwxp 8a6e3000 00:00 0 
8a7ef000-8a9ef000 rwxs 27c12000 00:0f 39193      /dev/nvidia0
8a9ef000-8abef000 rwxs 27ae3000 00:0f 39193      /dev/nvidia0
8abef000-8aef2000 rwxp 8abef000 00:00 0 
8af41000-8b048000 rwxp 8af41000 00:00 0 
8b072000-8b0f3000 rwxp 8b072000 00:00 0 
8b118000-8b21f000 rwxp 8b118000 00:00 0 
8b2ca000-8b5c4000 r-xp 00000000 08:21 2523139    /home/jared/HoN-32/game/libgame_shared-x86.so
8b5c4000-8b5d7000 rwxp 002f9000 08:21 2523139    /home/jared/HoN-32/game/libgame_shared-x86.so
8b5d7000-8b5eb000 rwxp 8b5d7000 00:00 0 
8b5eb000-8b747000 r-xp 00000000 08:21 2523137    /home/jared/HoN-32/game/cgame-x86.so
8b747000-8b74a000 rwxp 0015b000 08:21 2523137    /home/jared/HoN-32/game/cgame-x86.so
8b74a000-8b854000 rwxp 8b74a000 00:00 0 
8b87f000-8b900000 rwxp 8b87f000 00:00 0 
8b900000-8bb00000 rwxs 27353000 00:0f 39193      /dev/nvidia0
8bb00000-8bb21000 rwxp 8bb00000 00:00 0 
8bb21000-8bc00000 ---p 8bb21000 00:00 0 
8bc1f000-8ef1e000 rwxp 8bc1f000 00:00 0 
8ef2a000-8ef3c000 r-xp 00000000 08:24 6211       /lib/tls/i686/cmov/libresolv-2.9.so
8ef3c000-8ef3d000 r-xp 00011000 08:24 6211       /lib/tls/i686/cmov/libresolv-2.9.so
8ef3d000-8ef3e000 rwxp 00012000 08:24 6211       /lib/tls/i686/cmov/libresolv-2.9.so
8ef3e000-8ef40000 rwxp 8ef3e000 00:00 0 
8ef40000-8ef45000 r-xp 00000000 08:24 6198       /lib/tls/i686/cmov/libnss_dns-2.9.so
8ef45000-8ef46000 r-xp 00004000 08:24 6198       /lib/tls/i686/cmov/libnss_dns-2.9.so
8ef46000-8ef47000 rwxp 00005000 08:24 6198       /lib/tls/i686/cmov/libnss_dns-2.9.so
8ef57000-947ff000 r-xp 00000000 08:21 57485      /home/jared/HoN-32/game/textures.s2z
947ff000-949ff000 rwxs 1c975000 00:0f 39193      /dev/nvidia0
949ff000-94aff000 rwxs 30c5d000 00:0f 39193      /dev/nvidia0
94aff000-94b00000 rwxs f6c08000 00:0f 39193      /dev/nvidia0
94b00000-94b40000 rwxs 35355000 00:0f 39193      /dev/nvidia0
94b40000-94b60000 rwxs 1c951000 00:0f 39193      /dev/nvidia0
94b60000-94c33000 rwxp 94b60000 00:00 0 
94c33000-94c7d000 rwxp 00000000 00:0f 765        /dev/zero
94c7d000-94c81000 r-xp 00000000 08:24 9382       /usr/lib/libXfixes.so.3.1.0
94c81000-94c82000 rwxp 00003000 08:24 9382       /usr/lib/libXfixes.so.3.1.0
94c82000-94c8a000 r-xp 00000000 08:24 9374       /usr/lib/libXcursor.so.1.0.2
94c8a000-94c8b000 rwxp 00007000 08:24 9374       /usr/lib/libXcursor.so.1.0.2
94c8b000-94c91000 r-xp 00000000 08:24 9400       /usr/lib/libXrandr.so.2.2.0
94c91000-94c92000 r-xp 00006000 08:24 9400       /usr/lib/libXrandr.so.2.2.0
94c92000-94c93000 rwxp 00007000 08:24 9400       /usr/lib/libXrandr.so.2.2.0
94c97000-94c99000 r-xp 00000000 08:24 2635       /lib/libnss_mdns4_minimal.so.2
94c99000-94c9a000 rwxp 00001000 08:24 2635       /lib/libnss_mdns4_minimal.so.2
94c9a000-94c9e000 rwxs 35381000 00:0f 39193      /dev/nvidia0
94c9e000-94ca2000 rwxs 2a3fe000 00:0f 39193      /dev/nvidia0
94ca2000-94ca3000 rwxs e2801000 00:0f 39193      /dev/nvidia0
94ca3000-94d49000 rwxp 94ca3000 00:00 0 
94d49000-94d93000 rwxp 00000000 00:0f 765        /dev/zero
94d93000-94d94000 rwxs 2b83b000 00:0f 39193      /dev/nvidia0
94d94000-94dc8000 rwxp 94d94000 00:00 0 
94dc8000-94de9000 rwxs 00000000 00:09 0          /SYSV00000000 (deleted)
94de9000-9582e000 rwxp 94de9000 00:00 0 
9582e000-96548000 r-xp 00000000 08:24 6796       /usr/lib/libGLcore.so.180.44
96548000-9673a000 rwxp 00d19000 08:24 6796       /usr/lib/libGLcore.so.180.44
9673a000-96746000 rwxp 9673a000 00:00 0 
96746000-967d3000 r-xp 00000000 08:24 6795       /usr/lib/libGL.so.180.44
967d3000-967f1000 rwxp 0008d000 08:24 6795       /usr/lib/libGL.so.180.44
967f1000-96800000 rwxp 967f1000 00:00 0 
96800000-968df000 r-xp 00000000 08:21 2514949    /home/jared/HoN-32/vid_gl2-x86.so
968df000-968e1000 rwxp 000de000 08:21 2514949    /home/jared/HoN-32/vid_gl2-x86.so
968e1000-9691a000 rwxp 968e1000 00:00 0 
9691a000-9691b000 ---p 9691a000 00:00 0 
9691b000-9711b000 rwxp 9691b000 00:00 0 
9711b000-9711c000 ---p 9711b000 00:00 0 
9711c000-9791c000 rwxp 9711c000 00:00 0 
9b91c000-9b91d000 rwxp 9b91c000 00:00 0 
9b91d000-9b91e000 ---p 9b91d000 00:00 0 
9b91e000-9c1ae000 rwxp 9b91e000 00:00 0 
9c1ae000-9c1af000 ---p 9c1ae000 00:00 0 
9c1af000-9c9af000 rwxp 9c1af000 00:00 0 
9c9af000-9c9b0000 ---p 9c9af000 00:00 0 
9c9b0000-9d1b0000 rwxp 9c9b0000 00:00 0 
9d1b0000-a11b1000 rwxs 00000000 00:15 361717     /dev/shm/pulse-shm-3313292439
a11b1000-a11eb000 rwxp a11b1000 00:00 0 
a11eb000-a11f9000 r-xp 00000000 08:24 9380       /usr/lib/libXext.so.6.4.0
a11f9000-a11fa000 r-xp 0000d000 08:24 9380       /usr/lib/libXext.so.6.4.0
a11fa000-a11fb000 rwxp 0000e000 08:24 9380       /usr/lib/libXext.so.6.4.0
a11fb000-a11fc000 r-xp 00000000 08:24 6790       /usr/lib/tls/libnvidia-tls.so.180.44
a11fc000-a11fd000 rwxp 00000000 08:24 6790       /usr/lib/tls/libnvidia-tls.so.180.44
a11fd000-a126c000 r-xp 00000000 08:24 49242      /usr/lib/libGLU.so.1.3.070300
a126c000-a126d000 ---p 0006f000 08:24 49242      /usr/lib/libGLU.so.1.3.070300
a126d000-a126e000 r-xp 0006f000 08:24 49242      /usr/lib/libGLU.so.1.3.070300
a126e000-a126f000 rwxp 00070000 08:24 49242      /usr/lib/libGLU.so.1.3.070300
a126f000-a1270000 rwxs 2a3ff000 00:0f 39193      /dev/nvidia0
a1270000-a1271000 rwxs f6641000 00:0f 39193      /dev/nvidia0
a1271000-a1272000 rwxs 2a3b2000 00:0f 39193      /dev/nvidia0
a1272000-a1273000 rwxs f6060000 00:0f 39193      /dev/nvidia0
a1273000-a127b000 r-xp 00000000 08:24 9402       /usr/lib/libXrender.so.1.3.0
a127b000-a127c000 r-xp 00007000 08:24 9402       /usr/lib/libXrender.so.1.3.0
a127c000-a127d000 rwxp 00008000 08:24 9402       /usr/lib/libXrender.so.1.3.0
a127d000-a127f000 rwxp 00000000 00:0f 765        /dev/zero
a127f000-a1284000 r-xp 00000000 08:24 10627      /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
a1284000-a1285000 r-xp 00004000 08:24 10627      /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
a1285000-a1286000 rwxp 00005000 08:24 10627      /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
a1286000-a12bf000 rwxp a1286000 00:00 0 
a12bf000-a9b52000 r-xp 00000000 08:21 24763      /home/jared/HoN-32/game/resources0.s2z
a9b52000-a9b8b000 rwxp a9b52000 00:00 0 
a9b8b000-b241e000 r-xp 00000000 08:21 24763      /home/jared/HoN-32/game/resources0.s2z
b241e000-b245d000 r-xp 00000000 08:24 13388      /usr/lib/locale/en_ZA.utf8/LC_CTYPE
b245d000-b2548000 r-xp 00000000 08:24 13387      /usr/lib/locale/en_ZA.utf8/LC_COLLATE
b2548000-b2549000 ---p b2548000 00:00 0 
b2549000-b2d49000 rwxp b2549000 00:00 0 
b2d49000-b2d53000 r-xp 00000000 08:24 6200       /lib/tls/i686/cmov/libnss_files-2.9.so
b2d53000-b2d54000 r-xp 00009000 08:24 6200       /lib/tls/i686/cmov/libnss_files-2.9.so
b2d54000-b2d55000 rwxp 0000a000 08:24 6200       /lib/tls/i686/cmov/libnss_files-2.9.so
b2d55000-b6d56000 rwxs 00000000 00:15 361629     /dev/shm/pulse-shm-1716472462
b6d56000-b6d5a000 r-xp 00000000 08:24 2575       /lib/libattr.so.1.1.0
b6d5a000-b6d5b000 r-xp 00003000 08:24 2575       /lib/libattr.so.1.1.0
b6d5b000-b6d5c000 rwxp 00004000 08:24 2575       /lib/libattr.so.1.1.0
b6d5c000-b6d5f000 r-xp 00000000 08:24 2694       /lib/libuuid.so.1.2
b6d5f000-b6d60000 r-xp 00002000 08:24 2694       /lib/libuuid.so.1.2
b6d60000-b6d61000 rwxp 00003000 08:24 2694       /lib/libuuid.so.1.2
b6d61000-b6d66000 r-xp 00000000 08:24 9669       /usr/lib/libgdbm.so.3.0.0
b6d66000-b6d67000 r-xp 00004000 08:24 9669       /usr/lib/libgdbm.so.3.0.0
b6d67000-b6d68000 rwxp 00005000 08:24 9669       /usr/lib/libgdbm.so.3.0.0
b6d68000-b6d6b000 r-xp 00000000 08:24 2586       /lib/libcap.so.2.11
b6d6b000-b6d6c000 r-xp 00002000 08:24 2586       /lib/libcap.so.2.11
b6d6c000-b6d6d000 rwxp 00003000 08:24 2586       /lib/libcap.so.2.11
b6d6d000-b6d82000 r-xp 00000000 08:24 9328       /usr/lib/libICE.so.6.3.0
b6d82000-b6d83000 rwxp 00014000 08:24 9328       /usr/lib/libICE.so.6.3.0
b6d83000-b6d85000 rwxp b6d83000 00:00 0 
b6d85000-b6de2000 r-xp 00000000 08:24 10873      /usr/lib/libpulse.so.0.7.1
b6de2000-b6de3000 r-xp 0005c000 08:24 10873      /usr/lib/libpulse.so.0.7.1
b6de3000-b6de4000 rwxp 0005d000 08:24 10873      /usr/lib/libpulse.so.0.7.1
b6de4000-b6ea7000 r-xp 00000000 08:24 9441       /usr/lib/libasound.so.2.0.0
b6ea7000-b6ea9000 r-xp 000c2000 08:24 9441       /usr/lib/libasound.so.2.0.0
b6ea9000-b6eac000 rwxp 000c4000 08:24 9441       /usr/lib/libasound.so.2.0.0
b6eac000-b6ead000 r-xp 00000000 08:24 13393      /usr/lib/locale/en_ZA.utf8/LC_NUMERIC
b6ead000-b6eae000 r-xp 00000000 08:24 13396      /usr/lib/locale/en_ZA.utf8/LC_TIME
b6eae000-b6eaf000 r-xp 00000000 08:24 13391      /usr/lib/locale/en_ZA.utf8/LC_MONETARY
b6eaf000-b6eb0000 r-xp 00000000 08:24 13397      /usr/lib/locale/en_ZA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b6eb0000-b6eb1000 r-xp 00000000 08:24 13394      /usr/lib/locale/en_ZA.utf8/LC_PAPER
b6eb1000-b6eb2000 r-xp 00000000 08:24 13392      /usr/lib/locale/en_ZA.utf8/LC_NAME
b6eb2000-b6eb3000 r-xp 00000000 08:24 13386      /usr/lib/locale/en_ZA.utf8/LC_ADDRESS
b6eb3000-b6eb4000 r-xp 00000000 08:24 13395      /usr/lib/locale/en_ZA.utf8/LC_TELEPHONE
b6eb4000-b6eb5000 r-xp 00000000 08:24 13390      /usr/lib/locale/en_ZA.utf8/LC_MEASUREMENT
b6eb5000-b6ebc000 r-xs 00000000 08:24 11979      /usr/lib/gconv/gconv-modules.cache
b6ebc000-b6f62000 rwxp b6ebc000 00:00 0 
b6f62000-b6f66000 r-xp 00000000 08:24 9378       /usr/lib/libXdmcp.so.6.0.0
b6f66000-b6f67000 rwxp 00003000 08:24 9378       /usr/lib/libXdmcp.so.6.0.0
b6f67000-b6f69000 r-xp 00000000 08:24 9367       /usr/lib/libXau.so.6.0.0
b6f69000-b6f6a000 r-xp 00001000 08:24 9367       /usr/lib/libXau.so.6.0.0
b6f6a000-b6f6b000 rwxp 00002000 08:24 9367       /usr/lib/libXau.so.6.0.0
b6f6b000-b6f83000 r-xp 00000000 08:24 6242       /usr/lib/libxcb.so.1.1.0
b6f83000-b6f84000 r-xp 00017000 08:24 6242       /usr/lib/libxcb.so.1.1.0
b6f84000-b6f85000 rwxp 00018000 08:24 6242       /usr/lib/libxcb.so.1.1.0
b6f85000-b70c6000 r-xp 00000000 08:21 1056781    /home/jared/HoN-32/libs-x86/libfmodex.so
b70c6000-b70d2000 rwxp 00141000 08:21 1056781    /home/jared/HoN-32/libs-x86/libfmodex.so
b70d2000-b718d000 rwxp b70d2000 00:00 0 
b718d000-b719d000 r-xp 00000000 08:21 1056786    /home/jared/HoN-32/libs-x86/libspeexdsp.so.1
b719d000-b719e000 rwxp 0000f000 08:21 1056786    /home/jared/HoN-32/libs-x86/libspeexdsp.so.1
b719e000-b71b4000 r-xp 00000000 08:21 1056785    /home/jared/HoN-32/libs-x86/libspeex.so.1
b71b4000-b71b5000 rwxp 00016000 08:21 1056785    /home/jared/HoN-32/libs-x86/libspeex.so.1
b71b5000-b71e4000 r-xp 00000000 08:24 2620       /lib/libncurses.so.5.7
b71e4000-b71e6000 r-xp 0002e000 08:24 2620       /lib/libncurses.so.5.7
b71e6000-b71e7000 rwxp 00030000 08:24 2620       /lib/libncurses.so.5.7
b71e7000-b72d1000 r-xp 00000000 08:24 9361       /usr/lib/libX11.so.6.2.0
b72d1000-b72d2000 ---p 000ea000 08:24 9361       /usr/lib/libX11.so.6.2.0
b72d2000-b72d3000 r-xp 000ea000 08:24 9361       /usr/lib/libX11.so.6.2.0
b72d3000-b72d5000 rwxp 000eb000 08:24 9361       /usr/lib/libX11.so.6.2.0
b72d5000-b72d6000 rwxp b72d5000 00:00 0 
b72d6000-b7434000 r-xp 00000000 08:21 41207      /home/jared/HoN-32/libs-x86/libcurl.so.4
b7434000-b744d000 rwxp 0015d000 08:21 41207      /home/jared/HoN-32/libs-x86/libcurl.so.4
b744d000-b7451000 rwxp b744d000 00:00 0 
b7451000-b7586000 r-xp 00000000 08:24 10465      /usr/lib/libxml2.so.2.6.32
b7586000-b7587000 ---p 00135000 08:24 10465      /usr/lib/libxml2.so.2.6.32
b7587000-b758b000 r-xp 00135000 08:24 10465      /usr/lib/libxml2.so.2.6.32
b758b000-b758c000 rwxp 00139000 08:24 10465      /usr/lib/libxml2.so.2.6.32
b758c000-b758d000 rwxp b758c000 00:00 0 
b758d000-b760e000 r-xp 00000000 08:21 1056782    /home/jared/HoN-32/libs-x86/libfreetype.so.6
b760e000-b7612000 rwxp 00080000 08:21 1056782    /home/jared/HoN-32/libs-x86/libfreetype.so.6
b7612000-b7636000 r-xp 00000000 08:21 1056784    /home/jared/HoN-32/libs-x86/libpng12.so.0
b7636000-b7637000 rwxp 00023000 08:21 1056784    /home/jared/HoN-32/libs-x86/libpng12.so.0
b7637000-b764b000 r-xp 00000000 08:24 2701       /lib/libz.so.1.2.3.3
b764b000-b764c000 r-xp 00013000 08:24 2701       /lib/libz.so.1.2.3.3
b764c000-b764d000 rwxp 00014000 08:24 2701       /lib/libz.so.1.2.3.3
b764d000-b7654000 r-xp 00000000 08:24 6213       /lib/tls/i686/cmov/librt-2.9.so
b7654000-b7655000 r-xp 00006000 08:24 6213       /lib/tls/i686/cmov/librt-2.9.so
b7655000-b7656000 rwxp 00007000 08:24 6213       /lib/tls/i686/cmov/librt-2.9.so
b7656000-b7657000 rwxp b7656000 00:00 0 
b7657000-b7659000 r-xp 00000000 08:24 6189       /lib/tls/i686/cmov/libdl-2.9.so
b7659000-b765a000 r-xp 00001000 08:24 6189       /lib/tls/i686/cmov/libdl-2.9.so
b765a000-b765b000 rwxp 00002000 08:24 6189       /lib/tls/i686/cmov/libdl-2.9.so
b765b000-b77b7000 r-xp 00000000 08:24 6183       /lib/tls/i686/cmov/libc-2.9.so
b77b7000-b77b8000 ---p 0015c000 08:24 6183       /lib/tls/i686/cmov/libc-2.9.so
b77b8000-b77ba000 r-xp 0015c000 08:24 6183       /lib/tls/i686/cmov/libc-2.9.so
b77ba000-b77bb000 rwxp 0015e000 08:24 6183       /lib/tls/i686/cmov/libc-2.9.so
b77bb000-b77be000 rwxp b77bb000 00:00 0 
b77be000-b77c8000 r-xp 00000000 08:21 1056783    /home/jared/HoN-32/libs-x86/libgcc_s.so.1
b77c8000-b77c9000 rwxp 00009000 08:21 1056783    /home/jared/HoN-32/libs-x86/libgcc_s.so.1
b77c9000-b77ed000 r-xp 00000000 08:24 6191       /lib/tls/i686/cmov/libm-2.9.so
b77ed000-b77ee000 r-xp 00023000 08:24 6191       /lib/tls/i686/cmov/libm-2.9.so
b77ee000-b77ef000 rwxp 00024000 08:24 6191       /lib/tls/i686/cmov/libm-2.9.so
b77ef000-b789d000 r-xp 00000000 08:21 1056787    /home/jared/HoN-32/libs-x86/libstdc++.so.6
b789d000-b78a1000 r-xp 000ad000 08:21 1056787    /home/jared/HoN-32/libs-x86/libstdc++.so.6
b78a1000-b78a2000 rwxp 000b1000 08:21 1056787    /home/jared/HoN-32/libs-x86/libstdc++.so.6
b78a2000-b78a9000 rwxp b78a2000 00:00 0 
b78a9000-b7f55000 r-xp 00000000 08:21 2514947    /home/jared/HoN-32/libk2-x86.so
b7f55000-b7f6f000 rwxp 006ac000 08:21 2514947    /home/jared/HoN-32/libk2-x86.so
b7f6f000-b7fcf000 rwxp b7f6f000 00:00 0 
b7fcf000-b7fe4000 r-xp 00000000 08:24 6209       /lib/tls/i686/cmov/libpthread-2.9.so
b7fe4000-b7fe5000 r-xp 00014000 08:24 6209       /lib/tls/i686/cmov/libpthread-2.9.so
b7fe5000-b7fe6000 rwxp 00015000 08:24 6209       /lib/tls/i686/cmov/libpthread-2.9.so
b7fe6000-b7fe8000 rwxp b7fe6000 00:00 0 
b7fe8000-b7fe9000 r-xp 00000000 08:24 13389      /usr/lib/locale/en_ZA.utf8/LC_IDENTIFICATION
b7fe9000-b7ff0000 r-xp 00000000 08:24 9359       /usr/lib/libSM.so.6.0.0
b7ff0000-b7ff1000 r-xp 00006000 08:24 9359       /usr/lib/libSM.so.6.0.0
b7ff1000-b7ff2000 rwxp 00007000 08:24 9359       /usr/lib/libSM.so.6.0.0
b7ff2000-b7ff6000 r-xp 00000000 08:24 10620      /usr/lib/alsa-lib/libasound_module_ctl_pulse.so
b7ff6000-b7ff7000 r-xp 00004000 08:24 10620      /usr/lib/alsa-lib/libasound_module_ctl_pulse.so
b7ff7000-b7ff8000 rwxp 00005000 08:24 10620      /usr/lib/alsa-lib/libasound_module_ctl_pulse.so
b7ff8000-b7ffa000 rwxp b7ff8000 00:00 0 
b7ffa000-b7ffb000 r-xp b7ffa000 00:00 0          [vdso]
b7ffb000-b8017000 r-xp 00000000 08:24 2563       /lib/ld-2.9.so
b8017000-b8018000 r-xp 0001b000 08:24 2563       /lib/ld-2.9.so
b8018000-b8019000 rwxp 0001c000 08:24 2563       /lib/ld-2.9.so
bfcfa000-bfd18000 rwxp bffe2000 00:00 0          [stack]

State:
GS 0x00000033
FS -0x3ff00000
ES -0x3fefff85
DS -0x000ff85
EDI -0x68ee5dc0
ESI -0x68ee5d8a
EBP -0x68ee5e18
ESP -0x68ee5e30
EBX -0x4915700c
EDX 0x08ba6cf8
ECX 0x08ba40e0
EAX 0x00000000
TRAPNO 0x0000000e
ERR 0x00000004
EIP -0x4918ce8c
CS 0x00000073
EFL 0x00010282
UESP -0x68ee5e30
SS_T 0x0000007b
```

And this is the terminal output:

```
jared@4t0m1c-w0rM:~/HoN-32$ ./hon_update-x86
warning: The VAD has been replaced by a hack pending a complete rewrite
Crash log saved as '/home/jared/.Heroes of Newerth/game/crash_0.1.38.0_02.log'
Segmentation fault

```

---

### Post by Pythack on 2009-08-24
Hello.

We call "segmentation fault" when a program tries to access memory that is booked.

This memory is forbidden for the program and linux closes the program.

A segmentation fault was caused by a programming error, so please report this bug :p

Pythack.

---

### Post by Slim Odds on 2009-08-24
> **Pythack said:**
> A segmentation fault was caused by a programming error, so please report this bug :p


Hardware problems can also cause segmentation faults.

Especially, bad RAM.

---

### Post by 4t0m1c_w07f on 2009-08-24
Thanks for the reply... Any solution? Or how do I find out if there is bad RAM?

---

### Post by CatKiller on 2009-08-24
> **4t0m1c_w07f said:**
> Thanks for the reply... Any solution? 

As Pythack says, [segmentation faults]("http://en.wikipedia.org/wiki/Segmentation_fault") are caused when a program tries to access memory in a way that is isn't actually able to. What you do about it depends on what's caused it. It might be a bug in the application, or it might be a bug in the kernel's memory handling, or it might be caused by a program attempting to write directly to the video card's memory ("direct rendering") when the driver doesn't support that operation.

> Or how do I find out if there is bad RAM?

memtest (from the boot menu) is a good first port of call. Leaving it to run overnight is generally a reasonable amount to see if you've got a fault with your RAM. Any errors at all mean that you've got a problem; there isn't a "safe" level of errors when it comes to RAM.

---

