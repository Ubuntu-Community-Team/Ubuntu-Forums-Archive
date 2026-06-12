---
title: "Shortcut in Gnome-do docky item too long"
date: 2009-12-12
forum: General Help
---

### Post by arcane14 on 2009-12-12
karmic koala user here, on a toshiba satellite L305-S5907 laptop. I made the fatal mistake of adding a shortcut to OpenOffice Word Processor to my docky dock and now the damn thing won't load. looks like the shortcut's name is so long that the app just chokes on it. gnome-do --debug output below:

```
WARNING: [Do.Banshee,1.0] Could not load some add-in assemblies: File '/usr/lib/banshee-1/Banshee.CollectionIndexer.dll' not found.
ERROR: Errors found in add-in '/usr/lib/gnome-do/plugins/Banshee.dll:
ERROR: The file '/usr/lib/banshee-1/Banshee.CollectionIndexer.dll' referenced in the manifest could not be found.
[Debug 14:15:07.130] [SystemService] Using org.freedesktop.DeviceKit.Power for battery information
[Info  14:15:07.140] [Services] Successfully located service of type ILogService.
[Info  14:15:07.140] [Services] Successfully located service of type IPreferencesService.
[Info  14:15:07.143] [Services] Successfully located service of type ISecurePreferencesService.
[Info  14:15:07.149] [Services] Successfully located service of type INotificationsService.
[Debug 14:15:07.155] [InterfaceManager] "Docky" interface was loaded
[Info  14:15:07.156] [Services] Successfully located service of type ILogService.
[Debug 14:15:07.156] [InterfaceManager] "Mini" interface was loaded
[Debug 14:15:07.157] [InterfaceManager] "Classic" interface was loaded
[Debug 14:15:07.157] [InterfaceManager] "Glass" interface was loaded
[Debug 14:15:07.158] [InterfaceManager] "Nouveau" interface was loaded
[Debug 14:15:07.164] [PluginManager] Loaded "SessionCommandsItemSource" from plugin.
[Debug 14:15:07.165] [PluginManager] Loaded "NotesItemSource" from plugin.
[Info  14:15:07.173] [Services] Successfully located service of type IPreferencesService.
[Info  14:15:07.173] [Services] Successfully located service of type ISecurePreferencesService.
[Info  14:15:07.178] [Services] Successfully located service of type ICoreService.
[Info  14:15:07.180] [Services] Successfully located service of type INetworkService.
[Debug 14:15:07.187] [PluginManager] Loaded "WeatherItemSource" from plugin.
[Info  14:15:07.267] [Services] Successfully located service of type PathsService.
[Debug 14:15:07.272] [PluginManager] Loaded "FriendSource" from plugin.
[Info  14:15:07.275] [Services] Successfully located service of type AbstractApplicationService.
[Debug 14:15:07.276] [PluginManager] Loaded "InternalItemSource" from plugin.
[Debug 14:15:07.276] [PluginManager] Loaded "ItemSourceItemSource" from plugin.
[Debug 14:15:07.278] [PluginManager] Loaded "PlacesItemSource" from plugin.
[Debug 14:15:07.279] [PluginManager] Loaded "ApplicationItemSource" from plugin.
[Debug 14:15:07.280] [PluginManager] Loaded "GNOMESpecialLocationsItemSource" from plugin.
[Debug 14:15:07.281] [PluginManager] Loaded "ProfileItemSource" from plugin.
[Debug 14:15:07.282] [PluginManager] Loaded "ScreenshotItemSource" from plugin.
[Debug 14:15:07.283] [PluginManager] Loaded "GCalendarItemSource" from plugin.
[Debug 14:15:07.295] [PluginManager] Loaded "ScreenItemSource" from plugin.

(Do:2409): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[Debug 14:15:07.300] [PluginManager] Loaded "WindowItemSource" from plugin.
[Debug 14:15:07.304] [PluginManager] Loaded "EmailAction" from plugin.
[Debug 14:15:07.304] [PluginManager] Loaded "OpenAction" from plugin.
[Debug 14:15:07.307] [PluginManager] Loaded "OpenUrlAction" from plugin.
[Debug 14:15:07.307] [PluginManager] Loaded "OpenWithAction" from plugin.
[Debug 14:15:07.307] [PluginManager] Loaded "RevealAction" from plugin.
[Debug 14:15:07.307] [PluginManager] Loaded "RunAction" from plugin.
[Debug 14:15:07.308] [PluginManager] Loaded "OpenSearchAction" from plugin.
[Debug 14:15:07.309] [PluginManager] Loaded "PastebinAction" from plugin.
[Debug 14:15:07.310] [PluginManager] Loaded "NewNoteAction" from plugin.
[Debug 14:15:07.310] [PluginManager] Loaded "SearchNotesAction" from plugin.
[Debug 14:15:07.312] [PluginManager] Loaded "DefineAction" from plugin.
[Debug 14:15:07.312] [PluginManager] Loaded "PostAction" from plugin.
[Debug 14:15:07.312] [PluginManager] Loaded "CopyToClipboardAction" from plugin.
[Debug 14:15:07.314] [PluginManager] Loaded "MakeUrlTinyAction" from plugin.
[Debug 14:15:07.314] [PluginManager] Loaded "RunInTerminalAction" from plugin.
[Debug 14:15:07.314] [PluginManager] Loaded "OpenTerminalHereAction" from plugin.
[Debug 14:15:07.315] [PluginManager] Loaded "GoogleCalculatorAction" from plugin.
[Debug 14:15:07.315] [PluginManager] Loaded "TakeScreenshotAction" from plugin.
[Debug 14:15:07.316] [PluginManager] Loaded "GCalendarNewEvent" from plugin.
[Debug 14:15:07.316] [PluginManager] Loaded "GCalendarSearchEvents" from plugin.
[Debug 14:15:07.316] [PluginManager] Loaded "ViewCalendarAction" from plugin.
[Debug 14:15:07.316] [PluginManager] Loaded "ViewEventAction" from plugin.
[Debug 14:15:07.317] [PluginManager] Loaded "WindowMinimizeAction" from plugin.
[Debug 14:15:07.317] [PluginManager] Loaded "WindowMaximizeAction" from plugin.
[Debug 14:15:07.317] [PluginManager] Loaded "WindowCloseAction" from plugin.
[Debug 14:15:07.317] [PluginManager] Loaded "WindowFocusAction" from plugin.
[Debug 14:15:07.317] [PluginManager] Loaded "WindowMoveAction" from plugin.
[Debug 14:15:07.318] [PluginManager] Loaded "ScreenTileAction" from plugin.
[Debug 14:15:07.318] [PluginManager] Loaded "ScreenCascadeAction" from plugin.
[Debug 14:15:07.318] [PluginManager] Loaded "ScreenRestoreAction" from plugin.
[Debug 14:15:07.319] [PluginManager] Loaded "ScreenSwapAction" from plugin.
[Debug 14:15:07.319] [PluginManager] Loaded "ShowDesktopAction" from plugin.
[Info  14:15:07.320] [Services] Successfully located service of type AbstractSystemService.
[Debug 14:15:07.327] [SystemService] No other application instance detected. Continue startup.
[Debug 14:15:07.364] [Controller] Setting theme Docky
[Info  14:15:07.647] [UniverseManager] Reloading universe...
[Debug 14:15:07.648] [UniverseManager] Reloading actions...
[Debug 14:15:07.663] [UniverseManager] Reloading item source "GNOME Session Commands"...
[Debug 14:15:07.665] [UniverseManager] Reloading item source "Tomboy Notes"...
Could not locate Tomboy on D-Bus. Perhaps it's not running?
[Debug 14:15:07.675] [UniverseManager] Reloading item source "Weather Commands"...
[Debug 14:15:07.689] [UniverseManager] Reloading item source "Microblog friends"...
[Debug 14:15:07.689] [UniverseManager] Reloading item source "Internal GNOME Do Items"...
[Debug 14:15:07.690] [UniverseManager] Reloading item source "GNOME Do Item Sources"...
[Debug 14:15:07.693] [UniverseManager] Reloading item source "Firefox Places"...
[Debug 14:15:07.762] [UniverseManager] Reloading item source "Applications"...
[Debug 14:15:08.005] [UniverseManager] Reloading item source "GNOME Special Locations"...
[Debug 14:15:08.009] [UniverseManager] Reloading item source "GNOME Terminal Profiles"...
[Debug 14:15:08.024] [UniverseManager] Reloading item source "GNOME Screenshot Items"...
[Debug 14:15:08.068] [UniverseManager] Reloading item source "Google Calendars"...
[Debug 14:15:08.072] [UniverseManager] Reloading item source "Window Screen Items"...
[Debug 14:15:08.072] [UniverseManager] Reloading item source "Generic Window Items"...
[Info  14:15:08.073] [UniverseManager] Universe contains 320 items.
[Info  14:15:08.077] [AbstractWeatherSource] Weather Underground: Reloading weather data
[Error 14:15:08.082] Error in RunOnMainThread: Path is too long. Path: OpenOffice.org Word Processor: Create and edit text and graphics in letters, reports, documents and Web pages. (Do.Universe.Linux.ApplicationItem)
[Debug 14:15:08.109] [AbstractWeatherSource] Weather Underground: Fetching XML file 'http://api.wunderground.com/auto/wui/geo/WXCurrentObXML/index.xml?query=50014'
[Debug 14:15:08.110]   at System.IO.Directory.Exists (System.String path) [0x00000] 
  at Docky.Core.Default.ItemsService.MaybeCreateCustomItem (System.String& identifier) [0x00000] 
  at Docky.Core.Default.ItemsService.InternalAddItemToDock (System.String identifier, Int32 position) [0x00000] 
  at Docky.Core.Default.ItemsService.UpdateItems () [0x00000] 
  at Docky.Core.Default.ItemsService.HandleUniverseInitialized (System.Object sender, System.EventArgs e) [0x00000] 
  at (wrapper delegate-invoke) System.EventHandler:invoke_void__this___object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.EventHandler:invoke_void__this___object_EventArgs (object,System.EventArgs)
  at Do.Core.UniverseManager.<InitializeAsync>m__1F () [0x00000] 
  at Do.Platform.ApplicationService+<RunOnMainThread>c__AnonStorey10.<>m__29 (System.Object sender, System.EventArgs e) [0x00000] 
[Debug 14:15:13.477] [AbstractWeatherSource] Weather Underground: Fetching XML file 'http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=50014'
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IO.PathTooLongException: Path is too long. Path: OpenOffice.org Word Processor: Create and edit text and graphics in letters, reports, documents and Web pages. (Do.Universe.Linux.ApplicationItem)
  at System.IO.Directory.Exists (System.String path) [0x00000] 
  at Docky.Core.Default.ItemsService.MaybeCreateCustomItem (System.String& identifier) [0x00000] 
  at Docky.Core.Default.ItemsService.InternalAddItemToDock (System.String identifier, Int32 position) [0x00000] 
  at Docky.Core.Default.ItemsService.UpdateItems () [0x00000] 
  at Docky.Core.Default.ItemsService.ForceUpdate () [0x00000] 
  at Docky.Interface.DockArea.<HandlePainterHideRequest>m__3B () [0x00000] 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Do.Do.Main(System.String[] args)
```

I've tried removal and complete removal, even searching for all gnome-do files as root and just plain deleting them, but every time i resintall, this shortcut is back and killing my gnome-do. any ideas on what file i can modify to remove the problem shortcut?

---

### Post by Shellboy on 2009-12-24
I have the same problem here after adding open office as a starter to docky. Did u find a way to fix this?

Cheers Frank

---

### Post by Shellboy on 2009-12-25
Hi! 

I have found a workaround by deleting the folder ~/.local/share/gnome-do in my home directory and not putting writer back on docky.

---

### Post by arcane14 on 2010-01-10
> **Shellboy said:**
> Hi! 

I have found a workaround by deleting the folder ~/.local/share/gnome-do in my home directory and not putting writer back on docky.
thanks! this worked like a charm.

---

### Post by amattheisen on 2010-05-06
Awesome! - worked for me too.

---

### Post by helpful-hermet on 2011-02-20
hi,
it's sufficient to shorten the path in .local/share/gnome-do/ItemsService_CustomItems.
This way you won't throw away all you other gnome-do configurations, statistics etc. :)

---

