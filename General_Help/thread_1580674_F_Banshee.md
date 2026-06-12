---
title: "F****** Banshee"
date: 2010-09-23
forum: General Help
---

### Post by Cant on 2010-09-23
Everytime Banshee tries to switch songs from a local folder it crashes with. I have tried completely removing it and reinstalling but that did nothing. Here is what I get when I run it from a terminal.

```

[Info  20:56:57.939] Running Banshee 1.6.1: [Ubuntu 10.04 LTS (linux-gnu, i486) @ 2010-06-18 09:51:55 UTC]
[Info  20:56:59.862] All services are started 1.027051
[Info  20:57:00.666] nereid Client Started
```

^This is startup.

```
(Banshee:2996): Gtk-CRITICAL **: gtk_widget_event: assertion `WIDGET_REALIZED_FOR_EVENT (widget, event)' failed
```

^This happened a short while after startup.

```
Unhandled Exception: Mono.Data.Sqlite.SqliteException: The database disk image is malformed
database disk image is malformed
  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteNonQuery ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000]
```

^This is the crash.

Help? And please don't make me bump this thread endlessly, too :(

---

### Post by WorMzy on 2010-09-23
Try deleting your user's banshee folder. It'll probably be ~/.banshee, ~/.local/share/banshee, or ~/.config/banshee. If it's none of those, open a terminal and run

```
sudo updatedb && locate ~/.*/banshee
```

That should find the folder for you.

---

### Post by Cant on 2010-09-23
> **WorMzy said:**
> Try deleting your user's banshee folder. It'll probably be ~/.banshee, ~/.local/share/banshee, or ~/.config/banshee. If it's none of those, open a terminal and run

```
sudo updatedb && locate ~/.*/banshee
```

That should find the folder for you.

That worked, thank you :guitar:

---

### Post by WorMzy on 2010-09-23
Glad to hear it.

It's worth bearing in mind that, if an application suddenly stops working, it's more than likely that the problem lies in your home folder, and uninstalling/reinstalling the application will have no effect since the uninstallation procedure never touches the files stored in your home folder. So the next time something stops working, delete (or rename) the config folder in your home folder first, and see if that fixes the problem.

---

