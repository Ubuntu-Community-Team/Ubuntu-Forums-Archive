---
title: "gtkpod Issues"
date: 2006-02-05
forum: General Help
---

### Post by HokeyFry on 2006-02-05
For starters, this is NOT a thread for trying to get an iPod to work with gtkpod (I have seen a few like that). Actually, my iPod works quite well with gtkpod. Unfortunately, I have a couple of issues with it and was wondering if anyone knows how to overcome them.

When I view playlists, they come up in a random order (I believe the last random order that they were playing in on the iPod). Is there a way to fix this?

The other issue I have is when I try to load the iPod into gtkpod I get this message:

```
iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match
checksum in extended information file
'/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take
a long time.
```

Then it goes thru each song and it takes about two minutes before they show up on the screen, as I have about 2600 songs on it. Does anyone know the problem with this?


Also, if anyone does not know how to fix this, but does know a program that manages an iPod (not amaroK) that does not have these issues, I accept that as well. Thanks in advance for your help.

---

### Post by RAOF on 2006-02-05
You may have some luck with [banshee](www.banshee-project.org).  That appears to handle iPods pretty well (and is also a nice music library/player).

---

### Post by HokeyFry on 2006-02-05
ok after looking at banshee i decided i liked it and now i have it. but when I start it up with the iPod in the computer, OR if i plug it in while banshee is running, it crashes with this error:

```
Unhandled Exception: IPod.DatabaseReadException: Detected unsupported database version 16
in <0x001b7> IPod.DatabaseRecord:Read (IPod.DatabaseRecord db, System.IO.BinaryReader reader)
in <0x0010e> IPod.SongDatabase:Reload ()
in <0x000b2> IPod.SongDatabase:.ctor (IPod.Device device)
in <0x00033> IPod.Device:get_SongDatabase ()
in [0x00023] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Library.cs:316) Banshee.IpodSource:Refresh ()
in [0x00039] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Library.cs:308) Banshee.IpodSource:.ctor (IPod.Device device)
in [0x000b8] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/SourceView.cs:204) Banshee.SourceView:RefreshList ()
in [0x00139] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/SourceView.cs:162) Banshee.SourceView:.ctor ()
in [0x0025d] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/PlayerInterface.cs:264) Banshee.PlayerUI:BuildWindow ()
in [0x00066] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/PlayerInterface.cs:133) Banshee.PlayerUI:.ctor ()
in [0x0010d] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Main.cs:79) Banshee.BansheeEntry:Main (System.String[] args)
```

Anyone know how to fix this?

---

### Post by RAOF on 2006-02-05
Hm.  You're running version 0.9.7.  That's a bit old.  I know it's the version in the repositories, but Banshee is being developed pretty actively, so there's a lot of new stuff/bugfixes coming in frequently.  You might want to try adding the line
```

deb http://apt.filefind.net/ breezy main contrib non-free
``` to your sources.list - this (3rd party) repository contains up-to-date banshee builds (as well as other mono stuff).

After adding that line, run "sudo apt-get update", and then install the latest Banshee through your preferred apt frontend (like Synaptic).  It might be called something a little different (like banshee-filefind, perhaps).

---

### Post by binarymelon on 2006-02-06
RAOF, I'm going to ask this here because it's sort of related.  Do you know of a version of beagle that will run with the mono from that repository.  The one I had installed needed to be removed to install banshee and it's dependencies.

---

### Post by HokeyFry on 2006-02-06
ok... added the new repository from filefind, downloaded banshee. When I run from terminal, I get a couple of warnings, no sweat. but if my iPod is connected, i get another error:

```
Unhandled Exception: System.DllNotFoundException: libdbus-1.so.2
in (wrapper managed-to-native) Hal.DBusError:dbus_error_init (intptr)
in [0x00033] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/hal-sharp/DBusError.cs:39) Hal.DBusError:.ctor ()
in [0x00000] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/hal-sharp/HalDevice.cs:191) Hal.Device:set_WatchProperties (Boolean value)
in [0x0008f] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Banshee.Base/Dap/DapCore.cs:178) Banshee.Dap.DapCore:AddDevice (Hal.Device device, System.Type type)
in [0x0001e] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Banshee.Base/Dap/DapCore.cs:161) Banshee.Dap.DapCore:AddDevice (Hal.Device device)
in <0x0000d> Banshee.Dap.DapCore:<#AnonymousMethod>2 (System.Object o, Hal.DeviceAddedArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_DeviceAddedArgs (object,Hal.DeviceAddedArgs)
in [0x0002f] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Banshee.Base/HalCore.cs:63) Banshee.Base.HalCore:HalDeviceAdded (IntPtr contextRaw, IntPtr udiRaw)
in (wrapper native-to-managed) Banshee.Base.HalCore:HalDeviceAdded (intptr,intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in [0x001e3] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Main.cs:95) Banshee.BansheeEntry:Startup (System.String[] args)
in [0x00001] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Main.cs:57) Banshee.BansheeEntry:Main (System.String[] args)
```

why does this keep happening? my family actually likes banshee for music, but if I cant get the ipod to work with it, then they will make us go back to windows because of it (which is kind of a "rash" thing to do over a small problem.)

If this helps any, I am pretty sure my iPod is updated to the latest update.

---

### Post by RAOF on 2006-02-06
Well, it's complaining about not being able to find the DBus library.  I'm not sure why it would only bomb out while the iPod's connected, though.

Maybe you could install libdbus-1-2 from the filefind repository?

@binarymelon - I don't know about a version of beagle that will run with the mono from the filefind repo.  I'm running Dapper, and I've had to build-my-own beagle (it's actually pretty simple) 'cause the Dapper package is broken at the moment.

---

### Post by dudus on 2006-02-06
The best way I found to manage my ipod was the gnupod tools scripts. They're a set of CLI scripts. Most GTK ipod managers don't seem to work well with ipodshuffle. 

Couse of the small size I often have to remove the files and fill it again... and I wasn't lucky performing such tasks in gtkpod.

---

### Post by wilsonisme on 2006-02-06
Well, just to add in my experiance with GTKpod, I own a shuffle, I am using the GTKpod from the standard repo's, and it has never failed me.:-k

---

### Post by GreySim on 2006-02-07
I too am having dbus-related problems.  I think what's happening is Banshee wants a newer version of dbus than what is available in Ubuntu right now.  I filed a [bug against Banshee](http://bugzilla.gnome.org/show_bug.cgi?id=329966), but it appears that dbus is the problem here.

---

### Post by closeyourwindows on 2006-02-07
one thing that I had to do was change the name in the preferneces from /media/ipod to /media/<name on ipod> and then close the app and bring it back up.  it should recognize it then.  to make sure of the name that it is listed as, change directory to /media and then ls.  it should say either ipod or whatever you named it.

  I also use amarok to transfer music and did not have to change any settings.  the other alternative is wine.

---

