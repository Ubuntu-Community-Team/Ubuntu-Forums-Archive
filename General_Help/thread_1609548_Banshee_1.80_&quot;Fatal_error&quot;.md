---
title: "Banshee 1.80 &quot;Fatal error&quot;"
date: 2010-10-30
forum: General Help
---

### Post by Dportner on 2010-10-30
so just recently updated all my packages and restarted my computer, and now banshee gives me an error on start up 

"Encounterd a Fatal error"
Exception has been thrown by the target of an invocation.
```
An unhandled exception was thrown: The database disk image is malformed
database disk image is malformed

  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteNonQuery ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.32.25

Assembly Version Information:

Banshee.AudioCd (1.8.0.0)
Banshee.CoverArt (1.8.0.0)
Banshee.Bpm (1.8.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.8.0.0)
Banshee.AmazonMp3 (1.8.0.0)
Banshee.Daap (1.8.0.0)
Lastfm (1.8.0.0)
Banshee.Dap (1.8.0.0)
Migo (1.8.0.0)
Banshee.Podcasting (1.8.0.0)
Banshee.LibraryWatcher (1.8.0.0)
Banshee.MultimediaKeys (1.8.0.0)
webkit-sharp (1.1.15.0)
Banshee.Lyrics (1.7.4.0)
Banshee.Lastfm (1.8.0.0)
Banshee.WebBrowser (1.8.0.0)
Banshee.Wikipedia (1.8.0.0)
pango-sharp (2.12.0.0)
Banshee.Fixup (1.8.0.0)
Mirage (1.7.4.0)
Banshee.Mirage (1.7.4.0)
Banshee.Widgets (1.8.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (1.8.0.0)
Banshee.GStreamer (1.8.0.0)
Mono.Media (1.8.0.0)
System.Transactions (2.0.0.0)
System.Configuration (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.8.0.0)
Banshee.NowPlaying (1.8.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (1.8.0.0)
System.Xml (2.0.0.0)
Banshee.Core (1.8.0.0)
Hyena.Data.Sqlite (1.8.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.8.0.0)
Mono.Posix (2.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (1.8.0.0)
Nereid (1.8.0.0)
NDesk.DBus.Proxies (0.0.0.0)
System.Core (3.5.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Hyena (1.8.0.0)
System (2.0.0.0)
Banshee.Services (1.8.0.0)
Banshee (1.8.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-25-generic-pae i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

[/etc/debian_version]
squeeze/sid

```

---

### Post by directhex on 2010-10-30
Sounds like your Banshee library got corrupted. Try mv ~/.config/banshee-1/banshee.db ~/.config/banshee-1/banshee.db.bak

---

### Post by Fitoschido on 2010-11-14
Thank you so much!! I have the same problem after a crash in the system (I manually restarted the computer)... \\:D/

Greetings

---

