---
title: "WINE problems!"
date: 2006-04-27
forum: General Help
---

### Post by chris062689 on 2006-04-27
Whenever I try to load up dreammaker.exe,  I get the following errors;

[email]chris@ubuntu:~/.wine[/email]/drive_c/Program Files/BYOND/bin$ wine dreammaker.exe
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\Program Files\\BYOND\\bin\\byondcore.dll") not found
err:module:import_dll Library byondcore.dll (which is needed by L"C:\\Program Files\\BYOND\\bin\\byondwin.dll") not found
err:module:import_dll Library byondwin.dll (which is needed by L"C:\\Program Files\\BYOND\\bin\\dreammaker.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\Program Files\\BYOND\\bin\\byondcore.dll") not found
err:module:import_dll Library byondcore.dll (which is needed by L"C:\\Program Files\\BYOND\\bin\\dreammaker.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\BYOND\\bin\\dreammaker.exe" failed, status c0000135


Even though I have the dll MSVCIRT in the Program Files directory!
What's wrong? ](*,)

---

### Post by bluevoodoo1 on 2006-04-27
[QUOTE=chris062689]
Even though I have the dll MSVCIRT in the Program Files directory!
What's wrong? ](*,)[/QUOTE]

Is it in the "BYOND\\bin\\" directory? As well as the other DLLs mentioned?

---

### Post by sinkxdie on 2006-04-27
Do you have a real Windows installation?
Transfer the file to the "C:\windows"+"C:\windows\system32" directorys in your .wine(hidden) folder in your home directory.

---

### Post by chris062689 on 2006-04-27
I moved it to system32, but now... it doesn't look very happy!
(You've angered the WINE beast!)

[email]chris@ubuntu:~/.wine[/email]/drive_c/Program Files/BYOND/bin$ wine "dreammaker.exe"
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ed88f4f (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ed88f4f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ed88f4f ESP:7fb9e438 EBP:7ee86a00 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:ffffffff EDX:7fcf0458
 ESI:7ee86a00 EDI:00000000
Stack dump:
0x7fb9e438:  7fcf0458 00000003 7ee86a00 7ee86a00
0x7fb9e448:  00000000 7ff93830 00000001 7ffd3d84
0x7fb9e458:  7fd4ffe8 7fd4ffe8 7fb9e4fc 7fb9e434
0x7fb9e468:  7ff8e6a3 00000001 00000000 00000000
0x7fb9e478:  b7e45d79 7ff93830 00000001 7ffd3d84
0x7fb9e488:  00400000 00400000 7fb9e538 7fb9e450
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ed88f4f in byondcore (+0xf8f4f) (0x7ed88f4f)
  2 0x00000000 (0x00000000)
0x7ed88f4f: repne scasb %es:(%edi)
Modules:
Module  Address                 Debug info      Name (92 modules)
PE      0x00400000-004db000     Deferred        dreammaker
PE      0x10000000-100c9000     Deferred        byondwin
PE      0x73dd0000-73ece000     Deferred        mfc42
PE      0x780a0000-780b5000     Deferred        msvcirt
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d7e7000-7d82c000     Deferred        riched20<elf>
  \-PE  0x7d800000-7d82c000     \               riched20
ELF     0x7d82c000-7d840000     Deferred        riched32<elf>
  \-PE  0x7d830000-7d840000     \               riched32
ELF     0x7d8aa000-7d8db000     Deferred        uxtheme<elf>
  \-PE  0x7d8b0000-7d8db000     \               uxtheme
ELF     0x7d8db000-7d8f0000     Deferred        midimap<elf>
  \-PE  0x7d8e0000-7d8f0000     \               midimap
ELF     0x7da03000-7da27000     Deferred        msacm32<elf>
  \-PE  0x7da10000-7da27000     \               msacm32
ELF     0x7da27000-7da3e000     Deferred        msacm<elf>
  \-PE  0x7da30000-7da3e000     \               msacm
ELF     0x7da3e000-7da82000     Deferred        wineoss<elf>
  \-PE  0x7da50000-7da82000     \               wineoss
ELF     0x7da82000-7da8b000     Deferred        libxcursor.so.1
ELF     0x7da8b000-7daa7000     Deferred        imm32<elf>
  \-PE  0x7da90000-7daa7000     \               imm32
ELF     0x7daa7000-7daaf000     Deferred        libxrender.so.1
ELF     0x7e3af000-7e5b1000     Deferred        i915_dri.so
ELF     0x7e5b1000-7e617000     Deferred        libgl.so.1
ELF     0x7e617000-7e6fd000     Deferred        libx11.so.6
ELF     0x7e6fd000-7e715000     Deferred        libice.so.6
ELF     0x7e715000-7e794000     Deferred        winex11<elf>
  \-PE  0x7e720000-7e794000     \               winex11
ELF     0x7e794000-7e7b3000     Deferred        libexpat.so.1
ELF     0x7e7b3000-7e7e1000     Deferred        libfontconfig.so.1
ELF     0x7e7e1000-7e7f5000     Deferred        libz.so.1
ELF     0x7e7f5000-7e85e000     Deferred        libfreetype.so.6
ELF     0x7e85e000-7e8f0000     Deferred        oleaut32<elf>
  \-PE  0x7e880000-7e8f0000     \               oleaut32
PE      0x7e8f0000-7e90a000     Deferred        libpng
ELF     0x7e90a000-7e90e000     Deferred        libxfixes.so.3
ELF     0x7e90e000-7e970000     Deferred        msvcrt<elf>
  \-PE  0x7e920000-7e970000     \               msvcrt
PE      0x7e970000-7e97f000     Deferred        zip
ELF     0x7e981000-7ea36000     Deferred        comctl32<elf>
  \-PE  0x7e990000-7ea36000     \               comctl32
ELF     0x7ea36000-7ea7f000     Deferred        rpcrt4<elf>
  \-PE  0x7ea50000-7ea7f000     \               rpcrt4
ELF     0x7ea7f000-7eb0b000     Deferred        ole32<elf>
  \-PE  0x7ea90000-7eb0b000     \               ole32
ELF     0x7eb0b000-7eb64000     Deferred        shlwapi<elf>
  \-PE  0x7eb20000-7eb64000     \               shlwapi
ELF     0x7eb64000-7ec30000     Deferred        shell32<elf>
  \-PE  0x7eb80000-7ec30000     \               shell32
ELF     0x7ec30000-7ec4e000     Deferred        iphlpapi<elf>
  \-PE  0x7ec40000-7ec4e000     \               iphlpapi
ELF     0x7ec4e000-7ec77000     Deferred        ws2_32<elf>
  \-PE  0x7ec60000-7ec77000     \               ws2_32
ELF     0x7ec77000-7ec90000     Deferred        wsock32<elf>
  \-PE  0x7ec80000-7ec90000     \               wsock32
PE      0x7ec90000-7ee9c000     Export          byondcore
ELF     0x7ee9d000-7eea4000     Deferred        libdrm.so.2
ELF     0x7eea4000-7eee2000     Deferred        advapi32<elf>
  \-PE  0x7eeb0000-7eee2000     \               advapi32
ELF     0x7efb7000-7f8bb000     Deferred        gdi32<elf>
  \-PE  0x7f000000-7f8bb000     \               gdi32
ELF     0x7f8bb000-7f9dd000     Deferred        user32<elf>
  \-PE  0x7f8e0000-7f9dd000     \               user32
ELF     0x7f9dd000-7fa63000     Deferred        winmm<elf>
  \-PE  0x7f9f0000-7fa63000     \               winmm
ELF     0x7fa63000-7fa77000     Deferred        lz32<elf>
  \-PE  0x7fa70000-7fa77000     \               lz32
ELF     0x7fa77000-7fa90000     Deferred        version<elf>
  \-PE  0x7fa80000-7fa90000     \               version
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb3000-7fbb6000     Deferred        libxrandr.so.2
ELF     0x7fbb6000-7fbb9000     Deferred        libxau.so.6
ELF     0x7fbb9000-7fbbe000     Deferred        libxxf86vm.so.1
ELF     0x7fbf1000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe02000-7fe0c000     Deferred        libgcc_s.so.1
ELF     0x7fe0c000-7fe16000     Deferred        libnss_files.so.2
ELF     0x7fe16000-7fe1f000     Deferred        libnss_nis.so.2
ELF     0x7fe1f000-7fe34000     Deferred        libnsl.so.1
ELF     0x7fe34000-7fe3d000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4d000-7fe6f000     Deferred        libm.so.6
ELF     0x7fe6f000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e1a000-b7e1d000     Deferred        libdl.so.2
ELF     0xb7e1d000-b7f4c000     Deferred        libc.so.6
ELF     0xb7f4c000-b7f5e000     Deferred        libpthread.so.0
ELF     0xb7f6c000-b7f86000     Deferred        libwine.so.1
ELF     0xb7f89000-b7f9f000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) C:\Program Files\BYOND\bin\dreammaker.exe
        00000009    0 <==
[email]chris@ubuntu:~/.wine[/email]/drive_c/Program Files/BYOND/bin$

---

### Post by sinkxdie on 2006-04-27
Sorry...:(

---

