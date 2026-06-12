---
title: "Gtk-WARNING **: Locale not supported by C library."
date: 2011-07-06
forum: General Help
---

### Post by evanct on 2011-07-06
Running a fresh install of 10.10. Installed Banshee, it fails to run and gives me this:

```
(Banshee:1765): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

```

Running Devede throws something similar:

```
(process:2125): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
DeVeDe 3.16.9
Locale: en_US
Using package-installed files
Traceback (most recent call last):
  File "/usr/bin/devede", line 138, in <module>
    locale.setlocale(locale.LC_ALL,"")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

Also, probably related: in nautilus, sorting by name is case sensitive. Meaning all files/folders beginning with uppercase letters appear before all files/folders beginning with lowercase letters. I found [this thread]("https://bbs.archlinux.org/viewtopic.php?id=34699") about the same problem, but the solution doesn't apply to me because the line `export LC_COLLATE="C"` doesn't appear in my /etc/profile.

---

### Post by evanct on 2011-07-06
bump

---

### Post by evanct on 2011-07-06
anyone?

---

