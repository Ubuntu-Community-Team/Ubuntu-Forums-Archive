---
title: "Trying to install IE6 with WINE"
date: 2006-03-14
forum: General Help
---

### Post by Pulse on 2006-03-14
When I try to run ie6setup.exe I get the following error.
```
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP002.TMP\\" 00000000
fixme:setupapi:SETUPX_CreateStandardLDDs LDID_SRCPATH: what exactly do we have to do here ?
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:vcpUICallbackProc16 (0xfa80, 0705, 0000, 00000000, 7fdee2cc) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xfa80, 070f, 0000, 00000000, 7fdee2cc) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xfa80, 0710, 0000, 00000000, 7fdee2cc) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xfa80, 070b, 0000, 00000000, 7fdee2cc) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xfa80, 070c, 0000, 00000000, 7fdee2cc) - semi-stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 000c), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1197 GS:0033
 EIP:00000000 ESP:7dccbcb4 EBP:7dccbd20 EFLAGS:00010202(   - 00      - -RI1)
 EAX:7dbb0000 EBX:7dbc4678 ECX:7dbc0e21 EDX:00000000
 ESI:00000007 EDI:7dbcc35c
Stack dump:
0x7dccbcb4:  7dbb7bae 7dbb0000 7dbc0e21 7dccbd0c
0x7dccbcc4:  00000001 7dbc0f90 7dccbcd4 00000001
0x7dccbcd4:  7dbc0d91 7fdef660 7dbc0da3 7fdef690
0x7dccbce4:  7dbc0db6 7fdef6c0 7dbc0dc8 7fdef6f0
0x7dccbcf4:  7dbc0ddd 7fdf01c0 7dbc0df0 7fdf01f0
0x7dccbd04:  7dbc0e04 7fdf0220 00000007 7dccbcd4
0232: sel=1197 base=7dcce000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x00000000 (0x00000000)
  2 0x7dbb827b DllRegisterServer+0x4bb in urlmon (0x7dbb827b)
fixme:dbghelp:sffip_cb NIY on 'advpack.pdb'
  3 0x715f4c3b in advpack (+0x4c3b) (0x715f4c3b)
  4 0x715f880b in advpack (+0x880b) (0x715f880b)
  5 0x715f98a3 in advpack (+0x98a3) (0x715f98a3)
  6 0x715f9e9b in advpack (+0x9e9b) (0x715f9e9b)
fixme:dbghelp:sffip_cb NIY on 'ie6wzdex.pdb'
  7 0x010167a3 in ie6wzd (+0x167a3) (0x010167a3)
  8 0x0100b966 in ie6wzd (+0xb966) (0x0100b966)
  9 0x7fcd8061 in kernel32 (+0x68061) (0x7fcd8061)
  10 0x7bedb022 in ntdll (+0x3b022) (0x7bedb022)
  11 0xb7f77361 start_thread+0x81 in libpthread.so.0 (0xb7f77361)
  12 0xb7f0cbde __clone+0x5e in libc.so.6 (0xb7f0cbde)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (78 modules)
PE      0x01000000-01034000     Export          ie6wzd
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x70100000-70153000     Deferred        rpcrt4
PE      0x715f0000-71617000     Export          advpack
PE      0x716a0000-716a7000     Deferred        w95inf32
ELF     0x73975000-73977000     Deferred        xlcutf8load.so.2
ELF     0x7be86000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7db36000-7db79000     Deferred        wininet<elf>
  \-PE  0x7db40000-7db79000     \               wininet
ELF     0x7db79000-7db99000     Deferred        cabinet<elf>
  \-PE  0x7db80000-7db99000     \               cabinet
ELF     0x7db99000-7dbcd000     Export          urlmon<elf>
  \-PE  0x7dbb0000-7dbcd000     \               urlmon
ELF     0x7de3d000-7de90000     Deferred        setupapi<elf>
  \-PE  0x7de50000-7de90000     \               setupapi
ELF     0x7e037000-7e07c000     Deferred        riched20<elf>
  \-PE  0x7e050000-7e07c000     \               riched20
ELF     0x7e07c000-7e090000     Deferred        riched32<elf>
  \-PE  0x7e080000-7e090000     \               riched32
ELF     0x7e133000-7e18b000     Deferred        shlwapi<elf>
  \-PE  0x7e150000-7e18b000     \               shlwapi
ELF     0x7e18b000-7e250000     Deferred        shell32<elf>
  \-PE  0x7e1a0000-7e250000     \               shell32
ELF     0x7e256000-7e287000     Deferred        uxtheme<elf>
  \-PE  0x7e260000-7e287000     \               uxtheme
ELF     0x7e2a5000-7e2ae000     Deferred        libxcursor.so.1
ELF     0x7e2ae000-7e2ca000     Deferred        imm32<elf>
  \-PE  0x7e2c0000-7e2ca000     \               imm32
ELF     0x7e2ca000-7e2e6000     Deferred        ximcp.so.2
ELF     0x7e2e6000-7e2ee000     Deferred        librt.so.1
ELF     0x7e2f2000-7e2fa000     Deferred        libxrender.so.1
ELF     0x7e3b4000-7eaf7000     Deferred        fglrx_dri.so
ELF     0x7eaf7000-7eb96000     Deferred        libgl.so.1
ELF     0x7eb96000-7ec56000     Deferred        libx11.so.6
ELF     0x7ec56000-7ec6f000     Deferred        libice.so.6
ELF     0x7ec6f000-7ecee000     Deferred        winex11<elf>
  \-PE  0x7ec80000-7ecee000     \               winex11
ELF     0x7ecee000-7ed0d000     Deferred        libexpat.so.1
ELF     0x7ed0d000-7ed3b000     Deferred        libfontconfig.so.1
ELF     0x7ed3b000-7ed4f000     Deferred        libz.so.1
ELF     0x7ed4f000-7edb9000     Deferred        libfreetype.so.6
ELF     0x7edb9000-7edcd000     Deferred        lz32<elf>
  \-PE  0x7edc0000-7edcd000     \               lz32
ELF     0x7edcd000-7ede6000     Deferred        version<elf>
  \-PE  0x7edd0000-7ede6000     \               version
ELF     0x7ede6000-7ee9a000     Deferred        comctl32<elf>
  \-PE  0x7edf0000-7ee9a000     \               comctl32
ELF     0x7ee9a000-7eeb8000     Deferred        mpr<elf>
  \-PE  0x7eea0000-7eeb8000     \               mpr
ELF     0x7eeb8000-7efda000     Deferred        user32<elf>
  \-PE  0x7eed0000-7efda000     \               user32
ELF     0x7f0c0000-7f9c3000     Deferred        gdi32<elf>
  \-PE  0x7f100000-7f9c3000     \               gdi32
ELF     0x7f9c3000-7fa00000     Deferred        advapi32<elf>
  \-PE  0x7f9d0000-7fa00000     \               advapi32
ELF     0x7fb02000-7fb06000     Deferred        libxfixes.so.3
ELF     0x7fb06000-7fb0a000     Deferred        libxdmcp.so.6
ELF     0x7fc52000-7fd50000     Export          kernel32<elf>
  \-PE  0x7fc70000-7fd50000     \               kernel32
ELF     0x7fd53000-7fd60000     Deferred        libxext.so.6
ELF     0x7fd65000-7fd70000     Deferred        libgcc_s.so.1
ELF     0x7fe82000-7fe87000     Deferred        libxxf86vm.so.1
ELF     0x7fe87000-7fe91000     Deferred        libnss_files.so.2
ELF     0x7fe91000-7fe9a000     Deferred        libnss_nis.so.2
ELF     0x7fe9a000-7feaf000     Deferred        libnsl.so.1
ELF     0x7feaf000-7feb8000     Deferred        libnss_compat.so.2
ELF     0x7feb8000-7febd000     Deferred        libxxf86dga.so.1
ELF     0x7febd000-7fec4000     Deferred        libsm.so.6
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e30000-b7e33000     Deferred        libxau.so.6
ELF     0xb7e41000-b7e44000     Deferred        libdl.so.2
ELF     0xb7e44000-b7f72000     Export          libc.so.6
ELF     0xb7f72000-b7f84000     Export          libpthread.so.0
ELF     0xb7f90000-b7faa000     Deferred        libwine.so.1
ELF     0xb7fad000-b7fc3000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\windows\temp\IXP002.TMP\ie6wzd.exe
        0000000c    0 <==
        0000000b    0
00000008
        00000009    0
```

