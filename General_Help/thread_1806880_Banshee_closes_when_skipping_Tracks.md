---
title: "Banshee closes when skipping Tracks"
date: 2011-07-18
forum: General Help
---

### Post by Anno8 on 2011-07-18
Hi,
Banshee only recently started doing this:
When I play an song it works fine but if I click on skip it plays the next song for about 1-2 seconds then Banshee just closes. Also if I just let the song play (or skip to the end of the song) it also closes within 1-2 seconds of playing the next song. If I'm half way through a song I can click on another song to play it and it works fine through.
I've tried disabling all my extensions but that didn't make any difference.

If I launch Banshee by typing 'banshee' into Terminal (and then play a song and press the skip button) this is what the Terminal says: ```
[Info  23:04:34.467] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
[Info  23:04:44.674] Updating web proxy from GConf
[Info  23:04:45.528] All services are started 9.747955
** (Banshee:2497): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:2497): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:2497): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/anno/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:2497): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:2497): WARNING **: Error rescanning Purchased Music: No such file or directory
[Warn  23:04:56.020] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
** (Banshee:2497): DEBUG: Loading the real store page
[Info  23:04:58.665] nereid Client Started
[Info  23:04:59.801] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[Info  23:05:01.328] AppleDeviceSource is ignoring unmounted volume FACTORY_IMAGE
[Info  23:05:17.001] Uncached artwork size 234 requested
[Warn  23:05:20.430] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID = 6;
                  INSERT INTO CoreSmartPlaylistEntries
                    (EntryID, SmartPlaylistID, TrackID)
                    SELECT NULL, 6 as SmartPlaylistID, TrackId FROM CoreTracks,CoreArtists,CoreAlbums
                        WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID AND CoreTracks.PrimarySourceID = 1
                        AND (((CoreTracks.PlayCount = 0 AND CoreTracks.PlayCount IS NOT NULL) And (CoreTracks.SkipCount = 0 AND CoreTracks.SkipCount IS NOT NULL)))  ) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 

Unhandled Exception: Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID = 6;
                  INSERT INTO CoreSmartPlaylistEntries
                    (EntryID, SmartPlaylistID, TrackID)
                    SELECT NULL, 6 as SmartPlaylistID, TrackId FROM CoreTracks,CoreArtists,CoreAlbums
                        WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID AND CoreTracks.PrimarySourceID = 1
                        AND (((CoreTracks.PlayCount = 0 AND CoreTracks.PlayCount IS NOT NULL) And (CoreTracks.SkipCount = 0 AND CoreTracks.SkipCount IS NOT NULL)))  )
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 

```

EDIT: I'm using **U**buntu 11.04 not Lubuntu, how do I change it?

---

### Post by Anno8 on 2011-07-19
No one had this problem before?...

---

### Post by shashanksingh on 2011-07-19
It mite be a silly question, but are you sure the destination track you are playing has been properly mounted at the appropriate location?

I think the problem maybe banshee can't reach the track, the abve problem happens in my case, when my library has items that are not currently reachable.

---

### Post by Anno8 on 2011-07-19
Ok, I tried to re-import my music now it's showing this: 

[SIZE="3"]ENCOUNTERED A FATAL ERROR[/SIZE]
[SIZE="2"]Exception has been thrown by the target of an invocation.[/SIZE]
```
An unhandled exception was thrown: Object reference not set to an instance of an object

  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo].CheckCacheTable () [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.SqliteModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Database.BansheeModelCache`1[Banshee.Collection.Database.DatabaseArtistInfo]..ctor (Hyena.Data.Sqlite.HyenaSqliteConnection connection, System.String uuid, ICacheableDatabaseModel model, Hyena.Data.Sqlite.SqliteModelProvider`1 provider) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseFilterListModel`2[T,U]..ctor (System.String name, System.String label, Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Hyena.Data.Sqlite.HyenaSqliteConnection connection, Hyena.Data.Sqlite.SqliteModelProvider`1 provider, .U selectAllItem, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Database.DatabaseArtistListModel..ctor (Banshee.Sources.DatabaseSource source, Banshee.Collection.Database.DatabaseTrackListModel trackModel, Banshee.Database.BansheeDbConnection connection, System.String uuid) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource+<CreateFiltersFor>c__IteratorB.MoveNext () [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource.DatabaseSourceInitialize () [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order, Banshee.Sources.Source parent) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.DatabaseSource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Sources.PrimarySource..ctor (System.String generic_name, System.String name, System.String id, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Library.LibrarySource..ctor (System.String label, System.String name, Int32 order) [0x00000] in <filename unknown>:0 
  at Banshee.Library.MusicLibrarySource..ctor () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.Application.Run () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.38.10

Assembly Version Information:

Banshee.LastfmFingerprint (2.0.0.0)
gkeyfile-sharp (1.0.0.0)
Banshee.AudioCd (2.0.0.0)
Banshee.CoverArt (2.0.0.0)
Banshee.AmazonMp3 (2.0.0.0)
notify-sharp (0.4.0.0)
Banshee.SoundMenu (2.0.0.0)
Banshee.Mpris (2.0.0.0)
Lastfm (2.0.0.0)
Migo (2.0.0.0)
Banshee.Podcasting (2.0.0.0)
Banshee.Dap (2.0.0.0)
Banshee.MultimediaKeys (2.0.0.0)
Banshee.Lyrics (2.0.0.0)
Banshee.YouTube (2.0.0.0)
Banshee.WebBrowser (2.0.0.0)
Banshee.Wikipedia (2.0.0.0)
Banshee.Lastfm (2.0.0.0)
pango-sharp (2.12.0.0)
Banshee.Fixup (2.0.0.0)
Banshee.Widgets (2.0.0.0)
gio-sharp (2.14.0.0)
gudev-sharp (1.0.0.0)
Banshee.Gio (2.0.0.0)
Banshee.GStreamer (2.0.0.0)
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

Platform Information: Linux 2.6.38-10-generic i686 i386 GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

[/etc/debian_version]
squeeze/sid


```

---

### Post by Anno8 on 2011-07-19
Should I try to maybe re-install Banshee?

---

### Post by shashanksingh on 2011-07-19
It seems to be a database error, as I think banshee can't reach the files.
Do a clean re-install and try. Who knows may just sort it out itself

---

### Post by Anno8 on 2011-07-19
I went into Synaptic Software Manager and marked Banshee for re-installation, it still shows the same error.

---

### Post by mörgæs on 2011-07-20
This seems like a bug which should be reported in Launchpad (or confirmed, if it is already there).

[https://bugs.launchpad.net/ubuntu/+source/banshee/](https://bugs.launchpad.net/ubuntu/+source/banshee/)

---

### Post by Anno8 on 2011-07-23
No way to fix it?

---

### Post by Anno8 on 2011-07-23
Ok, I did a complete removal from Synaptic and marked to install again, that didn't work, still got fatal error.

Then I saw this thread: [http://ubuntuforums.org/showthread.php?t=1754843](http://ubuntuforums.org/showthread.php?t=1754843) and I did what it said in post [#3]("http://ubuntuforums.org/showpost.php?p=10827670&postcount=3") (deleting [COLOR="DarkRed"]/home/USER/.cache/.banshee-1[/COLOR] and [COLOR="DarkRed"]/home/USER/.config/banshee-1[/COLOR])

That seemed to fix the fatal error and the "Banshee closing when skipping tracks" issue.

---

