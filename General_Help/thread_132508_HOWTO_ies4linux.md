---
title: "HOWTO: ies4linux"
date: 2006-02-18
forum: General Help
---

### Post by Arandomcow5 on 2006-02-18
In my spare time, I like to webdesign. In linux, I can usually get a site up and running fast, but sadly Internet Explorer and Firefox interperet CSS differentley. So, in order for my site to work in Internet Explorer, I use to have to reboot into windows and work some more in there. I got tired of this, it caused nothing but problems, so I went for an alternative: Internet Explorer in Linux with ies4linux

Here is a HowTo on installing and ies4linux

**1. Install WINE**(skip this step if you already have wine)
To do this, first add these repositories to your /etc/apt/sources.list file:
```
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```
Now upgrade your sources with "sudo apt-get update"

After upgrading, you are now ready to install wine. This step is easy, enter this into a terminal:
```
apt-get install wine
```

Now you have wine. The next thing you need to do is install cabextract.

**2. Install Cabextract**
To install cabextract, extract the follwing into your filesystem:
[cabextract-1.1-1.i386.rpm]("http://www.kyz.uklinux.net/downloads/cabextract-1.1-1.i386.rpm")
This should add some files to the /usr/bin folder and /usr/share folders and subfolders

**3. Install ies4linux**
Download the ies4linux tar file with this code:
```
wget http://www.tatanka.com.br/ies4linux/download.php
```
after that is downloaded, extract it and open the resulting folder. There should be a shell script called "ies4linux". Double click on it, and when prompted "run in terminal". You will now be in the download process, just follow the options there.

Works great for web development, now go and make good websites

---

### Post by nalmeth on 2006-02-18
right on. 

I think that with winetools you can get IE 6, but I never use it, and it seems to cause some problems with wine sometimes

---

### Post by Arandomcow5 on 2006-02-18
maybe, but i always had trouble installing winetools. I think I went through 10 different guides, and none of them work. Furthermore, ive been using ies4linux for my webdevelopment, getting it to work on IE in linux, then double checked it in Windows. It emulates wonderfully.

---

### Post by dare2dreamer on 2006-02-23
Thank you for this. You're my new hero. :-)

---

### Post by nanotube on 2006-02-23
note: the cabextract package is available in the repositories, so no need to play with the rpm file.

---

### Post by Tim Thumb on 2006-04-14
This worked great for me and I'm now a step nearer to ditching Windows.

---

### Post by danalog on 2006-04-20
I've got it working but I have a problem.

The IE6 window does not have a border.

Using Xgl and Gnome on Dapper Drake.

---

### Post by yaddoshi on 2006-05-01
I followed the directions, everything downloads and installs fine, and then wine barfs on me when I try to run the binary.

