---
title: "Data corruption"
date: 2012-01-13
forum: General Help
---

### Post by GTMoraes on 2012-01-13
Meh. not a Ubuntu fault, but mine for not taking the proper precautions.

tl;dr:
Computer crashed and things became inconsistent. Radiance theme is mixed up with Ambiance theme and Banshee no longer opens (God knows what else doesn't). Ubuntu "scandisk" doesn't kick in on boot. How do I fix this? Screenshots of the mess below

Full version:
SO.. I was trying to find a good undervoltage value for my netbook, it's a try and error, as you might know.

But i messed things a little bit. As I was stress-testing the CPU on one frequency, I started to use the system normally, to see how it would operate under stress and how much watts would it take in that situation. 
Problem is, I carried the stress test to another frequency, with a untested voltage, while using the computer. It crashed after few seconds (due to 0,0125v). Nothing too bad, really.

Or not. When I restarted, at first sight, I noticed the changes: My Radiance theme is mixed up with Ambiance (windows topbar remains silver, but the area below it - where the Back and Forward buttons are - are black. Also, upon login, I see the original ubuntu wallpaper (while Unity isn't loaded), and then my wallpaper (used to be always my wallpaper upon login).
Icons have changed too, to match the black Ambiance theme (I'll be attaching a few screenshots).
Banshee isn't working either (actually, the netbook crashed while I was opening a music)
That's all what he says:
```

Encontered a Fatal Error
Exception has been thrown by the target of an invocation

An unhandled exception was thrown: Invalid handle to path 
"/home/gtmoraes/.config/banshee-1/addin-db-001/config.xml"

  at System.IO.FileStream..ctor (System.String path, FileMode
 mode, FileAccess access, FileShare share, Int32 bufferSize, 
Boolean anonymous, FileOptions options) [0x00000] in <filename 
unknown>:0 
  at System.IO.FileStream..ctor (System.String path, FileMode 
mode, FileAccess access, FileShare share) [0x00000] in <filename
 unknown>:0 
  at (wrapper remoting-invoke-with-check) 
System.IO.FileStream:.ctor 
(string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileSha
re)
  at System.Xml.XmlUrlResolver.GetEntity (System.Uri absoluteUri, System.String role, System.Type ofObjectToReturn) [0x00000] in 
<filename unknown>:0 
  at Mono.Xml2.XmlTextReader.GetStreamFromUrl (System.String url, System.String& absoluteUriString) [0x00000] in <filename 
unknown>:0 
  at Mono.Xml2.XmlTextReader..ctor (System.String url, 
System.Xml.XmlNameTable nt) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlTextReader..ctor (System.String url, 
System.Xml.XmlNameTable nt) [0x00000] in <filename unknown>:0 
  at System.Xml.XmlDocument.Load (System.String filename) 
[0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.DatabaseConfiguration.Read 
(System.String file) [0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.get_Configuration () 
[0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.RunPendingUninstalls 
(IProgressStatus monitor) [0x00000] in <filename unknown>:0 
  at Mono.Addins.Database.AddinDatabase.Update (IProgressStatus 
monitor, System.String domain) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinRegistry.Update (IProgressStatus monitor) 
[0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () 
[0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () 
[0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in 
<filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean 
registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault,
 System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename 
unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) 
System.Reflection.MonoCMethod:InternalInvoke 
(System.Reflection.MonoCMethod,object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, 
BindingFlags invokeAttr, System.Reflection.Binder binder, 
System.Object[] parameters, System.Globalization.CultureInfo 
culture) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, 
BindingFlags invokeAttr, System.Reflection.Binder binder, 
System.Object[] parameters, System.Globalization.CultureInfo 
culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags 
invokeAttr, System.Reflection.Binder binder, System.Object[] 
parameters, System.Globalization.CultureInfo culture) [0x00000]
 in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] 
parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean 
nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000]
 in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename
 unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup 
(Hyena.Gui.StartupInvocationHandler startup) [0x00000] in 
<filename unknown>:0 

.NET Version: 4.0.30319.1
OS Version: Unix 3.0.0.14


Assembly Version Information:

System.Xml (4.0.0.0)
Banshee.Core (2.2.0.0)
Hyena.Data.Sqlite (2.2.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.6.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.2.0.0)
Mono.Posix (4.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.2.0.0)
Nereid (2.2.0.0)
DBus.Proxies (0.0.0.0)
System.Core (4.0.0.0)
Hyena (2.2.0.0)
dbus-sharp (1.0.0.0)
glib-sharp (2.12.0.0)
System (4.0.0.0)
Banshee.Services (2.2.0.0)
Banshee (2.2.0.0)
mscorlib (4.0.0.0)

Platform Information: Linux 3.0.0-14-generic x86_64 x86_64 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

[/etc/debian_version]
wheezy/sid

```


So.. how do I fix the crap I've made?

---

### Post by directhex on 2012-01-13
Try "rm -r /home/gtmoraes/.config/banshee-1/"

---

### Post by GTMoraes on 2012-01-14
> **directhex said:**
> Try "rm -r /home/gtmoraes/.config/banshee-1/"
That did the trick for Banshee, thanks!

But what about the themes corruption?

---

