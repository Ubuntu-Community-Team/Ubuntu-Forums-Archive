---
title: "wine: pokerclient wont open new tables? (wine says the aplication is already running)"
date: 2006-06-01
forum: General Help
---

### Post by marken on 2006-06-01
Im trying to get my poker-client to run under wine (Svenska Spel). I
get wine to start it up with:
$wine poker.exe

i then get some error but it starts just as nice as in windows, here
are the text:

err:wave:DSDB_MapBuffer Could not map sound device for direct access
(Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:wininet:InternetGetConnectedState always returning LAN
connection.
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list
snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel
(0x7fdee550)->((nil),00000008)
DynamicLibrary::LoadLibrary: Failed to load
'gs3functioninterfaceDBG.dll'.
DynamicLibrary::LoadLibrary: Failed to load 'gs3functioninterface.dll'.
DynamicRNGClient::DynamicRNGClient: Library 'gs3functioninterface.dll'
not loaded.

I guess the sound is easy to fix, even though it works.

Anyway, i log into my account and everyting works fine untill i try to
open a table. Then wine spits out the following line in the terminal:

fixme:exec:SHELL_execute flags ignored: 0x00000400

And also a window oppens which says: "Error, A Boss Media gaming
software is already running on this computer!"

There is no problem to open a table in fullscreen, bt then i can only
play one table, which is not enough.

thanks in advance for the help.

---

