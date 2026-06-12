---
title: "Gnome-Do Problem"
date: 2009-08-23
forum: General Help
---

### Post by t4ggs on 2009-08-23
Sometimes when i enter ubuntu, gnome do works as expected, i start typing, s for example and it founds shiretoko (firefox 3.5) but sometimes it dosnt work at all, no matter what I type...in order to make it work i have to close it an launch gnome do again... any idea why?? or how to fix it???

---

### Post by t4ggs on 2009-08-23
bump

---

### Post by t4ggs on 2009-08-24
thats what i get when i run it form a terminal with debug

[Info  15:14:30.081] [UniverseManager] Universe contains 634 items.
[Debug 15:14:56.551] [RelevanceProvider] Successfully saved learned usage data.
[Debug 15:15:18.990] [UniverseManager] Reloading item source "Recent Files"...
[Debug 15:15:18.990] [UniverseManager] Reloading item source "Window Screen Items"...
[Debug 15:15:18.990] [UniverseManager] Reloading item source "Generic Window Items"...
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
GLib.MissingIntPtrCtorException: GLib.Object subclass Do.Interface.AnimatedClassicWindow must provide a protected or public IntPtr ctor to support wrapping of native object handles.
  at GLib.ObjectManager.CreateObject (IntPtr raw) [0x00000] 
  at GLib.Object.GetObject (IntPtr o, Boolean owned_ref) [0x00000] 
  at GLib.Object.GetObject (IntPtr o) [0x00000] 
  at Gtk.Widget.get_Parent () [0x00000] 
  at Do.Interface.ClassicBackgroundRenderer.get_BackgroundColor () [0x00000] 
  at Do.Interface.AnimationBase.BezelDrawingArea.get_BackgroundColor () [0x00000] 
  at Do.Interface.AnimationBase.BezelDrawingArea.OnStyleSet (Gtk.Style previous_style) [0x00000] 
  at Gtk.Widget.styleset_cb (IntPtr widget, IntPtr previous_style) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.styleset_cb(IntPtr widget, IntPtr previous_style)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Do.Do.Main(System.String[] args)
ytagger@ytagger-laptop:~$ 





any idea??? pleaseee

---

### Post by abrari on 2009-08-24
Try to uncheck "Animate window" on Do's preferences.

---

### Post by dhughes on 2009-08-24
Is the path your searching on an external drive that isn't mounted or doesn't auto mount at boot? 

 I'm sure you would notice that but I'd thought I'd point out the obvious first.

edit: ignore that, I re-read your comment. I don't look before I leap. At least I bumped your post.

---

### Post by t4ggs on 2009-08-24
i unchecked the "animate window" and still got lot of problems...btw what does the animate window does??

and dhughes, i didnt understand what u said...btw, i've not idea whats written in the debug info ... could u please explain it to me??
thanks guys

---

### Post by dhughes on 2009-08-25
> **t4ggs said:**
> i unchecked the "animate window" and still got lot of problems...btw what does the animate window does??

and dhughes, i didnt understand what u said...btw, i've not idea whats written in the debug info ... could u please explain it to me??
thanks guys


 I was thinking about Deskbar not Gnome-Do, I got a bit mixed up.

 Maybe you should re-install Gnome-Do it could do wonders, as well (after re-installing Gnome-Do) as re-indexing if it does index, or maybe I'm thinking of Deskbar again.

 Bumpity bump again!

---

### Post by t4ggs on 2009-08-25
hahaha no, that time is ok, gnome-do does index//anyway thanks for the bump haha

---

### Post by stinkeye on 2009-08-25
Try using the shelf plugin for your frequently used programs, or the alias plugin.

---

### Post by atulkakrana on 2011-02-08
Same problem...It is beyond fix...coz it is not identified yet..

Atul Kakrana

---

