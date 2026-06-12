---
title: "WoW - Black Screen?"
date: 2010-11-24
forum: General Help
---

### Post by Selim873 on 2010-11-24
Before, WoW kept crashing with a memory cannot be read error when it was in D3D mode, when I set it to OpenGL, the opening video sequences are completely white, and when I get to the menu, it shows nothing, but I can still navigate, knowing because I can hear different sounds supposedly by clicking around...  WoW only worked once, it was in D3D mode, the very first time I loaded it up and just ran around, it never crashed, it closed when I told it to.  Now it's not working... I want it to be working before my 10 day trial is over (December 2nd).
WoW works perfectly on my brother's Netbook with Windows 7, I have the exact same model, but I was stupid to not dual boot.
I tried Wine1.0, Wine1.2, and Wine1.3, no fix, at the time it worked, I had wine1.2.

Here's the log on the terminal, It must be a graphical issue.

[SIZE="5"]Direct3D Mode[/SIZE]
```
ty@ty-laptop:~$ wine --version
wine-1.2.1
ty@ty-laptop:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
archive Data\enUS\base-enUS.MPQ opened
archive Data/Cache/SoundCache-3.MPQ opened
archive Data/Cache/SoundCache-2.MPQ opened
archive Data/Cache/SoundCache-1.MPQ opened
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enUS/SoundCache-enUS.MPQ opened
archive Data/wow-update-13164.MPQ opened
archive Data/Cache/enUS/patch-enUS-13164.MPQ opened
archive Data/Cache/patch-base-13164.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13164.MPQ opened
archive Data/Cache/SoundCache-patch-13164.MPQ opened
archive Data/wow-update-13205.MPQ opened
archive Data/Cache/enUS/patch-enUS-13205.MPQ opened
archive Data/Cache/patch-base-13205.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13205.MPQ opened
archive Data/Cache/SoundCache-patch-13205.MPQ opened
archive Data/wow-update-13287.MPQ opened
archive Data/Cache/enUS/patch-enUS-13287.MPQ opened
archive Data/Cache/patch-base-13287.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13287.MPQ opened
archive Data/Cache/SoundCache-patch-13287.MPQ opened
archive Data/wow-update-13329.MPQ opened
archive Data/Cache/enUS/patch-enUS-13329.MPQ opened
archive Data/Cache/patch-base-13329.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13329.MPQ opened
archive Data/Cache/SoundCache-patch-13329.MPQ opened
archive Data\art.MPQ opened
archive Data\world.MPQ opened
archive Data\sound.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed7c,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea48,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3f0,0x00000000), stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x32f198,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee64,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1871c0,0x17e710): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1871c0,0x17e710): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x32f870): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f338,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f004,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
Unable to read archive hash/block table: "Data/wow-update-13287.MPQ"
err:d3d:loadNumberedArrays >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading numbered arrays @ state.c / 4203
ty@ty-laptop:~$ 

```

[SIZE="5"]OpenGL Mode[/SIZE]
```
ty@ty-laptop:~$ wine --version
wine-1.2.1
ty@ty-laptop:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
archive Data\enUS\base-enUS.MPQ opened
archive Data/Cache/SoundCache-3.MPQ opened
archive Data/Cache/SoundCache-2.MPQ opened
archive Data/Cache/SoundCache-1.MPQ opened
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enUS/SoundCache-enUS.MPQ opened
archive Data/wow-update-13164.MPQ opened
archive Data/Cache/enUS/patch-enUS-13164.MPQ opened
archive Data/Cache/patch-base-13164.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13164.MPQ opened
archive Data/Cache/SoundCache-patch-13164.MPQ opened
archive Data/wow-update-13205.MPQ opened
archive Data/Cache/enUS/patch-enUS-13205.MPQ opened
archive Data/Cache/patch-base-13205.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13205.MPQ opened
archive Data/Cache/SoundCache-patch-13205.MPQ opened
archive Data/wow-update-13287.MPQ opened
archive Data/Cache/enUS/patch-enUS-13287.MPQ opened
archive Data/Cache/patch-base-13287.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13287.MPQ opened
archive Data/Cache/SoundCache-patch-13287.MPQ opened
archive Data/wow-update-13329.MPQ opened
archive Data/Cache/enUS/patch-enUS-13329.MPQ opened
archive Data/Cache/patch-base-13329.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13329.MPQ opened
archive Data/Cache/SoundCache-patch-13329.MPQ opened
archive Data\art.MPQ opened
archive Data\world.MPQ opened
archive Data\sound.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed7c,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f198,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee64,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x169620,0x172480): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x169620,0x172480): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x32f870): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f338,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f004,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
Unable to read archive hash/block table: "Data/wow-update-13287.MPQ"
Unable to read archive hash/block table: "Data/wow-update-13287.MPQ"
ty@ty-laptop:~$ 

```

---

### Post by infernowolf36 on 2010-12-08
i've got the same problem 

fixme:win:EnumDisplayDevicesW ((null),0,0x32ed7c,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f198,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee64,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x168d28,0x171698): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x168d28,0x171698): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x32f870): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f338,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f004,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000

---

