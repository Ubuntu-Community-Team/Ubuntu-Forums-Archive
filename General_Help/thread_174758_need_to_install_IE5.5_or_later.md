---
title: "need to install IE5.5 or later"
date: 2006-05-12
forum: General Help
---

### Post by closeyourwindows on 2006-05-12
I am trying to use an application that requires IE through wine.  I downloaded the .exe and still no go.  is there a trick to getting IE to install through wine?

---

### Post by Abild on 2006-05-12
Use IES4Linux
[http://www.tatanka.com.br/ies4linux/]("http://www.tatanka.com.br/ies4linux/")

---

### Post by louis_nichols on 2006-05-12
[winetools]("http://www.von-thadden.de/Joachim/WineTools/") will do the trick for you.

---

### Post by dg_w on 2006-05-12
This should do it for you :)

[http://blog.drinsama.de/erich/en/linux/2006040302-msie-on-linux](http://blog.drinsama.de/erich/en/linux/2006040302-msie-on-linux)


Dg_w

---

### Post by closeyourwindows on 2006-05-12
[QUOTE=Abild]Use IES4Linux
[http://www.tatanka.com.br/ies4linux/]("http://www.tatanka.com.br/ies4linux/")[/QUOTE]


I did this and I have the IE icon on the desktop but it will not open.  I can open other apps in wine.

```
=================  IEs 4 Linux =================
Install IE6, IE5.5 and IE5 on Linux via Wine.
Credits: Sergio Lopes <slopes at gmail dot com>
Project page: http://tatanka.com.br/ies4linux
See README file for more info

Installation options:
[1] Install IE6, IE5.5 and IE5
[2] Install only IE6
[3] Install only IE5.5
[4] Install only IE5.0
Please choose an option: 3

Downloading everything we need ...
[ OK ]

Creating basic Windows installation ...
 Creating Wine Prefix
 Installing RICHED20
 Installing DCOM98
 Installing ActiveX MFC40
 Finalizing
[ OK ]

Installing IE 5.5 ...
 Extracting downloaded exe file
 Extracting CAB files
 Installing TTF Fonts
 Configuring ie55
[ OK ]

Installing Flash Player 8 ...
 Preparing installation
 Installing flash on ie55
[ OK ]

IEs4Linux installations finished! ...

```

any ideas on how to get this to recognize it?
here is a screen shot.

[http://img125.imageshack.us/my.php?image=screenshot3kg.png]("http://img125.imageshack.us/my.php?image=screenshot3kg.png")

---

### Post by aysiu on 2006-05-12
When you go to /home/closeyourwindows/bin, do you see a file there called ie5.5?

---

### Post by closeyourwindows on 2006-05-12
yeah, there is a bin directory with all three in there
```
nate@theother:~/bin$ ls
ie5  ie55  ie6

```

but when I try to open with wine or ./ I am not able to.  
```
nate@theother:~/bin$ ./ie5
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
fixme:shell:StopWatchMode () stub!
fixme:shell:SHCreateShellPalette stub
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
fixme:shell:MLGetUILanguage () stub
fixme:shell:StopWatchMode () stub!
fixme:shell:SHCreateShellPalette stub
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:shell:MLLoadLibraryW (L"browselc.dll",0x71060000,0x00000002) semi-stub!
fixme:shell:DeleteMenuWrap 0x140 00000003 00000400): semi-stub
fixme:shell:DeleteMenuWrap 0x370 00000003 00000400): semi-stub
fixme:shell:URL_ParseUrl failed to parse L"about:blank"
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10034,0x00008003,0x00008000,0x0000c072,0x00000001,0x7faf9d88):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10034, wParam=0x00000000, size.cx=1024, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x10038 wParam 00000001 lParam 00000000
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10052, wParam=0x00000000, size.cx=1024, size.cy=764 stub!
fixme:shell:NTSHChangeNotifyRegister (0x10052,0x00008003,0x0c02b7ff,0x0000c072,0x00000001,0x7faf9ddc):semi stub.
fixme:shell:SHIsLowMemoryMachine (0x00000000) stub
fixme:shell:SHIsLowMemoryMachine (0x00000000) stub
err:rebar:REBAR_Layout no redraw and client is zero, skip layout
fixme:urlmon:CoInternetQueryInfo (L"about:blank", 8, 0, 0x7faf8f2c, 4, 0x7faf8f20, 0): stub
fixme:urlmon:CoInternetQueryInfo (L"about:blank", a, 0, 0x7faf8f28, 4, 0x7faf8f1c, 0): stub
fixme:shell:SHPackDispParamsV 0x7faf5a98 0x7faf59f8 0x7 0x7faf5acc
fixme:shell:SHPackDispParamsV 0x7faf5aa0 0x7faf5a00 0x6 0x7faf5ad4
fixme:shell:IConnectionPoint_SimpleInvoke (0x7fdbe1f8 0x6a (nil)) stub
fixme:shell:IConnectionPoint_SimpleInvoke (0x7fdbe1e0 0x6a (nil)) stub
fixme:shell:MLGetUILanguage () stub
wine: Call from 0x7fca1600 to unimplemented function shlwapi.dll.ZoneComputePaneSize, aborting
wine: Unimplemented function shlwapi.dll.ZoneComputePaneSize called at address 0x7fca1600 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function shlwapi.dll.ZoneComputePaneSize called in 32-bit code (0x7fca166e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7fca166e ESP:7faf7040 EBP:7faf70a4 EFLAGS:00200202(   - 00      - - I1)
 EAX:7fc8ccb1 EBX:7fd02604 ECX:00000000 EDX:7faf70c8
 ESI:7faf70c8 EDI:00000001
Stack dump:
0x7faf7040:  7faf70c8 00000008 00000002 80000100
0x7faf7050:  00000001 00000000 7fca1600 00000002
0x7faf7060:  7f9df6a0 7f9dfab7 0000040e 00000000
0x7faf7070:  00000000 00000000 00000000 00000000
0x7faf7080:  00000000 00000000 00000008 7eefd66c
0x7faf7090:  7eeb2810 00000001 7faf70d8 7f9e756c
0200: sel=1007 base=7fec2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7fca166e RaiseException+0x6e in kernel32 (0x7fca166e)
  2 0x7f9df251 in shlwapi (+0x2f251) (0x7f9df251)
  3 0x7f9b7577 in shlwapi (+0x7577) (0x7f9b7577)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file SHDOCVW.dbg ("\x8c\xee\xab\x7f")
  4 0x70f51b22 in shdocvw (+0x21b22) (0x70f51b22)
  5 0x70f31dae in shdocvw (+0x1dae) (0x70f31dae)
  6 0x7eedbe5a WINPROC_wrapper+0x1a in user32 (0x7eedbe5a)
  7 0x7eedcaa6 in user32 (+0x8caa6) (0x7eedcaa6)
  8 0x7eee216b CallWindowProcW+0x43b in user32 (0x7eee216b)
  9 0x7eeaee87 in user32 (+0x5ee87) (0x7eeaee87)
  10 0x7eeb27fc SendMessageTimeoutW+0x16c in user32 (0x7eeb27fc)
  11 0x7eeb2847 SendMessageW+0x37 in user32 (0x7eeb2847)
  12 0x7ebc40f3 X11DRV_CreateWindow+0x5e3 in winex11 (0x7ebc40f3)
  13 0x7eed7a8e in user32 (+0x87a8e) (0x7eed7a8e)
  14 0x7eed8a43 CreateWindowExW+0x93 in user32 (0x7eed8a43)
  15 0x70f5c6c8 in shdocvw (+0x2c6c8) (0x70f5c6c8)
  16 0x70f5c0d8 in shdocvw (+0x2c0d8) (0x70f5c0d8)
  17 0x70f5bff8 in shdocvw (+0x2bff8) (0x70f5bff8)
  18 0x70f374f8 in shdocvw (+0x74f8) (0x70f374f8)
  19 0x70f37412 in shdocvw (+0x7412) (0x70f37412)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file BROWSEUI.dbg ("\x8c\xee\xab\x7f")
  20 0x71062e7b in browseui (+0x2e7b) (0x71062e7b)
  21 0x7106789a in browseui (+0x789a) (0x7106789a)
  22 0x70f3728b in shdocvw (+0x728b) (0x70f3728b)
  23 0x70f3716b in shdocvw (+0x716b) (0x70f3716b)
  24 0x70f36aec in shdocvw (+0x6aec) (0x70f36aec)
  25 0x71062e5a in browseui (+0x2e5a) (0x71062e5a)
  26 0x71077efe in browseui (+0x17efe) (0x71077efe)
  27 0x70f32475 in shdocvw (+0x2475) (0x70f32475)
  28 0x710620b0 in browseui (+0x20b0) (0x710620b0)
  29 0x71063107 in browseui (+0x3107) (0x71063107)
  30 0x71062f6c in browseui (+0x2f6c) (0x71062f6c)
  31 0x7eedbe5a WINPROC_wrapper+0x1a in user32 (0x7eedbe5a)
  32 0x7eedcaa6 in user32 (+0x8caa6) (0x7eedcaa6)
  33 0x7eee216b CallWindowProcW+0x43b in user32 (0x7eee216b)
  34 0x7eeaee87 in user32 (+0x5ee87) (0x7eeaee87)
  35 0x7eeb27fc SendMessageTimeoutW+0x16c in user32 (0x7eeb27fc)
  36 0x7eeb2847 SendMessageW+0x37 in user32 (0x7eeb2847)
  37 0x7ebc4044 X11DRV_CreateWindow+0x534 in winex11 (0x7ebc4044)
  38 0x7eed7a8e in user32 (+0x87a8e) (0x7eed7a8e)
  39 0x7eed8a43 CreateWindowExW+0x93 in user32 (0x7eed8a43)
  40 0x71074815 in browseui (+0x14815) (0x71074815)
  41 0x7107470f in browseui (+0x1470f) (0x7107470f)
  42 0x71074657 in browseui (+0x14657) (0x71074657)
  43 0x70f3fdf6 in shdocvw (+0xfdf6) (0x70f3fdf6)
  44 0x7fec0060 WinMain+0x20 in iexplore (0x7fec0060)
  45 0x7fec01da main+0xaa in iexplore (0x7fec01da)
  46 0x7fec010e in iexplore (+0x1010e) (0x7fec010e)
  47 0x7fcccfaf in kernel32 (+0x4cfaf) (0x7fcccfaf)
  48 0xb7fad617 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7fad617)
0x7fca166e RaiseException+0x6e in kernel32: addl        $12,%esp
Wine-dbg>

```

not sure what to do at this point, other than ctrl+z
I dont want to use IE, but I need it to install Xara.

---

### Post by aysiu on 2006-05-12
I'm not sure what the problem is. ```
./ie55
``` should work.

---

