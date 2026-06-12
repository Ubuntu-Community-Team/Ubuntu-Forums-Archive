---
title: "Desktop Drapes Won't Run in 11.04"
date: 2011-05-02
forum: General Help
---

### Post by bw3249 on 2011-05-02
Except for the drive mount point issue (can't type custom mount points) I installed 11.04 [64-bit] without issue.  Everything seems to work except Desktop Drapes.  It seems to have installed OK...it shows up in System|Preferences.  But when you click on it nothing happens.

Launching drapes from a terminal window yields:

brian@Main:~$ drapes
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.DllNotFoundException: libX11.so
  at (wrapper managed-to-native) Egg.TrayIcon:XInternAtom (intptr,string,bool)
  at Egg.TrayIcon.OnRealized () [0x00000] in <filename unknown>:0 
  at Gtk.Widget.realized_cb (IntPtr widget) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.realized_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.ShowAll()
   at Drapes.AppletWidget.CreateNotifyIcon()
   at Drapes.AppletWidget..ctor(AppletStyle style, Nullable`1 size)
   at Drapes.DrapesApp..ctor(System.String[] args)
   at Drapes.DrapesApp.Main(System.String[] args)
brian@Main:~$ 

Any suggestions?  :confused:

---

### Post by andrewthomas on 2011-05-02
Use desktopnova.

---

### Post by bw3249 on 2011-05-02
Always willing to try something new...that gets the job done.  Thanks!!!

---

### Post by qkall on 2011-05-15
> **andrewthomas said:**
> Use desktopnova.

thanks googled same issue and desktopnova is working for me :popcorn:

---

