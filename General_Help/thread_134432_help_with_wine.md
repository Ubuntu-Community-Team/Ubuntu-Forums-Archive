---
title: "help with wine"
date: 2006-02-21
forum: General Help
---

### Post by shiroma on 2006-02-21
i installed wine a few days ago and everytime i get this when i run winecfg.
i tryed to reinstal using synaptic package manager and automatix



wine: creating configuration directory '/home/ryan/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ec2613f (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ec2613f).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ec2613f ESP:7faffc2c EBP:7faffc68 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c0f2e40 ECX:b7f52900 EDX:7c028078
 ESI:7c028078 EDI:7c028078
Stack dump:
0x00000000:  00000000 00000000 00000000 00000000
0x00000010:  00000000 00000000 00000000 00000000
0x00000020:  00000000 00000000 00000000 00000000
0x00000030:  00000000 00000000 00000000 00000000
0x00000040:  00000000 00000000 00000000 00000000
0x00000050:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ec2613f in libgl.so.1 (+0x3613f) (0x7ec2613f)
  2 0x7ed9edb7 X11DRV_GDI_Finalize+0x27 in winex11 (0x7ed9edb7)
  3 0x7edb5251 DllMain+0x41 in winex11 (0x7edb5251)
  4 0x7edc432c in winex11 (+0x5432c) (0x7edc432c)
  5 0x7bebc0e5 call_dll_entry_point+0x15 in ntdll (0x7bebc0e5)
  6 0x7bebcefa in ntdll (+0x1cefa) (0x7bebcefa)
  7 0x7bebd1da in ntdll (+0x1d1da) (0x7bebd1da)
  8 0x7fcdb799 ExitProcess+0x19 in kernel32 (0x7fcdb799)
  9 0x7fb1eb36 in rundll32 (+0xeb36) (0x7fb1eb36)
  10 0x7fcdce0f in kernel32 (+0x4ce0f) (0x7fcdce0f)
  11 0xb7f6d237 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f6d237)
0x7ec2613f: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (94 modules)
ELF     0x7be87000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d999000-7d9b0000     Deferred        advpack<elf>
  \-PE  0x7d9a0000-7d9b0000     \               advpack
ELF     0x7daf3000-7db4b000     Deferred        shlwapi<elf>
  \-PE  0x7db10000-7db4b000     \               shlwapi
ELF     0x7db4b000-7dc10000     Deferred        shell32<elf>
  \-PE  0x7db60000-7dc10000     \               shell32
ELF     0x7dc10000-7dc41000     Deferred        uxtheme<elf>
  \-PE  0x7dc20000-7dc41000     \               uxtheme
ELF     0x7dc41000-7dcf5000     Deferred        comctl32<elf>
  \-PE  0x7dc50000-7dcf5000     \               comctl32
ELF     0x7dcf5000-7dd45000     Deferred        dsound<elf>
  \-PE  0x7dd10000-7dd45000     \               dsound
ELF     0x7dd45000-7dda0000     Deferred        quartz<elf>
  \-PE  0x7dd60000-7dda0000     \               quartz
ELF     0x7deb2000-7dec7000     Deferred        midimap<elf>
  \-PE  0x7dec0000-7dec7000     \               midimap
ELF     0x7dec7000-7dede000     Deferred        msacm<elf>
  \-PE  0x7ded0000-7dede000     \               msacm
ELF     0x7dede000-7df21000     Deferred        wineoss<elf>
  \-PE  0x7def0000-7df21000     \               wineoss
ELF     0x7df44000-7df69000     Deferred        msvfw32<elf>
  \-PE  0x7df50000-7df69000     \               msvfw32
ELF     0x7df69000-7dffa000     Deferred        oleaut32<elf>
  \-PE  0x7df80000-7dffa000     \               oleaut32
ELF     0x7dffa000-7e085000     Deferred        ole32<elf>
  \-PE  0x7e010000-7e085000     \               ole32
ELF     0x7e085000-7e10c000     Deferred        winmm<elf>
  \-PE  0x7e090000-7e10c000     \               winmm
ELF     0x7e10c000-7e130000     Deferred        msacm32<elf>
  \-PE  0x7e110000-7e130000     \               msacm32
ELF     0x7e245000-7e259000     Deferred        avicap32<elf>
  \-PE  0x7e250000-7e259000     \               avicap32
ELF     0x7e259000-7e27f000     Deferred        devenum<elf>
  \-PE  0x7e270000-7e27f000     \               devenum
ELF     0x7e27f000-7e29d000     Deferred        iphlpapi<elf>
  \-PE  0x7e290000-7e29d000     \               iphlpapi
ELF     0x7e29d000-7e2e5000     Deferred        rpcrt4<elf>
  \-PE  0x7e2b0000-7e2e5000     \               rpcrt4
