---
title: "F-Spot Photo Manager won't start."
date: 2010-05-29
forum: General Help
---

### Post by gabo.cr on 2010-05-29
Since I installed Lucid Lynx in my laptop one month ago, F-Spot Photo Manager won't start.
I did nothing to it, it has never worked, I just installed Ubuntu, I installed the restricted extras plus a few more packages.
But every time I click on the Photo Manager icon, nothing happens.
I am thinking on removing the program and reinstalling it from the Ubuntu Software Center, but I don't know if that is the best thing to do.
Any ideas?

---

### Post by wojox on 2010-05-29
What happens if you try to launch it from the terminal:

```
f-spot
```

---

### Post by westernpenguin on 2010-05-29
Check this thread: [http://ubuntuforums.org/showthread.php?p=9331837](http://ubuntuforums.org/showthread.php?p=9331837) 

Otherwise, can you run f-spot from a terminal and post/attach the output?

---

### Post by gabo.cr on 2010-05-30
This is what I get running f-spot in Terminal:

> $ f-spot
[Info  22:04:21.849] Initializing DBus
[Info  22:04:21.986] Initializing Mono.Addins
[Info  22:04:22.194] Starting new FSpot server (f-spot 0.6.1.5)
[Info  22:04:22.292] Updating F-Spot Database

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 

I then tried the solution from the thread: [http://ubuntuforums.org/showthread.php?p=9331837](http://ubuntuforums.org/showthread.php?p=9331837) 

I used this command:

```
rm -R ~/.config/f-spot
```

Then this one:

```
rm -R ~/gconf/apps/f-spot
```

But I get this error:

> rm: cannot remove `/home/gabo/gconf/apps/f-spot': No such file or directory


But F-Spot Manager is working now !
Thank you so much.
\\:D/\\:D/

---

