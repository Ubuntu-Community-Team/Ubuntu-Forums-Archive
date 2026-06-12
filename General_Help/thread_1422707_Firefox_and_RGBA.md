---
title: "Firefox and RGBA?"
date: 2010-03-05
forum: General Help
---

### Post by Da CalebMan on 2010-03-05
Hey Guys, I downloaded an [RGBA script with the murrine engine.]("http://www.omgubuntu.co.uk/2010/02/enable-rgba-window-transparency-in.html") It said there are programs that don't function with it. I noticed that Firefox (3.7) no longer works, due to some GTK error when run under a terminal. But it does run under root. I noticed that any application run under root is not transparent.

So How do I disable RGBA for firefox so I don't have to keep running it as root?

Please help! I have already tried the 'window-rules' method in CCSM.

---

### Post by Intrepid Ibex on 2010-03-05
So you didn't just use 'Ctrl + F' -> 'firefox' on that page :)?

```
In theory yes. the only applications it doesn't play ball with are OpenOffice, Firefox and a few others. it add these to the blacklist by default so you can still use them - albeit sans RGBA.
```
See /etc/profile.d/gtkrgba.sh

---

### Post by Da CalebMan on 2010-03-05
It's still not working. I tried changing the blacklist from firefox 3.5 to 3.7, but it still won't run...

here's the output of terminal:

```
dude@hp-desktop:~$ firefox-3.7

progname=firefox-3.7; RGBA=on

(firefox-3.7:2157): GLib-WARNING **: g_set_prgname() called multiple times

(firefox-3.7:2157): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_flat_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_resize_grip: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_extension: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_box_gap: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_shadow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_resize_grip: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(firefox-3.7:2157): Gtk-CRITICAL **: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed
###!!! ABORT: X_PolyFillRectangle: BadMatch (invalid parameter attributes); 263 requests ago: file /build/buildd/xulrunner-1.9.3-1.9.3~a3~hg20100304r38917+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 182
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x001EC510]
UNKNOWN [/usr/lib/libbonoboui-2.so.0 +0x00020C25]
_XError+0x00000109 [/usr/lib/libX11.so.6 +0x0003A839]
UNKNOWN [/usr/lib/libX11.so.6 +0x00040E9F]
_XEventsQueued+0x00000056 [/usr/lib/libX11.so.6 +0x000418C6]
XPending+0x00000068 [/usr/lib/libX11.so.6 +0x0002A588]
UNKNOWN [/usr/lib/libgdk-x11-2.0.so.0 +0x00052CC8]
g_main_context_prepare+0x000001B0 [/lib/libglib-2.0.so.0 +0x0003BF90]
UNKNOWN [/lib/libglib-2.0.so.0 +0x0003C351]
g_main_context_iteration+0x00000073 [/lib/libglib-2.0.so.0 +0x0003C863]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00A13F7C]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00A28DDC]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00A28F4D]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00B20A17]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00AEF28B]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00AAD201]
_ZN11MessageLoop11RunInternalEv+0x00000028 [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00B5BBBA]
_ZN11MessageLoop10RunHandlerEv+0x0000001A [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00B5BBDE]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00B5BC55]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x00A290B4]
UNKNOWN [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x008F0674]
XRE_main+0x00002C09 [/usr/lib/xulrunner-1.9.3a3pre/libxul.so +0x001E74DF]
UNKNOWN [/usr/lib/firefox-3.7a3pre/firefox-3.7 +0x000022FD]
__libc_start_main+0x000000E6 [/lib/tls/i686/cmov/libc.so.6 +0x00016B56]
Aborted
dude@hp-desktop:~$ 

```

Thanks!

---

### Post by Da CalebMan on 2010-03-05
Wait! It worked! Just had to reboot first.

THANKS SO MUCH!

---

