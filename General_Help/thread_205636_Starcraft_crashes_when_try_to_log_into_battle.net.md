---
title: "Starcraft crashes when try to log into battle.net"
date: 2006-06-28
forum: General Help
---

### Post by glasyalabolis on 2006-06-28
HI, I have the latest wine (I think, if not its the one that apt-get installs) and I have the latest patch from blizard. When I click on OK after selecting U.S. East it goes to the "connecting.." screen then Starcraft crashes leaving my resolution at 640x480.
This is what wine outputs in the terminal,

 ```
wine .wine/drive_c/Program\ Files/Starcraft/starcraft.exe
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd57e70)->(0x10022,00000013)fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
wine: Unhandled page fault on write access to 0x7cfbc000 at address 0x7da704a4 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x7cfbc000 in 32-bit code (0x7da704a4).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7da704a4 ESP:7fb9ef0c EBP:7fb9efc0 EFLAGS:00210206(   - 00      - RIP1) EAX:c7c7c76f EBX:7da7009c ECX:00000000 EDX:00000013
 ESI:71cf1014 EDI:7cfbc000
Stack dump:
0x7fb9ef0c:  00000000 7cfbb000 7cfbb000 00000000
0x7fb9ef1c:  71cf0010 7d023ff2 7fd58e68 7fb9efb4
0x7fb9ef2c:  7fb9ef6c 7d021fb8 7fd58e68 00000000
0x7fb9ef3c:  00000001 7f1261d8 7c038f38 7f1c9760
0x7fb9ef4c:  7fb9ef6c 7f1216f4 7c039478 7c0461f0
0x7fb9ef5c:  00000084 7fb9f0dc 00000000 15047b88
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7da704a4 (0x7da704a4)
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\StarCraft113f\Retail\Storm.pdb'
  2 0x15007d08 in storm (+0x7d08) (0x15007d08)
  3 0x00000000 (0x00000000)
0x7da704a4: movl        %eax,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (101 modules)
PE      0x00400000-006d5000     Deferred        starcraft
PE      0x02000000-02011000     Deferred        local
PE      0x10000000-1001a000     Deferred        smackw32
PE      0x15000000-15054000     Export          storm
PE      0x19000000-19083000     Deferred        battle.snp
ELF     0x72b05000-72b30000     Deferred        ws2_32<elf>
  \-PE  0x72b10000-72b30000     \               ws2_32
ELF     0x73606000-73620000     Deferred        wsock32<elf>
  \-PE  0x73610000-73620000     \               wsock32
ELF     0x73bd0000-73bf6000     Deferred        msacm32<elf>
  \-PE  0x73be0000-73bf6000     \               msacm32
ELF     0x73bf6000-73c0e000     Deferred        msacm<elf>
  \-PE  0x73c00000-73c0e000     \               msacm
ELF     0x73c0e000-73cc3000     Deferred        libasound.so.2
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7bf06000-7bf8e000     Deferred        winmm<elf>
  \-PE  0x7bf10000-7bf8e000     \               winmm
ELF     0x7bf8e000-7bfe0000     Deferred        dsound<elf>
  \-PE  0x7bfa0000-7bfe0000     \               dsound
ELF     0x7c337000-7c360000     Deferred        winealsa<elf>
  \-PE  0x7c340000-7c360000     \               winealsa
ELF     0x7cfc5000-7d040000     Deferred        ddraw<elf>
  \-PE  0x7cfe0000-7d040000     \               ddraw
ELF     0x7db7a000-7dbc6000     Deferred        libgcrypt.so.11
ELF     0x7dbc6000-7dbd6000     Deferred        libtasn1.so.2
ELF     0x7dbd6000-7dc03000     Deferred        libcrypt.so.1
ELF     0x7dc05000-7dc1a000     Deferred        midimap<elf>
  \-PE  0x7dc10000-7dc1a000     \               midimap
ELF     0x7dc1a000-7dc83000     Deferred        libgnutls.so.12
ELF     0x7dc83000-7dcb0000     Deferred        libcups.so.2
ELF     0x7dd0b000-7dd0f000     Deferred        libgpg-error.so.0
ELF     0x7dd91000-7ddc2000     Deferred        uxtheme<elf>
  \-PE  0x7dda0000-7ddc2000     \               uxtheme
ELF     0x7dde3000-7ddec000     Deferred        libxcursor.so.1
ELF     0x7ddec000-7ddf4000     Deferred        libxrender.so.1
ELF     0x7e674000-7e67c000     Deferred        librt.so.1
ELF     0x7e67e000-7e682000     Deferred        libxfixes.so.3
ELF     0x7e74d000-7f048000     Deferred        fglrx_dri.so
ELF     0x7f048000-7f0e8000     Deferred        libgl.so.1
ELF     0x7f0e8000-7f1ce000     Deferred        libx11.so.6
ELF     0x7f1ce000-7f1db000     Deferred        libxext.so.6
ELF     0x7f1db000-7f1e0000     Deferred        libxxf86vm.so.1
ELF     0x7f1e0000-7f1f8000     Deferred        libice.so.6
ELF     0x7f1f8000-7f27b000     Deferred        winex11<elf>
  \-PE  0x7f210000-7f27b000     \               winex11
ELF     0x7f27b000-7f29a000     Deferred        libexpat.so.1
ELF     0x7f29a000-7f2c8000     Deferred        libfontconfig.so.1
ELF     0x7f2c8000-7f2dc000     Deferred        libz.so.1
ELF     0x7f2dc000-7f345000     Deferred        libfreetype.so.6
ELF     0x7f345000-7f361000     Deferred        imm32<elf>
  \-PE  0x7f350000-7f361000     \               imm32
ELF     0x7f361000-7f37a000     Deferred        version<elf>
  \-PE  0x7f370000-7f37a000     \               version
ELF     0x7f37a000-7f3a6000     Deferred        winspool<elf>
  \-PE  0x7f380000-7f3a6000     \               winspool
ELF     0x7f3a6000-7f466000     Deferred        comctl32<elf>
  \-PE  0x7f3b0000-7f466000     \               comctl32
ELF     0x7f466000-7f485000     Deferred        iphlpapi<elf>
  \-PE  0x7f470000-7f485000     \               iphlpapi
ELF     0x7f485000-7f4ce000     Deferred        rpcrt4<elf>
  \-PE  0x7f4a0000-7f4ce000     \               rpcrt4
ELF     0x7f5a3000-7f654000     Deferred        gdi32<elf>
  \-PE  0x7f5c0000-7f654000     \               gdi32
ELF     0x7f654000-7f780000     Deferred        user32<elf>
  \-PE  0x7f670000-7f780000     \               user32
ELF     0x7f780000-7f811000     Deferred        ole32<elf>
  \-PE  0x7f7a0000-7f811000     \               ole32
ELF     0x7f811000-7f86c000     Deferred        shlwapi<elf>
  \-PE  0x7f820000-7f86c000     \               shlwapi
ELF     0x7f86c000-7f938000     Deferred        shell32<elf>
  \-PE  0x7f880000-7f938000     \               shell32
ELF     0x7f938000-7f9d5000     Deferred        comdlg32<elf>
  \-PE  0x7f950000-7f9d5000     \               comdlg32
ELF     0x7f9d5000-7fa15000     Deferred        advapi32<elf>
  \-PE  0x7f9e0000-7fa15000     \               advapi32
ELF     0x7fa15000-7fa76000     Deferred        msvcrt<elf>
  \-PE  0x7fa20000-7fa76000     \               msvcrt
ELF     0x7fa76000-7fa90000     Deferred        crtdll<elf>
  \-PE  0x7fa80000-7fa90000     \               crtdll
ELF     0x7fba3000-7fba8000     Deferred        libxxf86dga.so.1
ELF     0x7fba8000-7fbb0000     Deferred        libsm.so.6
ELF     0x7fbb1000-7fbbb000     Deferred        libgcc_s.so.1
ELF     0x7fbee000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe02000-7fe0c000     Deferred        libnss_files.so.2
ELF     0x7fe0c000-7fe15000     Deferred        libnss_nis.so.2
ELF     0x7fe15000-7fe2a000     Deferred        libnsl.so.1
ELF     0x7fe2a000-7fe33000     Deferred        libnss_compat.so.2
ELF     0x7fe33000-7fe36000     Deferred        libxrandr.so.2
ELF     0x7fe36000-7fe4a000     Deferred        lz32<elf>
  \-PE  0x7fe40000-7fe4a000     \               lz32
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e10000-b7e13000     Deferred        libdl.so.2
ELF     0xb7e13000-b7f42000     Deferred        libc.so.6
ELF     0xb7f42000-b7f54000     Deferred        libpthread.so.0
ELF     0xb7f55000-b7f58000     Deferred        libxau.so.6
ELF     0xb7f6c000-b7f86000     Deferred        libwine.so.1
ELF     0xb7f89000-b7f9f000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\.wine\drive_c\Program Files\Starcraft\starcraft.exe
        0000000e    2
        0000000d    0
        0000000c   15
        0000000b    0
        0000000a    1
        00000009    0 <==

```

any help would be appreciated, thx.

---

### Post by headchange on 2006-10-21
i had the same problem , its because the ms fonts arent installed from my understanding 
 sudo apt-get install msttcorefonts
  
run that and it should work, it worked for me, now only if i could get it to connect :/

---

### Post by CatKiller on 2006-10-21
And if you find that you're at the wrong resolution after a crash, press **Alt-F2** and type in **gnome-display-properties** to change the resolution back. There are keyboard combos to cycle through the available resolutions, but I can't remember what they are at the moment.

EDIT: The keyboard shortcuts are **Ctrl**-**Alt**-**+** and **Ctrl**-**Alt**-**-** on the keypad.

---

