---
title: "wine picasa problems"
date: 2006-04-23
forum: General Help
---

### Post by element on 2006-04-23
I installed wine and am trying to install picasa and get the following.  Can anyone help me with this one?
Thanks!

```
# wine picasa2-current.exe
wine: creating configuration directory '/root/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ec1d13f (t hread 0009), starting debugger...

```

---

### Post by apolyak on 2006-04-23
It looks you are trying to install Picasa as root, but root has no access to your display 0.0. You should do that as user. Also make sure you have the latest version of wine, follow instruction [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

After wine is install run winecfg and check available drives (run auto detect and remove all out of your home directory), then install Picasa.

Good luck

---

### Post by element on 2006-04-23
Thanks! That worked.  I got the installer up and installed it, but came across this. {see below}  Now that it is installed how do I launch Picasa?

```
fixme:win:SetWindowTextA setting text "Picasa2 Setup" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Picasa2 Setup" of other process window (nil) should not use SendMessage
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_AUTOURLDETECT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
fixme:shell:BrsFolder_OnCreate flags 40 not implemented
fixme:shell:BrsFolderDlgProc Set selection "c:\\Program Files\\Picasa2"
err:ntdll:RtlpWaitForCriticalSection section 0x40b468 "?" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
kde-config: WARNING: KLocale: trying to look up "" in catalog. Fix the program
err:menubuilder:extract_icon32 LoadLibraryExW (L"Z:\\mnt\\storage\\Picasa2\\Uninstall.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink

```

---

### Post by element on 2006-04-23
So my guess is I have to run "wine Picasa2.exe" from the location I installed it to, but I get this when running it...

```

cory@ubuntu:/mnt/storage/Picasa2$ wine Picasa2.exe
wine: creating configuration directory '/home/cory/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
err:advpack:create_tmp_ini_file Unable to create temp ini file
err:advpack:create_tmp_ini_file Unable to create temp ini file
wine: Unhandled exception (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e6e713f).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7e6e713f ESP:7fb1fb6c EBP:7fb1fba8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c0cb5e8 ECX:b7efe800 EDX:7c01a048
 ESI:7c01a048 EDI:7c01a048
Stack dump:
0x7fb1fb6c:  7c01a048 7e71c9a0 7c01a048 7e6e5ab6
0x7fb1fb7c:  7c01a048 7c01a048 7ed547d0 7c0cb600
0x7fb1fb8c:  7eca9883 7c01a048 7c0cb604 00000001
0x7fb1fb9c:  7edf6af0 7edfe74c 7fdeaef0 7fb1fbbc
0x7fb1fbac:  7edbec48 7c01a048 7edf6af0 80000004
0x7fb1fbbc:  7fb1fd0c 7edd6587 00000000 7ea675ac
0200: sel=1007 base=b7f3c000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x7e6e713f in libgl.so.1 (+0x3613f) (0x7fb1fba8)
  2 0x7edbec48 X11DRV_GDI_Finalize+0x28 in winex11.drv (0x7fb1fbbc)
  3 0x7edd6587 DllMain+0x36 in winex11.drv (0x7fb1fd0c)
  4 0x7ed9a06e in winex11.drv (+0xa06e) (0x7fb1fd3c)
  5 0x7bebf9e2 call_dll_entry_point+0x12 in ntdll (0x7fb1fd54)
  6 0x7bec075b in ntdll (+0x2075b) (0x7fb1fdec)
  7 0x7bec0a22 in ntdll (+0x20a22) (0x7fb1fe14)
  8 0x7fd07aed ExitProcess+0x1c in kernel32 (0x7fb1fea0)
  9 0x7fb3d1b5 in rundll32 (+0xd1b5) (0x7fb1ff20)
  10 0x7fd08e63 in kernel32 (+0x48e63) (0x7fb1fff4)
  11 0xb7f18c45 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x7e6e713f: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (90 modules)
ELF     0x7be87000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7dca0000-7dcfc000     Deferred        shlwapi<elf>
  \-PE  0x7dcc0000-7dcfc000     \               shlwapi
ELF     0x7dcfc000-7ddc2000     Deferred        shell32<elf>
  \-PE  0x7dd20000-7ddc2000     \               shell32
ELF     0x7ddc2000-7ddd9000     Deferred        advpack<elf>
  \-PE  0x7ddd0000-7ddd9000     \               advpack
ELF     0x7de08000-7dec7000     Deferred        comctl32<elf>
  \-PE  0x7de20000-7dec7000     \               comctl32
ELF     0x7dec7000-7deec000     Deferred        msvfw32<elf>
  \-PE  0x7ded0000-7deec000     \               msvfw32
ELF     0x7deec000-7df48000     Deferred        quartz<elf>
  \-PE  0x7df00000-7df48000     \               quartz
ELF     0x7df48000-7e6b1000     Deferred        libglcore.so.1
ELF     0x7e6b1000-7e730000     Export          libgl.so.1
ELF     0x7e842000-7e857000     Deferred        midimap<elf>
  \-PE  0x7e850000-7e857000     \               midimap
ELF     0x7e857000-7e870000     Deferred        msacm.drv<elf>
  \-PE  0x7e860000-7e870000     \               msacm.drv
ELF     0x7e870000-7e8b3000     Deferred        wineoss.drv<elf>
  \-PE  0x7e880000-7e8b3000     \               wineoss.drv
ELF     0x7e8b4000-7e902000     Deferred        dsound<elf>
  \-PE  0x7e8d0000-7e902000     \               dsound
ELF     0x7e902000-7e997000     Deferred        oleaut32<elf>
  \-PE  0x7e920000-7e997000     \               oleaut32
ELF     0x7e997000-7ea21000     Deferred        ole32<elf>
  \-PE  0x7e9b0000-7ea21000     \               ole32
ELF     0x7ea21000-7eaa1000     Deferred        winmm<elf>
  \-PE  0x7ea30000-7eaa1000     \               winmm
ELF     0x7eaa1000-7eac4000     Deferred        msacm32<elf>
  \-PE  0x7eab0000-7eac4000     \               msacm32
ELF     0x7eac9000-7eadd000     Deferred        avicap32<elf>
  \-PE  0x7ead0000-7eadd000     \               avicap32
ELF     0x7eadd000-7eb03000     Deferred        devenum<elf>
  \-PE  0x7eaf0000-7eb03000     \               devenum
ELF     0x7eb03000-7eb24000     Deferred        iphlpapi<elf>
  \-PE  0x7eb10000-7eb24000     \               iphlpapi
ELF     0x7eb24000-7eb6e000     Deferred        rpcrt4<elf>
  \-PE  0x7eb40000-7eb6e000     \               rpcrt4
ELF     0x7eb6e000-7eb82000     Deferred        lz32<elf>
  \-PE  0x7eb70000-7eb82000     \               lz32
ELF     0x7eb82000-7eb9d000     Deferred        version<elf>
  \-PE  0x7eb90000-7eb9d000     \               version
ELF     0x7eb9d000-7ebf8000     Deferred        setupapi<elf>
  \-PE  0x7ebb0000-7ebf8000     \               setupapi
ELF     0x7ec3c000-7ec45000     Deferred        libxcursor.so.1
ELF     0x7ec56000-7ec73000     Deferred        imm32<elf>
  \-PE  0x7ec60000-7ec73000     \               imm32
ELF     0x7ec73000-7ec8f000     Deferred        ximcp.so.2
ELF     0x7ec8f000-7ec97000     Deferred        libxrender.so.1
ELF     0x7ec97000-7ed57000     Deferred        libx11.so.6
ELF     0x7ed57000-7ed64000     Deferred        libxext.so.6
ELF     0x7ed64000-7ed7d000     Deferred        libice.so.6
ELF     0x7ed7d000-7edff000     Export          winex11.drv<elf>
  \-PE  0x7ed90000-7edff000     \               winex11.drv
ELF     0x7edff000-7ee1e000     Deferred        libexpat.so.1
ELF     0x7ee1e000-7ee4c000     Deferred        libfontconfig.so.1
ELF     0x7ee4c000-7ee60000     Deferred        libz.so.1
ELF     0x7ee60000-7eeca000     Deferred        libfreetype.so.6
ELF     0x7eeca000-7ef0b000     Deferred        advapi32<elf>
  \-PE  0x7eee0000-7ef0b000     \               advapi32
ELF     0x7eff1000-7f8f4000     Deferred        gdi32<elf>
  \-PE  0x7f040000-7f8f4000     \               gdi32
ELF     0x7f8f4000-7fa20000     Deferred        user32<elf>
  \-PE  0x7f920000-7fa20000     \               user32
ELF     0x7fb24000-7fb27000     Deferred        libxrandr.so.2
ELF     0x7fb27000-7fb2b000     Deferred        libxdmcp.so.6
ELF     0x7fb2b000-7fb40000     Export          rundll32<elf>
  \-PE  0x7fb30000-7fb40000     \               rundll32
ELF     0x7fb42000-7fb4d000     Deferred        libgcc_s.so.1
ELF     0x7fc95000-7fda0000     Export          kernel32<elf>
  \-PE  0x7fcc0000-7fda0000     \               kernel32
ELF     0x7feb0000-7feb7000     Deferred        libsm.so.6
ELF     0x7feb7000-7fecd000     Deferred        libnsl.so.1
ELF     0x7fecd000-7fed7000     Deferred        libnss_compat.so.2
ELF     0x7fee2000-7fee6000     Deferred        libxfixes.so.3
ELF     0x7fee6000-7fee8000     Deferred        xlcutf8load.so.2
ELF     0x7fee8000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7dc2000-b7dcd000     Deferred        libnss_files.so.2
ELF     0xb7dcf000-b7dd3000     Deferred        libdl.so.2
ELF     0xb7dd3000-b7f01000     Deferred        libc.so.6
ELF     0xb7f01000-b7f14000     Deferred        libpthread.so.0
ELF     0xb7f14000-b7f2d000     Export          libwine.so.1
ELF     0xb7f2d000-b7f2f000     Deferred        libnvidia-tls.so.1
ELF     0xb7f2f000-b7f32000     Deferred        libxau.so.6
ELF     0xb7f32000-b7f3c000     Deferred        libnss_nis.so.2
ELF     0xb7f40000-b7f56000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==
WineDbg terminated on pid 0x8
wine client error:9: write: Bad file descriptor
wine: '/home/cory/.wine' created successfully.
Xlib:  extension "GLX" missing on display ":0.0".
fixme:ole:CoResumeClassObjects stub
fixme:urlmon:CoInternetGetSession (0, 0x7fb1d4a4, 0): stub
fixme:urlmon:URLMON_DllGetClassObject {79eac9e2-baf9-11ce-8c82-00aa004ba90b}: no class found.
wine: Unhandled exception (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00609329).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:00609329 ESP:7fb1d494 EBP:7fb1fe94 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:7d772124 ECX:7d770b60 EDX:00000000
 ESI:007f547c EDI:7d772120
Stack dump:
0x7fb1d494:  00000000 007f547c 00000000 7d770b60
0x7fb1d4a4:  00000000 005dbef6 7beff980 00000000
0x7fb1d4b4:  00000000 7fd9001c 005156de 7beff980
0x7fb1d4c4:  00000000 7fd38ff4 33332d74 ffffffff
0x7fb1d4d4:  7c006470 b7f3aff4 b7f3b020 b7f133e8
0x7fb1d4e4:  b7eea514 b7f2bd5b 00000000 7c06f258
0200: sel=1007 base=b7f22000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x00609329 in picasa2 (+0x209329) (0x7fb1fe94)
  2 0x00620942 EntryPoint+0xe0 in picasa2 (0x7fb1ff20)
  3 0x7fcf8e63 in kernel32 (+0x48e63) (0x7fb1fff4)
  4 0xb7efec45 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x00609329: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (106 modules)
PE      0x00400000-0083e000     Export          picasa2
PE      0x10000000-10a43000     Deferred        picasai18n
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7d190000-7d1c7000     Deferred        ytitivo.yti
PE      0x7d400000-7d4fa000     Deferred        expwebsites.yti
PE      0x7d730000-7d759000     Deferred        cdvdr.yti
ELF     0x7d983000-7e0ec000     Deferred        libglcore.so.1
ELF     0x7e0ec000-7e16b000     Deferred        libgl.so.1
ELF     0x7e17c000-7e1de000     Deferred        libgnutls.so.11
ELF     0x7e303000-7e320000     Deferred        libcups.so.2
ELF     0x7e334000-7e380000     Deferred        libgcrypt.so.11
ELF     0x7e4d1000-7e4d5000     Deferred        libgpg-error.so.0
ELF     0x7e4d5000-7e4ea000     Deferred        midimap<elf>
  \-PE  0x7e4e0000-7e4ea000     \               midimap
ELF     0x7e4ea000-7e503000     Deferred        msacm.drv<elf>
  \-PE  0x7e4f0000-7e503000     \               msacm.drv
ELF     0x7e503000-7e546000     Deferred        wineoss.drv<elf>
  \-PE  0x7e510000-7e546000     \               wineoss.drv
ELF     0x7e58a000-7e58e000     Deferred        libxfixes.so.3
ELF     0x7e58e000-7e597000     Deferred        libxcursor.so.1
ELF     0x7e597000-7e5b3000     Deferred        ximcp.so.2
ELF     0x7e5b3000-7e5bb000     Deferred        libxrender.so.1
ELF     0x7e5bb000-7e63d000     Deferred        winex11.drv<elf>
  \-PE  0x7e5d0000-7e63d000     \               winex11.drv
ELF     0x7e63d000-7e65c000     Deferred        libexpat.so.1
ELF     0x7e65c000-7e68a000     Deferred        libfontconfig.so.1
ELF     0x7e68a000-7e69e000     Deferred        libz.so.1
ELF     0x7e69e000-7e708000     Deferred        libfreetype.so.6
ELF     0x7e708000-7e721000     Deferred        wintrust<elf>
  \-PE  0x7e710000-7e721000     \               wintrust
ELF     0x7e721000-7e7e1000     Deferred        libx11.so.6
ELF     0x7e7e1000-7e7fa000     Deferred        libice.so.6
ELF     0x7e7fa000-7e872000     Deferred        ddraw<elf>
  \-PE  0x7e820000-7e872000     \               ddraw
ELF     0x7e872000-7e88f000     Deferred        imm32<elf>
  \-PE  0x7e880000-7e88f000     \               imm32
ELF     0x7e88f000-7e924000     Deferred        oleaut32<elf>
  \-PE  0x7e8b0000-7e924000     \               oleaut32
ELF     0x7e924000-7e94f000     Deferred        winspool.drv<elf>
  \-PE  0x7e930000-7e94f000     \               winspool.drv
ELF     0x7e94f000-7e9df000     Deferred        comdlg32<elf>
  \-PE  0x7e960000-7e9df000     \               comdlg32
ELF     0x7e9df000-7ea08000     Deferred        cabinet<elf>
  \-PE  0x7e9f0000-7ea08000     \               cabinet
ELF     0x7ea08000-7ea30000     Deferred        urlmon<elf>
  \-PE  0x7ea20000-7ea30000     \               urlmon
ELF     0x7ea30000-7eaf6000     Deferred        shell32<elf>
  \-PE  0x7ea50000-7eaf6000     \               shell32
ELF     0x7eaf6000-7eb52000     Deferred        shlwapi<elf>
  \-PE  0x7eb10000-7eb52000     \               shlwapi
ELF     0x7eb52000-7eb71000     Deferred        mpr<elf>
  \-PE  0x7eb60000-7eb71000     \               mpr
ELF     0x7eb71000-7ebb5000     Deferred        wininet<elf>
  \-PE  0x7eb80000-7ebb5000     \               wininet
ELF     0x7ebb5000-7ebe0000     Deferred        ws2_32<elf>
  \-PE  0x7ebc0000-7ebe0000     \               ws2_32
ELF     0x7ebe0000-7ec01000     Deferred        iphlpapi<elf>
  \-PE  0x7ebf0000-7ec01000     \               iphlpapi
ELF     0x7ec01000-7ec4b000     Deferred        rpcrt4<elf>
  \-PE  0x7ec20000-7ec4b000     \               rpcrt4
ELF     0x7ec4b000-7ecd5000     Deferred        ole32<elf>
  \-PE  0x7ec60000-7ecd5000     \               ole32
ELF     0x7ecd5000-7ed94000     Deferred        comctl32<elf>
  \-PE  0x7ece0000-7ed94000     \               comctl32
ELF     0x7ed94000-7edb9000     Deferred        msvfw32<elf>
  \-PE  0x7eda0000-7edb9000     \               msvfw32
ELF     0x7edb9000-7edfa000     Deferred        advapi32<elf>
  \-PE  0x7edd0000-7edfa000     \               advapi32
ELF     0x7eee0000-7f7e3000     Deferred        gdi32<elf>
  \-PE  0x7ef30000-7f7e3000     \               gdi32
ELF     0x7f7e3000-7f90f000     Deferred        user32<elf>
  \-PE  0x7f800000-7f90f000     \               user32
ELF     0x7f90f000-7f98f000     Deferred        winmm<elf>
  \-PE  0x7f920000-7f98f000     \               winmm
ELF     0x7f98f000-7f9b2000     Deferred        msacm32<elf>
  \-PE  0x7f9a0000-7f9b2000     \               msacm32
ELF     0x7f9b2000-7f9f1000     Deferred        avifil32<elf>
  \-PE  0x7f9c0000-7f9f1000     \               avifil32
ELF     0x7f9f1000-7fa05000     Deferred        lz32<elf>
  \-PE  0x7fa00000-7fa05000     \               lz32
ELF     0x7fa05000-7fa20000     Deferred        version<elf>
  \-PE  0x7fa10000-7fa20000     \               version
ELF     0x7fb21000-7fb23000     Deferred        libnvidia-tls.so.1
ELF     0x7fb23000-7fb30000     Deferred        libxext.so.6
ELF     0x7fb32000-7fb36000     Deferred        libxdmcp.so.6
ELF     0x7fb36000-7fb3d000     Deferred        libsm.so.6
ELF     0x7fc85000-7fd90000     Export          kernel32<elf>
  \-PE  0x7fcb0000-7fd90000     \               kernel32
ELF     0x7fea1000-7feac000     Deferred        libgcc_s.so.1
ELF     0x7feac000-7feb7000     Deferred        libnss_files.so.2
ELF     0x7feb7000-7fecd000     Deferred        libnsl.so.1
ELF     0x7fecd000-7fed7000     Deferred        libnss_compat.so.2
ELF     0x7fed8000-7fee8000     Deferred        libtasn1.so.2
ELF     0x7fee8000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7db0000-b7db3000     Deferred        libxrandr.so.2
ELF     0xb7db5000-b7db9000     Deferred        libdl.so.2
ELF     0xb7db9000-b7ee7000     Deferred        libc.so.6
ELF     0xb7ee7000-b7efa000     Deferred        libpthread.so.0
ELF     0xb7efa000-b7f13000     Export          libwine.so.1
ELF     0xb7f13000-b7f15000     Deferred        xlcutf8load.so.2
ELF     0xb7f15000-b7f18000     Deferred        libxau.so.6
ELF     0xb7f18000-b7f22000     Deferred        libnss_nis.so.2
ELF     0xb7f26000-b7f3c000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\mnt\storage\Picasa2\Picasa2.exe
        00000009    0 <==
WineDbg terminated on pid 0x8
wine client error:9: write: Bad file descriptor

```

---

### Post by apolyak on 2006-04-23
Xlib:  extension "GLX" missing on display ":0.0".
Do you have nvidia video card and nvidia drivers installed? Check Help->User guide->Hardware on how to install nvidia drivers. For ati card search forum.
Then delete ~/.wine directory ( rm -r .wine ) and try again. Picasa running in wine just fine, in terminal, in your home dir (~/) type:
user_name@host_name:~$ wine .wine/drive_c/Program\ Files/Picasa2/Picasa2.exe
Good luck

---

### Post by dmizer on 2006-04-24
what is it that you're trying to do with picasa?  if i recall correctly it's merely a picture viewer.  i know it also has a utility that allows you to view pictures in a slideshow, but ubuntu is able to do that natively.

there's probably easier options for you than picasa in wine.

---