> yaddoshi@yaddo:~/bin$ ./ie55
fixme:shell:StopWatchMode () stub!
fixme:shell:SHCreateShellPalette stub
fixme:shell:MLGetUILanguage () stub
fixme:shell:StopWatchMode () stub!
fixme:shell:SHCreateShellPalette stub
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:shell:MLLoadLibraryW (L"browselc.dll",0x71110000,0x00000002) semi-stub!
fixme:shell:DeleteMenuWrap 0x140 00000003 00000400): semi-stub
fixme:shell:DeleteMenuWrap 0x370 00000003 00000400): semi-stub
fixme:shell:URL_ParseUrl failed to parse L"about:blank"
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10034,0x00008003,0x00008000,0x0000c072,0x00000001,0x7faf9de0):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10034, wParam=0x00000000, size.cx=1280, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x10038 wParam 00000001 lParam 00000000
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10052, wParam=0x00000000, size.cx=1280, size.cy=796 stub!
fixme:shell:NTSHChangeNotifyRegister (0x10052,0x00008003,0x0c02b7ff,0x0000c072,0x00000001,0x7faf9e34):semi stub.
fixme:shell:SHIsLowMemoryMachine (0x00000000) stub
fixme:shell:SHIsLowMemoryMachine (0x00000000) stub
err:rebar:REBAR_Layout no redraw and client is zero, skip layout
fixme:urlmon:CoInternetQueryInfo (L"about:blank", 8, 0, 0x7faf8f70, 4, 0x7faf8f64, 0): stub
fixme:urlmon:CoInternetQueryInfo (L"about:blank", a, 0, 0x7faf8f6c, 4, 0x7faf8f60, 0): stub
fixme:shell:SHPackDispParamsV 0x7faf6b28 0x7faf6a88 0x7 0x7faf6b5c
fixme:shell:SHPackDispParamsV 0x7faf6b30 0x7faf6a90 0x6 0x7faf6b64
fixme:shell:IConnectionPoint_SimpleInvoke (0x7fdcda18 0x6a (nil)) stub
fixme:shell:IConnectionPoint_SimpleInvoke (0x7fdcda00 0x6a (nil)) stub
fixme:shell:MLGetUILanguage () stub
wine: Call from 0x7fcb1600 to unimplemented function shlwapi.dll.ZoneComputePaneSize, aborting
wine: Unimplemented function shlwapi.dll.ZoneComputePaneSize called at address 0x7fcb1600 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function shlwapi.dll.ZoneComputePaneSize called in 32-bit code (0x7fcb166e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7fcb166e ESP:7faf80d8 EBP:7faf813c EFLAGS:00200216(   - 00      - IAP1)
 EAX:7fc9ccb1 EBX:7fd12604 ECX:00000000 EDX:7faf8160
 ESI:7faf8160 EDI:00000001
Stack dump:
0x7faf80d8:  7faf8160 00000008 00000002 80000100
0x7faf80e8:  00000001 00000000 7fcb1600 00000002
0x7faf80f8:  7f97d6a0 7f97dab7 0000040e 00000000
0x7faf8108:  00000000 00000000 00000000 00000000
0x7faf8118:  00000000 00000000 00000008 7eebd66c
0x7faf8128:  7ee72810 00000001 7faf8170 7f98556c
0200: sel=1007 base=7fec2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7fcb166e RaiseException+0x6e in kernel32 (0x7fcb166e)
  2 0x7f97d251 in shlwapi (+0x2d251) (0x7f97d251)
  3 0x7f955577 in shlwapi (+0x5577) (0x7f955577)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file SHDOCVW.dbg ("\x8c\xee\xab\x7f")
  4 0x70fe8275 in shdocvw (+0x8275) (0x70fe8275)
  5 0x70fe1bd9 in shdocvw (+0x1bd9) (0x70fe1bd9)
  6 0x7ee9be5a WINPROC_wrapper+0x1a in user32 (0x7ee9be5a)
  7 0x7ee9caa6 in user32 (+0x8caa6) (0x7ee9caa6)
  8 0x7eea216b CallWindowProcW+0x43b in user32 (0x7eea216b)
  9 0x7ee6ee87 in user32 (+0x5ee87) (0x7ee6ee87)
  10 0x7ee727fc SendMessageTimeoutW+0x16c in user32 (0x7ee727fc)
  11 0x7ee72847 SendMessageW+0x37 in user32 (0x7ee72847)
  12 0x7eb700f3 X11DRV_CreateWindow+0x5e3 in winex11 (0x7eb700f3)
  13 0x7ee97a8e in user32 (+0x87a8e) (0x7ee97a8e)
  14 0x7ee98a43 CreateWindowExW+0x93 in user32 (0x7ee98a43)
  15 0x70ff8499 in shdocvw (+0x18499) (0x70ff8499)
  16 0x70ff7f61 in shdocvw (+0x17f61) (0x70ff7f61)
  17 0x70ff7e81 in shdocvw (+0x17e81) (0x70ff7e81)
  18 0x70ff4903 in shdocvw (+0x14903) (0x70ff4903)
  19 0x70ff46a0 in shdocvw (+0x146a0) (0x70ff46a0)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file BROWSEUI.dbg ("\x8c\xee\xab\x7f")
  20 0x7112a3e5 in browseui (+0x1a3e5) (0x7112a3e5)
  21 0x7112ad0f in browseui (+0x1ad0f) (0x7112ad0f)
  22 0x70ff4560 in shdocvw (+0x14560) (0x70ff4560)
  23 0x70ff4409 in shdocvw (+0x14409) (0x70ff4409)
  24 0x70ff4343 in shdocvw (+0x14343) (0x70ff4343)
  25 0x7112a3c4 in browseui (+0x1a3c4) (0x7112a3c4)
  26 0x7112f6c6 in browseui (+0x1f6c6) (0x7112f6c6)
  27 0x70feff43 in shdocvw (+0xff43) (0x70feff43)
  28 0x71112006 in browseui (+0x2006) (0x71112006)
  29 0x71113013 in browseui (+0x3013) (0x71113013)
  30 0x71112e1c in browseui (+0x2e1c) (0x71112e1c)
  31 0x7ee9be5a WINPROC_wrapper+0x1a in user32 (0x7ee9be5a)
  32 0x7ee9caa6 in user32 (+0x8caa6) (0x7ee9caa6)
  33 0x7eea216b CallWindowProcW+0x43b in user32 (0x7eea216b)
  34 0x7ee6ee87 in user32 (+0x5ee87) (0x7ee6ee87)
  35 0x7ee727fc SendMessageTimeoutW+0x16c in user32 (0x7ee727fc)
  36 0x7ee72847 SendMessageW+0x37 in user32 (0x7ee72847)
  37 0x7eb70044 X11DRV_CreateWindow+0x534 in winex11 (0x7eb70044)
  38 0x7ee97a8e in user32 (+0x87a8e) (0x7ee97a8e)
  39 0x7ee98a43 CreateWindowExW+0x93 in user32 (0x7ee98a43)
  40 0x7112ef81 in browseui (+0x1ef81) (0x7112ef81)
  41 0x7112ee7b in browseui (+0x1ee7b) (0x7112ee7b)
  42 0x7112ed95 in browseui (+0x1ed95) (0x7112ed95)
  43 0x70ffa043 in shdocvw (+0x1a043) (0x70ffa043)
  44 0x7fb1e060 WinMain+0x20 in iexplore (0x7fb1e060)
  45 0x7fb1e1da main+0xaa in iexplore (0x7fb1e1da)
  46 0x7fb1e10e in iexplore (+0xe10e) (0x7fb1e10e)
  47 0x7fcdcfaf in kernel32 (+0x4cfaf) (0x7fcdcfaf)
  48 0xb7f16617 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f16617)
