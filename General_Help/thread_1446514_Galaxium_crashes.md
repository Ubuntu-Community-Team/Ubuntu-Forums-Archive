---
title: "Galaxium crashes"
date: 2010-04-04
forum: General Help
---

### Post by sven.cintern on 2010-04-04
Hi, 
I'm wondering how to change the proxy settings for galaxium from terminal. 
I've been using galaxium, and recently, I've needed a proxy for it, so I added with the galaxium pref, but accidentally saved half-way through adding the proxy, and now when galaxium launches it crashes instantly.  I've done complete removals, and even searched and deleted any galaxium prefs I could find, but everytime I reinstall, it still crashes. 
Here's what I get when I launch from terminal. [INDENT][FONT=Courier New]username@username-laptop:~$ galaxium
Galaxium Messenger
Copyright (C) 2003-2008 Philippe Durand <draekz@gmail.com>
Copyright (C) 2006-2008 Ben Motmans <ben.motmans@gmail.com>
Copyright (C) 2007-2008 Paul Burton <paulburton89@gmail.com>

Running in DEBUG mode, appName Galaxium
2010/04/04 21:25:30 [INFO] [CoreUtility.Initialize] Using application directory: /usr/lib/galaxium
2010/04/04 21:25:31 [DEBUG] [CoreUtility.Initialize] Data Directory: /usr/share/galaxium
2010/04/04 21:25:31 [INFO] [AddinUtility.Initialize] Initializing add-in manager...
2010/04/04 21:25:31 [INFO] [AddinUtility.Initialize] Rebuilding the add-in registry...
Checking: /usr/lib/galaxium
Folders checked (18 ms)
Looking for addins
Using assembly reflector: Mono.Addins.CecilReflector.Reflector
Checking: /usr/lib/galaxium
Checking: /home/sven/.config/Galaxium/addins
Scanning file: /usr/lib/galaxium/Galaxium.AdiumThemes.dll
Scanning file: /usr/lib/galaxium/Galaxium.Client.GtkGui.dll
Scanning file: /usr/lib/galaxium/Galaxium.Client.dll
Scanning file: /usr/lib/galaxium/Galaxium.Core.dll
Scanning file: /usr/lib/galaxium/Galaxium.GStreamer.dll
Scanning file: /usr/lib/galaxium/Galaxium.Gui.GtkGui.dll
Scanning file: /usr/lib/galaxium/Galaxium.Gui.dll
Scanning file: /usr/lib/galaxium/Galaxium.Protocol.Gui.dll
Scanning file: /usr/lib/galaxium/Galaxium.Protocol.Msn.GtkGui.dll
Scanning file: /usr/lib/galaxium/Galaxium.Protocol.Msn.dll
Scanning file: /usr/lib/galaxium/Galaxium.Protocol.dll
Scanning file: /usr/lib/galaxium/Galaxium.Startup.exe
Scanning file: /usr/lib/galaxium/Galaxium.WebKit.dll
Scanning file: /usr/lib/galaxium/libswfdec-sharp.dll
Folders scan completed (748 ms)
Regenerating all add-in relations.
Generating add-in extension maps
Addin relation map generated.
  Addins Updated: 12
  Extension points: 31
  Extensions: 33
  Extension nodes: 302
  Node sets: 3
Add-in relations analyzed (49 ms)
2010/04/04 21:25:32 [WARNING] [GLibLogging.LogFunc] GLib-Warning: g_set_prgname() called multiple times
Stack trace: 
   at GLib.Global.set_ProgramName(System.String value)
   at Gtk.Application.SetPrgname()
   at Gtk.Application.Init()
   at Galaxium.Client.GtkGui.MainWindow.ExecuteEntryPoint(System.Object[] args)
   at Galaxium.Core.EntryPointExtension.Execute(System.Object[] args)
   at Galaxium.Core.AddinUtility.Initialize()
   at Galaxium.Startup.Program..ctor(Boolean debug, System.String appName)
   at Galaxium.Startup.Program.Main(System.String[] args)
