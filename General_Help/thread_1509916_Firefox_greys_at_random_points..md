---
title: "Firefox greys at random points."
date: 2010-06-14
forum: General Help
---

### Post by themarker0 on 2010-06-14
Hey i'm having issues with firefox on lucid lynx. 

It happens whenever. Usually 15-25 minutes after i finished youtube or a flash game. Not during. Conky shows CPU maxed. If i use flash in any other browser, it works fine. No issue, unable to replicate.

---

### Post by lovinglinux on 2010-06-14
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by themarker0 on 2010-06-17
> **lovinglinux said:**
> Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

Flash doesn't show up on that list for some reason :/


```
  **Installed plugins**

 Find more information about browser plugins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Help for installing plugins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **IcedTea NPR Web Browser Plugin (using IcedTea6 1.8  (6b18-1.8-0ubuntu1))**

 File:  /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.soVersion:   The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8  (6b18-1.8-0ubuntu1)) executes Java applets.   MIME Type Description Suffixes Enabled    application/x-java-vm IcedTea class,jar Yes   application/x-java-applet IcedTea class,jar Yes   application/x-java-applet;version=1.1 IcedTea class,jar Yes   application/x-java-applet;version=1.1.1 IcedTea class,jar Yes   application/x-java-applet;version=1.1.2 IcedTea class,jar Yes   application/x-java-applet;version=1.1.3 IcedTea class,jar Yes   application/x-java-applet;version=1.2 IcedTea class,jar Yes   application/x-java-applet;version=1.2.1 IcedTea class,jar Yes   application/x-java-applet;version=1.2.2 IcedTea class,jar Yes   application/x-java-applet;version=1.3 IcedTea class,jar Yes   application/x-java-applet;version=1.3.1 IcedTea class,jar Yes   application/x-java-applet;version=1.4 IcedTea class,jar Yes   application/x-java-applet;version=1.4.1 IcedTea class,jar Yes   application/x-java-applet;version=1.4.2 IcedTea class,jar Yes   application/x-java-applet;version=1.5 IcedTea class,jar Yes   application/x-java-applet;version=1.6 IcedTea class,jar Yes   application/x-java-applet;jpi-version=1.6.0_18 IcedTea class,jar Yes   application/x-java-bean IcedTea class,jar Yes   application/x-java-bean;version=1.1 IcedTea class,jar Yes   application/x-java-bean;version=1.1.1 IcedTea class,jar Yes   application/x-java-bean;version=1.1.2 IcedTea class,jar Yes   application/x-java-bean;version=1.1.3 IcedTea class,jar Yes   application/x-java-bean;version=1.2 IcedTea class,jar Yes   application/x-java-bean;version=1.2.1 IcedTea class,jar Yes   application/x-java-bean;version=1.2.2 IcedTea class,jar Yes   application/x-java-bean;version=1.3 IcedTea class,jar Yes   application/x-java-bean;version=1.3.1 IcedTea class,jar Yes   application/x-java-bean;version=1.4 IcedTea class,jar Yes   application/x-java-bean;version=1.4.1 IcedTea class,jar Yes   application/x-java-bean;version=1.4.2 IcedTea class,jar Yes   application/x-java-bean;version=1.5 IcedTea class,jar Yes   application/x-java-bean;version=1.6 IcedTea class,jar Yes   application/x-java-bean;jpi-version=1.6.0_18 IcedTea class,jar Yes  **VLC Multimedia Plugin (compatible  Totem 2.30.2)**

 File:  /usr/lib/mozilla/plugins/libtotem-cone-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2  plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10  (compatible; Totem)**

 File:  /usr/lib/mozilla/plugins/libtotem-gmp-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2  plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **DivX® Web Player**

 File:  /usr/lib/mozilla/plugins/libtotem-mully-plugin.soVersion:   DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.6.6**

 File:  /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2  plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **iTunes Application Detector**

 File:  /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.soVersion:   This plug-in detects the presence of iTunes when opening iTunes Store  URLs in a web page with Firefox.   MIME Type Description Suffixes Enabled    application/itunes-plugin 

Yes   
  
```

---

### Post by lovinglinux on 2010-06-19
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by themarker0 on 2010-06-19
> **lovinglinux said:**
> Install [FLASH-AID]("http://flash-aid-extension.blogspot.com") extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR=Sienna]**Flash Optimization**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

I will thank you, i will report tomorrow.

---

### Post by lovinglinux on 2010-06-27
What is the current status of your situation?

---

### Post by themarker0 on 2010-06-28
> **lovinglinux said:**
> What is the current status of your situation?

I wiped and put Karmic on. Too much was wrong in lucid.

---

### Post by lovinglinux on 2010-06-29
> **themarker0 said:**
> I wiped and put Karmic on. Too much was wrong in lucid.

Ok then.

---

