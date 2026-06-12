---
title: "failure running incollector"
date: 2010-12-04
forum: General Help
---

### Post by aninona on 2010-12-04
've just installed incollector using deb file. running if from cli outputs:
```
** (incollector:3087): WARNING **: Missing method .ctor in assembly /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll, type System.Runtime.CompilerServices.RuntimeCompatibilityAttribute

** (incollector:3087): WARNING **: The class System.Runtime.CompilerServices.RuntimeCompatibilityAttribute could not be loaded, used in gtk-sharp

** (incollector:3087): WARNING **: Can't find custom attr constructor image: /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll mtoken: 0x0a000121

Unhandled Exception: System.TypeLoadException: Could not load type 'System.Runtime.CompilerServices.RuntimeCompatibilityAttribute' from assembly 'gtk-sharp'.
  at (wrapper managed-to-native) System.MonoType:GetMethodsByName (string,System.Reflection.BindingFlags,bool,System.Type)
  at System.MonoType.GetMethods (BindingFlags bindingAttr) [0x00000] in <filename unknown>:0 
  at GLib.Object.InvokeClassInitializers (GType gtype, System.Type t) [0x00000] in <filename unknown>:0 
  at GLib.Object.RegisterGType (System.Type t) [0x00000] in <filename unknown>:0 
  at GLib.Object.LookupGType (System.Type t) [0x00000] in <filename unknown>:0 
  at GLib.Object.LookupGType () [0x00000] in <filename unknown>:0 
  at GLib.Object.CreateNativeObject (System.String[] names, GLib.Value[] vals) [0x00000] in <filename unknown>:0 
  at Gtk.Object.CreateNativeObject (System.String[] names, GLib.Value[] vals) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.CreateNativeObject (System.String[] names, GLib.Value[] vals) [0x00000] in <filename unknown>:0 
  at Gtk.ScrolledWindow..ctor (Gtk.Adjustment hadjustment, Gtk.Adjustment vadjustment) [0x00000] in <filename unknown>:0 
  at Gtk.ScrolledWindow..ctor () [0x00000] in <filename unknown>:0 
  at Incollector.GUI.Widgets.EntryPreview..ctor () [0x00000] in <filename unknown>:0 
  at Incollector.GUI.MainWindow..ctor () [0x00000] in <filename unknown>:0 
  at Incollector.Engine.Globals.Init (System.String[] args) [0x00000] in <filename unknown>:0 
  at Incollector.MainClass.Main (System.String[] args) [0x00000] in <filename unknown>:0 

```

what shall I do? tnx;)

---

### Post by directhex on 2010-12-04
Looks like this needs to be recompiled against GTK# 2.12.10

---

### Post by Rob-NYC on 2011-01-06
inCollector apparently caused a big problem with my system, which is running Ubuntu 10.10. Seemed like a memory leak of some kind. The CPU was maxed out after installing inCollector. Additionally, the program would not run.

My system was so jammed up, I had to scrub the drive and reinstall Ubuntu.

So be careful about what you install.

---

### Post by bx.s on 2011-01-11
I found instructions here that helped me get incollector running on 10.10: [http://u8untu.blogetery.com/2010/02/09/incollector-with-good-karma/](http://u8untu.blogetery.com/2010/02/09/incollector-with-good-karma/)

However, step 3 seems to have a bug. This is what I ended up doing:
I changed the contents of /usr/bin/incollector to be:

[PHP]
#!/bin/sh
exec /usr/bin/mono --runtime=v2.0.50727 /usr/lib/incollector/incollector.exe
[/PHP]

---

