---
title: "Wine program closes....need any input"
date: 2006-04-03
forum: General Help
---

### Post by KansasJoe on 2006-04-03
I'm trying to run a certain trading program with wine and i've got the entire thing to work with the help of winetools except for when i try to get the graph the program closes and this is what the terminal lists...any ideas because this is one of the main reasons why i'm still dual booting

joe@wallace:~$ wine "/home/joe/.wine/c/Program Files/fxsgts/fxtraderum.exe"
joe@wallace:~$ wine: Unhandled page fault on read access to 0x00000000 at addres s 0x79c94064 (thread 000d), starting debugger...
WineDbg starting on pid 0xc
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7 9c94064).
fixme:dbghelp:sffip_cb NIY on 'D:\Dev\Cfx40\FinancialX\CfxFeRelease\Cfx4Fe.pdb'
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:79c94064 ESP:7fb8dfe0 EBP:00000000 EFLAGS:00210202(   - 00      - -RI1)
 EAX:79b55770 EBX:7b9d75e8 ECX:00000000 EDX:7a7c3664
 ESI:79b55758 EDI:79b55794
Stack dump:
0x7fb8dfe0:  00000000 79b55770 79b55758 00000000
0x7fb8dff0:  00000000 7d3510d8 00000009 0000001a
0x7fb8e000:  7d352a60 7d49a808 ffff7345 79a4733a
0x7fb8e010:  7b9d75e8 7b9d76b0 7fb8e58c 79cd8608
0x7fb8e020:  79cea318 ffffffff 00000000 79cd58bd
0x7fb8e030:  00000008 79cd537c 00000008 00000001
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x79c94064 in cfx4fe (+0x24064) (0x79c94064)
0x79c94064: movl        0x0(%ecx),%edx
Modules:
Module  Address                 Debug info      Name (95 modules)
PE      0x00400000-00930000     Deferred        fxtrader
PE      0x10000000-10023000     Deferred        ctdr~b4o
PE      0x11000000-1100e000     Deferred        trdenglish
PE      0x20000000-20044000     Deferred        richtx32
PE      0x212f0000-21323000     Deferred        tabctl32
PE      0x27580000-27686000     Deferred        mscomctl
PE      0x277b0000-2784f000     Deferred        mscomct2
PE      0x48000000-4806c000     Deferred        riched20
PE      0x5f300000-5f329000     Deferred        olepro32
PE      0x5f400000-5f4f2000     Deferred        mfc42
PE      0x65340000-653d2000     Deferred        oleaut32
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x66000000-66153000     Deferred        msvbvm60
PE      0x70100000-70153000     Deferred        rpcrt4
PE      0x70bd0000-70c35000     Deferred        shlwapi
PE      0x78000000-78044000     Deferred        msvcrt
PE      0x79c70000-79d1c000     Export          cfx4fe
PE      0x7a210000-7a254000     Deferred        fxmathlib
ELF     0x7a329000-7a347000     Deferred        iphlpapi<elf>
  \-PE  0x7a330000-7a347000     \               iphlpapi
ELF     0x7a347000-7a370000     Deferred        ws2_32<elf>
  \-PE  0x7a350000-7a370000     \               ws2_32
PE      0x7a370000-7a396000     Deferred        absolutehttp
ELF     0x7a8c3000-7a8d7000     Deferred        riched32<elf>
  \-PE  0x7a8d0000-7a8d7000     \               riched32
ELF     0x7a8d7000-7a8f0000     Deferred        oledlg<elf>
  \-PE  0x7a8e0000-7a8f0000     \               oledlg
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7c220000-7c246000     Deferred        asycfilt
PE      0x7c250000-7c2bf000     Deferred        mshflxgd
ELF     0x7c2f3000-7c307000     Deferred        lz32<elf>
  \-PE  0x7c300000-7c307000     \               lz32
ELF     0x7c307000-7c320000     Deferred        version<elf>
  \-PE  0x7c310000-7c320000     \               version
PE      0x7c320000-7c344000     Deferred        sfxbar
PE      0x7c350000-7c3e5000     Deferred        cfx4032
ELF     0x7d1b7000-7d203000     Deferred        libgcrypt.so.11
ELF     0x7d203000-7d230000     Deferred        libcrypt.so.1
ELF     0x7d230000-7d299000     Deferred        libgnutls.so.12
ELF     0x7d299000-7d2c0000     Deferred        libcups.so.2
ELF     0x7d31f000-7d350000     Deferred        uxtheme<elf>
  \-PE  0x7d330000-7d350000     \               uxtheme
