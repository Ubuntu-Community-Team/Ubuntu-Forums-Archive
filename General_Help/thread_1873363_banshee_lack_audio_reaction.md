---
title: "banshee lack audio reaction"
date: 2011-11-01
forum: General Help
---

### Post by saltcushy on 2011-11-01
When I changed on Lubuntu Banshe audio crashed. I wanna this player because him let SAVE special metadata like eg * , **,***,****,*****.
Doesn't exist similar  implemented option?
                         > [LEFT]banshee --debug [/LEFT]
    [LEFT]** Running Mono with --debug   **[/LEFT]
    [LEFT][1 Info  20:21:01.217] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC][/LEFT]
    [LEFT][1 Debug 20:21:01.236] Initializing GTK[/LEFT]
    [LEFT][1 Debug 20:21:02.115] Post-Initializing GTK[/LEFT]
    [LEFT][1 Debug 20:21:02.124] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)[/LEFT]
    [LEFT][1 Debug 20:21:02.130] Using default gconf-base-key[/LEFT]
    [LEFT][1 Debug 20:21:02.173] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner[/LEFT]
    [LEFT][1 Debug 20:21:02.232] Core service started (DBusServiceManager, 0,001249)[/LEFT]
    [LEFT][1 Debug 20:21:02.234] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee[/LEFT]
    [LEFT][1 Debug 20:21:02.241] Core service started (DBusCommandService, 0,00823)[/LEFT]
    [LEFT][1 Debug 20:21:02.274] Opened SQLite (version 3.7.7) connection to /home/lbu/.config/banshee-1/banshee.db[/LEFT]
    [LEFT][1 Debug 20:21:02.275] Core service started (DbConnection, 0,034212)[/LEFT]
    [LEFT][1 Debug 20:21:02.280] Database version 44 is up to date[/LEFT]
    [LEFT][1 Debug 20:21:02.314] Core service started (PreferenceService, 0,012489)[/LEFT]
    [LEFT][1 Debug 20:21:02.330] Core service started (Network, 0,015553)[/LEFT]
    [LEFT][1 Debug 20:21:02.330] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee[/LEFT]
    [LEFT][1 Debug 20:21:02.330] Core service started (SourceManager, 0,000704)[/LEFT]
    [LEFT][1 Debug 20:21:02.335] Core service started (MediaProfileManager, 0,000233)[/LEFT]
    [LEFT][1 Debug 20:21:02.340] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee[/LEFT]
    [LEFT][1 Debug 20:21:02.342] Core service started (PlayerEngine, 0,006053)[/LEFT]
    [LEFT][1 Debug 20:21:02.365] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee[/LEFT]
    [LEFT][1 Debug 20:21:02.367] Core service started (PlaybackController, 0,003322)[/LEFT]
    [LEFT][1 Debug 20:21:02.372] Starting - Startup Job[/LEFT]
    [LEFT][1 Debug 20:21:02.372] Core service started (JobScheduler, 0,00514)[/LEFT]
    [LEFT][1 Debug 20:21:02.390] IO provider extension loaded (Banshee.IO.Gio.Provider)[/LEFT]
    [LEFT][1 Debug 20:21:02.433] Loaded HardwareManager backend: Banshee.Hardware.Gio[/LEFT]
    [LEFT][1 Debug 20:21:02.435] Core service started (HardwareManager, 0,0623)[/LEFT]
    [LEFT][1 Debug 20:21:02.437] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner[/LEFT]
    [LEFT][1 Debug 20:21:02.438] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer[/LEFT]
    [LEFT][1 Debug 20:21:02.440] Core service started (CollectionIndexerService, 0,004633)[/LEFT]
    [LEFT][1 Debug 20:21:02.441] Core service started (SaveTrackMetadataService, 0,00124)[/LEFT]
    [LEFT][1 Debug 20:21:02.457] Adding icon theme search path: /usr/share/banshee/icons[/LEFT]
    [LEFT][1 Debug 20:21:02.458] Core service started (GtkElementsService, 0,017045)[/LEFT]
    [LEFT][1 Debug 20:21:02.459] Core service started (InterfaceActionService, 0,001175)[/LEFT]
    [LEFT][1 Debug 20:21:02.554] Extension actions loaded: MetadataFixActions[/LEFT]
    [LEFT][1 Debug 20:21:02.555] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee[/LEFT]
    [LEFT][1 Debug 20:21:02.556] Album artwork path set to /home/lbu/.cache/media-art[/LEFT]
    [LEFT][1 Debug 20:21:02.579] Core service started (ArtworkManager, 0,024145)[/LEFT]
    [LEFT][1 Debug 20:21:02.579] Core service started (BookmarksService, 0,000128)[/LEFT]
    [LEFT][1 Debug 20:21:02.801] Adding context page lastfm-recommendations[/LEFT]
    [LEFT][1 Debug 20:21:02.824] Adding context page wikipedia[/LEFT]
    [LEFT][1 Debug 20:21:03.019] Constructed Nereid interface: 0,399045[/LEFT]
    [LEFT][1 Debug 20:21:03.103] Creating new surface cache for 90px images, capped at 0,93 MiB (30 items)[/LEFT]
    [LEFT][1 Debug 20:21:03.152] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee[/LEFT]
    [LEFT][1 Debug 20:21:03.153] Core service started (NereidPlayerInterface, 0,555663)[/LEFT]
    [LEFT][1 Debug 20:21:03.169] Audioscrobbler state: disconnected[/LEFT]
    [LEFT][1 Debug 20:21:03.183] Extension service started (AudioscrobblerService, 0,028863)[/LEFT]
    [LEFT][1 Debug 20:21:03.184] Extension service started (DapService, 0,00088)[/LEFT]
    [LEFT][1 Debug 20:21:03.187] Extension service started (AmazonMp3DownloaderService, 0,002009)[/LEFT]
    [LEFT][1 Debug 20:21:03.241] Extension service started (AudioCdService, 0,050439)[/LEFT]
    [LEFT][1 Debug 20:21:03.246] Extension service started (DaapService, 0,000911)[/LEFT]
    [LEFT][1 Debug 20:21:03.287] Extension service started (GStreamerCoreService, 0,039025)[/LEFT]
    [LEFT][1 Debug 20:21:03.295] Extension service started (MprisService, 0,007826)[/LEFT]
    [LEFT][1 Debug 20:21:03.302] Extension service started (SoundMenuService, 0,007126)[/LEFT]
    [LEFT][1 Debug 20:21:03.332] Extension service started (EmusicService, 0,029692)[/LEFT]
    [LEFT][1 Info  20:21:03.336] Updating web proxy from GConf[/LEFT]
    [LEFT][1 Debug 20:21:03.350] Direct connection, no proxy in use[/LEFT]
    [LEFT][1 Debug 20:21:03.363] Extension service started (GnomeService, 0,031026)[/LEFT]
    [LEFT][1 Debug 20:21:03.373] Extension service started (BpmService, 0,01025)[/LEFT]
    [LEFT][1 Warn  20:21:03.385] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')[/LEFT]
    [LEFT]  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 [/LEFT]
    [LEFT]  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 [/LEFT]
    [LEFT][1 Warn  20:21:03.385] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.[/LEFT]
    [LEFT][1 Debug 20:21:03.388] Extension service started (CoverArtService, 0,002195)[/LEFT]
    [LEFT][1 Debug 20:21:03.389] Extension service started (PodcastService, 0,001534)[/LEFT]
    [LEFT][1 Warn  20:21:03.392] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')[/LEFT]
    [LEFT]  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 [/LEFT]
    [LEFT]  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 [/LEFT]
    [LEFT][1 Warn  20:21:03.392] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.[/LEFT]
    [LEFT][1 Info  20:21:03.392] All services are started 1,218407[/LEFT]
    [LEFT][1 Debug 20:21:03.679] Creating Pango.Layout, configuring Cairo.Context[/LEFT]
    [LEFT][1 Debug 20:21:03.784] Extension source loaded: Last.fm[/LEFT]
    [LEFT][1 Debug 20:21:03.873] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee[/LEFT]
    [LEFT][1 Debug 20:21:03.874] Extension source loaded: Kolejka odtwarzania[/LEFT]
    [LEFT][1 Debug 20:21:03.880] Extension source loaded: Teraz odtwarzany[/LEFT]
    [LEFT][1 Debug 20:21:03.915] Extension source loaded: Audiobooki[/LEFT]
    [LEFT][1 Debug 20:21:03.936] Extension source loaded: Radio[/LEFT]
    [LEFT][1 Debug 20:21:03.951] Extension source loaded: Internet Archive[/LEFT]
    [LEFT][1 Debug 20:21:03.975] Extension source loaded: Kolejka systemu plików[/LEFT]
    [LEFT][1 Info  20:21:03.981] AmazonMP3 store redirect URL: [https://one.ubuntu.com/music/store/amz/](https://one.ubuntu.com/music/store/amz/)[/LEFT]
    [LEFT][1 Debug 20:21:03.984] Extension source loaded: Sklep Amazon MP3[/LEFT]
    [LEFT][1 Debug 20:21:03.990] Extension source loaded: Przewodnik Miro[/LEFT]
    [LEFT][1 Debug 20:21:04.005] Starting GTK main loop[/LEFT]
    [LEFT][1 Debug 20:21:04.205] Creating Pango.Layout, configuring Cairo.Context[/LEFT]
    [LEFT][1 Debug 20:21:04.242] Creating Pango.Layout, configuring Cairo.Context[/LEFT]
    [LEFT][1 Info  20:21:04.339] nereid Client Started[/LEFT]
    [LEFT][1 Debug 20:21:04.341] Delayed Initializating Banshee.MediaEngine.PlayerEngineService[/LEFT]
    [LEFT]Cannot connect to server socket err = Nie ma takiego pliku ani katalogu[/LEFT]
    [LEFT]Cannot connect to server socket[/LEFT]
    [LEFT]jack server is not running or cannot be started[/LEFT]
    [LEFT][1 Debug 20:21:04.358] (libbanshee:player) Audiosink has volume: NO[/LEFT]
    [LEFT][1 Debug 20:21:04.372] (libbanshee:player) Using system (gst-plugins-good) equalizer element[/LEFT]
    [LEFT][1 Debug 20:21:04.427] Player state change: NotReady -> Ready[/LEFT]
    [LEFT][1 Debug 20:21:04.431] Loaded equalizer presets: 0,000181[/LEFT]
    [LEFT][1 Debug 20:21:04.445] Selected equalizer: Rock[/LEFT]
    [LEFT][1 Debug 20:21:04.450] Player state change: Ready -> Idle[/LEFT]
    [LEFT][1 Debug 20:21:04.454] (libbanshee:player) Disabled ReplayGain[/LEFT]
    [LEFT][1 Info  20:21:04.456] GStreamer version 0.10.35.0, gapless: True, replaygain: False[/LEFT]
    [LEFT][1 Debug 20:21:04.461] Delayed Initializating Banshee.Dap.DapService[/LEFT]
    [LEFT][1 Debug 20:21:04.475] Dap support extension loaded: Banshee.Dap.Mtp[/LEFT]
    [LEFT][1 Debug 20:21:04.477] Dap support extension loaded: Banshee.Dap.MassStorage[/LEFT]
    [LEFT][1 Debug 20:21:04.478] Dap support extension loaded: Banshee.Dap.AppleDevice[/LEFT]
    [LEFT][1 Debug 20:21:04.482] Delayed Initializating Banshee.Daap.DaapService[/LEFT]
    [LEFT][1 Debug 20:21:04.489] Delayed Initializating Banshee.Podcasting.PodcastService[/LEFT]
    [LEFT][1 Debug 20:21:05.572] Finished - Startup Job[/LEFT]
    [LEFT][13 Debug 20:21:05.998] DAAP Proxy listening for connections on port 808[/LEFT]


---

### Post by saltcushy on 2011-11-01
Someone helped from banshe.fm
install packages:
> ubuntu-restricted-extras 
w32codecs 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by amjjawad on 2011-11-03
Hi,

On my signature, check Lubuntu One Stop Thread - Section B - Contact Us. Go to the IRC Channels and ask your question there and I'm sure one of the team will help you :)
Sorry, I wish I could help more but I don't have a direct answer ... I don't use that application.

---