ELF     0x7e2e5000-7e2f9000     Deferred        lz32<elf>
  \-PE  0x7e2f0000-7e2f9000     \               lz32
ELF     0x7e2f9000-7e312000     Deferred        version<elf>
  \-PE  0x7e300000-7e312000     \               version
ELF     0x7e312000-7e365000     Deferred        setupapi<elf>
  \-PE  0x7e320000-7e365000     \               setupapi
ELF     0x7e433000-7e43c000     Deferred        libxcursor.so.1
ELF     0x7e43c000-7e458000     Deferred        imm32<elf>
  \-PE  0x7e440000-7e458000     \               imm32
ELF     0x7e458000-7e474000     Deferred        ximcp.so.2
ELF     0x7e474000-7e47c000     Deferred        libxrender.so.1
ELF     0x7e487000-7ebf0000     Deferred        libglcore.so.1
ELF     0x7ebf0000-7ec6f000     Export          libgl.so.1
ELF     0x7ec6f000-7ec73000     Deferred        libxdmcp.so.6
ELF     0x7ec73000-7ed33000     Deferred        libx11.so.6
ELF     0x7ed33000-7ed40000     Deferred        libxext.so.6
ELF     0x7ed40000-7ed45000     Deferred        libxxf86vm.so.1
ELF     0x7ed45000-7ed5e000     Deferred        libice.so.6
ELF     0x7ed5e000-7eddd000     Export          winex11<elf>
  \-PE  0x7ed70000-7eddd000     \               winex11
ELF     0x7eddd000-7edfc000     Deferred        libexpat.so.1
ELF     0x7edfc000-7ee2a000     Deferred        libfontconfig.so.1
ELF     0x7ee2a000-7ee3e000     Deferred        libz.so.1
ELF     0x7ee3e000-7eea8000     Deferred        libfreetype.so.6
ELF     0x7eea8000-7eee5000     Deferred        advapi32<elf>
  \-PE  0x7eeb0000-7eee5000     \               advapi32
ELF     0x7efcb000-7f8ce000     Deferred        gdi32<elf>
  \-PE  0x7f010000-7f8ce000     \               gdi32
ELF     0x7f8ce000-7f9f0000     Deferred        user32<elf>
  \-PE  0x7f8f0000-7f9f0000     \               user32
ELF     0x7fb01000-7fb0c000     Deferred        libgcc_s.so.1
ELF     0x7fb0c000-7fb20000     Export          rundll32<elf>
  \-PE  0x7fb10000-7fb20000     \               rundll32
ELF     0x7fb24000-7fb29000     Deferred        libxxf86dga.so.1
ELF     0x7fc71000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe81000-7fe88000     Deferred        libsm.so.6
ELF     0x7fe88000-7fe92000     Deferred        libnss_files.so.2
ELF     0x7fe92000-7fe9b000     Deferred        libnss_nis.so.2
ELF     0x7fe9b000-7feb0000     Deferred        libnsl.so.1
ELF     0x7feb0000-7feb9000     Deferred        libnss_compat.so.2
ELF     0x7feb9000-7febd000     Deferred        libxfixes.so.3
ELF     0x7febd000-7febf000     Deferred        xlcutf8load.so.2
ELF     0x7febf000-7fec2000     Deferred        libxrandr.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e21000-b7e23000     Deferred        libnvidia-tls.so.1
ELF     0xb7e24000-b7e27000     Deferred        libdl.so.2
ELF     0xb7e27000-b7f55000     Deferred        libc.so.6
ELF     0xb7f56000-b7f68000     Deferred        libpthread.so.0
ELF     0xb7f68000-b7f82000     Export          libwine.so.1
ELF     0xb7f82000-b7f85000     Deferred        libxau.so.6
ELF     0xb7f90000-b7fa6000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==
WineDbg terminated on pid 0x8

---

### Post by dcstar on 2006-02-22
[QUOTE=shiroma]i installed wine a few days ago and everytime i get this when i run winecfg.
i tryed to reinstal using synaptic package manager and automatix

wine: creating configuration directory '/home/ryan/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
......[/QUOTE]
Rename your hidden .wine directory (to something like wine.bad), and then in a user terminal do:

winecfg

and see if it starts up.

---

### Post by shiroma on 2006-02-23
that didnt work thaks for helping me though

---

### Post by arnieboy on 2006-02-23
your video drivers seem to be messed up. are u using a nvidia card by any chance? if yes, please let me know the exact model.

---

### Post by shiroma on 2006-02-24
yes i have an nvidia card. it is  a 6800gs. i used automatix to download the nvidia driver but thats all i have done

---

### Post by shiroma on 2006-02-24
i used one of the tutorials to get nvidia drivers working and i found out that i have been using vesa driver. but when i enter winecfg nothing happens

---

