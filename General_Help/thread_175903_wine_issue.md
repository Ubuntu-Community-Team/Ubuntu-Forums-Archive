---
title: "wine issue"
date: 2006-05-14
forum: General Help
---

### Post by wana10 on 2006-05-14
when ever i run a program in wine a window pops up asking me "unhandled page faulton write access to 0x00000074 at address 0x7e627550. Do you wish to debug it?" clicking yes causes it to think for a little and then quit, no causes it to quit instantly. terminal shows this,
```
wesley@ubuntu:~/.wine/drive_c/Cavedog/TotalA/Demo$ wine TADemo.exe
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
wine: Unhandled page fault on write access to 0x00000074 at address 0x7e627550 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x00000074 in 32-bit code (0x7e627550).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7e627550 ESP:7fb0f8a8 EBP:7fb0f8a8 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7e7dc690 ECX:7e7dc690 EDX:7c1c7644
 ESI:7c1c73c0 EDI:7c074f60
Stack dump:
0x7fb0f8a8:  7fb0fb58 7e62c304 00000000 7c1c7644
0x7fb0f8b8:  00000000 0000000c 00000040 7d6099dc
0x7fb0f8c8:  7d609dec 7c1c7584 0000010c 7e65055c
0x7fb0f8d8:  00000000 7c1c7644 7c022be0 7c1c7658
0x7fb0f8e8:  7c1c757c 7c1c7584 7c016260 00000000
0x7fb0f8f8:  7c022be0 7fcf2b7e 00000000 7fb0fa0c
0200: sel=1007 base=7fec2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7e627550 driSetTextureSwapCounterLocation+0x18 in r128_dri.so (0x7e627550)  2 0x7e62c304 r128CreateContext+0x4e8 in r128_dri.so (0x7e62c304)
  3 0x7e628f68 in r128_dri.so (+0x1df68) (0x7e628f68)
  4 0x7e83228a in libgl.so.1 (+0x3328a) (0x7e83228a)
  5 0x7e832599 glXCreateContext+0x38 in libgl.so.1 (0x7e832599)
  6 0x7ead0a4b d3ddevice_init_at_startup+0x15b in ddraw (0x7ead0a4b)
  7 0x7eaeca92 DllMain+0x10b2 in ddraw (0x7eaeca92)
  8 0x7eaf8aec in ddraw (+0x38aec) (0x7eaf8aec)
  9 0x7bebb065 call_dll_entry_point+0x15 in ntdll (0x7bebb065)
  10 0x7bebc57a in ntdll (+0x1c57a) (0x7bebc57a)
  11 0x7bebc85c in ntdll (+0x1c85c) (0x7bebc85c)
  12 0x7bebc832 in ntdll (+0x1c832) (0x7bebc832)
  13 0x7bebf4bc LdrInitializeThunk+0x34c in ntdll (0x7bebf4bc)
  14 0x7fcdd1ac in kernel32 (+0x4d1ac) (0x7fcdd1ac)
  15 0xb7f425f7 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f425f7)
0x7e627550 driSetTextureSwapCounterLocation+0x18 in r128_dri.so: movl   %edx,0x74(%eax)
Modules:
Module  Address                 Debug info      Name (80 modules)
PE      0x00400000-0051a000     Deferred        tademo
ELF     0x7be86000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7cc2a000-7cc5b000     Deferred        uxtheme<elf>
  \-PE  0x7cc30000-7cc5b000     \               uxtheme
ELF     0x7cc5b000-7cc70000     Deferred        midimap<elf>
  \-PE  0x7cc60000-7cc70000     \               midimap
ELF     0x7cd87000-7cdab000     Deferred        msacm32<elf>
  \-PE  0x7cd90000-7cdab000     \               msacm32
ELF     0x7cdab000-7cdc2000     Deferred        msacm<elf>
  \-PE  0x7cdb0000-7cdc2000     \               msacm
ELF     0x7cdc2000-7ce75000     Deferred        libasound.so.2
ELF     0x7ce75000-7ce96000     Deferred        libaudiofile.so.0
ELF     0x7ce96000-7cea0000     Deferred        libesd.so.0
ELF     0x7cea0000-7ceba000     Deferred        wineesd<elf>
  \-PE  0x7ceb0000-7ceba000     \               wineesd
ELF     0x7ced8000-7cedc000     Deferred        libxfixes.so.3
ELF     0x7cedc000-7cee5000     Deferred        libxcursor.so.1
ELF     0x7cee5000-7cf01000     Deferred        imm32<elf>
  \-PE  0x7cef0000-7cf01000     \               imm32
ELF     0x7cf01000-7cf1d000     Deferred        ximcp.so.2
ELF     0x7cf1d000-7cf25000     Deferred        libxrender.so.1
ELF     0x7e60b000-7e7f8000     Export          r128_dri.so
ELF     0x7e7f8000-7e7ff000     Deferred        libdrm.so.1
ELF     0x7e7ff000-7e865000     Export          libgl.so.1
ELF     0x7e865000-7e8e4000     Deferred        winex11<elf>
  \-PE  0x7e870000-7e8e4000     \               winex11
ELF     0x7e8e4000-7e903000     Deferred        libexpat.so.1
ELF     0x7e903000-7e931000     Deferred        libfontconfig.so.1
ELF     0x7e931000-7e945000     Deferred        libz.so.1
ELF     0x7e945000-7e9af000     Deferred        libfreetype.so.6
ELF     0x7e9af000-7e9b3000     Deferred        libxdmcp.so.6
ELF     0x7e9b3000-7ea73000     Deferred        libx11.so.6
ELF     0x7ea73000-7ea80000     Deferred        libxext.so.6
ELF     0x7ea80000-7ea99000     Deferred        libice.so.6
ELF     0x7ea99000-7eb14000     Export          ddraw<elf>
  \-PE  0x7eac0000-7eb14000     \               ddraw
ELF     0x7eb14000-7eb65000     Deferred        dsound<elf>
  \-PE  0x7eb30000-7eb65000     \               dsound
ELF     0x7eb65000-7ec1a000     Deferred        comctl32<elf>
  \-PE  0x7eb70000-7ec1a000     \               comctl32
ELF     0x7ec1a000-7ec38000     Deferred        iphlpapi<elf>
  \-PE  0x7ec20000-7ec38000     \               iphlpapi
ELF     0x7ec38000-7ec80000     Deferred        rpcrt4<elf>
  \-PE  0x7ec50000-7ec80000     \               rpcrt4
ELF     0x7ec80000-7ed0c000     Deferred        ole32<elf>
  \-PE  0x7eca0000-7ed0c000     \               ole32
ELF     0x7ed0c000-7ed64000     Deferred        shlwapi<elf>
  \-PE  0x7ed20000-7ed64000     \               shlwapi
ELF     0x7ed64000-7ee30000     Deferred        shell32<elf>
  \-PE  0x7ed80000-7ee30000     \               shell32
ELF     0x7ee30000-7ee6e000     Deferred        advapi32<elf>
  \-PE  0x7ee40000-7ee6e000     \               advapi32
ELF     0x7ef54000-7f857000     Deferred        gdi32<elf>
  \-PE  0x7efa0000-7f857000     \               gdi32
ELF     0x7f857000-7f979000     Deferred        user32<elf>
  \-PE  0x7f870000-7f979000     \               user32
ELF     0x7f979000-7fa00000     Deferred        winmm<elf>
  \-PE  0x7f980000-7fa00000     \               winmm
ELF     0x7fb10000-7fb15000     Deferred        libxxf86vm.so.1
ELF     0x7fb15000-7fb20000     Deferred        libgcc_s.so.1
ELF     0x7fb24000-7fb29000     Deferred        libxxf86dga.so.1
ELF     0x7fc71000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe80000-7fe83000     Deferred        libxrandr.so.2
ELF     0x7fe83000-7fe8e000     Deferred        libnss_files.so.2
ELF     0x7fe8e000-7fe98000     Deferred        libnss_nis.so.2
ELF     0x7fe98000-7feae000     Deferred        libnsl.so.1
ELF     0x7feae000-7feb8000     Deferred        libnss_compat.so.2
ELF     0x7feb8000-7febb000     Deferred        libxau.so.6
ELF     0x7febb000-7fec2000     Deferred        libsm.so.6
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7dee000-b7df2000     Deferred        libdl.so.2
ELF     0xb7df2000-b7f20000     Deferred        libc.so.6
ELF     0xb7f20000-b7f33000     Deferred        libpthread.so.0
ELF     0xb7f33000-b7f35000     Deferred        xlcutf8load.so.2
ELF     0xb7f3d000-b7f57000     Export          libwine.so.1
ELF     0xb7f59000-b7f6f000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) C:\Cavedog\TotalA\Demo\TADemo.exe
        00000009    0 <==
wesley@ubuntu:~/.wine/drive_c/Cavedog/TotalA/Demo$


```
this happens for every program i run under wine, any help would be greatly appreciated.

---

### Post by YokoZar on 2006-05-14
How did you install Wine?

You should be using the latest version from here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Other than that, there might be something seriously wrong with your wine configuration.  As a test, try renaming your ~/.wine directory to something like ~/.wine.backup  (you can use the command *mv ~/.wine ~/.wine.backup* in a terminal).

Then, try running winecfg again, and click ok - this will recreate the .wine directory from scratch with the default configuration.  Then try launching an app, and see if it still crashes.

---

