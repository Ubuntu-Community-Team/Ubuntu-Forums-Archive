---
title: "Banshee crashes immediately after startup"
date: 2011-01-07
forum: General Help
---

### Post by quick_nick on 2011-01-07
I don't know if this is related but It first crashed after I attempted to add a podcast.  I have since deleted all videos/music/podcasts ect and deleted the ~/.config/banshe-1 folder.  It still is crashing.  I have tried complete removal and re-instillation many times.

Here is my debug
```
** Running Mono with --debug   **
[1 Info  16:15:47.621] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[1 Debug 16:15:47.655] Initializing GTK
[1 Debug 16:15:49.659] Post-Initializing GTK
[1 Debug 16:15:49.689] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 16:15:49.714] Using default gconf-base-key
[1 Debug 16:15:49.764] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 16:15:49.872] Core service started (DBusServiceManager, 0.001785)
[1 Debug 16:15:49.876] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 16:15:49.890] Core service started (DBusCommandService, 0.017297)
[1 Debug 16:15:49.997] Opened SQLite (version 3.7.2) connection to /home/nick/.config/banshee-1/banshee.db
[1 Debug 16:15:49.998] Core service started (DbConnection, 0.107754)
[1 Debug 16:15:50.006] Database version 43 is up to date
[1 Info  16:15:50.036] Starting collection of anonymous usage data
[1 Debug 16:15:50.091] Core service started (PreferenceService, 0.034586)
[1 Debug 16:15:50.102] Core service started (Network, 0.010579)
[1 Debug 16:15:50.103] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 16:15:50.104] Core service started (SourceManager, 0.001162)
[1 Debug 16:15:50.117] Core service started (MediaProfileManager, 0.000409)
[1 Debug 16:15:50.121] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 16:15:50.124] Core service started (PlayerEngine, 0.006512)
[1 Debug 16:15:50.154] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 16:15:50.155] Core service started (PlaybackController, 0.004578)
[1 Debug 16:15:50.167] Starting - Startup Job
[1 Debug 16:15:50.168] Core service started (JobScheduler, 0.012779)
[1 Debug 16:15:50.194] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 16:15:50.247] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 16:15:50.250] Core service started (HardwareManager, 0.081878)
[1 Debug 16:15:50.255] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 16:15:50.258] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 16:15:50.261] Core service started (CollectionIndexerService, 0.010209)
[1 Debug 16:15:50.263] Core service started (SaveTrackMetadataService, 0.002402)
[1 Debug 16:15:50.277] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 16:15:50.279] Core service started (GtkElementsService, 0.015136)
[1 Debug 16:15:50.281] Core service started (InterfaceActionService, 0.002091)
[1 Debug 16:15:50.427] Extension actions loaded: MetadataFixActions
[1 Debug 16:15:50.428] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 16:15:50.434] Album artwork path set to /home/nick/.cache/media-art
[1 Debug 16:15:50.463] Core service started (ArtworkManager, 0.03537)
[1 Debug 16:15:50.464] Core service started (BookmarksService, 0.000255)
[1 Debug 16:15:50.748] Adding context page lastfm-recommendations
[1 Debug 16:15:50.779] Adding context page wikipedia
[1 Debug 16:15:51.205] Constructed Nereid interface: 0.701292
[1 Debug 16:15:51.333] Creating new surface cache for 90px images, capped at 0.56 MiB (18 items)
[1 Debug 16:15:51.408] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 16:15:51.408] Core service started (NereidPlayerInterface, 0.944115)
[1 Debug 16:15:51.767] Extension service started (GStreamerCoreService, 0.357274)
[1 Debug 16:15:51.777] Extension service started (BpmService, 0.010511)
[1 Debug 16:15:51.783] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 16:15:51.783] Extension service started (MultimediaKeysService, 0.005049)
[1 Debug 16:15:51.785] Extension service started (LibraryWatcherService, 0.002181)
[1 Debug 16:15:51.790] Extension service started (PodcastService, 0.004302)
[1 Debug 16:15:51.792] Extension service started (DapService, 0.001833)
[1 Debug 16:15:51.817] Audioscrobbler state: connected
[1 Debug 16:15:51.820] Extension service started (AudioscrobblerService, 0.02835)
[1 Debug 16:15:51.826] Extension service started (LastfmStreamingService, 0.005492)
[1 Debug 16:15:51.828] Extension service started (DaapService, 0.001978)
[1 Info  16:15:51.837] Updating web proxy from GConf
[1 Debug 16:15:51.843] Direct connection, no proxy in use
[1 Debug 16:15:51.865] Extension service started (GnomeService, 0.037164)
[1 Debug 16:15:51.869] Extension service started (AmazonMp3DownloaderService, 0.0029)
[1 Debug 16:15:52.006] Extension service started (NotificationAreaService, 0.136627)
[1 Debug 16:15:52.009] Extension service started (CoverArtService, 0.003473)
[1 Debug 16:15:52.054] Extension service started (AudioCdService, 0.044653)
[1 Info  16:15:52.056] All services are started 2.29036
[1 Debug 16:15:52.619] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 16:15:52.620] Extension source loaded: Play Queue
[1 Debug 16:15:52.673] Extension source loaded: Last.fm
[1 Debug 16:15:52.683] Extension source loaded: Now Playing
[1 Debug 16:15:52.705] Extension source loaded: Radio
[1 Debug 16:15:52.730] Extension source loaded: File System Queue
[1 Debug 16:15:52.741] Extension source loaded: Amazon MP3 Store
[1 Debug 16:15:52.752] Extension source loaded: Miro Guide
[1 Debug 16:15:52.770] Extension source loaded: Internet Archive
[1 Debug 16:15:52.817] Extension source loaded: Audiobooks, etc
[1 Debug 16:15:52.825] Starting GTK main loop
[1 Debug 16:15:53.124] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 16:15:53.201] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 16:15:53.216] Creating Pango.Layout, configuring Cairo.Context
[1 Info  16:15:53.385] nereid Client Started
[1 Debug 16:15:53.390] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 16:15:53.397] (libbanshee:player) Stream volume supported: YES
[1 Debug 16:15:53.400] (libbanshee:player) Audiosink has volume: NO
[1 Debug 16:15:53.410] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 16:15:53.496] Player state change: NotReady -> Ready
[1 Debug 16:15:53.503] Loaded equalizer presets: 0.000213
[1 Debug 16:15:53.509] Selected equalizer: Rock
[1 Debug 16:15:53.516] Player state change: Ready -> Idle
[1 Debug 16:15:53.522] (libbanshee:player) Disabled ReplayGain
[1 Debug 16:15:53.530] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 16:15:53.544] Core service started (LibraryImportManager, 0.007284)
[1 Debug 16:15:53.579] Started LibraryWatcher for Music (/home/nick/Music/)
[1 Debug 16:15:53.586] Started LibraryWatcher for Videos (/home/nick/Videos/)
[1 Debug 16:15:53.591] Starting
[1 Debug 16:15:53.631] Starting
[1 Debug 16:15:53.646] Delayed Initializating Banshee.Podcasting.PodcastService
[2 Debug 16:15:53.655] Finished
[3 Debug 16:15:53.655] Finished
[1 Debug 16:15:53.742] Delayed Initializating Banshee.Dap.DapService
[1 Debug 16:15:53.757] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 16:15:53.759] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 16:15:53.762] Dap support extension loaded: Banshee.Dap.Karma
[1 Debug 16:15:53.763] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 16:15:53.770] Delayed Initializating Banshee.Daap.DaapService
[4 Debug 16:15:53.790] Refreshing any podcasts that haven't been updated in over an hour
[5 Info  16:15:53.821] AppleDeviceSource is ignoring unmounted volume C drive
[5 Warn  16:15:53.845] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[6 Debug 16:15:53.975] DAAP Proxy listening for connections on port 8089
[1 Debug 16:15:54.840] Finished - Startup Job
[1 Debug 16:15:54.841] Starting - Downloading Cover Art
[7 Debug 16:15:54.844] Finished - Downloading Cover Art
[1 Debug 16:15:56.241] Starting - Detecting BPM
[8 Debug 16:15:56.242] Finished - Detecting BPM

Stacktrace:

  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at (wrapper managed-to-native) System.Net.Dns.GetHostByName_internal (string,string&,string[]&,string[]&) <0x00004>
  at System.Net.Dns.GetHostByName (string) <IL 0x00018, 0x00038>
  at System.Net.ServicePoint.get_HostEntry () <IL 0x000a6, 0x00137>
  at System.Net.WebConnection.Connect (System.Net.HttpWebRequest) <IL 0x00086, 0x0010b>
  at System.Net.WebConnection.InitConnection (object) <IL 0x0003f, 0x00129>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <IL 0x0001e, 0x00046>

Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x810ffeb]
	[0xb781a40c]
	/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x3f) [0xaab6d61f]
	/lib/libc.so.6(gethostbyname2_r+0x1c5) [0xb766c1a5]
	/lib/libc.so.6(+0xa782c) [0xb762b82c]
	/lib/libc.so.6(getaddrinfo+0x165) [0xb762d3b5]
	banshee-1() [0x8158c93]
	[0xaafcfb63]
	[0xaafcfa81]
	[0xaafcf8a0]
	[0xaafcf2dc]
	[0xaafcefb2]
	[0xb68bb0bf]
	banshee-1() [0x8061328]
	banshee-1(mono_runtime_invoke+0x40) [0x813c890]
	banshee-1(mono_runtime_invoke_array+0x2a4) [0x81421a4]
	banshee-1() [0x814266e]
	banshee-1() [0x81d2341]
	banshee-1() [0x81d2858]
	banshee-1() [0x81b11db]
	banshee-1() [0x81e8e4e]
	banshee-1() [0x8214f85]
	/lib/libpthread.so.0(+0x5cc9) [0xb770ccc9]
	/lib/libc.so.6(clone+0x5e) [0xb765469e]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```


