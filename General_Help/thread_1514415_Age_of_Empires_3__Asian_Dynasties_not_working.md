---
title: "Age of Empires 3 : Asian Dynasties not working"
date: 2010-06-21
forum: General Help
---

### Post by boaty on 2010-06-21
Hey everyone,

today I successfully installed both Age of Empires 3 and the Asian Dynasties expansion following the instructions in the Wine AppDB.

In addition, I've also patched AoE to version 1.14 and Asian Dynasties to 1.03.

However, whenever I attempt to play either game, I get this:
"Initialization Failed"

Wine Version:  1.1.42

The terminal output for Asian Dynasties:
```

zach@Zach-Desktop:~/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III$ wine age3y.exe
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x1657b0)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x1657b0)
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x10058, 0x132310): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:ole:CoCreateInstance no instance created for interface {3e90ade3-7594-4cb0-bb58-69628f5f458c} of class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50}, hres is 0x80004002
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32f048,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e9ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e240,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e300,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32eafc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e390,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e450,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e428,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dcbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dd7c,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e930,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e1c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e284,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
zach@Zach-Desktop:~/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III$ wine age3y.exe
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x1657b0)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x1657b0)
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x10058, 0x132310): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:ole:CoCreateInstance no instance created for interface {3e90ade3-7594-4cb0-bb58-69628f5f458c} of class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50}, hres is 0x80004002
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32f048,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e9ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e240,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e300,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32eafc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e390,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e450,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e428,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dcbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dd7c,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e930,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e1c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e284,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB:(0x131c18)
fixme:msctf:LangBarMgr_ShowFloating STUB:(0x131c18)

```

Thank for in advance for any help.  Let me know if there is anything else that would be useful in helping figure this out.

---

### Post by skaarr on 2010-06-22
The other thread got closed so I'll reply here. 
You could try to find the missing dll files (copy from a windows computer or something) and put them into wine. I'm not sure exactly how that works so you'd have to google it.

My other suggestion is to try installing the game using Play on Linux (available in the software centre) which claims to be able to install both game and expansion successfully. 

As a side note, did you try running the game before you patched it? The wine DB says that it will run but I don't think that it mentions the patched version. You might want to try reinstalling and running the game without installing the patch.

---

### Post by boaty on 2010-06-23
Okay, so I looked into PlayOnLinux, and that's what I'm using now.  I actually got to the point where the game loaded and gave the "XML Error Fonts2.xml couldn't be parsed" or something like that.

I'm off to google, but if you have the answer in your head, feel free to let me know :D

Edit:

Ahahaa!  Finally tracked down the solution.  To any with this problem, or a "Initialization Failed" message:
Use winetricks to install MSXML4.
Go to winecfg either from your main menu, playonlinux, or the command line winecfg.
Go to Libraries -> New override for library -> Add -> msxml4
msxml4 should be added to Existing overrides
Start the game :D

NB:  I supposed I should add that I only tested this without the expansion (haven't installed with playonlinux yet).  But, considering how the errors were the same for both games, I think this should work with AD too.

---

