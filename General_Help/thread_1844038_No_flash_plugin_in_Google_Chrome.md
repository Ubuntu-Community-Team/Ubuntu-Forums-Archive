---
title: "No flash plugin in Google Chrome"
date: 2011-09-14
forum: General Help
---

### Post by TheHimself on 2011-09-14
I have the latest version of Google Chrome installed but can't watch any flash content. The adobe website says I should enable the built in  flash plugin in about: plugins but surprisingly there is no such plugin! :confused:
The problem started when I upgraded the package "flash plugin installer".

---

### Post by haqking on 2011-09-14
> **TheHimself said:**
> I have the latest version of Google Chrome installed but can't watch any flash content. The adobe website says I should enable the built in  flash plugin in about: plugins but surprisingly there is no such plugin! :confused:
The problem started when I upgraded the package "flash plugin installer".

Do you have fire fox also ?

is so you can use [Flash Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/") and that will install the most approipriate for your system and then it will be used across the system by other browsers also

---

### Post by TheHimself on 2011-09-15
I have firefox and it can display flash content. However Chrome is supposed to have an integrated flash plugin which I couldn't find.

---

### Post by khelben1979 on 2011-09-15
I would suggest you reinstall Google Chrome to see if it helps.

---

### Post by dummy910 on 2011-09-15
Same exact thing happened on a machine I admin for just yesterday....

Load your SoftwareCenter, type in Chrome as to list it's status page and  look towards the lower part of the page that shows the addons etc for  Chrome... Flash should be the top choice and of course, make sure it's  checked, if not, check it and it will begin to download after you hit  the apply(i think its named).

---

### Post by gandaran on 2011-09-15
> **TheHimself said:**
> I have firefox and it can display flash content. However Chrome is supposed to have an integrated flash plugin which I couldn't find.
if you have the 64-bits chrome then it doesn't have the built in flash only 32-bits version has it, install the firefox flash-aid addon to install 64-bits system flash, chrome will use the system flash plugin.

---

### Post by vasa1 on 2011-09-15
> **TheHimself said:**
> I have the latest version of Google Chrome installed but can't watch any flash content. The adobe website says I should enable the built in  flash plugin in about: plugins but surprisingly there is no such plugin! :confused:
The problem started when I upgraded the package "flash plugin installer".
What do you see when you type "about:" (without quotes) in the address bar and hit enter?
Do you see something like this:
> Google Chrome	13.0.782.220 (Official Build 99552)
OS	Linux
WebKit	535.1 (branches/chromium/782@93192)
JavaScript	V8 3.3.10.30
Flash	10.3 r183
User Agent	Mozilla/5.0 (X11; Linux i686) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/13.0.782.220 Safari/535.1
Command Line	 /opt/google/chrome/google-chrome --flag-switches-begin --flag-switches-end
Executable Path	/opt/google/chrome/google-chrome
Profile Path	/home/your_name/.config/google-chrome/Default

What do you see when you type "about: plugins" (without quotes and without spaces) in the address bar and hit enter?
First, you should click on the + sign on the right-side of the resulting screen. That will expand the plug-in list.
If I look in the **Flash** section, I see:
> Version:	10.3 r183
Location:	/opt/google/chrome/libgcflashplayer.so
and, below that:
> Version:	10.3 r183
Location:	/usr/lib/adobe-flashplugin/libflashplayer.so
I have disabled the lower one and left the upper one enabled.

---

### Post by TheHimself on 2011-09-15
I'm using 64 bit Chrome and it seems that this is the problem. Adobe has a 64 bit flash for Linux here: [http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)
but doesn't say where to unzip it. 

Flash-aid doesn't download completely.

---

### Post by haqking on 2011-09-15
> **TheHimself said:**
> I'm using 64 bit Chrome and it seems that this is the problem. Adobe has a 64 bit flash for Linux here: [http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)
but doesn't say where to unzip it. 

Flash-aid doesn't download completely.

you need to put  libflashplayer.so into the plugins folder for your default browser see here [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

When you say that Flash Aid does not download completely what do you mean exactly ? it should work fine

---

### Post by TheHimself on 2011-09-16
But Chrome doesn't seem to have a plugin folder.

Flashaid's download gets stuck in the middle. Tried many times.

---

### Post by vasa1 on 2011-09-16
> **TheHimself said:**
> But Chrome doesn't seem to have a plugin folder.
...

That's amazing.

I'll ask again, what do you get when you type "about : plugins" (without any quotes or spaces) in the address bar and hit enter?

---

### Post by TheHimself on 2011-09-19
```
Plug-ins (11)		
Details
IcedTea - Version: 1.9.9
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.9 (6b20-1.9.9-0ubuntu1~10.10.2)) executes Java applets.
Name:	IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.9 (6b20-1.9.9-0ubuntu1~10.10.2))
Description:	The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.9 (6b20-1.9.9-0ubuntu1~10.10.2)) executes Java applets.
Version:	1.9.9
Location:	/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-java-vm	IcedTea	
.class	.jar
application/x-java-applet	IcedTea	
.class	.jar
application/x-java-applet;version=1.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.3	IcedTea	
.class	.jar
application/x-java-applet;version=1.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.2.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.2.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.3	IcedTea	
.class	.jar
application/x-java-applet;version=1.3.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.4	IcedTea	
.class	.jar
application/x-java-applet;version=1.4.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.4.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.5	IcedTea	
.class	.jar
application/x-java-applet;version=1.6	IcedTea	
.class	.jar
application/x-java-applet;jpi-version=1.6.0_20	IcedTea	
.class	.jar
application/x-java-bean	IcedTea	
.class	.jar
application/x-java-bean;version=1.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.3	IcedTea	
.class	.jar
application/x-java-bean;version=1.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.2.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.2.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.3	IcedTea	
.class	.jar
application/x-java-bean;version=1.3.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.4	IcedTea	
.class	.jar
application/x-java-bean;version=1.4.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.4.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.5	IcedTea	
.class	.jar
application/x-java-bean;version=1.6	IcedTea	
.class	.jar
application/x-java-bean;jpi-version=1.6.0_20	IcedTea	
.class	.jar
application/x-java-vm-npruntime	IcedTea	
.
Disable
Chrome NaCl (Disabled)
Name:	Chrome NaCl
Version:	
Location:	/opt/google/chrome/libppGoogleNaClPluginChrome.so
 	(Disabled) Enable
MIME types:	
MIME type	Description	File extensions
application/x-nacl	Native Client Executable	
.nexe
Enable
Chrome PDF Viewer
Name:	Chrome PDF Viewer
Version:	
Location:	/opt/google/chrome/libpdf.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/pdf	Portable Document Format	
.pdf
Disable
VLC Multimedia Plug-in
Version 1.1.4 The Luggage, copyright 1996-2007 The VideoLAN Team
[http://www.videolan.org/](http://www.videolan.org/)
Name:	VLC Multimedia Plug-in
Description:	Version 1.1.4 The Luggage, copyright 1996-2007 The VideoLAN Team
[http://www.videolan.org/](http://www.videolan.org/)
Version:	
Location:	/usr/lib/mozilla/plugins/libvlcplugin.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
audio/mpeg	MPEG audio	
.mp2	.mp3	.mpga	.mpega
audio/x-mpeg	MPEG audio	
.mp2	.mp3	.mpga	.mpega
video/mpeg	MPEG video	
.mpg	.mpeg	.mpe
video/x-mpeg	MPEG video	
.mpg	.mpeg	.mpe
video/mpeg-system	MPEG video	
.mpg	.mpeg	.mpe	.vob
video/x-mpeg-system	MPEG video	
.mpg	.mpeg	.mpe	.vob
audio/x-mpegurl	MPEG audio	
.m3u
video/mp4	MPEG-4 video	
.mp4	.mpg4
audio/mp4	MPEG-4 audio	
.mp4	.mpg4
audio/x-m4a	MPEG-4 audio	
.m4a
application/mpeg4-iod	MPEG-4 video	
.mp4	.mpg4
application/mpeg4-muxcodetable	MPEG-4 video	
.mp4	.mpg4
video/x-msvideo	AVI video	
.avi
video/quicktime	QuickTime video	
.mov	.qt
application/x-ogg	Ogg stream	
.ogg
application/ogg	Ogg stream	
.ogg
application/x-vlc-plugin	VLC plug-in	
.vlc
video/x-ms-asf-plugin	Windows Media Video	
.asf	.asx
video/x-ms-asf	Windows Media Video	
.asf	.asx
application/x-mplayer2	Windows Media	
.
video/x-ms-wmv	Windows Media	
.wmv
video/x-ms-wvx	Windows Media Video	
.wvx
audio/x-ms-wma	Windows Media Audio	
.wma
application/x-google-vlc-plugin	Google VLC plug-in	
.
audio/wav	WAV audio	
.wav
audio/x-wav	WAV audio	
.wav
audio/3gpp	3GPP audio	
.3gp	.3gpp
video/3gpp	3GPP video	
.3gp	.3gpp
audio/3gpp2	3GPP2 audio	
.3g2	.3gpp2
video/3gpp2	3GPP2 video	
.3g2	.3gpp2
video/divx	DivX video	
.divx
video/flv	FLV video	
.flv
video/x-flv	FLV video	
.flv
video/x-matroska	Matroska video	
.mkv
audio/x-matroska	Matroska audio	
.mka
application/xspf+xml	Playlist xspf	
.xspf
video/webm	WebM video	
.webm
audio/webm	WebM audio	
.webm
Disable
iTunes Application Detector
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Name:	iTunes Application Detector
Description:	This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Version:	
Location:	/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/itunes-plugin		
.
Disable
VLC Multimedia Plugin (compatible Totem 2.32.0) (Disabled)
The Totem 2.32.0 plugin handles video and audio streams.
Name:	VLC Multimedia Plugin (compatible Totem 2.32.0)
Description:	The Totem 2.32.0 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-cone-plugin.so
 	(Disabled) Enable
MIME types:	
MIME type	Description	File extensions
application/x-vlc-plugin	VLC Multimedia Plugin	
.
application/vlc	VLC Multimedia Plugin	
.
video/x-google-vlc-plugin	VLC Multimedia Plugin	
.
application/x-ogg	Ogg multimedia file	
.ogg
application/ogg	Ogg multimedia file	
.ogg
audio/ogg	Ogg Audio	
.oga
audio/x-ogg	Ogg Audio	
.ogg
video/ogg	Ogg Video	
.ogv
video/x-ogg	Ogg Video	
.ogg
application/annodex	Annodex exchange format	
.anx
audio/annodex	Annodex Audio	
.axa
video/annodex	Annodex Video	
.axv
video/mpeg	MPEG video	
.mpg	.mpeg	.mpe
audio/wav	WAV audio	
.wav
audio/x-wav	WAV audio	
.wav
audio/mpeg	MP3 audio	
.mp3
application/x-nsv-vp3-mp3	NullSoft video	
.nsv
video/flv	Flash video	
.flv
video/webm	WebM video	
.webm
application/x-totem-plugin	Totem Multimedia plugin	
.
Enable
Windows Media Player Plug-in 10 (compatible; Totem)
The Totem 2.32.0 plugin handles video and audio streams.
Name:	Windows Media Player Plug-in 10 (compatible; Totem)
Description:	The Totem 2.32.0 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-mplayer2	AVI video	
.avi	.wma	.wmv
video/x-ms-asf-plugin	ASF video	
.asf	.wmv
video/x-msvideo	AVI video	
.asf	.wmv
video/x-ms-asf	ASF video	
.asf
video/x-ms-wmv	Windows Media video	
.wmv
video/x-wmv	Windows Media video	
.wmv
video/x-ms-wvx	Windows Media video	
.wmv
video/x-ms-wm	Windows Media video	
.wmv
video/x-ms-wmp	Windows Media video	
.wmv
application/x-ms-wms	Windows Media video	
.wms
application/x-ms-wmp	Windows Media video	
.wmp
application/asx	Microsoft ASX playlist	
.asx
audio/x-ms-wma	Windows Media audio	
.wma
Disable
DivX® Web Player
DivX Web Player version 1.4.0.233
Name:	DivX® Web Player
Description:	DivX Web Player version 1.4.0.233
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-mully-plugin.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
video/divx	AVI video	
.divx
Disable
QuickTime Plug-in 7.6.6
The Totem 2.32.0 plugin handles video and audio streams.
Name:	QuickTime Plug-in 7.6.6
Description:	The Totem 2.32.0 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
video/quicktime	QuickTime video	
.mov
video/mp4	MPEG-4 video	
.mp4
image/x-macpaint	MacPaint Bitmap image	
.pntg
image/x-quicktime	Macintosh Quickdraw/PICT drawing	
.pict	.pict1	.pict2
video/x-m4v	MPEG-4 video	
.m4v
Disable
Parole media player plugin-in
Media player browser plugin for various media format version 0.2.0.2
Name:	Parole media player plugin-in
Description:	Media player browser plugin for various media format version 0.2.0.2
Version:	
Location:	/usr/lib/mozilla/plugins/parole-player.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/asx	Media Files	
.*
video/x-ms-asf-plugin	Media Files	
.*
video/x-msvideo	AVI	
.avi	.*
video/msvideo	AVI	
.avi	.*
application/x-mplayer2	Media Files	
.*
application/x-ms-wmv	Microsoft WMV video	
.wmv	.*
video/x-ms-asf	Media Files	
.asf	.asx	.*
video/x-ms-wm	Media Files	
.wm	.*
video/x-ms-wmv	Microsoft WMV video	
.wmv	.*
audio/x-ms-wmv	Windows Media	
.wmv	.*
video/x-ms-wmp	Windows Media	
.wmp	.*
application/x-ms-wmp	Windows Media	
.wmp	.*
video/x-ms-wvx	Windows Media	
.wvx	.*
audio/x-ms-wax	Windows Media	
.wax	.*
audio/x-ms-wma	Windows Media	
.wma	.*
application/x-drm-v2	Windows Media	
.asx	.*
audio/wav	Microsoft wave file	
.wav	.*
audio/x-wav	Microsoft wave file	
.wav	.*
audio/x-mpegurl	MPEG Playlist	
.m3u
video/mpeg	MPEG	
.mpg	.mpeg
audio/mpeg	MPEG	
.mpg	.mpeg
video/x-mpeg	MPEG	
.mpg	.mpeg
video/x-mpeg2	MPEG2	
.mpv2	.mp2ve
audio/mpeg	MPEG	
.mpg	.mpeg
audio/x-mpeg	MPEG	
.mpg	.mpeg
audio/mpeg2	MPEG audio	
.mp2
audio/x-mpeg2	MPEG audio	
.mp2
audio/mp4	MPEG 4 audio	
.mp4
audio/x-mp4	MPEG 4 audio	
.mp4
video/mp4	MPEG 4 Video	
.mp4
video/x-m4v	MPEG 4 Video	
.m4v
video/3gpp	MPEG 4 Video	
.mp4	.3gp
application/x-ogg	Ogg Vorbis Media	
.ogg
audio/flac	FLAC Lossless Audio	
.ogg
audio/x-flac	FLAC Lossless Audio	
.ogg
audio/ogg	Ogg Vorbis Audio	
.ogg
audio/ogg	Ogg Vorbis Audio	
.x-ogg
application/ogg	Ogg Vorbis / Ogg Theora	
.ogg
video/ogg	Ogg Vorbis Video	
.ogg
video/ogg	Ogg Vorbis Video	
.x-ogg
audio/x-pn-realaudio	RealAudio	
.ram	.rm
application/vnd.rn-realmedia	RealMedia	
.rm
application/vnd.rn-realaudio	RealAudio	
.ra	.ram
video/vnd.rn-realvideo	RealVideo	
.rv
audio/x-realaudio	RealAudio	
.ra
audio/x-pn-realaudio-plugin	RealAudio	
.rpm
application/smil	SMIL	
.smil
video/divx	DivX Media Format	
.divx
video/vnd.divx	DivX Media Format	
.divx
video/quicktime	Quicktime	
.mov
video/x-quicktime	Quicktime	
.mov
image/x-quicktime	Quicktime	
.mov
video/quicktime	Quicktime	
.mp4
video/quicktime	Quicktime - Session Description Protocol	
.sdp
application/x-quicktimeplayer	Quicktime	
.mov
Disable
Default Plug-in - Version: 1
Provides functionality for installing third-party plug-ins
Name:	Default Plug-in
Description:	Provides functionality for installing third-party plug-ins
Version:	1
Location:	default_plugin
 	 Disable
MIME types:	
MIME type	Description	File extensions
*		
Disable
```

Edit: Code tags added

---

### Post by vasa1 on 2011-09-19
> **TheHimself said:**
> But Chrome doesn't seem to have a plugin folder.
...

Do you have **/usr/lib/adobe-flashplugin/** ?
You could trying copying libflashplayer.so into there because that maybe where Google Chrome looks for it based on what I see for my 32-bit Chrome:
```

Name: Shockwave Flash
Version: 10.3 r183
Location: /usr/lib/adobe-flashplugin/libflashplayer.so

```

---

### Post by TheHimself on 2011-09-27
> **vasa1 said:**
> Do you have **/usr/lib/adobe-flashplugin/** ?
You could trying copying libflashplayer.so into there because that maybe where Google Chrome looks for it based on what I see for my 32-bit Chrome:
```

Name: Shockwave Flash
Version: 10.3 r183
Location: /usr/lib/adobe-flashplugin/libflashplayer.so

```

Even that doesn't help. ](*,)

---

### Post by TheHimself on 2011-09-29
Here is what I did:

1-Installed chromium
2-Copied the files in google-chrom's settings directory to chromium's
3-Reinstalled flash-plugin-installer.

And now chromium works.

---

### Post by maul9999 on 2011-09-29
> **TheHimself said:**
> I have firefox and it can display flash content. However Chrome is supposed to have an integrated flash plugin which I couldn't find.

Chrome isn't always "integrated flash plugin" true, that is why i always download adobe flash.

---

