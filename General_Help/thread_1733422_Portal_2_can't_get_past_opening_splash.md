---
title: "Portal 2 can't get past opening splash"
date: 2011-04-19
forum: General Help
---

### Post by topdownjimmy on 2011-04-19
Portal 1 has been working great for me, but I can't seem to get Portal 2 past the opening splash screen.

I've disabled Compiz, for what it's worth.  Anybody else having this problem?

```
jay@jay-desktop:~$ env WINEPREFIX="/home/jay/.wine" wine C:\\Program\ Files\\Steam\\steam.exe -silent -applaunch 620 -window -novid -width 1680 -height 1050
fixme:advapi:SetNamedSecurityInfoW L"Nitro PDF Reader" 3 4 (nil) (nil) 0x18ed98 (nil)
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:alsa:ALSA_CheckSetVolume Could not find '{PCM,Line} Playback Volume' element
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x14ce270, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x431be50)
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:win:EnumDisplayDevicesW ((null),0,0x32c584,0x00000000), stub!
fixme:advapi:RegisterTraceGuidsW (0x38e5290, 0x3f3b738, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x3f13b24, (null), (null), 0x3f3b750,)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x10148
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33e1b8,0x00000000), stub!
Using breakpad crash handler
Setting breakpad minidump AppID = 620
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198026698008 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198026698008
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x41415353) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x41415353) in the format lookup table
Convar r_flashlightscissor has conflicting FCVAR_CHEAT flags (child: no FCVAR_CHEAT, parent: has FCVAR_CHEAT, parent wins)
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x199fa8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e110)
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33de4c, uiNumDevices=1, cbSize=12) stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
Convar building_cubemaps has conflicting FCVAR_CHEAT flags (child: has FCVAR_CHEAT, parent: no FCVAR_CHEAT, parent wins)
Game.dll loaded for "Half-Life 2"
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0x2b0): stub
fixme:thread:SetThreadIdealProcessor (0x2d0): stub
fixme:thread:SetThreadIdealProcessor (0x2ec): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:dbghelp:elf_search_auxv can't find symbol in module
```

---

### Post by lovinglinux on 2011-04-19
I wouldn't expect it to work so soon. If you are planning to use Linux as gaming platform, exclusively, I would recommend waiting a few months before buying new games like Portal 2 and monitor winedb for news.

---

### Post by Sillywombat on 2011-04-19
Well, I guess thats replies my question:
[http://ubuntuforums.org/showthread.php?t=1733491](http://ubuntuforums.org/showthread.php?t=1733491)

What LovingLinux said is right.... as usual.
Since I started using my main Ubuntu partition as my gaming rig, and installed steam, I have noticed that the easier windows-only games usually work well, but the main titles, 3D enabled, multiplatform games tend to have a problem, or needs tweeking.
Plus seeming as the game has only been out for what I understand, is serveral hours, your going to have to wait a bit to see if someone comes across a workaround, or a patch either with wine or the game itself.

What I can tell you is this doesnt seem to be a wine only problem according to some people:
forums.steampowered.com/forums/showthread.php?t=1847517 
(But I doubt this is the same bug as the windows users are reporting)

---

### Post by Sillywombat on 2011-04-19
BTW, forgot to ask.
Have you tried using [Playonlinux]("http://www.playonlinux.com")?

---

### Post by topdownjimmy on 2011-04-19
For people with the same problem:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23278](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23278)
[http://bugs.winehq.org/show_bug.cgi?id=26835](http://bugs.winehq.org/show_bug.cgi?id=26835)

---

### Post by VeeDubb on 2011-05-01
I've read both of the discussions linked to in the last post, and they are contradictory.

One says that it's a program bug that affects everyone.  The other makes it pretty clear that it's a bug that is mostly or entirely unique to people using an "unsupported" OS.

Has anyone made any progress in getting this to work through the Steam app without resorting to anything of questionable legality?

I bought the game because codeweavers listed it as Silver, only to find out that in this case, their idea of "Silver" is along the lines of "installs fine, but crashes after the splash screen."

---

