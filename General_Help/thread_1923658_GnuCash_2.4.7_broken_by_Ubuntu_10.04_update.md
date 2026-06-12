---
title: "GnuCash 2.4.7 broken by Ubuntu 10.04 update"
date: 2012-02-11
forum: General Help
---

### Post by foxylady337 on 2012-02-11
I've been using GnuCash for more than a year, and had upgraded from the standard issue 2.2.9 to the GetDeb version 2.4.7 without trouble.

In the last ten days, GnuCash has been crashing when I Open the "Account Summary" Report and then close it.

I've uninstalled and reinstalled GnuCash without fixing this problem, and I've now built the most recent stable version (2.4.10) and it's still there.

The only recent change to my system has been through the routine system updates from Ubuntu.

My current copy of GnuCash 2.4.10 has been built with debugging information built in, and I have supplied a backtrace from gdb to the GnuCash team to isolate the fault.

Is there some way I can identify and reverse the change in 10.04 which has broken GnuCash?

---

### Post by winh8r on 2012-02-11
I would suggest running gnucash from the terminal and trying replicate the crash then copy and paste the output from the terminal here (obviously removing any sensitive personal information from the output first!)

A copy of the debug report might shed some light on it too.

---

### Post by foxylady337 on 2012-02-11
Here's the terminal output:

[FONT=Courier New]michael@Linley6:~/unstable/gnucash/bin$ gnucash
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

Found Finance::Quote version 1.17
Segmentation fault
michael@Linley6:~/unstable/gnucash/bin$ [/FONT]

Not very helpful, I fear!

I'll post the backtrace from gdb separately.

---

### Post by foxylady337 on 2012-02-11
[FONT=Courier New][FONT=Verdana]Here's the backtrace from gdb.[/FONT]

Program received signal SIGSEGV, Segmentation fault.
0x0105dee7 in g_datalist_id_set_data_full () from /lib/libglib-2.0.so.0
(gdb) bt
#0  0x0105dee7 in g_datalist_id_set_data_full () from /lib/libglib-2.0.so.0
#1  0x00fec017 in ?? () from /usr/lib/libgobject-2.0.so.0
#2  0x009c4461 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#3  0x00ad23c4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#4  0x00fec9ff in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
#5  0x009c415e in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#6  0x008d3b3d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#7  0x00a0356d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#8  0x0090c3f4 in gtk_container_foreach () from /usr/lib/libgtk-x11-2.0.so.0
#9  0x0090cc88 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#10 0x00a0529c in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#11 0x00ffa0cc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#12 0x00fe8487 in ?? () from /usr/lib/libgobject-2.0.so.0
#13 0x00fe9e1a in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#14 0x0100366c in ?? () from /usr/lib/libgobject-2.0.so.0
#15 0x01004e54 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#16 0x010055c2 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#17 0x009c4451 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x00ad23c4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#19 0x00fec9ff in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
#20 0x009c415e in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#21 0x012a7ee1 in gnc_html_dispose (obj=0x83e3688) at gnc-html.c:126
---Type <return> to continue, or q <return> to quit---
#22 0x012aebfa in gnc_html_gtkhtml_dispose (obj=0x83e3688)
    at gnc-html-gtkhtml.c:191
#23 0x00fec46b in g_object_unref () from /usr/lib/libgobject-2.0.so.0
#24 0x012a8d3f in gnc_html_destroy (self=0x83e3688) at gnc-html.c:441
#25 0x00140062 in gnc_plugin_page_report_destroy (priv=0x8677c90)
    at gnc-plugin-page-report.c:1006
#26 0x0013f119 in gnc_plugin_page_report_destroy_widget (plugin_page=0x8677c48)
    at gnc-plugin-page-report.c:706
#27 0x002466d1 in gnc_plugin_page_destroy_widget (plugin_page=0x8677c48)
    at gnc-plugin-page.c:186
#28 0x0023c648 in gnc_main_window_close_page (page=0x8677c48)
    at gnc-main-window.c:2734
#29 0x0023efda in gnc_main_window_cmd_file_close (action=0x814b9b0, 
    window=0x8145000) at gnc-main-window.c:3683
#30 0x00ffa0cc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#31 0x00fe9e1a in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#32 0x010037ed in ?? () from /usr/lib/libgobject-2.0.so.0
#33 0x01004e54 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#34 0x010055c2 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#35 0x008c4da5 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#36 0x008c6ead in gtk_action_activate () from /usr/lib/libgtk-x11-2.0.so.0
#37 0x00a7832e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#38 0x00ffa0cc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#39 0x00fe9e1a in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#40 0x010037ed in ?? () from /usr/lib/libgobject-2.0.so.0
#41 0x01004e54 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#42 0x010055c2 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#43 0x008dfc7a in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
#44 0x008e1238 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#45 0x00ffa0cc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#46 0x00fe8487 in ?? () from /usr/lib/libgobject-2.0.so.0
#47 0x00fe9e1a in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#48 0x0100308a in ?? () from /usr/lib/libgobject-2.0.so.0
#49 0x01004e54 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#50 0x010055c2 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#51 0x008dfd1a in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
#52 0x008dfd63 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#53 0x0099d434 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#54 0x00fe8487 in ?? () from /usr/lib/libgobject-2.0.so.0
#55 0x00fe9e1a in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#56 0x01003436 in ?? () from /usr/lib/libgobject-2.0.so.0
#57 0x01004cd3 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#58 0x010055c2 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#59 0x00aca646 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#60 0x00995a6d in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#61 0x00996e17 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#62 0x00c8b39a in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#63 0x01076b05 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#64 0x0107b0c8 in ?? () from /lib/libglib-2.0.so.0
#65 0x0107b607 in g_main_loop_run () from /lib/libglib-2.0.so.0
#66 0x009973d9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#67 0x00234520 in gnc_ui_start_event_loop () at gnc-gnome-utils.c:668
#68 0x0804d5b5 in inner_main (closure=0x0, argc=1, argv=0xbffff434)
    at gnucash-bin.c:735
