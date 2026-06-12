---
title: "Gnome Do 0.8.2 Crashes When Using Ping.fm"
date: 2010-01-03
forum: General Help
---

### Post by Joseph Schwenker on 2010-01-03
I am using Gnome Do 0.8.2, which I added using the PPA.  It is great, although when I summon Do, and type a Ping.fm status, and press enter, Gnome Do crashes with this output: 

```
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentNullException: Argument cannot be null.
Parameter name: element
  at Do.Core.HistogramRelevanceProvider.IncreaseRelevance (Do.Universe.Item element, System.String match, Do.Universe.Item other) [0x00000] 
  at Do.Core.ItemExtensions.IncreaseRelevance (Do.Universe.Item self, System.String match, Do.Universe.Item other) [0x00000] 
  at Do.Core.Controller.PerformAction (Boolean vanish) [0x00000] 
  at Do.Core.Controller.OnActivateKeyPressEvent (Gdk.EventKey evnt) [0x00000] 
  at Do.Core.Controller.KeyPressWrap (Gdk.EventKey evnt) [0x00000] 
  at Docky.Interface.DockWindow.OnKeyPressEvent (Gdk.EventKey evnt) [0x00000] 
  at Gtk.Widget.keypressevent_cb (IntPtr widget, IntPtr evnt) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.keypressevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Do.Do.Main(System.String[] args)
```

Can anyone make any sense of this?  Additionally, when it starts, it outputs this: ```
(Do:2672): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.
```

The Ping.fm gadget worked fine in the Gnome Do in the 9.04 repositories!  I am using Ubuntu 9.04 32 bit, with all of the latest updates.  Can anyone help?

---

### Post by Joseph Schwenker on 2010-01-04
Now that I have enabled the Twitter docklet as well as the Ping.fm one, it is working fine.  If someone could explain why, though, it would be much appreciated.

---

