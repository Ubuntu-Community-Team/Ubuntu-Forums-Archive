---
title: "Need help with Dolphin Emulator"
date: 2010-10-24
forum: General Help
---

### Post by ivarn on 2010-10-24
Hey.
I can't get this Dolphin-emu to work.
When I install it and run it from the games menu nothing happens.
And from the terminal I'm getting this error message:
> dolphin-emu: symbol _ZN12wxAuiToolBar12ms_classInfoE, version WXU_2.8 not defined in file libwx_gtk2u_aui-2.8.so.0 with link time reference

So, what's wrong with this package and how can I fix this problem?
Thanx in advance:)

---

### Post by ivarn on 2010-10-25
Bump

---

### Post by emoguitarist06 on 2010-11-04
[COLOR="Red"]**BUMP**[/COLOR]

I can start Dolphin but when I try to play a game the screen pops up like it's about to play however it shuts down soon after.

Here is my terminal output:
```
phillipguy@phillipguy-laptop:~$ dolphin-emu 
29:14:873 Source/Core/Common/Src/FileUtil.cpp:97 W[COMMON]: IsDirectory: stat failed on /home/phillipguy/.dolphin-emu/Wii/title/00000001/00000002/content: 
29:15:300 Source/Core/DolphinWX/Src/X11Utils.cpp:115 N[Video]: XRRExtension-Version 1.3
29:15:319 Source/Core/DolphinWX/Src/X11Utils.cpp:158 N[Video]: Fullscreen Resolution 640x480
29:17:761 Source/Plugins/Plugin_VideoOGL/Src/GLUtil.cpp:351 N[Video]: glX-Version 1.4
29:17:763 Source/Plugins/Plugin_VideoOGL/Src/GLUtil.cpp:373 N[Video]: Got Doublebuffered Visual!
29:23:496 Source/Core/Core/Src/Boot/Boot.cpp:165 N[BOOT]: Booting /home/phillipguy/Games/gamecube/[NGC]Call_of_Duty_2_Big_Red_One[PAL][MULTI5][ESPALWii.com]/[NGC] [PAL] [MULTI5] Call of Duty 2 Big Red One [EspalWii.com].iso.iso
29:23:509 Source/Core/DiscIO/Src/FileMonitor.cpp:135 N[FileMon]: Opening '/home/phillipguy/Games/gamecube/[NGC]Call_of_Duty_2_Big_Red_One[PAL][MULTI5][ESPALWii.com]/[NGC] [PAL] [MULTI5] Call of Duty 2 Big Red One [EspalWii.com].iso.iso'
29:23:590 Source/Core/Core/Src/HLE/HLE_OS.cpp:52 N[OSREPORT]: 81200508->81300000| 
Apploader Initialized.
29:23:590 Source/Core/Core/Src/HLE/HLE_OS.cpp:52 N[OSREPORT]: 81200524->81300000| This Apploader built Nov 10 2004 06:47:07
29:24:402 Source/Core/Core/Src/PowerPC/Interpreter/Interpreter_SystemRegisters.cpp:353 N[PowerPC]: Flush Instruction Cache! ICE=0
29:24:462 Source/Core/Core/Src/PowerPC/Interpreter/Interpreter_SystemRegisters.cpp:344 N[PowerPC]: Instruction Cache Enable (HID0.ICE) = 1
Segmentation fault
phillipguy@phillipguy-laptop:~$ 

```

---

### Post by emoguitarist06 on 2010-11-04
> **ivarn said:**
> Hey.
I can't get this Dolphin-emu to work.
When I install it and run it from the games menu nothing happens.
And from the terminal I'm getting this error message:

So, what's wrong with this package and how can I fix this problem?
Thanx in advance:)

What verision of Ubuntu are you running? How did you install Dolphin?
I used this PPA to installer on maverick 
[https://launchpad.net/~glennric/+archive/dolphin-emu](https://launchpad.net/~glennric/+archive/dolphin-emu)

---

