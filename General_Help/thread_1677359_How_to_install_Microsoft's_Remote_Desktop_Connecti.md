---
title: "How to install Microsoft's Remote Desktop Connection 7 (RDP 7) in Wine"
date: 2011-01-28
forum: General Help
---

### Post by bmullan on 2011-01-28
If you do a search on the web you can find where to download Microsoft's Remote Desktop Connection 7 client (rdp client).

To get it to work under Wine (I used Crossover Office) actually was pretty simple.

You will need to copy four files from an existing Windows 7 system. 

Two of them, **mstc.exe** and **mstscax.dll** are located in the **C:\WINDOWS\system32** directory.

The other two files, **mstsc.exe.mui** and **mstscax.dll.mui**, are located [I]in a subdirectory within C:\WINDOWS\system32. 
[/I]
The name of the subdirectory will depend on the language and locale of the Windows system you are using. 

If your language is English and you are in the USA, they will be located in **C:\WINDOWS\system32\en-us**

Copy those 4 files to some temporary directory on your Linux system.

Next create a new Wine Windows XP "bottle".

Use either Crossover or Wine to browse to the SAME wine C: drive subdirectories as on the Win7 PC (see above) and copy the respective files into each subdirectory in your Wine Bottle.  Two files each into 2 different directories.

Finally I'd reboot your Wine bottle for good measure.

Next using either Crossover or Wine execute the RDC 7 application.

wine mstsc.exe

In Crossover you can just click the button the RUN a COMMAND and just enter "mstsc.exe"

The RDC login screen should appear prompting for a Server address and a login ID.

You can also change various other "options".

I have not tested alot but it does seem to work pretty well so far.

---

### Post by swordphsh on 2011-02-21
Have you found any way to enable NLA and connect anywhere gateway mode?

---

### Post by dfxdeimos on 2011-07-21
Thank you for this article but I am having some difficulty implementing this solution. When adding the 4 files as you mentioned and trying to execute "wine mstsc.exe" I get the following error:


```
fixme:advapi:RegisterTraceGuidsW 0x1044843 0x1066058 0x10019cc 1 0x32fe50 (null) (null) 0x1066060
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterTraceGuidsW 0x2d1c9fa6 0x2d3bdaf0 0x2d162764 1 0x32fa24 (null) (null) 0x2d3bdaf8
fixme:advapi:RegisterTraceGuidsW 0x2d1c9fa6 0x2d3bdb10 0x2d162774 1 0x32fa24 (null) (null) 0x2d3bdb18
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:ole:CoGetClassObject class {56fdf344-fd6d-11d0-958a-006097c9a090} not registered
err:ole:CoGetClassObject no class object {56fdf344-fd6d-11d0-958a-006097c9a090} could be created for context 0x1
wine: Call from 0x2d229ca5 to unimplemented function KERNEL32.dll.GetVolumePathNamesForVolumeNameW, aborting
wine: Unimplemented function KERNEL32.dll.GetVolumePathNamesForVolumeNameW called at address 0x2d229ca5 (thread 0025), starting debugger...
Can't attach process 0024: error 5
```

You mentioned something about "Windows XP Bottles" but there is no mention of that at all in the Wine install that I have (Ubuntu 11.04) - am I missing something here?

---

