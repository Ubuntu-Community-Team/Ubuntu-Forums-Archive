---
title: "easytag tag from txt file"
date: 2009-08-13
forum: General Help
---

### Post by tempo500 on 2009-08-13
hi, since the last two ubuntu versions it is not possible any more to tag ogg,mp3 etc with the "load filename from txt". it just crashes.... i bothered to compile it manually, but produces the same crash.... any help?

```
Configuration for easytag 2.1.6 :
--------------------------------

Source code location ....: .
Host System Type ........: x86_64-unknown-linux-gnu
Preprocessor ............: gcc
Compiler ................: gcc -g -O2 -Wall
Linker ..................: gcc -lwavpack -lm -lmp4v2 -lm -lz -lstdc++ -lid3 -lid3tag -lFLAC -lm -lm -lvorbisfile -lvorbis -logg -lm
GTK2 version ............: 2.16.1
MP3 file support ........: yes
ID3v2.3 tags support ....: yes (id3lib-3.8.3)
Ogg Vorbis file support .: yes
Speex file support ......: no
FLAC file support .......: yes (flac-1.2.1)
MP4 file support ........: yes (mpeg4ip-1.6)
WavPack support .........: yes
NLS/gettext .............: yes
Install path ............: /usr/local

```

```
easytag
*** glibc detected *** easytag: double free or corruption (out): 0x0000000001e93210 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fd0b3bdfcb8]
/lib/libc.so.6(cfree+0x76)[0x7fd0b3be2276]
easytag[0x446918]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x16d)[0x7fd0b611b27d]
/usr/lib/libgobject-2.0.so.0[0x7fd0b6130e3b]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7e2)[0x7fd0b6132432]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7fd0b6132953]
/usr/lib/libgtk-x11-2.0.so.0[0x7fd0b7afe7dd]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x16d)[0x7fd0b611b27d]
/usr/lib/libgobject-2.0.so.0[0x7fd0b6130723]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7e2)[0x7fd0b6132432]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7fd0b6132953]
/usr/lib/libgtk-x11-2.0.so.0[0x7fd0b7afd46d]
/usr/lib/libgtk-x11-2.0.so.0[0x7fd0b7ba8df8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x16d)[0x7fd0b611b27d]
/usr/lib/libgobject-2.0.so.0[0x7fd0b6130b1e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x66d)[0x7fd0b61322bd]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7fd0b6132953]
/usr/lib/libgtk-x11-2.0.so.0[0x7fd0b7cb109e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xe3)[0x7fd0b7ba1693]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2e3)[0x7fd0b7ba27b3]
/usr/lib/libgdk-x11-2.0.so.0[0x7fd0b781bf3c]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x24a)[0x7fd0b5c7f20a]
/usr/lib/libglib-2.0.so.0[0x7fd0b5c828e0]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1cd)[0x7fd0b5c82dad]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7fd0b7ba2bc7]
easytag[0x4382fa]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fd0b3b865a6]
easytag[0x4110a9]
======= Memory map: ========
00400000-0049c000 r-xp 00000000 08:02 416139                             /usr/local/bin/easytag
0069b000-0069c000 r--p 0009b000 08:02 416139                             /usr/local/bin/easytag
0069c000-006ab000 rw-p 0009c000 08:02 416139                             /usr/local/bin/easytag
006ab000-00742000 rw-p 006ab000 00:00 0 
01682000-01f4d000 rw-p 01682000 00:00 0                                  [heap]
7fd0a8000000-7fd0a8021000 rw-p 7fd0a8000000 00:00 0 
7fd0a8021000-7fd0ac000000 ---p 7fd0a8021000 00:00 0 
7fd0ac536000-7fd0ac54d000 r-xp 00000000 08:02 319301                     /usr/lib/libbeagle.so.1.0.2
7fd0ac54d000-7fd0ac74c000 ---p 00017000 08:02 319301                     /usr/lib/libbeagle.so.1.0.2
7fd0ac74c000-7fd0ac74d000 r--p 00016000 08:02 319301                     /usr/lib/libbeagle.so.1.0.2
7fd0ac74d000-7fd0ac74e000 rw-p 00017000 08:02 319301                     /usr/lib/libbeagle.so.1.0.2
7fd0ac74e000-7fd0ac76e000 r-xp 00000000 08:02 319388                     /usr/lib/libdbus-glib-1.so.2.1.0
7fd0ac76e000-7fd0ac96e000 ---p 00020000 08:02 319388                     /usr/lib/libdbus-glib-1.so.2.1.0
7fd0ac96e000-7fd0ac96f000 r--p 00020000 08:02 319388                     /usr/lib/libdbus-glib-1.so.2.1.0
7fd0ac96f000-7fd0ac970000 rw-p 00021000 08:02 319388                     /usr/lib/libdbus-glib-1.so.2.1.0
7fd0ac970000-7fd0ac97c000 r-xp 00000000 08:02 318543                     /usr/lib/libtrackerclient.so.0.0.0
7fd0ac97c000-7fd0acb7b000 ---p 0000c000 08:02 318543                     /usr/lib/libtrackerclient.so.0.0.0
7fd0acb7b000-7fd0acb7c000 r--p 0000b000 08:02 318543                     /usr/lib/libtrackerclient.so.0.0.0
7fd0acb7c000-7fd0acb7d000 rw-p 0000c000 08:02 318543                     /usr/lib/libtrackerclient.so.0.0.0
7fd0acb7d000-7fd0acc09000 r--p 00000000 08:02 457730                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7fd0acc09000-7fd0acc18000 r-xp 00000000 08:02 1132054                    /lib/libbz2.so.1.0.4
7fd0acc18000-7fd0ace18000 ---p 0000f000 08:02 1132054                    /lib/libbz2.so.1.0.4
7fd0ace18000-7fd0ace19000 r--p 0000f000 08:02 1132054                    /lib/libbz2.so.1.0.4
7fd0ace19000-7fd0ace1a000 rw-p 00010000 08:02 1132054                    /lib/libbz2.so.1.0.4
7fd0ace1a000-7fd0acf6d000 r-xp 00000000 08:02 318857                     /usr/lib/libxml2.so.2.6.32
7fd0acf6d000-7fd0ad16c000 ---p 00153000 08:02 318857                     /usr/lib/libxml2.so.2.6.32
7fd0ad16c000-7fd0ad174000 r--p 00152000 08:02 318857                     /usr/lib/libxml2.so.2.6.32
7fd0ad174000-7fd0ad176000 rw-p 0015a000 08:02 318857                     /usr/lib/libxml2.so.2.6.32
7fd0ad176000-7fd0ad177000 rw-p 7fd0ad176000 00:00 0 
7fd0ad177000-7fd0ad1ad000 r-xp 00000000 08:02 319362                     /usr/lib/libcroco-0.6.so.3.0.1
7fd0ad1ad000-7fd0ad3ac000 ---p 00036000 08:02 319362                     /usr/lib/libcroco-0.6.so.3.0.1
7fd0ad3ac000-7fd0ad3b0000 rw-p 00035000 08:02 319362                     /usr/lib/libcroco-0.6.so.3.0.1
7fd0ad3b0000-7fd0ad3ce000 r-xp 00000000 08:02 351478                     /usr/lib/gio/modules/libgvfsdbus.so
7fd0ad3ce000-7fd0ad5cd000 ---p 0001e000 08:02 351478                     /usr/lib/gio/modules/libgvfsdbus.so
7fd0ad5cd000-7fd0ad5ce000 r--p 0001d000 08:02 351478                     /usr/lib/gio/modules/libgvfsdbus.so
7fd0ad5ce000-7fd0ad5cf000 rw-p 0001e000 08:02 351478                     /usr/lib/gio/modules/libgvfsdbus.so
7fd0ad5d0000-7fd0ad61f000 r--p 00000000 08:02 457733                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
7fd0ad61f000-7fd0ad658000 r-xp 00000000 08:02 319639                     /usr/lib/libgsf-1.so.114.0.11
7fd0ad658000-7fd0ad858000 ---p 00039000 08:02 319639                     /usr/lib/libgsf-1.so.114.0.11
7fd0ad858000-7fd0ad85b000 r--p 00039000 08:02 319639                     /usr/lib/libgsf-1.so.114.0.11
7fd0ad85b000-7fd0ad85c000 rw-p 0003c000 08:02 319639                     /usr/lib/libgsf-1.so.114.0.11
7fd0ad85c000-7fd0ad85e000 rw-p 7fd0ad85c000 00:00 0 
7fd0ad85e000-7fd0ad893000 r-xp 00000000 08:02 320017                     /usr/lib/librsvg-2.so.2.26.0
7fd0ad893000-7fd0ada93000 ---p 00035000 08:02 320017                     /usr/lib/librsvg-2.so.2.26.0
7fd0ada93000-7fd0ada94000 r--p 00035000 08:02 320017                     /usr/lib/librsvg-2.so.2.26.0
7fd0ada94000-7fd0ada95000 rw-p 00036000 08:02 320017                     /usr/lib/librsvg-2.so.2.26.0
7fd0ada95000-7fd0ada97000 r-xp 00000000 08:02 350638                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7fd0ada97000-7fd0adc96000 ---p 00002000 08:02 350638                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7fd0adc96000-7fd0adc97000 r--p 00001000 08:02 350638                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7fd0adc97000-7fd0adc98000 rw-p 00002000 08:02 350638                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7fd0adc98000-7fd0adc9c000 r-xp 00000000 08:02 350851                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7fd0adc9c000-7fd0ade9c000 ---p 00004000 08:02 350851                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7fd0ade9c000-7fd0ade9d000 r--p 00004000 08:02 350851                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7fd0ade9d000-7fd0ade9e000 rw-p 00005000 08:02 350851                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7fd0ade9e000-7fd0adeda000 r-xp 00000000 08:02 1133068                    /lib/libdbus-1.so.3.4.0
7fd0adeda000-7fd0ae0d9000 ---p 0003c000 08:02 1133068                    /lib/libdbus-1.so.3.4.0
7fd0ae0d9000-7fd0ae0da000 r--p 0003b000 08:02 1133068                    /lib/libdbus-1.so.3.4.0
7fd0ae0da000-7fd0ae0db000 rw-p 0003c000 08:02 1133068                    /lib/libdbus-1.so.3.4.0
7fd0ae0db000-7fd0ae0f0000 r-xp 00000000 08:02 318958                     /usr/lib/libgvfscommon.so.0.0.0
7fd0ae0f0000-7fd0ae2f0000 ---p 00015000 08:02 318958                     /usr/lib/libgvfscommon.so.0.0.0
7fd0ae2f0000-7fd0ae2f1000 r--p 00015000 08:02 318958                     /usr/lib/libgvfscommon.so.0.0.0
7fd0ae2f1000-7fd0ae2f2000 rw-p 00016000 08:02 318958                     /usr/lib/libgvfscommon.so.0.0.0
7fd0ae2f2000-7fd0ae303000 r-xp 00000000 08:02 351477                     /usr/lib/gio/modules/libgioremote-volume-monitor.so
7fd0ae303000-7fd0ae502000 ---p 00011000 08:02 351477                     /usr/lib/gio/modules/libgioremote-volume-monitor.so
7fd0ae502000-7fd0ae503000 r--p 00010000 08:02 351477                     /usr/lib/gio/modules/libgioremote-volume-monitor.so
7fd0ae503000-7fd0ae504000 rw-p 00011000 08:02 351477                     /usr/lib/gio/modules/libgioremote-volume-monitor.so
7fd0ae504000-7fd0ae59c000 r--p 00000000 08:02 457731                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7fd0ae59c000-7fd0ae59e000 r-xp 00000000 08:02 358792                     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7fd0ae59e000-7fd0ae79d000 ---p 00002000 08:02 358792                     /usr/lib/pango/1.6.0/modules/pangAborted

```

