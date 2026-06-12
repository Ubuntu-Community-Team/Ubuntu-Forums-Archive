---
title: "Synaptic crashes when trying to re-install xterm"
date: 2010-10-15
forum: General Help
---

### Post by jondslater on 2010-10-15
I have installed Ubuntu as a 'headless' system.  When I try to run Synaptic (to re-install xterm), the application crashes.

I've tried running Synaptic from a terminal to see if I could capture error messages, and got:

 $ sudo synaptic
  Xlib:  extension "RANDR" missing on display ":8.0".
  *** glibc detected *** synaptic: free(): corrupted unsorted chunks: 0x0000000001ec51f0 *** ======= Backtrace: ========= /lib/libc.so.6(+0x774b6)[0x7f99009184b6]
  /lib/libc.so.6(cfree+0x73)[0x7f990091ec83]
  /usr/lib/libpixman-1.so.0(pixman_image_unref+0x96)[0x7f98fe99c176]
  /usr/lib/libpixman-1.so.0(pixman_image_fill_boxes+0x2aa)[0x7f98fe9b76aa]
  /usr/lib/libcairo.so.2(+0x27c68)[0x7f99039ffc68]
  /usr/lib/libcairo.so.2(+0x48848)[0x7f9903a20848]
  /usr/lib/libcairo.so.2(+0x4b885)[0x7f9903a23885]
  /usr/lib/libcairo.so.2(+0x48861)[0x7f9903a20861]
  /usr/lib/libcairo.so.2(+0x4cac7)[0x7f9903a24ac7]
  /usr/lib/libcairo.so.2(+0x4cc92)[0x7f9903a24c92]
  /usr/lib/libcairo.so.2(+0x4d8d9)[0x7f9903a258d9]
  /usr/lib/libcairo.so.2(+0x4a191)[0x7f9903a22191]
  /usr/lib/libcairo.so.2(+0x2282a)[0x7f99039fa82a]
  /usr/lib/libcairo.so.2(cairo_stroke_preserve+0x1b)[0x7f99039f149b]
  /usr/lib/libcairo.so.2(cairo_stroke+0x9)[0x7f99039f14c9]
  /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so(murrine_draw_focus+0x5e)[0x7f98fd09915e]
  /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so(+0xf724)[0x7f98fd089724]
  /usr/lib/libgtk-x11-2.0.so.0(+0x240008)[0x7f9905050008]
  /usr/lib/libgtk-x11-2.0.so.0(+0x240115)[0x7f9905050115]
  /usr/lib/libgtk-x11-2.0.so.0(+0x13a9d8)[0x7f9904f4a9d8]
  /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f9902e6fa6e]
  /usr/lib/libgobject-2.0.so.0(+0x24120)[0x7f9902e85120]
  /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x62b)[0x7f9902e867db]
  /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f9902e86f53]
  /usr/lib/libgtk-x11-2.0.so.0(+0x2536df)[0x7f99050636df]
  /usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x556)[0x7f9904f441b6]
  /usr/lib/libgdk-x11-2.0.so.0(+0x439da)[0x7f99048539da]
  /usr/lib/libgdk-x11-2.0.so.0(+0x43987)[0x7f9904853987]
  ======= Memory map: ========
  00400000-004b7000 r-xp 00000000 08:01 1718749                            /usr/sbin/synaptic
  006b7000-006b8000 r--p 000b7000 08:01 1718749                            /usr/sbin/synaptic
  006b8000-006bd000 rw-p 000b8000 08:01 1718749                            /usr/sbin/synaptic
  006bd000-006bf000 rw-p 00000000 00:00 0 
  00afa000-02111000 rw-p 00000000 00:00 0                                  [heap]
  7f98f4000000-7f98f4021000 rw-p 00000000 00:00 0 7f98f4021000-7f98f8000000 ---p 00000000 00:00 0 7f98f808f000-7f98f8284000 rw-p 00000000 00:00 0 
  7f98f8284000-7f98f9291000 r--s 00000000 08:01 393228                     /var/cache/apt/pkgcache.bin
  7f98f9291000-7f98f92de000 r--p 00000000 08:01 2494911                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
  7f98f92de000-7f98f92e4000 r-xp 00000000 08:01 2752968                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
  7f98f92e4000-7f98f94e3000 ---p 00006000 08:01 2752968                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
  7f98f94e3000-7f98f94e4000 r--p 00005000 08:01 2752968                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
  7f98f94e4000-7f98f94e5000 rw-p 00006000 08:01 2752968                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so
  7f98f94e5000-7f98f9525000 r-xp 00000000 08:01 1720996                    /usr/lib/libibus.so.2.0.0
  7f98f9525000-7f98f9725000 ---p 00040000 08:01 1720996                    /usr/lib/libibus.so.2.0.0
  7f98f9725000-7f98f9726000 r--p 00040000 08:01 1720996                    /usr/lib/libibus.so.2.0.0
  7f98f9726000-7f98f9727000 rw-p 00041000 08:01 1720996                    /usr/lib/libibus.so.2.0.0
  7f98f9727000-7f98f9728000 rw-p 00000000 00:00 0 
  7f98f9728000-7f98f9768000 r-xp 00000000 08:01 131078                     /lib/libdbus-1.so.3.5.2
  7f98f9768000-7f98f9968000 ---p 00040000 08:01 131078                     /lib/libdbus-1.so.3.5.2
  7f98f9968000-7f98f9969000 r--p 00040000 08:01 131078                     /lib/libdbus-1.so.3.5.2
  7f98f9969000-7f98f996a000 rw-p 00041000 08:01 131078                     /lib/libdbus-1.so.3.5.2
  7f98f9977000-7f98f997c000 r-xp 00000000 08:01 2100836                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
  7f98f997c000-7f98f9b7b000 ---p 00005000 08:01 2100836                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
  7f98f9b7b000-7f98f9b7c000 r--p 00004000 08:01 2100836                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
  7f98f9b7c000-7f98f9b7d000 rw-p 00005000 08:01 2100836                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
  7f98f9b7d000-7f98f9bcc000 r--p 00000000 08:01 2492340                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
  7f98f9bcc000-7f98f9c1a000 r--p 00000000 08:01 2494912                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
  7f98f9c1a000-7f98f9c1c000 r-xp 00000000 08:01 1970757                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
  7f98f9c1c000-7f98f9e1b000 ---p 00002000 08:01 1970757                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
  7f98f9e1b000-7f98f9e1c000 r--p 00001000 08:01 1970757                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
  7f98f9e1c000-7f98f9e1d000 rw-p 00002000 08:01 1970757                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
  7f98f9e1d000-7f98f9e1e000 r--s 00000000 08:01 395183                     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3
  7f98f9e1e000-7f98f9e27000 r--s 00000000 08:01 401003                     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
  7f98f9e27000-7f98f9e29000 r--s 00000000 08:01 400865                     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3
  7f98f9e29000-7f98f9e2c000 r--s 00000000 08:01 401000                     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le64.cache-3
  7f98f9e2c000-7f98f9e2f000 r--s 00000000 08:01 400999                     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le64.cache-3
  7f98f9e2f000-7f98f9e30000 r--s 00000000 08:01 400998                     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le64.cache-3
  7f98f9e30000-7f98f9e34000 r--s 00000000 08:01 400997                     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le64.cache-3
  7f98f9e34000-7f98f9e39000 r-xp 00000000 08:01 2752960                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
  7f98f9e39000-7f98fa038000 ---p 00005000 08:01 2752960                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
  7f98fa038000-7f98fa039000 r--p 00004000 08:01 2752960                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
  7f98fa039000-7f98fa03a000 rw-p 00005000 08:01 2752960                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
  7f98fa03a000-7f98fa070000 r-xp 00000000 08:01 1717612                    /usr/lib/libcroco-0.6.so.3.0.1
  7f98fa070000-7f98fa26f000 ---p 00036000 08:01 1717612                    /usr/lib/libcroco-0.6.so.3.0.1
  7f98fa26f000-7f98fa270000 r--p 00035000 08:01 1717612                    /usr/lib/libcroco-0.6.so.3.0.1
  7f98fa270000-7f98fa273000 rw-p 00036000 08:01 1717612                    /usr/lib/libcroco-0.6.so.3.0.1
  7f98fa273000-7f98fa2a6000 r-xp 00000000 08:01 1717615                    /usr/lib/librsvg-2.so.2.32.0
  7f98fa2a6000-7f98fa4a6000 ---p 00033000 08:01 1717615                    /usr/lib/librsvg-2.so.2.32.0
  7f98fa4a6000-7f98fa4a7000 r--p 00033000 08:01 1717615                    /usr/lib/librsvg-2.so.2.32.0
  7f98fa4a7000-7f98fa4a8000 rw-p 00034000 08:01 1717615                    /usr/lib/librsvg-2.so.2.32.0
  7f98fa4a8000-7f98fa4aa000 r-xp 00000000 08:01 2756319                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
  7f98fa4aa000-7f98fa6a9000 ---p 00002000 08:01 2756319                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
  7f98fa6a9000-7f98fa6aa000 r--p 00001000 08:01 2756319                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
  7f98fa6aa000-7f98fa6ab000 rw-p 00002000 08:01 2756319                    /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
  7f98fa6ab000-7f98faaf4000 r--p 00000000 08:01 2762221                    /usr/share/icons/hicolor/icon-theme.cache
  7f98faaf4000-7f98fcd9e000 r--p 00000000 08:01 2762222                    /usr/share/icons/gnome/icon-theme.cache
  7f98fcd9e000-7f98fce6f000 r--p 00000000 08:01 2762279                    /usr/share/icons/Humanity/icon-theme.cache
  7f98fce6f000-7f98fce78000 r-xp 00000000 08:01 2234780                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
  7f98fce78000-7f98fd078000 ---p 00009000 08:01 2234780                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
  7f98fd078000-7f98fd079000 r--p 00009000 08:01 2234780                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
  7f98fd079000-7f98fd07a000 rw-p 0000a000 08:01 2234780                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
  7f98fd07a000-7f98fd0a9000 r-xp 00000000 08:01 2234781                    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
  7f98fd0a9000-7f98fd2a9000 ---p 0002f000 08:01 2234781                    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
  7f98fd2a9000-7f98fd2aa000 r--p 0002f000 08:01 2234781                    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
  7f98fd2aa000-7f98fd2ab000 rw-p 00030000 08:01 2234781                    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
  7f98fd2ab000-7f98fd2b7000 r-xp 00000000 08:01 131109                     /lib/libnss_files-2.12.1.so
  7f98fd2b7000-7f98fd4b6000 ---p 0000c000 08:01 131109                     /lib/libnss_files-2.12.1.so
  7f98fd4b6000-7f98fd4b7000 r--p 0000b000 08:01 131109                     /lib/libnss_files-2.12.1.so
  7f98fd4b7000-7f98fd4b8000 rw-p 0000c000 08:01 131109                     /lib/libnss_files-2.12.1.so
  7f98fd4b8000-7f98fd4c2000 r-xp 00000000 08:01 131104                     /lib/libnss_nis-2.12.1.so
  7f98fd4c2000-7f98fd6c1000 ---p 0000a000 08:01 131104                     /lib/libnss_nis-2.12.1.so
  7f98fd6c1000-7f98fd6c2000 r--p 00009000 08:01 131104                     /lib/libnss_nis-2.12.1.so
  7f98fd6c2000-7f98fd6c3000 rw-p 0000a000 08:01 131104                     /lib/libnss_nis-2.12.1.so
  7f98fd6c3000-7f98fd6da000 r-xp 00000000 08:01 131108                     /lib/libnsl-2.12.1.so
  7f98fd6da000-7f98fd8d9000 ---p 00017000 08:01 131108                     /lib/libnsl-2.12.1.so
  7f98fd8d9000-7f98fd8da000 r--p 00016000 08:01 131108                     /lib/libnsl-2.12.1.so
  7f98fd8da000-7f98fd8db000 rw-p 00017000 08:01 131108                     /lib/libnsl-2.12.1.so
  7f98fd8db000-7f98fd8dd000 rw-p 00000000 00:00 0 
  7f98fd8dd000-7f98fd8e5000 r-xp 00000000 08:01 131106                     /lib/libnss_compat-2.12.1.so
  7f98fd8e5000-7f98fdae4000 ---p 00008000 08:01 131106                     /lib/libnss_compat-2.12.1.so
  7f98fdae4000-7f98fdae5000 r--p 00007000 08:01 131106                     /lib/libnss_compat-2.12.1.so
  7f98fdae5000-7f98fdae6000 rw-p 00008000 08:01 131106                     /lib/libnss_compat-2.12.1.so
  7f98fdae6000-7f98fdaeb000 r-xp 00000000 08:01 1713538                    /usr/lib/libXdmcp.so.6.0.0
  7f98fdaeb000-7f98fdcea000 ---p 00005000 08:01 1713538                    /usr/lib/libXdmcp.so.6.0.0
  7f98fdcea000-7f98fdceb000 r--p 00004000 08:01 1713538                    /usr/lib/libXdmcp.so.6.0.0
  7f98fdceb000-7f98fdcec000 rw-p 00005000 08:01 1713538                    /usr/lib/libXdmcp.so.6.0.0
  7f98fdcec000-7f98fdcee000 r-xp 00000000 08:01 1713536                    /usr/lib/libXau.so.6.0.0
  7f98fdcee000-7f98fdeed000 ---p 00002000 08:01 1713536                    /usr/lib/libXau.so.6.0.0
  7f98fdeed000-7f98fdeee000 r--p 00001000 08:01 1713536                    /usr/lib/libXau.so.6.0.0
  7f98fdeee000-7f98fdeef000 rw-p 00002000 08:01 1713536                    /usr/lib/libXau.so.6.0.0
  7f98fdeef000-7f98fdf2f000 r-xp 00000000 08:01 131156                     /lib/libncurses.so.5.7
  7f98fdf2f000-7f98fe12e000 ---p 00040000 08:01 131156                     /lib/libncurses.so.5.7
  7f98fe12e000-7f98fe132000 r--p 0003f000 08:01 131156                     /lib/libncurses.so.5.7
  7f98fe132000-7f98fe133000 rw-p 00043000 08:01 131156                     /lib/libncurses.so.5.7
  7f98fe133000-7f98fe159000 r-xp 00000000 08:01 131321                     /lib/libexpat.so.1.5.2
  7f98fe159000-7f98fe359000 ---p 00026000 08:01 131321                     /lib/libexpat.so.1.5.2
  7f98fe359000-7f98fe35b000 r--p 00026000 08:01 131321                     /lib/libexpat.so.1.5.2
  7f98fe35b000-7f98fe35c000 rw-p 00028000 08:01 131321                     /lib/libexpat.so.1.5.2
  7f98fe35c000-7f98fe377000 r-xp 00000000 08:01 1713540                    /usr/lib/libxcb.so.1.1.0
  7f98fe377000-7f98fe577000 ---p 0001b000 08:01 1713540                    /usr/lib/libxcb.so.1.1.0
  7f98fe577000-7f98fe578000 r--p 0001b000 08:01 1713540                    /usr/lib/libxcb.so.1.1.0
  7f98fe578000-7f98fe579000 rw-p 0001c000 08:01 1713540                    /usr/lib/libxcb.so.1.1.0
  7f98fe579000-7f98fe580000 r-xp 00000000 08:01 1713545                    /usr/lib/libxcb-render.so.0.0.0
  7f98fe580000-7f98fe780000 ---p 00007000 08:01 1713545                    /usr/lib/libxcb-render.so.0.0.0
  7f98fe780000-7f98fe781000 r--p 00007000 08:01 1713545                    /usr/lib/libxcb-render.so.0.0.0
  7f98fe781000-7f98fe782000 rw-p 00008000 08:01 1713545                    /usr/lib/libxcb-render.so.0.0.0Aborted

---

