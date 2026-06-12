---
title: "Thunderbird GTK errors causing crashes"
date: 2011-07-30
forum: General Help
---

### Post by whiterabbit7500 on 2011-07-30
I have been running Thunderbird for a few days now on a new Ubuntu 11 box, with no errors. Today I went to start it up, and it crashed right away upon hitting the launcher. I ran from terminal and received the following:

```

david@dm_home:~$ thunderbird

progname=thunderbird-bin; RGBA=on

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_vline: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_handle: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_resize_grip: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_extension: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box_gap: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_check: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_slider: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_check: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_vline: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_resize_grip: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_extension: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box_gap: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_slider: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(thunderbird-bin:3856): Gtk-CRITICAL **: IA__gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed
###!!! ABORT: X_PolyFillRectangle: BadMatch (invalid parameter attributes); 322 requests ago: file nsX11ErrorHandler.cpp, line 182
_XError+0x0000012F [/usr/lib/x86_64-linux-gnu/libX11.so.6 +0x00042D3F]
UNKNOWN [/usr/lib/x86_64-linux-gnu/libX11.so.6 +0x0003FFB1]
UNKNOWN [/usr/lib/x86_64-linux-gnu/libX11.so.6 +0x0003FFF5]
_XReply+0x00000200 [/usr/lib/x86_64-linux-gnu/libX11.so.6 +0x000409A0]
XTranslateCoordinates+0x0000009D [/usr/lib/x86_64-linux-gnu/libX11.so.6 +0x0003DB3D]
UNKNOWN [/usr/lib/libgdk-x11-2.0.so.0 +0x0006B9DD]
gdk_window_get_origin+0x000000CF [/usr/lib/libgdk-x11-2.0.so.0 +0x00041ECF]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0020B1B9]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0056EB64]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0056FF79]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x00328AA6]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x003A0A9D]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x003AD846]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x003AD994]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x003ADF29]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x00259D6E]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0025A036]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0025AF92]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x00406D00]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x00407FA1]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x004046A8]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0020A801]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0020F213]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0020F29D]
UNKNOWN [/usr/lib/libgtk-x11-2.0.so.0 +0x00138578]
g_closure_invoke+0x0000015C [/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 +0x0000E81C]
UNKNOWN [/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 +0x00020019]
g_signal_emit_valist+0x000005A9 [/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 +0x00028FA9]
g_signal_emit+0x0000007F [/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 +0x0002941F]
UNKNOWN [/usr/lib/libgtk-x11-2.0.so.0 +0x002544D1]
gtk_propagate_event+0x000000C3 [/usr/lib/libgtk-x11-2.0.so.0 +0x00136763]
gtk_main_do_event+0x0000021B [/usr/lib/libgtk-x11-2.0.so.0 +0x00136A5B]
UNKNOWN [/usr/lib/libgdk-x11-2.0.so.0 +0x0005C5CC]
g_main_context_dispatch+0x000001DD [/lib/x86_64-linux-gnu/libglib-2.0.so.0 +0x00042BCD]
UNKNOWN [/lib/x86_64-linux-gnu/libglib-2.0.so.0 +0x000433A8]
g_main_context_iteration+0x00000069 [/lib/x86_64-linux-gnu/libglib-2.0.so.0 +0x00043639]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x001FADDB]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x001FAED3]
UNKNOWN [/usr/lib/thunderbird-3.1.11/libxpcom_core.so +0x00064742]
_Z21NS_ProcessNextEvent_PP9nsIThreadi+0x0000002B [/usr/lib/thunderbird-3.1.11/libxpcom_core.so +0x00038D7F]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x001FAC21]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0074D396]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x00047567]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x0004260E]
__libc_start_main+0x000000FF [/lib/x86_64-linux-gnu/libc.so.6 +0x0001EEFF]
UNKNOWN [/usr/lib/thunderbird-3.1.11/thunderbird-bin +0x00042409]

progname=crashreporter; RGBA=on

```

Obviously, the problem lies in GTK somewhere, which I think may have been messed up by a GTK theme I tried installing yesterday and it failed. How can I reset GTK to defaults, to enable thunderbird to run?

---

