---
title: "Purge F-spot configure files??? due to crash"
date: 2010-01-03
forum: General Help
---

### Post by Jimtuv on 2010-01-03
I am running Ubuntu 9.10 and F-spot 0.6.1.5

F-spot is crashing in one user but not any others. I need to purge the configuration files for that user. anyone know where they are stored. I already tried deleting the f-spot folders in .conf and .gconf with no effect.

---

### Post by Jimtuv on 2010-01-04
The odd thing about this is that I switched into KDE and f-spot works fine in there. this is only when I am in gnome and only in one user. f-spot works fine in all other users in Gnome and KDE. It crashes on startup

---

### Post by Jimtuv on 2010-01-04
I fixed it. More accidentally then on purpose. By going into KDE and starting the F-spot then importing some photos and exiting. When I logged off and back on into Gnome F-spot worked fine.

---

### Post by samden on 2010-01-31
Very odd. I've just experienced similar behaviour - f-spot crashes for one user but not the other, when applying a tag to any photo. Linux Mint 8 (basically Ubuntu 9.10) and F-spot 0.6.1.5, so the same setup as yourself.

The config files should be identical for both users, as I've got them both symlinked to a central location to synchronise it across both accounts. So as you've found the problem must be somewhere other than in the config files. Unfortunately I'm only running Gnome so can't try your fix.

Terminal output.
On starting f-spot:
```
(/usr/lib/f-spot/f-spot.exe:3005): GLib-WARNING **: g_set_prgname() called multiple times
[Info  21:54:35.617] Initializing DBus
[Info  21:54:35.762] Initializing Mono.Addins
ERROR: Add-in cache directory could not be created (Access to the path "/home/sarah/.config/f-spot/addin-db-001/addin-data/125646" is denied.)
[Info  21:54:35.959] Starting new FSpot server (f-spot 0.6.1.5)

** (/usr/lib/f-spot/f-spot.exe:3005): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:3005): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:3005): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:3005): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:3005): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  21:54:38.619] Starting BeagleService
[Info  21:54:38.642] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:3005): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
```
When it crashes:
```
Unhandled Exception: Mono.Data.SqliteClient.SqliteExecutionException: SQL logic error or missing database
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
```
It's all greek to me, but if someone can understand it that would be great.

Does anyone have any thoughts as to possible causes of this?

---

### Post by samden on 2010-01-31
Solved, simple mistake: permissions error. Didn't have write permissions for config files due to my tweaking. Hopefully helps someone in future.

---

