---
title: "winecfg problem"
date: 2006-03-12
forum: General Help
---

### Post by ajgreeny on 2006-03-12
Whenever I try to run winecfg in konsole I get this error message:-

wine: creating configuration directory '/home/andrew/.wine'...
wine: Unhandled page fault on read access to 0x1008002f at address 0x7bebc9ae (thread 0009), starting debugger...

Then when I run the debugger the following long thread of info which means nothing to me.

WineDbg starting on pid 0x8
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image C:\windows\rundll32.exe
Unhandled exception: page fault on read access to 0x1008002f in 32-bit code (0x7bebc9ae).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:ffff GS:0033
 EIP:7bebc9ae ESP:7fafd5c0 EBP:7fafd5d8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7bef34fc ECX:00000002 EDX:ffffffff
 ESI:1007ffff EDI:7fe297f8
Stack dump:
0x7fafd5c0:  7fe29308 00000000 00000000 7bef34fc
0x7fafd5d0:  00000000 7befb8c4 7fafd608 7bebf5e7
0x7fafd5e0:  7fafd5fc 7fd6cb00 00000090 7fd70326
0x7fafd5f0:  00000000 7fafd5a0 7fe297f8 7fd125fc
0x7fafd600:  7fe29308 00000008 7fafd858 7fcd0ce0
0x7fafd610:  7fe29308 00000008 7fafd874 7fafd848
Backtrace:
=>1 0x7bebc9ae in ntdll (+0x1c9ae) (0x7bebc9ae)
  2 0x7bebf5e7 LdrLoadDll+0x87 in ntdll (0x7bebf5e7)
  3 0x7fcd0ce0 in kernel32 (+0x40ce0) (0x7fcd0ce0)
  4 0x7fcd0e6f LoadLibraryExW+0x4f in kernel32 (0x7fcd0e6f)
  5 0x7e1d88d8 in setupapi (+0x188d8) (0x7e1d88d8)
  6 0x7e1d78f8 in setupapi (+0x178f8) (0x7e1d78f8)
  7 0x7e1d7b5d SetupInstallFromInfSectionW+0x11d in setupapi (0x7e1d7b5d)
  8 0x7e1d856e InstallHinfSectionW+0x1de in setupapi (0x7e1d856e)
  9 0x7fb1e5c4 main+0x334 in rundll32 (0x7fb1e5c4)
  10 0x7fb1eb7e in rundll32 (+0xeb7e) (0x7fb1eb7e)
  11 0x7fcddc9f in kernel32 (+0x4dc9f) (0x7fcddc9f)
  12 0xb7ee6107 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7ee6107)
0x7bebc9ae: movl        0x30(%esi),%eax
Modules:
Module  Address                 Debug info      Name (74 modules)
ELF     0x7396f000-73977000     Deferred        libxrender.so.1
ELF     0x7be86000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7dd51000-7dd66000     Deferred        midimap<elf>
  \-PE  0x7dd60000-7dd66000     \               midimap
ELF     0x7dd66000-7dd7d000     Deferred        msacm<elf>
  \-PE  0x7dd70000-7dd7d000     \               msacm
ELF     0x7dd7d000-7ddc0000     Deferred        wineoss<elf>
  \-PE  0x7dd90000-7ddc0000     \               wineoss
ELF     0x7de1f000-7deab000     Deferred        ole32<elf>
  \-PE  0x7de30000-7deab000     \               ole32
ELF     0x7deab000-7df25000     Deferred        ddraw<elf>
  \-PE  0x7ded0000-7df25000     \               ddraw
ELF     0x7df25000-7dfac000     Deferred        winmm<elf>
  \-PE  0x7df30000-7dfac000     \               winmm
ELF     0x7dfac000-7dfd0000     Deferred        msacm32<elf>
  \-PE  0x7dfb0000-7dfd0000     \               msacm32
ELF     0x7e121000-7e13f000     Deferred        iphlpapi<elf>
  \-PE  0x7e130000-7e13f000     \               iphlpapi
ELF     0x7e13f000-7e187000     Deferred        rpcrt4<elf>
  \-PE  0x7e150000-7e187000     \               rpcrt4
ELF     0x7e187000-7e19b000     Deferred        lz32<elf>
  \-PE  0x7e190000-7e19b000     \               lz32
ELF     0x7e19b000-7e1b4000     Deferred        version<elf>
  \-PE  0x7e1a0000-7e1b4000     \               version
ELF     0x7e1b4000-7e207000     Export          setupapi<elf>
  \-PE  0x7e1c0000-7e207000     \               setupapi
ELF     0x7e23f000-7e25b000     Deferred        imm32<elf>
  \-PE  0x7e250000-7e25b000     \               imm32
ELF     0x7e25b000-7e277000     Deferred        ximcp.so.2
ELF     0x7e277000-7e27f000     Deferred        librt.so.1
ELF     0x7e280000-7e284000     Deferred        libxfixes.so.3
ELF     0x7e284000-7e28d000     Deferred        libxcursor.so.1
ELF     0x7e28d000-7e28f000     Deferred        xlcutf8load.so.2
ELF     0x7e349000-7ebd9000     Deferred        atiogl_a_dri.so
ELF     0x7ebd9000-7ec78000     Deferred        libgl.so.1
ELF     0x7ec78000-7ed38000     Deferred        libx11.so.6
ELF     0x7ed38000-7ed45000     Deferred        libxext.so.6
ELF     0x7ed45000-7ed5e000     Deferred        libice.so.6
ELF     0x7ed5e000-7eddd000     Deferred        winex11<elf>
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
PE      0x7fb0c000-7fb20000     Export          rundll32
PE      0x7fb10000-7fb20000     Export          rundll32
ELF     0x7fb21000-7fb25000     Deferred        libxdmcp.so.6
ELF     0x7fb25000-7fb2a000     Deferred        libxxf86vm.so.1
ELF     0x7fc72000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe80000-7fe83000     Deferred        libxrandr.so.2
ELF     0x7fe83000-7fe8d000     Deferred        libnss_files.so.2
ELF     0x7fe8d000-7fe96000     Deferred        libnss_nis.so.2
ELF     0x7fe96000-7feab000     Deferred        libnsl.so.1
ELF     0x7feab000-7feb4000     Deferred        libnss_compat.so.2
ELF     0x7feb5000-7feb8000     Deferred        libxau.so.6
ELF     0x7feb8000-7febd000     Deferred        libxxf86dga.so.1
ELF     0x7febd000-7fec4000     Deferred        libsm.so.6
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7d8e000-b7d91000     Deferred        libdl.so.2
ELF     0xb7d91000-b7ebf000     Deferred        libc.so.6
ELF     0xb7ebf000-b7ed1000     Deferred        libpthread.so.0
ELF     0xb7ee1000-b7efb000     Export          libwine.so.1
ELF     0xb7efe000-b7f14000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==
wine: '/home/andrew/.wine' created successfully.
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:wave:ARTS_WaveInit arts_init() crashed
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

I have tried to run many windows programs such as picasa2, mailwasher free, and several other simple utilities in the resulting setup, usually using the defaults presented to me but so far have not managed to get anything to run.

Anyone got any clues what is going on?

---

### Post by knalle on 2006-03-12
[QUOTE=ajgreeny]ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:wave:ARTS_WaveInit arts_init() crashed
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
[/QUOTE]

lookes like libjack.so is missing try

```
sudo apt-get install libjack0
```

---

### Post by ajgreeny on 2006-03-13
Thanks Knalle, but I do have libjack0.80.0-0 installed already.  Any other clues?  What about the libjack0.80.0-dev package, I thought this was only for developing other jack applications.

---

