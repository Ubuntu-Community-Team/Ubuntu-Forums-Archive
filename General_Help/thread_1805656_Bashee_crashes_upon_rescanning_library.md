---
title: "Bashee crashes upon rescanning library"
date: 2011-07-16
forum: General Help
---

### Post by astrobob.tk on 2011-07-16
Hello,

Banshee error after sudden freeze of system while banshee was rescaning music library & after forced (manual) shutdown.

```
$ banshee
[Info  15:22:23.050] Running Banshee 2.0.1: [Ubuntu 10.04.2 LTS (linux-gnu, i486) @ 2011-07-03 20:54:33 UTC]
[Warn  15:22:23.284] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 14: unable to open database file (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] 
  at Hyena.Data.Sqlite.Statement..ctor (Hyena.Data.Sqlite.Connection connection, System.String sql) [0x00000] 
  at Hyena.Data.Sqlite.Connection.Query[Object] (System.String sql) [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] 
[Warn  15:22:23.285] Service `Banshee.Database.BansheeDbConnection' not started: Sqlite error 14: unable to open database file (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks')
[Warn  15:22:23.285] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 14: unable to open database file (SQL: SELECT COUNT(*) FROM sqlite_master WHERE Type='table' AND Name='CoreTracks') (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] 
  at Hyena.Data.Sqlite.Statement.CheckError (Int32 code) [0x00000] 
  at Hyena.Data.Sqlite.Statement..ctor (Hyena.Data.Sqlite.Connection connection, System.String sql) [0x00000] 
  at Hyena.Data.Sqlite.Connection.Query[Object] (System.String sql) [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] 
^C
```

I tried reinstalling banshee, but the problem persisted.

I then found this post: [http://ubuntuforums.org/archive/index.php/t-1678064.html](http://ubuntuforums.org/archive/index.php/t-1678064.html)

I renamed the file: /home/username/.config/banshee-1/banshee.db to /home/username/.config/banshee-1/banshee-backup.db

Banshee started with no error but upon rescanning my library it crashes again:

```
$ banshee
[Info  18:23:15.798] Running Banshee 2.0.1: [Ubuntu 10.04.2 LTS (linux-gnu, i486) @ 2011-07-03 20:54:33 UTC]
[Info  18:23:17.555] Updating web proxy from GConf
[Info  18:23:18.420] All services are started 2.436413
[Info  18:23:18.868] AmazonMP3 store redirect URL: http://integrated-services.banshee.fm/amz/redirect.do/
[Info  18:23:19.228] nereid Client Started
[Info  18:23:19.309] GStreamer version 0.10.28.0, gapless: True, replaygain: False
[Info  18:23:19.339] AppleDeviceSource is ignoring unmounted volume OS
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Hyena.Data.Gui.ListView`1[T].OnExposeEvent (Gdk.EventExpose evnt) [0x00000] 
  at Gtk.Widget.exposeevent_cb (IntPtr widget, IntPtr evnt) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.exposeevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

```

Any help would be appreciated. 

Another question: will my ratings & playlists still exist or are they lost? :S

Thanks

---

### Post by dino99 on 2011-07-16
sudo dpkg-reconfigure banshee

---

### Post by astrobob.tk on 2011-07-16
> **dino99 said:**
> sudo dpkg-reconfigure banshee

Great :D thanks, this solved the crash thing but unfortunately i lost the playlists & ratings :S

anyways, thanks :D

---