#69 0x00481f46 in ?? () from /usr/lib/libguile.so.17
#70 0x00452e02 in ?? () from /usr/lib/libguile.so.17
#71 0x004c8c43 in scm_c_catch () from /usr/lib/libguile.so.17
#72 0x004533e2 in scm_i_with_continuation_barrier ()
   from /usr/lib/libguile.so.17
#73 0x004534c3 in scm_c_with_continuation_barrier ()
   from /usr/lib/libguile.so.17
#74 0x004c77b9 in scm_i_with_guile_and_parent () from /usr/lib/libguile.so.17
#75 0x004c78ae in scm_with_guile () from /usr/lib/libguile.so.17
#76 0x00481edf in scm_boot_guile () from /usr/lib/libguile.so.17
#77 0x0804d9b1 in main (argc=1, argv=0xbffff434) at gnucash-bin.c:879
(gdb) 
[/FONT]

---

### Post by winh8r on 2012-02-11
Hi,

I remembered seeing a post elsewhere recently regarding problems with starting and running gnucash, and managed to find the following info
> Stefan Kost 2012-01-02 16:07:31 UTC

According to gnucash developers gnucash does not support guile-2. I have
downgraded guile-2.0.2 to guile-1.8.8
([http://download.opensuse.org/repositories/multimedia:/apps/openSUSE_12.1](http://download.opensuse.org/repositories/multimedia:/apps/openSUSE_12.1)), but
neither gnucash-2.4.7 nor gnucash-2.4.8 (from dimstars repo) work. According to
the gnucash folks gnucash needs to be compiled against guile-1.8.8 to make it
work. Also according to the developers 
"""
2.4.x will not support guile-2, and trunk (2.5/2.6) may, but only if people can
figure out how to tell guile-2 how to load libraries from a non-standard
location.
"""

So, can we please downgrade guile back to 1.8.8 and push an upgrade of
recompiled packages?

[reply] [-] Comment 28 Stefan Kost 2012-01-02 19:32:25 UTC

I have rebuild the official gnucash package (2.4.7) against guile-1.8.8 and can
confirm that it works.


Which was lifted from here:

[https://bugzilla.novell.com/show_bug.cgi?id=724917]("https://bugzilla.novell.com/show_bug.cgi?id=724917")

Looks like they have been having quite a few concurrent issues recently but seem to be getting them resolved now.

Might be a good idea to get a source package from one of them and rebuild again and restructure the dependencies to get it running properly again.

I hope that this is of some help to you.

---

### Post by foxylady337 on 2012-02-11
This appears to have been a much more severe problem than mine, and in this case GnuCash was broken by a SuSE upgrade.

I've tried installing 2.4.7 from GetDeb on my laptop (which has Ubuntu 11.10 on it) and this combination works fine.

I've also built the unstable "trunk" version of GnuCash, which also fails to crash when I close the "Account Summary" Report, but I'm unwilling to use this version "live" because it is, well, unstable!

I was hoping to be able to unwind the update to Ubuntu 10.04 which had revealed the problem, and prevent this update from happening again until the next version of GnuCash appears.

If this isn't possible, I have found a way of working around the problem, and would rather work this way than experiment with alterations to the source code - on the "better the devil you know..." principle.

---

### Post by winh8r on 2012-02-11
I was looking more at the fact that there seemed to be a lot of issues with guile2 on open suse and wondered if you were still running libguile 1.8 on Ubuntu or if the update had upped it to 2.0 and given you the issue.

But i fully agree that it is better to do what you are doing and let them get it all ironed out before you go tramping around in the source which might already be a bit suspect in some areas where dependencies are concerned.

Good luck with it anyway!

---

### Post by foxylady337 on 2012-02-11
[FONT=Courier New]michael@Linley6:~$ guile -v
Guile 1.8.7[/FONT]

... so that's not the issue.

Just completing a (long-postponed) set of reconciliations, which has gone well, albeit with frequent Obsessional Saves!

It seems to be just the Reports that cause the problem, so as long as I don't close the reports without saving my work, and I can tolerate the warning about file-locking when I next open GnuCash, I think I'll be OK until the next release (of GnuCash).

It's tiresome of Canonical not to maintain the current versions of programs that are supported at the time LTS versions are released.

I think that the batch of programs supported with the release of any LTS version, should be supported at least until the next LTS version.

I'm not that enthusiastic about Unity as a GUI - perhaps I'm getting old? - although I realise that it's possible to revert to a more traditional desktop GUI in the later releases of Ubuntu.

---

### Post by winh8r on 2012-02-12
This thread might be useful for you in getting you back to a classic desktop in 11.10

[http://ubuntuforums.org/showthread.php?t=1859961]("http://ubuntuforums.org/showthread.php?t=1859961")


Personally, I have not enjoyed my encounter with 11.10, and thought for a while that maybe it was an age thing too! nice to know that i am not the only one who thinks that!

Hope they get GnuCash stabilised soon, but at least you know that you can still use it for now , even if it does not have full functionality.

---

