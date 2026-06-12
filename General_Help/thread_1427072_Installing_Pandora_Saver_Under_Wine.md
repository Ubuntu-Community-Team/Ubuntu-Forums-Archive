---
title: "Installing Pandora Saver Under Wine"
date: 2010-03-11
forum: General Help
---

### Post by Keith1212 on 2010-03-11
I installed Pandora Saver 2 Using Wine V 1.0.1. I click the option while installing to use the Wine config. The first time it lauched I just got a small box that said it needed to close, but as long as i didnt click ok it worked fine playing my stations and saving music. So the next time i went to use it it gave me another error(see pic below). The smaller error box was the first one it gave me after the first install but allowed me to still use the app. The bigger box came after i started it the next time and will not allow me to use the app.
[img]http://img7.imageshack.us/img7/4801/screenshotlg.png[/img]


Sproxy.log below
```
3/11/2010 1:32:50 AM    Creating a new configuration file

3/11/2010 1:32:51 AM    DebugLevel defaulting to 0

3/11/2010 1:32:51 AM    LinuxHacks defaulting to False

3/11/2010 1:32:50 AM    Creating a new configuration file

3/11/2010 1:32:56 AM    Wrote 3 settings to disk

3/11/2010 1:33:13 AM    Configuration read, 3 keys

3/11/2010 1:33:13 AM    DebugLevel defaulting to 0

3/11/2010 1:33:13 AM    AllowNonLocal defaulting to False

3/11/2010 1:33:13 AM    AllowExemptions defaulting to True

3/11/2010 1:33:13 AM    BuildDate defaulting to 

3/11/2010 1:33:13 AM    DoTamperAlways defaulting to False

3/11/2010 1:33:13 AM    DoubleBuffered defaulting to False

3/11/2010 1:33:13 AM    Debug defaulting to False

3/11/2010 1:33:13 AM    IEProxies defaulting to False

3/11/2010 1:33:13 AM    ForceLocalResolves defaulting to False

3/11/2010 1:33:13 AM    ListenPort defaulting to 8888

3/11/2010 1:33:13 AM    Timeout defaulting to 60000

3/11/2010 1:33:13 AM    MaxSimulConnections defaulting to 32

3/11/2010 1:33:13 AM    ServerName defaulting to 127.0.0.1

3/11/2010 1:33:13 AM    StartMinimized defaulting to False

3/11/2010 1:33:13 AM    ProxyDefaultExempt defaulting to False

3/11/2010 1:33:13 AM    ProxyType defaulting to 0

3/11/2010 1:33:13 AM    ProxyAddr defaulting to 127.0.0.1

3/11/2010 1:33:13 AM    ProxyPort defaulting to 8080

3/11/2010 1:33:13 AM    ProxyUser defaulting to 

3/11/2010 1:33:13 AM    ProxyPass defaulting to 

3/11/2010 1:33:13 AM    ProxyTimeout defaulting to 60000

3/11/2010 1:33:13 AM    ProxyNeedAuth defaulting to False

3/11/2010 1:33:13 AM    TargetDownSpeed defaulting to 0

3/11/2010 1:33:13 AM    MaxDownstreamSpeed defaulting to 100000

3/11/2010 1:33:13 AM    MaxUpstreamSpeed defaulting to 10000

3/11/2010 1:33:13 AM    ShowStatsForm defaulting to False

3/11/2010 1:33:13 AM    ShowTrayIcon defaulting to False

3/11/2010 1:33:13 AM    Wrote 30 settings to disk

3/11/2010 1:33:14 AM    SProxy application started.

3/11/2010 1:33:14 AM    Debug level of 0

3/11/2010 1:33:14 AM    Skipping duplicate process check

3/11/2010 1:33:18 AM    Searching for plugins in C:\Program Files\Saver2\

3/11/2010 1:33:18 AM    __YouTube_Enabled defaulting to True

3/11/2010 1:33:18 AM    __YouTube_ConvertAllVideos defaulting to False

3/11/2010 1:33:18 AM    Loaded plugin YouTube.YouTube from Saver.YouTube.dll

3/11/2010 1:33:18 AM    Loaded plugin SongManager.SongManager from SongManager.dll

3/11/2010 1:33:18 AM    Pandora and all related trademarks are property of Pandora Media, Inc.

3/11/2010 1:33:18 AM    __Pandora_Debug defaulting to False

3/11/2010 1:33:18 AM    __Pandora_AARTTimeout defaulting to 90

3/11/2010 1:33:18 AM    __Pandora_AutoReloadTime defaulting to 60

3/11/2010 1:33:18 AM    __Pandora_DeleteNegRatedSongs defaulting to False

3/11/2010 1:33:18 AM    __Pandora_DLButton defaulting to False

3/11/2010 1:33:18 AM    __Pandora_DLPosRatedSongs defaulting to True

3/11/2010 1:33:18 AM    __Pandora_Enabled defaulting to True

3/11/2010 1:33:18 AM    __Pandora_TurboMode defaulting to False

3/11/2010 1:33:18 AM    __Pandora_MangleAds defaulting to True

3/11/2010 1:33:18 AM    __Pandora_DLPrePosRated defaulting to True

3/11/2010 1:33:18 AM    __Pandora_AutoRefreshMiniPlayer defaulting to True

3/11/2010 1:33:18 AM    __Pandora_ExemptData defaulting to True

3/11/2010 1:33:18 AM    __Pandora_TurboOverride defaulting to False

3/11/2010 1:33:18 AM    __Pandora_WriteXMLs defaulting to False

3/11/2010 1:33:18 AM    __Pandora_ForceTurboSpeed defaulting to -1

3/11/2010 1:33:18 AM    Loaded plugin Pandora.Pandora from Saver.Pandora.dll

3/11/2010 1:33:18 AM    __PandoraClient_Debug defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_SkipOnBan defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_Username defaulting to 

3/11/2010 1:33:18 AM    __PandoraClient_Password defaulting to 

3/11/2010 1:33:18 AM    __PandoraClient_CurrentStation defaulting to 

3/11/2010 1:33:18 AM    __PandoraClient_ClientAutoLaunch defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_KeyboardCtrl defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_Shuffle defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_Volume defaulting to 80

3/11/2010 1:33:18 AM    __PandoraClient_SniffShared defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_AlwaysOnTop defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_AutoLogin defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_FadedOutPercent defaulting to 35

3/11/2010 1:33:18 AM    __PandoraClient_FadedInPercent defaulting to 99

3/11/2010 1:33:18 AM    __PandoraClient_BaseOpChg defaulting to 5

3/11/2010 1:33:18 AM    __PandoraClient_FadeIntensity defaulting to 20

3/11/2010 1:33:18 AM    __PandoraClient_ShowTimeOnUpdate defaulting to 10000

3/11/2010 1:33:18 AM    __PandoraClient_AnimSpeed defaulting to 20

3/11/2010 1:33:18 AM    __PandoraClient_FadingEnabled defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_FadeOnChange defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_FixedOPWhileShaded defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_RememberPos defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_LastPosition defaulting to 300,300

3/11/2010 1:33:18 AM    __PandoraClient_AutoCloseSP defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_SnapToEdges defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_NewGuiEnabled defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_LastWindState defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_TireEverySong defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_UseSoftvol defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_PrecacheSize defaulting to 393216

3/11/2010 1:33:18 AM    __PandoraClient_StrongMove defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_TrayNotify defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_OldSaveButton defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_ExMPArgs defaulting to 

3/11/2010 1:33:18 AM    __PandoraClient_HighPriority defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_DiscardUserInfo defaulting to False

3/11/2010 1:33:18 AM    __PandoraClient_TutorialMode defaulting to True

3/11/2010 1:33:18 AM    __PandoraClient_PlayPauseKey defaulting to FFF,179,MediaPlayPause

3/11/2010 1:33:18 AM    __PandoraClient_NextKey defaulting to FFF,176,MediaNextTrack

3/11/2010 1:33:18 AM    __PandoraClient_RateGoodKey defaulting to none

3/11/2010 1:33:18 AM    __PandoraClient_RateBadKey defaulting to none

3/11/2010 1:33:18 AM    __PandoraClient_VolUpKey defaulting to none

3/11/2010 1:33:18 AM    __PandoraClient_VolDownKey defaulting to none

3/11/2010 1:33:18 AM    Loaded plugin Client.Client from PandoraClient.dll

3/11/2010 1:33:18 AM    __SimpleBlacklist_Enabled defaulting to False

3/11/2010 1:33:18 AM    __SimpleBlacklist_DeleteBlacklisted defaulting to False

3/11/2010 1:33:18 AM    __SimpleBlacklist_MatchTolerance defaulting to 90

3/11/2010 1:33:18 AM    Loaded plugin SimpleBlacklist.SimpleBlacklist from SimpleBlacklist.dll

3/11/2010 1:33:18 AM    __Saver2_BuildDate defaulting to 

3/11/2010 1:33:18 AM    __Saver2_AutorunCmd defaulting to 

3/11/2010 1:33:18 AM    __Saver2_ShownBetaMsg defaulting to False

3/11/2010 1:33:18 AM    __Saver2_SaveDir defaulting to C:\Program Files\Saver2\Saved Music\

3/11/2010 1:33:18 AM    __Saver2_RipMode defaulting to 1

3/11/2010 1:33:18 AM    __Saver2_Whitelist defaulting to False

3/11/2010 1:33:18 AM    __Saver2_StrictDupChecking defaulting to True

3/11/2010 1:33:18 AM    __Saver2_ReplaceLQSongs defaulting to False

3/11/2010 1:33:18 AM    __Saver2_Encoding defaulting to False

3/11/2010 1:33:18 AM    __Saver2_Blacklist defaulting to False

3/11/2010 1:33:18 AM    __Saver2_Multicore defaulting to True

3/11/2010 1:33:18 AM    __Saver2_LowPriorityEncoder defaulting to True

3/11/2010 1:33:18 AM    __Saver2_SaveAART defaulting to True

3/11/2010 1:33:18 AM    __Saver2_SongNameFormat defaulting to %artist% - %title%

3/11/2010 1:33:18 AM    __Saver2_FolderStructure defaulting to %artist%\%album%\

3/11/2010 1:33:18 AM    __Saver2_EncoderExt defaulting to .mp3

3/11/2010 1:33:18 AM    __Saver2_EncoderCmd defaulting to -h -b %bitrate% %wavtmp% %out%

3/11/2010 1:33:18 AM    __Saver2_EncoderLoc defaulting to %path%lame.exe

3/11/2010 1:33:18 AM    __Saver2_MP3Quality defaulting to 160

3/11/2010 1:33:18 AM    __Saver2_ClearAllTemp defaulting to 2

3/11/2010 1:33:18 AM    __Saver2_TrayIconNotify defaulting to True

3/11/2010 1:33:18 AM    __Saver2_MaxPendingSongs defaulting to 50

3/11/2010 1:33:18 AM    __Saver2_DupMatchTolerance defaulting to 100

3/11/2010 1:33:18 AM    __Saver2_ReapSongs defaulting to False

3/11/2010 1:33:18 AM    __Saver2_WarnPendingExit defaulting to True

3/11/2010 1:33:18 AM    __Saver2_CreatePlaylists defaulting to True

3/11/2010 1:33:18 AM    __Saver2_UpdateCheck defaulting to True

3/11/2010 1:33:18 AM    __Saver2_NotifyNonVitalUpdate defaulting to False

3/11/2010 1:33:18 AM    __Saver2_AbsolutePlaylistPaths defaulting to False

3/11/2010 1:33:18 AM    __Saver2_AmazonAARTLookup defaulting to True

3/11/2010 1:33:18 AM    __Saver2_UpgradeMinSize defaulting to 125

3/11/2010 1:33:18 AM    __Saver2_ScrapGenreAlways defaulting to True

3/11/2010 1:33:18 AM    Loaded plugin Saver2.Saver from Saver2.dll

3/11/2010 1:33:18 AM    __Grooveshark_Enabled defaulting to True

3/11/2010 1:33:18 AM    __Grooveshark_Debug defaulting to False

3/11/2010 1:33:18 AM    __Grooveshark_DontUseProxy defaulting to False

3/11/2010 1:33:18 AM    Loaded plugin Grooveshark.Grooveshark from Saver.Grooveshark.dll

3/11/2010 1:33:18 AM    __SongFader_Enabled defaulting to False

3/11/2010 1:33:18 AM    __SongFader_FadedOutPercent defaulting to 35

3/11/2010 1:33:18 AM    __SongFader_FadedInPercent defaulting to 99

3/11/2010 1:33:18 AM    __SongFader_BaseOpChg defaulting to 5

3/11/2010 1:33:18 AM    __SongFader_FadeIntensity defaulting to 20

3/11/2010 1:33:18 AM    __SongFader_ShowTimeOnUpdate defaulting to 15000

3/11/2010 1:33:18 AM    __SongFader_AnimSpeed defaulting to 20

3/11/2010 1:33:18 AM    Loaded plugin SongFader.SongFader from SongFader.dll

3/11/2010 1:33:18 AM    __Slacker_Enabled defaulting to True

3/11/2010 1:33:18 AM    __Slacker_Debug defaulting to False

3/11/2010 1:33:18 AM    Loaded plugin Slacker.Slacker from Saver.Slacker.dll

3/11/2010 1:33:18 AM    __Playlist_Enabled defaulting to True

3/11/2010 1:33:18 AM    Loaded plugin PlaylistDotCom.PlaylistDotCom from Saver.Playlist.dll

3/11/2010 1:33:18 AM    Saver2: Checking vital files...

3/11/2010 1:33:18 AM    Saver2: Verifying mplayer.exe

3/11/2010 1:33:18 AM    Saver2: Verifying mp4tags.exe

3/11/2010 1:33:18 AM    Saver2: Verifying lame.exe

3/11/2010 1:33:18 AM    Saver2: Verification completed successfully.

3/11/2010 1:33:18 AM    Saver2 Core 1.2.4 loaded; looking for suitable plugins...

3/11/2010 1:33:18 AM    Saver2: YouTube 1.0 found!

3/11/2010 1:33:18 AM    Saver2: Song Manager 1.001 found!

3/11/2010 1:33:18 AM    Saver2: Pandora Saver S2.1 found!

3/11/2010 1:33:18 AM    Saver2: Pandora Client C1.3 found!

3/11/2010 1:33:18 AM    Saver2: Simple Blacklisting 1.008 found!

3/11/2010 1:33:18 AM    Saver2: Grooveshark 1.0 found!

3/11/2010 1:33:18 AM    Saver2: Song Fader 1.008a found!

3/11/2010 1:33:18 AM    Saver2: Slacker 1.0 found!

3/11/2010 1:33:18 AM    Saver2: Playlist.com 1.0 found!

3/11/2010 1:33:18 AM    Saver2: Saver2 built on 3/6/2010 2:17:52 PM CST

3/11/2010 1:33:18 AM    Saver2: WARNING: This software is for educational use only. Do not use the software in a way that would contravene any music copyright laws.

3/11/2010 1:33:18 AM    Saver2: Any information provided by software is for educational purposes only. No function is implied or in any way guaranteed.

3/11/2010 1:33:18 AM    Saver2: SaveDir = C:\Program Files\Saver2\Saved Music\

3/11/2010 1:33:18 AM    Saver2: NrCores = 2

3/11/2010 1:33:18 AM    Saver2: Worker thread started!

3/11/2010 1:33:18 AM    Saver2: Updating playlists to use relative paths.

3/11/2010 1:33:19 AM    SBL: Loading blacklists...

3/11/2010 1:33:19 AM    SBL: Loaded 0 blacklist patterns from file 'C:\Program Files\Saver2\Sample.blacklist.txt'

3/11/2010 1:33:19 AM    SProxy starting

3/11/2010 1:33:19 AM    Listening for connections on port 8888

3/11/2010 1:33:46 AM    Configuration read, 30 keys

3/11/2010 1:33:46 AM    BuildDate defaulting to 

3/11/2010 1:33:47 AM    Wrote 30 settings to disk

3/11/2010 1:33:47 AM    SProxy application started.

3/11/2010 1:33:47 AM    Debug level of 0

3/11/2010 1:33:47 AM    Skipping duplicate process check

3/11/2010 1:33:49 AM    Searching for plugins in C:\Program Files\Saver2\

3/11/2010 1:33:49 AM    __YouTube_Enabled defaulting to True

3/11/2010 1:33:49 AM    __YouTube_ConvertAllVideos defaulting to False

3/11/2010 1:33:49 AM    Loaded plugin YouTube.YouTube from Saver.YouTube.dll

3/11/2010 1:33:49 AM    Loaded plugin SongManager.SongManager from SongManager.dll

3/11/2010 1:33:49 AM    Pandora and all related trademarks are property of Pandora Media, Inc.

3/11/2010 1:33:49 AM    __Pandora_Debug defaulting to False

3/11/2010 1:33:49 AM    __Pandora_AARTTimeout defaulting to 90

3/11/2010 1:33:49 AM    __Pandora_AutoReloadTime defaulting to 60

3/11/2010 1:33:49 AM    __Pandora_DeleteNegRatedSongs defaulting to False

3/11/2010 1:33:49 AM    __Pandora_DLButton defaulting to False

3/11/2010 1:33:49 AM    __Pandora_DLPosRatedSongs defaulting to True

3/11/2010 1:33:49 AM    __Pandora_Enabled defaulting to True

3/11/2010 1:33:49 AM    __Pandora_TurboMode defaulting to False

3/11/2010 1:33:49 AM    __Pandora_MangleAds defaulting to True

3/11/2010 1:33:49 AM    __Pandora_DLPrePosRated defaulting to True

3/11/2010 1:33:49 AM    __Pandora_AutoRefreshMiniPlayer defaulting to True

3/11/2010 1:33:49 AM    __Pandora_ExemptData defaulting to True

3/11/2010 1:33:49 AM    __Pandora_TurboOverride defaulting to False

3/11/2010 1:33:49 AM    __Pandora_WriteXMLs defaulting to False

3/11/2010 1:33:49 AM    __Pandora_ForceTurboSpeed defaulting to -1

3/11/2010 1:33:49 AM    Loaded plugin Pandora.Pandora from Saver.Pandora.dll

3/11/2010 1:33:49 AM    __PandoraClient_Debug defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_SkipOnBan defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_Username defaulting to 

3/11/2010 1:33:49 AM    __PandoraClient_Password defaulting to 

3/11/2010 1:33:49 AM    __PandoraClient_CurrentStation defaulting to 

3/11/2010 1:33:49 AM    __PandoraClient_ClientAutoLaunch defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_KeyboardCtrl defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_Shuffle defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_Volume defaulting to 80

3/11/2010 1:33:49 AM    __PandoraClient_SniffShared defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_AlwaysOnTop defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_AutoLogin defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_FadedOutPercent defaulting to 35

3/11/2010 1:33:49 AM    __PandoraClient_FadedInPercent defaulting to 99

3/11/2010 1:33:49 AM    __PandoraClient_BaseOpChg defaulting to 5

3/11/2010 1:33:49 AM    __PandoraClient_FadeIntensity defaulting to 20

3/11/2010 1:33:49 AM    __PandoraClient_ShowTimeOnUpdate defaulting to 10000

3/11/2010 1:33:49 AM    __PandoraClient_AnimSpeed defaulting to 20

3/11/2010 1:33:49 AM    __PandoraClient_FadingEnabled defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_FadeOnChange defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_FixedOPWhileShaded defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_RememberPos defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_LastPosition defaulting to 300,300

3/11/2010 1:33:49 AM    __PandoraClient_AutoCloseSP defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_SnapToEdges defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_NewGuiEnabled defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_LastWindState defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_TireEverySong defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_UseSoftvol defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_PrecacheSize defaulting to 393216

3/11/2010 1:33:49 AM    __PandoraClient_StrongMove defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_TrayNotify defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_OldSaveButton defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_ExMPArgs defaulting to 

3/11/2010 1:33:49 AM    __PandoraClient_HighPriority defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_DiscardUserInfo defaulting to False

3/11/2010 1:33:49 AM    __PandoraClient_TutorialMode defaulting to True

3/11/2010 1:33:49 AM    __PandoraClient_PlayPauseKey defaulting to FFF,179,MediaPlayPause

3/11/2010 1:33:49 AM    __PandoraClient_NextKey defaulting to FFF,176,MediaNextTrack

3/11/2010 1:33:49 AM    __PandoraClient_RateGoodKey defaulting to none

3/11/2010 1:33:49 AM    __PandoraClient_RateBadKey defaulting to none

3/11/2010 1:33:49 AM    __PandoraClient_VolUpKey defaulting to none

3/11/2010 1:33:49 AM    __PandoraClient_VolDownKey defaulting to none

3/11/2010 1:33:49 AM    Loaded plugin Client.Client from PandoraClient.dll

3/11/2010 1:33:49 AM    __SimpleBlacklist_Enabled defaulting to False

3/11/2010 1:33:49 AM    __SimpleBlacklist_DeleteBlacklisted defaulting to False

3/11/2010 1:33:49 AM    __SimpleBlacklist_MatchTolerance defaulting to 90

3/11/2010 1:33:49 AM    Loaded plugin SimpleBlacklist.SimpleBlacklist from SimpleBlacklist.dll

3/11/2010 1:33:49 AM    __Saver2_BuildDate defaulting to 

3/11/2010 1:33:49 AM    __Saver2_AutorunCmd defaulting to 

3/11/2010 1:33:49 AM    __Saver2_ShownBetaMsg defaulting to False

3/11/2010 1:33:49 AM    __Saver2_SaveDir defaulting to C:\Program Files\Saver2\Saved Music\

3/11/2010 1:33:49 AM    __Saver2_RipMode defaulting to 1

3/11/2010 1:33:49 AM    __Saver2_Whitelist defaulting to False

3/11/2010 1:33:49 AM    __Saver2_StrictDupChecking defaulting to True

3/11/2010 1:33:49 AM    __Saver2_ReplaceLQSongs defaulting to False

3/11/2010 1:33:49 AM    __Saver2_Encoding defaulting to False

3/11/2010 1:33:49 AM    __Saver2_Blacklist defaulting to False

3/11/2010 1:33:49 AM    __Saver2_Multicore defaulting to True

3/11/2010 1:33:49 AM    __Saver2_LowPriorityEncoder defaulting to True

3/11/2010 1:33:49 AM    __Saver2_SaveAART defaulting to True

3/11/2010 1:33:49 AM    __Saver2_SongNameFormat defaulting to %artist% - %title%

3/11/2010 1:33:49 AM    __Saver2_FolderStructure defaulting to %artist%\%album%\

3/11/2010 1:33:49 AM    __Saver2_EncoderExt defaulting to .mp3

3/11/2010 1:33:49 AM    __Saver2_EncoderCmd defaulting to -h -b %bitrate% %wavtmp% %out%

3/11/2010 1:33:49 AM    __Saver2_EncoderLoc defaulting to %path%lame.exe

3/11/2010 1:33:49 AM    __Saver2_MP3Quality defaulting to 160

3/11/2010 1:33:49 AM    __Saver2_ClearAllTemp defaulting to 2

3/11/2010 1:33:49 AM    __Saver2_TrayIconNotify defaulting to True

3/11/2010 1:33:49 AM    __Saver2_MaxPendingSongs defaulting to 50

3/11/2010 1:33:49 AM    __Saver2_DupMatchTolerance defaulting to 100

3/11/2010 1:33:49 AM    __Saver2_ReapSongs defaulting to False

3/11/2010 1:33:49 AM    __Saver2_WarnPendingExit defaulting to True

3/11/2010 1:33:49 AM    __Saver2_CreatePlaylists defaulting to True

3/11/2010 1:33:49 AM    __Saver2_UpdateCheck defaulting to True

3/11/2010 1:33:49 AM    __Saver2_NotifyNonVitalUpdate defaulting to False

3/11/2010 1:33:49 AM    __Saver2_AbsolutePlaylistPaths defaulting to False

3/11/2010 1:33:49 AM    __Saver2_AmazonAARTLookup defaulting to True

3/11/2010 1:33:49 AM    __Saver2_UpgradeMinSize defaulting to 125

3/11/2010 1:33:49 AM    __Saver2_ScrapGenreAlways defaulting to True

3/11/2010 1:33:50 AM    Loaded plugin Saver2.Saver from Saver2.dll

3/11/2010 1:33:50 AM    __Grooveshark_Enabled defaulting to True

3/11/2010 1:33:50 AM    __Grooveshark_Debug defaulting to False

3/11/2010 1:33:50 AM    __Grooveshark_DontUseProxy defaulting to False

3/11/2010 1:33:50 AM    Loaded plugin Grooveshark.Grooveshark from Saver.Grooveshark.dll

3/11/2010 1:33:50 AM    __SongFader_Enabled defaulting to False

3/11/2010 1:33:50 AM    __SongFader_FadedOutPercent defaulting to 35

3/11/2010 1:33:50 AM    __SongFader_FadedInPercent defaulting to 99

3/11/2010 1:33:50 AM    __SongFader_BaseOpChg defaulting to 5

3/11/2010 1:33:50 AM    __SongFader_FadeIntensity defaulting to 20

3/11/2010 1:33:50 AM    __SongFader_ShowTimeOnUpdate defaulting to 15000

3/11/2010 1:33:50 AM    __SongFader_AnimSpeed defaulting to 20

3/11/2010 1:33:50 AM    Loaded plugin SongFader.SongFader from SongFader.dll

3/11/2010 1:33:50 AM    __Slacker_Enabled defaulting to True

3/11/2010 1:33:50 AM    __Slacker_Debug defaulting to False

3/11/2010 1:33:50 AM    Loaded plugin Slacker.Slacker from Saver.Slacker.dll

3/11/2010 1:33:50 AM    __Playlist_Enabled defaulting to True

3/11/2010 1:33:50 AM    Loaded plugin PlaylistDotCom.PlaylistDotCom from Saver.Playlist.dll

3/11/2010 1:33:50 AM    Saver2: Checking vital files...

3/11/2010 1:33:50 AM    Saver2: Verifying mplayer.exe

3/11/2010 1:33:50 AM    Saver2: Verifying mp4tags.exe

3/11/2010 1:33:50 AM    Saver2: Verifying lame.exe

3/11/2010 1:33:50 AM    Saver2: Verification completed successfully.

3/11/2010 1:33:50 AM    Saver2 Core 1.2.4 loaded; looking for suitable plugins...

3/11/2010 1:33:50 AM    Saver2: YouTube 1.0 found!

3/11/2010 1:33:50 AM    Saver2: Song Manager 1.001 found!

3/11/2010 1:33:50 AM    Saver2: Pandora Saver S2.1 found!

3/11/2010 1:33:50 AM    Saver2: Pandora Client C1.3 found!

3/11/2010 1:33:50 AM    Saver2: Simple Blacklisting 1.008 found!

3/11/2010 1:33:50 AM    Saver2: Grooveshark 1.0 found!

3/11/2010 1:33:50 AM    Saver2: Song Fader 1.008a found!

3/11/2010 1:33:50 AM    Saver2: Slacker 1.0 found!

3/11/2010 1:33:50 AM    Saver2: Playlist.com 1.0 found!

3/11/2010 1:33:50 AM    Saver2: Saver2 built on 3/6/2010 2:17:52 PM CST

3/11/2010 1:33:50 AM    Saver2: WARNING: This software is for educational use only. Do not use the software in a way that would contravene any music copyright laws.

3/11/2010 1:33:50 AM    Saver2: Any information provided by software is for educational purposes only. No function is implied or in any way guaranteed.

3/11/2010 1:33:50 AM    Saver2: SaveDir = C:\Program Files\Saver2\Saved Music\

3/11/2010 1:33:50 AM    Saver2: NrCores = 2

3/11/2010 1:33:50 AM    Saver2: Worker thread started!

3/11/2010 1:33:50 AM    Saver2: Updating playlists to use relative paths.

3/11/2010 1:33:50 AM    SBL: Loading blacklists...

3/11/2010 1:33:50 AM    SBL: Loaded 0 blacklist patterns from file 'C:\Program Files\Saver2\Sample.blacklist.txt'

3/11/2010 1:33:50 AM    SProxy starting

3/11/2010 1:33:50 AM    Listening for connections on port 8888

3/11/2010 1:33:51 AM    Saver2: Checking for updates....

3/11/2010 1:33:51 AM    #0    GET http://zzj.itf-inc.com/s2/updatechk.php

3/11/2010 1:33:52 AM    Saver2: Up to date (md5 hash match)

3/11/2010 1:35:05 AM    Wrote 140 settings to disk

3/11/2010 1:35:05 AM    Loaded documentation; 30 entries

3/11/2010 1:35:13 AM    Client: Using old GUI

3/11/2010 1:35:13 AM    PClient 1.4 started; protocol v26

3/11/2010 1:35:14 AM    StreamPlayer: Opening mplayer.log

3/11/2010 1:35:14 AM    StreamPlayer: Launching mplayer w/ args -slave -idle -cache 320 -demuxer audio -quiet

3/11/2010 1:35:16 AM    StreamPlayer: mplayer ready for playback

3/11/2010 1:35:17 AM    Client: Logging in to Pandora

3/11/2010 1:35:17 AM    Client: Syncing

3/11/2010 1:35:17 AM    #1    POST http://www.pandora.com/radio/xmlrpc/v26?rid=8292917P&method=sync

3/11/2010 1:35:17 AM    #1 POST 210 bytes to www.pandora.com

3/11/2010 1:35:17 AM    Pandora: Inspecting XMLRPC 'sync': http://www.pandora.com/radio/xmlrpc/v26?rid=8292917P&method=sync

3/11/2010 1:35:18 AM    Client: Authenticating...

3/11/2010 1:35:52 AM    #2    POST http://www.pandora.com/radio/xmlrpc/v26?rid=8292917P&method=authenticateListener

3/11/2010 1:35:52 AM    #2 POST 594 bytes to www.pandora.com

3/11/2010 1:35:53 AM    Pandora: Inspecting XMLRPC 'authenticateListener': http://www.pandora.com/radio/xmlrpc/v26?rid=8292917P&method=authenticateListener

3/11/2010 1:35:53 AM    ----- Logged in keith12121

3/11/2010 1:35:53 AM    | Acct type: REGISTERED

3/11/2010 1:35:53 AM    | Bill freq: 

3/11/2010 1:35:53 AM    -------------

3/11/2010 1:35:54 AM    Client: Fetching stations...

3/11/2010 1:35:54 AM    #3    POST http://www.pandora.com/radio/xmlrpc/v26?rid=8292917P&lid=139934328&method=getStations

3/11/2010 1:35:54 AM    #3 POST 482 bytes to www.pandora.com

3/11/2010 1:35:54 AM    Pandora: Inspecting XMLRPC 'getStations': http://www.pandora.com/radio/xmlrpc/v26?rid=8292917P&lid=139934328&method=getStations

3/11/2010 1:35:54 AM    Pandora: Sniffed 11 new station names

3/11/2010 1:35:55 AM    Client: Got 11 stations

3/11/2010 1:36:01 AM    Client: Changing station to 178774693826214520 | Staind Radio

3/11/2010 1:36:01 AM    Client: Fetching playlist...

3/11/2010 1:36:01 AM    #4    POST http://www.pandora.com/radio/xmlrpc/v26?rid=8292917P&lid=139934328&method=getFragment&arg1=178774693826214520&arg2=1&arg3=&arg4=&arg5=mp3%2Dhifi&arg6=0&arg7=0

3/11/2010 1:36:01 AM    #4 POST 1202 bytes to www.pandora.com

3/11/2010 1:36:02 AM    Pandora: Inspecting XMLRPC 'getFragment': http://www.pandora.com/radio/xmlrpc/v26?rid=8292917P&lid=139934328&method=getFragment&arg1=178774693826214520&arg2=1&arg3=&arg4=&arg5=mp3%2Dhifi&arg6=0&arg7=0

3/11/2010 1:36:02 AM    Pandora: Data format: mp3

3/11/2010 1:36:02 AM    Pandora: Got song S124406, URL = http://audio-ash-t2-1.pandora.com/access/?version=4&lid=139934328&token=Hi3ek1HN1vW4OdBt%2F%2FE6n3U%2B4D9kAMPIdBKCVn%2FZnDOo5Dt4f%2BKI91BTdrkIwsos3V2Ro2oN8%2BAHRXve1k22A9aKkGjiGLW%2BMYoL6vth0GXI7S%2FgVFbu6MzPQ6NkU2axVxAJf2Paq6eJ4DZCMEVxKJivo20sTZHBi18Or1%2BGBBEIc1zcBI2n7MPnUh8haop2iD%2Ft3%2BQpA4UAxq3JVmfMc8DWt%2F5Lq6wf91k39rzf2oOQfdq5Qyug20ZbpyV%2BIVP3fQrMNZf40bBSf9BlF56f8IOGxk%2FnF%2BOAmsXiebjFoGZ3qI7o2Izx15NVEz8jzWfmqnpqu4hHLEY%3D

3/11/2010 1:36:02 AM    Pandora: Got song S1197292, URL = http://audio-ash-t3-1.pandora.com/access/?version=4&lid=139934328&token=Hi3ek1HN1vW4OdBt%2F%2FE6n3U%2B4D9kAMPIdBKCVn%2FZnDOo5Dt4f%2BKI91BTdrkIwsos3V2Ro2oN8%2BAHRXve1k22Azt5WPHg41k3RzyXxOryADKsQMVZ2LuawYzt7AT%2BH6Gs60laNkp3%2FxaunDyXQB0rRGoNPNNRcVdeCA%2BWnRfxja7ykb3JxvsONxoB1j3T5PVZK4fgHeuFG3tmGueQQ%2BGaL96S3kUicGMQxDjuqDyLBaHvnU1IxEGUBHb6bRsgcO0CkR0EJH5N%2BISFtxNOh6fBf4VJERK0M7ij9bTeeh%2BE46zoiBz8m57JGIczMSlpT%2FxJe8HrYAPuo9U%3D

3/11/2010 1:36:02 AM    Pandora: Got song S121548, URL = http://audio-ash-t2-1.pandora.com/access/7839921226119254785?version=4&lid=139934328&token=Hi3ek1HN1vW4OdBt%2F%2FE6n3U%2B4D9kAMPIdBKCVn%2FZnDOo5Dt4f%2BKI91BTdrkIwsos3V2Ro2oN8%2BAHRXve1k22A%2F7u0ZRb0deDEML4s%2FwY4SlYianfZjGEEZvREzHo0KD4laRz6anRkwxVHeZSHSnAu4Hq1jBKksm1muc5DxpSj3arJ4DaDmefzvmV%2BX2GUZYFhkZumFJPNX5c3JeNrkbBWTzZAkGXetYY9%2Br%2FWwAmMf%2BOho62BsCvtKsNMPK5hCElTntwCxOufLXO9zJ2oESnspGJ7O10DbU9bMPlf%2BUKikMKp9u9zhRBz7KeF22f3Mrd6aEuqIJVqsE%3D

3/11/2010 1:36:02 AM    Pandora: Got song S516104, URL = http://audio-sjl-t2-2.pandora.com/access/?version=4&lid=139934328&token=Hi3ek1HN1vW4OdBt%2F%2FE6n3U%2B4D9kAMPIdBKCVn%2FZnDOo5Dt4f%2BKI91BTdrkIwsos3V2Ro2oN8%2BAHRXve1k22Ay7Nn1A8VMNZiOQthOLMa1iz8hLP1f%2B9zGx3HeV5W5wwrsgsf90vTiAGl5QPhXD9XQN70xvubeJr144vA6UknhsSHYPUDqYPpqlao7OFbor4mEP55NeuDA%2BCc%2Bdd6V8yEmgP6Pm9CU5oHWDQHVat%2BwZZ2WP3atFyCqUJqw176xyxP1SzcKE7beeMA3mKC7rMj9eGUVGJ2cOhB0tFIXLMc0px%2FcIQVVW67oKX2w5Ca7crd5QVYR%2B77RQ%3D

3/11/2010 1:36:03 AM    Client: Starting playback of song Linkin Park - "Easier To Run" on 'Meteora' (ID S124406)

3/11/2010 1:36:03 AM    StreamPlayer: Play URL http://audio-ash-t2-1.pandora.com/access/?version=4&lid=139934328&token=Hi3ek1HN1vW4OdBt%2F%2FE6n3U%2B4D9kAMPIdBKCVn%2FZnDOo5Dt4f%2BKI91BTdrkIwsos3V2Ro2oN8%2BAHRXve1k22A9aKkGjiGLW%2BMYoL6vth0GXI7S%2FgVFbu6MzPQ6NkU2axVxAJf2Paq6eJ4DZCMEVxKJivo20sTZHBi18Or1%2BGBBEIc1zcBI2n7MPnUh8haop2iD%2Ft3%2BQpA4UAxq3JVmfMc8DWt%2F5Lq6wf91k39rzf2oOQfdq5Qyug20ZbpyV%2BIVP3fQrMNZf40bBSf9BlF56f8IOGxk%2FnF%2BOAmsXiebjFoGZ3qI7o2Izx15NVEz8jzWfmqnpqu4hHLEY%3D

3/11/2010 1:36:03 AM    #5    GET http://audio-ash-t2-1.pandora.com/access/?version=4&lid=139934328&token=Hi3ek1HN1vW4OdBt%2F%2FE6n3U%2B4D9kAMPIdBKCVn%2FZnDOo5Dt4f%2BKI91BTdrkIwsos3V2Ro2oN8%2BAHRXve1k22A9aKkGjiGLW%2BMYoL6vth0GXI7S%2FgVFbu6MzPQ6NkU2axVxAJf2Paq6eJ4DZCMEVxKJivo20sTZHBi18Or1%2BGBBEIc1zcBI2n7MPnUh8haop2iD%2Ft3%2BQpA4UAxq3JVmfMc8DWt%2F5Lq6wf91k39rzf2oOQfdq5Qyug20ZbpyV%2BIVP3fQrMNZf40bBSf9BlF56f8IOGxk%2FnF%2BOAmsXiebjFoGZ3qI7o2Izx15NVEz8jzWfmqnpqu4hHLEY%3D

3/11/2010 1:36:03 AM    Pandora: sniffed Linkin Park - "Easier To Run" on 'Meteora' (ID S124406)

3/11/2010 1:36:03 AM    S124406: Started downloading

3/11/2010 1:36:03 AM    StreamPlayer: Starting data transfer

3/11/2010 1:36:03 AM    StreamPlayer: Data pipe ready

3/11/2010 1:36:03 AM    StreamPlayer: Pipe connected

3/11/2010 1:36:04 AM    StreamPlayer: Starting data transfer

3/11/2010 1:36:05 AM    #6    GET http://images-ash-t2-1.pandora.com/images/public/amz/5/2/6/8/093624818625_130W_130H.jpg

3/11/2010 1:36:05 AM    Client: Showing mini-tutorial

3/11/2010 1:36:05 AM    S124406: Got album art

3/11/2010 1:36:08 AM    S124406: Finished downloading

3/11/2010 1:36:08 AM    StreamPlayer: Song download complete

3/11/2010 1:36:08 AM    S124406: Song AART ready, submitting

3/11/2010 1:36:08 AM    Saver2: Processing song Linkin Park - "Easier To Run" on 'Meteora' (ID S124406)

3/11/2010 1:36:09 AM    #7    GET http://www.google.com/search?q=Linkin%20Park%20Meteora%20genre&num=100

3/11/2010 1:36:09 AM    Saver2: Scraped genre: rock / metal

3/11/2010 1:36:09 AM    FILE SAVED, Source: Pandora; MP3 format, 3268857 bytes

3/11/2010 1:36:11 AM    #8    GET http://www.amazon.com/gp/search/ref=sr_adv_m_pop/?search-alias=popular&field-artist=Linkin%20Park&field-title=Meteora&sort=relevancerank

3/11/2010 1:36:12 AM    Saver2: Successfully looked up larger album art for S124406

3/11/2010 1:36:12 AM    Saver2: Fetching AART...

3/11/2010 1:36:12 AM    #9    GET http://ecx.images-amazon.com/images/I/31N10AYD1QL._SL500_.jpg

3/11/2010 1:36:13 AM    S124406: Tagging aac/mp3 file.

3/11/2010 1:36:13 AM    Saver2: Saved AART to 'G:\Music\Music\Linkin Park\Meteora\Meteora.png'

3/11/2010 1:36:13 AM    Saver2: Adding Linkin Park - Easier To Run.mp3 to Staind Radio.m3u

3/11/2010 1:36:47 AM    Configuration read, 140 keys

3/11/2010 1:36:47 AM    Wrote 140 settings to disk

3/11/2010 1:36:47 AM    SProxy application started.

3/11/2010 1:36:47 AM    Debug level of 0

3/11/2010 1:36:47 AM    Skipping duplicate process check

3/11/2010 1:37:40 AM    Configuration read, 140 keys

3/11/2010 1:37:41 AM    Wrote 140 settings to disk

3/11/2010 1:37:41 AM    SProxy application started.

3/11/2010 1:37:41 AM    Debug level of 0

3/11/2010 1:37:41 AM    Skipping duplicate process check

3/11/2010 1:42:30 AM    Configuration read, 140 keys

3/11/2010 1:42:30 AM    Wrote 140 settings to disk

3/11/2010 1:42:30 AM    SProxy application started.

3/11/2010 1:42:30 AM    Debug level of 0

3/11/2010 1:42:30 AM    Skipping duplicate process check

3/11/2010 1:44:56 AM    Configuration read, 140 keys

3/11/2010 1:44:57 AM    Wrote 140 settings to disk

3/11/2010 1:45:06 AM    Configuration read, 140 keys

3/11/2010 1:45:06 AM    Wrote 140 settings to disk

3/11/2010 1:45:06 AM    SProxy application started.

3/11/2010 1:45:06 AM    Debug level of 0

3/11/2010 1:45:06 AM    Skipping duplicate process check
```


Any help is appreciated thanks

---

### Post by Keith1212 on 2010-03-11
solved. Changed my listening port and logged in anonymously.

---

