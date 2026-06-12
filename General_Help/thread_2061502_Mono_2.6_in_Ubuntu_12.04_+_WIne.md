---
title: "Mono 2.6 in Ubuntu 12.04 + WIne"
date: 2012-09-22
forum: General Help
---

### Post by CrusaderAD on 2012-09-22
I can't find any modern threads or support for this error message. Any ideas? Trying to play a game with playonlinux but it crashes and displays this in the debugger.

```
wine: Install Mono 2.6 for Windows to run .NET 1.1 applications.
```

---

### Post by CrusaderAD on 2012-09-22
Playonlinux let's you install mono 2.6 right from it's settings. Now I can launch the program, but I've hit a new wall. Any ideas?

> [09/22/12 16:53:43] - Running wine- dndlauncher.exe
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"system.windows.forms" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"requiredRuntime" in state 2
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"appSettings" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"add" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"add" in state 3
err:mscoree:CLRMetaHost_GetRuntime Cannot parse L"V1.1.4322"
fixme:gameux:GameExplorerImpl_VerifyAccess (0x1cb920, L"C:\\Program Files\\Turbine\\DDO Unlimited\\DDO.gdf.dll", 0x33fa78)
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"system.windows.forms" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"requiredRuntime" in state 2
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"appSettings" in state 1
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"add" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"add" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"add" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"add" in state 3
fixme:mscoree:ConfigFileHandler_startElement Unknown element L"add" in state 3
err:mscoree:CLRMetaHost_GetRuntime Cannot parse L"V1.1.4322"
fixme:secur32:schan_QueryCredentialsAttributes SECPKG_ATTR_CIPHER_STRENGTHS: semi-stub
fixme:gdiplus:GdipAddPathString (0x147e330, L"COMMUNITY", 9, 0x16658f8, 0, 11.000000, 0x33ed50, 0x146cf60): stub
fixme:gdiplus:GdipAddPathString (0x147e330, L"ACCOUNT", 7, 0x16658f8, 0, 11.000000, 0x33ed50, 0x146cf60): stub
fixme:gdiplus:GdipAddPathString (0x147e330, L"SUPPORT", 7, 0x16658f8, 0, 11.000000, 0x33ed50, 0x146cf60): stub
fixme:gdiplus:GdipAddPathString (0x147e330, L"COMMUNITY", 9, 0x16658f8, 0, 11.000000, 0x33ed30, 0x147e230): stub
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:resample_bitmap_pixel Unimplemented interpolation 7
fixme:gdiplus:GdipAddPathString (0x147e068, L"ACCOUNT", 7, 0x16658f8, 0, 11.000000, 0x33ed30, 0x147e030): stub
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipAddPathString (0x1683b70, L"SUPPORT", 7, 0x16658f8, 0, 11.000000, 0x33ed30, 0x12e7a48): stub
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipAddPathString (0x1876d78, L"Update", 6, 0x1756830, 0, 15.000000, 0x33e510, 0x1876cc0): stub
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipAddPathString (0x1876a10, L"Continue", 8, 0x1756830, 0, 15.000000, 0x33e510, 0x1876d78): stub
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
err:mscoree:expect_no_runtimes Process exited with a Mono runtime loaded.

---

