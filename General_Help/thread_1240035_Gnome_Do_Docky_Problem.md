---
title: "Gnome Do Docky Problem"
date: 2009-08-14
forum: General Help
---

### Post by Jason Weiss on 2009-08-14
Hi 

I have friends coming around tomorrow and I want to show them how cool computer my is so I tried to install Docky by using metacity.

I followed a tut I found on google, but when I try to open gnome do it just closes again.

Please help me impress my friends, if I can't go "look at me, I use linux!!" then I might as well not invite them around. 

PS friends = random realestate agents I pick from the phone book and ask them to come around to give me a free valuation on my house, even though I am renting.

When I run Gnome do in terminal this is the out put

```
Could not read MPD database file: ApplicationName='/usr/bin/mpc', CommandLine='playlist --format ":%title%:%artist%:%album%:%file%"', CurrentDirectory=''
Could not locate Skype on D-Bus. Make sure Skype is running
Could not locate Skype on D-Bus. Make sure Skype is running
Could not locate Skype on D-Bus. Make sure Skype is running
Could not read MPD database file: ApplicationName='/usr/bin/mpc', CommandLine='playlist --format ":%title%:%artist%:%album%:%file%"', CurrentDirectory=''
[Error 21:03:42.913] [PidginContactItemSource] Error reading Pidgin buddy list file: Could not find file "/home/jason/.purple/blist.xml".
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: Object reference not set to an instance of an object.
[Debug 21:03:43.497] Acquiring org.freedesktop.DBus session instance
[Debug 21:03:43.505] Starting org.bansheeproject.CollectionIndexer

Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bansheeproject.CollectionIndexer was not provided by any .service files
  at IBusProxy.StartServiceByName (System.String flags, UInt32 ) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name, UInt32 flags) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name) [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.IndexerClient.Start () [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.SimpleIndexerClient.Start () [0x00000] 

(Do:5163): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(Do:5163): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(Do:5163): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(Do:5163): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

It seems to be looking for applications I originally
 setup in Gnome do that I have not actually got around to installing.  (I thought gnome do might install them for me)

---

