---
title: "Sketchup (Wine) fails to launch"
date: 2011-10-20
forum: General Help
---

### Post by Eben Fourie on 2011-10-20
Hi,

Ubuntu 10.04  Desktop
Wine 1.2.3
Sketchup 7.0 (also happens with 8.0)

I've previously had no problems running Sketchup under Wine.

Now it fails to launch. When I click on the link, I get the "egg shaker" circle thingy, and a window in the bottom status bar, saying "Starting Sketchup", then both disappear...

I've completely uninstalled Wine & Sketchup, re-installed, same problem.

Is there a log file I can check for more details ? Simple instructions pls ;)

Thanks,
   Eben

---

### Post by Eben Fourie on 2011-10-20
Some more info:

When installing Sketchup, it now only creates a launcher on the desktop, not in the main menu under Applications | Wine | Programs ...

If I run the following command:
```
 wine "/home/eben/.wine/drive_c/Program Files/Google/Google SketchUp 7/SketchUp.exe"
```

I get:
```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  969
  Current serial number in output stream:  969

```

And for :
```
 winedbg "/home/eben/.wine/drive_c/Program Files/Google/Google SketchUp 7/SketchUp.exe"
```

I get:
```
WineDbg starting on pid 0018
First chance exception: page fault on write access to 0x003f0000 in 32-bit code (0x682b32ad).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:682b32ad ESP:0033f810 EBP:0033f888 EFLAGS:00010a02(  R- --O I   - - - )
 EAX:80808081 EBX:68352ff4 ECX:00000000 EDX:00000067
 ESI:000000ac EDI:003f0000
Stack dump:
0x0033f810:  0000031c 00000000 00000000 00000010
0x0033f820:  00000010 00000000 00000000 00000010
0x0033f830:  00000010 68654d9c 00131820 00000000
0x0033f840:  00cc0020 00000308 00330001 683d0001
0x0033f850:  0033f868 0000031c 00132090 00000328
0x0033f860:  00000000 00000000 00000010 00000010
Backtrace:
=>0 0x682b32ad in user32 (+0x132ad) (0x0033f888)
  1 0x682b3923 in user32 (+0x13922) (0x0033f908)
  2 0x682b3ebc in user32 (+0x13ebb) (0x0033f958)
  3 0x682b4145 CreateIconFromResourceEx+0xd4() in user32 (0x0033f9b8)
  4 0x682b4b6f in user32 (+0x14b6e) (0x0033fa88)
  5 0x682b4fa0 LoadImageW+0x1bf() in user32 (0x0033fb88)
  6 0x682b5f5e LoadImageA+0x19d() in user32 (0x0033fc78)
  7 0x6856ca26 SIC_Initialize+0x1a5() in shell32 (0x0033fcc8)
  8 0x68576222 in shell32 (+0x26221) (0x0033fd08)
  9 0x7bc49d35 call_dll_entry_point+0x14() in ntdll (0x0033fd28)
  10 0x7bc4ce13 in ntdll (+0x3ce12) (0x0033fe68)
  11 0x7bc4d740 in ntdll (+0x3d73f) (0x0033fec8)
  12 0x7bc4d712 in ntdll (+0x3d711) (0x0033ff28)
  13 0x7bc4d712 in ntdll (+0x3d711) (0x0033ff88)
  14 0x7bc4d943 in ntdll (+0x3d942) (0x0033ffe8)
0x682b32ad: movb    %dl,0x0(%edi,%ecx,4)

```

Any suggestions ?

---

