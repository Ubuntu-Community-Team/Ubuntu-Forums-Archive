---
title: "(Wine 1.2) World of Warcraft Fall of the Lich King: Blank Screen"
date: 2010-03-31
forum: General Help
---

### Post by emivanbuuren on 2010-03-31
Hello, I'm a Ubu-newbie... I have a problem with WoW 3.3, when it starts I get a Black Screen, but I can hear the sound, and the windows responds to keypresses (like, pressing Esc exits the game, o when I press enter I hear the sound of logging in).

I have a Lenovo G530, with Intel GMA X4500 as display processor. I think that the drivers are working fine, as I can run all the OpenGL games without problems. I have Ubu 9.10 and Wine 1.2. I've tried many solutions posted on this forums and WowWiki.

When I run the game from a console with **wine "/home/xxxx/Storage/Games/wow3/Wow.exe" -opengl -windowed**, it outputs:
```
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\enGB\patch-enGB-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed2c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39eb1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f370,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f504,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0c0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39de70,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39de98,0x00000000), stub!
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
archive data\enGB\agreements.mpq opened
```
Any help would be very appreciated,

Thanks in advance,
Emiliano

---

### Post by jus^ on 2010-04-18
Hi,

I have the exact same problem. Any solutions?

---

