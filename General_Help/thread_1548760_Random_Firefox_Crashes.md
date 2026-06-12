---
title: "Random Firefox Crashes"
date: 2010-08-08
forum: General Help
---

### Post by Lucky75 on 2010-08-08
Hi!

I seem to be getting a lot of firefox crashes. I was actually able to reproduce it every time by typing "S02" into the search bar...not sure why. Here's the backtrace.

Edit: Odd, it also crashes when I enter s02 into my history search box...

```


[Thread debugging using libthread_db enabled]
[New Thread 0xb543eb70 (LWP 1524)]
[New Thread 0xb4affb70 (LWP 1525)]
[New Thread 0xb42feb70 (LWP 1526)]
[New Thread 0xb37ffb70 (LWP 1527)]
[New Thread 0xb2ffeb70 (LWP 1528)]
[New Thread 0xaf7f1b70 (LWP 1529)]
[Thread 0xaf7f1b70 (LWP 1529) exited]
[New Thread 0xaf7f1b70 (LWP 1530)]
[New Thread 0xaeff0b70 (LWP 1531)]
[New Thread 0xae7efb70 (LWP 1532)]
[New Thread 0xa9402b70 (LWP 1533)]
[New Thread 0xa8bf6b70 (LWP 1534)]
[New Thread 0xa81ffb70 (LWP 1535)]
[New Thread 0xa79feb70 (LWP 1536)]
[New Thread 0xa71fdb70 (LWP 1537)]
[New Thread 0xa51ffb70 (LWP 1539)]
[New Thread 0xa3bffb70 (LWP 1540)]
[New Thread 0xa2effb70 (LWP 1541)]
[Thread 0xa2effb70 (LWP 1541) exited]
[New Thread 0xa2effb70 (LWP 1542)]
[New Thread 0xa23ffb70 (LWP 1543)]
[New Thread 0xa19ffb70 (LWP 1544)]
[New Thread 0xa11feb70 (LWP 1545)]
[New Thread 0xa00ffb70 (LWP 1546)]
[New Thread 0x9f6ffb70 (LWP 1547)]
[Thread 0xa00ffb70 (LWP 1546) exited]
[New Thread 0x9ebffb70 (LWP 1548)]
[New Thread 0x9e3feb70 (LWP 1549)]
[Thread 0x9f6ffb70 (LWP 1547) exited]
[Thread 0x9ebffb70 (LWP 1548) exited]
[Thread 0x9e3feb70 (LWP 1549) exited]
[New Thread 0x9d5ffb70 (LWP 1550)]
[New Thread 0x9cdfeb70 (LWP 1551)]
[New Thread 0x9c5fdb70 (LWP 1552)]
[New Thread 0xa00ffb70 (LWP 1553)]
[Thread 0x9d5ffb70 (LWP 1550) exited]
[New Thread 0x9f6ffb70 (LWP 1554)]
[Thread 0x9cdfeb70 (LWP 1551) exited]
[New Thread 0x9ebffb70 (LWP 1555)]
[New Thread 0x9e3feb70 (LWP 1556)]
[New Thread 0x9bdfcb70 (LWP 1557)]
[Thread 0x9c5fdb70 (LWP 1552) exited]
[Thread 0xa00ffb70 (LWP 1553) exited]
[New Thread 0x9b5fbb70 (LWP 1558)]
[Thread 0x9f6ffb70 (LWP 1554) exited]
[Thread 0x9ebffb70 (LWP 1555) exited]
[New Thread 0x9adfab70 (LWP 1559)]
[Thread 0x9e3feb70 (LWP 1556) exited]
[New Thread 0x9a5f9b70 (LWP 1560)]
[New Thread 0x99df8b70 (LWP 1561)]
[New Thread 0x995f7b70 (LWP 1562)]
[Thread 0x9bdfcb70 (LWP 1557) exited]
[Thread 0x9b5fbb70 (LWP 1558) exited]
[Thread 0x9adfab70 (LWP 1559) exited]
[Thread 0x9a5f9b70 (LWP 1560) exited]
[Thread 0x99df8b70 (LWP 1561) exited]
[Thread 0x995f7b70 (LWP 1562) exited]
[New Thread 0x975ffb70 (LWP 1563)]
[New Thread 0x9d5ffb70 (LWP 1564)]
[Thread 0x975ffb70 (LWP 1563) exited]

Program received signal SIGSEGV, Segmentation fault.
0xb703ea6e in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
(gdb) bt
#0  0xb703ea6e in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#1  0xb7058829 in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#2  0xb705b3a6 in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#3  0xb6feac77 in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#4  0xb6ff4dce in js_Invoke () from /usr/lib/firefox-3.6.8/libmozjs.so
#5  0xb6fa630c in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#6  0xb6feac77 in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#7  0xb6ff6aaf in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#8  0xb6ff6cca in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#9  0xb6feac77 in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#10 0xb6ff4dce in js_Invoke () from /usr/lib/firefox-3.6.8/libmozjs.so
#11 0xb6ff5591 in ?? () from /usr/lib/firefox-3.6.8/libmozjs.so
#12 0xb6f98da0 in JS_CallFunctionValue ()
   from /usr/lib/firefox-3.6.8/libmozjs.so
#13 0xb76f716d in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#14 0xb771152d in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#15 0xb77118de in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#16 0xb7c20dda in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#17 0xb7c20e95 in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#18 0xb7c1e2a0 in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#19 0xb7becafb in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#20 0xb7c1e5d1 in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#21 0xb7c2aea7 in NS_InvokeByIndex_P () from /usr/lib/firefox-3.6.8/libxul.so
---Type <return> to continue, or q <return> to quit---
#22 0xb7c22b8d in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#23 0xb7c1e2a0 in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#24 0xb7becafb in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#25 0xb7b63491 in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#26 0xb7bbac86 in MessageLoop::RunInternal() ()
   from /usr/lib/firefox-3.6.8/libxul.so
#27 0xb7bbacaa in MessageLoop::RunHandler() ()
   from /usr/lib/firefox-3.6.8/libxul.so
#28 0xb7bbad21 in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#29 0xb7abceb8 in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#30 0xb797e39c in ?? () from /usr/lib/firefox-3.6.8/libxul.so
#31 0xb72c3986 in XRE_main () from /usr/lib/firefox-3.6.8/libxul.so
#32 0xb7ff59e3 in ?? ()
#33 0xb62dcbd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#34 0xb7ff5731 in ?? ()

```

