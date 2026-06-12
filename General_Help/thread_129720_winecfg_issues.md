---
title: "winecfg issues"
date: 2006-02-14
forum: General Help
---

### Post by harty83 on 2006-02-14
Hello,

I installed wine from the repository and tried to run winecfg. I get a page fault, and the backtrace.  Nothing happens except that wine-preloader sucks my system resources.

Below is the backtrace I get.  Any ideas on how to get wine fixed? Or am I doing something wrong (which is VERY possible)?  Thanks!

```
alan@hartyslaptop:~$ winecfg
wine: creating configuration directory '/home/alan/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7f5ee4ff (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7f5ee4ff).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f5ee4ff ESP:7fbafc44 EBP:7fbafc80 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c150418 ECX:b7ee5240 EDX:7c02c620
 ESI:7c02c620 EDI:7c02c620
Stack dump:
0x7fbafc44:  7c02c620 7f6238e0 7c02c620 7f5ecd56
0x7fbafc54:  7c02c620 7c02c620 7f717760 7c14f4e8
0x7fbafc64:  7f64c3f3 7c02c620 7c14f4ec 00000001
0x7fbafc74:  7f7bc20c 7f7c3638 00000000 7fbafc94
0x7fbafc84:  7f782d48 7c02c620 7f7bc20c 7ffdf6bc
0x7fbafc94:  7fbafde4 7f79abdf 7eaa66f0 7fd8e870
0200: sel=1007 base=7ff64000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7f5ee4ff in libgl.so.1 (+0x304ff) (0x7f5ee4ff)
  2 0x7f782d48 X11DRV_GDI_Finalize+0x28 in winex11 (0x7f782d48)
  3 0x7f79abdf DllMain+0x40 in winex11 (0x7f79abdf)
  4 0x7f7ab18a in winex11 (+0x5b18a) (0x7f7ab18a)
  5 0x7ff9d855 call_dll_entry_point+0x15 in ntdll (0x7ff9d855)
  6 0x7ff9e617 in ntdll (+0x1e617) (0x7ff9e617)
  7 0x7ff9e8df in ntdll (+0x1e8df) (0x7ff9e8df)
  8 0x7fc59d6c ExitProcess+0x1b in kernel32 (0x7fc59d6c)
  9 0x7fe2de2f in rundll32 (+0xde2f) (0x7fe2de2f)
  10 0x7fc5b403 in kernel32 (+0x4b403) (0x7fc5b403)
  11 0xb7effb1b wine_switch_to_stack+0x17 in libwine.so.1 (0xb7effb1b)
0x7f5ee4ff: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (90 modules)
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e3b9000-7e3d0000     Deferred        advpack<elf>
  \-PE  0x7e3c0000-7e3d0000     \               advpack
ELF     0x7e4ec000-7e546000     Deferred        shlwapi<elf>
  \-PE  0x7e500000-7e546000     \               shlwapi
ELF     0x7e546000-7e60f000     Deferred        shell32<elf>
  \-PE  0x7e560000-7e60f000     \               shell32
ELF     0x7e60f000-7e640000     Deferred        uxtheme<elf>
  \-PE  0x7e620000-7e640000     \               uxtheme
ELF     0x7e640000-7e700000     Deferred        comctl32<elf>
  \-PE  0x7e650000-7e700000     \               comctl32
ELF     0x7e700000-7e752000     Deferred        dsound<elf>
  \-PE  0x7e710000-7e752000     \               dsound
ELF     0x7e752000-7e7b0000     Deferred        quartz<elf>
  \-PE  0x7e770000-7e7b0000     \               quartz
ELF     0x7e8c1000-7e8d6000     Deferred        midimap<elf>
  \-PE  0x7e8d0000-7e8d6000     \               midimap
ELF     0x7e8d6000-7e91a000     Deferred        wineoss<elf>
  \-PE  0x7e8f0000-7e91a000     \               wineoss
ELF     0x7e946000-7e96b000     Deferred        msvfw32<elf>
  \-PE  0x7e950000-7e96b000     \               msvfw32
ELF     0x7e96b000-7e9ff000     Deferred        oleaut32<elf>
  \-PE  0x7e980000-7e9ff000     \               oleaut32
ELF     0x7e9ff000-7ea8e000     Deferred        ole32<elf>
  \-PE  0x7ea10000-7ea8e000     \               ole32
ELF     0x7ea8e000-7eb12000     Deferred        winmm<elf>
  \-PE  0x7eaa0000-7eb12000     \               winmm
ELF     0x7eb15000-7eb29000     Deferred        avicap32<elf>
  \-PE  0x7eb20000-7eb29000     \               avicap32
ELF     0x7eb29000-7eb50000     Deferred        devenum<elf>
  \-PE  0x7eb40000-7eb50000     \               devenum
ELF     0x7ec60000-7ec78000     Deferred        msacm<elf>
  \-PE  0x7ec70000-7ec78000     \               msacm
ELF     0x7ec78000-7ec9d000     Deferred        msacm32<elf>
  \-PE  0x7ec80000-7ec9d000     \               msacm32
ELF     0x7ec9d000-7ecbc000     Deferred        iphlpapi<elf>
  \-PE  0x7eca0000-7ecbc000     \               iphlpapi
ELF     0x7ecbc000-7ed05000     Deferred        rpcrt4<elf>
  \-PE  0x7ecd0000-7ed05000     \               rpcrt4
ELF     0x7ed05000-7ed19000     Deferred        lz32<elf>
  \-PE  0x7ed10000-7ed19000     \               lz32
ELF     0x7ed19000-7ed6e000     Deferred        setupapi<elf>
  \-PE  0x7ed20000-7ed6e000     \               setupapi
ELF     0x7ee3c000-7ee40000     Deferred        libxfixes.so.3
ELF     0x7ee40000-7ee49000     Deferred        libxcursor.so.1
ELF     0x7ee4c000-7ee65000     Deferred        version<elf>
  \-PE  0x7ee50000-7ee65000     \               version
ELF     0x7ee65000-7ee6d000     Deferred        libxrender.so.1
ELF     0x7ee6d000-7f5be000     Deferred        libglcore.so.1
ELF     0x7f5be000-7f636000     Export          libgl.so.1
ELF     0x7f636000-7f71c000     Deferred        libx11.so.6
ELF     0x7f71c000-7f729000     Deferred        libxext.so.6
ELF     0x7f729000-7f741000     Deferred        libice.so.6
ELF     0x7f741000-7f7c4000     Export          winex11<elf>
  \-PE  0x7f750000-7f7c4000     \               winex11
ELF     0x7f7c4000-7f7e3000     Deferred        libexpat.so.1
ELF     0x7f7e3000-7f811000     Deferred        libfontconfig.so.1
ELF     0x7f811000-7f825000     Deferred        libz.so.1
ELF     0x7f825000-7f88e000     Deferred        libfreetype.so.6
ELF     0x7f88e000-7f8aa000     Deferred        imm32<elf>
  \-PE  0x7f8a0000-7f8aa000     \               imm32
ELF     0x7f8aa000-7f8e9000     Deferred        advapi32<elf>
  \-PE  0x7f8c0000-7f8e9000     \               advapi32
ELF     0x7f8e9000-7f975000     Deferred        gdi32<elf>
  \-PE  0x7f900000-7f975000     \               gdi32
ELF     0x7f975000-7faa0000     Deferred        user32<elf>
  \-PE  0x7f990000-7faa0000     \               user32
ELF     0x7fbb3000-7fbbb000     Deferred        libsm.so.6
ELF     0x7fbee000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe00000-7fe05000     Deferred        libxxf86vm.so.1
ELF     0x7fe05000-7fe0f000     Deferred        libnss_files.so.2
ELF     0x7fe0f000-7fe18000     Deferred        libnss_nis.so.2
ELF     0x7fe1b000-7fe30000     Export          rundll32<elf>
  \-PE  0x7fe20000-7fe30000     \               rundll32
ELF     0x7fe31000-7fe34000     Deferred        libxrandr.so.2
ELF     0x7fe34000-7fe56000     Deferred        libm.so.6
ELF     0x7fe56000-7ff4c000     Deferred        libwine_unicode.so.1
ELF     0x7ff4f000-7ff64000     Deferred        libnsl.so.1
ELF     0x7ff66000-7ff68000     Deferred        libnvidia-tls.so.1
ELF     0x7ff68000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7db0000-b7db5000     Deferred        libxxf86dga.so.1
ELF     0xb7db6000-b7db9000     Deferred        libdl.so.2
ELF     0xb7db9000-b7ee8000     Deferred        libc.so.6
ELF     0xb7ee9000-b7efb000     Deferred        libpthread.so.0
ELF     0xb7efb000-b7f14000     Export          libwine.so.1
ELF     0xb7f14000-b7f17000     Deferred        libxau.so.6
ELF     0xb7f17000-b7f20000     Deferred        libnss_compat.so.2
ELF     0xb7f33000-b7f49000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==
WineDbg terminated on pid 0x8

```

---

### Post by dcstar on 2006-02-14
[QUOTE=harty83]Hello,

I installed wine from the repository and tried to run winecfg. I get a page fault, and the backtrace.  Nothing happens except that wine-preloader sucks my system resources.

Below is the backtrace I get.  Any ideas on how to get wine fixed? Or am I doing something wrong (which is VERY possible)?  Thanks!

[CODE]alan@hartyslaptop:~$ winecfg
wine: creating configuration directory '/home/alan/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
......[/QUOTE]
What do you get running "glxinfo"?

---

### Post by harty83 on 2006-02-15
I get

```
alan@hartyslaptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```

---

