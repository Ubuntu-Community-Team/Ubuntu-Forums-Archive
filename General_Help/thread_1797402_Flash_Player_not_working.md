---
title: "Flash Player not working?"
date: 2011-07-05
forum: General Help
---

### Post by itz_speld_rong on 2011-07-05
No videos will play on either Youtube or Yahoo so I feel it safe to accuse my browser (or flash player?) of being at fault.

I'm using the most up to date version of Natty,

I just watched videos last night... Suggestions?


Edit: Most up to date Adobe Flash as well (10.3.181.34)

---

### Post by uRock on 2011-07-05
Install and run the [FlashAid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") add on in Firefox.

---

### Post by Alwimo on 2011-07-05
I can watch flash videos, but other flash content in websites is dodgy.
 
I see lots of squares on this page [www.gamearena.com.au]("http://www.gamearena.com.au") in 64 bit but not 32 bit.
 
I tried flash aid but it didn't help.
 
Is this the case for others?

---

### Post by raja.genupula on 2011-07-05
may be flash player crashed , resinstall it 


u can get it from adobe

---

### Post by itz_speld_rong on 2011-07-05
> **Alwimo said:**
> I can watch flash videos, but other flash content in websites is dodgy.
 
I see lots of squares on this page [www.gamearena.com.au]("http://www.gamearena.com.au") in 64 bit but not 32 bit.
 
I tried flash aid but it didn't help.
 
Is this the case for others?

Same problem... I've seen this on multiple websites and it's another issue I would like to address. >_<

---

### Post by nomko on 2011-07-05
Did you also installed the ubuntu-restricted-extra package which can be found in synaptic?

---

### Post by garvinrick4 on 2011-07-05
> **Alwimo said:**
> I can watch flash videos, but other flash content in websites is dodgy.
 
I see lots of squares on this page [www.gamearena.com.au]("http://www.gamearena.com.au") in 64 bit but not 32 bit.
 
I tried flash aid but it didn't help.
 
Is this the case for others?
That site uses about twice the cpu usage than you tube for me. Do you have a recent processor? How much is being used of it on that site. Can type "top" into terminal or
use the package "gnome-system-monitor" I believe it is.

---

### Post by itz_speld_rong on 2011-07-05
> **nomko said:**
> Did you also installed the ubuntu-restricted-extra package which can be found in synaptic?

Trying this now...

I can hardly keep up with the suggestions. 

Reinstall and ad-ons didn't help.

---

### Post by itz_speld_rong on 2011-07-05
> **nomko said:**
> Did you also installed the ubuntu-restricted-extra package which can be found in synaptic?
This didn't work either..


Just a big black box where the video should be... :(

---

### Post by Alwimo on 2011-07-05
> **garvinrick4 said:**
> That site uses about twice the cpu usage  than you tube for me. Do you have a recent processor? How much is being  used of it on that site. Can type "top" into terminal or
use the package "gnome-system-monitor" I believe it is.
Is firefox-bin what I am supposed to look at? It uses about 59 MiB playing a YouTube right after Firefox 5 was  opened, and about 64 MiB on the Game Arena site right after Firefox 5  was opened, 86.3 MiB if it is playing a video.

My system says it has the following specifications:
Memory: 3.6 GiB
Processor 0: Intel(R) Core(TM) i5 CPU  M 460 @ 2.53GHz
Processor 1: Intel(R) Core(TM) i5 CPU  M 460 @ 2.53GHz
Processor 2: Intel(R) Core(TM) i5 CPU  M 460 @ 2.53GHz
Processor 3: Intel(R) Core(TM) i5 CPU  M 460 @ 2.53GHz

---

### Post by nomko on 2011-07-05
Yes, firefox-bin is the one you're looking for and to kill.

---

### Post by Alwimo on 2011-07-05
Thank you. But I don't think I want to kill it.

---

### Post by nomko on 2011-07-05
Why not? It's not gonna harm your system in any way. After killing it you can restart Firefox the normal way.

---

### Post by Alwimo on 2011-07-05
I mean that it wouldn't fix the problem.

---

### Post by mikejonesey on 2011-07-05
have you guys tried downloadings flash player direct from adobe? i use the 64bit "unstable" shared libary version, have been for a while and all works just fine...

---

### Post by nomko on 2011-07-05
The "original" Flash player from Adobe is a bit of a security risk. Better is to use the flashplugin-nonfree from the repository. But then again, it could work for the topic starter. 
 
@Alwimo:
Just give it a shot! You migth never know!

---

### Post by lulled on 2011-07-05
I'm facing a similar problem with YouTube. I can't load any videos from YouTube.com but oddly I can watch YouTube videos I posted on my blog. Ah, and the same thing happens on Firefox and Chrome. Does it make any sense to anyone here?

---

### Post by lovinglinux on 2011-07-05
Please click Flash-Aid icon in the toolbar, select Help >>> Generate report, then paste the results here.

---

### Post by lulled on 2011-07-05
@lovinglinux
I have Flash-Aid installed here, but I don't see a "Help" option. :oops:

---

### Post by lovinglinux on 2011-07-05
> **lulled said:**
> @lovinglinux
I have Flash-Aid installed here, but I don't see a "Help" option. :oops:

Right-click on a toolbar, select "customize", then drag the Flash-Aid icon to the toolbar.

---

### Post by lulled on 2011-07-05
Thanks. Here it goes

```

Ubuntu Architecture

Linux luis-note 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-5.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
google-chrome.list.save
mozillateam-firefox-stable-lucid.list

Flash packages

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so


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
Arch:x86_64-gcc3:$

[PLUGINS]
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1277465636000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:Vídeo do QuickTime:mov:$
1:video/mp4:Vídeo MPEG-4:mp4:$
2:image/x-macpaint:Imagem de bitmap do MacPaint:pntg:$
3:image/x-quicktime:Desenho do Macintosh Quickdraw/PICT:pict, pict1, pict2:$
4:video/x-m4v:Vídeo MPEG-4:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1274282974000:1:5:$
DivX Web Player version 1.4.0.233:$
DivX® Web Player:$
1
0:video/divx:Vídeo AVI:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:Vídeo AVI:avi, wma, wmv:$
1:video/x-ms-asf-plugin:Vídeo ASF:asf, wmv:$
2:video/x-msvideo:Vídeo AVI:asf, wmv:$
3:video/x-ms-asf:Vídeo ASF:asf:$
4:video/x-ms-wmv:Vídeo do Windows Media:wmv:$
5:video/x-wmv:Vídeo do Windows Media:wmv:$
6:video/x-ms-wvx:Vídeo do Windows Media:wmv:$
7:video/x-ms-wm:Vídeo do Windows Media:wmv:$
8:video/x-ms-wmp:Vídeo do Windows Media:wmv:$
9:application/x-ms-wms:Vídeo do Windows Media:wms:$
10:application/x-ms-wmp:Vídeo do Windows Media:wmp:$
11:application/asx:Lista de execução do Microsoft ASX:asx:$
12:audio/x-ms-wma:Áudio do Windows Media:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.30.2):$
19
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Arquivo multimídia Ogg:ogg:$
4:application/ogg:Arquivo multimídia Ogg:ogg:$
5:audio/ogg:Áudio Ogg:oga:$
6:audio/x-ogg:Áudio Ogg:ogg:$
7:video/ogg:Vídeo Ogg:ogv:$
8:video/x-ogg:Vídeo Ogg:ogg:$
9:application/annodex:Formato de troca Annodex:anx:$
10:audio/annodex:Áudio Annodex:axa:$
11:video/annodex:Vídeo Annodex:axv:$
12:video/mpeg:Vídeo MPEG:mpg, mpeg, mpe:$
13:audio/wav:Áudio WAV:wav:$
14:audio/x-wav:Áudio WAV:wav:$
15:audio/mpeg:Áudio MP3:mp3:$
16:application/x-nsv-vp3-mp3:Vídeo do Nullsoft:nsv:$
17:video/flv:Vídeo Flash:flv:$
18:application/x-totem-plugin:Totem Multimedia plugin::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1289952613000:1:1:$
Shockwave Flash 10.3 d162:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

[INVALID]

```

---

### Post by lovinglinux on 2011-07-05
> **lulled said:**
> Thanks. Here it goes

```

Ubuntu Architecture

Linux luis-note 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-5.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
google-chrome.list.save
mozillateam-firefox-stable-lucid.list

Flash packages

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so


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
Arch:x86_64-gcc3:$

[PLUGINS]
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1277465636000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:Vídeo do QuickTime:mov:$
1:video/mp4:Vídeo MPEG-4:mp4:$
2:image/x-macpaint:Imagem de bitmap do MacPaint:pntg:$
3:image/x-quicktime:Desenho do Macintosh Quickdraw/PICT:pict, pict1, pict2:$
4:video/x-m4v:Vídeo MPEG-4:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1274282974000:1:5:$
DivX Web Player version 1.4.0.233:$
DivX® Web Player:$
1
0:video/divx:Vídeo AVI:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:Vídeo AVI:avi, wma, wmv:$
1:video/x-ms-asf-plugin:Vídeo ASF:asf, wmv:$
2:video/x-msvideo:Vídeo AVI:asf, wmv:$
3:video/x-ms-asf:Vídeo ASF:asf:$
4:video/x-ms-wmv:Vídeo do Windows Media:wmv:$
5:video/x-wmv:Vídeo do Windows Media:wmv:$
6:video/x-ms-wvx:Vídeo do Windows Media:wmv:$
7:video/x-ms-wm:Vídeo do Windows Media:wmv:$
8:video/x-ms-wmp:Vídeo do Windows Media:wmv:$
9:application/x-ms-wms:Vídeo do Windows Media:wms:$
10:application/x-ms-wmp:Vídeo do Windows Media:wmp:$
11:application/asx:Lista de execução do Microsoft ASX:asx:$
12:audio/x-ms-wma:Áudio do Windows Media:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.30.2):$
19
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Arquivo multimídia Ogg:ogg:$
4:application/ogg:Arquivo multimídia Ogg:ogg:$
5:audio/ogg:Áudio Ogg:oga:$
6:audio/x-ogg:Áudio Ogg:ogg:$
7:video/ogg:Vídeo Ogg:ogv:$
8:video/x-ogg:Vídeo Ogg:ogg:$
9:application/annodex:Formato de troca Annodex:anx:$
10:audio/annodex:Áudio Annodex:axa:$
11:video/annodex:Vídeo Annodex:axv:$
12:video/mpeg:Vídeo MPEG:mpg, mpeg, mpe:$
13:audio/wav:Áudio WAV:wav:$
14:audio/x-wav:Áudio WAV:wav:$
15:audio/mpeg:Áudio MP3:mp3:$
16:application/x-nsv-vp3-mp3:Vídeo do Nullsoft:nsv:$
17:video/flv:Vídeo Flash:flv:$
18:application/x-totem-plugin:Totem Multimedia plugin::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1289952613000:1:1:$
Shockwave Flash 10.3 d162:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

[INVALID]

```

Nothing wrong in your report. But please paste the result of:

```
file /usr/lib/xulrunner-addons/plugins/libflashplayer.so
```

You could try to block YouTube cookies. Most likely that they are causing the problem, since you can watch videos embedded on other sites. YouTube cookies has some history of causing such issues.

---

### Post by lulled on 2011-07-05
Thank you for your help
Here it goes

```
file /usr/lib/xulrunner-addons/plugins/libflashplayer.so 
/usr/lib/xulrunner-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'

```Then 
```
file /usr/lib/mozilla/plugins/libflashplayer.so 
/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
```I'll see if blocking youtube's cookies will do. Thanks again.

---

### Post by lovinglinux on 2011-07-05
> **lulled said:**
> Thank you for your help
Here it goes

```
file /usr/lib/xulrunner-addons/plugins/libflashplayer.so 
/usr/lib/xulrunner-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'

```Then 
```
file /usr/lib/mozilla/plugins/libflashplayer.so 
/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
```I'll see if blocking youtube's cookies will do. Thanks again.

I just wanted to make sure that file was pointing to the correct path. It is.

I suppose is the cookie problem. Let me know if it works.

---

### Post by lulled on 2011-07-05
Thank you very much for your efforts to help me out here, but I disabled cookies from YouTube and still it won't load. When I right-click the black screen of what should be the video, one disabled option of the menu is "Movie not loaded..." (or something like that, mine is in Portuguese). Does that ring a bell?

Thanks a lot again.

---

### Post by lovinglinux on 2011-07-05
> **lulled said:**
> Thank you very much for your efforts to help me out here, but I disabled cookies from YouTube and still it won't load. When I right-click the black screen of what should be the video, one disabled option of the menu is "Movie not loaded..." (or something like that, mine is in Portuguese). Does that ring a bell?

Thanks a lot again.

Have you tried to install the flash from the repositories? Just run Flash-Aid Wizard again and select the stable flash version. It might help.

You could also try to disable hardware acceleration in the movie right-click options.

Another alternative is to use my [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/") extension, that allows to watch YouTube with a much better plugin.

---

### Post by itz_speld_rong on 2011-07-06
This seems to be a somewhat widespread problem... Possibly an Adobe update?

Edit: The "FlashVideoReplacer" shows a loading bar and the first frame of a youtube video but doesn't want to actually play it. The "FlashAid" hasn't done a thing for me thus far.

---

### Post by Chicharito14 on 2011-07-06
I installed flash aid for firefox and the videos still do not work... And i dont think it was an adobe update because i was using the same adobe flash player like a minute before... I had problems with ubuntu when my laptop suddenly dies

---

### Post by Alwimo on 2011-07-06
Installing Chromium is a work-around for the [www.gamearena.com](www.gamearena.com) problem.

---

### Post by Chicharito14 on 2011-07-06
I just installed flashblocker like one guy suggested and it now shows the video as it is loading but it does not play it there just still shots with no sound

---

### Post by lovinglinux on 2011-07-06
> **itz_speld_rong said:**
> This seems to be a somewhat widespread problem... Possibly an Adobe update?

Edit: The "FlashVideoReplacer" shows a loading bar and the first frame of a youtube video but doesn't want to actually play it. The "FlashAid" hasn't done a thing for me thus far.

The recommended plugin to be used with FlashVideoReplacer is gecko-mediaplayer. If you are using Totem plugin, then set the Mime Type in FVR preferences to Totem (application/x-totem-plugin).

---

### Post by itz_speld_rong on 2011-07-06
I have a video working on Youtube.

I just clicked "FlashAid" and went to Quick Mode -> Install Stable Flash

Now I think the "FlashVideoReplacer" and the "FlashAid" are working together.

I still would prefer "Adobe Flash Player" and I hope this problem is resolved so I can use it again. >_<

---

### Post by itz_speld_rong on 2011-07-06
And, after posting the previous, I find that it only played maybe 15 seconds before wigging out and losing sound and the video freezing and skipping. These two ad-ons seem to be flooding my NIC probably 10x more than the AdobeFlashPlayer ever did.

---

### Post by itz_speld_rong on 2011-07-06
> **itz_speld_rong said:**
> These two ad-ons seem to be flooding my NIC probably 10x more than the AdobeFlashPlayer ever did.

I'm thinking this is because the video is being downloaded faster than what Adobe was doing.

---

### Post by lovinglinux on 2011-07-06
> **Chicharito14 said:**
> I just installed flashblocker like one guy suggested and it now shows the video as it is loading but it does not play it there just still shots with no sound

I don't see any suggestion about Flashblock here. It won't solve your flash problems. However, it is highly recommended to prevent websites from running unnecessary flash objects, which could lead to excessive CPU usage.

> **Chicharito14 said:**
> I installed flash aid for firefox and the videos still do not work... And i dont think it was an adobe update because i was using the same adobe flash player like a minute before... I had problems with ubuntu when my laptop suddenly dies

Have you executed Flash-Aid Wizard? Just installing Flash-Aid doesn't do anything. You need to run the Wizard so it can detect your system settings, remove flash, install the latest version apply some tweaks.

> **itz_speld_rong said:**
> This seems to be a somewhat widespread problem... Possibly an Adobe update?...

...The "FlashAid" hasn't done a thing for me thus far.

> **itz_speld_rong said:**
> I have a video working on Youtube.

I just clicked "FlashAid" and went to Quick Mode -> Install Stable Flash

Now I think the "FlashVideoReplacer" and the "FlashAid" are working together.

I still would prefer "Adobe Flash Player" and I hope this problem is resolved so I can use it again. >_<

> **itz_speld_rong said:**
> And, after posting the previous, I find that it only played maybe 15 seconds before wigging out and losing sound and the video freezing and skipping. These two ad-ons seem to be flooding my NIC probably 10x more than the AdobeFlashPlayer ever did.

Please let explain what Flash-Aid is and what it does. Essentially, it is a script generator that detects some system information, like installed flash plugins on several locations, OS architecture and common issues on config files related to flash. Then Flash-Aid prompts you for installation, removal and tweaking options and generate a script according to your system specs and personal choices. It can execute the script for you, which removes any conflicting plugins, install the selected flash version and apply performance tweaks. This is the Wizard Mode. The Quick Mode you have used select the best choices by default and skip all the questions, but essentially does the same thing: remove conflicting flash plugins, install the best version and apply tweaks, nothing more.

Flash-Aid can solve many issues, but not all of them. But even if it doesn't solve your problem, at least it eliminates many sources of common issues. Please use the Flash-Aid report generation as suggested, so I can have a better picture of of problem. Also please specify if the problem occurs only on YouTube, fullscreen etc.

After Flash-Aid generates the script and execute it, it doesn't do anything. It just sits there. The only thing it does is to check if there is a new flash version once a day. To do that, it communicates with my web site and download a very tiny json file that only has a timestamp. That's it.

Flash-Aid doesn't communicate with FlashVideoReplacer in any way.

What about FlashVideoReplacer? The extension only activates when you visit a supported video site, like YouTube. Once you open a video page, FVR inspects the page for the original video files urls (sometimes it queries the host for additional xml info) and saves that information. Then it removes the flash video object from the page and puts a placeholder on its place. When you click the placeholder, FVR put the video object back in place, but this time using another mime type, so your browser can play it with a different plugin. When you actually play the video, is not FVR that is working any more, is the video plugin. FVR job is to replace the video so you can play it with a different plugin. If the video doesn't load, the is the plugin that needs some tweaking or you need a different plugin. While FVR works with many plugins on Linux, the best option is gecko-mediaplayer. VLC plugin is worthless and Totem only works well if you change the Mime Type as I mentioned on my previous post.

So what is the advantage of FVR? Essentially performance. Flash sucks on Linux and uses too much CPU, which causes video stuttering and overheating, because it cannot use xv output. Depending on the site, it cannot even use hardware acceleration, which makes thing even worse. Some sites like YouTube work considerably well, because it can use hardware acceleration. However, it doesn't play well with Compiz, which is the thing that makes all the fancy animation on your desktop.

When you use FVR, you can actually play the videos with a decent plugin that makes use of hardware acceleration and xv output, reducing CPU usage a LOT. In your case, it also allows you to watch the videos, since Flash doesn't want to work.

---

### Post by lovinglinux on 2011-07-06
> **itz_speld_rong said:**
> I'm thinking this is because the video is being downloaded faster than what Adobe was doing.

Probably, since it doesn't download anything else other than the original video. See my previous post.

What happens is that YouTube intentionally caps your download speed. I am not sure if using a different plugin can bypass the cap, but depending on the resolution chosen, speed may vary considerably. The size of the download file doesn't change tho and only depends on the resolution chosen in FVR placeholder. You might want to reduce the quality of the video if you are experiencing network issues.

Which plugin are you using to play the videos?

If the embedded mode doesn't work well for you, FVR can also play the videos with external players. Just select the Standalone option in the placeholder or the preferences.

---

### Post by whatthefunk on 2011-07-06
Same problem here.  Firefox played youtube videos fine until a couple days ago.  Now it just says "An error occurred.  Please try again later."  Videos still work with Chromium.  Anybody know whats going on?

---

### Post by whatthefunk on 2011-07-06
[http://ubuntuforums.org/showthread.php?t=1280836&page=2](http://ubuntuforums.org/showthread.php?t=1280836&page=2)

This worked for me.  Delete the cookies and disable cookies from youtube.

---

### Post by lovinglinux on 2011-07-06
> **whatthefunk said:**
> Same problem here.  Firefox played youtube videos fine until a couple days ago.  Now it just says "An error occurred.  Please try again later."  Videos still work with Chromium.  Anybody know whats going on?

Trying to figure out, but seems to be one of those events that screwed YouTube playing for a lot of people some time ago. Probably related to YouTube cookies.

Does it work on other sites? If yes, then try to block YouTube cookies in Firefox preferences.

---

### Post by Rob Glenn on 2011-07-06
Upgrading to the latest Flash version using FlashAid, either stable or beta, killed YouTube for me.  No video, just a beige region, right-clicking gives a menu with the entries "Movie not loaded", "About Adobe Flash <whatever>".  Tried the debug player as well, it generated an empty log. Clearing Youtube's cookies had no effect.  Downgrading to Flash 10.2 got Youtube working again.  This appears to be Youtube-specific as other sites such as Metacafe and some unmentionables work fine with the latest version.  Looks like someone might've broke something!  Anyone have any thoughts on what might be up with this?

---

### Post by Rob Glenn on 2011-07-06
Now 10.2 quit working as well.  Oh man...

---

### Post by lovinglinux on 2011-07-06
> **Rob Glenn said:**
> Now 10.2 quit working as well.  Oh man...

Even after blocking cookies?

---

### Post by whatthefunk on 2011-07-06
Blocking cookies seems to be the solution...

---

### Post by lulled on 2011-07-06
Blocking cookies worked for me. I said previously that it didn't, well, actually, what happened, is that I wasn't doing it right. :oops:
On Opera, where I can see clearly what sites I'm blocking cookies from (I have to find a way to specify what sites I don't want cookies from on Firefox and Chrome), I blocked cookies from YouTube and voilá, it worked. Many thanks for your help.

---

### Post by itz_speld_rong on 2011-07-06
I deleted the cookies  and cache and re-installed the Adobe Flash and it's up and working again. I think I'll keep FlashAid still, but the "FlashVideoReplacer" wasn't exactly useful. 

Thanks for all the help guys.

---

### Post by lovinglinux on 2011-07-07
See [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

---

### Post by In Flames We Trust on 2011-07-07
I was having this same issue with there just being a black box where the video was suppose to be, so I installed FVR and installed the recommended plugins and it worked immediately. Thanks!\\:D/

---

### Post by silverlady37 on 2011-07-08
> **Alwimo said:**
> I can watch flash videos, but other flash content in websites is dodgy.
 
I see lots of squares on this page [www.gamearena.com.au]("http://www.gamearena.com.au") in 64 bit but not 32 bit.
 
I tried flash aid but it didn't help.[[COLOR="White"]flash mp3 player[/COLOR]]("www.spencer-tech.com/my_scripts/mp3_player")
 
Is this the case for others?
 
Unfortunately that doesn't really work..sorry.

---

### Post by sbol1 on 2012-04-10
I just wanted to post a quick but grateful thank you!  I'm really new to Ubuntu Linux and do like it now that I'm gettin' the hang of things a little.  However, I was very frustrated with very similar Youtube issues.  FlashVideoReplacer was finally my solution after I'd gone through many of the thread suggestions.  Keep up the great work of this site!!  It's great to have help when you're lost!! LOL!

---