Here is what happens if i run it with my C drive mounted
```
** Running Mono with --debug   **
[1 Info  16:19:21.093] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[1 Debug 16:19:21.128] Initializing GTK
[1 Debug 16:19:23.148] Post-Initializing GTK
[1 Debug 16:19:23.179] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 16:19:23.203] Using default gconf-base-key
[1 Debug 16:19:23.253] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 16:19:23.358] Core service started (DBusServiceManager, 0.001738)
[1 Debug 16:19:23.361] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 16:19:23.375] Core service started (DBusCommandService, 0.016285)
[1 Debug 16:19:23.487] Opened SQLite (version 3.7.2) connection to /home/nick/.config/banshee-1/banshee.db
[1 Debug 16:19:23.488] Core service started (DbConnection, 0.113826)
[1 Debug 16:19:23.494] Database version 43 is up to date
[1 Info  16:19:23.518] Starting collection of anonymous usage data
[1 Debug 16:19:23.569] Core service started (PreferenceService, 0.03034)
[1 Debug 16:19:23.579] Core service started (Network, 0.009878)
[1 Debug 16:19:23.580] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 16:19:23.581] Core service started (SourceManager, 0.001138)
[1 Debug 16:19:23.594] Core service started (MediaProfileManager, 0.000461)
[1 Debug 16:19:23.598] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 16:19:23.601] Core service started (PlayerEngine, 0.006373)
[1 Debug 16:19:23.625] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 16:19:23.627] Core service started (PlaybackController, 0.004365)
[1 Debug 16:19:23.639] Starting - Startup Job
[1 Debug 16:19:23.640] Core service started (JobScheduler, 0.012905)
[1 Debug 16:19:23.665] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 16:19:23.717] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 16:19:23.720] Core service started (HardwareManager, 0.079689)
[1 Debug 16:19:23.724] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 16:19:23.726] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 16:19:23.728] Core service started (CollectionIndexerService, 0.008338)
[1 Debug 16:19:23.731] Core service started (SaveTrackMetadataService, 0.002439)
[1 Debug 16:19:23.745] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 16:19:23.747] Core service started (GtkElementsService, 0.015509)
[1 Debug 16:19:23.749] Core service started (InterfaceActionService, 0.002109)
[1 Debug 16:19:23.904] Extension actions loaded: MetadataFixActions
[1 Debug 16:19:23.905] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 16:19:23.909] Album artwork path set to /home/nick/.cache/media-art
[1 Debug 16:19:23.939] Core service started (ArtworkManager, 0.033954)
[1 Debug 16:19:23.940] Core service started (BookmarksService, 0.000316)
[1 Debug 16:19:24.227] Adding context page lastfm-recommendations
[1 Debug 16:19:24.260] Adding context page wikipedia
[1 Debug 16:19:24.718] Constructed Nereid interface: 0.734055
[1 Debug 16:19:24.846] Creating new surface cache for 90px images, capped at 0.56 MiB (18 items)
[1 Debug 16:19:24.960] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 16:19:24.960] Core service started (NereidPlayerInterface, 1.020088)
[1 Debug 16:19:24.992] Extension service started (GStreamerCoreService, 0.030812)
[1 Debug 16:19:25.004] Extension service started (BpmService, 0.011077)
[1 Debug 16:19:25.010] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 16:19:25.010] Extension service started (MultimediaKeysService, 0.005939)
[1 Debug 16:19:25.017] Extension service started (LibraryWatcherService, 0.007146)
[1 Debug 16:19:25.022] Extension service started (PodcastService, 0.003857)
[1 Debug 16:19:25.024] Extension service started (DapService, 0.001831)
[1 Debug 16:19:25.045] Audioscrobbler state: connected
[1 Debug 16:19:25.048] Extension service started (AudioscrobblerService, 0.023581)
[1 Debug 16:19:25.053] Extension service started (LastfmStreamingService, 0.005119)
[1 Debug 16:19:25.055] Extension service started (DaapService, 0.001792)
[1 Info  16:19:25.060] Updating web proxy from GConf
[1 Debug 16:19:25.066] Direct connection, no proxy in use
[1 Debug 16:19:25.088] Extension service started (GnomeService, 0.032039)
[1 Debug 16:19:25.091] Extension service started (AmazonMp3DownloaderService, 0.002745)
[1 Debug 16:19:25.216] Extension service started (NotificationAreaService, 0.124833)
[1 Debug 16:19:25.220] Extension service started (CoverArtService, 0.003391)
[1 Debug 16:19:25.256] Extension service started (AudioCdService, 0.036454)
[1 Info  16:19:25.258] All services are started 2.003201
[1 Debug 16:19:25.774] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 16:19:25.775] Extension source loaded: Play Queue
[1 Debug 16:19:25.831] Extension source loaded: Last.fm
[1 Debug 16:19:25.840] Extension source loaded: Now Playing
[1 Debug 16:19:25.863] Extension source loaded: Radio
[1 Debug 16:19:25.899] Extension source loaded: File System Queue
[1 Debug 16:19:25.920] Extension source loaded: Amazon MP3 Store
[1 Debug 16:19:25.930] Extension source loaded: Miro Guide
[1 Debug 16:19:25.947] Extension source loaded: Internet Archive
[1 Debug 16:19:25.982] Extension source loaded: Audiobooks, etc
[1 Debug 16:19:25.990] Starting GTK main loop
[1 Debug 16:19:26.327] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 16:19:26.403] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 16:19:26.420] Creating Pango.Layout, configuring Cairo.Context
[1 Info  16:19:26.585] nereid Client Started
[1 Debug 16:19:26.590] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 16:19:26.596] (libbanshee:player) Stream volume supported: YES
[1 Debug 16:19:26.600] (libbanshee:player) Audiosink has volume: NO
[1 Debug 16:19:26.609] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 16:19:26.696] Player state change: NotReady -> Ready
[1 Debug 16:19:26.703] Loaded equalizer presets: 0.000212
[1 Debug 16:19:26.713] Selected equalizer: Rock
[1 Debug 16:19:26.720] Player state change: Ready -> Idle
[1 Debug 16:19:26.726] (libbanshee:player) Disabled ReplayGain
[1 Debug 16:19:26.737] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 16:19:26.751] Core service started (LibraryImportManager, 0.008139)
[1 Debug 16:19:26.790] Started LibraryWatcher for Music (/home/nick/Music/)
[1 Debug 16:19:26.794] Started LibraryWatcher for Videos (/home/nick/Videos/)
[1 Debug 16:19:26.799] Starting
[1 Debug 16:19:26.841] Starting
[1 Debug 16:19:26.855] Delayed Initializating Banshee.Podcasting.PodcastService
[2 Debug 16:19:26.877] Finished
[3 Debug 16:19:26.882] Finished
[1 Debug 16:19:26.979] Delayed Initializating Banshee.Dap.DapService
[1 Debug 16:19:26.990] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 16:19:26.994] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 16:19:26.998] Dap support extension loaded: Banshee.Dap.Karma
[1 Debug 16:19:27.000] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 16:19:27.007] Delayed Initializating Banshee.Daap.DaapService
[4 Debug 16:19:27.031] Refreshing any podcasts that haven't been updated in over an hour
[5 Debug 16:19:27.315] DAAP Proxy listening for connections on port 8089
[1 Debug 16:19:28.060] Finished - Startup Job
[1 Debug 16:19:28.061] Starting - Downloading Cover Art
[6 Debug 16:19:28.064] Finished - Downloading Cover Art
[1 Debug 16:19:29.442] Starting - Detecting BPM
[7 Debug 16:19:29.444] Finished - Detecting BPM
Stacktrace:


Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x810ffeb]
	[0xb77b840c]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```
I do not nor have I ever attached an apple device to this machine so I don't know why its complaining about that.  It almost looks like it seems to have a hard on for my c drive being mounted.  If i run banshee as root it will not crash but then I need to have all my music in root and I shouldn't have to open banshee as root everytime.

PLEASE HELP!!  I am kind of new to the Ubuntu experience but I can Google to figure out how to do things or ask follow up questions if absolutely necessary.

---

### Post by quick_nick on 2011-01-07
I fixed my problem using [this fix]("http://ubuntuforums.org/showthread.php?t=1554252&page=2")

---

