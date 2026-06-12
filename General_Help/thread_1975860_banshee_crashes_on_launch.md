---
title: "banshee crashes on launch"
date: 2012-05-07
forum: General Help
---

### Post by pmheideman on 2012-05-07
banshee is crashing on launch.  I'm running 12.04 on an hp dm1z.  tried removing and reinstalling from synaptic, no dice.  here's the code I get when launching from terminal.

```
Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.UnknownMethod: Method "Present" with signature "" on interface "org.bansheeproject.Banshee.ClientWindow" doesn't exist
  at Halie.Client+IClientWindowProxy.Present () [0x00000] in <filename unknown>:0 
  at Halie.Client.HandleWindowCommands (Boolean present) [0x00000] in <filename unknown>:0 
  at Halie.Client.Main () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] in <filename unknown>:0 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] in <filename unknown>:0 
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.Exception: org.freedesktop.DBus.Error.UnknownMethod: Method "Present" with signature "" on interface "org.bansheeproject.Banshee.ClientWindow" doesn't exist
  at Halie.Client+IClientWindowProxy.Present () [0x00000] in <filename unknown>:0 
  at Halie.Client.HandleWindowCommands (Boolean present) [0x00000] in <filename unknown>:0 
  at Halie.Client.Main () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] in <filename unknown>:0 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] in <filename unknown>:0 
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 

```

---

### Post by pmheideman on 2012-05-08
Now I'm getting something slightly different.  Here's what terminal says
[```
Info  09:09:59.635] Running Banshee 2.4.0: [Ubuntu 12.04 LTS (linux-gnu, i686) @ 2012-04-21 02:12:32 UTC]
Missing method GetExtensionNodes in assembly /usr/lib/banshee/Banshee.Services.dll, type Mono.Addins.AddinManager
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.TypeLoadException: Could not load type 'Banshee.ServiceStack.ServiceManager' from assembly 'Banshee.Services, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null'.
  at Banshee.ServiceStack.Application.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (System.Reflection.MonoCMethod,object,object[],System.Exception&)
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

I'm also getting a fatal error window that says:
```
An unhandled exception was thrown: Could not load type 'Banshee.ServiceStack.ServiceManager' from assembly 'Banshee.Services, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null'.

  at Banshee.ServiceStack.Application.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (System.Reflection.MonoCMethod,object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 4.0.30319.1
OS Version: Unix 3.2.0.24

Assembly Version Information:

Banshee.Core (2.4.0.0)
Hyena.Data.Sqlite (2.4.0.0)
gdk-sharp (2.12.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.4.0.0)
Mono.Posix (4.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.4.0.0)
Nereid (2.4.0.0)
DBus.Proxies (0.0.0.0)
dbus-sharp-glib (1.0.0.0)
System.Core (4.0.0.0)
Hyena (2.4.0.0)
dbus-sharp (1.0.0.0)
glib-sharp (2.12.0.0)
System (4.0.0.0)
Banshee.Services (2.4.0.0)
Banshee (2.4.0.0)
mscorlib (4.0.0.0)

Platform Information: Linux 3.2.0-24-generic-pae i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

[/etc/debian_version]
wheezy/sid


```

---

### Post by directhex on 2012-05-08
Your Banshee install sounds pretty corrupted.

Install "debsums", and run "debsums -s" - this will report all corrupted packages, which you should reinstall

---

### Post by pmheideman on 2012-05-08
cool thanks i'll give this a try.

---

### Post by pmheideman on 2012-05-08
Here's what I get when I run debsums -s while sudo'd:
```
debsums: changed file /opt/Adobe/Reader9/Reader/GlobalPrefs/.config (from acroread package)
debsums: missing file /opt/Adobe/Reader9/Reader/intellinux/lib/liblber.so (from acroread package)
debsums: missing file /opt/Adobe/Reader9/Reader/intellinux/lib/libldap.so (from acroread package)
debsums: no md5sums for binutils
debsums: no md5sums for cups-driver-gutenprint
debsums: no md5sums for g++
debsums: no md5sums for icedtea6-plugin
debsums: no md5sums for libaudio2
debsums: can't open ure file /usr/share/doc/ure/README.Debian.gz (Too many levels of symbolic links)
debsums: can't open ure file /usr/share/doc/ure/changelog.Debian.gz (Too many levels of symbolic links)

```

Nothing from banshee, so far as I can tell.

---

### Post by pmheideman on 2012-05-16
*bump*

---

### Post by directhex on 2012-05-17
> **pmheideman said:**
> *bump*

Not sure what more it could be. I'd suggest filing a bug on bugzilla.gnome.org

---

### Post by pmheideman on 2012-05-17
thanks, will do.

---

