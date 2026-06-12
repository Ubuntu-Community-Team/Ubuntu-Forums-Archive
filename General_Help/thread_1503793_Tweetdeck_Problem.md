---
title: "Tweetdeck Problem"
date: 2010-06-07
forum: General Help
---

### Post by SoulSmasher on 2010-06-07
Hi, I have a problem running tweetdeck, I both tried downloading the adobe air from application manager, and adobe.com's website and both installed tweetdeck manually and automatically, but right after it starts, it shuts down. This is my terminal output:
```
arda@arda-laptop:/opt$ cd /opt
arda@arda-laptop:/opt$ dir
Adobe\ AIR  google  TweetDeck
arda@arda-laptop:/opt$ cd TweetDeck/
arda@arda-laptop:/opt/TweetDeck$ dir
bin  share
arda@arda-laptop:/opt/TweetDeck$ cd bin
arda@arda-laptop:/opt/TweetDeck/bin$ dir
TweetDeck
arda@arda-laptop:/opt/TweetDeck/bin$ ./TweetDeck 

progname=TweetDeck; RGBA=on
/home/arda/.themes/Darkness (rgba true)/gtk-2.0/gtkrc:80: Murrine configuration option "profile" is no longer supported and will be ignored.
The program 'TweetDeck' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 705 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Application crashed with an unhandled SIGSEGV
Crashlog has been dumped in /tmp/airCrashLogs/0607_1446_sRDGaM
arda@arda-laptop:/opt/TweetDeck/bin$ 

```

And this is the Crashlog:

```
Build: 9130

00110000-0012d000 r-xp 00000000 08:06 1838675    /lib/libgcc_s.so.1
0012d000-0012e000 r--p 0001c000 08:06 1838675    /lib/libgcc_s.so.1
0012e000-0012f000 rw-p 0001d000 08:06 1838675    /lib/libgcc_s.so.1
0012f000-00137000 r-xp 00000000 08:06 791036     /usr/lib/libXrender.so.1.3.0
00137000-00138000 r--p 00007000 08:06 791036     /usr/lib/libXrender.so.1.3.0
00138000-00139000 rw-p 00008000 08:06 791036     /usr/lib/libXrender.so.1.3.0
00139000-0013c000 r-xp 00000000 08:06 795086     /opt/Adobe AIR/Versions/1.0/Resources/libeggtray.so
0013c000-0013d000 rw-p 00002000 08:06 795086     /opt/Adobe AIR/Versions/1.0/Resources/libeggtray.so
0013d000-0013f000 r-xp 00000000 08:06 791024     /usr/lib/libXinerama.so.1.0.0
0013f000-00140000 r--p 00001000 08:06 791024     /usr/lib/libXinerama.so.1.0.0
00140000-00141000 rw-p 00002000 08:06 791024     /usr/lib/libXinerama.so.1.0.0
00141000-00143000 r-xp 00000000 08:06 791006     /usr/lib/libXcomposite.so.1.0.0
00143000-00144000 r--p 00001000 08:06 791006     /usr/lib/libXcomposite.so.1.0.0
00144000-00145000 rw-p 00002000 08:06 791006     /usr/lib/libXcomposite.so.1.0.0
00147000-00148000 r-xp 00000000 00:00 0          [vdso]
00148000-0029b000 r-xp 00000000 08:06 1838641    /lib/tls/i686/cmov/libc-2.11.1.so
0029b000-0029c000 ---p 00153000 08:06 1838641    /lib/tls/i686/cmov/libc-2.11.1.so
0029c000-0029e000 r--p 00153000 08:06 1838641    /lib/tls/i686/cmov/libc-2.11.1.so
0029e000-0029f000 rw-p 00155000 08:06 1838641    /lib/tls/i686/cmov/libc-2.11.1.so
0029f000-002a2000 rw-p 00000000 00:00 0 
002a2000-0066f000 r-xp 00000000 08:06 790731     /usr/lib/libgtk-x11-2.0.so.0.2000.1
0066f000-00673000 r--p 003cd000 08:06 790731     /usr/lib/libgtk-x11-2.0.so.0.2000.1
00673000-00675000 rw-p 003d1000 08:06 790731     /usr/lib/libgtk-x11-2.0.so.0.2000.1
00675000-00677000 rw-p 00000000 00:00 0 
00677000-0068f000 r-xp 00000000 08:06 790733     /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
0068f000-00690000 r--p 00017000 08:06 790733     /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00690000-00691000 rw-p 00018000 08:06 790733     /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00691000-00697000 r-xp 00000000 08:06 791034     /usr/lib/libXrandr.so.2.2.0
00697000-00698000 r--p 00005000 08:06 791034     /usr/lib/libXrandr.so.2.2.0
00698000-00699000 rw-p 00006000 08:06 791034     /usr/lib/libXrandr.so.2.2.0
0069a000-0069c000 r-xp 00000000 08:06 1838655    /lib/tls/i686/cmov/libdl-2.11.1.so
0069c000-0069d000 r--p 00001000 08:06 1838655    /lib/tls/i686/cmov/libdl-2.11.1.so
0069d000-0069e000 rw-p 00002000 08:06 1838655    /lib/tls/i686/cmov/libdl-2.11.1.so
0069e000-006db000 r-xp 00000000 08:06 802794     /usr/lib/libgobject-2.0.so.0.2400.1
006db000-006dc000 r--p 0003c000 08:06 802794     /usr/lib/libgobject-2.0.so.0.2400.1
006dc000-006dd000 rw-p 0003d000 08:06 802794     /usr/lib/libgobject-2.0.so.0.2400.1
006dd000-006f2000 r-xp 00000000 08:06 1838749    /lib/tls/i686/cmov/libpthread-2.11.1.so
006f2000-006f3000 r--p 00014000 08:06 1838749    /lib/tls/i686/cmov/libpthread-2.11.1.so
006f3000-006f4000 rw-p 00015000 08:06 1838749    /lib/tls/i686/cmov/libpthread-2.11.1.so
006f4000-006f6000 rw-p 00000000 00:00 0 
006f6000-00724000 r-xp 00000000 08:06 791293     /usr/lib/libfontconfig.so.1.4.4
00724000-00725000 r--p 0002d000 08:06 791293     /usr/lib/libfontconfig.so.1.4.4
00725000-00726000 rw-p 0002e000 08:06 791293     /usr/lib/libfontconfig.so.1.4.4
00726000-00739000 r-xp 00000000 08:06 1838790    /lib/libz.so.1.2.3.3
00739000-0073a000 r--p 00012000 08:06 1838790    /lib/libz.so.1.2.3.3
0073a000-0073b000 rw-p 00013000 08:06 1838790    /lib/libz.so.1.2.3.3
0073b000-0076a000 r-xp 00000000 08:06 791901     /usr/lib/libssl3.so
0076a000-0076c000 r--p 0002e000 08:06 791901     /usr/lib/libssl3.so
0076c000-0076d000 rw-p 00030000 08:06 791901     /usr/lib/libssl3.so
0076d000-0077b000 r-xp 00000000 08:06 791014     /usr/lib/libXext.so.6.4.0
0077b000-0077c000 r--p 0000d000 08:06 791014     /usr/lib/libXext.so.6.4.0
0077c000-0077d000 rw-p 0000e000 08:06 791014     /usr/lib/libXext.so.6.4.0
0077d000-0077f000 r-xp 00000000 08:06 791010     /usr/lib/libXdamage.so.1.1.0
0077f000-00780000 r--p 00001000 08:06 791010     /usr/lib/libXdamage.so.1.1.0
00780000-00781000 rw-p 00002000 08:06 791010     /usr/lib/libXdamage.so.1.1.0
00781000-00784000 r-xp 00000000 08:06 802795     /usr/lib/libgmodule-2.0.so.0.2400.1
00784000-00785000 r--p 00002000 08:06 802795     /usr/lib/libgmodule-2.0.so.0.2400.1
00785000-00786000 rw-p 00003000 08:06 802795     /usr/lib/libgmodule-2.0.so.0.2400.1
00786000-0078a000 r-xp 00000000 08:06 802796     /usr/lib/libgthread-2.0.so.0.2400.1
0078a000-0078b000 r--p 00003000 08:06 802796     /usr/lib/libgthread-2.0.so.0.2400.1
0078b000-0078c000 rw-p 00004000 08:06 802796     /usr/lib/libgthread-2.0.so.0.2400.1
0078c000-00854000 r-xp 00000000 08:06 1847073    /lib/libglib-2.0.so.0.2400.1
00854000-00855000 r--p 000c7000 08:06 1847073    /lib/libglib-2.0.so.0.2400.1
00855000-00856000 rw-p 000c8000 08:06 1847073    /lib/libglib-2.0.so.0.2400.1
00856000-0096f000 r-xp 00000000 08:06 790997     /usr/lib/libX11.so.6.3.0
0096f000-00970000 r--p 00118000 08:06 790997     /usr/lib/libX11.so.6.3.0
00970000-00972000 rw-p 00119000 08:06 790997     /usr/lib/libX11.so.6.3.0
00972000-00973000 rw-p 00000000 00:00 0 
00973000-00995000 r-xp 00000000 08:06 791876     /usr/lib/libsmime3.so
00995000-00997000 r--p 00021000 08:06 791876     /usr/lib/libsmime3.so
00997000-00998000 rw-p 00023000 08:06 791876     /usr/lib/libsmime3.so
00998000-009a0000 r-xp 00000000 08:06 791008     /usr/lib/libXcursor.so.1.0.2
009a0000-009a1000 r--p 00007000 08:06 791008     /usr/lib/libXcursor.so.1.0.2
009a1000-009a2000 rw-p 00008000 08:06 791008     /usr/lib/libXcursor.so.1.0.2
009a2000-009a3000 r-xp 00000000 08:06 801459     /usr/lib/gtk-2.0/modules/librgba.so
009a3000-009a4000 r--p 00000000 08:06 801459     /usr/lib/gtk-2.0/modules/librgba.so
009a4000-009a5000 rw-p 00001000 08:06 801459     /usr/lib/gtk-2.0/modules/librgba.so
009a5000-00a38000 r-xp 00000000 08:06 790732     /usr/lib/libgdk-x11-2.0.so.0.2000.1
00a38000-00a3a000 r--p 00093000 08:06 790732     /usr/lib/libgdk-x11-2.0.so.0.2000.1
00a3a000-00a3b000 rw-p 00095000 08:06 790732     /usr/lib/libgdk-x11-2.0.so.0.2000.1
00a3b000-00aac000 r-xp 00000000 08:06 791301     /usr/lib/libfreetype.so.6.3.22
00aac000-00ab0000 r--p 00070000 08:06 791301     /usr/lib/libfreetype.so.6.3.22
00ab0000-00ab1000 rw-p 00074000 08:06 791301     /usr/lib/libfreetype.so.6.3.22
00ab1000-00b4d000 r-xp 00000000 08:06 788436     /usr/lib/libadobecertstore.so
00b4d000-00b5c000 rw-p 0009b000 08:06 788436     /usr/lib/libadobecertstore.so
00b5c000-00b5f000 rw-p 00000000 00:00 0 
00b5f000-00b90000 r-xp 00000000 08:06 791710     /usr/lib/libnspr4.so
00b90000-00b91000 r--p 00030000 08:06 791710     /usr/lib/libnspr4.so
00b91000-00b92000 rw-p 00031000 08:06 791710     /usr/lib/libnspr4.so
00b92000-00b94000 rw-p 00000000 00:00 0 
00b94000-00ba0000 r-xp 00000000 08:06 791022     /usr/lib/libXi.so.6.1.0
00ba0000-00ba1000 r--p 0000c000 08:06 791022     /usr/lib/libXi.so.6.1.0
00ba1000-00ba2000 rw-p 0000d000 08:06 791022     /usr/lib/libXi.so.6.1.0
00ba2000-00bac000 r-xp 00000000 08:06 791744     /usr/lib/libpangocairo-1.0.so.0.2800.0
00bac000-00bad000 r--p 00009000 08:06 791744     /usr/lib/libpangocairo-1.0.so.0.2800.0
00bad000-00bae000 rw-p 0000a000 08:06 791744     /usr/lib/libpangocairo-1.0.so.0.2800.0
00bae000-00bb2000 r-xp 00000000 08:06 791016     /usr/lib/libXfixes.so.3.1.0
00bb2000-00bb3000 r--p 00003000 08:06 791016     /usr/lib/libXfixes.so.3.1.0
00bb3000-00bb4000 rw-p 00004000 08:06 791016     /usr/lib/libXfixes.so.3.1.0
00bb4000-00bbb000 r-xp 00000000 08:06 1838755    /lib/tls/i686/cmov/librt-2.11.1.so
00bbb000-00bbc000 r--p 00006000 08:06 1838755    /lib/tls/i686/cmov/librt-2.11.1.so
00bbc000-00bbd000 rw-p 00007000 08:06 1838755    /lib/tls/i686/cmov/librt-2.11.1.so
00bbd000-00bc0000 r-xp 00000000 08:06 791773     /usr/lib/libplc4.so
00bc0000-00bc1000 r--p 00002000 08:06 791773     /usr/lib/libplc4.so
00bc1000-00bc2000 rw-p 00003000 08:06 791773     /usr/lib/libplc4.so
00bc2000-00bc4000 r-xp 00000000 08:06 791775     /usr/lib/libplds4.so
00bc4000-00bc5000 r--p 00001000 08:06 791775     /usr/lib/libplds4.so
00bc5000-00bc6000 rw-p 00002000 08:06 791775     /usr/lib/libplds4.so
00bc7000-00be2000 r-xp 00000000 08:06 1847216    /lib/ld-2.11.1.so
00be2000-00be3000 r--p 0001a000 08:06 1847216    /lib/ld-2.11.1.so
00be3000-00be4000 rw-p 0001b000 08:06 1847216    /lib/ld-2.11.1.so
00be4000-00d07000 r-xp 00000000 08:06 790387     /opt/Adobe AIR/Versions/1.0/Resources/libcurl.so
00d07000-00d1e000 rw-p 00122000 08:06 790387     /opt/Adobe AIR/Versions/1.0/Resources/libcurl.so
00d1e000-00d22000 rw-p 00000000 00:00 0 
00d22000-00d2a000 r-xp 00000000 08:06 791305     /usr/lib/libfusion-1.2.so.0.8.0
00d2a000-00d2b000 r--p 00007000 08:06 791305     /usr/lib/libfusion-1.2.so.0.8.0
00d2b000-00d2c000 rw-p 00008000 08:06 791305     /usr/lib/libfusion-1.2.so.0.8.0
00d2c000-00d2e000 r-xp 00000000 08:06 791001     /usr/lib/libXau.so.6.0.0
00d2e000-00d2f000 r--p 00001000 08:06 791001     /usr/lib/libXau.so.6.0.0
00d2f000-00d30000 rw-p 00002000 08:06 791001     /usr/lib/libXau.so.6.0.0
00d30000-00e19000 r-xp 00000000 08:06 791906     /usr/lib/libstdc++.so.6.0.13
00e19000-00e1a000 ---p 000e9000 08:06 791906     /usr/lib/libstdc++.so.6.0.13
00e1a000-00e1e000 r--p 000e9000 08:06 791906     /usr/lib/libstdc++.so.6.0.13
00e1e000-00e1f000 rw-p 000ed000 08:06 791906     /usr/lib/libstdc++.so.6.0.13
00e1f000-00e26000 rw-p 00000000 00:00 0 
00e26000-00e3f000 r-xp 00000000 08:06 791087     /usr/lib/libatk-1.0.so.0.3009.1
00e3f000-00e40000 ---p 00019000 08:06 791087     /usr/lib/libatk-1.0.so.0.3009.1
00e40000-00e41000 r--p 00019000 08:06 791087     /usr/lib/libatk-1.0.so.0.3009.1
00e41000-00e42000 rw-p 0001a000 08:06 791087     /usr/lib/libatk-1.0.so.0.3009.1
00e42000-00e67000 r-xp 00000000 08:06 791746     /usr/lib/libpangoft2-1.0.so.0.2800.0
00e67000-00e68000 r--p 00024000 08:06 791746     /usr/lib/libpangoft2-1.0.so.0.2800.0
00e68000-00e69000 rw-p 00025000 08:06 791746     /usr/lib/libpangoft2-1.0.so.0.2800.0
00e69000-00e81000 r-xp 00000000 08:06 792008     /usr/lib/libxcb.so.1.1.0
00e81000-00e82000 r--p 00017000 08:06 792008     /usr/lib/libxcb.so.1.1.0
00e82000-00e83000 rw-p 00018000 08:06 792008     /usr/lib/libxcb.so.1.1.0
00e86000-00eaa000 r-xp 00000000 08:06 1838690    /lib/tls/i686/cmov/libm-2.11.1.so
00eaa000-00eab000 r--p 00023000 08:06 1838690    /lib/tls/i686/cmov/libm-2.11.1.so
00eab000-00eac000 rw-p 00024000 08:06 1838690    /lib/tls/i686/cmov/libm-2.11.1.so
00eac000-0187e000 r-xp 00000000 08:06 790364     /opt/Adobe AIR/Versions/1.0/libCore.so
0187e000-018e2000 rw-p 009d2000 08:06 790364     /opt/Adobe AIR/Versions/1.0/libCore.so
018e2000-019bb000 rw-p 00000000 00:00 0 
019bb000-01a2e000 r-xp 00000000 08:06 791230     /usr/lib/libdirectfb-1.2.so.0.8.0
01a2e000-01a2f000 ---p 00073000 08:06 791230     /usr/lib/libdirectfb-1.2.so.0.8.0
01a2f000-01a30000 r--p 00073000 08:06 791230     /usr/lib/libdirectfb-1.2.so.0.8.0
01a30000-01a31000 rw-p 00074000 08:06 791230     /usr/lib/libdirectfb-1.2.so.0.8.0
01a31000-01a32000 rw-p 00000000 00:00 0 
01a32000-01a37000 r-xp 00000000 08:06 791725     /usr/lib/libogg.so.0.6.0
01a37000-01a38000 r--p 00004000 08:06 791725     /usr/lib/libogg.so.0.6.0
01a38000-01a39000 rw-p 00005000 08:06 791725     /usr/lib/libogg.so.0.6.0
01a39000-01a3a000 ---p 00000000 00:00 0 
01a3a000-0223a000 rwxp 00000000 00:00 0 
0223a000-0225c000 r-xp 00000000 08:06 797015     /usr/lib/nss/libnssdbm3.so
0225c000-0225d000 r--p 00021000 08:06 797015     /usr/lib/nss/libnssdbm3.so
0225d000-0225e000 rw-p 00022000 08:06 797015     /usr/lib/nss/libnssdbm3.so
0225e000-02262000 r-xp 00000000 08:06 790705     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
02262000-02263000 r--p 00003000 08:06 790705     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
02263000-02264000 rw-p 00004000 08:06 790705     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
02264000-0227f000 r-xp 00000000 08:06 791382     /usr/lib/libgnome-keyring.so.0.1.1
0227f000-02280000 r--p 0001a000 08:06 791382     /usr/lib/libgnome-keyring.so.0.1.1
02280000-02281000 rw-p 0001b000 08:06 791382     /usr/lib/libgnome-keyring.so.0.1.1
02296000-022ab000 r-xp 00000000 08:06 791720     /usr/lib/libnssutil3.so
022ab000-022ae000 r--p 00014000 08:06 791720     /usr/lib/libnssutil3.so
022ae000-022af000 rw-p 00017000 08:06 791720     /usr/lib/libnssutil3.so
022af000-022e6000 r-xp 00000000 08:06 1838653    /lib/libdbus-1.so.3.4.0
022e6000-022e7000 r--p 00036000 08:06 1838653    /lib/libdbus-1.so.3.4.0
022e7000-022e8000 rw-p 00037000 08:06 1838653    /lib/libdbus-1.so.3.4.0
022e8000-02358000 r-xp 00000000 08:06 1838677    /lib/libgcrypt.so.11.5.2
02358000-02359000 r--p 00070000 08:06 1838677    /lib/libgcrypt.so.11.5.2
02359000-0235b000 rw-p 00071000 08:06 1838677    /lib/libgcrypt.so.11.5.2
02570000-0259f000 r-xp 00000000 08:06 1838733    /lib/libpcre.so.3.12.1
0259f000-025a0000 r--p 0002e000 08:06 1838733    /lib/libpcre.so.3.12.1
025a0000-025a1000 rw-p 0002f000 08:06 1838733    /lib/libpcre.so.3.12.1
02657000-026aa000 r-xp 00000000 08:06 797013     /usr/lib/nss/libnssckbi.so
026aa000-026b3000 r--p 00053000 08:06 797013     /usr/lib/nss/libnssckbi.so
026b3000-026b8000 rw-p 0005c000 08:06 797013     /usr/lib/nss/libnssckbi.so
02941000-02976000 r-xp 00000000 08:06 797017     /usr/lib/nss/libsoftokn3.so
02976000-02977000 r--p 00035000 08:06 797017     /usr/lib/nss/libsoftokn3.so
02977000-02978000 rw-p 00036000 08:06 797017     /usr/lib/nss/libsoftokn3.so
02a68000-02b02000 r-xp 00000000 08:06 802797     /usr/lib/libgio-2.0.so.0.2400.1
02b02000-02b03000 ---p 0009a000 08:06 802797     /usr/lib/libgio-2.0.so.0.2400.1
02b03000-02b04000 r--p 0009a000 08:06 802797     /usr/lib/libgio-2.0.so.0.2400.1
02b04000-02b05000 rw-p 0009b000 08:06 802797     /usr/lib/libgio-2.0.so.0.2400.1
02b05000-02b06000 rw-p 00000000 00:00 0 
02b8e000-02b95000 r-xp 00000000 08:06 791642     /usr/lib/libltdl.so.7.2.1
02b95000-02b96000 r--p 00006000 08:06 791642     /usr/lib/libltdl.so.7.2.1
02b96000-02b97000 rw-p 00007000 08:06 791642     /usr/lib/libltdl.so.7.2.1
03315000-03318000 r-xp 00000000 08:06 791142     /usr/lib/libcanberra-gtk.so.0.1.5
03318000-03319000 r--p 00003000 08:06 791142     /usr/lib/libcanberra-gtk.so.0.1.5
03319000-0331a000 rw-p 00004000 08:06 791142     /usr/lib/libcanberra-gtk.so.0.1.5
03618000-0363f000 r-xp 00000000 08:06 791967     /usr/lib/libvorbis.so.0.4.3
0363f000-03640000 r--p 00026000 08:06 791967     /usr/lib/libvorbis.so.0.4.3
03640000-03641000 rw-p 00027000 08:06 791967     /usr/lib/libvorbis.so.0.4.3
0365f000-03678000 r-xp 00000000 08:06 1838757    /lib/libselinux.so.1
03678000-03679000 r--p 00018000 08:06 1838757    /lib/libselinux.so.1
03679000-0367a000 rw-p 00019000 08:06 1838757    /lib/libselinux.so.1
03c78000-03cbe000 r-xp 00000000 08:06 797012     /usr/lib/nss/libfreebl3.so
03cbe000-03cbf000 r--p 00046000 08:06 797012     /usr/lib/nss/libfreebl3.so
03cbf000-03cc0000 rw-p 00047000 08:06 797012     /usr/lib/nss/libfreebl3.so
03cc0000-03cc4000 rw-p 00000000 00:00 0 
03d7b000-03d83000 r-xp 00000000 08:06 790691     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
03d83000-03d84000 r--p 00007000 08:06 790691     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
03d84000-03d85000 rw-p 00008000 08:06 790691     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
03e3e000-03e95000 r-xp 00000000 08:06 791772     /usr/lib/libpixman-1.so.0.16.4
03e95000-03e97000 r--p 00057000 08:06 791772     /usr/lib/libpixman-1.so.0.16.4
03e97000-03e98000 rw-p 00059000 08:06 791772     /usr/lib/libpixman-1.so.0.16.4
03fc8000-03fcb000 r-xp 00000000 08:06 1838681    /lib/libgpg-error.so.0.4.0
03fcb000-03fcc000 r--p 00002000 08:06 1838681    /lib/libgpg-error.so.0.4.0
03fcc000-03fcd000 rw-p 00003000 08:06 1838681    /lib/libgpg-error.so.0.4.0
041c7000-041ce000 r-xp 00000000 08:06 791971     /usr/lib/libvorbisfile.so.3.3.2
041ce000-041cf000 r--p 00006000 08:06 791971     /usr/lib/libvorbisfile.so.3.3.2
041cf000-041d0000 rw-p 00007000 08:06 791971     /usr/lib/libvorbisfile.so.3.3.2
0475e000-0479e000 r-xp 00000000 08:06 791742     /usr/lib/libpango-1.0.so.0.2800.0
0479e000-0479f000 ---p 00040000 08:06 791742     /usr/lib/libpango-1.0.so.0.2800.0
0479f000-047a0000 r--p 00040000 08:06 791742     /usr/lib/libpango-1.0.so.0.2800.0
047a0000-047a1000 rw-p 00041000 08:06 791742     /usr/lib/libpango-1.0.so.0.2800.0
04ba5000-04bb5000 r-xp 00000000 08:06 1838753    /lib/tls/i686/cmov/libresolv-2.11.1.so
04bb5000-04bb6000 r--p 00010000 08:06 1838753    /lib/tls/i686/cmov/libresolv-2.11.1.so
04bb6000-04bb7000 rw-p 00011000 08:06 1838753    /lib/tls/i686/cmov/libresolv-2.11.1.so
04bb7000-04bb9000 rw-p 00000000 00:00 0 
04f44000-05052000 r-xp 00000000 08:06 791712     /usr/lib/libnss3.so
05052000-05055000 r--p 0010d000 08:06 791712     /usr/lib/libnss3.so
05055000-05057000 rw-p 00110000 08:06 791712     /usr/lib/libnss3.so
050aa000-050b8000 r-xp 00000000 08:06 791144     /usr/lib/libcanberra.so.0.2.1
050b8000-050b9000 r--p 0000d000 08:06 791144     /usr/lib/libcanberra.so.0.2.1
050b9000-050ba000 rw-p 0000e000 08:06 791144     /usr/lib/libcanberra.so.0.2.1
051a2000-051b6000 r-xp 00000000 08:06 791228     /usr/lib/libdirect-1.2.so.0.8.0
051b6000-051b7000 r--p 00013000 08:06 791228     /usr/lib/libdirect-1.2.so.0.8.0
051b7000-051b8000 rw-p 00014000 08:06 791228     /usr/lib/libdirect-1.2.so.0.8.0
0537f000-05383000 r-xp 00000000 08:06 791012     /usr/lib/libXdmcp.so.6.0.0
05383000-05384000 r--p 00003000 08:06 791012     /usr/lib/libXdmcp.so.6.0.0
05384000-05385000 rw-p 00004000 08:06 791012     /usr/lib/libXdmcp.so.6.0.0
0558a000-056ae000 r-xp 00000000 08:06 792014     /usr/lib/libxml2.so.2.7.6
056ae000-056b2000 r--p 00123000 08:06 792014     /usr/lib/libxml2.so.2.7.6
056b2000-056b3000 rw-p 00127000 08:06 792014     /usr/lib/libxml2.so.2.7.6
056b3000-056b4000 rw-p 00000000 00:00 0 
05e73000-05e97000 r-xp 00000000 08:06 1838668    /lib/libexpat.so.1.5.2
05e97000-05e99000 r--p 00024000 08:06 1838668    /lib/libexpat.so.1.5.2
05e99000-05e9a000 rw-p 00026000 08:06 1838668    /lib/libexpat.so.1.5.2
06010000-06013000 r-xp 00000000 08:06 792004     /usr/lib/libxcb-render-util.so.0.0.0
06013000-06014000 r--p 00002000 08:06 792004     /usr/lib/libxcb-render-util.so.0.0.0
06014000-06015000 rw-p 00003000 08:06 792004     /usr/lib/libxcb-render-util.so.0.0.0
060a0000-060a6000 r-xp 00000000 08:06 1838703    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
060a6000-060a7000 r--p 00006000 08:06 1838703    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
060a7000-060a8000 rw-p 00007000 08:06 1838703    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
067b1000-067b9000 r-xp 00000000 08:06 1838717    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
067b9000-067ba000 r--p 00007000 08:06 1838717    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
067ba000-067bb000 rw-p 00008000 08:06 1838717    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
068e5000-06908000 r-xp 00000000 08:06 1838745    /lib/libpng12.so.0.42.0
06908000-06909000 r--p 00022000 08:06 1838745    /lib/libpng12.so.0.42.0
06909000-0690a000 rw-p 00023000 08:06 1838745    /lib/libpng12.so.0.42.0
06a20000-06aa0000 r-xp 00000000 08:06 791899     /usr/lib/libsqlite3.so.0.8.6
06aa0000-06aa1000 r--p 0007f000 08:06 791899     /usr/lib/libsqlite3.so.0.8.6
06aa1000-06aa2000 rw-p 00080000 08:06 791899     /usr/lib/libsqlite3.so.0.8.6
06aa2000-06aa3000 rw-p 00000000 00:00 0 
06d31000-06d57000 r-xp 00000000 08:06 803847     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
06d57000-06d58000 r--p 00025000 08:06 803847     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
06d58000-06d59000 rw-p 00026000 08:06 803847     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
06fe2000-070a5000 r-xp 00000000 08:06 791081     /usr/lib/libasound.so.2.0.0
070a5000-070a9000 r--p 000c2000 08:06 791081     /usr/lib/libasound.so.2.0.0
070a9000-070aa000 rw-p 000c6000 08:06 791081     /usr/lib/libasound.so.2.0.0
071a2000-071a6000 r-xp 00000000 08:06 795358     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
071a6000-071a7000 ---p 00004000 08:06 795358     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
071a7000-071a8000 r--p 00004000 08:06 795358     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
071a8000-071a9000 rw-p 00005000 08:06 795358     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
073b0000-073ba000 r-xp 00000000 08:06 1838707    /lib/tls/i686/cmov/libnss_files-2.11.1.so
073ba000-073bb000 r--p 00009000 08:06 1838707    /lib/tls/i686/cmov/libnss_files-2.11.1.so
073bb000-073bc000 rw-p 0000a000 08:06 1838707    /lib/tls/i686/cmov/libnss_files-2.11.1.so
073bc000-073bd000 ---p 00000000 00:00 0 
073bd000-07bbd000 rwxp 00000000 00:00 0 
08048000-08049000 r-xp 00000000 08:06 795181     /opt/TweetDeck/bin/TweetDeck
08049000-0804a000 rw-p 00000000 08:06 795181     /opt/TweetDeck/bin/TweetDeck
08217000-08224000 r-xp 00000000 08:06 791916     /usr/lib/libtdb.so.1.2.0
08224000-08225000 r--p 0000c000 08:06 791916     /usr/lib/libtdb.so.1.2.0
08225000-08226000 rw-p 0000d000 08:06 791916     /usr/lib/libtdb.so.1.2.0
08318000-0838f000 r-xp 00000000 08:06 791134     /usr/lib/libcairo.so.2.10800.10
0838f000-08391000 r--p 00076000 08:06 791134     /usr/lib/libcairo.so.2.10800.10
08391000-08392000 rw-p 00078000 08:06 791134     /usr/lib/libcairo.so.2.10800.10
084d0000-084e3000 r-xp 00000000 08:06 1838701    /lib/tls/i686/cmov/libnsl-2.11.1.so
084e3000-084e4000 r--p 00012000 08:06 1838701    /lib/tls/i686/cmov/libnsl-2.11.1.so
084e4000-084e5000 rw-p 00013000 08:06 1838701    /lib/tls/i686/cmov/libnsl-2.11.1.so
084e5000-084e7000 rw-p 00000000 00:00 0 
084e7000-084e8000 ---p 00000000 00:00 0 
084e8000-08ce8000 rwxp 00000000 00:00 0 
08f92000-08f98000 r-xp 00000000 08:06 792006     /usr/lib/libxcb-render.so.0.0.0
08f98000-08f99000 r--p 00005000 08:06 792006     /usr/lib/libxcb-render.so.0.0.0
08f99000-08f9a000 rw-p 00006000 08:06 792006     /usr/lib/libxcb-render.so.0.0.0
090bc000-093bb000 rw-p 00000000 00:00 0          [heap]
ab136000-ab1ce000 r--p 00000000 08:06 949281     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
ab1ce000-ab1f1000 r--p 00000000 08:06 525419     /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
ab1f1000-ab272000 rw-p 00000000 00:00 0 
ab6d7000-ab6db000 ---p 00000000 00:00 0 
ab6db000-ab7d7000 rw-p 00000000 00:00 0 
ab7d7000-ab7d8000 ---p 00000000 00:00 0 
ab7d8000-abfd8000 rwxp 00000000 00:00 0 
ac0d8000-ac0f1000 r--p 00000000 08:06 949392     /usr/share/fonts/type1/gsfonts/n021003l.pfb
ac0f1000-ac113000 r--s 00000000 08:06 1087474    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
ac6d5000-ac716000 rw-p 00000000 00:00 0 
b2a0f000-b2a31000 r--p 00000000 08:06 525387     /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
b2a31000-b2a54000 r--p 00000000 08:06 525419     /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
b2a54000-b2ad5000 rw-p 00000000 00:00 0 
b2ad5000-b2ad9000 rw-p 00000000 00:00 0 
b2ad9000-b2adb000 rw-p 00000000 00:00 0 
b3500000-b3561000 rw-p 00000000 00:00 0 
b3561000-b3600000 ---p 00000000 00:00 0 
b3600000-b3601000 r--s 00000000 08:06 1102838    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b3601000-b3602000 r--s 00000000 08:06 1092967    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b3602000-b3608000 r--s 00000000 08:06 1092964    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b3608000-b360a000 r--s 00000000 08:06 1092965    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b360a000-b360d000 r--s 00000000 08:06 1092974    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b360d000-b360e000 r--s 00000000 08:06 1092975    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b360e000-b3611000 r--s 00000000 08:06 1092961    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b3611000-b3612000 r--s 00000000 08:06 1092957    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b3612000-b3613000 r--s 00000000 08:06 1092951    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b3676000-b367a000 r--s 00000000 08:06 1092966    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b367a000-b3681000 r--s 00000000 08:06 1099740    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b3681000-b368c000 r--s 00000000 08:06 1092952    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b368c000-b368f000 r--s 00000000 08:06 1092971    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b368f000-b3697000 r--s 00000000 08:06 1092970    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b3697000-b3698000 ---p 00000000 00:00 0 
b3698000-b3e98000 rwxp 00000000 00:00 0 
b3e98000-b3ef8000 rw-s 00000000 00:04 1933325    /SYSV00000000 (deleted)
b4973000-b6974000 rw-p 00000000 00:00 0 
b6b72000-b6bb5000 rw-p 00000000 00:00 0 
b6bb5000-b6bb8000 ---p 00000000 00:00 0 
b6bb8000-b6bba000 rw-p 00000000 00:00 0 
b6bba000-b6bc0000 ---p 00000000 00:00 0 
b6bc0000-b6bc1000 rw-p 00000000 00:00 0 
b6bc1000-b6cb5000 ---p 00000000 00:00 0 
b6cb5000-b6cb6000 rw-p 00000000 00:00 0 
b6cb6000-b6cf5000 r--p 00000000 08:06 795937     /usr/lib/locale/en_US.utf8/LC_CTYPE
b6cf5000-b6cf6000 r--p 00000000 08:06 795942     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6cf6000-b6cf7000 r--p 00000000 08:06 798661     /usr/lib/locale/en_US.utf8/LC_TIME
b6cf7000-b6e15000 r--p 00000000 08:06 795897     /usr/lib/locale/en_US.utf8/LC_COLLATE
b6e15000-b77c4000 r--p 00000000 08:06 795035     /opt/Adobe AIR/Versions/1.0/Resources/libicudata.so.36
b77c4000-b77c5000 r--p 009ae000 08:06 795035     /opt/Adobe AIR/Versions/1.0/Resources/libicudata.so.36
b77c5000-b77c7000 rw-p 00000000 00:00 0 
b77c7000-b77c8000 r--s 00000000 08:06 1092959    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b77c8000-b77c9000 r--s 00000000 08:06 1092955    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b77c9000-b77cb000 r--s 00000000 08:06 1057464    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b77cb000-b77ce000 r--s 00000000 08:06 1087461    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b77ce000-b77cf000 r--p 00000000 08:06 798662     /usr/lib/locale/en_US.utf8/LC_MONETARY
b77cf000-b77d0000 r--p 00000000 08:06 798663     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b77d0000-b77d1000 r--p 00000000 08:06 795943     /usr/lib/locale/en_US.utf8/LC_PAPER
b77d1000-b77d2000 r--p 00000000 08:06 795902     /usr/lib/locale/en_US.utf8/LC_NAME
b77d2000-b77d3000 r--p 00000000 08:06 798664     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b77d3000-b77d4000 r--p 00000000 08:06 798665     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b77d4000-b77d5000 r--p 00000000 08:06 795900     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b77d5000-b77dc000 r--s 00000000 08:06 802878     /usr/lib/gconv/gconv-modules.cache
b77dc000-b77dd000 r--p 00000000 08:06 798666     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b77dd000-b77df000 rw-p 00000000 00:00 0 
bfca4000-bfcb8000 rwxp 00000000 00:00 0          [stack]
bfcb8000-bfcba000 rw-p 00000000 00:00 0 

========================================= END =========================================

/opt/Adobe AIR/Versions/1.0/libCore.so(+0x2eaf8e) [0x1196f8e]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x2df111) [0x118b111]
[0x147410]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x51b24c) [0x13c724c]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x51bb9c) [0x13c7b9c]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x51bd4d) [0x13c7d4d]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x51bdaf) [0x13c7daf]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x51aadb) [0x13c6adb]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x12a273) [0xfd6273]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x12a2d1) [0xfd62d1]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x12b2fc) [0xfd72fc]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x1291c6) [0xfd51c6]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0xcc744) [0xf78744]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x2e95a2) [0x11955a2]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x2df40b) [0x118b40b]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x81cbb) [0xf2dcbb]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x70023) [0xf1c023]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x70a63) [0xf1ca63]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x70a83) [0xf1ca83]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x70abf) [0xf1cabf]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x70adf) [0xf1cadf]
/lib/tls/i686/cmov/libc.so.6(+0x2f1bf) [0x1771bf]
/lib/tls/i686/cmov/libc.so.6(+0x2f22f) [0x17722f]
/usr/lib/libgdk-x11-2.0.so.0(+0x5ddc1) [0xa02dc1]
/usr/lib/libX11.so.6(_XError+0x109) [0x891299]
/usr/lib/libX11.so.6(+0x4192f) [0x89792f]
/usr/lib/libX11.so.6(_XReply+0x106) [0x897fb6]
/usr/lib/libX11.so.6(XInternAtom+0xaa) [0x87a37a]
/opt/Adobe AIR/Versions/1.0/Resources/libeggtray.so(+0x2152) [0x13b152]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x6b6dcc]
/usr/lib/libgobject-2.0.so.0(+0x98b9) [0x6a78b9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x6a9252]
/usr/lib/libgobject-2.0.so.0(+0x1f23a) [0x6bd23a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754) [0x6bedb4]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6bf256]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xbb) [0x51336b]
/usr/lib/libgtk-x11-2.0.so.0(+0x283bf5) [0x525bf5]
/usr/lib/libgtk-x11-2.0.so.0(+0x16eaac) [0x410aac]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x6b6dcc]
/usr/lib/libgobject-2.0.so.0(+0x98b9) [0x6a78b9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x6a9252]
/usr/lib/libgobject-2.0.so.0(+0x1f23a) [0x6bd23a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754) [0x6bedb4]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6bf256]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_show+0xa2) [0x514432]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x3c1732) [0x126d732]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x3c1a23) [0x126da23]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x33a153) [0x11e6153]
[0xb4340c4f]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x3cf88c) [0x127b88c]
[0xacabf4da]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x423144) [0x12cf144]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x3cf88c) [0x127b88c]
[0xacabf085]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x423144) [0x12cf144]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x3d110f) [0x127d10f]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x3e96e4) [0x12956e4]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x1624c3) [0x100e4c3]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x16289e) [0x100e89e]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x15c89f) [0x100889f]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x15cff1) [0x1008ff1]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x161822) [0x100d822]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x2094c2) [0x10b54c2]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x209fb8) [0x10b5fb8]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x20b898) [0x10b7898]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x238b44) [0x10e4b44]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0xc6c18) [0xf72c18]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x2e6759) [0x1192759]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x2deeee) [0x118aeee]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0xf4a3e) [0xfa0a3e]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0xf4b80) [0xfa0b80]
/lib/libglib-2.0.so.0(+0x3bd5c) [0x7c7d5c]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5) [0x7c75e5]
/lib/libglib-2.0.so.0(+0x3f2d8) [0x7cb2d8]
/lib/libglib-2.0.so.0(g_main_loop_run+0x187) [0x7cb817]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0x3d9309]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x823af) [0xf2e3af]
/opt/Adobe AIR/Versions/1.0/libCore.so(+0x82780) [0xf2e780]
/opt/Adobe AIR/Versions/1.0/libCore.so(AppEntryMain+0xac) [0xf2eb24]
./TweetDeck(main+0xd5) [0x8048859]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x15ebd6]
./TweetDeck(__gxx_personality_v0+0x41) [0x8048701]

```

