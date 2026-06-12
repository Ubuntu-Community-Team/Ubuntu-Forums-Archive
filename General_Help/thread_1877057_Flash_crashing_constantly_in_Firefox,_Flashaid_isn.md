---
title: "Flash crashing constantly in Firefox, Flashaid isn't fixing it."
date: 2011-11-07
forum: General Help
---

### Post by brntoki on 2011-11-07
I'm a Flashaid believer and it usually solves all Flash related headaches, but not this time. Ubuntu 11.04 64bit. I notice it with Youtube. I had been/am (I don't know) using the html5 deal in Youtube, but that isn't solving the issue. I'm wondering if it's creating it.

Any ideas what I might look for to fix this very annoying problem???

Thanks.

---

### Post by brntoki on 2011-11-07
Bump.

---

### Post by coldraven on 2011-11-07
I've been having some flash problems in the last few days.
I always use Flashaid but on the BBC news site some videos will not play.
They work for about 10 secs then stop although the progress bar continues as normal.
Using Flashaid I've tried installing the 32 or 64 bit versions to no effect.
It seems to be a Flash or BBC problem and is getting better, most videos work now.

---

### Post by compiz addict on 2011-11-07
Somebody correct my if I'm wrong, but I believe YouTube's HTML5 player doesn't use any flash whatsoever, so if would be completely unrelated to flash and would explain why Flashaid wont solve the problem. If nobody can give you a better solution, you should consider using Google Chrome/Chromium and see if that works.

---

### Post by brntoki on 2011-11-07
Giving this a shot. Don't know why I haven't already. Not enough caffeine, I suppose. But, my reason for saying Flash is crashing is because, well, Flash is crashing, and telling me that it's doing it with the little Lego thingy asking me if I want to report it.




> **compiz addict said:**
> Somebody correct my if I'm wrong, but I believe YouTube's HTML5 player doesn't use any flash whatsoever, so if would be completely unrelated to flash and would explain why Flashaid wont solve the problem. If nobody can give you a better solution, you should consider using Google Chrome/Chromium and see if that works.

---

### Post by brntoki on 2011-11-08
No dice. Same problem.

---

### Post by brntoki on 2011-11-08
Bump again.

---

### Post by lovinglinux on 2011-11-09
Please generate a report through Flash-Aid Help menu and post here.

BTW, I need to update Flash-Aid to deal with the *flashplugin-downloader* package in Oneiric. I will try to do this tomorrow.

---

### Post by brntoki on 2011-11-10
Here you go. Thanks for any help you can give.




```
Ubuntu Architecture

Linux brent-P35-DS3L 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:27:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install
firefox-locale-ja				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-7.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

caffeine-developers-ppa-natty.list
caffeine-developers-ppa-natty.list.save
medibuntu.list
medibuntu.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.save
ubuntu-wine-ppa-natty.list
ubuntu-wine-ppa-natty.list.save

Flash packages

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86-gcc3:$

[PLUGINS]

[INVALID]
/usr/lib/mozilla/plugins/libvlcplugin.so:$
1302784555000:$
/usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so:$
1300984376000:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
1298508273000:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
1289952613000:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
1277465636000:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
1274282974000:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
1274282974000:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
1274282974000:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
1274282974000:$
/opt/google/picasa/3.0/lib/npPicasa3.so:$
1226106226000:$
Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
npwrapper.nppdf.so:$
/usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so:$
:$
1318650868000:1:5:$
The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser. :$
Adobe Reader 9.4:$
5
0:application/pdf:Portable Document Format:pdf:$
1:application/vnd.fdf:Acrobat Forms Data Format:fdf:$
2:application/vnd.adobe.xfdf:XML Version of Acrobat Forms Data Format:xfdf:$
3:application/vnd.adobe.xdp+xml:Acrobat XML Data Package:xdp:$
4:application/vnd.adobe.xfd+xml:Adobe FormFlow99 Data File:xfd:$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1318377712000:1:1:$
Shockwave Flash 11.2 d202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1311152095000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1300218622000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime Movie:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.32.0):$
20
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:Movie Clip:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
mozplugger.so:$
/usr/lib/mozilla/plugins/mozplugger.so:$
1.14.3:$
1299402944000:1:5:$
MozPlugger version 1.14.3, maintained by Louis Bavoil and Peter Leese, a fork of plugger written by Fredrik H&uuml;binette.<br>For documentation on how to configure mozplugger, check the man page. (type <tt>man&nbsp;mozplugger</tt>) <table>  <tr><td>Configuration file:</td><td>/etc/mozpluggerrc</td></tr>  <tr><td>Helper binary:</td><td>mozplugger-helper</td></tr>  <tr><td>Controller binary:</td><td>mozplugger-controller</td></tr>  <tr><td>Link launcher binary:</td><td>mozplugger-linker</td></tr>  <tr><td>Debug file:</td><td>$HOME/tmp/mozdebug</td></tr>  </table> <br clear=all>:$
MozPlugger 1.14.3 handles QuickTime and Windows Media Player Plugin:$
99
0:video/mpeg:MPEG animation:mpeg,mpg,mpe:$
1:video/x-mpeg:MPEG animation:mpeg,mpg,mpe:$
2:video/x-mpeg2:MPEG2 animation:mpv2,mp2ve:$
3:video/mp4:MPEG4 animation:mp4:$
4:video/msvideo:AVI animation:avi:$
5:video/x-msvideo:AVI animation:avi:$
6:video/fli:FLI animation:fli,flc:$
7:video/x-fli:FLI animation:fli,flc:$
8:application/x-mplayer2:Windows Media video:*:$
9:video/x-ms-asf:Windows Media video:asf,asx:$
10:video/x-ms-wm:Windows Media video:wm:$
11:video/x-ms-wmv:Windows Media video:wmv:$
12:video/x-ms-wvx:Windows Media video:wvx:$
13:video/x-ms-asf-plugin:Window Media video:*:$
14:application/asx:Windows Media video:asx:$
15:application/x-quicktimeplayer:Quicktime animation:mov:$
16:image/x-macpaint:Quicktime animation:pntg,mov:$
17:video/quicktime:Quicktime animation:mov,qt:$
18:video/x-quicktime:Quicktime animation:mov,qt:$
19:video/x-theora:OGG stream with video:ogg:$
20:video/theora:OGG stream with video:ogg:$
21:video/ogg:OGG stream with video:ogg:$
22:video/x-ogg:OGG stream with video:ogm,ogv:$
23:audio/mp3:MPEG audio:mp3:$
24:audio/x-mp3:MPEG audio:mp3:$
25:audio/mpeg2:MPEG audio:mp2:$
26:audio/x-mpeg2:MPEG audio:mp2:$
27:audio/mpeg3:MPEG audio:mp3:$
28:audio/x-mpeg3:MPEG audio:mp3:$
29:audio/mpeg:MPEG audio:mpa,abs,mpega:$
30:audio/x-mpeg:MPEG audio:mpa,abs,mpega:$
31:audio/x-ogg:OGG audio:ogg:$
32:application/x-ogg:OGG audio:ogg:$
33:application/ogg:OGG audio:ogg:$
34:audio/x-flac:FLAC audio:flac:$
35:application/x-flac:FLAC audio:flac:$
36:audio/x-ms-wax:Windows Media Audio:wax:$
37:audio/x-ms-wma:Windows Media Audio:wma:$
38:image/sun-raster:SUN raster image:rs:$
39:image/x-sun-raster:SUN raster image:rs:$
40:image/x-rgb:RGB Image:rgb:$
41:image/x-portable-pixmap:PPM Image:ppm:$
42:image/x-portable-graymap:PGM Image:pgm:$
43:image/x-portable-bitmap:PBM Image:pbm:$
44:image/x-portable-anymap:PBM Image:pnm:$
45:image/tiff:TIFF image:tiff,tif:$
46:image/x-tiff:TIFF image:tiff,tif:$
47:image/x-xcf:Gimp Image:xcf:$
48:image/xcf:Gimp Image:xcf:$
49:application/x-gimp:Gimp Image:xcf:$
50:application/gimp:Gimp Image:xcf:$
51:application/photoshop:PhotoShop Image:psd:$
52:application/x-photoshop:PhotoShop Image:psd:$
53:application/pdf:PDF file:pdf:$
54:application/x-pdf:PDF file:pdf:$
55:text/pdf:PDF file:pdf:$
56:text/x-pdf:PDF file:pdf:$
57:application/x-dvi:DVI file:dvi:$
58:application/x-postscript:PostScript file:ps:$
59:application/postscript:PostScript file:ps:$
60:application/x-rtf:Rich Text Format:rtf:$
61:application/rtf:Rich Text Format:rtf:$
62:text/rtf:Rich Text Format:rtf:$
63:application/x-msword:Microsoft Word Document:doc,dot:$
64:application/msword:Microsoft Word Document:doc,dot:$
65:application/vnd.ms-excel:Microsoft Excel Document:xls,xlb:$
66:application/vnd.sun.xml.writer:OpenOffice Writer 6.0 documents:sxw:$
67:application/so7_vnd.sun.xml.writer:OpenOffice Writer 7.0 documents:sxw:$
68:application/vnd.sun.xml.writer.template:OpenOffice Writer 6.0 templates:stw:$
69:application/vnd.sun.xml.writer.global:OpenOffice Writer 6.0 global documents:sxg:$
70:application/vnd.stardivision.writer:StarWriter 5.x documents:sdw:$
71:application/vnd.stardivision.writer-global:StarWriter 5.x global documents:sgl:$
72:application/x-starwriter:StarWriter 4.x documents:sdw:$
73:application/vnd.sun.xml.calc:OpenOffice Calc 6.0 spreadsheets:sxc:$
74:application/so7_vnd.sun.xml.calc:OpenOffice Calc 7.0 spreadsheets:sxc:$
75:application/vnd.sun.xml.calc.template:OpenOffice Calc 6.0 templates:stc:$
76:application/vnd.stardivision.calc:StarCalc 5.x spreadsheets:sdc:$
77:application/x-starcalc:StarCalc 4.x spreadsheets:sdc:$
78:application/vnd.lotus-1-2-3: Lotus 1-2-3 Document: 123, wk1:$
79:application/vnd.sun.xml.draw:OpenOffice Draw 6.0 documents:sxd:$
80:application/so7_vnd.sun.xml.draw:StarOffice Draw 7.0 documents:sxc:$
81:application/vnd.sun.xml.draw.template:OpenOffice Draw 6.0 templates:std:$
82:application/vnd.stardivision.draw:StarDraw 5.x documents:sda:$
83:application/x-stardraw:StarDraw 4.x documents:sda:$
84:application/vnd.sun.xml.impress:OpenOffice Impress 6.0 presentations:sxi:$
85:application/so7_vnd.sun.xml.impress:StarOffice 7.0 Impress presentations:sxi:$
86:application/vnd.sun.xml.impress.template:OpenOffice Impress 6.0 templates:sti:$
87:application/vnd.stardivision.impress:StarImpress 5.x presentations:sdd:$
88:application/vnd.stardivision.impress-packed:StarImpress Packed 5.x files:sdp:$
89:application/x-starimpress:StarImpress 4.x presentations:sdd:$
90:application/vnd.ms-powerpoint:PowerPoint Slideshow:ppt:$
91:application/mspowerpoint:PowerPoint Slideshow:ppt,ppz,pps,pot:$
92:application/vnd.sun.xml.math:OpenOffice Math 6.0 documents:sxm:$
93:application/so7_vnd.sun.xml.math:StarOffice 7.0 Math documents:sxm:$
94:application/vnd.stardivision.math:StarMath 5.x documents:smf:$
95:application/x-starmath:StarMath 4.x documents:smf:$
96:application/vnd.oasis.opendocument.text:OASIS OpenDocument Text:odt,ODT:$
97:application/vnd.oasis.opendocument.spreadsheet:OASIS OpenDocument SpreadSheet:ods,ODS:$
98:application/vnd.oasis.opendocument.presentation:OASIS OpenDocument Presentation:odp,ODP:$

[INVALID]

```

