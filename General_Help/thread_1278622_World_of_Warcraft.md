---
title: "World of Warcraft"
date: 2009-09-29
forum: General Help
---

### Post by DarkMage2303 on 2009-09-29
I've followed the Ubuntu World of Warcraft guide, so please don't just link it.

When I try to run WoW (using WINE 1.0.1) the game loads properly, I get to the loading screen and at the end of the loading screen the game just freezes.

**Quote from the Terminal:**

> scott@scott-laptop:~$ wine "/media/FreeAgent Drive/Games/World of Warcraft/WoW.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ec9c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f510,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f500,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f008,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37404524) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20024, 0x1386f8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39dae4,0x00000000), stub!
failed to open Z:/media/FreeAgent Drive/Games/World of Warcraft/Data/Interface/Icons
failed to open Z:/media/FreeAgent Drive/Games/World of Warcraft/Interface/Icons
err:ntdll:RtlpWaitForCriticalSection section 0x5ea3d7c "?" wait timed out in thread 0022, blocked by 0009, retrying (60 sec)



---

### Post by korin43 on 2009-09-29
On WineHQ it says:

**How to get World Of Warcraft 3.2. to work on wine 1.1.29**
Open the wine configurator program.

The text and graphics display on the menu won't work (everything gray) unless you uncheck the 'Alow pixel shader' option in the Direct3D section of the graphics tab.

The sound won't work if you have the os set to Vista, but sound will work perfectly if you set the os to XP (I haven't tried other windows versions).


If that doesn't help, I'd install a newer version of wine and see if that helps.

---

### Post by DarkMage2303 on 2009-09-29
Updated WINE to the development version, unticked that box. Now I'm starting WoW again.

EDIT: Same error

> scott@scott-laptop:~$ wine "/media/FreeAgent Drive/Games/World of Warcraft/WoW.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed5c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39eb5c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f260,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f538,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f534,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4c0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39efb8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0f0,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13e1c8,0x16f4b8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39de9c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ded4,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404524) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20030, 0x13cc98): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39da94,0x00000000), stub!
failed to open Z:/media/FreeAgent Drive/Games/World of Warcraft/Data/Interface/Icons
failed to open Z:/media/FreeAgent Drive/Games/World of Warcraft/Interface/Icons
err:ntdll:RtlpWaitForCriticalSection section 0x5d9e844 "?" wait timed out in thread 0021, blocked by 0009, retrying (60 sec)


---

### Post by DarkMage2303 on 2009-09-30
bump

---

### Post by DarkMage2303 on 2009-10-02
bump

---

### Post by DarkMage2303 on 2009-10-03
Bring
Up
My
Post

can anyone help?

---

### Post by NexusZA on 2010-02-22
I have the same timeout error. One thing I think that may affect is that I notice your WoW directory is sitting on n external drive which I would bet is an NTFS formatted drive.. correct?

My WoW directory is sitting in the same place so I am at the moment just copying WoW to my EXT partition (home directory) and will test there to see if it helps and let you know.

My timeout message happens however when I log out and causes logout to take aaaaagggeeeessss....

---

### Post by ravisghosh on 2010-03-19
I'm getting the same error while trying to run utorrent over wine. OF note is the fact that it was working fine yesterday and I have not updated/installed/uninstalled anything.

---

