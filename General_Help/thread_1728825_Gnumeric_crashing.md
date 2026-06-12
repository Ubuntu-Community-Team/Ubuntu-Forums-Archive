---
title: "Gnumeric crashing"
date: 2011-04-14
forum: General Help
---

### Post by garethfoxwilliams on 2011-04-14
Whenever I try to export a spreadsheet to Pdf. Gnumeric exits / crashes.
The Pdf is not saved, and any unsaved changes are also lost.
I have re-installed Gnumeric via Synaptic and the problem persists.

Is there anywhere I can find out what's going on?

Thanks

---

### Post by TeoBigusGeekus on 2011-04-14
Start gnumeric from terminal and post us any error messages you get when it crashes.

---

### Post by garethfoxwilliams on 2011-04-14
"segmentation fault"

That's all it said.

Thanks for your help - I hope that means something to you !!

---

### Post by TeoBigusGeekus on 2011-04-14
The only thing I can suggest is a reinstallation of cups-pdf
```
sudo apt-get install --reinstall cups-pdf
```
"Segmentation fault" is too general an error to be assessed.

---

### Post by garethfoxwilliams on 2011-04-14
Thanks.
Done that - restarted. Sadly it still crashes.

---

### Post by KegHead on 2011-04-14
Hi!

Try:

System..admin...synaptic package manager.

Remove Gnumeric and reinstall.

KegHead

---

### Post by garethfoxwilliams on 2011-04-14
That was the first thing I did. - "completely remove" then "install".

Ive done that to evince too.

I've still got the letter/number gibberish thing happening too ( see my other threads....)

---

### Post by KegHead on 2011-04-14
Hi!

What version are you running?

What version of linux?

KegHead

---

### Post by KegHead on 2011-04-14
Hmm,

Have you tried:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

KegHead

---

### Post by jbrefort on 2011-04-14
How do you export to pdf? Using the file print command or the file save command?

---

### Post by KegHead on 2011-04-14
Gnumeric manual;