---

### Post by lovinglinux on 2011-11-10
> **brntoki said:**
> Here you go. Thanks for any help you can give.

I see nothing wrong in your report. I suppose the problem is with the flash version. I have seen some bad comments about the latest version.

If you have a nVidia card, disable HWVideo decode in Flash-Aid tweaking options and install flash again trough it. If not, try to disable GPU override.

---

### Post by flipper T on 2011-11-10
the BBC received a lot of complaints 2 days ago about flash not working.

they contacted adobe, and the problem turned out to be that for the 64 bit version of flash, the buffer had been set to zero. 

adobe fixed this, but i don´t know if they also fixed this for linux 64bit.

if you are having these problems, try using flash aid to install the 32bit version of flash.

this worked for me. 

as always, your experience may vary.

---

### Post by BillyBoa on 2011-11-10
The usual workaround is to use Chrome. I had constant flash crashes in Firefox but none problem in Chrome so far.

---

### Post by brntoki on 2011-11-10
Thanks everyone. I'm testing by running a playlist in YouTube after trying lovinlinux' suggestions. Will report back.

---

### Post by brntoki on 2011-11-10
Okay! It appears to be just as I thought. Lovinglinux is a certified genius!

Disabling the HWVideo decode option and running Flash-Aid again fixed it. So far, I think the only thing that Flash-Aid hasn't fixed for me is breakfast. Could you get to work on that lovinglinux?

Many thanks! Now I can resume my regularly scheduled programming of scanning, editing, and printing with some good YouTube playlists keeping me "in the mood". Awesome!




> **lovinglinux said:**
> I see nothing wrong in your report. I suppose the problem is with the flash version. I have seen some bad comments about the latest version.

If you have a nVidia card, disable HWVideo decode in Flash-Aid tweaking options and install flash again trough it. If not, try to disable GPU override.

---

### Post by lovinglinux on 2011-11-11
> **brntoki said:**
> Okay! It appears to be just as I thought. Lovinglinux is a certified genius!

Disabling the HWVideo decode option and running Flash-Aid again fixed it. So far, I think the only thing that Flash-Aid hasn't fixed for me is breakfast. Could you get to work on that lovinglinux?

Many thanks! Now I can resume my regularly scheduled programming of scanning, editing, and printing with some good YouTube playlists keeping me "in the mood". Awesome!

I am glad the problem is over. I will add a "Bacon Button" in the next version. :-)

---

### Post by craig100 on 2011-11-14
I use Google Chrome as well and Flash crashes it too. I'm on a massive machine with Ubuntu 10.10 x64 and nVidia card. I use the Firefox FlashAid to install Flash. It crashes on both Chrome 15 and FF 7. Will be moving to Mint 12 when it's out so maybe that will fix it.

---

