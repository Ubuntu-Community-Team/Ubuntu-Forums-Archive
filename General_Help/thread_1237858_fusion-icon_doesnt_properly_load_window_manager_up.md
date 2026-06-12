---
title: "fusion-icon doesnt properly load window manager upon startup"
date: 2009-08-11
forum: General Help
---

### Post by Zeroangel on 2009-08-11
Hi All,

I'm using an app called fusion-icon so that I can better control my Window Managers, and have it set to start up with GNOME.

The problem is that when it starts up, my default WM is Metacity instead of Compiz, when I want it to start with Compiz as the default. This is unusual since it worked fine when I was on Gutsy. Anyways I tried running it via the console and this is the output.

```
david@icarus ~ $ sleep 5 && fusion-icon
 * Detected Session: gnome             
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface                               
 * Starting Compiz                                       
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp --loose-binding
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format          
compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png      
*** glibc detected *** compiz.real: corrupted double-linked list: 0x09c06490 ***             
======= Backtrace: =========                                                                                                                                                        
/lib/tls/i686/cmov/libc.so.6[0xb7b99604]                                                                                                                                            
/lib/tls/i686/cmov/libc.so.6[0xb7b9b383]                                                                                                                                            
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7b9b5b6]                                                                                                                                
/usr/lib/libGL.so.1[0xb7d173e1]                                                                                                                                                     
======= Memory map: ========                                                                                                                                                        
08048000-0807c000 r-xp 00000000 08:05 29126      /usr/bin/compiz.real                                                                                                               
0807c000-0807d000 r--p 00033000 08:05 29126      /usr/bin/compiz.real                                                                                                               
0807d000-0807e000 rw-p 00034000 08:05 29126      /usr/bin/compiz.real                                                                                                               
099b3000-0aa28000 rw-p 099b3000 00:00 0          [heap]                                                                                                                             
b4aa4000-b4b24000 rw-s 355db000 00:0f 8067       /dev/nvidia0                                                                                                                       
b5054000-b505b000 r--s 00000000 08:05 12341      /usr/lib/gconv/gconv-modules.cache                                                                                                 
b505b000-b509a000 r--p 00000000 08:05 16766      /usr/lib/locale/en_CA.utf8/LC_CTYPE                                                                                                
b6144000-b614e000 r-xp 00000000 08:05 6259       /lib/tls/i686/cmov/libnss_files-2.9.so                                                                                             
b614e000-b614f000 r--p 00009000 08:05 6259       /lib/tls/i686/cmov/libnss_files-2.9.so                                                                                             
b614f000-b6150000 rw-p 0000a000 08:05 6259       /lib/tls/i686/cmov/libnss_files-2.9.so                                                                                             
b6150000-b6159000 r-xp 00000000 08:05 6263       /lib/tls/i686/cmov/libnss_nis-2.9.so                                                                                               
b6159000-b615a000 r--p 00008000 08:05 6263       /lib/tls/i686/cmov/libnss_nis-2.9.so                                                                                               
b615a000-b615b000 rw-p 00009000 08:05 6263       /lib/tls/i686/cmov/libnss_nis-2.9.so                                                                                               
b615b000-b6170000 r-xp 00000000 08:05 6253       /lib/tls/i686/cmov/libnsl-2.9.so                                                                                                   
b6170000-b6171000 r--p 00014000 08:05 6253       /lib/tls/i686/cmov/libnsl-2.9.so                                                                                                   
b6171000-b6172000 rw-p 00015000 08:05 6253       /lib/tls/i686/cmov/libnsl-2.9.so                                                                                                   
b6172000-b6174000 rw-p b6172000 00:00 0
b6174000-b617b000 r-xp 00000000 08:05 6255       /lib/tls/i686/cmov/libnss_compat-2.9.so
b617b000-b617c000 r--p 00006000 08:05 6255       /lib/tls/i686/cmov/libnss_compat-2.9.so
b617c000-b617d000 rw-p 00007000 08:05 6255       /lib/tls/i686/cmov/libnss_compat-2.9.so
b617d000-b61ad000 r-xp 00000000 08:05 2714       /lib/libpcre.so.3.12.1
b61ad000-b61ae000 r--p 0002f000 08:05 2714       /lib/libpcre.so.3.12.1
b61ae000-b61af000 rw-p 00030000 08:05 2714       /lib/libpcre.so.3.12.1
b61af000-b61eb000 r-xp 00000000 08:05 10030      /usr/lib/libgobject-2.0.so.0.2000.1
b61eb000-b61ec000 r--p 0003b000 08:05 10030      /usr/lib/libgobject-2.0.so.0.2000.1
b61ec000-b61ed000 rw-p 0003c000 08:05 10030      /usr/lib/libgobject-2.0.so.0.2000.1
b61ed000-b6223000 r-xp 00000000 08:05 169570     /lib/libdbus-1.so.3.4.0
b6223000-b6224000 r--p 00035000 08:05 169570     /lib/libdbus-1.so.3.4.0
b6224000-b6225000 rw-p 00036000 08:05 169570     /lib/libdbus-1.so.3.4.0
b6225000-b6241000 r-xp 00000000 08:05 9764       /usr/lib/libdbus-glib-1.so.2.1.0
b6241000-b6242000 r--p 0001b000 08:05 9764       /usr/lib/libdbus-glib-1.so.2.1.0
b6242000-b6243000 rw-p 0001c000 08:05 9764       /usr/lib/libdbus-glib-1.so.2.1.0
b6243000-b624a000 r-xp 00000000 08:05 6272       /lib/tls/i686/cmov/librt-2.9.so
b624a000-b624b000 r--p 00006000 08:05 6272       /lib/tls/i686/cmov/librt-2.9.so
b624b000-b624c000 rw-p 00007000 08:05 6272       /lib/tls/i686/cmov/librt-2.9.so
b624c000-b6295000 r-xp 00000000 08:05 9538       /usr/lib/libORBit-2.so.0.1.0
b6295000-b629d000 r--p 00049000 08:05 9538       /usr/lib/libORBit-2.so.0.1.0
b629d000-b629f000 rw-p 00051000 08:05 9538       /usr/lib/libORBit-2.so.0.1.0
b629f000-b6355000 r-xp 00000000 08:05 9970       /usr/lib/libglib-2.0.so.0.2000.1
b6355000-b6356000 r--p 000b5000 08:05 9970       /usr/lib/libglib-2.0.so.0.2000.1
b6356000-b6357000 rw-p 000b6000 08:05 9970       /usr/lib/libglib-2.0.so.0.2000.1
b6357000-b6385000 r-xp 00000000 08:05 9902       /usr/lib/libgconf-2.so.4.1.5
b6385000-b6386000 ---p 0002e000 08:05 9902       /usr/lib/libgconf-2.so.4.1.5
b6386000-b6387000 r--p 0002e000 08:05 9902       /usr/lib/libgconf-2.so.4.1.5
b6387000-b6389000 rw-p 0002f000 08:05 9902       /usr/lib/libgconf-2.so.4.1.5
b63a0000-b63ad000 r-xp 00000000 08:05 2663       /lib/libgcc_s.so.1
b63ad000-b63ae000 r--p 0000c000 08:05 2663       /lib/libgcc_s.so.1
b63ae000-b63af000 rw-p 0000d000 08:05 2663       /lib/libgcc_s.so.1
b63af000-b6493000 r-xp 00000000 08:05 10584      /usr/lib/libstdc++.so.6.0.10
b6493000-b6497000 r--p 000e3000 08:05 10584      /usr/lib/libstdc++.so.6.0.10
b6497000-b6498000 rw-p 000e7000 08:05 10584      /usr/lib/libstdc++.so.6.0.10 * Setting window manager to Compiz
Terminated
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp --loose-binding
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png"
```Anyone have any ideas about what I can do to fix this problem?

I am using a GeForce 8600GT, restricted drivers, Compiz->Loose Bindings On

---

