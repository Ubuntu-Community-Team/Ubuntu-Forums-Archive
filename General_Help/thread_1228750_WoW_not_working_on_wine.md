---
title: "WoW not working on wine"
date: 2009-08-01
forum: General Help
---

### Post by chenlahav105 on 2009-08-01
hey. whenever i try to start WoW, the sound for the intro would start, i'd still be seeing the desktop, then i'd be getting this error message>                                   ==============================================================================
 World of WarCraft (build 9947)
 

 Exe:      C:\World of Warcraft\Wow.exe
 Time:     Aug  1, 2009  2:02:36.884 PM
 User:     chenlahav105
 Computer: ubuntu
 ------------------------------------------------------------------------------
 

 This application has encountered a critical error:
 

 ERROR #132 (0x85100084) Fatal Exception
 Program:    C:\World of Warcraft\Wow.exe
 Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:7D8B73A8
 

 The instruction at "0x7D8B73A8" referenced memory at "0x00000000".
 The memory could not be "read".
 

 

 WoWBuild: 9947
 Settings:  
 SET readTOS "-1"
 SET readEULA "-1"
 SET readScanning "-1"
 SET readContest "-1"
 SET readTerminationWithoutNotice "-1"
 SET installType "Retail"
 SET locale "enGB"
 SET movie "0"
 SET showToolsUI "1"
 SET portal "eu"
 SET realmList "eu.logon.worldofwarcraft.com"
 SET patchlist "eu.version.worldofwarcraft.com"
 SET coresDetected "2"
 SET hwDetect "0"
 SET gxRefresh "64"
 SET gxMultisampleQuality "0.000000"
 SET gxFixLag "0"
 SET videoOptionsVersion "2"
 SET Gamma "1.000000"
 SET Sound_OutputDriverName "System Default"
 SET Sound_MusicVolume "0.40000000596046"
 SET Sound_AmbienceVolume "0.60000002384186"
 SET farclip "777.000000"
 SET specular "1"
 SET groundEffectDensity "24"
 SET projectedTextures "1"
 ------------------------------------------------------------------------------
 

 ----------------------------------------
     x86 Registers
 ----------------------------------------
 

 EAX=001480C0  EBX=7D9ACFF4  ECX=00000000  EDX=00000000  ESI=0000002A
 EDI=00000001  EBP=003AD5C0  ESP=003AD308  EIP=7D8B73A8  FLG=00010283
 CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B
 

 

 ----------------------------------------
     Stack Trace (Manual)
 ----------------------------------------
 

 Address  Frame    Logical addr  Module
 

 Showing 14/14 threads...
 

 --- Thread ID: 55 ---
 7BC72105 0B22E9E8 0001:00061105 C:\windows\system32\ntdll.dll
 7BC72402 0B22EA18 0001:00061402 C:\windows\system32\ntdll.dll
 7BC7245C 0B22EA38 0001:0006145C C:\windows\system32\ntdll.dll
 7BC77995 0B22EA98 0001:00066995 C:\windows\system32\ntdll.dll
 7BC6B908 0B22EAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 0B22EB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 0B22F3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 0B22F4B8 0000:00000000 <unknown>
 

 --- Thread ID: 54 ---
 7BC72105 08BCE6A4 0001:00061105 C:\windows\system32\ntdll.dll
 7BC72402 08BCE6D4 0001:00061402 C:\windows\system32\ntdll.dll
 7B88FCD2 08BCE814 0001:0006ECD2 C:\windows\system32\KERNEL32.dll
 7D146C0B 08BCE844 0001:00035C0B C:\windows\system32\winex11.drv
 7ED1C325 08BCE9F4 0001:0007B325 C:\windows\system32\user32.dll
 7ED1C38F 08BCEA14 0001:0007B38F C:\windows\system32\user32.dll
 004415D9 08BCEA44 0001:000405D9 C:\World of Warcraft\Wow.exe
 004425DA 08BCEA58 0001:000415DA C:\World of Warcraft\Wow.exe
 008D967F 08BCEA90 0001:004D867F C:\World of Warcraft\Wow.exe
 008D9724 08BCEAA8 0001:004D8724 C:\World of Warcraft\Wow.exe
 7BC6BB10 08BCEB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 08BCF3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 08BCF4B8 0000:00000000 <unknown>
 

 --- Thread ID: 53 ---
 7BC72105 07ADE688 0001:00061105 C:\windows\system32\ntdll.dll
 7BC72402 07ADE6B8 0001:00061402 C:\windows\system32\ntdll.dll
 7B88FCD2 07ADE7F8 0001:0006ECD2 C:\windows\system32\KERNEL32.dll
 7B88FE2A 07ADE818 0001:0006EE2A C:\windows\system32\KERNEL32.dll
 0046293B 07ADEA70 0001:0006193B C:\World of Warcraft\Wow.exe
 004620CE 07ADEA7C 0001:000610CE C:\World of Warcraft\Wow.exe
 0053BBE7 07ADEA98 0001:0013ABE7 C:\World of Warcraft\Wow.exe
 7BC6B908 07ADEAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 07ADEB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 07ADF3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 07ADF4B8 0000:00000000 <unknown>
 

 --- Thread ID: 52 ---
 7BC72105 0796E8B8 0001:00061105 C:\windows\system32\ntdll.dll
 7BC72402 0796E8E8 0001:00061402 C:\windows\system32\ntdll.dll
 7B88FCD2 0796EA28 0001:0006ECD2 C:\windows\system32\KERNEL32.dll
 7B88FECC 0796EA48 0001:0006EECC C:\windows\system32\KERNEL32.dll
 00540210 0796EA58 0001:0013F210 C:\World of Warcraft\Wow.exe
 00462125 0796EA70 0001:00061125 C:\World of Warcraft\Wow.exe
 00462291 0796EA7C 0001:00061291 C:\World of Warcraft\Wow.exe
 0053BBE7 0796EA98 0001:0013ABE7 C:\World of Warcraft\Wow.exe
 7BC6B908 0796EAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 0796EB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 0796F3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 0796F4B8 0000:00000000 <unknown>
 

 --- Thread ID: 51 ---
 7BC72105 077FE8D0 0001:00061105 C:\windows\system32\ntdll.dll
 7BC72402 077FE900 0001:00061402 C:\windows\system32\ntdll.dll
 7B88FCD2 077FEA40 0001:0006ECD2 C:\windows\system32\KERNEL32.dll
 7B88FECC 077FEA60 0001:0006EECC C:\windows\system32\KERNEL32.dll
 00540210 077FEA70 0001:0013F210 C:\World of Warcraft\Wow.exe
 007AD8CB 077FEA98 0001:003AC8CB C:\World of Warcraft\Wow.exe
 7BC6B908 077FEAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 077FEB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 077FF3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 077FF4B8 0000:00000000 <unknown>
 

 --- Thread ID: 50 ---
 7B88FFE2 0768EA58 0001:0006EFE2 C:\windows\system32\KERNEL32.dll
 7B890025 0768EA78 0001:0006F025 C:\windows\system32\KERNEL32.dll
 008552DD 0768EA84 0001:004542DD C:\World of Warcraft\Wow.exe
 00855B0C 0768EA98 0001:00454B0C C:\World of Warcraft\Wow.exe
 7BC6B908 0768EAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 0768EB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 0768F3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 0768F4B8 0000:00000000 <unknown>
 

 --- Thread ID: 49 ---
 7B88FFE2 0641EA58 0001:0006EFE2 C:\windows\system32\KERNEL32.dll
 7B890025 0641EA78 0001:0006F025 C:\windows\system32\KERNEL32.dll
 008552DD 0641EA84 0001:004542DD C:\World of Warcraft\Wow.exe
 00855B0C 0641EA98 0001:00454B0C C:\World of Warcraft\Wow.exe
 7BC6B908 0641EAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 0641EB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 0641F3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 0641F4B8 0000:00000000 <unknown>
 

 --- Thread ID: 48 ---
 7B88FFE2 062AEA58 0001:0006EFE2 C:\windows\system32\KERNEL32.dll
 7B890025 062AEA78 0001:0006F025 C:\windows\system32\KERNEL32.dll
 008552DD 062AEA84 0001:004542DD C:\World of Warcraft\Wow.exe
 00855B0C 062AEA98 0001:00454B0C C:\World of Warcraft\Wow.exe
 7BC6B908 062AEAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 062AEB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 062AF3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 062AF4B8 0000:00000000 <unknown>
 

 --- Thread ID: 47 ---
 7B88FFE2 0613EA58 0001:0006EFE2 C:\windows\system32\KERNEL32.dll
 7B890025 0613EA78 0001:0006F025 C:\windows\system32\KERNEL32.dll
 008552DD 0613EA84 0001:004542DD C:\World of Warcraft\Wow.exe
 00855B0C 0613EA98 0001:00454B0C C:\World of Warcraft\Wow.exe
 7BC6B908 0613EAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 0613EB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 0613F3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 0613F4B8 0000:00000000 <unknown>
 

 --- Thread ID: 46 ---
 7EE0CE57 05FCEA98 0001:0002BE57 C:\windows\system32\winmm.dll
 7BC6B908 05FCEAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 05FCEB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 05FCF3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 05FCF4B8 0000:00000000 <unknown>
 

 --- Thread ID: 45 ---
 7BC72105 0405E8C4 0001:00061105 C:\windows\system32\ntdll.dll
 7BC72402 0405E8F4 0001:00061402 C:\windows\system32\ntdll.dll
 7B88FCD2 0405EA34 0001:0006ECD2 C:\windows\system32\KERNEL32.dll
 7B88FECC 0405EA54 0001:0006EECC C:\windows\system32\KERNEL32.dll
 00540210 0405EA64 0001:0013F210 C:\World of Warcraft\Wow.exe
 00477D72 0405EA7C 0001:00076D72 C:\World of Warcraft\Wow.exe
 0053BBE7 0405EA98 0001:0013ABE7 C:\World of Warcraft\Wow.exe
 7BC6B908 0405EAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 0405EB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 0405F3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 0405F4B8 0000:00000000 <unknown>
 

 --- Thread ID: 44 ---
 7B88FFE2 0398E630 0001:0006EFE2 C:\windows\system32\KERNEL32.dll
 7B890025 0398E650 0001:0006F025 C:\windows\system32\KERNEL32.dll
 0046E92D 0398E65C 0001:0006D92D C:\World of Warcraft\Wow.exe
 007DAAD5 0398EA7C 0001:003D9AD5 C:\World of Warcraft\Wow.exe
 0053BBE7 0398EA98 0001:0013ABE7 C:\World of Warcraft\Wow.exe
 7BC6B908 0398EAA8 0001:0005A908 C:\windows\system32\ntdll.dll
 7BC6BB10 0398EB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 0398F3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 0398F4B8 0000:00000000 <unknown>
 

 --- Thread ID: 43 ---
 7B88FFE2 01CCEA10 0001:0006EFE2 C:\windows\system32\KERNEL32.dll
 7B890025 01CCEA30 0001:0006F025 C:\windows\system32\KERNEL32.dll
 004245E4 01CCEA58 0001:000235E4 C:\World of Warcraft\Wow.exe
 008D967F 01CCEA90 0001:004D867F C:\World of Warcraft\Wow.exe
 008D9724 01CCEAA8 0001:004D8724 C:\World of Warcraft\Wow.exe
 7BC6BB10 01CCEB78 0001:0005AB10 C:\windows\system32\ntdll.dll
 7BC73C8B 01CCF3B8 0001:00062C8B C:\windows\system32\ntdll.dll
 B7EEE4FF 01CCF4B8 0000:00000000 <unknown>
 

 --- Thread ID: 42 [Current Thread] ---
 7D8B73A8 003AD5C0 0001:000363A8 C:\windows\system32\wined3d.dll
 7D8CB581 003AD620 0001:0004A581 C:\windows\system32\wined3d.dll
 7D8D500D 003AD6A0 0001:0005400D C:\windows\system32\wined3d.dll
 7D9CA4E2 003AD710 0001:000094E2 C:\windows\system32\d3d9.dll
 0062A25C 003AD76C 0001:0022925C C:\World of Warcraft\Wow.exe
 006285EF 003AD7DC 0001:002275EF C:\World of Warcraft\Wow.exe
 7ED567DA 003AD80C 0001:000B57DA C:\windows\system32\user32.dll
 7ED56C2A 003AD84C 0001:000B5C2A C:\windows\system32\user32.dll
 7ED59A55 003ADD1C 0001:000B8A55 C:\windows\system32\user32.dll
 7ED5BFEE 003ADD5C 0001:000BAFEE C:\windows\system32\user32.dll
 7ED1AED1 003ADDBC 0001:00079ED1 C:\windows\system32\user32.dll
 7ED201D5 003ADE1C 0001:0007F1D5 C:\windows\system32\user32.dll
 7ED206EC 003ADE5C 0001:0007F6EC C:\windows\system32\user32.dll
 7ECE1652 003ADF2C 0001:00040652 C:\windows\system32\user32.dll
 7ECE2431 003ADF7C 0001:00041431 C:\windows\system32\user32.dll
 0046E007 003ADFB0 0001:0006D007 C:\World of Warcraft\Wow.exe
 00628700 003AE024 0001:00227700 C:\World of Warcraft\Wow.exe
 7ED567DA 003AE054 0001:000B57DA C:\windows\system32\user32.dll
 7ED56C2A 003AE094 0001:000B5C2A C:\windows\system32\user32.dll
 7ED59A55 003AE564 0001:000B8A55 C:\windows\system32\user32.dll
 7ED5BFEE 003AE5A4 0001:000BAFEE C:\windows\system32\user32.dll
 7ED1AED1 003AE604 0001:00079ED1 C:\windows\system32\user32.dll
 7ED201D5 003AE664 0001:0007F1D5 C:\windows\system32\user32.dll
 7ED206EC 003AE6A4 0001:0007F6EC C:\windows\system32\user32.dll
 7ED514FB 003AE7F4 0001:000B04FB C:\windows\system32\user32.dll
 7ED52358 003AE864 0001:000B1358 C:\windows\system32\user32.dll
 7D8CAC99 003AE8A4 0001:00049C99 C:\windows\system32\wined3d.dll
 7D8D58B4 003AE924 0001:000548B4 C:\windows\system32\wined3d.dll
 7D9CA4E2 003AE994 0001:000094E2 C:\windows\system32\d3d9.dll
 0062A25C 003AE9F0 0001:0022925C C:\World of Warcraft\Wow.exe
 006285EF 003AEA60 0001:002275EF C:\World of Warcraft\Wow.exe
 7ED567DA 003AEA90 0001:000B57DA C:\windows\system32\user32.dll
 7ED56C2A 003AEAD0 0001:000B5C2A C:\windows\system32\user32.dll
 7ED59A55 003AEFA0 0001:000B8A55 C:\windows\system32\user32.dll
 7ED5BFEE 003AEFE0 0001:000BAFEE C:\windows\system32\user32.dll
 7ED1AED1 003AF040 0001:00079ED1 C:\windows\system32\user32.dll
 7ED201D5 003AF0A0 0001:0007F1D5 C:\windows\system32\user32.dll
 7ED206EC 003AF0E0 0001:0007F6EC C:\windows\system32\user32.dll
 7ECE1652 003AF1B0 0001:00040652 C:\windows\system32\user32.dll
 7ECE2431 003AF200 0001:00041431 C:\windows\system32\user32.dll
 0046E007 003AF234 0001:0006D007 C:\World of Warcraft\Wow.exe
 00628700 003AF2A8 0001:00227700 C:\World of Warcraft\Wow.exe
 7ED567DA 003AF2D8 0001:000B57DA C:\windows\system32\user32.dll
 7ED56C2A 003AF318 0001:000B5C2A C:\windows\system32\user32.dll
 7ED59A55 003AF7E8 0001:000B8A55 C:\windows\system32\user32.dll
 7ED5BFEE 003AF828 0001:000BAFEE C:\windows\system32\user32.dll
 7ED1AED1 003AF888 0001:00079ED1 C:\windows\system32\user32.dll
 7ED201D5 003AF8E8 0001:0007F1D5 C:\windows\system32\user32.dll
 7ED206EC 003AF928 0001:0007F6EC C:\windows\system32\user32.dll
 7ED514FB 003AFA78 0001:000B04FB C:\windows\system32\user32.dll
 7ED52358 003AFAE8 0001:000B1358 C:\windows\system32\user32.dll
 7D144FB4 003AFB68 0001:00033FB4 C:\windows\system32\winex11.drv
 7D1466FB 003AFC98 0001:000356FB C:\windows\system32\winex11.drv
 7D146BA5 003AFCC8 0001:00035BA5 C:\windows\system32\winex11.drv
 7ED1F4C8 003AFD18 0001:0007E4C8 C:\windows\system32\user32.dll
 7ED1F5EB 003AFD48 0001:0007E5EB C:\windows\system32\user32.dll
 0046D68F 003AFD9C 0001:0006C68F C:\World of Warcraft\Wow.exe
 008350C6 003AFDD4 0001:004340C6 C:\World of Warcraft\Wow.exe
 00833D62 003AFE54 0001:00432D62 C:\World of Warcraft\Wow.exe
 00833F11 003AFE6C 0001:00432F11 C:\World of Warcraft\Wow.exe
 00406C7D 003AFF08 0001:00005C7D C:\World of Warcraft\Wow.exe
 7B878370 003AFFE8 0001:00057370 C:\windows\system32\KERNEL32.dll
 

 ----------------------------------------
     Stack Trace (Using DBGHELP.DLL)
 ----------------------------------------
 

 Showing 14/14 threads...
 

 --- Thread ID: 55 ---
 7BC72105 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0B22EA40,0x00000004,0x0B22EA80)
 7BC72402 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0B22EA40,0x00000000,0x00000000)
 7BC7245C ntdll.dll    NtWaitForSingleObject+60 (0x000021D0,0x00000000,0x0B22EA80,0x7BC91143)
 7BC77995 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7FFA4F10,0x0B22EB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x7BC77850,0x00000000,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x7BC77850,0x00000000,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x0B22FB90,0x0B22FB90,0x0B22FB90)
 B7EEE4FF              start_thread+191 (0x0B22FB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 54 ---
 7BC72105 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x08BCE6FC,0x00000004,0x00000000)
 7BC72402 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x08BCE6FC,0x00000000,0x00000000)
 7B88FCD2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x08BCE874,0x00000000,0xFFFFFFFF)
 7D146C0B winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x08BCE874,0xFFFFFFFF,0x00000000)
 7ED1C325 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x08BCEA3C,0xFFFFFFFF,0x00000000)
 7ED1C38F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x08BCEA3C,0x00000000,0xFFFFFFFF)
 004415D9 Wow.exe      <unknown symbol>+0 (0x0106A1D0,0x7FFA81D4,0x074EBEB8,0x08BCEA90)
 004425DA Wow.exe      <unknown symbol>+0 (0x074EBE58,0x844AD3D2,0x7FFA81D4,0x074EBEB
 008D967F Wow.exe      <unknown symbol>+0 (0x7FFA8F10,0x7BC6B908,0x074EBEB8,0x7FFA8F10)
 008D9724 Wow.exe      <unknown symbol>+0 (0x008D96A5,0x074EBEB8,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x074EBEB8,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x08BCFB90,0x08BCFB90,0x08BCFB90)
 B7EEE4FF              start_thread+191 (0x08BCFB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 53 ---
 7BC72105 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x07ADE6E0,0x00000004,0x07ADE7E0)
 7BC72402 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x07ADE6E0,0x00000000,0x00000000)
 7B88FCD2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x07ADE93C,0x00000000,0x000001F4)
 7B88FE2A KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x07ADE93C,0x00000000,0x000001F4)
 0046293B Wow.exe      <unknown symbol>+0 (0x004620C0,0x07ADEA98,0x0053BBE7,0x07152B90)
 004620CE Wow.exe      <unknown symbol>+0 (0x07152B90,0x7FFAC1D4,0x7FFACF10,0x7BC94FF4)
 0053BBE7 Wow.exe      <unknown symbol>+0 (0x000021AC,0x7FFACF10,0x07ADEB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x0053BB90,0x06FD6358,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x06FD6358,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x07ADFB90,0x07ADFB90,0x07ADFB90)
 B7EEE4FF              start_thread+191 (0x07ADFB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 52 ---
 7BC72105 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0796E910,0x00000004,0x0796EA10)
 7BC72402 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0796E910,0x00000000,0x00000000)
 7B88FCD2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0796EA50,0x00000000,0x000003E
 7B88FECC KERNEL32.dll WaitForSingleObject+60 (0x0000211C,0x000003E8,0x0796EA70,0x00462125)
 00540210 Wow.exe      <unknown symbol>+0 (0x000003E8,0x00000034,0x00462280,0x07152BA0)
 00462125 Wow.exe      <unknown symbol>+0 (0x00000000,0x0796EA98,0x0053BBE7,0x07152BA0)
 00462291 Wow.exe      <unknown symbol>+0 (0x07152BA0,0x7FFB01D4,0x7FFB0F10,0x7BC94FF4)
 0053BBE7 Wow.exe      <unknown symbol>+0 (0x000021A8,0x7FFB0F10,0x0796EB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x0053BB90,0x06FD6340,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x06FD6340,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x0796FB90,0x0796FB90,0x0796FB90)
 B7EEE4FF              start_thread+191 (0x0796FB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 51 ---
 7BC72105 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x077FE928,0x00000004,0x00000000)
 7BC72402 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x077FE928,0x00000000,0x00000000)
 7B88FCD2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x077FEA68,0x00000000,0xFFFFFFFF)
 7B88FECC KERNEL32.dll WaitForSingleObject+60 (0x0000207C,0xFFFFFFFF,0x077FEA98,0x007AD8CB)
 00540210 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x00000000,0x0053BBE7,0x00000000)
 007AD8CB Wow.exe      <unknown symbol>+0 (0x00002114,0x7FFB4F10,0x077FEB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x0053BB90,0x0709A1F0,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x0709A1F0,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x077FFB90,0x077FFB90,0x077FFB90)
 B7EEE4FF              start_thread+191 (0x077FFB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 50 ---
 7B88FFE2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x0768EA84,0x00842D8A)
 7B890025 KERNEL32.dll Sleep+37 (0x0000000A,0x0768EA98,0x00855B0C,0x0000000A)
 008552DD Wow.exe      <unknown symbol>+0 (0x0000000A,0x7FFB8F10,0x00000032,0x0768EAA
 00855B0C Wow.exe      <unknown symbol>+0 (0x04D17EC0,0x7FFB8F10,0x0768EB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x00855A90,0x04D17EC0,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x04D17EC0,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x0768FB90,0x0768FB90,0x0768FB90)
 B7EEE4FF              start_thread+191 (0x0768FB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 49 ---
 7B88FFE2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000001)
 7B890025 KERNEL32.dll Sleep+37 (0x0000000A,0x0641EA98,0x00855B0C,0x0000000A)
 008552DD Wow.exe      <unknown symbol>+0 (0x0000000A,0x7FFBCF10,0x00000031,0x0641EAA
 00855B0C Wow.exe      <unknown symbol>+0 (0x04AFF578,0x7FFBCF10,0x0641EB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x00855A90,0x04AFF578,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x04AFF578,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x0641FB90,0x0641FB90,0x0641FB90)
 B7EEE4FF              start_thread+191 (0x0641FB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 48 ---
 7B88FFE2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x062AEA84,0x00842D8A)
 7B890025 KERNEL32.dll Sleep+37 (0x0000000A,0x062AEA98,0x00855B0C,0x0000000A)
 008552DD Wow.exe      <unknown symbol>+0 (0x0000000A,0x7FFC0F10,0x00000030,0x062AEAA8)
 00855B0C Wow.exe      <unknown symbol>+0 (0x04D20540,0x7FFC0F10,0x062AEB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x00855A90,0x04D20540,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x04D20540,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x062AFB90,0x062AFB90,0x062AFB90)
 B7EEE4FF              start_thread+191 (0x062AFB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 47 ---
 7B88FFE2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000002)
 7B890025 KERNEL32.dll Sleep+37 (0x0000000A,0x0613EA98,0x00855B0C,0x0000000A)
 008552DD Wow.exe      <unknown symbol>+0 (0x0000000A,0x7FFC4F10,0x0000002F,0x0613EAA8)
 00855B0C Wow.exe      <unknown symbol>+0 (0x04A77D48,0x7FFC4F10,0x0613EB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x00855A90,0x04A77D48,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x04A77D48,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x0613FB90,0x0613FB90,0x0613FB90)
 B7EEE4FF              start_thread+191 (0x0613FB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 46 ---
 7EE0CE57 winmm.dll    <unknown symbol>+0 (0x00000000,0x7FFC8F10,0x05FCEB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x7EE0CC20,0x00000000,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x7EE0CC20,0x00000000,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x05FCFB90,0x05FCFB90,0x05FCFB90)
 B7EEE4FF              start_thread+191 (0x05FCFB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 45 ---
 7BC72105 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0405E91C,0x00000004,0x00000000)
 7BC72402 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0405E91C,0x00000000,0x00000000)
 7B88FCD2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0405EA5C,0x00000000,0xFFFFFFFF)
 7B88FECC KERNEL32.dll WaitForSingleObject+60 (0x0000206C,0xFFFFFFFF,0x0405EA7C,0x00477D72)
 00540210 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x01072010,0x0000002D,0x00477D10)
 00477D72 Wow.exe      <unknown symbol>+0 (0x01072010,0x7FFCC1D4,0x7FFCCF10,0x7BC94FF4)
 0053BBE7 Wow.exe      <unknown symbol>+0 (0x000020E0,0x7FFCCF10,0x0405EB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x0053BB90,0x02B97C58,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x02B97C58,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x0405FB90,0x0405FB90,0x0405FB90)
 B7EEE4FF              start_thread+191 (0x0405FB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 44 ---
 7B88FFE2 KERNEL32.dll SleepEx+50 (0x00000001,0x00000000,0x00000000,0x00000000)
 7B890025 KERNEL32.dll Sleep+37 (0x00000001,0x0398EA7C,0x007DAAD5,0x00000001)
 0046E92D Wow.exe      <unknown symbol>+0 (0x00000001,0x007DA900,0x02B3D3B8,0x0000002C)
 007DAAD5 Wow.exe      <unknown symbol>+0 (0x02B3D3B8,0x7FFD01D4,0x7FFD0F10,0x7BC94FF4)
 0053BBE7 Wow.exe      <unknown symbol>+0 (0x000020DC,0x7FFD0F10,0x0398EB78,0x7BC6BB10)
 7BC6B908 ntdll.dll    call_thread_func+12 (0x0053BB90,0x02B3D3D8,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x02B3D3D8,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x0398FB90,0x0398FB90,0x0398FB90)
 B7EEE4FF              start_thread+191 (0x0398FB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 43 ---
 7B88FFE2 KERNEL32.dll SleepEx+50 (0x00000064,0x00000000,0x01CCEA30,0x7B854C77)
 7B890025 KERNEL32.dll Sleep+37 (0x00000064,0x7FFD41D4,0x7BC94FF4,0x01AEB0C8)
 004245E4 Wow.exe      <unknown symbol>+0 (0x01AEB0C8,0x8D3AD3D2,0x7FFD41D4,0x01AEB128)
 008D967F Wow.exe      <unknown symbol>+0 (0x7FFD4F10,0x7BC6B908,0x01AEB128,0x7FFD4F10)
 008D9724 Wow.exe      <unknown symbol>+0 (0x008D96A5,0x01AEB128,0x00000000,0x00000000)
 7BC6BB10 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x01AEB128,0x00000000,0x00000000)
 7BC73C8B ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x01CCFB90,0x01CCFB90,0x01CCFB90)
 B7EEE4FF              start_thread+191 (0x01CCFB90,0x00000000,0x00000000,0x00000000)
 B7E6849E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 --- Thread ID: 42 [Current Thread] ---
 7D8B73A8 wined3d.dll  ActivateContext+136 (0x001480C0,0x0015F6A8,0x00000001,0x00000000)
 7D8CB581 wined3d.dll  delete_opengl_contexts+49 (0x001480C0,0x0015EB90,0x00000000,0x0000000E)
 7D8D500D wined3d.dll  <unknown symbol>+0 (0x001480C0,0x003AD6C4,0x003AD700,0x00000000)
 7D9CA4E2 d3d9.dll     <unknown symbol>+0 (0x0013D728,0x003AD724,0x02B33768,0x00000400)
 0062A25C Wow.exe      <unknown symbol>+0 (0x00000000,0x003AD7CC,0x00000000,0x0005006E)
 006285EF Wow.exe      <unknown symbol>+0 (0x0005006E,0x00000005,0x00000000,0x00000400)
 7ED567DA user32.dll   WINPROC_wrapper+26 (0x00628480,0x0005006E,0x00000005,0x00000000)
 7ED56C2A user32.dll   WINPROC_wrapper+1130 (0x0005006E,0x00000005,0x00000000,0x03000400)
 7ED59A55 user32.dll   <unknown symbol>+0 (0x00000005,0x00000000,0x03000400,0x003ADDB0)
 7ED5BFEE user32.dll   <unknown symbol>+0 (0x0005006E,0x00000005,0x00000000,0x03000400)
 7ED1AED1 user32.dll   <unknown symbol>+0 (0x00000000,0x03000400,0x00000001,0x00000001)
 7ED201D5 user32.dll   <unknown symbol>+0 (0x00000001,0x0005006E,0x00000001,0x0000002A)
 7ED206EC user32.dll   SendMessageW+76 (0x0005006E,0x00000005,0x00000000,0x03000400)
 7ECE1652 user32.dll   <unknown symbol>+0 (0x00000000,0x003AE83C,0x00000047,0x00000000)
 7ECE2431 user32.dll   DefWindowProcA+161 (0x0005006E,0x00000047,0x00000000,0x003AE83C)
 0046E007 Wow.exe      <unknown symbol>+0 (0x0005006E,0x00000047,0x00000000,0x003AE83C)
 00628700 Wow.exe      <unknown symbol>+0 (0x0005006E,0x00000047,0x00000000,0x003AE83C)
 7ED567DA user32.dll   WINPROC_wrapper+26 (0x00628480,0x0005006E,0x00000047,0x00000000)
 7ED56C2A user32.dll   WINPROC_wrapper+1130 (0x0005006E,0x00000047,0x00000000,0x003AE83C)
 7ED59A55 user32.dll   <unknown symbol>+0 (0x00000047,0x00000000,0x003AE83C,0x003AE5F8)
 7ED5BFEE user32.dll   <unknown symbol>+0 (0x0005006E,0x00000047,0x00000000,0x003AE83C)
 7ED1AED1 user32.dll   <unknown symbol>+0 (0x00000000,0x003AE83C,0x00000001,0x00000001)
 7ED201D5 user32.dll   <unknown symbol>+0 (0x00000001,0x003AE83C,0x00000001,0x0000002A)
 7ED206EC user32.dll   SendMessageW+76 (0x0005006E,0x00000047,0x00000000,0x003AE83C)
 7ED514FB user32.dll   <unknown symbol>+0 (0x003AE83C,0x00000000,0x003AE814,0x7D9ACFF4)
 7ED52358 user32.dll   SetWindowPos+168 (0x0005006E,0x00000000,0x00000000,0x00000000)
 7D8CAC99 wined3d.dll  <unknown symbol>+0 (0x00000400,0x00000300,0x00000000,0x0000000E)
 7D8D58B4 wined3d.dll  <unknown symbol>+0 (0x001480C0,0x003AE948,0x003AE984,0x00000000)
 7D9CA4E2 d3d9.dll     <unknown symbol>+0 (0x0013D728,0x003AE9A8,0x02B33768,0x00000400)
 0062A25C Wow.exe      <unknown symbol>+0 (0x00000000,0x003AEA50,0x00000000,0x0005006E)
 006285EF Wow.exe      <unknown symbol>+0 (0x0005006E,0x00000005,0x00000000,0x00000400)
 7ED567DA user32.dll   WINPROC_wrapper+26 (0x00628480,0x0005006E,0x00000005,0x00000000)
 7ED56C2A user32.dll   WINPROC_wrapper+1130 (0x0005006E,0x00000005,0x00000000,0x02E70400)
 7ED59A55 user32.dll   <unknown symbol>+0 (0x00000005,0x00000000,0x02E70400,0x003AF034)
 7ED5BFEE user32.dll   <unknown symbol>+0 (0x0005006E,0x00000005,0x00000000,0x02E70400)
 7ED1AED1 user32.dll   <unknown symbol>+0 (0x00000000,0x02E70400,0x00000001,0x00000001)
 7ED201D5 user32.dll   <unknown symbol>+0 (0x00000001,0x0005006E,0x00000001,0x0000002A)
 7ED206EC user32.dll   SendMessageW+76 (0x0005006E,0x00000005,0x00000000,0x02E70400)
 7ECE1652 user32.dll   <unknown symbol>+0 (0x00000000,0x003AFAC0,0x00000047,0x00000000)
 7ECE2431 user32.dll   DefWindowProcA+161 (0x0005006E,0x00000047,0x00000000,0x003AFAC0)
 0046E007 Wow.exe      <unknown symbol>+0 (0x0005006E,0x00000047,0x00000000,0x003AFAC0)
 00628700 Wow.exe      <unknown symbol>+0 (0x0005006E,0x00000047,0x00000000,0x003AFAC0)
 7ED567DA user32.dll   WINPROC_wrapper+26 (0x00628480,0x0005006E,0x00000047,0x00000000)
 7ED56C2A user32.dll   WINPROC_wrapper+1130 (0x0005006E,0x00000047,0x00000000,0x003AFAC0)
 7ED59A55 user32.dll   <unknown symbol>+0 (0x00000047,0x00000000,0x003AFAC0,0x003AF87C)
 7ED5BFEE user32.dll   <unknown symbol>+0 (0x0005006E,0x00000047,0x00000000,0x003AFAC0)
 7ED1AED1 user32.dll   <unknown symbol>+0 (0x00000000,0x003AFAC0,0x00000001,0x00000001)
 7ED201D5 user32.dll   <unknown symbol>+0 (0x00000001,0x00000000,0x00000001,0x0000002A)
 7ED206EC user32.dll   SendMessageW+76 (0x0005006E,0x00000047,0x00000000,0x003AFAC0)
 7ED514FB user32.dll   <unknown symbol>+0 (0x003AFAC0,0x03E0000B,0x00000103,0x00000000)
 7ED52358 user32.dll   SetWindowPos+168 (0x0005006E,0x00000000,0x00000000,0x00000019)
 7D144FB4 winex11.drv  <unknown symbol>+0 (0x0005006E,0x003AFBC8,0xFFFFFFFD,0x003AFBC4)
 7D1466FB winex11.drv  <unknown symbol>+0 (0x000004FF,0x00000000,0x7D86DF20,0x00000026)
 7D146BA5 winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+85 (0x00000000,0x00000000,0x00000000,0x000004FF)
 7ED1F4C8 user32.dll   PeekMessageW+88 (0x003AFD70,0x00000000,0x00000000,0x00000000)
 7ED1F5EB user32.dll   PeekMessageA+91 (0x003AFD70,0x00000000,0x00000000,0x00000000)
 0046D68F Wow.exe      <unknown symbol>+0 (0x003AFDDC,0x003AFDC0,0x003AFDC4,0x003AFDC8)
 008350C6 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x003AFE4C,0x00000A28,0x00000002)
 00833D62 Wow.exe      <unknown symbol>+0 (0x00000000,0x00406C02,0x00000001,0x00000001)
 00833F11 Wow.exe      <unknown symbol>+0 (0x0040AFD9,0x00400000,0x00000000,0x00114EAE)
 00406C7D Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
 7B878370 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
 B7F16E1D              wine_call_on_stack+29 (0x00000000,0x00000000,0x00000000,0x00000000)
 

 

 ----------------------------------------
     Loaded Modules
 ----------------------------------------
 

 0x00400000 - 0x01758000  C:\World of Warcraft\Wow.exe
 0x10000000 - 0x10069000  C:\World of Warcraft\DivxDecoder.dll
 0x7B820000 - 0x7B962000  C:\windows\system32\KERNEL32.dll
 0x7BC10000 - 0x7BCB1000  C:\windows\system32\ntdll.dll
 0x7BF90000 - 0x7BFA5000  C:\windows\system32\psapi.dll
 0x7BFC0000 - 0x7C000000  C:\windows\system32\dsound.dll
 0x7C500000 - 0x7C53E000  C:\windows\system32\dbghelp.dll
 0x7C570000 - 0x7C595000  C:\windows\system32\uxtheme.dll
 0x7CF30000 - 0x7CF38000  C:\windows\system32\midimap.dll
 0x7CF40000 - 0x7CF50000  C:\windows\system32\msacm32.drv
 0x7D0A0000 - 0x7D0D2000  C:\windows\system32\winealsa.drv
 0x7D110000 - 0x7D1A3000  C:\windows\system32\winex11.drv
 0x7D2D0000 - 0x7D2D8000  C:\windows\system32\lz32.dll
 0x7D2E0000 - 0x7D2F3000  C:\windows\system32\version.dll
 0x7D300000 - 0x7D360000  C:\windows\system32\rpcrt4.dll
 0x7D380000 - 0x7D45C000  C:\windows\system32\ole32.dll
 0x7D460000 - 0x7D495000  C:\windows\system32\dinput.dll
 0x7D4A0000 - 0x7D4AF000  C:\windows\system32\dinput8.dll
 0x7D4C0000 - 0x7D4DD000  C:\windows\system32\ws2_32.dll
 0x7D4E0000 - 0x7D503000  C:\windows\system32\msacm32.dll
 0x7D510000 - 0x7D5CB000  C:\windows\system32\comctl32.dll
 0x7D5E0000 - 0x7D759000  C:\windows\system32\shell32.dll
 0x7D770000 - 0x7D7B7000  C:\windows\system32\shlwapi.dll
 0x7D7C0000 - 0x7D7DA000  C:\windows\system32\mpr.dll
 0x7D810000 - 0x7D851000  C:\windows\system32\wininet.dll
 0x7D860000 - 0x7D872000  C:\windows\system32\imm32.dll
 0x7D880000 - 0x7D9AF000  C:\windows\system32\wined3d.dll
 0x7D9C0000 - 0x7D9E0000  C:\windows\system32\d3d9.dll
 0x7EB10000 - 0x7EB92000  C:\windows\system32\opengl32.dll
 0x7EBA0000 - 0x7EBE8000  C:\windows\system32\advapi32.dll
 0x7EC00000 - 0x7EC8A000  C:\windows\system32\gdi32.dll
 0x7ECA0000 - 0x7EDD6000  C:\windows\system32\user32.dll
 0x7EDE0000 - 0x7EE72000  C:\windows\system32\winmm.dll
 

 

 ----------------------------------------
     Memory Dump
 ----------------------------------------
 

 Code: 16 bytes starting at (EIP = 7D8B73A8)
 

 7D8B73A8: 8B 09 89 4D  E4 0F 84 95  0B 00 00 8B  4D DC 8B B1  ...M........M...
 

 

 Stack: 1024 bytes starting at (ESP = 003AD308)
 

 * = addr                            **                                *        
 003AD300: 00 00 00 00  37 73 8B 7D  10 00 00 00  F0 00 00 00  ....7s.}........
 003AD310: 40 01 00 00  00 00 00 00  00 00 00 00  00 00 00 00  @...............
 003AD320: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD330: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD340: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD350: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD360: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD370: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD380: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD390: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD3A0: C3 9A 35 10  F4 CF D7 7E  69 00 00 00  46 00 00 00  ..5....~i...F...
 003AD3B0: D0 D3 3A 00  2B 82 D3 7E  00 00 00 00  69 00 00 00  ..:.+..~....i...
 003AD3C0: 08 D4 3A 00  00 00 00 00  F9 81 D3 7E  F4 CF 9A 7D  ..:........~...}
 003AD3D0: F0 D4 3A 00  AD A4 8D 7D  00 00 00 00  69 00 00 00  ..:....}....i...
 003AD3E0: 08 D4 3A 00  00 00 00 00  00 00 00 00  00 00 00 00  ..:.............
 003AD3F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD400: 08 D4 3A 00  00 00 00 00  57 00 69 00  6E 00 65 00  ..:.....W.i.n.e.
 003AD410: 20 00 58 00  31 00 31 00  20 00 64 00  72 00 69 00   .X.1.1. .d.r.i.
 003AD420: 76 00 65 00  72 00 00 00  20 00 00 00  00 03 00 00  v.e.r... .......
 003AD430: 00 04 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD440: 00 00 00 00  00 00 00 00  01 04 01 04  BC 00 00 00  ................
 003AD450: 00 00 7C 00  00 00 00 00  00 00 00 00  00 00 00 00  ..|.............
 003AD460: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD470: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD480: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD490: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD4A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD4B0: 10 00 00 00  40 01 00 00  F0 00 00 00  00 00 00 00  ....@...........
 003AD4C0: C3 9A 35 10  F4 CF D7 7E  0F 00 00 00  00 00 00 00  ..5....~........
 003AD4D0: F0 D4 3A 00  2B 82 D3 7E  00 00 00 00  0E 00 00 00  ..:.+..~........
 003AD4E0: 38 D5 3A 00  00 00 00 00  F9 81 D3 7E  AB BA 96 7D  8.:........~...}
 003AD4F0: 20 D6 3A 00  21 B4 8D 7D  20 00 00 00  0E 00 00 00   .:.!..} .......
 003AD500: 38 D5 3A 00  00 00 00 00  00 00 00 00  69 00 00 00  8.:.........i...
 003AD510: 38 D5 3A 00  00 00 00 00  00 00 00 00  00 00 00 00  8.:.............
 003AD520: 00 00 00 00  2E A9 90 7D  38 D5 3A 00  0E 00 00 00  .......}8.:.....
 003AD530: 0F 00 00 00  00 00 00 00  57 00 69 00  6E 00 65 00  ........W.i.n.e.
 003AD540: 20 00 58 00  31 00 31 00  20 00 64 00  72 00 69 00   .X.1.1. .d.r.i.
 003AD550: 76 00 65 00  72 00 00 00  00 00 00 00  00 00 00 00  v.e.r...........
 003AD560: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD570: 00 00 00 00  00 00 00 00  01 04 01 04  BC 00 00 00  ................
 003AD580: 00 00 7C 00  00 00 00 00  00 00 00 00  A8 F6 15 00  ..|.............
 003AD590: C0 80 14 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD5A0: 00 81 14 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD5B0: 00 00 00 00  F4 CF 9A 7D  C0 80 14 00  C0 80 14 00  .......}........
 003AD5C0: 20 D6 3A 00  81 B5 8C 7D  C0 80 14 00  A8 F6 15 00   .:....}........
 003AD5D0: 01 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD5E0: 20 00 00 00  00 04 00 00  00 03 00 00  00 00 00 00   ...............
 003AD5F0: 40 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  @...............
 003AD600: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
 003AD610: 6B 91 8C 7D  F4 CF 9A 7D  C0 80 14 00  70 D6 3A 00  k..}...}....p.:.
 003AD620: A0 D6 3A 00  0D 50 8D 7D  C0 80 14 00  90 EB 15 00  ..:..P.}........
 003AD630: 00 00 00 00  0E 00 00 00  70 D6 3A 00  CC 80 FD 7F  ........p.:.....
 003AD640: 80 D6 3A 00  9B 18 89 7B  60 B4 D9 7E  00 00 00 00  ..:....{`..~....
 003AD650: 80 F6 15 00  AC DA 9A 7D  1D 7A 98 7D  D7 29 98 7D  .......}.z.}.).}
 003AD660: 46 00 00 00  00 D6 8B 7D  A8 F6 15 00  00 D7 3A 00  F......}......:.
 003AD670: 00 04 00 00  00 03 00 00  40 00 00 00  03 00 00 00  ........@.......
 003AD680: A0 D6 3A 00  F7 8F 9C 7D  E0 65 98 7D  F1 1D 98 7D  ..:....}.e.}...}
 003AD690: 90 EB 15 00  F4 EF 9D 7D  10 00 00 00  28 D7 13 00  .......}....(...
 003AD6A0: 10 D7 3A 00  E2 A4 9C 7D  C0 80 14 00  C4 D6 3A 00  ..:....}......:.
 003AD6B0: 00 D7 3A 00  00 00 00 00  00 00 00 00  FF 02 00 00  ..:.............
 003AD6C0: DF 46 C3 7B  00 04 00 00  00 03 00 00  03 00 00 00  .F.{............
 003AD6D0: 01 00 00 00  00 00 00 00  00 00 00 00  01 00 00 00  ................
 003AD6E0: 6E 00 05 00  00 00 00 00  01 00 00 00  1A 00 00 00  n...............
 003AD6F0: 01 00 00 00  40 00 00 00  01 00 00 00  01 00 00 00  ....@...........
 003AD700: 01 00 00 00  00 00 00 00  68 37 B3 02  00 04 00 03  ........h7......
 

 

 ------------------------------------------------------------------------------
 

 ======================================================================
 Hardware/Driver Information:
 Processor:              0x0
 Page Size:              4096
 Min App Address:        0x10000
 Max App Address:        0x7ffeffff
 Processor Mask:         0x3
 Number of Processors:   2
 Processor Type:         586
 Allocation Granularity: 65536
 Processor Level:        6
 Processor Revision:     5898
 Os Version:             5.1
 Os Service Pack:        3.0
 

 Percent memory used:    89
 Total physical memory:  1050849280
 Free Memory:            111079424
 Page file:              1756811264
 Total virtual memory:   2147352575
 if anyone here has ever had this happen to him/her, or if you jsut know what this is about, i'd greatly appreciate any help on the matter

---

