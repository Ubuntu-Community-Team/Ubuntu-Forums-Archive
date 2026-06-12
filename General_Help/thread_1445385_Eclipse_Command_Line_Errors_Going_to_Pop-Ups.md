---
title: "Eclipse: Command Line Errors Going to Pop-Ups"
date: 2010-04-02
forum: General Help
---

### Post by shonuff on 2010-04-02
My question is:  

Is there a way to ensure errors from command line actions to are sent  to the console instead of a pop-up?


Background story:I'm trying to run various Eclipse tools from the command line (via SSH... I'm setting up automation) and I repeatedly run into errors like:

org.eclipse.swt.SWTError: No more handles gtk_init_check() failed
at org.eclipse.swt.SWT.error(SWT.java:3803)
at org.eclipse.swt.widgets.Display.createDisplay(Display.java:855)


 or 



 (.:24425): GLib-GObject-WARNING **: invalid (NULL) pointer instance
(.:24425): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion  `G_TYPE_CHECK_INSTANCE (instance)’ failed
(.:24425): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion  `GDK_IS_SCREEN (screen)’ failed
(.:24425): GLib-GObject-CRITICAL **: g_object_get: assertion  `G_IS_OBJECT (object)’ failed


It turns out that this is because there are error messages that are being sent to pop-ups.  To find out what is going on, I have to VNC to the device,  xhost + localhost, and run the command again to see the error message printed.  


I'm using:
RSAEE 7.0.1
java.fullversion=JRE 1.6.0 IBM J9 2.4 Linux x86-32  jvmxi3260sr6-20091001_43491 (JIT enabled, AOT enabled)
Ubuntu 9.10

---

### Post by shonuff on 2010-04-07
I don't know if this is a problem in Rational Software Analyzer or in Unbuntu.  (I suspect the former, and that my original question was therefore nonsensical.)

In either case, I solved the problem by running the command via VNC (and there responding to pop-ups and taking corrective action) until there were no more error pop-ups.  The command was then running cleanly via VNC, however, when running via SSH I continued to see messages like.....

(.:19232): Gtk-WARNING **: Error loading theme icon 'gtk-dialog-error' for stock:
(.:19232): Gtk-CRITICAL **: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed
(.:19232): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkstyle.c:2318: invalid icon size '6'
(.:19232): Gtk-CRITICAL **: gtk_style_render_icon: assertion `pixbuf != NULL' failed
(.:19232): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

**I got around this using xvfb.**

I'm adding all this in case somebody comes across this thread by Googling when they hit this problem.

---

