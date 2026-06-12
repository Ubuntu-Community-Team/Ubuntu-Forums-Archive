---
title: "Drapes Not Working in Gnome3"
date: 2011-05-22
forum: General Help
---

### Post by mac4rfree on 2011-05-22
Hi Guys,

I am having GNome3. Now even after i have installed Drapes. I am not able to make it work..

Whenever i am trying to start it from terminal, i am getting this.

```
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

```

Can somebody help me with this..

Cheers!!!!

---

### Post by cbowman57 on 2011-05-22
I've never used drapes, I usually use desktopnova but I haven't tested that with G3 shell.

Does drapes work in the other environments?  Unity, classic gnome.

---

### Post by hawthornso23 on 2011-05-22
Drapes isn't being actively maintained as far as I can see. I looked at the source code a while back, but it was a mess and wouldn't compile. It doesn't work properly with either gnome 3 or unity. In natty with gnome 2, while it does work sometimes, there are problems. It sometimes crashes leaving orphaned mono processes running which slow the machine and which a logout won't kill. 

I haves used drapes for 2 years, however because of these issues I have recently switched to DesktopNova. It works in a very similar fashion to Drapes and is being actively maintained. I recommend you consider  switching to DesktopNova. My experience has been good.

I have not tried it with Gnome 3. However because it is being actively maintained you are likely to have better luck getting it to run with gnome3 than Drapes.

---

