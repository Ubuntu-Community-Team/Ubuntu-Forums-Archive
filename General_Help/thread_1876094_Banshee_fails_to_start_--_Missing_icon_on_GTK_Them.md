---
title: "Banshee fails to start -- Missing icon on GTK Theme"
date: 2011-11-05
forum: General Help
---

### Post by Kentucky88 on 2011-11-05
I am running Ubuntu 11.10 and I installed the kde-desktop plasma windows manager.  I like KDE better and I'd like to keep it as my desktop manager, but some programs simply no longer work.  Banshee runs fine under GNOME, but not under KDE.  The reason has something to do with either the Desktop or Application theme.  I found a work-around which involves changing back to the default KDE theme.  However, I don't want to do this every time I want to start some applications.  What's the long-term fix for the error message below that will allow me to use other GTK themes?

[PHP]
System-Product-Name:~$ banshee
[Info  13:26:13.541] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, x86_64) @ 2011-09-23 04:47:58 UTC]
[Warn  13:26:14.429] Caught an exception - GLib.GException: Icon 'process-working' not present in theme (in `gtk-sharp')
  at Gtk.IconTheme.LoadIcon (System.String icon_name, Int32 size, IconLookupFlags flags) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.Widgets.TaskStatusIcon..ctor () [0x00000] in <filename unknown>:0 
The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 556 error_code 10 request_code 152 minor_code 1)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/PHP]

Update: The work around is to go under GTK+ Appearance and change GTK+ Styles from oxygen-gtk to Raleigh, then open Banshee, then change back to oxygen-gtk.  From the error description above, I think the problem is that something is missing the bouncing progress ball icon that pops up when the application is loading.  So instead of simply displaying a generic icon, the application crashes.  Nice.

---

### Post by SPARTAN-118 on 2011-11-06
Hold on, I have this exact problem, and Banshee successfully starts when the GTK+ Appearance is set to Raleigh. However, switching it back is unsuccessful; while the cursor has the Banshee icon bouncing around, it doesn't actually start (after the loading cursor disappears, a window is still open in the Panel, but then disappears).

I think I might be misunderstanding; do you mean to switch back the GTK+ theme while Banshee is running, like I did, or close Banshee, then switch it back, then launch it again?

I should note that Banshee starts almost immediately when GTK+ is set to Raleigh. There isn't even a loading cursor, it just goes *pop* - here I am!

---

### Post by odysseusjak on 2012-01-03
So, it seems that the issue is the outdated version of Oxygen-GTK. Does anyone know if the latest version (1.1.6) fixes this issue? I can't get it to install.

---

