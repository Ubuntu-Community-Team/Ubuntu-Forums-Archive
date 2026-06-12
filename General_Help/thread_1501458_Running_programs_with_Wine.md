---
title: "Running programs with Wine"
date: 2010-06-04
forum: General Help
---

### Post by sr.vinay on 2010-06-04
I can run a few programs with Wine. But, when I run Counter Strike, the game just closes after the loading is complete. The game worked before I configured my graphics driver. After I configured it, the game has stopped working.
What could be the reason? How can I fix it?

---

### Post by pedro_orange on 2010-06-04
For in depth information regarding the specific application you're running, please visit appdb.winehq and find the relevant application. 

I would imagine you have either configured your graphics card incorrectly, or you have loaded an incompatible driver. How exactly did you configure your graphics? 

You should try running the game from the terminal so you can see what error messages are being spat out. This usually helps in debugging issues.

---

### Post by dino99 on 2010-06-04
[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=3731](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=3731)

---

### Post by moonport on 2010-06-04
Sounds like a video configuration issue.
BTW, check the fonts in your dir  /home/user/.wine/drive_c/windows/fonts/.
Remember you need the Windows' tahoma.ttf (you can download it from [http://resources.bravenet.com/free_fonts/standard/tahoma/download/](http://resources.bravenet.com/free_fonts/standard/tahoma/download/))

---

### Post by sr.vinay on 2010-06-04
>  I would imagine you have either configured your graphics card incorrectly, or you have loaded an incompatible driver. How exactly did you configure your graphics? 

I let Ubuntu do the configuration. I downloaded the appropriate driver from the company website and then scanned my system using the "Hardware Driver manager". There, I activated the driver. It connected to the net and did the configuration.

---

### Post by sr.vinay on 2010-06-04
**The end of the output in the terminal looked something like this:**
wine /media/**/Games/Half-Life/czero.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise->(1 00000002)
fixme:shdocvw:PersistStreamInit_InitNew 
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser ->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget ->(ffffffff)
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan : stub
fixme:shdocvw:ViewObject_SetAdvise ->(1 00000002)
fixme:shdocvw:PersistStreamInit_InitNew 
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget ->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x6ed2008)->(1 00000002)
fixme:shdocvw:PersistStreamInit_InitNew )
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser ->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate 
fixme:shdocvw:OleInPlaceObject_UIDeactivate
fixme:shdocvw:OleObject_Close ->(1)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd
fixme:iphlpapi:NotifyAddrChange (Handle overlapped 0xbdce8e0): stub
0[210ed8]: IMM32: InitKeyboardLayout, aKeyboardLayout=04090409, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus ->((null) 1  (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 000000f0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsChannel_Open ->
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate 
fixme:shdocvw:OleInPlaceObject_UIDeactivate 
fixme:shdocvw:OleObject_Close ->(1)
fixme:shdocvw:ViewObject_Draw ->(1 -1 (nil) (nil) 0xcf8 0xd10 0x32f838 (nil) (nil) 00000000)
fixme:resource:GetGuiResources (0): stub
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget 
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer 
fixme:shdocvw:InPlaceFrame_SetStatusText ->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:HTMLBodyElement_put_scroll ->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll ->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll ->(L"no")
fixme:winmm:MMDRV_Exit Closing while ll-driver open
File z:\media\**\games\half-life\czero\demoheader.dmf was never closed

---

### Post by pedro_orange on 2010-06-04
Did you check the link dino99 posted above? 

In the known issues it says:

```
Counter Strike crashes as soon as it starts or you join a game. 
You most likely have other program(s) using sound. Run winecfg and select only ALSA sound driver. OSS is not the best choice anymore. 

For Ubuntu 8.04 and up - kill/disable pulseaudio. It is not compatible with Wine. And will cause all sorts of problems if left running. 

Another possible reason - you have "Steam Community In-Game" enabled. It does not work properly on Wine and causes all games to crash. Please disable it in settings -> In-game tab.
```

Also what version of WINE are you using? Doing a quick google for "demoheader.dmf was never closed" suggests updating WINE solved the issue for a number of users.

---

### Post by sr.vinay on 2010-06-04
Those audio settings like the one with ALSA I had already done.
The game still crashes. And, I've the latest version of WINE.

---

### Post by sr.vinay on 2010-06-04
I think it should be a problem with my graphics configuration.
The game used to work fine before I configured my graphics card.
I think the problem lies in the fact that I have an ATI card.
The drivers aren't that good with linux.
Anyone know how to fix it (the crash and the graphics driver)?

---

