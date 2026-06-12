---
title: "Ubuntu froze, upon restart, Pidgin doesn't work.  (terminal post included)"
date: 2009-07-11
forum: General Help
---

### Post by Mashuteichou on 2009-07-11
Ubuntu is making me slightly irritated.  It likes to randomly freeze at seemingly random times.  For example, yesterday I was watching a movie.  All of a sudden, right in the middle of a seen, the screen dims over a period of about 30 seconds, till the point I can barely see any movement.  No commands worked, couldn't exit, keyboard wouldn't work, nothing.  Just flat froze.  So I had to hold the power button to kill it.  Now Pidgin doesn't work.  

Another time about 4 days ago, I woke up, and the computer was froze in screen off mode.  I have it set so after 2 min, the screen shuts off because its a laptop.  Works well about 90% of the time.  10% of the time it freezes in that mode.  

So heres the pidgin terminal message.  


*** glibc detected *** pidgin: double free or corruption (out): 0x0a2acc68 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7543604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb75455b6]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb7770126]
/usr/lib/libglib-2.0.so.0(g_strfreev+0x20)[0xb7789090]
/usr/lib/libgstreamer-0.10.so.0[0xb7e658b0]
/usr/lib/libglib-2.0.so.0(g_list_foreach+0x27)[0xb77653a7]
/usr/lib/libgstreamer-0.10.so.0[0xb7e67836]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0x173)[0xb77f2df3]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unref+0x8f)[0xb7e2830f]
/usr/lib/libgstreamer-0.10.so.0[0xb7e71f49]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0x173)[0xb77f2df3]
/usr/lib/libgstreamer-0.10.so.0(gst_object_unref+0x8f)[0xb7e2830f]
/usr/lib/libgstreamer-0.10.so.0[0xb7e6f7bd]
/usr/lib/libgstreamer-0.10.so.0(gst_deinit+0x14e)[0xb7e267de]
pidgin[0x80e5435]
/usr/lib/libpurple.so.0(purple_sound_uninit+0x25)[0xb76c9d55]
/usr/lib/libpurple.so.0(purple_core_quit+0xad)[0xb769b40d]
pidgin[0x807a534]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a60526]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb77f0c7b]
/usr/lib/libgobject-2.0.so.0[0xb7806e57]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb780834f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7808936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b7b2ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x49c)[0xb7a5a4dc]
/usr/lib/libgdk-x11-2.0.so.0[0xb78e734a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb7767b88]
/usr/lib/libglib-2.0.so.0[0xb776b0eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb776b5ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7a5a7d9]
pidgin(main+0x89a)[0x80c30ba]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb74ea775]
pidgin[0x806daa1]
======= Memory map: ========
08048000-0810e000 r-xp 00000000 08:11 4588389    /usr/bin/pidgin
0810e000-0810f000 r--p 000c5000 08:11 4588389    /usr/bin/pidgin
0810f000-08112000 rw-p 000c6000 08:11 4588389    /usr/bin/pidgin
09d4f000-0a82c000 rw-p 09d4f000 00:00 0          [heap]
b2935000-b2936000 r-xp 00000000 08:11 2097344    /usr/lib/gconv/ISO8859-1.so
b2936000-b2937000 r--p 00001000 08:11 2097344    /usr/lib/gconv/ISO8859-1.so
b2937000-b2938000 rw-p 00002000 08:11 2097344    /usr/lib/gconv/ISO8859-1.so
b2938000-b2998000 rw-s 00000000 00:09 4161554    /SYSV00000000 (deleted)
b2998000-b29f8000 rw-s 00000000 00:09 4128781    /SYSV00000000 (deleted)
b29f8000-b2a84000 r--p 00000000 08:11 4817696    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b2a84000-b2a9b000 r--s 00000000 08:11 5099136    /var/lib/aspell/en_CA-wo_accents-only.rws
b2a9b000-b2d23000 r--s 00000000 08:11 5099130    /var/lib/aspell/en-common.rws
b2d23000-b2d62000 r-xp 00000000 08:11 4589652    /usr/lib/libhunspell-1.2.so.0.0.0
b2d62000-b2d63000 r--p 0003e000 08:11 4589652    /usr/lib/libhunspell-1.2.so.0.0.0
b2d63000-b2d67000 rw-p 0003f000 08:11 4589652    /usr/lib/libhunspell-1.2.so.0.0.0
b2d7d000-b2d88000 r-xp 00000000 08:11 1835012    /usr/lib/enchant/libenchant_ispell.so
b2d88000-b2d89000 r--p 0000a000 08:11 1835012    /usr/lib/enchant/libenchant_ispell.so
b2d89000-b2d8a000 rw-p 0000b000 08:11 1835012    /usr/lib/enchant/libenchant_ispell.so
b2d8a000-b2e1e000 r-xp 00000000 08:11 4589180    /usr/lib/libaspell.so.15.1.4
b2e1e000-b2e21000 r--p 00093000 08:11 4589180    /usr/lib/libaspell.so.15.1.4
b2e21000-b2e22000 rw-p 00096000 08:11 4589180    /usr/lib/libaspell.so.15.1.4
b2e22000-b2e26000 rw-p b2e22000 00:00 0 
b2e27000-b2e29000 r-xp 00000000 08:11 1835014    /usr/lib/enchant/libenchant_zemberek.so
b2e29000-b2e2a000 r--p 00001000 08:11 1835014    /usr/lib/enchant/libenchant_zemberek.so
b2e2a000-b2e2b000 rw-p 00002000 08:11 1835014    /usr/lib/enchant/libenchant_zemberek.so
b2e2b000-b2e2f000 r-xp 00000000 08:11 1835013    /usr/lib/enchant/libenchant_myspell.so
b2e2f000-b2e30000 r--p 00003000 08:11 1835013    /usr/lib/enchant/libenchant_myspell.so
b2e30000-b2e31000 rw-p 00004000 08:11 1835013    /usr/lib/enchant/libenchant_myspell.so
b2e31000-b2e39000 r-xp 00000000 08:11 1835011    /usr/lib/enchant/libenchant_hspell.so
b2e39000-b2e3a000 r--p 00007000 08:11 1835011    /usr/lib/enchant/libenchant_hspell.so
b2e3a000-b2e3c000 rw-p 00008000 08:11 1835011    /usr/lib/enchant/libenchant_hspell.so
b2e3c000-b2ed4000 r--p 00000000 08:11 4817697    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b2ed4000-b2eda000 r--s 00000000 08:11 5098867    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b2eda000-b2ee1000 r--s 00000000 08:11 5099906    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b2ee1000-b2ee9000 r--s 00000000 08:11 5099904    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b2ee9000-b2ef4000 r--s 00000000 08:11 5099903    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b2ef4000-b2f16000 r--s 00000000 08:11 5099900    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b2f16000-b2f1d000 r--s 00000000 08:11 5099894    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b2f1d000-b2f23000 r--s 00000000 08:11 5099892    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b2f23000-b2f3d000 r--s 00000000 08:11 4768804    /usr/share/mime/mime.cache
b2f3d000-b2f49000 r-xp 00000000 08:11 4590618    /usr/lib/libmjpegutils-1.9.so.0.0.0
b2f49000-b2f4a000 r--p 0000c000 08:11 4590618    /usr/lib/libmjpegutils-1.9.so.0.0.0
b2f4a000-b2f4b000 rw-p 0000d000 08:11 4590618    /usr/lib/libmjpegutils-1.9.so.0.0.0
b2f4b000-b2f77000 r-xp 00000000 08:11 4590619    /usr/lib/libmpeg2encpp-1.9.so.0.0.0
b2f77000-b2f78000 r--p 0002c000 08:11 4590619    /usr/lib/libmpeg2encpp-1.9.so.0.0.0
b2f78000-b2f79000 rw-p 0002d000 08:11 4590619    /usr/lib/libmpeg2encpp-1.9.so.0.0.0
b2f79000-b2f7a000 rw-p b2f79000 00:00 0 
b2f7a000-b2f7c000 r-xp 00000000 08:11 1835010    /usr/lib/enchant/libenchant_aspell.so
b2f7c000-b2f7d000 r--p 00001000 08:11 1835010    /usr/lib/enchant/libenchant_aspell.so
b2f7d000-b2f7e000 rw-p 00002000 08:11 1835010    /usr/lib/enchant/libenchant_aspell.so
b2f7e000-b2f85000 r--s 00000000 08:11 5098873    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b2f85000-b2f8e000 r-xp 00000000 08:11 2506954    /usr/lib/gstreamer-0.10/libgstlame.so
b2f8e000-b2f8f000 r--p 00009000 08:11 2506954    /usr/lib/gstreamer-0.10/libgstlame.so
b2f8f000-b2f90000 rw-p 0000a000 08:11 2506954    /usr/lib/gstreamer-0.10/libgstlame.so
b2f90000-b2f9b000 r-xp 00000000 08:11 2506952    /usr/lib/gstreamer-0.10/libgstmpeg2enc.so
b2f9b000-b2f9c000 r--p 0000a000 08:11 2506952    /usr/lib/gstreamer-0.10/libgstmpeg2enc.so
b2f9c000-b2f9d000 rw-p 0000b000 08:11 2506952    /usr/lib/gstreamer-0.10/libgstmpeg2enc.so
b2f9d000-b2fb2000 r-xp 00000000 08:11 4590335    /usr/lib/libdvdnav.so.4.1.3
b2fb2000-b2fb3000 r--p 00014000 08:11 4590335    /usr/lib/libdvdnav.so.4.1.3
b2fb3000-b2fb4000 rw-p 00015000 08:11 4590335    /usr/lib/libdvdnav.so.4.1.3
b2fb5000-b2fbb000 r-xp 00000000 08:11 2506953    /usr/lib/gstreamer-0.10/libgstx264.so
b2fbb000-b2fbc000 r--p 00005000 08:11 2506953    /usr/lib/gstreamer-0.10/libgstx264.so
b2fbc000-b2fbd000 rw-p 00006000 08:11 2506953    /usr/lib/gstreamer-0.10/libgstx264.so
b2fbd000-b2fc8000 r-xp 00000000 08:11 2506950    /usr/lib/gstreamer-0.10/libgstxvid.so
b2fc8000-b2fc9000 r--p 0000a000 08:11 2506950    /usr/lib/gstreamer-0.10/libgstxvid.so
b2fc9000-b2fca000 rw-p 0000b000 08:11 2506950    /usr/lib/gstreamer-0.10/libgstxvid.so
b2fca000-b2ff4000 r-xp 00000000 08:11 2506949    /usr/lib/gstreamer-0.10/libresindvd.so
b2ff4000-b2ff5000 r--p 00029000 08:11 2506949    /usr/lib/gstreamer-0.10/libresindvd.so
b2ff5000-b2ff6000 rw-p 0002a000 08:11 2506949    /usr/lib/gstreamer-0.10/libresindvd.so
b2ff6000-b3004000 r-xp 00000000 08:11 4590610    /usr/lib/libWildMidi.so.0.0.0
b3004000-b3006000 rw-p 0000d000 08:11 4590610    /usr/lib/libWildMidi.so.0.0.0
b3006000-b300e000 rw-p b3006000 00:00 0 
b300e000-b3013000 r-xp 00000000 08:11 2506951    /usr/lib/gstreamer-0.10/libgstfaac.so
b3013000-b3014000 r--p 00004000 08:11 2506951    /usr/lib/gstreamer-0.10/libgstfaac.so
b3014000-b3015000 rw-p 00005000 08:11 2506951    /usr/lib/gstreamer-0.10/libgstfaac.so
b3015000-b301d000 r-xp 00000000 08:11 2506947    /usr/lib/gstreamer-0.10/libgstxdgmime.so
b301d000-b301e000 r--p 00007000 08:11 2506947    /usr/lib/gstreamer-0.10/libgstxdgmime.so
b301e000-b301f000 rw-p 00008000 08:11 2506947    /usr/lib/gstreamer-0.10/libgstxdgmime.so
b301f000-b3022000 r-xp 00000000 08:11 2506944    /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b3022000-b3023000 r--p 00002000 08:11 2506944    /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b3023000-b3024000 rw-p 00003000 08:11 2506944    /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b3024000-b304e000 r-xp 00000000 08:11 4589760    /usr/lib/libmusicbrainz.so.4.0.3
b304e000-b304f000 r--p 00029000 08:11 4589760    /usr/lib/libmusicbrainz.so.4.0.3
b304f000-bAborted

---

