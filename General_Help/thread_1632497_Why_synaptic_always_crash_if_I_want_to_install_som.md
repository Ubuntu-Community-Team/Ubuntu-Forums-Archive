---
title: "Why synaptic always crash if I want to install somthing?"
date: 2010-11-28
forum: General Help
---

### Post by dantetwc on 2010-11-28
Everything I try to install something by synaptic, it will crash immediately.
This happens to filezilla and disk utility  too.
How can I solve this?
Thanks.

```
 *** glibc detected *** palimpsest: malloc(): memory corruption: 0x0000000001ea7280 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f16db9fc4b6]
/lib/libc.so.6(+0x7b55f)[0x7f16dba0055f]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7f16dba0138e]
/usr/lib/libpixman-1.so.0(+0x1724b)[0x7f16d91b424b]
/usr/lib/libpixman-1.so.0(pixman_image_create_solid_fill+0x9)[0x7f16d91d58b9]
/usr/lib/libpixman-1.so.0(pixman_image_fill_boxes+0x23a)[0x7f16d91cf63a]
/usr/lib/libcairo.so.2(+0x27c68)[0x7f16dd18ac68]
/usr/lib/libcairo.so.2(+0x48848)[0x7f16dd1ab848]
/usr/lib/libcairo.so.2(+0x4b885)[0x7f16dd1ae885]
/usr/lib/libcairo.so.2(+0x48861)[0x7f16dd1ab861]
/usr/lib/libcairo.so.2(+0x4cac7)[0x7f16dd1afac7]
/usr/lib/libcairo.so.2(+0x4cc92)[0x7f16dd1afc92]
/usr/lib/libcairo.so.2(+0x4d8d9)[0x7f16dd1b08d9]
/usr/lib/libcairo.so.2(+0x4a191)[0x7f16dd1ad191]
/usr/lib/libcairo.so.2(+0x2282a)[0x7f16dd18582a]
/usr/lib/libcairo.so.2(cairo_stroke_preserve+0x1b)[0x7f16dd17c49b]
/usr/lib/libcairo.so.2(cairo_stroke+0x9)[0x7f16dd17c4c9]
/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so(murrine_draw_focus+0x5e)[0x7f16d786a15e]
/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so(+0xf724)[0x7f16d785a724]
/usr/lib/libgtk-x11-2.0.so.0(+0x240008)[0x7f16ded2d008]
/usr/lib/libgtk-x11-2.0.so.0(+0x240115)[0x7f16ded2d115]
/usr/lib/libgtk-x11-2.0.so.0(+0x13a9d8)[0x7f16dec279d8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f16dc609a6e]
/usr/lib/libgobject-2.0.so.0(+0x24120)[0x7f16dc61f120]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x62b)[0x7f16dc6207db]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f16dc620f53]
/usr/lib/libgtk-x11-2.0.so.0(+0x2536df)[0x7f16ded406df]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x556)[0x7f16dec211b6]
/usr/lib/libgdk-x11-2.0.so.0(+0x439da)[0x7f16de2619da]
/usr/lib/libgdk-x11-2.0.so.0(+0x43987)[0x7f16de261987]
======= Memory map: ========
00400000-0041e000 r-xp 00000000 08:01 19973561                           /usr/bin/palimpsest
0061d000-0061e000 r--p 0001d000 08:01 19973561                           /usr/bin/palimpsest
0061e000-0061f000 rw-p 0001e000 08:01 19973561                           /usr/bin/palimpsest
0061f000-00620000 rw-p 00000000 00:00 0 
01cc9000-01f3d000 rw-p 00000000 00:00 0                                  [heap]
7f16cc000000-7f16cc021000 rw-p 00000000 00:00 0 
7f16cc021000-7f16d0000000 ---p 00000000 00:00 0 
7f16d3bd7000-7f16d3bec000 r-xp 00000000 08:01 119508554                  /lib/libgcc_s.so.1
7f16d3bec000-7f16d3deb000 ---p 00015000 08:01 119508554                  /lib/libgcc_s.so.1
7f16d3deb000-7f16d3dec000 r--p 00014000 08:01 119508554                  /lib/libgcc_s.so.1
7f16d3dec000-7f16d3ded000 rw-p 00015000 08:01 119508554                  /lib/libgcc_s.so.1
7f16d3dfc000-7f16d3f40000 r-xp 00000000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7f16d3f40000-7f16d413f000 ---p 00144000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7f16d413f000-7f16d4147000 r--p 00143000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7f16d4147000-7f16d4149000 rw-p 0014b000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7f16d4149000-7f16d414a000 rw-p 00000000 00:00 0 
7f16d414a000-7f16d4180000 r-xp 00000000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7f16d4180000-7f16d437f000 ---p 00036000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7f16d437f000-7f16d4380000 r--p 00035000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7f16d4380000-7f16d4383000 rw-p 00036000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7f16d4383000-7f16d43b6000 r-xp 00000000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7f16d43b6000-7f16d45b6000 ---p 00033000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7f16d45b6000-7f16d45b7000 r--p 00033000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7f16d45b7000-7f16d45b8000 rw-p 00034000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7f16d45b8000-7f16d45ba000 r-xp 00000000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f16d45ba000-7f16d47b9000 ---p 00002000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f16d47b9000-7f16d47ba000 r--p 00001000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f16d47ba000-7f16d47bb000 rw-p 00002000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f16d47bb000-7f16d47bd000 r-xp 00000000 08:01 119508844                  /lib/libutil-2.12.1.so
7f16d47bd000-7f16d49bc000 ---p 00002000 08:01 119508844                  /lib/libutil-2.12.1.so
7f16d49bc000-7f16d49bd000 r--p 00001000 08:01 119508844                  /lib/libutil-2.12.1.so
7f16d49bd000-7f16d49be000 rw-p 00002000 08:01 119508844                  /lib/libutil-2.12.1.so
7f16d49be000-7f16d49d4000 r-xp 00000000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7f16d49d4000-7f16d4bd4000 ---p 00016000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7f16d4bd4000-7f16d4bd5000 r--p 00016000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7f16d4bd5000-7f16d4bd6000 rw-p 00017000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7f16d4bd6000-7f16d4bfe000 r-xp 00000000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7f16d4bfe000-7f16d4dfe000 ---p 00028000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7f16d4dfe000-7f16d4dff000 r--p 00028000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7f16d4dff000-7f16d4e00000 rw-p 00029000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7f16d4e00000-7f16d4e02000 r-xp 00000000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f16d4e02000-7f16d5001000 ---p 00002000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f16d5001000-7f16d5002000 r--p 00001000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f16d5002000-7f16d5003000 rw-p 00002000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f16d5003000-7f16d500c000 r--s 00000000 08:01 87208984                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7f16d500c000-7f16d500e000 r--s 00000000 08:01 87209616                   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3*** glibc detected *** palimpsest: malloc(): memory corruption: 0x0000000000b2b280 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7fc0ed8d44b6]
/lib/libc.so.6(+0x7b55f)[0x7fc0ed8d855f]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7fc0ed8d938e]
/usr/lib/libpixman-1.so.0(+0x1724b)[0x7fc0eb08c24b]
/usr/lib/libpixman-1.so.0(pixman_image_create_solid_fill+0x9)[0x7fc0eb0ad8b9]
/usr/lib/libpixman-1.so.0(pixman_image_fill_boxes+0x23a)[0x7fc0eb0a763a]
/usr/lib/libcairo.so.2(+0x27c68)[0x7fc0ef062c68]
/usr/lib/libcairo.so.2(+0x48848)[0x7fc0ef083848]
/usr/lib/libcairo.so.2(+0x4b885)[0x7fc0ef086885]
/usr/lib/libcairo.so.2(+0x48861)[0x7fc0ef083861]
/usr/lib/libcairo.so.2(+0x4cac7)[0x7fc0ef087ac7]
/usr/lib/libcairo.so.2(+0x4cc92)[0x7fc0ef087c92]
/usr/lib/libcairo.so.2(+0x4d8d9)[0x7fc0ef0888d9]
/usr/lib/libcairo.so.2(+0x4a191)[0x7fc0ef085191]
/usr/lib/libcairo.so.2(+0x2282a)[0x7fc0ef05d82a]
/usr/lib/libcairo.so.2(cairo_stroke_preserve+0x1b)[0x7fc0ef05449b]
/usr/lib/libcairo.so.2(cairo_stroke+0x9)[0x7fc0ef0544c9]
/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so(murrine_draw_focus+0x5e)[0x7fc0e974215e]
/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so(+0xf724)[0x7fc0e9732724]
/usr/lib/libgtk-x11-2.0.so.0(+0x240008)[0x7fc0f0c05008]
/usr/lib/libgtk-x11-2.0.so.0(+0x240115)[0x7fc0f0c05115]
/usr/lib/libgtk-x11-2.0.so.0(+0x13a9d8)[0x7fc0f0aff9d8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7fc0ee4e1a6e]
/usr/lib/libgobject-2.0.so.0(+0x24120)[0x7fc0ee4f7120]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x62b)[0x7fc0ee4f87db]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7fc0ee4f8f53]
/usr/lib/libgtk-x11-2.0.so.0(+0x2536df)[0x7fc0f0c186df]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x556)[0x7fc0f0af91b6]
/usr/lib/libgdk-x11-2.0.so.0(+0x439da)[0x7fc0f01399da]
/usr/lib/libgdk-x11-2.0.so.0(+0x43987)[0x7fc0f0139987]
======= Memory map: ========
00400000-0041e000 r-xp 00000000 08:01 19973561                           /usr/bin/palimpsest
0061d000-0061e000 r--p 0001d000 08:01 19973561                           /usr/bin/palimpsest
0061e000-0061f000 rw-p 0001e000 08:01 19973561                           /usr/bin/palimpsest
0061f000-00620000 rw-p 00000000 00:00 0 
0094d000-00bc1000 rw-p 00000000 00:00 0                                  [heap]
7fc0e0000000-7fc0e0021000 rw-p 00000000 00:00 0 
7fc0e0021000-7fc0e4000000 ---p 00000000 00:00 0 
7fc0e5aaf000-7fc0e5ac4000 r-xp 00000000 08:01 119508554                  /lib/libgcc_s.so.1
7fc0e5ac4000-7fc0e5cc3000 ---p 00015000 08:01 119508554                  /lib/libgcc_s.so.1
7fc0e5cc3000-7fc0e5cc4000 r--p 00014000 08:01 119508554                  /lib/libgcc_s.so.1
7fc0e5cc4000-7fc0e5cc5000 rw-p 00015000 08:01 119508554                  /lib/libgcc_s.so.1
7fc0e5cd4000-7fc0e5e18000 r-xp 00000000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7fc0e5e18000-7fc0e6017000 ---p 00144000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7fc0e6017000-7fc0e601f000 r--p 00143000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7fc0e601f000-7fc0e6021000 rw-p 0014b000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7fc0e6021000-7fc0e6022000 rw-p 00000000 00:00 0 
7fc0e6022000-7fc0e6058000 r-xp 00000000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7fc0e6058000-7fc0e6257000 ---p 00036000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7fc0e6257000-7fc0e6258000 r--p 00035000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7fc0e6258000-7fc0e625b000 rw-p 00036000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7fc0e625b000-7fc0e628e000 r-xp 00000000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7fc0e628e000-7fc0e648e000 ---p 00033000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7fc0e648e000-7fc0e648f000 r--p 00033000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7fc0e648f000-7fc0e6490000 rw-p 00034000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7fc0e6490000-7fc0e6492000 r-xp 00000000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7fc0e6492000-7fc0e6691000 ---p 00002000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7fc0e6691000-7fc0e6692000 r--p 00001000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7fc0e6692000-7fc0e6693000 rw-p 00002000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7fc0e6693000-7fc0e6695000 r-xp 00000000 08:01 119508844                  /lib/libutil-2.12.1.so
7fc0e6695000-7fc0e6894000 ---p 00002000 08:01 119508844                  /lib/libutil-2.12.1.so
7fc0e6894000-7fc0e6895000 r--p 00001000 08:01 119508844                  /lib/libutil-2.12.1.so
7fc0e6895000-7fc0e6896000 rw-p 00002000 08:01 119508844                  /lib/libutil-2.12.1.so
7fc0e6896000-7fc0e68ac000 r-xp 00000000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7fc0e68ac000-7fc0e6aac000 ---p 00016000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7fc0e6aac000-7fc0e6aad000 r--p 00016000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7fc0e6aad000-7fc0e6aae000 rw-p 00017000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7fc0e6aae000-7fc0e6ad6000 r-xp 00000000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7fc0e6ad6000-7fc0e6cd6000 ---p 00028000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7fc0e6cd6000-7fc0e6cd7000 r--p 00028000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7fc0e6cd7000-7fc0e6cd8000 rw-p 00029000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7fc0e6cd8000-7fc0e6cda000 r-xp 00000000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7fc0e6cda000-7fc0e6ed9000 ---p 00002000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7fc0e6ed9000-7fc0e6eda000 r--p 00001000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7fc0e6eda000-7fc0e6edb000 rw-p 00002000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7fc0e6edb000-7fc0e6ee4000 r--s 00000000 08:01 87208984                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7fc0e6ee4000-7fc0e6ee6000 r--s 00000000 08:01 87209616                   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3*** glibc detected *** palimpsest: malloc(): memory corruption: 0x000000000104c9c0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f313899e4b6]
/lib/libc.so.6(+0x7b55f)[0x7f31389a255f]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7f31389a338e]
/usr/lib/libpixman-1.so.0(+0x1724b)[0x7f313615624b]
/usr/lib/libpixman-1.so.0(pixman_image_create_solid_fill+0x9)[0x7f31361778b9]
/usr/lib/libpixman-1.so.0(pixman_image_fill_boxes+0x23a)[0x7f313617163a]
/usr/lib/libcairo.so.2(+0x27c68)[0x7f313a12cc68]
/usr/lib/libcairo.so.2(+0x48848)[0x7f313a14d848]
/usr/lib/libcairo.so.2(+0x4b885)[0x7f313a150885]
/usr/lib/libcairo.so.2(+0x48861)[0x7f313a14d861]
/usr/lib/libcairo.so.2(+0x4cac7)[0x7f313a151ac7]
/usr/lib/libcairo.so.2(+0x4cc92)[0x7f313a151c92]
/usr/lib/libcairo.so.2(+0x4d8d9)[0x7f313a1528d9]
/usr/lib/libcairo.so.2(+0x4a191)[0x7f313a14f191]
/usr/lib/libcairo.so.2(+0x2282a)[0x7f313a12782a]
/usr/lib/libcairo.so.2(cairo_stroke_preserve+0x1b)[0x7f313a11e49b]
/usr/lib/libcairo.so.2(cairo_stroke+0x9)[0x7f313a11e4c9]
/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so(murrine_draw_focus+0x5e)[0x7f313480c15e]
/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so(+0xf724)[0x7f31347fc724]
/usr/lib/libgtk-x11-2.0.so.0(+0x240008)[0x7f313bccf008]
/usr/lib/libgtk-x11-2.0.so.0(+0x240115)[0x7f313bccf115]
/usr/lib/libgtk-x11-2.0.so.0(+0x13a9d8)[0x7f313bbc99d8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f31395aba6e]
/usr/lib/libgobject-2.0.so.0(+0x24120)[0x7f31395c1120]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x62b)[0x7f31395c27db]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f31395c2f53]
/usr/lib/libgtk-x11-2.0.so.0(+0x2536df)[0x7f313bce26df]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x556)[0x7f313bbc31b6]
/usr/lib/libgdk-x11-2.0.so.0(+0x439da)[0x7f313b2039da]
/usr/lib/libgdk-x11-2.0.so.0(+0x43987)[0x7f313b203987]
======= Memory map: ========
00400000-0041e000 r-xp 00000000 08:01 19973561                           /usr/bin/palimpsest
0061d000-0061e000 r--p 0001d000 08:01 19973561                           /usr/bin/palimpsest
0061e000-0061f000 rw-p 0001e000 08:01 19973561                           /usr/bin/palimpsest
0061f000-00620000 rw-p 00000000 00:00 0 
00e6c000-010e1000 rw-p 00000000 00:00 0                                  [heap]
7f312c000000-7f312c021000 rw-p 00000000 00:00 0 
7f312c021000-7f3130000000 ---p 00000000 00:00 0 
7f3130b79000-7f3130b8e000 r-xp 00000000 08:01 119508554                  /lib/libgcc_s.so.1
7f3130b8e000-7f3130d8d000 ---p 00015000 08:01 119508554                  /lib/libgcc_s.so.1
7f3130d8d000-7f3130d8e000 r--p 00014000 08:01 119508554                  /lib/libgcc_s.so.1
7f3130d8e000-7f3130d8f000 rw-p 00015000 08:01 119508554                  /lib/libgcc_s.so.1
7f3130d9e000-7f3130ee2000 r-xp 00000000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7f3130ee2000-7f31310e1000 ---p 00144000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7f31310e1000-7f31310e9000 r--p 00143000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7f31310e9000-7f31310eb000 rw-p 0014b000 08:01 19967931                   /usr/lib/libxml2.so.2.7.7
7f31310eb000-7f31310ec000 rw-p 00000000 00:00 0 
7f31310ec000-7f3131122000 r-xp 00000000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7f3131122000-7f3131321000 ---p 00036000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7f3131321000-7f3131322000 r--p 00035000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7f3131322000-7f3131325000 rw-p 00036000 08:01 19971158                   /usr/lib/libcroco-0.6.so.3.0.1
7f3131325000-7f3131358000 r-xp 00000000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7f3131358000-7f3131558000 ---p 00033000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7f3131558000-7f3131559000 r--p 00033000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7f3131559000-7f313155a000 rw-p 00034000 08:01 19971161                   /usr/lib/librsvg-2.so.2.32.0
7f313155a000-7f313155c000 r-xp 00000000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f313155c000-7f313175b000 ---p 00002000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f313175b000-7f313175c000 r--p 00001000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f313175c000-7f313175d000 rw-p 00002000 08:01 21547841                   /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f313175d000-7f313175f000 r-xp 00000000 08:01 119508844                  /lib/libutil-2.12.1.so
7f313175f000-7f313195e000 ---p 00002000 08:01 119508844                  /lib/libutil-2.12.1.so
7f313195e000-7f313195f000 r--p 00001000 08:01 119508844                  /lib/libutil-2.12.1.so
7f313195f000-7f3131960000 rw-p 00002000 08:01 119508844                  /lib/libutil-2.12.1.so
7f3131960000-7f3131976000 r-xp 00000000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7f3131976000-7f3131b76000 ---p 00016000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7f3131b76000-7f3131b77000 r--p 00016000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7f3131b77000-7f3131b78000 rw-p 00017000 08:01 19971378                   /usr/lib/libgvfscommon.so.0.0.0
7f3131b78000-7f3131ba0000 r-xp 00000000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7f3131ba0000-7f3131da0000 ---p 00028000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7f3131da0000-7f3131da1000 r--p 00028000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7f3131da1000-7f3131da2000 rw-p 00029000 08:01 19971382                   /usr/lib/gio/modules/libgvfsdbus.so
7f3131da2000-7f3131da4000 r-xp 00000000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f3131da4000-7f3131fa3000 ---p 00002000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f3131fa3000-7f3131fa4000 r--p 00001000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f3131fa4000-7f3131fa5000 rw-p 00002000 08:01 21547682                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f3131fa5000-7f3131fae000 r--s 00000000 08:01 87208984                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7f3131fae000-7f3131fb0000 r--s 00000000 08:01 87209616                   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3

```

---

### Post by dantetwc on 2010-11-28
Please Help. It is annoying that I can't use it normally:(

---

### Post by Yellow Pasque on 2010-11-28
Run memtest to rule out a bad RAM module.

---

### Post by Quackers on 2010-11-28
The first line of your printout reads
 *** glibc detected *** palimpsest: malloc(): memory corruption: 0x0000000001ea7280 ***

A Memtest sounds sensible to me :-)

---