0x7fcb166e RaiseException+0x6e in kernel32: addl        $12,%esp
Wine-dbg>quit
wine: Call from 0x7fcb1600 to unimplemented function shlwapi.dll.ZoneConfigureW, aborting
Process of pid=0x00000008 has terminated

I am presently running Breezy Ubuntu on a Medion Akoya LS notebook (which is actually MSI S260 barebones w/ Samsung drives and RAM and Medion's sticker on it), with a Pentium M 1.6GHz, intel 900 chipset w/ i910/915 graphics, 512MB DDR memory.  I originally tried this on Dapper with IE 6 and IE 5.5, and had the same result each time.  I presently have and had wine version 0.9.12 installed.  I don't know enough about wine yet to know what I'm missing - I followed [these directions]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine&back=HOWTO+INDEX+Wine") to get wine up and running in the first place, and installed it directly from "deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/" with aptitude.

Am I missing / forgetting something?  Should I downgrade to an earlier version?

Thanks in advance.

---

### Post by yaddoshi on 2006-05-02
Apparently there's a new Beta release of IES4LINUX - I found info about it on [this thread]("http://ubuntuforums.org/showthread.php?t=167491&page=2&highlight=ies4linux") or you could just go [straight to the update on the website]("http://www.tatanka.com.br/ies4linux/blog/2006/04/25/fresh-news-ies4linux-20-beta1-and-many-improvements/").

I've already installed it and it's the first time I've gotten IE working on my system - both IE 5.5 and 6 work perfectly fine.

---

### Post by GaFFy on 2006-05-09
[QUOTE=yaddoshi]Apparently there's a new Beta release of IES4LINUX - I found info about it on [this thread]("http://ubuntuforums.org/showthread.php?t=167491&page=2&highlight=ies4linux") or you could just go [straight to the update on the website]("http://www.tatanka.com.br/ies4linux/blog/2006/04/25/fresh-news-ies4linux-20-beta1-and-many-improvements/").

I've already installed it and it's the first time I've gotten IE working on my system - both IE 5.5 and 6 work perfectly fine.[/QUOTE]

Did you uninstall the other one first and if so how? :-k

---

