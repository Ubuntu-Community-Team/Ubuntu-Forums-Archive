---
title: "Segmentation Fault On All Gnome Applications"
date: 2010-09-16
forum: General Help
---

### Post by johnny111 on 2010-09-16
Hi everyone.

I am unable to successfully start either the XFCE or Gnome desktops, in Gnome the my wallpaper is displayed but that is all. This problem appeared yesterday night after my hard disk filled up, then all Gnome programs began to crash, also "df" failed to terminate. I was able to clear some space from the terminal (around 2 GB).

I was able to run an xterm so I attempted to load the components of Gnome manually from the terminal, to see which were problematic. I found that every application which uses Gnome fails to execute, producing a segmentation fault. A Java crash informed me that a "problematic frame" producing SIGSEGV was libgnomevfs-2.so.0.

I ran md5sum on all libraries matching the pattern /usr/lib/*gnome*, the checksums are identical to those on a working Ubuntu installation, so it is unlikely to be corruption of a library.

I have managed to determine that the problem is not in GLib or GTK+ as I wrote a simple (hello world) GTK+ application which executes without problem.

Furthermore (due to a lack of Gnome's network manager) I am without a network connection on the problematic computer.

Thank you all in advance for your help!

---

### Post by johnny111 on 2010-09-16
Hi again, I've managed to find some more information on the problem by doing stack backtraces in gdb.

Here are traces for three applications:

gnome-panel
```
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/gnome-panel...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/bin/gnome-panel 
[Thread debugging using libthread_db enabled]

Program received signal SIGSEGV, Segmentation fault.
0x00be6e30 in *__GI_strcmp (p1=0x7e8bc6ff <Address 0x7e8bc6ff out of bounds>, p2=0x81a9638 "gnome-panel.png") at strcmp.c:38
	in strcmp.c
(gdb) backtrace
#0  0x00be6e30 in *__GI_strcmp (p1=0x7e8bc6ff <Address 0x7e8bc6ff out of bounds>, p2=0x81a9638 "gnome-panel.png") at strcmp.c:38
#1  0x00833f7f in ?? () from /usr/lib/libgio-2.0.so.0
#2  0x008346f7 in ?? () from /usr/lib/libgio-2.0.so.0
#3  0x008331f4 in ?? () from /usr/lib/libgio-2.0.so.0
#4  0x007cf532 in g_content_type_guess () from /usr/lib/libgio-2.0.so.0
#5  0x00827071 in ?? () from /usr/lib/libgio-2.0.so.0
#6  0x00827d8b in ?? () from /usr/lib/libgio-2.0.so.0
#7  0x008232e8 in ?? () from /usr/lib/libgio-2.0.so.0
#8  0x007df4b8 in g_file_query_info () from /usr/lib/libgio-2.0.so.0
#9  0x0042eb75 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#10 0x0042f4a1 in gtk_icon_info_load_icon () from /usr/lib/libgtk-x11-2.0.so.0
#11 0x0043182a in gtk_icon_theme_load_icon () from /usr/lib/libgtk-x11-2.0.so.0
#12 0x005a4d66 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x005a534d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#14 0x005ae408 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#15 0x0809e7a8 in ?? ()
#16 0x00965dcc in g_cclosure_marshal_VOID__VOID () from /usr/lib/libgobject-2.0.so.0
#17 0x009568b9 in ?? () from /usr/lib/libgobject-2.0.so.0
#18 0x00958252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#19 0x0096c23a in ?? () from /usr/lib/libgobject-2.0.so.0
#20 0x0096ddb4 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#21 0x0096e256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#22 0x0059c43b in gtk_widget_realize () from /usr/lib/libgtk-x11-2.0.so.0
#23 0x005aecc5 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#24 0x00965dcc in g_cclosure_marshal_VOID__VOID () from /usr/lib/libgobject-2.0.so.0
#25 0x009568b9 in ?? () from /usr/lib/libgobject-2.0.so.0
#26 0x00958252 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#27 0x0096c23a in ?? () from /usr/lib/libgobject-2.0.so.0
#28 0x0096ddb4 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#29 0x0096e256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#30 0x0059d502 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#31 0x080aa3f6 in ?? ()
#32 0x080aa6f7 in panel_profile_load ()
#33 0x0806596e in main ()
(gdb) quit
A debugging session is active.

	Inferior 1 [process 16192] will be killed.

Quit anyway? (y or n) 
```

nautilus
```
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/nautilus...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/bin/nautilus 
[Thread debugging using libthread_db enabled]
[New Thread 0xb7e62b70 (LWP 16201)]

Program received signal SIGSEGV, Segmentation fault.
0x00d42e30 in *__GI_strcmp (p1=0x7e08a6ff <Address 0x7e08a6ff out of bounds>, p2=0x82ab6f8 "lpi-help.png") at strcmp.c:38
	in strcmp.c
(gdb) backtrace
#0  0x00d42e30 in *__GI_strcmp (p1=0x7e08a6ff <Address 0x7e08a6ff out of bounds>, p2=0x82ab6f8 "lpi-help.png") at strcmp.c:38
#1  0x006ebf7f in ?? () from /usr/lib/libgio-2.0.so.0
#2  0x006ec6f7 in ?? () from /usr/lib/libgio-2.0.so.0
#3  0x006eb1f4 in ?? () from /usr/lib/libgio-2.0.so.0
#4  0x00687532 in g_content_type_guess () from /usr/lib/libgio-2.0.so.0
#5  0x006df071 in ?? () from /usr/lib/libgio-2.0.so.0
#6  0x006dfd8b in ?? () from /usr/lib/libgio-2.0.so.0
#7  0x006db2e8 in ?? () from /usr/lib/libgio-2.0.so.0
#8  0x006974b8 in g_file_query_info () from /usr/lib/libgio-2.0.so.0
#9  0x002e6b75 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#10 0x002e74a1 in gtk_icon_info_load_icon () from /usr/lib/libgtk-x11-2.0.so.0
#11 0x002e982a in gtk_icon_theme_load_icon () from /usr/lib/libgtk-x11-2.0.so.0
#12 0x00195705 in launchpad_integration_add_item_factory () from /usr/lib/liblaunchpad-integration.so.1
#13 0x0019580c in ?? () from /usr/lib/liblaunchpad-integration.so.1
#14 0x00195abd in launchpad_integration_add_ui () from /usr/lib/liblaunchpad-integration.so.1
#15 0x080a5472 in ?? ()
#16 0x080acdbc in ?? ()
#17 0x0080b818 in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#18 0x007efa18 in ?? () from /usr/lib/libgobject-2.0.so.0
#19 0x080ac044 in ?? ()
#20 0x007f0c4c in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#21 0x007f190c in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#22 0x00455865 in gtk_widget_new () from /usr/lib/libgtk-x11-2.0.so.0
#23 0x08075fe3 in ?? ()
#24 0x0806deea in ?? ()
#25 0x0806ed0b in ?? ()
#26 0x08080dcf in ?? ()
#27 0x00ce5bc6 in __libc_start_main (main=0x8080700, argc=1, ubp_av=0xbffff5a4, init=0x81a9010, fini=0x81a9000, rtld_fini=0x11e0c0 <_dl_fini>, stack_end=0xbffff59c) at libc-start.c:226
#28 0x0806c6b1 in ?? ()
(gdb) quit
A debugging session is active.

	Inferior 1 [process 16198] will be killed.

Quit anyway? (y or n) 
```

rhythmbox
```
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/rhythmbox...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/bin/rhythmbox 
[Thread debugging using libthread_db enabled]

Program received signal SIGSEGV, Segmentation fault.
0x010a0e30 in *__GI_strcmp (p1=0xedf97332 <Address 0xedf97332 out of bounds>, p2=0x826cbc8 "playlist.png") at strcmp.c:38
	in strcmp.c
(gdb) backtrace
#0  0x010a0e30 in *__GI_strcmp (p1=0xedf97332 <Address 0xedf97332 out of bounds>, p2=0x826cbc8 "playlist.png") at strcmp.c:38
#1  0x009e1f7f in ?? () from /usr/lib/libgio-2.0.so.0
#2  0x009e26f7 in ?? () from /usr/lib/libgio-2.0.so.0
#3  0x009e11f4 in ?? () from /usr/lib/libgio-2.0.so.0
#4  0x0097d532 in g_content_type_guess () from /usr/lib/libgio-2.0.so.0
#5  0x009d5071 in ?? () from /usr/lib/libgio-2.0.so.0
#6  0x009d5d8b in ?? () from /usr/lib/libgio-2.0.so.0
#7  0x009d12e8 in ?? () from /usr/lib/libgio-2.0.so.0
#8  0x0098d4b8 in g_file_query_info () from /usr/lib/libgio-2.0.so.0
#9  0x003b6b75 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#10 0x003b74a1 in gtk_icon_info_load_icon () from /usr/lib/libgtk-x11-2.0.so.0
#11 0x003b982a in gtk_icon_theme_load_icon () from /usr/lib/libgtk-x11-2.0.so.0
#12 0x0019a4e1 in ?? () from /usr/lib/librhythmbox-core.so.0
#13 0x00cd8818 in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#14 0x00cbca18 in ?? () from /usr/lib/libgobject-2.0.so.0
#15 0x00cbdc4c in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#16 0x00cbe90c in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#17 0x00cbea27 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#18 0x0019a8d4 in rb_play_queue_source_new () from /usr/lib/librhythmbox-core.so.0
#19 0x00162bf9 in ?? () from /usr/lib/librhythmbox-core.so.0
#20 0x00cbde68 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#21 0x00cbe90c in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#22 0x00cbea27 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#23 0x0015eabc in rb_shell_new () from /usr/lib/librhythmbox-core.so.0
#24 0x0804b30e in main ()
(gdb) quit
A debugging session is active.

	Inferior 1 [process 16205] will be killed.

Quit anyway? (y or n) 
```

Clearly all traces have calls #0 to #11 in common. (With the exception of the strings "lpi-help.png" and "playlist.png".)

---

