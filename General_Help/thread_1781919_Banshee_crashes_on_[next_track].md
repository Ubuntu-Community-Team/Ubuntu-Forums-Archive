---
title: "Banshee crashes on [next track]"
date: 2011-06-14
forum: General Help
---

### Post by Biopyro on 2011-06-14
I've been using banshee for a about a week, but it has recently started closing abruptly whenever it needs to play the next track. It will happily load the first track, and it is possible to play songs by selecting them, but allowing a song to finish, pressing next, previous or stop track causes it to crash.

I am running natty 11.04 and banshee 2.0.0

This is the output of banshee --debug. I pressed the next button within the player.
```
[1 Debug 10:19:45.509] Initializing GTK
[1 Debug 10:19:46.955] Post-Initializing GTK
[1 Debug 10:19:46.962] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 10:19:46.975] Using default gconf-base-key
[1 Debug 10:19:47.022] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 10:19:47.091] Core service started (DBusServiceManager, 0.000929)
[1 Debug 10:19:47.092] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 10:19:47.099] Core service started (DBusCommandService, 0.008504)
[1 Debug 10:19:47.126] Opened SQLite (version 3.7.4) connection to /home/guy/.config/banshee-1/banshee.db
[1 Debug 10:19:47.128] Core service started (DbConnection, 0.028314)
[1 Debug 10:19:47.148] Database version 43 is up to date
[1 Debug 10:19:47.205] Core service started (PreferenceService, 0.025402)
[1 Debug 10:19:47.213] Core service started (Network, 0.008287)
[1 Debug 10:19:47.214] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 10:19:47.214] Core service started (SourceManager, 0.00072)
[1 Debug 10:19:47.225] Core service started (MediaProfileManager, 0.000244)
[1 Debug 10:19:47.228] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 10:19:47.230] Core service started (PlayerEngine, 0.005428)
[1 Debug 10:19:47.320] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 10:19:47.322] Core service started (PlaybackController, 0.007359)
[1 Debug 10:19:47.342] Starting - Startup Job
[1 Debug 10:19:47.345] Core service started (JobScheduler, 0.022738)
[1 Debug 10:19:47.355] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 10:19:47.429] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 10:19:47.433] Core service started (HardwareManager, 0.088107)
[1 Debug 10:19:47.435] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 10:19:47.437] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 10:19:47.439] Core service started (CollectionIndexerService, 0.006219)
[1 Debug 10:19:47.441] Core service started (SaveTrackMetadataService, 0.001653)
[1 Debug 10:19:47.451] Adding icon theme search path: /usr/share/banshee/icons
[1 Debug 10:19:47.452] Core service started (GtkElementsService, 0.011053)
[1 Debug 10:19:47.454] Core service started (InterfaceActionService, 0.001645)
[1 Debug 10:19:47.539] Extension actions loaded: MetadataFixActions
[1 Debug 10:19:47.539] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 10:19:47.540] Album artwork path set to /home/guy/.cache/media-art
[1 Debug 10:19:47.574] Core service started (ArtworkManager, 0.034869)
[1 Debug 10:19:47.574] Core service started (BookmarksService, 0.000321)
[1 Debug 10:19:47.815] Adding context page wikipedia
[1 Debug 10:19:48.229] Adding context page lastfm-recommendations
[1 Debug 10:19:48.254] Adding context page YouTube
[1 Debug 10:19:48.619] Constructed Nereid interface: 0.962082
[1 Debug 10:19:48.751] Creating new surface cache for 90px images, capped at 0.74 MiB (24 items)
[1 Debug 10:19:48.796] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 10:19:48.796] Core service started (NereidPlayerInterface, 1.196165)
[1 Debug 10:19:48.813] Extension service started (GStreamerCoreService, 0.01703)
[1 Debug 10:19:48.818] Extension service started (BpmService, 0.004492)
[1 Debug 10:19:48.862] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 10:19:48.862] Extension service started (MultimediaKeysService, 0.043784)
[1 Debug 10:19:48.863] Extension service started (LibraryWatcherService, 0.001661)
[1 Debug 10:19:48.873] Extension service started (DapService, 0.009765)
[1 Debug 10:19:48.881] Extension service started (PodcastService, 0.008054)
[1 Debug 10:19:48.994] Audioscrobbler state: connected
[1 Debug 10:19:48.996] Extension service started (AudioscrobblerService, 0.113962)
[1 Info  10:19:48.998] Updating web proxy from GConf
[1 Debug 10:19:49.002] Direct connection, no proxy in use
[1 Debug 10:19:49.015] Extension service started (GnomeService, 0.018972)
[1 Debug 10:19:49.016] Extension service started (DaapService, 0.001153)
[1 Debug 10:19:49.068] Extension service started (NotificationAreaService, 0.052643)
[1 Debug 10:19:49.070] Extension service started (CoverArtService, 0.001592)
[1 Debug 10:19:49.078] Extension service started (MprisService, 0.007412)
[1 Debug 10:19:49.083] Extension service started (MiniModeService, 0.004972)
[1 Debug 10:19:49.123] Extension service started (AudioCdService, 0.040203)
[1 Info  10:19:49.124] All services are started 2.100494
[1 Debug 10:19:49.624] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 10:19:50.035] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 10:19:50.036] Extension source loaded: Play Queue
[1 Debug 10:19:50.072] Extension source loaded: Now Playing
[1 Debug 10:19:50.089] Extension source loaded: Last.fm
[1 Debug 10:19:50.109] Extension source loaded: Radio
[1 Debug 10:19:50.187] Extension source loaded: File System Queue
[1 Debug 10:19:50.197] Extension source loaded: Internet Archive
[1 Debug 10:19:50.212] Extension source loaded: Audiobooks
[1 Debug 10:19:50.215] Starting GTK main loop
[1 Debug 10:19:50.324] Growing surface cache for 90px images to 1.54 MiB (50 items)
[1 Debug 10:19:50.510] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 10:19:50.608] Creating Pango.Layout, configuring Cairo.Context
[1 Info  10:19:50.799] nereid Client Started
[1 Debug 10:19:50.804] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 10:19:50.819] (libbanshee:player) Stream volume supported: YES
[1 Debug 10:19:50.836] (libbanshee:player) Audiosink has volume: NO
[1 Debug 10:19:50.946] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 10:19:51.100] Player state change: NotReady -> Ready
[1 Debug 10:19:51.103] Loaded equalizer presets: 0.000135
[1 Debug 10:19:51.106] Selected equalizer: Rock
[1 Debug 10:19:51.110] Player state change: Ready -> Idle
[1 Debug 10:19:51.113] (libbanshee:player) Disabled ReplayGain
[1 Info  10:19:51.114] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[1 Debug 10:19:51.117] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 10:19:51.124] Core service started (LibraryImportManager, 0.003899)
[1 Debug 10:19:51.141] Started LibraryWatcher for Music (/home/guy/Music/)
[1 Debug 10:19:51.141] Started LibraryWatcher for Videos (/home/guy/Videos/)
[1 Debug 10:19:51.141] Delayed Initializating Banshee.Dap.DapService
[1 Debug 10:19:51.146] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 10:19:51.147] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 10:19:51.149] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 10:19:51.175] Delayed Initializating Banshee.Podcasting.PodcastService
[2 Info  10:19:51.283] AppleDeviceSource is ignoring unmounted volume 55 GB File system
[1 Debug 10:19:51.401] Delayed Initializating Banshee.Daap.DaapService
[3 Debug 10:19:51.426] Refreshing any podcasts that haven't been updated in over an hour
[4 Debug 10:19:51.527] DAAP Proxy listening for connections on port 8089
[1 Debug 10:19:52.440] Finished - Startup Job
[1 Debug 10:19:52.449] Starting - Downloading Cover Art
[5 Debug 10:19:52.456] Finished - Downloading Cover Art
[1 Debug 10:19:52.990] Querying model for track to play in song:Next mode
[1 Debug 10:19:53.030] Player state change: Idle -> Loading
[1 Debug 10:19:53.422] Player state change: Loading -> Loaded
[1 Debug 10:19:53.426] (libbanshee:player) [gapless] Triggering track-change signal
[1 Info  10:19:53.503] Uncached artwork size 241 requested
[1 Debug 10:19:53.509] Opening http://en.wikipedia.org/wiki/Torpeedoh
[1 Debug 10:19:53.541] Player state change: Loaded -> Playing
[1 Debug 10:19:53.576] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 10:19:53.576] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 10:19:54.550] TrackInfoDisplay RenderAnimation: 29.00 FPS
[1 Debug 10:19:54.550] TrackInfoDisplay RenderAnimation: 28.00 FPS
[1 Debug 10:19:57.449] Starting - Saving Metadata to File
[6 Debug 10:19:57.454] Finished - Saving Metadata to File
[7 Debug 10:20:06.255] Audioscrobbler sign-on succeeded - Session ID received
[1 Debug 10:20:06.442] Querying model for track to play in song:Next mode
[1 Debug 10:20:06.484] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[1 Debug 10:20:06.489] Player state change: Playing -> Idle
[1 Debug 10:20:06.493] Player state change: Idle -> Loading
[8 Debug 10:20:06.610] Exception executing command: DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID = 2;
                  INSERT INTO CoreSmartPlaylistEntries
                    (EntryID, SmartPlaylistID, TrackID)
                    SELECT NULL, 2 as SmartPlaylistID, TrackId FROM CoreTracks,CoreArtists,CoreAlbums
                        WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID AND CoreTracks.PrimarySourceID = 1
                        AND ((CoreTracks.PlayCount = 3 AND CoreTracks.PlayCount IS NOT NULL))  
[1 Debug 10:20:06.611] Player state change: Loading -> Loaded
[1 Debug 10:20:06.614] (libbanshee:player) [gapless] Triggering track-change signal
[8 Warn  10:20:06.614] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID = 2;
                  INSERT INTO CoreSmartPlaylistEntries
                    (EntryID, SmartPlaylistID, TrackID)
                    SELECT NULL, 2 as SmartPlaylistID, TrackId FROM CoreTracks,CoreArtists,CoreAlbums
                        WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID AND CoreTracks.PrimarySourceID = 1
                        AND ((CoreTracks.PlayCount = 3 AND CoreTracks.PlayCount IS NOT NULL))  ) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 

Unhandled Exception: Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID = 2;
                  INSERT INTO CoreSmartPlaylistEntries
                    (EntryID, SmartPlaylistID, TrackID)
                    SELECT NULL, 2 as SmartPlaylistID, TrackId FROM CoreTracks,CoreArtists,CoreAlbums
                        WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID AND CoreTracks.PrimarySourceID = 1
                        AND ((CoreTracks.PlayCount = 3 AND CoreTracks.PlayCount IS NOT NULL))  )
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 

```

---

### Post by Biopyro on 2011-06-30
Found the solution [here]("http://www.streamreader.org/askubuntu/questions/30185/banshee-encountered-a-fatal-error-(sqlite-error-11") and recovered my settings using the second reply in that thread. Simply had to search google for ```
"(sqlite error 11: database disk image is malformed)" banshee
```
to find a solution, apparently this fatal error is not uncommon and an automated fix  is being worked on.

[Mirror]("http://i.imgur.com/TRHkv.png") image in case that goes down.

---

### Post by ben2talk on 2011-07-17
So what is the temporary fix? delete the database?

Hours of work sorting out playlists!!!

UPDATE:
[http://i.imgur.com/TRHkv.png](http://i.imgur.com/TRHkv.png)

Thanks guys - this recovered everything for me.

---

### Post by thelastbiscuitinthetin on 2011-12-02
Having the same problem. It happens randomly while my playlist is on automatic shuffle, repeat all. Quite annoying. Running Ubuntu 11.10.

---

