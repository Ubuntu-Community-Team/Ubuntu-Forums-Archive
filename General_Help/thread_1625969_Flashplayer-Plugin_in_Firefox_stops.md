---
title: "Flashplayer-Plugin in Firefox stops"
date: 2010-11-19
forum: General Help
---

### Post by frotscher on 2010-11-19
Hi,

I've got a strange problem (but who doesn't?) with my flashplayer-plugin in firefox. Normally it works fine but in some cases, when I open a second website using the flashplayer at least one of the two become grey. Let give me an example:

I'm watching a youtube video in one tab and open a website in a second tab that also contains flashplayer contents, e.g. again youtube. At least in the first tab the part of the site where the video should be displayed becomes grey but mostly both of them are. The sound also disappears but all the other contents of the website are displayed correctly and a reloading of the site is successful. So I think the error can be reduced to the flashplayer.

Unfortunately the error is not reproducible that means sometimes it appears sometimes it doesn't. I'm using Ubuntu 10.04 and a call of "about:plugins" in the firefox adress field yields:
```

**VLC Multimedia Plugin (compatible Totem 2.30.2)**

 File:  libtotem-cone-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File:  libtotem-gmp-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **DivX® Web Player**

 File:  libtotem-mully-plugin.soVersion:   DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.6.6**

 File:  libtotem-narrowspace-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **iTunes Application Detector**

 File:  librhythmbox-itms-detection-plugin.soVersion:   This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.   MIME Type Description Suffixes Enabled    application/itunes-plugin 

Yes  **Shockwave Flash**

 File:  npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r102   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes
```Do you know a solution? Do I use a wrong plugin and/or can I use another one that works?

Thanks for any help,

Ralf

---

