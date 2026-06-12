---
title: "UPS Worlship with wine..."
date: 2009-07-25
forum: General Help
---

### Post by BarefootSoul83 on 2009-07-25
I'm trying to install UPS Worldship 10.0 on Ubuntu

I have gotten through a few hoops but I am a beginner... can someone take a look @ this for me...Thanks

(I did get the mfc42.dll file and put it into:    wine/..../.../system32) I was told that Linux is case sensitive so I renamed the file in all caps..eg. MFC42.dll) 



donald@Tux:/media/cdrom0$ wine Setup.exe
wine: Call from 0x401d44 to unimplemented function MFC42.DLL.6927, aborting
wine: Unimplemented function MFC42.DLL.6927 called at address 0x401d44 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6927 called in 32-bit code (0x7bc46f80).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc46f80 ESP:0032fd44 EBP:0032fda8 EFLAGS:00000202(   - 00      - - I1)
 EAX:00001b0f EBX:7bc8aff4 ECX:00411334 EDX:0012ae10
 ESI:0032fd50 EDI:7eb563c0
Stack dump:
0x0032fd44:  00110014 7eb66ff4 ffffffff 80000100
0x0032fd54:  00000001 00000000 00401d44 00000002
0x0032fd64:  0040d928 00001b0f 7eb46a80 ffffffff
0x0032fd74:  00000009 7bc68f3b 0012ae1c 0012ad90
0x0032fd84:  00000009 00411308 0012ad90 0012ad90
0x0032fd94:  00411308 5f408c08 0012ae1c 00000000
Backtrace:
=>1 0x7bc46f80 in ntdll (+0x36f80) (0x0032fda8)
  2 0x00401d44 in setup (+0x1d44) (0x00411308)
  3 0x00000001 (0x0040b6dc)
  4 0x00401970 in setup (+0x1970) (0x00409a88)
  5 0x25ff0040 (0xb31025ff)
  6 0x00000000 (0x00000000)
0x7bc46f80: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (56 modules)
PE      400000-  41f000    Export          setup
PE    5f400000-5f4ed000    Deferred        mfc42
ELF    7b800000-7b93d000    Deferred        kernel32<elf>
  \-PE    7b820000-7b93d000    \               kernel32
ELF    7bc00000-7bca7000    Export          ntdll<elf>
  \-PE    7bc10000-7bca7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e7be000-7e7c7000    Deferred        libxcursor.so.1
ELF    7e7c7000-7e7cc000    Deferred        libxfixes.so.3
ELF    7e7cc000-7e7d0000    Deferred        libxcomposite.so.1
ELF    7e7d0000-7e7d8000    Deferred        libxrandr.so.2
ELF    7e7d8000-7e7e2000    Deferred        libxrender.so.1
ELF    7e7e2000-7e7e5000    Deferred        libxinerama.so.1
ELF    7e7e5000-7e806000    Deferred        imm32<elf>
  \-PE    7e7f0000-7e806000    \               imm32
ELF    7e806000-7e80b000    Deferred        libxdmcp.so.6
ELF    7e80b000-7e825000    Deferred        libxcb.so.1
ELF    7e825000-7e829000    Deferred        libxau.so.6
ELF    7e829000-7e82e000    Deferred        libuuid.so.1
ELF    7e82e000-7e91d000    Deferred        libx11.so.6
ELF    7e91d000-7e92d000    Deferred        libxext.so.6
ELF    7e92d000-7e933000    Deferred        libxxf86vm.so.1
ELF    7e933000-7e94b000    Deferred        libice.so.6
ELF    7e94b000-7e954000    Deferred        libsm.so.6
ELF    7e965000-7ea00000    Deferred        winex11<elf>
  \-PE    7e970000-7ea00000    \               winex11
ELF    7ea13000-7ea3a000    Deferred        libexpat.so.1
ELF    7ea3a000-7ea67000    Deferred        libfontconfig.so.1
ELF    7ea78000-7ea8e000    Deferred        libz.so.1
ELF    7ea8e000-7eb05000    Deferred        libfreetype.so.6
ELF    7eb16000-7eb82000    Deferred        msvcrt<elf>
  \-PE    7eb30000-7eb82000    \               msvcrt
ELF    7eb82000-7eba5000    Deferred        mpr<elf>
  \-PE    7eb90000-7eba5000    \               mpr
ELF    7eba5000-7ebf8000    Deferred        advapi32<elf>
  \-PE    7ebb0000-7ebf8000    \               advapi32
ELF    7ebf8000-7ec98000    Deferred        gdi32<elf>
  \-PE    7ec10000-7ec98000    \               gdi32
ELF    7ec98000-7ede4000    Deferred        user32<elf>
  \-PE    7ecb0000-7ede4000    \               user32
ELF    7ede4000-7ee3f000    Deferred        shlwapi<elf>
  \-PE    7edf0000-7ee3f000    \               shlwapi
ELF    7ee3f000-7ee54000    Deferred        lz32<elf>
  \-PE    7ee40000-7ee54000    \               lz32
ELF    7ee54000-7ee6f000    Deferred        version<elf>
  \-PE    7ee60000-7ee6f000    \               version
ELF    7ef99000-7efa5000    Deferred        libnss_files.so.2
ELF    7efa5000-7efb0000    Deferred        libnss_nis.so.2
ELF    7efb0000-7efc9000    Deferred        libnsl.so.1
ELF    7efc9000-7efef000    Deferred        libm.so.6
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    b7d08000-b7d0c000    Deferred        libdl.so.2
ELF    b7d0c000-b7e6f000    Deferred        libc.so.6
ELF    b7e70000-b7e89000    Deferred        libpthread.so.0
ELF    b7e9a000-b7fd1000    Deferred        libwine.so.1
ELF    b7fd3000-b7ff1000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\Setup.exe
    00000009    0 <==
0000000c 
    00000014    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000016    0
    00000015    0
    00000011    0
    00000010    0
00000017 
    00000018    0
Backtrace:
=>1 0x7bc46f80 in ntdll (+0x36f80) (0x0032fda8)
  2 0x00401d44 in setup (+0x1d44) (0x00411308)
  3 0x00000001 (0x0040b6dc)
  4 0x00401970 in setup (+0x1970) (0x00409a88)
  5 0x25ff0040 (0xb31025ff)
  6 0x00000000 (0x00000000)
wine: Call from 0x401d44 to unimplemented function MFC42.DLL.6927, aborting

---

