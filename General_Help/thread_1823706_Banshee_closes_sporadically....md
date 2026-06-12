---
title: "Banshee closes sporadically..."
date: 2011-08-12
forum: General Help
---

### Post by InsertNameHere345 on 2011-08-12
Hey, as soon as I open Banshee, the player closes as soon as I click on the window itself :confused: It had been working fine, it crashed once, and now I have this problem.

Running through terminal I get:

```

[Info  17:16:06.275] Running Banshee 1.8.1: [Ubuntu 10.10 (linux-gnu, i686) @ 2011-02-02 09:04:16 UTC]
[Info  17:16:13.646] Updating web proxy from GConf
[Info  17:16:13.927] All services are started 6.355532
[Info  17:16:18.778] nereid Client Started
[Info  17:16:19.554] AppleDeviceSource is ignoring unmounted volume System Reserved
[Warn  17:16:19.577] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 

Unhandled Exception: Mono.Data.Sqlite.SqliteException: Sqlite error
cannot start a transaction within a transaction
  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteNonQuery () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteNonQuery ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] in <filename unknown>:0 

```

---

