---
title: "Sage 200 in Wine Ubuntu 11.10"
date: 2012-01-25
forum: General Help
---

### Post by shaneo1 on 2012-01-25
Im moving to ltsp, but the company uses Sage 200 mms which is their accounting software. It's really only for windows, but I have managed to install it using wine. But it need the login credentials from the windows server hosting sage server, which uses ms SQL as the database.  Has any one had any dealings with this trying to gt it to work with Ubuntu and wine.

If so please let me know or maybe you could assist me.  For now I have vbox with an instance of windows xp installed with the sage client on it, although it works in the thin clients it's a little bit juddery.

Ideally I would just like my Ubuntu server to talk to the windows sage server and share the sage client with all my thin clients.  I have licenses for all the versions of windows xp in vbox now, so I'm covered, but I would like to ditch vbox in favour to run sage 200 in wine. 

Thanks in advance guys. Your help would benefit my position greatly.

---

### Post by Mark Phelps on 2012-01-26
If it's anything like the sofware referenced in the linked WineHQ page, you're wasting your time:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8489]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=8489")

---

### Post by shaneo1 on 2012-01-26
Hi mark no, its more like Sage Line 50

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1098](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1098)

but thanks for your reply

---

### Post by Mark Phelps on 2012-01-26
OK, then, suggest you read through the Testing Results on the page you found and see if anything there helps.  Bronze is pretty much a waste of time, as well, but Silver might give you enough functionality to actually be useful.

Generally, anything you need to rely on daily needs to be rated Gold or better to be worth your time setting it up and configuring it to work.

---

### Post by shaneo1 on 2012-01-26
Thanks for your advice Mark.

I will see what I can find out. 

Thanks again for your time.

---

### Post by shaneo1 on 2012-01-26
I have installed msxml3.dll and mono 2.6 now when I come to run Sage200Desktop.exe this is the output:

```
shane@IT-MANAGER:~/.wine/drive_c/Program Files/Sage/Sage200$ wine Sage200Desktop.exe 
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"configSections" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"sectionGroup" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"section" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"section" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"section" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"section" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"section" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"sectionGroup" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"section" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"section" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"unity" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"typeAliases" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"typeAlias" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"typeAlias" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"containers" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"container" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"types" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"type" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"userSettings" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"Infragistics.Win.UltraWinDock.UltraDockManager.DeskTopForm.UltraDockManager" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"base64Binary" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"Infragistics.Win.UltraWinExplorerBar.UltraExplorerBar.DeskTopForm._NavigationStackBar" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"base64Binary" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"Infragistics.Win.UltraWinToolbars.UltraToolbarsManager.DeskTopForm._NavigationToolBars" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"base64Binary" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"Sage.MMS.Desktop.Properties.Settings" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"applicationfiles" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"file" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"file" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"file" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"LoadApplications" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"defaultToolBars" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbars" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbar" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTools" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbar" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTools" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"toolbarTool" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"SageMMSDeskTop.Properties.Settings" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"applicationSettings" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"Sage.MMS.Desktop.Properties.Settings" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"setting" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"value" in state 3

** (Sage200Desktop.exe:96): WARNING **: The following assembly referenced from C:\Program Files\Sage\Sage200\Sage200Desktop.exe could not be loaded:
     Assembly:   Infragistics2.Win.UltraWinToolbars.v8.2    (assemblyref_index=10)
     Version:    8.2.20082.1000
     Public Key: 7dd5c3163f2cd0cb
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (C:\Program Files\Sage\Sage200\).


** (Sage200Desktop.exe:96): WARNING **: Could not load file or assembly 'Infragistics2.Win.UltraWinToolbars.v8.2, Version=8.2.20082.1000, Culture=neutral, PublicKeyToken=7dd5c3163f2cd0cb' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Sage.MMS.Desktop.DeskTopForm' from assembly 'Sage200Desktop, Version=15.0.31.0, Culture=neutral, PublicKeyToken=affbf938bc5e4d7b'.
err:mscoree:expect_no_runtimes Process exited with a Mono runtime loaded.

```

Would this be something that could be fixed in wine?

---

