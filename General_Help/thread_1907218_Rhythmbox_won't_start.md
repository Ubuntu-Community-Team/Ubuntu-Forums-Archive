---
title: "Rhythmbox won't start"
date: 2012-01-10
forum: General Help
---

### Post by jonnyboysmithy on 2012-01-10
I downgraded from 11.10 to 10.04 and rhythmbox won't start, it complains that the database is a newer version. I tried reconfiguring it, and reinstalling it. from terminal I get this: ```
jotham@jotham-desktop:~$ rhythmbox
jotham@jotham-desktop:~$ 

```
I tried banshee but that also is a newer version and also throws and error:An unhandled exception was thrown: ```
Could not read add-in description

  at Mono.Addins.Addin.get_Description () [0x00000] 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] 
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () [0x00000] 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] 
  at Nereid.Client..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.32.37

Assembly Version Information:

System.Xml (2.0.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.6.0.0)
gtk-sharp (2.12.0.0)
Banshee.Core (1.6.0.0)
Banshee.ThickClient (1.6.0.0)
Nereid (1.6.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
System (2.0.0.0)
Hyena (1.6.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.6.0.0)
Banshee (1.6.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-37-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

[/etc/debian_version]
squeeze/sid

```
How can I start either of these?

---

### Post by jonnyboysmithy on 2012-01-11
Okay so I got banshee working again by deleting the config folder, rhythmbox won't go still..

---

### Post by jonnyboysmithy on 2012-01-11
Help anyone?

---

### Post by jonnyboysmithy on 2012-01-11
Solved! I deleted all the config files rebooted and rhythmbox works fine once again:):popcorn:

---

