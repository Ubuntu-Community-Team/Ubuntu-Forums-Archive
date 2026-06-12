---
title: "gnome-do will no longer open after update"
date: 2009-07-04
forum: General Help
---

### Post by chriskin on 2009-07-04
i get this error when i run it in terminal

```

(Do:14746): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[Debug 03:57:17.257] Acquiring org.freedesktop.DBus session instance
[Debug 03:57:17.265] Starting org.bansheeproject.CollectionIndexer

Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bansheeproject.CollectionIndexer was not provided by any .service files
  at IBusProxy.StartServiceByName (System.String flags, UInt32 ) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name, UInt32 flags) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name) [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.IndexerClient.Start () [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.SimpleIndexerClient.Start () [0x00000] 
christos@CNB:~$ 

```

and then gnome-do just disappears.
it stays on the tray for less than a second each time

---

### Post by mjbauer95 on 2009-07-19
Similar messages here.

---

### Post by orbish on 2009-07-20
I was having a similar problem, I just updated my repositories to karmic, and just updated everything.  Having gnome-do was more important to me than a few hiccups from running alpha.

---

