---
title: "Help with WOW Updater Error"
date: 2006-04-11
forum: General Help
---

### Post by Lushlie on 2006-04-11
I'm running Ubuntu and am getting an error message with the game World of Warcraft, been playing it for a long time with this same computer. Now I am getting this error message when trying to install their most recent update:

This application has encountered a critical error: 

FATAL ERROR! 
Program: D:\games\WOW\BNUpdate.exe 
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:408C4DD5 

The instruction at "0x408C4DD5" referenced memory at "0x00000000". 
The memory could not be "read". 

------------------------------------------------------------------------------ 

---------------------------------------- 
x86 Registers 
---------------------------------------- 

EAX=00000000 EBX=409025BC ECX=FFFFFFFF EDX=00000000 ESI=00000001 
EDI=00000000 EBP=40671B04 ESP=40671AF4 EIP=408C4DD5 FLG=00210246 
CS =0073 DS =007B ES =007B SS =007B FS =003B GS =0033 


---------------------------------------- 
Stack Trace (Manual) 
---------------------------------------- 

Address Frame Logical addr Module 

408C4DD5 40671B04 0000:00000000 <unknown> 
0040E0BC 4067225C 0001:0000D0BC D:\games\WOW\BNUpdate.exe 
400B5DC0 40672304 0000:00000000 <unknown> 
400B5ED3 40672438 0000:00000000 <unknown> 
4FA3D381 406724B8 0000:00000000 <unknown> 

---------------------------------------- 
Stack Trace (Using DBGHELP.DLL) 
---------------------------------------- 

408C4DD5 <unknown module> <unknown symbol>+0 (0x40242040,0x00000000,0x00000001,0x40242040) 


---------------------------------------- 
Loaded Modules 
---------------------------------------- 

0x00400000 - 0x00495000 BNUpdate.exe 
0x03000000 - 0x03118000 dbghelp.dll 
0x40040000 - 0x40136000 ntdll.dll 
0x40683000 - 0x406C9000 msvcrt.dll 
0x406E8000 - 0x40708000 gdi32.dll 
0x4079E000 - 0x4088E000 user32.dll 
0x408B2000 - 0x408B3000 shell32.dll 
0x40959000 - 0x4097F000 ole32.dll 
0x409C2000 - 0x409C3000 rpcrt4.dll 
0x40A02000 - 0x40A03000 shlwapi.dll 
0x40A33000 - 0x40A34000 comctl32.dll 
0x40ACC000 - 0x40ACD000 oleaut32.dll 
0x40B12000 - 0x40B13000 version.dll 
0x40B1C000 - 0x40B1D000 lz32.dll 
0x40B85000 - 0x40B86000 x11drv.dll 
0x5F400000 - 0x5F4F2000 mfc42.dll 
0x77034000 - 0x7708E000 kernel32.dll 

I've been to the Warcraft tech site, it said to try deleting my interface folder and a couple other folders, have tried this with no luck. My RAM seems to be fine too. Any suggestions on what could be causing this/how to fix it would be appreciated

---

### Post by gord on 2006-04-11
unfortunatly WOW is not a native linux application, and it has to be run with wine, and as such wine is not perfect. so whenever wow updates something, there is a chance wine won't work with it. apart from upgrading to a newer version of wine, i would suggest combing the WOW forums for other people in the same boat.

---

