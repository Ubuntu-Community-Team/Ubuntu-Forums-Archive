---
title: "F-Spot Encountered a Fatal Error"
date: 2010-03-30
forum: General Help
---

### Post by wbar2 on 2010-03-30
Ubuntu 9.10 64-bit

I was importing photos into f-spot. Then my laptop shutdown because it overheated (a different problem). Now f-spot will not open. A dialog pops up and says "F-Spot Encountered a Fatal Error. Exception has been thrown by the target of an invocation."

Here are the error details:

```
An unhandled exception was thrown: Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at Mono.Addins.RuntimeAddin.CreateInstance (System.String typeName, Boolean throwIfNotFound) [0x00000] 
  at Mono.Addins.RuntimeAddin.CreateInstance (System.String typeName) [0x00000] 
  at FSpot.Widgets.SidebarPageNode.GetSidebarPage () [0x00000] 
  at MainWindow.OnSidebarExtensionChanged (System.Object s, Mono.Addins.ExtensionNodeEventArgs args) [0x00000] 
  at Mono.Addins.ExtensionNode.OnChildNodeAdded (Mono.Addins.ExtensionNode node) [0x00000] 
  at Mono.Addins.ExtensionNode.NotifyChildChanged () [0x00000] 
  at Mono.Addins.TreeNode.NotifyChildrenChanged () [0x00000] 
  at Mono.Addins.ExtensionContext.NotifyConditionChanged (Mono.Addins.ConditionType cond) [0x00000] 
  at Mono.Addins.ExtensionContext.OnConditionChanged (System.Object s, System.EventArgs a) [0x00000] 
  at Mono.Addins.ConditionType.NotifyChanged () [0x00000] 
  at FSpot.Extensions.ViewModeCondition.<ViewModeCondition>m__5 () [0x00000] 
  at FSpot.Extensions.ViewModeCondition.set_Mode (ViewMode value) [0x00000] 
  at FSpot.Widgets.Sidebar.HandleContextChanged (System.Object sender, System.EventArgs args) [0x00000] 
  at FSpot.Widgets.Sidebar.set_Context (ViewContext value) [0x00000] 
  at MainWindow..ctor (.Db db) [0x00000] 
  at FSpot.Core.get_MainWindow () [0x00000] 
  at FSpot.Core.Organize () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.1433

Assembly Version Information:

glade-sharp (2.12.0.0)
System.Core (3.5.0.0)
FSpot.Bling (0.0.0.0)
pango-sharp (2.12.0.0)
gtk-sharp-beans (2.14.0.0)
gnome-sharp (2.24.0.0)
System.Transactions (2.0.0.0)
System.Configuration (2.0.0.0)
FSpot.Widgets (0.0.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.24.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
FSpot.Query (0.0.0.0)
FSpot.JobScheduler (0.0.0.0)
gdk-sharp (2.12.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gnome-vfs-sharp (2.24.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
FSpot.Platform (0.0.0.0)
Mono.Posix (2.0.0.0)
FSpot.Utils (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
System (2.0.0.0)
Mono.Addins.Setup (0.4.0.0)
glib-sharp (2.12.0.0)
f-spot (0.6.1.5)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.31-20-generic x86_64 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
squeeze/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```

I've read somewhere that there might be a bug with themes, but I've changed mine back and forth. I don't really think this is a bug as much as something that happened when the computer crashed. I've tried uninstalling f-spot and reinstalling it, but I've had no luck. I get the same error above. Anybody have any idea on how to get it working again?

---

### Post by wbar2 on 2010-04-01
bump

---

### Post by IanVaughan on 2010-04-04
Mine just closes without showing anything when lauched via the menu item.
And hangs from command line at :
```
Found active FSpot server: FSpot.ICoreProxy
```

> 
$ uname -a
Linux Bart 2.6.32-19-generic #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 i686 GNU/Linux

$ f-spot -version
F-Spot  0.6.1.5 - (c)2003-2009, Novell Inc
Personal photo management for the GNOME Desktop

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"


---

### Post by wbar2 on 2010-04-09
I'm running Karmic, not Lucid.

^bump

---

### Post by wbar2 on 2010-04-09
The database was corrupt. I deleted it, and now it works fine.

It was located here:
~/.config/f-spot/photos.db

---

### Post by crinus on 2011-02-19
Superb! 

Worked for me, too. 
):P

I was thinking before this that it might be some serious 
error, because there plenty of lines in the error trace. But it was quite simple.

Regards,
Jukka

---