ELF     0x7d57d000-7d5a7000     Deferred        winspool<elf>
  \-PE  0x7d590000-7d5a7000     \               winspool
ELF     0x7d5a7000-7d65c000     Deferred        comctl32<elf>
  \-PE  0x7d5b0000-7d65c000     \               comctl32
ELF     0x7d65c000-7d728000     Deferred        shell32<elf>
  \-PE  0x7d670000-7d728000     \               shell32
ELF     0x7d728000-7d7c0000     Deferred        comdlg32<elf>
  \-PE  0x7d740000-7d7c0000     \               comdlg32
ELF     0x7de40000-7de50000     Deferred        libtasn1.so.2
ELF     0x7e374000-7e378000     Deferred        libgpg-error.so.0
ELF     0x7e49b000-7e4a4000     Deferred        libxcursor.so.1
ELF     0x7e4a4000-7e4c0000     Deferred        imm32<elf>
  \-PE  0x7e4b0000-7e4c0000     \               imm32
ELF     0x7e4c0000-7ec7e000     Deferred        libglcore.so.1
ELF     0x7ec7e000-7ed01000     Deferred        libgl.so.1
ELF     0x7ed01000-7ede7000     Deferred        libx11.so.6
ELF     0x7ede7000-7edff000     Deferred        libice.so.6
ELF     0x7edff000-7ee7e000     Deferred        winex11<elf>
  \-PE  0x7ee10000-7ee7e000     \               winex11
ELF     0x7ee7e000-7ee9d000     Deferred        libexpat.so.1
ELF     0x7ee9d000-7eecb000     Deferred        libfontconfig.so.1
ELF     0x7eecb000-7eedf000     Deferred        libz.so.1
ELF     0x7eedf000-7ef48000     Deferred        libfreetype.so.6
ELF     0x7ef48000-7ef86000     Deferred        advapi32<elf>
  \-PE  0x7ef50000-7ef86000     \               advapi32
ELF     0x7f05b000-7f95e000     Deferred        gdi32<elf>
  \-PE  0x7f0a0000-7f95e000     \               gdi32
ELF     0x7f95e000-7fa80000     Deferred        user32<elf>
  \-PE  0x7f980000-7fa80000     \               user32
ELF     0x7fb96000-7fb9e000     Deferred        libxrender.so.1
ELF     0x7fbd1000-7fcd0000     Deferred        kernel32<elf>
  \-PE  0x7fbf0000-7fcd0000     \               kernel32
ELF     0x7fcd3000-7fce0000     Deferred        libxext.so.6
ELF     0x7fce2000-7fce6000     Deferred        libxfixes.so.3
ELF     0x7fce6000-7fceb000     Deferred        libxxf86vm.so.1
ELF     0x7fceb000-7fcf0000     Deferred        libxxf86dga.so.1
ELF     0x7fe04000-7fe0e000     Deferred        libgcc_s.so.1
ELF     0x7fe0e000-7fe18000     Deferred        libnss_files.so.2
ELF     0x7fe18000-7fe21000     Deferred        libnss_nis.so.2
ELF     0x7fe21000-7fe36000     Deferred        libnsl.so.1
ELF     0x7fe36000-7fe3f000     Deferred        libnss_compat.so.2
ELF     0x7fe40000-7fe42000     Deferred        libnvidia-tls.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4d000-7fe6f000     Deferred        libm.so.6
ELF     0x7fe6f000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e11000-b7e14000     Deferred        libdl.so.2
ELF     0xb7e14000-b7f43000     Deferred        libc.so.6
ELF     0xb7f43000-b7f55000     Deferred        libpthread.so.0
ELF     0xb7f56000-b7f59000     Deferred        libxau.so.6
ELF     0xb7f61000-b7f7b000     Deferred        libwine.so.1
ELF     0xb7f7e000-b7f94000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c (D) C:\Program Files\fxsgts\fxtrader.exe
        0000000d    0 <==
0000000a
        0000000b    0

---

