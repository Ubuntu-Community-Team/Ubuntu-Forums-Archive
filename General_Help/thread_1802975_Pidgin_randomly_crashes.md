---
title: "Pidgin randomly crashes"
date: 2011-07-12
forum: General Help
---

### Post by Drakmor on 2011-07-12
Hey, I've been using Pidgin for a while now, and it worked fine until today. I haven't installed anything new or messed around with anything, but now whenever I launch pidgin, it runs fine for about five minutes, then crashes. I ran it through the terminal and got this:

```
$ pidgin

(Pidgin:5165): GStreamer-CRITICAL **: gst_object_get_parent: assertion `GST_IS_OBJECT (object)' failed

(Pidgin:5165): GStreamer-CRITICAL **: gst_element_get_static_pad: assertion `GST_IS_ELEMENT (element)' failed

(Pidgin:5165): GStreamer-CRITICAL **: gst_object_get_parent: assertion `GST_IS_OBJECT (object)' failed

(Pidgin:5165): GStreamer-CRITICAL **: gst_element_get_static_pad: assertion `GST_IS_ELEMENT (element)' failed

(Pidgin:5165): GStreamer-CRITICAL **: gst_object_get_parent: assertion `GST_IS_OBJECT (object)' failed

(Pidgin:5165): GStreamer-CRITICAL **: gst_element_get_static_pad: assertion `GST_IS_ELEMENT (element)' failed
*** glibc detected *** pidgin: double free or corruption (!prev): 0x0a2c9788 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x7ae591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0x7afde8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x7b2ecd]
/usr/lib/libpulse.so.0(pa_xfree+0x35)[0x4604b35]
/usr/lib/libpulse.so.0(+0xcdb8)[0x45d9db8]
/usr/lib/libpulse.so.0(pa_context_connect+0x256)[0x45dcb56]
/usr/lib/gstreamer-0.10/libgstpulse.so(+0xab9b)[0x6765b9b]
/usr/lib/libgstaudio-0.10.so.0(gst_ring_buffer_open_device+0x1ee)[0x563697e]
/usr/lib/libgstaudio-0.10.so.0(+0x14f2e)[0x5640f2e]
/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35)[0x1cd435]
/usr/lib/libgstreamer-0.10.so.0(+0x3a928)[0x1d0928]
/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90)[0x1cc7f0]
/usr/lib/gstreamer-0.10/libgstautodetect.so(+0x24e9)[0x350a4e9]
/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35)[0x1cd435]
/usr/lib/libgstreamer-0.10.so.0(+0x3a928)[0x1d0928]
/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90)[0x1cc7f0]
/usr/lib/libgstreamer-0.10.so.0(+0x26827)[0x1bc827]
/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35)[0x1cd435]
/usr/lib/libgstreamer-0.10.so.0(+0x3a928)[0x1d0928]
/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90)[0x1cc7f0]
/usr/lib/gstreamer-0.10/libgstgconfelements.so(+0x49a3)[0x16419a3]
/usr/lib/gstreamer-0.10/libgstgconfelements.so(+0x1c27)[0x163ec27]
/usr/lib/gstreamer-0.10/libgstgconfelements.so(+0x1f7d)[0x163ef7d]
/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35)[0x1cd435]
/usr/lib/libgstreamer-0.10.so.0(+0x3a928)[0x1d0928]
/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90)[0x1cc7f0]
/usr/lib/libgstreamer-0.10.so.0(+0x26827)[0x1bc827]
/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35)[0x1cd435]
/usr/lib/libgstreamer-0.10.so.0(+0x3a928)[0x1d0928]
/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90)[0x1cc7f0]
/usr/lib/gstreamer-0.10/libgstplaybin.so(+0x9102)[0x1684102]
/usr/lib/gstreamer-0.10/libgstplaybin.so(+0x9d14)[0x1684d14]
/usr/lib/gstreamer-0.10/libgstplaybin.so(+0x203b4)[0x169b3b4]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c)[0x9a6dcc]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2)[0x999252]
/usr/lib/libgobject-2.0.so.0(+0x1f99d)[0x9ad99d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754)[0x9aedb4]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0x9af256]
/usr/lib/libgstreamer-0.10.so.0(gst_element_no_more_pads+0x8a)[0x1ced3a]
/usr/lib/gstreamer-0.10/libgstdecodebin.so(+0x675e)[0x5daf75e]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c)[0x9a6dcc]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2)[0x999252]
/usr/lib/libgobject-2.0.so.0(+0x1f99d)[0x9ad99d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754)[0x9aedb4]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0x9af256]
/usr/lib/libgstreamer-0.10.so.0(gst_element_no_more_pads+0x8a)[0x1ced3a]
/usr/lib/gstreamer-0.10/libgstwavparse.so(+0x7708)[0x3a19708]
/usr/lib/gstreamer-0.10/libgstwavparse.so(+0x7d1b)[0x3a19d1b]
/usr/lib/gstreamer-0.10/libgstwavparse.so(+0x8b34)[0x3a1ab34]
/usr/lib/libgstreamer-0.10.so.0(+0x7dd6b)[0x213d6b]
/usr/lib/libgstreamer-0.10.so.0(+0x7f377)[0x215377]
/lib/libglib-2.0.so.0(+0x67d0c)[0x573d0c]
/lib/libglib-2.0.so.0(+0x65def)[0x571def]
/lib/tls/i686/cmov/libpthread.so.0(+0x596e)[0x18296e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0x810a4e]
======= Memory map: ========
00110000-00129000 r-xp 00000000 08:02 3016381    /usr/lib/libatk-1.0.so.0.3009.1
00129000-0012a000 ---p 00019000 08:02 3016381    /usr/lib/libatk-1.0.so.0.3009.1
0012a000-0012b000 r--p 00019000 08:02 3016381    /usr/lib/libatk-1.0.so.0.3009.1
0012b000-0012c000 rw-p 0001a000 08:02 3016381    /usr/lib/libatk-1.0.so.0.3009.1
0012c000-00144000 r-xp 00000000 08:02 3016519    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00144000-00145000 r--p 00017000 08:02 3016519    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00145000-00146000 rw-p 00018000 08:02 3016519    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00146000-0014a000 r-xp 00000000 08:02 3016616    /usr/lib/libgthread-2.0.so.0.2400.1
0014a000-0014b000 r--p 00003000 08:02 3016616    /usr/lib/libgthread-2.0.so.0.2400.1
0014b000-0014c000 rw-p 00004000 08:02 3016616    /usr/lib/libgthread-2.0.so.0.2400.1
0014c000-00170000 r-xp 00000000 08:02 3277836    /lib/tls/i686/cmov/libm-2.11.1.so
00170000-00171000 r--p 00023000 08:02 3277836    /lib/tls/i686/cmov/libm-2.11.1.so
00171000-00172000 rw-p 00024000 08:02 3277836    /lib/tls/i686/cmov/libm-2.11.1.so
00172000-00174000 r-xp 00000000 08:02 3014921    /usr/lib/libxcb-aux.so.0.0.0
00174000-00175000 r--p 00001000 08:02 3014921    /usr/lib/libxcb-aux.so.0.0.0
00175000-00176000 rw-p 00002000 08:02 3014921    /usr/lib/libxcb-aux.so.0.0.0
00176000-00178000 r-xp 00000000 08:02 3014923    /usr/lib/libxcb-event.so.1.0.0
00178000-00179000 r--p 00001000 08:02 3014923    /usr/lib/libxcb-event.so.1.0.0
00179000-0017a000 rw-p 00002000 08:02 3014923    /usr/lib/libxcb-event.so.1.0.0
0017a000-0017b000 r-xp 00000000 08:02 3277563    /usr/lib/pidgin/gtkbuddynote.so
0017b000-0017c000 r--p 00000000 08:02 3277563    /usr/lib/pidgin/gtkbuddynote.so
0017c000-0017d000 rw-p 00001000 08:02 3277563    /usr/lib/pidgin/gtkbuddynote.so
0017d000-00192000 r-xp 00000000 08:02 3277854    /lib/tls/i686/cmov/libpthread-2.11.1.so
00192000-00193000 r--p 00014000 08:02 3277854    /lib/tls/i686/cmov/libpthread-2.11.1.so
00193000-00194000 rw-p 00015000 08:02 3277854    /lib/tls/i686/cmov/libpthread-2.11.1.so
00194000-00196000 rw-p 00000000 00:00 0 
00196000-00252000 r-xp 00000000 08:02 3016602    /usr/lib/libgstreamer-0.10.so.0.24.1
00252000-00255000 r--p 000bb000 08:02 3016602    /usr/lib/libgstreamer-0.10.so.0.24.1
00255000-00256000 rw-p 000be000 08:02 3016602    /usr/lib/libgstreamer-0.10.so.0.24.1
00256000-00257000 rw-p 00000000 00:00 0 
00257000-002ea000 r-xp 00000000 08:02 3016517    /usr/lib/libgdk-x11-2.0.so.0.2000.1
002ea000-002ec000 r--p 00093000 08:02 3016517    /usr/lib/libgdk-x11-2.0.so.0.2000.1
002ec000-002ed000 rw-p 00095000 08:02 3016517    /usr/lib/libgdk-x11-2.0.so.0.2000.1
002ed000-0032d000 r-xp 00000000 08:02 3018878    /usr/lib/libpango-1.0.so.0.2800.0
0032d000-0032e000 ---p 00040000 08:02 3018878    /usr/lib/libpango-1.0.so.0.2800.0
0032e000-0032f000 r--p 00040000 08:02 3018878    /usr/lib/libpango-1.0.so.0.2800.0
0032f000-00330000 rw-p 00041000 08:02 3018878    /usr/lib/libpango-1.0.so.0.2800.0
00330000-00348000 r-xp 00000000 08:02 3017329    /usr/lib/libxcb.so.1.1.0
00348000-00349000 r--p 00017000 08:02 3017329    /usr/lib/libxcb.so.1.1.0
00349000-0034a000 rw-p 00018000 08:02 3017329    /usr/lib/libxcb.so.1.1.0
0034a000-003e4000 r-xp 00000000 08:02 3016526    /usr/lib/libgio-2.0.so.0.2400.1
003e4000-003e5000 ---p 0009a000 08:02 3016526    /usr/lib/libgio-2.0.so.0.2400.1
003e5000-003e6000 r--p 0009a000 08:02 3016526    /usr/lib/libgio-2.0.so.0.2400.1
003e6000-003e7000 rw-p 0009b000 08:02 3016526    /usr/lib/libgio-2.0.so.0.2400.1
003e7000-003e8000 rw-p 00000000 00:00 0 
003e8000-003eb000 r-xp 00000000 08:02 3014815    /usr/lib/libxcb-atom.so.1.0.0
003eb000-003ec000 r--p 00002000 08:02 3014815    /usr/lib/libxcb-atom.so.1.0.0Aborted

```
Nothing seems to visibly trigger this- this just occurs when Pidgin is sitting idle.
I'm not very good at interpreting this, but if its a memoy issue, the only thing I can think of is that I'm running a game that takes up about 70-80% of my RAM. It worked before though while running the game, so I'm not sure.

Pidgin/libpurple version 2.6.6, I already checked for updates. I'm running kubuntu 10.04 LTS.  Let me know if you need any more details! Thanks!

---