Does anybody know what might be causing the problem?

I'm using wine 0.9.9-winehq-2 from the WHQ repository and I've tried configuring with winecfg, winetools and downloading somebody else's config and none of them made any difference.

I've also tried ies4linux, which installs correctly and allows me to run IE, but programs that require IE don't recognize it as installed, making it useless to me (I don't want to use IE, just some programs that need it).

---

### Post by az on 2006-03-14
This seems to work:
[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

### Post by aysiu on 2006-03-14
Try Googling *ies4linux*

---

### Post by Pulse on 2006-03-14
[QUOTE=azz]This seems to work:
[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)[/QUOTE]
The IE6 installer crashes right after agreeing to the EULA, just like it does with every other method.

---

### Post by az on 2006-03-14
I wonder if this is Microsoft realising that wine exists...

---

### Post by Pulse on 2006-03-14
[QUOTE=azz]I wonder if this is Microsoft realising that wine exists...[/QUOTE]
If Microsoft had the power to retroactively change every IE6 installer on the internet at will, world domination would be as easy as HURK-

NOTHING TO SEE HERE.  MOVE ALONG, CITIZEN

---

### Post by chaoschannel on 2006-03-14
Had the same problem. From what I can find Wine 0.9.9 has a problem with IE6
[http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

I had to revert to 0.9.8 to get it to install.
[http://sourceforge.net/project/showfiles.php?group_id=6241](http://sourceforge.net/project/showfiles.php?group_id=6241)

---

### Post by aysiu on 2006-03-14
Please give IEs4Linux a shot.

---

### Post by Pulse on 2006-03-14
[QUOTE=chaoschannel]Had the same problem. From what I can find Wine 0.9.9 has a problem with IE6
[http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

I had to revert to 0.9.8 to get it to install.
[http://sourceforge.net/project/showfiles.php?group_id=6241](http://sourceforge.net/project/showfiles.php?group_id=6241)[/QUOTE]
Reverting to 0.9.8 worked like a charm, thanks!

I've run into another roadblock, however.  The Windows Installer installer (InstMsiA.exe) crashes with this error:
```
wine: could not load L"C:\\windows\\Installer\\InstMsi4\\msiexec.exe" as Win32 binary
```

At first glance it looked to me like the file was corrupted, so I got Winetools to redownload it, and then downloading it from a different source, all with the same result.  Not quite as major as IE not working, but still annoying.

[quote=aysiu]Please give IEs4Linux a shot.[/quote]
[quote=me, in the original post]
I've also tried ies4linux, which installs correctly and allows me to run IE, but programs that require IE don't recognize it as installed, making it useless to me (I don't want to use IE, just some programs that need it).[/quote]

---

### Post by aysiu on 2006-03-14
Sorry. I'm stupid. I missed that.

---

### Post by Pulse on 2006-03-14
I re-updated to wine 0.9.9 to see if it would work with Windows Installer.  It doesn't, but at least it spits out a different error message: ```
fixme:msiexec:main /regserver not implemented yet, ignoring
fixme:msiexec:main /unregserver not implemented yet, ignoring
```

---

### Post by az on 2006-03-14
[QUOTE=Pulse]If Microsoft had the power to retroactively change every IE6 installer on the internet at will, world domination would be as easy as HURK-

NOTHING TO SEE HERE.  MOVE ALONG, CITIZEN[/QUOTE]

Well, AFAIK, even if you get an earlier version of the installer, it will fetch the current version from it's repository.

---