I also get crashes randomly at other times (though I wasn't debugging it):

```


(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GtkWindow'

(<unknown>:18234): Gtk-CRITICAL **: gtk_window_get_type_hint: assertion `GTK_IS_WINDOW (window)' failed

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GtkWindow'

(<unknown>:18234): Gtk-CRITICAL **: gtk_window_get_decorated: assertion `GTK_IS_WINDOW (window)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GtkWidget'

(<unknown>:18234): Gtk-CRITICAL **: gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(<unknown>:18234): Gtk-CRITICAL **: gtk_window_get_type_hint: assertion `GTK_IS_WINDOW (window)' failed

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(<unknown>:18234): Gtk-CRITICAL **: gtk_window_get_decorated: assertion `GTK_IS_WINDOW (window)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWidget'

(<unknown>:18234): Gtk-CRITICAL **: gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(<unknown>:18234): Gtk-CRITICAL **: gtk_window_get_type_hint: assertion `GTK_IS_WINDOW (window)' failed

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(<unknown>:18234): Gtk-CRITICAL **: gtk_window_get_decorated: assertion `GTK_IS_WINDOW (window)' failed

(<unknown>:18234): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWidget'

(<unknown>:18234): Gtk-CRITICAL **: gtk_widget_get_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:18234): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
!!! [SmartNamer] updateEntry(): TypeError: /^https?:\/\/([^\/]+)/.exec(pageUrl) is null
Segmentation fault


```

Any suggestions? It's frustrating when firefox is this instable.

---

### Post by lovinglinux on 2010-08-08
First, [optimize Firefox databases]("http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html") then try typing again in the address bar to see if the problem persists.

If that doesn't help, then try to [start Firefox in safe mode and create a clean test profile]("http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html") to see if the problem persists. 

If the problem still occurs with safe mode and with a clean profile, then create a new Ubuntu test user, login with the new account and test it to see if the problem lies somewhere in your Gnome settings.

---

### Post by Lucky75 on 2010-08-14
hmm...problem only persists in my current profile.

I created a new profile and it was fine. Then I copied all my extensions over and it was still fine. 

I also vacuumed the databases for the one that was causing me problems, but it still crashes when I type it into the address bar. Could it be something to do with the history or something?

---

### Post by lovinglinux on 2010-08-15
> **Lucky75 said:**
> hmm...problem only persists in my current profile.

I created a new profile and it was fine. Then I copied all my extensions over and it was still fine. 

I also vacuumed the databases for the one that was causing me problems, but it still crashes when I type it into the address bar. Could it be something to do with the history or something?

Yes. Export your bookmarks using the bookmark manager then close Firefox and move the file **places.sqlite** from your profile. Start Firefox again and import the bookmarks exported previously.

---

