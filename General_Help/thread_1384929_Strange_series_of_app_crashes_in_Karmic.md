---
title: "Strange series of app crashes in Karmic"
date: 2010-01-19
forum: General Help
---

### Post by fishexe on 2010-01-19
In the last day or so I have had a series of programs crash when I clicked and dragged something.  The first one was freeciv.  After a couple hours of playing the problem arose; the program quit, and when I loaded the most recent autosave it died again the very first time I did a click-and-drag.  Turns out it was a SIGSEGV, so I tried running civclient-gtk in gdb and it gave me the following backtrace:

#0  0x080a1ad3 in ?? ()
#1  0x080ea372 in ?? ()
#2  0x080ea845 in ?? ()
#3  0x080eaf2a in ?? ()
#4  0x08063159 in ?? ()
#5  0x0806345c in ?? ()
#6  0x08114c60 in ?? ()
#7  0x080608f5 in ?? ()
#8  0x08114dd3 in ?? ()
#9  0x00a4c474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#10 0x003a2072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#11 0x003b77a8 in ?? () from /usr/lib/libgobject-2.0.so.0
#12 0x003b89b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#13 0x003b8fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#14 0x00b6895e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#15 0x00a44c20 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#16 0x00a45ea9 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#17 0x0016562a in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#18 0x0040de88 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#19 0x00411730 in ?? () from /lib/libglib-2.0.so.0
#20 0x00411b9f in g_main_loop_run () from /lib/libglib-2.0.so.0
#21 0x00a46419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#22 0x0810d184 in ?? ()
---Type <return> to continue, or q <return> to quit---
#23 0x08059764 in ?? ()
#24 0x0071ab56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#25 0x08054091 in ?? ()

I don't have any idea if this is useful or not, but I have also attached the offending autosave in hopes somebody can recreate the problem.  This one is particularly tricky because it seems to be affecting other programs, so I suspect it is one of my libs (possibly gtk?) rather than each separate program that has a problem.  Specifically, later in the day I was running gnometris, I used the pause button on my keyboard to pause the game, clicked and dragged on the menu bar, and the window disappeared.  This time I was unable to reproduce the error.  I don't remember what else may have crashed, but I think at least one other program was affected.  How do I go about diagnosing a problem like this?

---

### Post by fishexe on 2010-01-21
I've managed to reproduce the crash from gnometris...it occurs when I pause the game using my media pause key, then try to unpause it the same way (which doesn't work) and then click on the menu bar.  It may be I was jumping to conclusions about the two being related because most of the stack seems to be in different libs.  Here's my backtrace:

#0  0x00868003 in clutter_actor_get_parent ()
   from /usr/lib/libclutter-glx-1.0.so.0
#1  0x008901c0 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#2  0x008a33c8 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#3  0x0089144a in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#4  0x003d9e88 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#5  0x003dd730 in ?? () from /lib/libglib-2.0.so.0
#6  0x003ddb9f in g_main_loop_run () from /lib/libglib-2.0.so.0
#7  0x00d6d419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#8  0x08050cf3 in ?? ()
#9  0x0100db56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#10 0x08050a91 in ?? ()

I still don't know what to do with these bugs.  Should I report them as bugs in gnometris and civclient-gtk respectively, or as library bugs?  Does anyone know how I can fix something like this on my system?

---