2010/04/04 21:25:32 [DEBUG] [GtkUtility.Initialize] Initializing gtk utility...
2010/04/04 21:25:32 [DEBUG] [IconUtility.Initialize] Initializing icon utility...
2010/04/04 21:25:32 [DEBUG] [IconUtility.Initialize] Initializing icon & animation theme: default
2010/04/04 21:25:32 [INFO] [GtkUtility.Initialize] Unable to find libswfdec-0.6, swf playback disabled
2010/04/04 21:25:32 [INFO] [SoundUtility.set_ActiveBackend] Using sound backend: Galaxium.GStreamer.GStreamerSoundBackend
2010/04/04 21:25:32 [DEBUG] [EmoticonUtility.Initialize] Initializing emoticon utility...
2010/04/04 21:25:32 [DEBUG] [SoundSetUtility.Initialize] Initializing sound set utility...
2010/04/04 21:25:32 [FATAL] [GLibLogging.LogFunc] Gtk-Critical: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
Stack trace: 
   at Glade.XML..ctor(System.IO.Stream s, System.String root, System.String domain)
   at Galaxium.Client.GtkGui.MainWindow..ctor()
   at Galaxium.Client.GtkGui.MainWindow.ExecuteEntryPoint(System.Object[] args)
   at Galaxium.Core.EntryPointExtension.Execute(System.Object[] args)
   at Galaxium.Core.AddinUtility.Initialize()
   at Galaxium.Startup.Program..ctor(Boolean debug, System.String appName)
   at Galaxium.Startup.Program.Main(System.String[] args)
2010/04/04 21:25:32 [DEBUG] [MsnClientConfig.RequestConfig] Requesting client config from [http://config.messenger.msn.com/Config/MsgrConfig.asmx?op=GetClientConfig&Country=&CLCID=1409&PLCID=0000](http://config.messenger.msn.com/Config/MsgrConfig.asmx?op=GetClientConfig&Country=&CLCID=1409&PLCID=0000)
2010/04/04 21:25:33 [DEBUG] [TCPConnection.Connect] Connect to 64.4.34.154:1863
2010/04/04 21:25:33 [FATAL] [Program.Main] Fatal exception while running Galaxium.
FormatException: An invalid IP address was specified.
  at System.Net.IPAddress.Parse (System.String ipString) [0x00000] 
  at System.Net.Dns.GetHostByAddressFromString (System.String address, Boolean parse) [0x00000] 
  at System.Net.Dns.GetHostByAddress (System.String address) [0x00000] 
  at Galaxium.Protocol.SocksSocket.ConnectToSocks5Proxy (System.String proxyAdress, UInt16 proxyPort, System.String destAddress, UInt16 destPort, System.String userName, System.String password) [0x00000] 
  at Galaxium.Protocol.TCPConnection.Connect () [0x00000] 
  at Galaxium.Protocol.Msn.CommandConnection.Connect () [0x00000] 
  at Galaxium.Protocol.Msn.MsnSession.Connect () [0x00000] 
  at Galaxium.Gui.GtkGui.BasicAccountWidget.ConnectButtonClicked (System.Object sender, System.EventArgs args) [0x00000] 
  at Galaxium.Protocol.Msn.GtkGui.MsnAccountWidget.ConnectButtonClicked (System.Object sender, System.EventArgs args) [0x00000] 
  at Galaxium.Gui.GtkGui.BasicAccountWidget.Connect () [0x00000] 
  at Galaxium.Client.GtkGui.MainWindow..ctor () [0x00000] 
  at Galaxium.Client.GtkGui.MainWindow.ExecuteEntryPoint (System.Object[] args) [0x00000] 
  at Galaxium.Core.EntryPointExtension.Execute (System.Object[] args) [0x00000] 
  at Galaxium.Core.AddinUtility.Initialize () [0x00000] 
  at Galaxium.Startup.Program..ctor (Boolean debug, System.String appName) [0x00000] 
  at Galaxium.Startup.Program.Main (System.String[] args) [0x00000] 
username@username-laptop:~$
[/FONT][/INDENT]thanks in advance!
Steve

---

### Post by sven.cintern on 2010-04-07
bump :P

---

