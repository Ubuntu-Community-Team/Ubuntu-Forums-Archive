---
title: "ROOT (root.cern.ch) BOF"
date: 2009-09-15
forum: General Help
---

### Post by ManDay on 2009-09-15
The following is the output thrown by ROOT upon

TH1F *h1 = new TH1F( , ,100,-3,3 ); 
h1->Draw( "][" ); 

and alike. I've filed a bug, but got answered that I'm the only one having this problem.

The BOF backtrace:

```

<TCanvas::MakeDefCanvas>: created default TCanvas with name c1
*** buffer overflow detected ***: /usr/bin/root.exe terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7112da8]
/lib/tls/i686/cmov/libc.so.6[0xb7110eb0]
/lib/tls/i686/cmov/libc.so.6[0xb711013d]
/usr/lib/root/5.18/libHistPainter.so(_ZN12THistPainter9PaintHistEPKc+0xc38)[0xb5b77958]
/usr/lib/root/5.18/libHistPainter.so(_ZN12THistPainter5PaintEPKc+0x909)[0xb5b7cb69]
/usr/lib/root/5.18/libHist.so(_ZN3TH15PaintEPKc+0x6f)[0xb6b12b6f]
/usr/lib/root/5.18/libGpad.so(_ZN4TPad13PaintModifiedEv+0x298)[0xb65da9c8]
/usr/lib/root/5.18/libGpad.so(_ZN7TCanvas6UpdateEv+0x9a)[0xb65b841a]
/usr/lib/root/libCore.so.5.18(_ZN5TCint17UpdateAllCanvasesEv+0x69)[0xb7a61dd9]
/usr/lib/root/libCore.so.5.18(_ZN5TCint11ProcessLineEPKcPN12TInterpreter10EErrorCodeE+0xd5)[0xb7a64145]
/usr/lib/root/libCore.so.5.18(_ZN5TCint16ProcessLineSynchEPKcPN12TInterpreter10EErrorCodeE+0x57)[0xb7a606d7]
/usr/lib/root/libCore.so.5.18(_ZN5TCint15EndOfLineActionEv+0x34)[0xb7a60644]
/usr/lib/root/libRint.so.5.18(_ZN5TRint15HandleTermInputEv+0x270)[0xb72c7000]
/usr/lib/root/libRint.so.5.18(_ZN17TTermInputHandler6NotifyEv+0x25)[0xb72c6a45]
/usr/lib/root/libRint.so.5.18(_ZN17TTermInputHandler10ReadNotifyEv+0x14)[0xb72c9124]
/usr/lib/root/libCore.so.5.18(_ZN11TUnixSystem16CheckDescriptorsEv+0x1b9)[0xb7a927e9]
/usr/lib/root/libCore.so.5.18(_ZN11TUnixSystem16DispatchOneEventEb+0x109)[0xb7a92e49]
/usr/lib/root/libCore.so.5.18(_ZN7TSystem9InnerLoopEv+0x21)[0xb7a1c181]
/usr/lib/root/libCore.so.5.18(_ZN7TSystem3RunEv+0x89)[0xb7a1ef29]
/usr/lib/root/libCore.so.5.18(_ZN12TApplication3RunEb+0x37)[0xb79b9527]
/usr/lib/root/libRint.so.5.18(_ZN5TRint3RunEb+0x448)[0xb72c8c18]
/usr/bin/root.exe(main+0x85)[0x8048ec5]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb702b775]
/usr/bin/root.exe[0x8048d71]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:05 212531     /usr/bin/root.exe
0804a000-0804b000 r--p 00001000 08:05 212531     /usr/bin/root.exe
0804b000-0804c000 rw-p 00002000 08:05 212531     /usr/bin/root.exe
09a0c000-09eb1000 rw-p 09a0c000 00:00 0          [heap]
b5b58000-b5bca000 r-xp 00000000 08:05 855673     /usr/lib/root/5.18/libHistPainter.so.5.18
b5bca000-b5bcb000 r--p 00072000 08:05 855673     /usr/lib/root/5.18/libHistPainter.so.5.18
b5bcb000-b5bcc000 rw-p 00073000 08:05 855673     /usr/lib/root/5.18/libHistPainter.so.5.18
b5bcc000-b5bcd000 rw-p b5bcc000 00:00 0 
b5bcd000-b5bf1000 r-xp 00000000 08:05 824396     /usr/lib/libpng12.so.0.27.0
b5bf1000-b5bf2000 r--p 00023000 08:05 824396     /usr/lib/libpng12.so.0.27.0
b5bf2000-b5bf3000 rw-p 00024000 08:05 824396     /usr/lib/libpng12.so.0.27.0
b5bf3000-b5bfa000 r-xp 00000000 08:05 825129     /usr/lib/libgif.so.4.1.6
b5bfa000-b5bfb000 r--p 00006000 08:05 825129     /usr/lib/libgif.so.4.1.6
b5bfb000-b5bfc000 rw-p 00007000 08:05 825129     /usr/lib/libgif.so.4.1.6
b5bfc000-b5c4e000 r-xp 00000000 08:05 824398     /usr/lib/libtiff.so.4.2.1
b5c4e000-b5c4f000 ---p 00052000 08:05 824398     /usr/lib/libtiff.so.4.2.1
b5c4f000-b5c51000 r--p 00052000 08:05 824398     /usr/lib/libtiff.so.4.2.1
b5c51000-b5c52000 rw-p 00054000 08:05 824398     /usr/lib/libtiff.so.4.2.1
b5c52000-b5c71000 r-xp 00000000 08:05 824394     /usr/lib/libjpeg.so.62.0.0
b5c71000-b5c72000 rw-p 0001e000 08:05 824394     /usr/lib/libjpeg.so.62.0.0
b5c72000-b5d02000 r-xp 00000000 08:05 856038     /usr/lib/root/5.18/libASImage.so.5.18
b5d02000-b5d03000 ---p 00090000 08:05 856038     /usr/lib/root/5.18/libASImage.so.5.18
b5d03000-b5d05000 r--p 00090000 08:05 856038     /usr/lib/root/5.18/libASImage.so.5.18
b5d05000-b5d07000 rw-p 00092000 08:05 856038     /usr/lib/root/5.18/libASImage.so.5.18
b5d07000-b5d13000 rw-p b5d07000 00:00 0 
b5d13000-b5d17000 r-xp 00000000 08:05 824494     /usr/lib/libXfixes.so.3.1.0
b5d17000-b5d18000 rw-p 00003000 08:05 824494     /usr/lib/libXfixes.so.3.1.0
b5d18000-b5d20000 r-xp 00000000 08:05 824498     /usr/lib/libXcursor.so.1.0.2
b5d20000-b5d21000 rw-p 00007000 08:05 824498     /usr/lib/libXcursor.so.1.0.2
b5d21000-b5d46000 r--p 00000000 08:05 774305     /usr/share/fonts/truetype/freefont/FreeSansBold.ttf
b5d46000-b5d58000 r-xp 00000000 08:05 855647     /usr/lib/root/5.18/libGX11TTF.so.5.18
b5d58000-b5d59000 r--p 00011000 08:05 855647     /usr/lib/root/5.18/libGX11TTF.so.5.18
b5d59000-b5d5a000 rw-p 00012000 08:05 855647     /usr/lib/root/5.18/libGX11TTF.so.5.18
b5d5a000-b6364000 r-xp 00000000 08:05 855665     /usr/lib/root/5.18/libGui.so.5.18
b6364000-b6389000 r--p 0060a000 08:05 855665     /usr/lib/root/5.18/libGui.so.5.18
b6389000-b6390000 rw-p 0062f000 08:05 855665     /usr/lib/root/5.18/libGui.so.5.18
b6390000-b6397000 rw-p b6390000 00:00 0 
b6397000-b63bb000 r-xp 00000000 08:05 824401     /usr/lib/libexpat.so.1.5.2
b63bb000-b63bd000 r--p 00023000 08:05 824401     /usr/lib/libexpat.so.1.5.2
b63bd000-b63be000 rw-p 00025000 08:05 824401     /usr/lib/libexpat.so.1.5.2
b63be000-b63c2000 r-xp 00000000 08:05 824381     /usr/lib/libXdmcp.so.6.0.0
b63c2000-b63c3000 rw-p 00003000 08:05 824381     /usr/lib/libXdmcp.so.6.0.0
b63c3000-b63cb000 r-xp 00000000 08:05 824466     /usr/lib/libXrender.so.1.3.0
b63cb000-b63cc000 r--p 00007000 08:05 824466     /usr/lib/libXrender.so.1.3.0
b63cc000-b63cd000 rw-p 00008000 08:05 824466     /usr/lib/libXrender.so.1.3.0
b63cd000-b63f8000 r-xp 00000000 08:05 824407     /usr/lib/libfontconfig.so.1
```

---

### Post by a_nomad on 2010-02-15
I have the exact same problem. I have tried to recompile from scratch and that did not resolve the issue. Did you get an answer from ROOT about this?

---

### Post by dvd_it on 2010-08-30
I have no problems running this on my self-compiled root package [1].
d

[1] [http://sourceforge.net/projects/cernrootdebs/](http://sourceforge.net/projects/cernrootdebs/)
read instructions!

---

