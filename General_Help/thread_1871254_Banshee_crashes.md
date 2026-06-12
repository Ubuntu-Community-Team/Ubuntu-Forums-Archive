---
title: "Banshee crashes"
date: 2011-10-28
forum: General Help
---

### Post by cyberdyne3 on 2011-10-28
Banshee was by far my favourite player so I decided to upgrade to 2.2. To begin with, 2.2 was working fine but all of a sudden it crashed - just closed itself - and continued to do so every time I tried to re-open it.
So, I removed it and reinstalled it (presumably v2.0 (?) - from the software center) but the same problem exists.

The error on the last crash is below.

```
An unhandled exception was thrown: This version of Banshee was prepared to work with older database versions (=< 43) thus it is too old to support the current version of the database (44).

  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.38.12

Assembly Version Information:

System.Configuration (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (2.0.0.0)
Banshee.NowPlaying (2.0.0.0)
Mono.Cairo (2.0.0.0)
System.Xml (2.0.0.0)
Banshee.Core (2.0.0.0)
Hyena.Data.Sqlite (2.0.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (2.0.0.0)
gtk-sharp (2.12.0.0)
Banshee.ThickClient (2.0.0.0)
Nereid (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
Hyena (2.0.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
System (2.0.0.0)
Banshee.Services (2.0.0.0)
Banshee (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.38-12-generic i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

[/etc/debian_version]
squeeze/sid
```

Any help greatly appreciated.
Thank you

---

### Post by LinuxFan999 on 2011-10-28
Banshee sucks. Try VLC instead.

---

### Post by cyberdyne3 on 2011-10-28
> **LinuxFan999 said:**
> Banshee sucks. Try VLC instead.

Yeah, big help, thanks but no thanks

---

### Post by directhex on 2011-10-31
The error is self-explanatory. Banshee is dying on your database file (~/.config/banshee-1/banshee.db) because the database file uses internal format 44, and your version of Banshee supports only 43 or below. This will have happened because 2.2 and 2.0 use different versions, and when you ran 2.2 it upgraded your database to format version 44.

If you blow away the DB, it will be recreated.

---

### Post by cyberdyne3 on 2011-10-31
> **directhex said:**
> ..//..
If you blow away the DB, it will be recreated.

Could you tell me how to do that please?
Thank you.

---

### Post by awatt on 2011-11-18
[COLOR=Sienna]directhex[/COLOR] means that if you delete it, Banshee will create this file when you start it next time.
I was having the same problem, and deleting the (~/.config/banshee-1/banshee.db) file fixed it.
I did have to re-import all of my audio files however.

---

### Post by Michael.1 on 2012-03-23
Actually it is possible to restore Banshee without removing it's database. All you need is to change the 'database version' mentioned in the error message.
Run in the terminal
```
sqlite3 -interactive ~/.config/banshee-1/banshee.db
```
A command prompt will appear starting with 'sqlite>'
Then enter the command
```
update CoreConfiguration set Value = 43 where EntryID = 1;
```
To quit the sqlite3 command line, enter
```
.quit
```

---

### Post by indigo42 on 2012-11-03
@Michael.1
Thanks so much! Your solution worked and my database is in tact!

You...sir...are a Gentleman and a Scholar!

---

