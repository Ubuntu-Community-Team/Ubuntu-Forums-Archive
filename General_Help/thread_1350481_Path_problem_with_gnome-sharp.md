---
title: "Path problem with gnome-sharp"
date: 2009-12-09
forum: General Help
---

### Post by afrodeity on 2009-12-09
[I]Why can't mono find gtk-sharp.dll?
You most likely have installed Gtk# into a prefix other than where mono is installed. In order for the runtime to locate the Gtk# assemblies, you will need to add their location to the MONO_GAC_PREFIX environment variable. For the default installation prefix, this will mean executing the following command:[/I]

export MONO_GAC_PREFIX=/usr/local:$MONO_GAC_PREFIX

But doing this hasn't helped find gnome-sharp which is here

usr/lib/cli/gnome-sharp-2.24
/usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll
/usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll.config

I've tried 
export MONO_GAC_PREFIX=/usr/local:/usr/lib/cli/:$MONO_GAC_PREFIX

---

### Post by afrodeity on 2009-12-09
[http://ubuntuforums.org/showthread.php?t=640121](http://ubuntuforums.org/showthread.php?t=640121)

---

### Post by afrodeity on 2009-12-09
glibsharpglue-2???????????? stuck :(

```
Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Gtk.Application ---> System.DllNotFoundException: glibsharpglue-2
  at (wrapper managed-to-native) GLib.Thread:glibsharp_g_thread_supported ()
  at GLib.Thread.get_Supported () [0x00000] 
  at Gtk.Application..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 

```

---