---

### Post by P4man on 2009-08-13
seems to work for me, but I just installed it from the repo's, and unlike you, im on a 32 bit install..

---

### Post by tempo500 on 2009-08-13
i thought so too that this could be 64bit prob... i first installed it through the repros... just was curious if compiling fixes it.

---

### Post by bleedingpowers on 2009-08-28
I experienced the same crash. Try different files and text formats, but easytag 2.1.4 still crashes. Surprisingly, it doesn't crash when using Windows. Unfortunately. So I had to go that route just for using easytag with this renaming feature working properly.

---

### Post by meho_r on 2009-08-28
Same here, 64bit, crashes every time :( 

BTW, is there any other tag editor for linux with this feature?

---

### Post by bleedingpowers on 2009-08-29
This doesn't happen only in 64-bit processors, but also 32-bit ones, both Intel and AMD, so I don't believe this bug is related to the width of the CPU, but to other factor, like the Window manager or so...Just speculating (don't take this seriously), I haven't debug the program to jump to a direct conclusion. The weird thing is that this doesn't happen on a ugly Windows XP machine, why? and with a beta version of easytag...

---

### Post by meho_r on 2009-08-29
I just got mail from Jérôme, the author, and he is aware of this bug. Will be fixed in next, 2.1.7 version. However, he told me that there is a temporary fix for 2.1.6. All you have to do is change the line 3330 in file "misc.c". Change:
```
g_free(currentPath);
``` to this:
```
gtk_tree_path_free(currentPath);
```
and then compile. With this correction, Load filenames from .txt file feature works fine.

---

### Post by Emilie on 2010-05-07
Thanks a lot!  That change worked for me.  I wonder if there will ever be a new version, I hope so :)

I wonder if it is worth making a patch and submitting it to the Ubuntu bugzilla?

---

