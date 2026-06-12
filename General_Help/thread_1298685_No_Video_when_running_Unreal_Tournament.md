---
title: "No Video when running Unreal Tournament"
date: 2009-10-23
forum: General Help
---

### Post by ducktapebz on 2009-10-23
Hello, i'm trying to get the first Unreal Tournament working on ubuntu 9.0.4. i dont have the disc and i'm running it thru wine. when i start it i have sound but no video, i have no idea what it could be... any ideas?
 
heres the error: 
```
zach@home-desktop:~$ wine PROGRAM Unreal Tournament
fixme:ntoskrnl:KeInitializeMutex stub: 0x1318e0, 0
fixme:ntoskrnl:KeInitializeMutex stub: 0x130ec8, 0
fixme:ntoskrnl:KeInitializeMutex stub: 0x130ff0, 0
fixme:ntoskrnl:KeInitializeMutex stub: 0x131030, 0
fixme:ntoskrnl:KeInitializeMutex stub: 0x131070, 0
fixme:ntoskrnl:KeInitializeMutex stub: 0x1310b0, 0
fixme:ntoskrnl:KeInitializeMutex stub: 0x1310f0, 0
fixme:ntoskrnl:IoGetDeviceObjectPointer stub: L"\\Device\\DebugMessageDevice" 1f01ff 0x64e684 0x64e680
fixme:ntoskrnl:KeInitializeEvent stub: 0x131cc0 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x131cd8 1 0
fixme:ntoskrnl:IoRegisterDriverReinitialization stub: 0x7ee914a0 0x6568cf 0x131a60
wine: Unhandled page fault on read access to 0x80a9a018 at address 0x66901b (thread 001c), starting debugger...
Unhandled exception: page fault on read access to 0x80a9a018 in 32-bit code (0x0066901b).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0066901b ESP:0064e71c EBP:0064e760 EFLAGS:00010202(  R- --  I   - - - )
 EAX:80a9a000 EBX:001319c0 ECX:00000000 EDX:00000053
 ESI:00000000 EDI:00000000
Stack dump:
0x0064e71c:  a0000fff 000080a9 00669246 0064e9dc
0x0064e72c:  001319e0 7ede2280 00000000 00000018
0x0064e73c:  00000000 0064e6d8 00000040 00000000
0x0064e74c:  00000000 00000040 00000000 00000000
0x0064e75c:  00000000 001319c0 00669343 0064e9dc
0x0064e76c:  006500e0 0066934a 7ee90ff4 0064e9f8
Backtrace:
=>0 0x0066901b in tpkd.sys (+0x1901b) (0x0064e760)
  1 0x00669343 in tpkd.sys (+0x19343) (0x001319c0)
  2 0x7ee914a0 in winedevice (+0x114a0) (0x006624a0)
  3 0x00656b90 in tpkd.sys (+0x6b90) (0x006691a6)
  4 0x56532cec (0x83ec8b55)
  5 0x00000000 (0x00000000)
0x0066901b: xorl	0x18(%eax),%ecx
Modules:
Module	Address			Debug info	Name (30 modules)
PE	  650000-  66e000	Export          tpkd.sys
ELF	7b800000-7b972000	Deferred        kernel32<elf>
  \-PE	7b820000-7b972000	\               kernel32
ELF	7bc00000-7bcb2000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb2000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ecb9000-7ecd0000	Deferred        hal<elf>
  \-PE	7ecc0000-7ecd0000	\               hal
ELF	7ecd0000-7ed3f000	Deferred        msvcrt<elf>
  \-PE	7ece0000-7ed3f000	\               msvcrt
ELF	7ed3f000-7edad000	Deferred        rpcrt4<elf>
  \-PE	7ed50000-7edad000	\               rpcrt4
ELF	7edad000-7edc2000	Deferred        system.drv16.so
PE	7edb0000-7edc2000	Deferred        system.drv16
ELF	7edc2000-7edfd000	Deferred        ntoskrnl<elf>
  \-PE	7edd0000-7edfd000	\               ntoskrnl
ELF	7edfd000-7ee54000	Deferred        advapi32<elf>
  \-PE	7ee10000-7ee54000	\               advapi32
ELF	7ee54000-7ee60000	Deferred        libnss_files.so.2
ELF	7ee60000-7ee6b000	Deferred        libnss_nis.so.2
ELF	7ee6b000-7ee74000	Deferred        libnss_compat.so.2
ELF	7ee7d000-7ee92000	Export          winedevice<elf>
  \-PE	7ee80000-7ee92000	\               winedevice
ELF	7efbc000-7efe2000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        libnsl.so.1
ELF	f7cc1000-f7cc5000	Deferred        libdl.so.2
ELF	f7cc5000-f7e28000	Deferred        libc.so.6
ELF	f7e29000-f7e42000	Deferred        libpthread.so.0
ELF	f7e60000-f7f9c000	Deferred        libwine.so.1
ELF	f7f9e000-f7fbf000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	0000000d    0
0000000e 
	0000001b    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 (D) C:\windows\system32\winedevice.exe
	0000001c    0 <==
	0000001a    0
	00000019    0
Backtrace:
=>0 0x0066901b in tpkd.sys (+0x1901b) (0x0064e760)
  1 0x00669343 in tpkd.sys (+0x19343) (0x001319c0)
  2 0x7ee914a0 in winedevice (+0x114a0) (0x006624a0)
  3 0x00656b90 in tpkd.sys (+0x6b90) (0x006691a6)
  4 0x56532cec (0x83ec8b55)
  5 0x00000000 (0x00000000)
wine: could not load L"C:\\windows\\system32\\PROGRAM.exe": Module not found
zach@home-desktop:~$ err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/zach/.local/share/mime/packages/x-wine-extension-/bzw.xml
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/zach/.local/share/applications/wine-extension-/bzw.desktop"
File '/home/zach/.local/share/applications/wine-extension-skp.desktop' contains invalid MIME type 'SKP' that is missing a slash
```

---