```
arda@arda-laptop:/opt/TweetDeck/bin$ ./TweetDeck --sync

progname=TweetDeck; RGBA=on
/home/arda/.themes/Darkness (rgba true)/gtk-2.0/gtkrc:80: Murrine configuration option "profile" is no longer supported and will be ignored.
The program 'TweetDeck' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 1284 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Application crashed with an unhandled SIGSEGV
Crashlog has been dumped in /tmp/airCrashLogs/0607_1453_gSMmFl
arda@arda-laptop:/opt/TweetDeck/bin$ 

```

What could cause this ? How can I fix this ?
Cheers,

---

### Post by SoulSmasher on 2010-06-08
*bump* anyone??

---

### Post by SoulSmasher on 2010-06-12
I guess noone knows:/

---

### Post by ghalilk on 2010-11-05
I've just fixed this. That's because you have RGBA support on. It causes many apps to crash. To fix that I created a file called ".profile" (use gedit or another text editor) in my home folder.

This is how it looks:

```
export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:gnome-mplayer:totem:soffice:checkgmail:chromium-browser:exe:TweetDeck
```

Those are examples of apps having problems with RGBA support.
If that doesn't work, try editing/creating this file with a text editor

```
#export GTK_MODULES=rgba
#export GTK_RGBA_APPS=allbut:firefox:firefox-3.5:gksudo:ooffice:soffice:inksca\
#pe:gksu:gtk-recordMyDesktop:kompozer-bin:gpaint:lernid:totem:truecrypt:thunde\
#rbird-bin:thunderbird:checkgmail:gloobus-preview:exe:firefox-bin:swiftfox-bin\
#:gnome-mplayer:gnome-screensaver:google-chrome:chromium-browser:exe:prism-bin:gno\
#me-mplayer:libflashplayer.so:TweetDeck
```

Again, it shows some applications having problems with RGBA. The file you need to create has to be this (as root):

/etc/profile.d/gtkrgba.sh

---