[http://projects.gnome.org/gnumeric/doc/sect-printing.shtml](http://projects.gnome.org/gnumeric/doc/sect-printing.shtml)

KegHead

---

### Post by jbrefort on 2011-04-14
I mean, when the crash occurs, which command was used. There are two ways to generate a pdf file in gnumeric, as mentionned early.
One important question, too, which is the cairo version?

---

### Post by garethfoxwilliams on 2011-04-15
I'm running Xubuntu 10.10 upgraded to XFCE 4.8 with no problems.

The issues described were presen before the upgrade.

I export from Gnumeric using the Save As... dialogue and select PDF export from the dropdown box.

I don't know what the upgrade -f option means, I'm afraid.

Thanks for the interest.

---

### Post by garethfoxwilliams on 2011-04-15
Just tried the Print to PDF option and it crashed too.

---

### Post by TeoBigusGeekus on 2011-04-15
Does this happen with other apps as well?
Have you tried printing to pdf from gedit, geany, Open/Libreoffice writer, firefox even?

---

### Post by garethfoxwilliams on 2011-04-15
No problems with the same document opened with Libre Office.
No problems with gedit.

---

### Post by TeoBigusGeekus on 2011-04-15
So it's a gnumeric bug.
You could file a report.

---

### Post by jbrefort on 2011-04-15
Maverick has cairo-1.10.0 which had issues. Please test with at least cairo-1.10.2. Things work for me in debian sid (gnumeric git, cairo-1.10.2).

---

### Post by garethfoxwilliams on 2011-04-18
libcairo upgraded to 1.10.2

Problem persists.

Might it be that there is an image in the sheet? - I think it's a PNG, at least it wants to save it as that if I right click on it.

---

### Post by jbrefort on 2011-04-19
I have no more idea about what can cause the issue. Would it be possible for you to file a bug report at bugzilla.gnome.org and attache your file? Or just send me privately the file (jean doc brefort at normalesup dot org)?

I tested with a sheet with an embedded png image and things work for me.

---

### Post by philsalkie on 2011-04-25
I'm getting a similar crash on "Save As" - just posted to the Gnumeric mailing list about it.  Running Kubuntu Trinity Maverick, fully updated, and found that the "Save As" dialog doesn't have any options under the "Filter" dropdown - they all just say "Unknown", and any action once the "Save As" dialog has been opened results in a segfault.  I tried updating Gnumeric from the .debs in the Natty repo, now running 1.10.13, but still have the problem.

---

gnumeric

(gnumeric:17269): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(gnumeric:17269): Gdk-CRITICAL **: IA__gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed

(gnumeric:17269): Gdk-CRITICAL **: IA__gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed

(gnumeric:17269): Gdk-CRITICAL **: IA__gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed

(gnumeric:17269): Gdk-CRITICAL **: IA__gdk_window_get_user_data: assertion `GDK_IS_WINDOW (window)' failed

(gnumeric:17269): Gtk-CRITICAL **: IA__gtk_style_detach: assertion `style->attach_count > 0' failed

(gnumeric:17269): Gtk-CRITICAL **: IA__gtk_style_attach: assertion `window != NULL' failed

(gnumeric:17269): Gtk-CRITICAL **: _gtk_style_peek_property_value: assertion `GTK_IS_STYLE (style)' failed
Segmentation fault

---

Any suggestions for further debugging?  Thanks!

---

### Post by jbrefort on 2011-04-26
Those criticals should not happen. You might get a stack trace using gdb with the following command:

G_DEBUG="fatal_criticals" gdb gnumeric

This will make gnumeric crash on first critical. If you don't know about gdb usage, just ask.

---

### Post by philsalkie on 2011-04-26
Here's the backtrace:


-------------------


Starting program: /usr/bin/gnumeric
[Thread debugging using libthread_db enabled]
[New Thread 0xb7dd5b70 (LWP 26898)]
[New Thread 0xb68bfb70 (LWP 26904)]
[New Thread 0xb60beb70 (LWP 26905)]
[New Thread 0xb58bdb70 (LWP 26906)]
[Thread 0xb60beb70 (LWP 26905) exited]
[Thread 0xb58bdb70 (LWP 26906) exited]

Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion
`GDK_IS_WINDOW (window)' failed
aborting...

Program received signal SIGABRT, Aborted.
0x0012e416 in __kernel_vsyscall ()
(gdb) bt
#0  0x0012e416 in __kernel_vsyscall ()
#1  0x00aae941 in raise () from /lib/libc.so.6
#2  0x00ab1e42 in abort () from /lib/libc.so.6
#3  0x009e3536 in g_logv () from /lib/libglib-2.0.so.0
#4  0x009e3572 in g_log () from /lib/libglib-2.0.so.0
#5  0x009e379d in g_return_if_fail_warning ()
   from /lib/libglib-2.0.so.0
#6  0x008e115f in gdk_window_get_window_type ()
   from /usr/lib/libgdk-x11-2.0.so.0
#7  0x006027cc in gtk_grab_add () from /usr/lib/libgtk-x11-2.0.so.0
#8  0x0047e7ab in go_gtk_file_sel_dialog ()
   from /usr/lib/libgoffice-0.8.so.8
#9  0x001cf128 in gui_file_save_as ()
   from /usr/lib/libspreadsheet-1.10.13.so
#10 0x001cf52f in gui_file_save ()
   from /usr/lib/libspreadsheet-1.10.13.so
#11 0x0027655f in ?? () from /usr/lib/libspreadsheet-1.10.13.so
#12 0x0096ff2c in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#13 0x00960412 in g_closure_invoke () from
/usr/lib/libgobject-2.0.so.0
#14 0x00976b85 in ?? () from /usr/lib/libgobject-2.0.so.0
#15 0x00977fac in g_signal_emit_valist ()
   from /usr/lib/libgobject-2.0.so.0
#16 0x00978452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#17 0x00530325 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x0053242d in gtk_action_activate ()
   from /usr/lib/libgtk-x11-2.0.so.0
#19 0x006e57ce in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#20 0x0096ff2c in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#21 0x00960412 in g_closure_invoke () from
/usr/lib/libgobject-2.0.so.0#22 0x00976b85 in ?? () from /usr/lib/libgobject-2.0.so.0
#23 0x00977fac in g_signal_emit_valist ()
   from /usr/lib/libgobject-2.0.so.0
#24 0x00978452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#25 0x0054b2ca in gtk_button_clicked ()
   from /usr/lib/libgtk-x11-2.0.so.0
#26 0x0054c888 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#27 0x0096ff2c in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#28 0x0095ea87 in ?? () from /usr/lib/libgobject-2.0.so.0
#29 0x00960412 in g_closure_invoke () from
/usr/lib/libgobject-2.0.so.0
#30 0x0097642a in ?? () from /usr/lib/libgobject-2.0.so.0
#31 0x00977fac in g_signal_emit_valist ()
   from /usr/lib/libgobject-2.0.so.0
#32 0x00978452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#33 0x0054b36a in gtk_button_released ()
   from /usr/lib/libgtk-x11-2.0.so.0
#34 0x0054b3b3 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#35 0x00609284 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#36 0x0095ea87 in ?? () from /usr/lib/libgobject-2.0.so.0
#37 0x00960412 in g_closure_invoke () from
/usr/lib/libgobject-2.0.so.0
#38 0x009767d6 in ?? () from /usr/lib/libgobject-2.0.so.0
#39 0x00977e2b in g_signal_emit_valist ()
   from /usr/lib/libgobject-2.0.so.0
#40 0x00978452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#41 0x00737b96 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#42 0x0060185d in gtk_propagate_event ()
   from /usr/lib/libgtk-x11-2.0.so.0
#43 0x00602c17 in gtk_main_do_event ()
   from /usr/lib/libgtk-x11-2.0.so.0
#44 0x008fa36a in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#45 0x009d8855 in g_main_context_dispatch () from
/lib/libglib-2.0.so.0
#46 0x009dc668 in ?? () from /lib/libglib-2.0.so.0
#47 0x009dcba7 in g_main_loop_run () from /lib/libglib-2.0.so.0
#48 0x006031d9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#49 0x0804bc02 in main ()

------------------------


Interestingly, the "Save As" dialog box is different on the machine
that's having problems (makes me like having statically linked _everything_):

A working instance of Gnumeric on KDE3 has a "Save As" dialog box
which shows:

-----------------------------------------------------
Select a file (title bar)

Name:   Book1

Save in folder:  phil (greyed out)

Browse for other folders

< phil                                  Create Folder

Places          Name                            Modified




Add     Remove                                  Spreadsheets


File type:   Gnumeric XML (*.gnumeric)

                                        Cancel  Save

--------------------------------------------------

Yet the dialog box on the problem machine shows:

---------------------------------------------------------
Select a file (title bar)

Glyphs for Up, Back, Fwd, Reload, New Folder, and Wrench, address bar

Places on               List of files in the current directory
left with
no heading





        Location: Book 1                        Save

        Filter:   All Supported Files           Cancel


-----------------------------------------------------------


Is this maybe something to do with themes?  How else could the two dialog
boxes be so different on the same installation of the same OS (both Kubuntu Trinity Maverick Meerkat, both installed initially from the Ubuntu repos)?


(Attached two screenshots)

Thanks,

Phil

---

### Post by jbrefort on 2011-04-26
Strange Gtk+ version. Check it, there's something wrong with it. The bug is not in gnumeric or goffice code.

---

### Post by philsalkie on 2011-04-26
Got it working.  Did apt-get install --reinstall on everything gtk2 I could find, that didn't help.  Then did:


phil@eeep:/usr$ set | grep gtk
GTK2_RC_FILES=/home/phil/.gtkrc-2.0-kde-kde4:/home/phil/.kde3/share/config/gtkrc-2.0
GTK_MODULES=canberra-gtk-module
GTK_RC_FILES=/etc/gtk/gtkrc:/home/phil/.gtkrc:/home/phil/.kde3/share/config/gtkrc
LD_PRELOAD=/opt/kde3/lib/kgtk/libkgtk2.so:
phil@eeep:/usr$ export GTK_MODULES=
phil@eeep:/usr$ export LD_PRELOAD=
phil@eeep:/usr$ export GTK2_RC_FILES=
phil@eeep:/usr$ export GTK_RC_FILES=
phil@eeep:/usr$ set | grep gtk
phil@eeep:/usr$ gnumeric

and Gnumeric came up fine.

Narrowed it down to LD_PRELOAD - with some more digging, found a file:
/opt/kde3/share/kgtk/preload
which contains the single line:
/opt/kde3/lib/kgtk/libkgtk2.so

The systems with a working Gnumeric don't have that "preload" file.  So, I renamed it to "preload_hold", logged out, logged back in, and it's all good.  I'll send a note to the Trinity (Kubuntu KDE3 project) to see if they know what that preload's all about.

Thanks for the insight! (still don't know why Gimp works with libkgtk2 but Gnumeric doesn't, but maybe that's a different question...)

- Phil

---

