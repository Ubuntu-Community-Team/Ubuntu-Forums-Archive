---
title: "PlayOnLinux: Steam will not launch any games"
date: 2011-10-28
forum: General Help
---

### Post by Impossible9 on 2011-10-28
I installed Steam & Counter-Strike: Source using PlayOnLinux.

However, whenever I try to launch any Steam games(I tried this with Wine alone too with several versions), it says "Preparing to launch game", closes, the game seems to start for a second as the frame around my avatar turns green and then back to blue.
But then nothing happens.

PlayOnLinux log when I launch Counter-Strike: Source:
```
[POL_Wine_SetVersionEnv] Message: Setting wine version path: 1.3.25, x86
[POL_Wine_SetVersionEnv] Message: "/home/impossible/.PlayOnLinux//wine/linux-x86/1.3.25" exists
[POL_Wine] Message: Running wine-1.3.25 Steam.exe -applaunch 240
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x94e6d4 0x94e6cc
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 6 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x1dbbd8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x4a2c668)
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:create_server class {dff32fea-3331-48da-a272-ccfc238695be} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {dff32fea-3331-48da-a272-ccfc238695be} could be created for context 0x17
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x94e6d0 0x94e6c8
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x94e6d0 0x94e6c8
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x94e714 0x94e70c
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x94e6d4 0x94e6cc
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:win:RegisterDeviceNotificationA (hwnd=0x100be, filter=0x32d5e4,flags=0x00000004) returns a fake device notification handle!
fixme:win:EnumDisplayDevicesW ((null),0,0x32c4d0,0x00000000), stub!
fixme:advapi:RegisterTraceGuidsW (0x3392630, 0x3e2b7b8, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x3dfd5f8, (null), (null), 0x3e2b7d0,): stub
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x10140
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x94e6d0 0x94e6c8
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0x94e6d0 0x94e6c8
err:ole:RevokeDragDrop invalid hwnd (nil)
fixme:win:UnregisterDeviceNotification (handle=0xcafecafe), STUB!
fixme:advapi:UnregisterTraceGuids 0: stub
Shutting down. . .
[POL_Wine] Message: Wine return: 0
```

My Specs Are:
Intel® Core™ i5-2400 CPU @ 3.10GHz × 4 
GeForce GTX 570/PCI/SSE2 

I'm using the Proprietary drivers for my GTX 570. 
The drivers are activated.

I tried completely uninstalling compiz, it didn't help.

Thanks in advance for your help, and please let me know if you need any additional info. :D

---