### Post by arindambiswas on 2012-01-26
Have been struggling with this for the past 3 days now. Flash reports being installed on both Chrome and Firefox but no embeds render. :-(

Your help is greatly appreciated.

```
Ubuntu Architecture

Linux arindamb 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-locale-bn				install
firefox-locale-en				install
firefox-locale-hi				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-9.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

adilson-experimental-oneiric.list
adilson-experimental-oneiric.list.save
alexmurray-indicator-sensors-oneiric.list
alexmurray-indicator-sensors-oneiric.list.save
amandeepgrewal-notifyosdconfig-maverick.list.save
am-monkeyd-nautilus-elementary-ppa-maverick.list
am-monkeyd-nautilus-elementary-ppa-maverick.list.distUpgrade
am-monkeyd-nautilus-elementary-ppa-maverick.list.save
awn-testing-ppa-maverick.list
awn-testing-ppa-maverick.list.distUpgrade
awn-testing-ppa-maverick.list.save
bigwhale-kazam-oneric-oneiric.list
bigwhale-kazam-oneric-oneiric.list.save
bisigi-ppa-maverick.list
bisigi-ppa-maverick.list.distUpgrade
bisigi-ppa-maverick.list.save
blueman-ppa-maverick.list
blueman-ppa-maverick.list.distUpgrade
blueman-ppa-maverick.list.save
clicompanion-devs-clicompanion-nightlies-maverick.list
clicompanion-devs-clicompanion-nightlies-maverick.list.distUpgrade
clicompanion-devs-clicompanion-nightlies-maverick.list.save
damnvid-ppa-maverick.list
damnvid-ppa-maverick.list.distUpgrade
damnvid-ppa-maverick.list.save
david4dev-qr-maverick.list
david4dev-qr-maverick.list.distUpgrade
david4dev-qr-maverick.list.save
disper-dev-ppa-oneiric.list
disper-dev-ppa-oneiric.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
geod-ppa-geod-maverick.list
geod-ppa-geod-maverick.list.distUpgrade
geod-ppa-geod-maverick.list.save
goehle-goehle-ppa-maverick.list
goehle-goehle-ppa-maverick.list.distUpgrade
goehle-goehle-ppa-maverick.list.save
goehle-goehle-ppasudo-maverick.list
goehle-goehle-ppasudo-maverick.list.distUpgrade
goehle-goehle-ppasudo-maverick.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google.list
google.list.distUpgrade
google.list.save
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
hplip-isv-ppa-natty.list
hplip-isv-ppa-natty.list.distUpgrade
hplip-isv-ppa-natty.list.save
indicator-multiload-stable-daily-oneiric.list
indicator-multiload-stable-daily-oneiric.list.save
janousek_jiri-google-music-frame-daily-oneiric.list
janousek_jiri-google-music-frame-daily-oneiric.list.save
jconti-recent-notifications-maverick.list
jconti-recent-notifications-maverick.list.distUpgrade
jconti-recent-notifications-maverick.list.save
jfi-psensor-unstable-oneiric.list
jfi-psensor-unstable-oneiric.list.save
jonoomph-openshot-edge-maverick.list
jonoomph-openshot-edge-maverick.list.distUpgrade
jonoomph-openshot-edge-maverick.list.save
keks9n-main-natty.list
keks9n-main-natty.list.distUpgrade
keks9n-main-natty.list.save
kilian-f_lux-oneiric.list
kilian-f_lux-oneiric.list.save
kokoto-java-usu-extras-maverick.list
kokoto-java-usu-extras-maverick.list.distUpgrade
kokoto-java-usu-extras-maverick.list.save
leolik-leolik-maverick.list
leolik-leolik-maverick.list.distUpgrade
leolik-leolik-maverick.list.save
librecad-dev-librecad-daily-oneiric.list
librecad-dev-librecad-daily-oneiric.list.save
libreoffice-ppa-maverick.list
libreoffice-ppa-maverick.list.distUpgrade
libreoffice-ppa-maverick.list.save
libreoffice-ppa-natty.list
libreoffice-ppa-natty.list.distUpgrade
libreoffice-ppa-natty.list.save
libreplan-ppa-oneiric.list
libreplan-ppa-oneiric.list.save
lkjoel-flash-doctor-oneiric.list
lkjoel-flash-doctor-oneiric.list.save
loell-ppa-oneiric.list
loell-ppa-oneiric.list.save
manu-tm-newsrssticker-natty.list
manu-tm-newsrssticker-natty.list.distUpgrade
manu-tm-newsrssticker-natty.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
mj-casalogic-ironhide-oneiric.list
mj-casalogic-ironhide-oneiric.list.save
mozillateam-firefox-stable-maverick.list
mozillateam-firefox-stable-maverick.list.distUpgrade
mozillateam-firefox-stable-maverick.list.save
nikount-orta-desktop-natty.list
nikount-orta-desktop-natty.list.distUpgrade
nikount-orta-desktop-natty.list.save
nilarimogard-webupd8-maverick.list
nilarimogard-webupd8-maverick.list.distUpgrade
nilarimogard-webupd8-maverick.list.save
nuovodna-nuovodna-stuff-maverick.list
nuovodna-nuovodna-stuff-maverick.list.distUpgrade
nuovodna-nuovodna-stuff-maverick.list.save
nvidia-vdpau-ppa-natty.list
nvidia-vdpau-ppa-natty.list.distUpgrade
nvidia-vdpau-ppa-natty.list.save
openbravo-isv-ppa-maverick.list
openbravo-isv-ppa-maverick.list.distUpgrade
openbravo-isv-ppa-maverick.list.save
opera.list
osmoma-audio-recorder-maverick.list
osmoma-audio-recorder-maverick.list.distUpgrade
osmoma-audio-recorder-maverick.list.save
osmoma-audio-recorder-oneiric.list
osmoma-audio-recorder-oneiric.list.save
rabbitvcs-ppa-maverick.list
rabbitvcs-ppa-maverick.list.distUpgrade
rabbitvcs-ppa-maverick.list.save
ricotz-docky-maverick.list
ricotz-docky-maverick.list.distUpgrade
ricotz-docky-maverick.list.save
sevenmachines-flash-maverick.list
sevenmachines-flash-maverick.list.distUpgrade
sevenmachines-flash-maverick.list.save
sevenmachines-flash-natty.list
sevenmachines-flash-natty.list.distUpgrade
sevenmachines-flash-natty.list.save
sevenmachines-flash-oneiric.list
shiki-mediainfo-natty.list
shiki-mediainfo-natty.list.distUpgrade
shiki-mediainfo-natty.list.save
shnatsel-flashfreeze-oneiric.list
shnatsel-flashfreeze-oneiric.list.save
stebbins-handbrake-releases-maverick.list
stebbins-handbrake-releases-maverick.list.distUpgrade
stebbins-handbrake-releases-maverick.list.save
stebbins-handbrake-releases-natty.list
stebbins-handbrake-releases-natty.list.distUpgrade
stebbins-handbrake-releases-natty.list.save
stebbins-handbrake-snapshots-maverick.list
stebbins-handbrake-snapshots-maverick.list.distUpgrade
stebbins-handbrake-snapshots-maverick.list.save
stedy6-stedy-minidna-natty.list
stedy6-stedy-minidna-natty.list.distUpgrade
stedy6-stedy-minidna-natty.list.save
team-xbmc-ppa-natty.list
team-xbmc-ppa-natty.list.distUpgrade
team-xbmc-ppa-natty.list.save
team-xbmc-unstable-natty.list
team-xbmc-unstable-natty.list.distUpgrade
team-xbmc-unstable-natty.list.save
time-drive-devel-stable-maverick.list
time-drive-devel-stable-maverick.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.distUpgrade
tualatrix-ppa-maverick.list.save
ubuntu-tweak-stable.list.save
ubuntu-wine-ppa-maverick.list
ubuntu-wine-ppa-maverick.list.distUpgrade
ubuntu-wine-ppa-maverick.list.save
ubuntu-x-swat-x-updates-maverick.list
ubuntu-x-swat-x-updates-maverick.list.distUpgrade
ubuntu-x-swat-x-updates-maverick.list.save
ubuntu-x-swat-x-updates-oneiric.list
ubuntu-x-swat-x-updates-oneiric.list.save
webupd8team-gnome3-oneiric.list
webupd8team-gnome3-oneiric.list.save
webupd8team-gtk-recordmydesktop-maverick.list.save
webupd8team-haguichi-maverick.list
webupd8team-haguichi-maverick.list.distUpgrade
webupd8team-haguichi-maverick.list.save
webupd8team-jupiter-oneiric.list
webupd8team-jupiter-oneiric.list.save
webupd8team-y-ppa-manager-maverick.list
webupd8team-y-ppa-manager-maverick.list.distUpgrade
webupd8team-y-ppa-manager-maverick.list.save
wfg-0ad-maverick.list
wfg-0ad-maverick.list.distUpgrade
wfg-0ad-maverick.list.save
xorg-edgers-ppa-natty.list
xorg-edgers-ppa-natty.list.distUpgrade
xorg-edgers-ppa-natty.list.save
xorg-edgers-ppa-oneiric.list
xorg-edgers-ppa-oneiric.list.save
zeitgeist-sharp-daily-maverick.list
zeitgeist-sharp-daily-maverick.list.distUpgrade
zeitgeist-sharp-daily-maverick.list.save

Flash packages

adobe-flash-properties-gtk			install
adobe-flashplugin				install
com.iflashlord.mochidecrypt			install
flashfreeze					install
Plugin locations

/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/player/10.2/lnx/libflashplayer.so
/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.1.0.16076/runtimes/player/10/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.1.0.16076/runtimes/player/10.1/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.0.18623/__MACOSX/flex_sdk_4.5.0.18623/runtimes/player/10.2/lnx/._libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.0.18623/flex_sdk_4.5.0.18623/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/player/10.2/lnx/libflashplayer.so
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Downloads/ACROBEDIA/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/AIR/AdobeAIRSDK/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/flashplayer_10_plugin_debug/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/player/flashplayer10-3_b2_debug_lin_033111/libflashplayer.so
/home/arindam/Downloads/tmp/flashplayer11-2_p4_install_lin_64_011912/libflashplayer.so
/home/arindam/tmp/libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so.BAK
/usr/share/ubufox/plugins/libflashplayer.so.BD


Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1326484954000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1326079387000:1:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
libgnome-shell-browser-plugin.so:$
/usr/lib/mozilla/plugins/libgnome-shell-browser-plugin.so:$
:$
1324368571000:1:5:$
This plugin provides integration with Gnome Shell for live extension enabling and disabling. It can be used only by extensions.gnome.org:$
Gnome Shell Integration:$
1
0:application/x-gnome-shell-integration:Gnome Shell Integration Dummy Content-Type::$
libnpsoplugin.so:$
/usr/lib/libreoffice/program/libnpsoplugin.so:$
:$
1321272902000:1:5:$
OpenOffice.org Plug-in handles all its documents:$
OpenOffice.org Plug-in:$
30
0:application/vnd.stardivision.calc:StarCalc 3.0 - 5.0:sdc:$
1:application/vnd.stardivision.chart:StarChart 3.0 - 5.0:sds:$
2:application/vnd.stardivision.draw:StarDraw 3.0 - 5.0:sda:$
3:application/vnd.stardivision.impress:StarImpress 3.0 - 5.0:sdd:$
4:application/vnd.stardivision.impress-packed:StarImpress-packed 3.0 - 5.0:sdp:$
5:application/vnd.stardivision.math:StarMath 3.0 - 5.0:smf:$
6:application/vnd.stardivision.writer:StarWriter Template 3.0 - 5.0:vor:$
7:application/vnd.stardivision.writer-global:StarWriter Global 3.0 - 5.0:sgl:$
8:application/vnd.staroffice.writer:StarWriter 3.0 - 5.0:sdw:$
9:application/vnd.sun.xml.calc:StarOffice 6.0/7 Spreadsheet:sxc:$
10:application/vnd.sun.xml.calc.template:StarOffice 6.0/7 Spreadsheet Template:stc:$
11:application/vnd.sun.xml.draw:StarOffice 6.0/7 Drawing:sxd:$
12:application/vnd.sun.xml.draw.template:StarOffice 6.0/7 Drawing Template:std:$
13:application/vnd.sun.xml.impress:StarOffice 6.0/7 Presentation:sxi:$
14:application/vnd.sun.xml.impress.template:StarOffice 6.0/7 Presentation Template:sti:$
15:application/vnd.sun.xml.math:StarOffice 6.0/7 Formula:sxm:$
16:application/vnd.sun.xml.writer:StarOffice 6.0/7 Text Document:sxw:$
17:application/vnd.sun.xml.writer.global:StarOffice 6.0/7 Master Document:sxg:$
18:application/vnd.sun.xml.writer.template:StarOffice 6.0/7 Text Document Template:stw:$
19:application/vnd.oasis.opendocument.text:OpenDocument Text:odt:$
20:application/vnd.oasis.opendocument.text-template:OpenDocument Text Template:ott:$
21:application/vnd.oasis.opendocument.text-master:OpenDocument Master Document:odm:$
22:application/vnd.oasis.opendocument.text-web:HTML Document Template:oth:$
23:application/vnd.oasis.opendocument.spreadsheet:OpenDocument Spreadsheet:ods:$
24:application/vnd.oasis.opendocument.spreadsheet-template:OpenDocument Spreadsheet Template:ots:$
25:application/vnd.oasis.opendocument.graphics:OpenDocument Drawing:odg:$
26:application/vnd.oasis.opendocument.graphics-template:OpenDocument Drawing Template:otg:$
27:application/vnd.oasis.opendocument.presentation:OpenDocument Presentation:odp:$
28:application/vnd.oasis.opendocument.presentation-template:OpenDocument Presentation Template:otp:$
29:application/vnd.oasis.opendocument.formula:OpenDocument Formula:odf:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1320721707000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 3.0.1):$
21
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
20:audio/midi:MIDI audio:mid, midi:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1318915705000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$

[INVALID]
/usr/lib/mozilla/plugins/flashplugin-alternative.so:$
0:$
```

---

### Post by lovinglinux on 2012-01-27
> **arindambiswas said:**
> Have been struggling with this for the past 3 days now. Flash reports being installed on both Chrome and Firefox but no embeds render. :-(

Your help is greatly appreciated.

```
Ubuntu Architecture

Linux arindamb 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-locale-bn				install
firefox-locale-en				install
firefox-locale-hi				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-9.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

adilson-experimental-oneiric.list
adilson-experimental-oneiric.list.save
alexmurray-indicator-sensors-oneiric.list
alexmurray-indicator-sensors-oneiric.list.save
amandeepgrewal-notifyosdconfig-maverick.list.save
am-monkeyd-nautilus-elementary-ppa-maverick.list
am-monkeyd-nautilus-elementary-ppa-maverick.list.distUpgrade
am-monkeyd-nautilus-elementary-ppa-maverick.list.save
awn-testing-ppa-maverick.list
awn-testing-ppa-maverick.list.distUpgrade
awn-testing-ppa-maverick.list.save
bigwhale-kazam-oneric-oneiric.list
bigwhale-kazam-oneric-oneiric.list.save
bisigi-ppa-maverick.list
bisigi-ppa-maverick.list.distUpgrade
bisigi-ppa-maverick.list.save
blueman-ppa-maverick.list
blueman-ppa-maverick.list.distUpgrade
blueman-ppa-maverick.list.save
clicompanion-devs-clicompanion-nightlies-maverick.list
clicompanion-devs-clicompanion-nightlies-maverick.list.distUpgrade
clicompanion-devs-clicompanion-nightlies-maverick.list.save
damnvid-ppa-maverick.list
damnvid-ppa-maverick.list.distUpgrade
damnvid-ppa-maverick.list.save
david4dev-qr-maverick.list
david4dev-qr-maverick.list.distUpgrade
david4dev-qr-maverick.list.save
disper-dev-ppa-oneiric.list
disper-dev-ppa-oneiric.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
geod-ppa-geod-maverick.list
geod-ppa-geod-maverick.list.distUpgrade
geod-ppa-geod-maverick.list.save
goehle-goehle-ppa-maverick.list
goehle-goehle-ppa-maverick.list.distUpgrade
goehle-goehle-ppa-maverick.list.save
goehle-goehle-ppasudo-maverick.list
goehle-goehle-ppasudo-maverick.list.distUpgrade
goehle-goehle-ppasudo-maverick.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google.list
google.list.distUpgrade
google.list.save
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
hplip-isv-ppa-natty.list
hplip-isv-ppa-natty.list.distUpgrade
hplip-isv-ppa-natty.list.save
indicator-multiload-stable-daily-oneiric.list
indicator-multiload-stable-daily-oneiric.list.save
janousek_jiri-google-music-frame-daily-oneiric.list
janousek_jiri-google-music-frame-daily-oneiric.list.save
jconti-recent-notifications-maverick.list
jconti-recent-notifications-maverick.list.distUpgrade
jconti-recent-notifications-maverick.list.save
jfi-psensor-unstable-oneiric.list
jfi-psensor-unstable-oneiric.list.save
jonoomph-openshot-edge-maverick.list
jonoomph-openshot-edge-maverick.list.distUpgrade
jonoomph-openshot-edge-maverick.list.save
keks9n-main-natty.list
keks9n-main-natty.list.distUpgrade
keks9n-main-natty.list.save
kilian-f_lux-oneiric.list
kilian-f_lux-oneiric.list.save
kokoto-java-usu-extras-maverick.list
kokoto-java-usu-extras-maverick.list.distUpgrade
kokoto-java-usu-extras-maverick.list.save
leolik-leolik-maverick.list
leolik-leolik-maverick.list.distUpgrade
leolik-leolik-maverick.list.save
librecad-dev-librecad-daily-oneiric.list
librecad-dev-librecad-daily-oneiric.list.save
libreoffice-ppa-maverick.list
libreoffice-ppa-maverick.list.distUpgrade
libreoffice-ppa-maverick.list.save
libreoffice-ppa-natty.list
libreoffice-ppa-natty.list.distUpgrade
libreoffice-ppa-natty.list.save
libreplan-ppa-oneiric.list
libreplan-ppa-oneiric.list.save
lkjoel-flash-doctor-oneiric.list
lkjoel-flash-doctor-oneiric.list.save
loell-ppa-oneiric.list
loell-ppa-oneiric.list.save
manu-tm-newsrssticker-natty.list
manu-tm-newsrssticker-natty.list.distUpgrade
manu-tm-newsrssticker-natty.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
mj-casalogic-ironhide-oneiric.list
mj-casalogic-ironhide-oneiric.list.save
mozillateam-firefox-stable-maverick.list
mozillateam-firefox-stable-maverick.list.distUpgrade
mozillateam-firefox-stable-maverick.list.save
nikount-orta-desktop-natty.list
nikount-orta-desktop-natty.list.distUpgrade
nikount-orta-desktop-natty.list.save
nilarimogard-webupd8-maverick.list
nilarimogard-webupd8-maverick.list.distUpgrade
nilarimogard-webupd8-maverick.list.save
nuovodna-nuovodna-stuff-maverick.list
nuovodna-nuovodna-stuff-maverick.list.distUpgrade
nuovodna-nuovodna-stuff-maverick.list.save
nvidia-vdpau-ppa-natty.list
nvidia-vdpau-ppa-natty.list.distUpgrade
nvidia-vdpau-ppa-natty.list.save
openbravo-isv-ppa-maverick.list
openbravo-isv-ppa-maverick.list.distUpgrade
openbravo-isv-ppa-maverick.list.save
opera.list
osmoma-audio-recorder-maverick.list
osmoma-audio-recorder-maverick.list.distUpgrade
osmoma-audio-recorder-maverick.list.save
osmoma-audio-recorder-oneiric.list
osmoma-audio-recorder-oneiric.list.save
rabbitvcs-ppa-maverick.list
rabbitvcs-ppa-maverick.list.distUpgrade
rabbitvcs-ppa-maverick.list.save
ricotz-docky-maverick.list
ricotz-docky-maverick.list.distUpgrade
ricotz-docky-maverick.list.save
sevenmachines-flash-maverick.list
sevenmachines-flash-maverick.list.distUpgrade
sevenmachines-flash-maverick.list.save
sevenmachines-flash-natty.list
sevenmachines-flash-natty.list.distUpgrade
sevenmachines-flash-natty.list.save
sevenmachines-flash-oneiric.list
shiki-mediainfo-natty.list
shiki-mediainfo-natty.list.distUpgrade
shiki-mediainfo-natty.list.save
shnatsel-flashfreeze-oneiric.list
shnatsel-flashfreeze-oneiric.list.save
stebbins-handbrake-releases-maverick.list
stebbins-handbrake-releases-maverick.list.distUpgrade
stebbins-handbrake-releases-maverick.list.save
stebbins-handbrake-releases-natty.list
stebbins-handbrake-releases-natty.list.distUpgrade
stebbins-handbrake-releases-natty.list.save
stebbins-handbrake-snapshots-maverick.list
stebbins-handbrake-snapshots-maverick.list.distUpgrade
stebbins-handbrake-snapshots-maverick.list.save
stedy6-stedy-minidna-natty.list
stedy6-stedy-minidna-natty.list.distUpgrade
stedy6-stedy-minidna-natty.list.save
team-xbmc-ppa-natty.list
team-xbmc-ppa-natty.list.distUpgrade
team-xbmc-ppa-natty.list.save
team-xbmc-unstable-natty.list
team-xbmc-unstable-natty.list.distUpgrade
team-xbmc-unstable-natty.list.save
time-drive-devel-stable-maverick.list
time-drive-devel-stable-maverick.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.distUpgrade
tualatrix-ppa-maverick.list.save
ubuntu-tweak-stable.list.save
ubuntu-wine-ppa-maverick.list
ubuntu-wine-ppa-maverick.list.distUpgrade
ubuntu-wine-ppa-maverick.list.save
ubuntu-x-swat-x-updates-maverick.list
ubuntu-x-swat-x-updates-maverick.list.distUpgrade
ubuntu-x-swat-x-updates-maverick.list.save
ubuntu-x-swat-x-updates-oneiric.list
ubuntu-x-swat-x-updates-oneiric.list.save
webupd8team-gnome3-oneiric.list
webupd8team-gnome3-oneiric.list.save
webupd8team-gtk-recordmydesktop-maverick.list.save
webupd8team-haguichi-maverick.list
webupd8team-haguichi-maverick.list.distUpgrade
webupd8team-haguichi-maverick.list.save
webupd8team-jupiter-oneiric.list
webupd8team-jupiter-oneiric.list.save
webupd8team-y-ppa-manager-maverick.list
webupd8team-y-ppa-manager-maverick.list.distUpgrade
webupd8team-y-ppa-manager-maverick.list.save
wfg-0ad-maverick.list
wfg-0ad-maverick.list.distUpgrade
wfg-0ad-maverick.list.save
xorg-edgers-ppa-natty.list
xorg-edgers-ppa-natty.list.distUpgrade
xorg-edgers-ppa-natty.list.save
xorg-edgers-ppa-oneiric.list
xorg-edgers-ppa-oneiric.list.save
zeitgeist-sharp-daily-maverick.list
zeitgeist-sharp-daily-maverick.list.distUpgrade
zeitgeist-sharp-daily-maverick.list.save

Flash packages

adobe-flash-properties-gtk			install
adobe-flashplugin				install
com.iflashlord.mochidecrypt			install
flashfreeze					install
Plugin locations

/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/player/10.2/lnx/libflashplayer.so
/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.1.0.16076/runtimes/player/10/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.1.0.16076/runtimes/player/10.1/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.0.18623/__MACOSX/flex_sdk_4.5.0.18623/runtimes/player/10.2/lnx/._libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.0.18623/flex_sdk_4.5.0.18623/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/player/10.2/lnx/libflashplayer.so
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Downloads/ACROBEDIA/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/AIR/AdobeAIRSDK/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/flashplayer_10_plugin_debug/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/player/flashplayer10-3_b2_debug_lin_033111/libflashplayer.so
/home/arindam/Downloads/tmp/flashplayer11-2_p4_install_lin_64_011912/libflashplayer.so
/home/arindam/tmp/libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so.BAK
/usr/share/ubufox/plugins/libflashplayer.so.BD


Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1326484954000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1326079387000:1:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
libgnome-shell-browser-plugin.so:$
/usr/lib/mozilla/plugins/libgnome-shell-browser-plugin.so:$
:$
1324368571000:1:5:$
This plugin provides integration with Gnome Shell for live extension enabling and disabling. It can be used only by extensions.gnome.org:$
Gnome Shell Integration:$
1
0:application/x-gnome-shell-integration:Gnome Shell Integration Dummy Content-Type::$
libnpsoplugin.so:$
/usr/lib/libreoffice/program/libnpsoplugin.so:$
:$
1321272902000:1:5:$
OpenOffice.org Plug-in handles all its documents:$
OpenOffice.org Plug-in:$
30
0:application/vnd.stardivision.calc:StarCalc 3.0 - 5.0:sdc:$
1:application/vnd.stardivision.chart:StarChart 3.0 - 5.0:sds:$
2:application/vnd.stardivision.draw:StarDraw 3.0 - 5.0:sda:$
3:application/vnd.stardivision.impress:StarImpress 3.0 - 5.0:sdd:$
4:application/vnd.stardivision.impress-packed:StarImpress-packed 3.0 - 5.0:sdp:$
5:application/vnd.stardivision.math:StarMath 3.0 - 5.0:smf:$
6:application/vnd.stardivision.writer:StarWriter Template 3.0 - 5.0:vor:$
7:application/vnd.stardivision.writer-global:StarWriter Global 3.0 - 5.0:sgl:$
8:application/vnd.staroffice.writer:StarWriter 3.0 - 5.0:sdw:$
9:application/vnd.sun.xml.calc:StarOffice 6.0/7 Spreadsheet:sxc:$
10:application/vnd.sun.xml.calc.template:StarOffice 6.0/7 Spreadsheet Template:stc:$
11:application/vnd.sun.xml.draw:StarOffice 6.0/7 Drawing:sxd:$
12:application/vnd.sun.xml.draw.template:StarOffice 6.0/7 Drawing Template:std:$
13:application/vnd.sun.xml.impress:StarOffice 6.0/7 Presentation:sxi:$
14:application/vnd.sun.xml.impress.template:StarOffice 6.0/7 Presentation Template:sti:$
15:application/vnd.sun.xml.math:StarOffice 6.0/7 Formula:sxm:$
16:application/vnd.sun.xml.writer:StarOffice 6.0/7 Text Document:sxw:$
17:application/vnd.sun.xml.writer.global:StarOffice 6.0/7 Master Document:sxg:$
18:application/vnd.sun.xml.writer.template:StarOffice 6.0/7 Text Document Template:stw:$
19:application/vnd.oasis.opendocument.text:OpenDocument Text:odt:$
20:application/vnd.oasis.opendocument.text-template:OpenDocument Text Template:ott:$
21:application/vnd.oasis.opendocument.text-master:OpenDocument Master Document:odm:$
22:application/vnd.oasis.opendocument.text-web:HTML Document Template:oth:$
23:application/vnd.oasis.opendocument.spreadsheet:OpenDocument Spreadsheet:ods:$
24:application/vnd.oasis.opendocument.spreadsheet-template:OpenDocument Spreadsheet Template:ots:$
25:application/vnd.oasis.opendocument.graphics:OpenDocument Drawing:odg:$
26:application/vnd.oasis.opendocument.graphics-template:OpenDocument Drawing Template:otg:$
27:application/vnd.oasis.opendocument.presentation:OpenDocument Presentation:odp:$
28:application/vnd.oasis.opendocument.presentation-template:OpenDocument Presentation Template:otp:$
29:application/vnd.oasis.opendocument.formula:OpenDocument Formula:odf:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1320721707000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 3.0.1):$
21
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
20:audio/midi:MIDI audio:mid, midi:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1318915705000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$

[INVALID]
/usr/lib/mozilla/plugins/flashplugin-alternative.so:$
0:$
```

Please be more specific about which sites doesn't work.

---

### Post by arindambiswas on 2012-01-29
> **lovinglinux said:**
> Please be more specific about which sites doesn't work.

I meant, no flash embeds render on any site. I have tried to check whether the dependencies are in order and they seem right :
```
arindam@arindamb/usr/lib/firefox-addons/plugins $ ldd /usr/lib/mozilla/plugins/libflashplayer.so
linux-vdso.so.1 => (0x00007fffe2dff000)
libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007f7756633000)
libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f77562fb000)
libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f77560e7000)
libXt.so.6 => /usr/lib/x86_64-linux-gnu/libXt.so.6 (0x00007f7755e82000)
librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f7755c7a000)
libXcursor.so.1 => /usr/lib/x86_64-linux-gnu/libXcursor.so.1 (0x00007f7755a6f000)
libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007f7755864000)
libssl3.so => /usr/lib/x86_64-linux-gnu/libssl3.so (0x00007f775562a000)
libsmime3.so => /usr/lib/x86_64-linux-gnu/libsmime3.so (0x00007f77553fd000)
libnss3.so => /usr/lib/x86_64-linux-gnu/libnss3.so (0x00007f77550c5000)
libnssutil3.so => /usr/lib/x86_64-linux-gnu/libnssutil3.so (0x00007f7754ea6000)
libplds4.so => /usr/lib/x86_64-linux-gnu/libplds4.so (0x00007f7754ca1000)
libplc4.so => /usr/lib/x86_64-linux-gnu/libplc4.so (0x00007f7754a9c000)
libnspr4.so => /usr/lib/x86_64-linux-gnu/libnspr4.so (0x00007f7754861000)
libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f7754643000)
libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f775443f000)
libgtk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0 (0x00007f7753e03000)
libgdk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0 (0x00007f7753b50000)
libatk-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0 (0x00007f775392e000)
libpangoft2-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0 (0x00007f7753703000)
libgdk_pixbuf-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0 (0x00007f77534e3000)
libpangocairo-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0 (0x00007f77532d6000)
libcairo.so.2 => /usr/lib/x86_64-linux-gnu/libcairo.so.2 (0x00007f7753018000)
libpango-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0 (0x00007f7752dcd000)
libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f7752b35000)
libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007f77528ff000)
libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007f77526ad000)
libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007f77524a9000)
libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f77521b3000)
libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f7751f2e000)
libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f7751b8f000)
/lib64/ld-linux-x86-64.so.2 (0x00007f7757dba000)
libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f7751973000)
libSM.so.6 => /usr/lib/x86_64-linux-gnu/libSM.so.6 (0x00007f775176a000)
libICE.so.6 => /usr/lib/x86_64-linux-gnu/libICE.so.6 (0x00007f7751550000)
libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007f775134a000)
libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f7751131000)
libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007f7750def000)
libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007f7750beb000)
libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007f77509db000)
libXrandr.so.2 => /usr/lib/x86_64-linux-gnu/libXrandr.so.2 (0x00007f77507d2000)
libXcomposite.so.1 => /usr/lib/x86_64-linux-gnu/libXcomposite.so.1 (0x00007f77505ce000)
libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007f77503cb000)
libpixman-1.so.0 => /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x00007f7750156000)
libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007f774ff2f000)
libxcb-shm.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 (0x00007f774fd2c000)
libxcb-render.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-render.so.0 (0x00007f774fb22000)
libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f774f8f8000)
libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f774f6ef000)
libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f774f4b3000)
libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f774f2b0000)
libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f774f0a9000)
libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007f774eea4000)
libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007f774ec86000)
libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f774ea6a000)

```

---

### Post by lovinglinux on 2012-01-29
> **arindambiswas said:**
> I meant, no flash embeds render on any site. I have tried to check whether the dependencies are in order and they seem right :

Okay, what I actually need to know if you can for example watch an YouTube video on the original site and not an YouTube video embedded on third party sites? Ifd that is the case, then is probably a cookie issue. If you can't even watch a video on YouTube site, then I need to know what error do you get.

---

### Post by arindambiswas on 2012-01-30
> **lovinglinux said:**
> Okay, what I actually need to know if you can for example watch an YouTube video on the original site and not an YouTube video embedded on third party sites? Ifd that is the case, then is probably a cookie issue. If you can't even watch a video on YouTube site, then I need to know what error do you get.

Unable to watch a YouTube video on YouTube too. Same thing in Google Chrome too. I tried to revert back to the stable release using Flash-Aid, but that didnt work either. There is no error as such, please check the screenshot of YouTube below. Here is the new report generated using Flash-Aid.
```
Ubuntu Architecture

Linux arindamb 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox                        install
firefox-globalmenu                install
firefox-locale-bn                install
firefox-locale-en                install
firefox-locale-hi                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-9.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

adilson-experimental-oneiric.list
adilson-experimental-oneiric.list.save
alexmurray-indicator-sensors-oneiric.list
alexmurray-indicator-sensors-oneiric.list.save
amandeepgrewal-notifyosdconfig-maverick.list.save
am-monkeyd-nautilus-elementary-ppa-maverick.list
am-monkeyd-nautilus-elementary-ppa-maverick.list.distUpgrade
am-monkeyd-nautilus-elementary-ppa-maverick.list.save
awn-testing-ppa-maverick.list
awn-testing-ppa-maverick.list.distUpgrade
awn-testing-ppa-maverick.list.save
bigwhale-kazam-oneric-oneiric.list
bigwhale-kazam-oneric-oneiric.list.save
bisigi-ppa-maverick.list
bisigi-ppa-maverick.list.distUpgrade
bisigi-ppa-maverick.list.save
blueman-ppa-maverick.list
blueman-ppa-maverick.list.distUpgrade
blueman-ppa-maverick.list.save
clicompanion-devs-clicompanion-nightlies-maverick.list
clicompanion-devs-clicompanion-nightlies-maverick.list.distUpgrade
clicompanion-devs-clicompanion-nightlies-maverick.list.save
damnvid-ppa-maverick.list
damnvid-ppa-maverick.list.distUpgrade
damnvid-ppa-maverick.list.save
david4dev-qr-maverick.list
david4dev-qr-maverick.list.distUpgrade
david4dev-qr-maverick.list.save
disper-dev-ppa-oneiric.list
disper-dev-ppa-oneiric.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
geod-ppa-geod-maverick.list
geod-ppa-geod-maverick.list.distUpgrade
geod-ppa-geod-maverick.list.save
goehle-goehle-ppa-maverick.list
goehle-goehle-ppa-maverick.list.distUpgrade
goehle-goehle-ppa-maverick.list.save
goehle-goehle-ppasudo-maverick.list
goehle-goehle-ppasudo-maverick.list.distUpgrade
goehle-goehle-ppasudo-maverick.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google.list
google.list.distUpgrade
google.list.save
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
hplip-isv-ppa-natty.list
hplip-isv-ppa-natty.list.distUpgrade
hplip-isv-ppa-natty.list.save
indicator-multiload-stable-daily-oneiric.list
indicator-multiload-stable-daily-oneiric.list.save
janousek_jiri-google-music-frame-daily-oneiric.list
janousek_jiri-google-music-frame-daily-oneiric.list.save
jconti-recent-notifications-maverick.list
jconti-recent-notifications-maverick.list.distUpgrade
jconti-recent-notifications-maverick.list.save
jfi-psensor-unstable-oneiric.list
jfi-psensor-unstable-oneiric.list.save
jonoomph-openshot-edge-maverick.list
jonoomph-openshot-edge-maverick.list.distUpgrade
jonoomph-openshot-edge-maverick.list.save
keks9n-main-natty.list
keks9n-main-natty.list.distUpgrade
keks9n-main-natty.list.save
kilian-f_lux-oneiric.list
kilian-f_lux-oneiric.list.save
kokoto-java-usu-extras-maverick.list
kokoto-java-usu-extras-maverick.list.distUpgrade
kokoto-java-usu-extras-maverick.list.save
leolik-leolik-maverick.list
leolik-leolik-maverick.list.distUpgrade
leolik-leolik-maverick.list.save
librecad-dev-librecad-daily-oneiric.list
librecad-dev-librecad-daily-oneiric.list.save
libreoffice-ppa-maverick.list
libreoffice-ppa-maverick.list.distUpgrade
libreoffice-ppa-maverick.list.save
libreoffice-ppa-natty.list
libreoffice-ppa-natty.list.distUpgrade
libreoffice-ppa-natty.list.save
libreplan-ppa-oneiric.list
libreplan-ppa-oneiric.list.save
lkjoel-flash-doctor-oneiric.list
lkjoel-flash-doctor-oneiric.list.save
loell-ppa-oneiric.list
loell-ppa-oneiric.list.save
manu-tm-newsrssticker-natty.list
manu-tm-newsrssticker-natty.list.distUpgrade
manu-tm-newsrssticker-natty.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
mj-casalogic-ironhide-oneiric.list
mj-casalogic-ironhide-oneiric.list.save
mozillateam-firefox-stable-maverick.list
mozillateam-firefox-stable-maverick.list.distUpgrade
mozillateam-firefox-stable-maverick.list.save
nikount-orta-desktop-natty.list
nikount-orta-desktop-natty.list.distUpgrade
nikount-orta-desktop-natty.list.save
nilarimogard-webupd8-maverick.list
nilarimogard-webupd8-maverick.list.distUpgrade
nilarimogard-webupd8-maverick.list.save
nuovodna-nuovodna-stuff-maverick.list
nuovodna-nuovodna-stuff-maverick.list.distUpgrade
nuovodna-nuovodna-stuff-maverick.list.save
nvidia-vdpau-ppa-natty.list
nvidia-vdpau-ppa-natty.list.distUpgrade
nvidia-vdpau-ppa-natty.list.save
openbravo-isv-ppa-maverick.list
openbravo-isv-ppa-maverick.list.distUpgrade
openbravo-isv-ppa-maverick.list.save
opera.list
osmoma-audio-recorder-maverick.list
osmoma-audio-recorder-maverick.list.distUpgrade
osmoma-audio-recorder-maverick.list.save
osmoma-audio-recorder-oneiric.list
osmoma-audio-recorder-oneiric.list.save
rabbitvcs-ppa-maverick.list
rabbitvcs-ppa-maverick.list.distUpgrade
rabbitvcs-ppa-maverick.list.save
ricotz-docky-maverick.list
ricotz-docky-maverick.list.distUpgrade
ricotz-docky-maverick.list.save
sevenmachines-flash-maverick.list
sevenmachines-flash-maverick.list.distUpgrade
sevenmachines-flash-maverick.list.save
sevenmachines-flash-natty.list
sevenmachines-flash-natty.list.distUpgrade
sevenmachines-flash-natty.list.save
sevenmachines-flash-oneiric.list
shiki-mediainfo-natty.list
shiki-mediainfo-natty.list.distUpgrade
shiki-mediainfo-natty.list.save
shnatsel-flashfreeze-oneiric.list
shnatsel-flashfreeze-oneiric.list.save
stebbins-handbrake-releases-maverick.list
stebbins-handbrake-releases-maverick.list.distUpgrade
stebbins-handbrake-releases-maverick.list.save
stebbins-handbrake-releases-natty.list
stebbins-handbrake-releases-natty.list.distUpgrade
stebbins-handbrake-releases-natty.list.save
stebbins-handbrake-snapshots-maverick.list
stebbins-handbrake-snapshots-maverick.list.distUpgrade
stebbins-handbrake-snapshots-maverick.list.save
stedy6-stedy-minidna-natty.list
stedy6-stedy-minidna-natty.list.distUpgrade
stedy6-stedy-minidna-natty.list.save
team-xbmc-ppa-natty.list
team-xbmc-ppa-natty.list.distUpgrade
team-xbmc-ppa-natty.list.save
team-xbmc-unstable-natty.list
team-xbmc-unstable-natty.list.distUpgrade
team-xbmc-unstable-natty.list.save
time-drive-devel-stable-maverick.list
time-drive-devel-stable-maverick.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.distUpgrade
tualatrix-ppa-maverick.list.save
ubuntu-tweak-stable.list.save
ubuntu-wine-ppa-maverick.list
ubuntu-wine-ppa-maverick.list.distUpgrade
ubuntu-wine-ppa-maverick.list.save
ubuntu-x-swat-x-updates-maverick.list
ubuntu-x-swat-x-updates-maverick.list.distUpgrade
ubuntu-x-swat-x-updates-maverick.list.save
ubuntu-x-swat-x-updates-oneiric.list
ubuntu-x-swat-x-updates-oneiric.list.save
webupd8team-gnome3-oneiric.list
webupd8team-gnome3-oneiric.list.save
webupd8team-gtk-recordmydesktop-maverick.list.save
webupd8team-haguichi-maverick.list
webupd8team-haguichi-maverick.list.distUpgrade
webupd8team-haguichi-maverick.list.save
webupd8team-jupiter-oneiric.list
webupd8team-jupiter-oneiric.list.save
webupd8team-y-ppa-manager-maverick.list
webupd8team-y-ppa-manager-maverick.list.distUpgrade
webupd8team-y-ppa-manager-maverick.list.save
wfg-0ad-maverick.list
wfg-0ad-maverick.list.distUpgrade
wfg-0ad-maverick.list.save
xorg-edgers-ppa-natty.list
xorg-edgers-ppa-natty.list.distUpgrade
xorg-edgers-ppa-natty.list.save
xorg-edgers-ppa-oneiric.list
xorg-edgers-ppa-oneiric.list.save
zeitgeist-sharp-daily-maverick.list
zeitgeist-sharp-daily-maverick.list.distUpgrade
zeitgeist-sharp-daily-maverick.list.save

Flash packages

adobe-flash-properties-gtk            install
adobe-flashplugin                install
com.iflashlord.mochidecrypt            install
flashfreeze                    install
flashplugin-downloader:i386            deinstall
Plugin locations

/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/player/10.2/lnx/libflashplayer.so
/home/arindam/Documents/sdk/as3/RIM/blackberry-tablet-sdk-1.1.0/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.1.0.16076/runtimes/player/10/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.1.0.16076/runtimes/player/10.1/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.0.18623/__MACOSX/flex_sdk_4.5.0.18623/runtimes/player/10.2/lnx/._libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.0.18623/flex_sdk_4.5.0.18623/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/player/10.2/lnx/libflashplayer.so
/home/arindam/Documents/sdk/as3/flex_sdk_4.5.1.21328/runtimes/player/10.2/lnx/libflashplayer.so.tar.gz
/home/arindam/Downloads/ACROBEDIA/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/AIR/AdobeAIRSDK/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/flashplayer_10_plugin_debug/libflashplayer.so
/home/arindam/Downloads/ACROBEDIA/player/flashplayer10-3_b2_debug_lin_033111/libflashplayer.so
/home/arindam/Downloads/tmp/flashplayer11-2_p4_install_lin_64_011912/libflashplayer.so
/home/arindam/tmp/libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so.BAK
/usr/share/ubufox/plugins/libflashplayer.so.BD

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1326484954000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1326079387000:1:1:$
Shockwave Flash 11.1 r102:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
libgnome-shell-browser-plugin.so:$
/usr/lib/mozilla/plugins/libgnome-shell-browser-plugin.so:$
:$
1324368571000:1:5:$
This plugin provides integration with Gnome Shell for live extension enabling and disabling. It can be used only by extensions.gnome.org:$
Gnome Shell Integration:$
1
0:application/x-gnome-shell-integration:Gnome Shell Integration Dummy Content-Type::$
libnpsoplugin.so:$
/usr/lib/libreoffice/program/libnpsoplugin.so:$
:$
1321272902000:1:5:$
OpenOffice.org Plug-in handles all its documents:$
OpenOffice.org Plug-in:$
30
0:application/vnd.stardivision.calc:StarCalc 3.0 - 5.0:sdc:$
1:application/vnd.stardivision.chart:StarChart 3.0 - 5.0:sds:$
2:application/vnd.stardivision.draw:StarDraw 3.0 - 5.0:sda:$
3:application/vnd.stardivision.impress:StarImpress 3.0 - 5.0:sdd:$
4:application/vnd.stardivision.impress-packed:StarImpress-packed 3.0 - 5.0:sdp:$
5:application/vnd.stardivision.math:StarMath 3.0 - 5.0:smf:$
6:application/vnd.stardivision.writer:StarWriter Template 3.0 - 5.0:vor:$
7:application/vnd.stardivision.writer-global:StarWriter Global 3.0 - 5.0:sgl:$
8:application/vnd.staroffice.writer:StarWriter 3.0 - 5.0:sdw:$
9:application/vnd.sun.xml.calc:StarOffice 6.0/7 Spreadsheet:sxc:$
10:application/vnd.sun.xml.calc.template:StarOffice 6.0/7 Spreadsheet Template:stc:$
11:application/vnd.sun.xml.draw:StarOffice 6.0/7 Drawing:sxd:$
12:application/vnd.sun.xml.draw.template:StarOffice 6.0/7 Drawing Template:std:$
13:application/vnd.sun.xml.impress:StarOffice 6.0/7 Presentation:sxi:$
14:application/vnd.sun.xml.impress.template:StarOffice 6.0/7 Presentation Template:sti:$
15:application/vnd.sun.xml.math:StarOffice 6.0/7 Formula:sxm:$
16:application/vnd.sun.xml.writer:StarOffice 6.0/7 Text Document:sxw:$
17:application/vnd.sun.xml.writer.global:StarOffice 6.0/7 Master Document:sxg:$
18:application/vnd.sun.xml.writer.template:StarOffice 6.0/7 Text Document Template:stw:$
19:application/vnd.oasis.opendocument.text:OpenDocument Text:odt:$
20:application/vnd.oasis.opendocument.text-template:OpenDocument Text Template:ott:$
21:application/vnd.oasis.opendocument.text-master:OpenDocument Master Document:odm:$
22:application/vnd.oasis.opendocument.text-web:HTML Document Template:oth:$
23:application/vnd.oasis.opendocument.spreadsheet:OpenDocument Spreadsheet:ods:$
24:application/vnd.oasis.opendocument.spreadsheet-template:OpenDocument Spreadsheet Template:ots:$
25:application/vnd.oasis.opendocument.graphics:OpenDocument Drawing:odg:$
26:application/vnd.oasis.opendocument.graphics-template:OpenDocument Drawing Template:otg:$
27:application/vnd.oasis.opendocument.presentation:OpenDocument Presentation:odp:$
28:application/vnd.oasis.opendocument.presentation-template:OpenDocument Presentation Template:otp:$
29:application/vnd.oasis.opendocument.formula:OpenDocument Formula:odf:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1320721707000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1318915705000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 3.0.1):$
21
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
20:audio/midi:MIDI audio:mid, midi:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1318915705000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libflashplayer.so:$
/usr/lib/adobe-flashplugin/libflashplayer.so:$
:$
1320112563000:1:13:$
Shockwave Flash 11.1 r102:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

[INVALID]
```

Firefox add-ons page reports that the plugin is installed

[IMG]http://www.apptikka.com/customer_projects/arindam/flashbuntu/Firefox-addons.jpg[/IMG]

But YouTube does not render ...

[IMG]http://www.apptikka.com/customer_projects/arindam/flashbuntu/YouTube-rc.jpg[/IMG] 

And neither does the Adobe site on its test page

[IMG]http://www.apptikka.com/customer_projects/arindam/flashbuntu/Adobe-flash.jpg[/IMG]
 

Google Chrome reports that the flash player is installed but doesn't render too

[IMG]http://www.apptikka.com/customer_projects/arindam/flashbuntu/GoogleChrome.jpg[/IMG]

---

### Post by lovinglinux on 2012-01-30
I don't see anything wrong with your setup. Try to purge your cookies and browser cache. Then access [https://www.youtube.com](https://www.youtube.com) which is the https version of YouTube. Let me know if it works.

---

### Post by arindambiswas on 2012-01-31
> **lovinglinux said:**
> I don't see anything wrong with your setup. Try to purge your cookies and browser cache. Then access [https://www.youtube.com](https://www.youtube.com) which is the https version of YouTube. Let me know if it works.

Nopes. :( didnt work. I have tried reinstalling firefox thru agt-get too but it has not worked. Its been more than a week now and i cannot figure out for the life of me what went wrong. 

@lovinglinux : if its fine by you, you could add me via TeamViewer and check whether there is anything that i am doing wrong.

---

