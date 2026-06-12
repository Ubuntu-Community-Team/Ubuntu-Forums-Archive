---
title: "Realplay audio firefox plugin not working"
date: 2006-06-21
forum: General Help
---

### Post by v4169sgr on 2006-06-21
Banging my head against a brick wall here.#-o 

I've discovered the painful way that the Firefox supplied with Dapper by default does not play nice with the Realplay plugin [no sound, little or no picture]. Suggestions to use mplayer instead are all very well but do not seem to work for 'important' web sites that insist on Realplay.

So I've downloaded Firefox 1.5.0.4 to /usr/local/ and copied some plugins over. At the moment I'm trying to keep things simple so have:

```
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.581 built with gcc 3.2.0 on Feb 1 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
Shockwave Flash

    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/futuresplash 	Future Splash 	spl 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r63

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Adobe Reader 7.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
```

Now, I try accessing this website:

[http://www.rfi.fr/](http://www.rfi.fr/)

and selecting 'RFI Monde' on the left hand side. In the popup window, I select 'Realplay Audio'. Nothign appears to happen in the app, but in the console I see the following:

```
Calling realplay
playeripc: Got command Version 1
playeripc: Got command Embed name='STREAM' src='http://www.tv-radio.com/station/rfi/rfi-20k.ram' style='position: absolute; left: 10px; top: 10px; width: 10px; height: 10px; visibility: hidden;' type='audio/x-pn-realaudio-plugin' controls='ImageWindow' console='cons' autostart='true'

** (realplay.bin:6928): WARNING **: Ignoring unknown attribute style
playeripc: Got command Browser 0 'Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.0.4) Gecko/20060508 Firefox/1.5.0.4' 0 1
playeripc: Got command SetWindow 0 50358208 10 10 10 10 0 0 10 10 1

** (realplay.bin:6928): WARNING **: Width and height for window 0 are invalid

(realplay.bin:6928): Gtk-WARNING **: Attempting to add a widget with type HXPlayer to a container of type HXBin, but the widget is already inside a container of type HXBin, the GTK+ FAQ at http://www.gtk.org/faq/ explains how to reparent a widget.
playeripc: Got command Embed src='http://www.tv-radio.com/station/rfi/rfi-20k.ram' style='position: absolute; left: 5px; top: 1px; width: 191px; height: 27px;' type='audio/x-pn-realaudio-plugin' controls='ControlPanel' console='cons' autostart='true'

** (realplay.bin:6928): WARNING **: Ignoring unknown attribute style
playeripc: Got command Browser 1 'Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.0.4) Gecko/20060508 Firefox/1.5.0.4' 0 1
playeripc: Got command SetWindow 1 50358211 5 1 191 27 0 0 27 191 1

** (realplay.bin:6928): WARNING **: Width and height for window 1 are invalid
playeripc: Got command SetWindow 1 50358211 5 1 191 27 0 0 27 191 1

** (realplay.bin:6928): WARNING **: Width and height for window 1 are invalid
playeripc: Got command Embed id='STREAM' src='http://www.tv-radio.com/station/rfi/rfi-20k.ram' style='position: absolute; left: 4px; top: 29px; width: 192px; height: 21px;' type='audio/x-pn-realaudio-plugin' controls='StatusBar' console='cons' autostart='true'

** (realplay.bin:6928): WARNING **: Ignoring unknown attribute id

** (realplay.bin:6928): WARNING **: Ignoring unknown attribute style
playeripc: Got command Browser 2 'Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.0.4) Gecko/20060508 Firefox/1.5.0.4' 0 1
playeripc: Got command SetWindow 2 50358214 4 29 192 21 0 0 21 192 1

** (realplay.bin:6928): WARNING **: Width and height for window 2 are invalid
playeripc: Got command SetWindow 2 50358214 4 29 192 21 0 0 21 192 1

** (realplay.bin:6928): WARNING **: Width and height for window 2 are invalid
playeripc: Got command SetWindow 1 50358211 5 1 191 27 0 0 27 191 1

** (realplay.bin:6928): WARNING **: Width and height for window 1 are invalid
playeripc: Got command SetWindow 2 50358214 4 29 192 21 0 0 21 192 1

** (realplay.bin:6928): WARNING **: Width and height for window 2 are invalid
playeripc: Got command NewStream 0 0 http://www.tv-radio.com/station/rfi/rfi-20k.ram audio/x-pn-realaudio 182
playeripc: Got command NewStream 1 0 http://www.tv-radio.com/station/rfi/rfi-20k.ram audio/x-pn-realaudio 182
playeripc: Got command NewStream 2 0 http://www.tv-radio.com/station/rfi/rfi-20k.ram audio/x-pn-realaudio 182
/usr/bin/realplay: line 75:  6928 Segmentation fault      $REALPLAYBIN "$@"
read: Connection reset by peer

```

However, if I start realplay as a stand alone app using 

realplay [http://www.tv-radio.com/station/rfi/rfi-20k.ram](http://www.tv-radio.com/station/rfi/rfi-20k.ram)

then the link works and I get clear audio from Realplayer.

Can anyone advise how to solve these problems so I can get Realplay working as a plugin? Many thanks!

---

### Post by v4169sgr on 2006-06-21
The same browser set up plays the BBC Radiom audio streams really nicely with no problems.

---

### Post by v4169sgr on 2006-06-22
Anyone?

---

