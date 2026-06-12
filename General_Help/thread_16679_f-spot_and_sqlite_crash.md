---
title: "f-spot and sqlite crash"
date: 2005-02-23
forum: General Help
---

### Post by brettatoms on 2005-02-23
when i start f-spot-0.0.9 on my hoary system for the first time i get this error....
------------------------------------------------------------
Unhandled Exception: System.ApplicationException: Sqlite error database is full
in [0x000d8] (at /build/buildd/mcs-1.0.5/class/Mono.Data.SqliteClient/Mono.Data.SqliteClient/SqliteCommand.cs:255) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader (System.Data.CommandBehavior,bool,int&)
in [0x00005] (at /build/buildd/mcs-1.0.5/class/Mono.Data.SqliteClient/Mono.Data.SqliteClient/SqliteCommand.cs:176) Mono.Data.SqliteClient.SqliteCommand:ExecuteNonQuery ()
in [0x0001e] (at /build/buildd/f-spot-0.0.9/src/TagStore.cs:291) TagStore:CreateTable ()
in [0x0002c] (at /build/buildd/f-spot-0.0.9/src/TagStore.cs:341) TagStore:.ctor (Mono.Data.SqliteClient.SqliteConnection,bool)
in [0x00061] (at /build/buildd/f-spot-0.0.9/src/Db.cs:154) Db:.ctor (string,bool)
in [0x00050] (at /build/buildd/f-spot-0.0.9/src/main.cs:24) Driver:Main (string[])
--------------------------------------

when i start it the second time i get this....

--------------------------------------
Unhandled Exception: System.ApplicationException: Sqlite error no such table: tags
in [0x000d8] (at /build/buildd/mcs-1.0.5/class/Mono.Data.SqliteClient/Mono.Data.SqliteClient/SqliteCommand.cs:255) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader (System.Data.CommandBehavior,bool,int&)
in [0x00005] (at /build/buildd/mcs-1.0.5/class/Mono.Data.SqliteClient/Mono.Data.SqliteClient/SqliteCommand.cs:209) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader (System.Data.CommandBehavior)
in [0x00002] (at /build/buildd/mcs-1.0.5/class/Mono.Data.SqliteClient/Mono.Data.SqliteClient/SqliteCommand.cs:203) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader ()
in [0x0001e] (at /build/buildd/f-spot-0.0.9/src/TagStore.cs:225) TagStore:LoadAllTags ()
in [0x00021] (at /build/buildd/f-spot-0.0.9/src/TagStore.cs:339) TagStore:.ctor (Mono.Data.SqliteClient.SqliteConnection,bool)
in [0x00061] (at /build/buildd/f-spot-0.0.9/src/Db.cs:154) Db:.ctor (string,bool)
in [0x00050] (at /build/buildd/f-spot-0.0.9/src/main.cs:24) Driver:Main (string[])
------------------------------

apparantly its having problems creating the photo database in ~/.gnome2/f-spot...
as root it runs fine, i don't know if it matters but my user home is an NFS mounted share but my root home is a local drive

any ideas?

---

### Post by brettatoms on 2005-02-23
could someone move this post to Desktop Support

---

