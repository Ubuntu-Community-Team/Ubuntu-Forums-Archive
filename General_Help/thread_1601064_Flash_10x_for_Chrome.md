---
title: "Flash 10x for Chrome"
date: 2010-10-19
forum: General Help
---

### Post by stat30fbliss on 2010-10-19
I am having a hard time getting flash working in my freshly updated version of chrome.  Is there no way to get these to work, or am I missing something all together?

Thank you

---

### Post by TBABill on 2010-10-19
Flash comes with Chromium. What type of problems are you encountering? Specific sites that won't work? If you can post some sites/links I can try to test from my Chromium to confirm.

Edit: Click the wrench, about Chromium...what is the version number?

---

### Post by stat30fbliss on 2010-10-19
I dont have chromium, I have actual google chrome, downloaded from the google page.  Install was a breeze, and when I try to watch any flash based videos, i get notified that I do not have flash.  Once I click on the get flash icon, adobe tells me I have an up to date version... 

YouTube works, but a lot of 3rd party sites I find when stumbling dont work. I also design websites in flash, so I need to find how I can make this compatible with linux.

---

### Post by ThePhysician on 2010-10-19
I installed Chrome from google.com/chrome as well, and while all Flash websites do work.. the plugin will frequently crash.

But what you're saying is that certain pages actually say you don't have flash? Is everything up to date on your system?

---

### Post by TBABill on 2010-10-19
Have you tried to install Chromium from the repos to see if performance is better than Chrome? That doesn't fix the Chrome issue, but it's an external app from the repo so it may not have as many users to assist.

---

### Post by efflandt on 2010-10-19
Google Chrome is supposed to come with the most recent flash version, which should be updated automatically by Chrome according to Adobe.com.  Go to this page and see what Flash version it shows [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

The Google Chrome flash plugin is called flashplayergc.so instead of flashplayer.so.  See this to use different than the default [http://kb2.adobe.com/cps/839/cpsid_83950.html](http://kb2.adobe.com/cps/839/cpsid_83950.html)

I don't know if Chromium includes flash or not (/usr/lib/chromium-browser/plugins/ is empty), but in 64-bit Maverick the about link above shows that my Chromium is using Flash 10.2.161.22, same as real 64-bit flash that I installed for Firefox and Hulu Desktop.  The most recent normal flash version is 10.1.85.3.

PS: The only site I am aware of which does not work with flash in Chromium, but does work with Firefox, is cbs.com, and someone in a thread about that speculated that it might be blocked by CBS due to Google TV.

---

### Post by stat30fbliss on 2010-10-20
Yeah it can seem to be a bit glitchy on when it does and does not want to work.  

I am noticing the stats in my wordpress.org blog not showing up saying plugin missing regularly, and other videos or flash apps I may stumble across. 

Firefox seems a bit more stable which sucks cause I LOVE chrome...

---

### Post by VMC on 2010-10-20
Open a new page and type: ***about:plugins*** into the URL, then details to see what version flash your using and if enabled.

---

### Post by stat30fbliss on 2010-10-20
Here is what my **about: plugins** page said:

```

Plug-ins (7)        
Details
Default Plug-in - Version: 1
Provides functionality for installing third-party plug-ins
Name:    Default Plug-in
Description:    Provides functionality for installing third-party plug-ins
Version:    1
Priority:    6
Location:    default_plugin
      Disable
MIME types:    
MIME type    Description    File extensions
*        
.
Disable
Chrome PDF Viewer (Disabled)
Portable Document Format
Name:    Chrome PDF Viewer
Description:    Portable Document Format
Version:    
Priority:    0
Location:    /opt/google/chrome/libpdf.so
     (Disabled) Enable
MIME types:    
MIME type    Description    File extensions
application/pdf        
.pdf
Enable

iTunes Application Detector
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Name:    iTunes Application Detector
Description:    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Version:    
Priority:    1
Location:    /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
      Disable
MIME types:    
MIME type    Description    File extensions
application/itunes-plugin        
.
Disable

VLC Multimedia Plugin (compatible Totem 2.30.2)
The Totem 2.30.2 plugin handles video and audio streams.
Name:    VLC Multimedia Plugin (compatible Totem 2.30.2)
Description:    The Totem 2.30.2 plugin handles video and audio streams.
Version:    
Priority:    2
Location:    /usr/lib/mozilla/plugins/libtotem-cone-plugin.so
      Disable
MIME types:    
MIME type    Description    File extensions
application/x-vlc-plugin    VLC Multimedia Plugin    
.
application/vlc    VLC Multimedia Plugin    
.
video/x-google-vlc-plugin    VLC Multimedia Plugin    
.
application/x-ogg    Ogg multimedia file    
.ogg
application/ogg    Ogg multimedia file    
.ogg
audio/ogg    Ogg Audio    
.oga
audio/x-ogg    Ogg Audio    
.ogg
video/ogg    Ogg Video    
.ogv
video/x-ogg    Ogg Video    
.ogg
application/annodex    Annodex exchange format    
.anx
audio/annodex    Annodex Audio    
.axa
video/annodex    Annodex Video    
.axv
video/mpeg    MPEG video    
.mpg    .mpeg    .mpe
audio/wav    WAV audio    
.wav
audio/x-wav    WAV audio    
.wav
audio/mpeg    MP3 audio    
.mp3
application/x-nsv-vp3-mp3    NullSoft video    
.nsv
video/flv    Flash video    
.flv
application/x-totem-plugin    Totem Multimedia plugin    
.
Disable

Windows Media Player Plug-in 10 (compatible; Totem)
The Totem 2.30.2 plugin handles video and audio streams.
Name:    Windows Media Player Plug-in 10 (compatible; Totem)
Description:    The Totem 2.30.2 plugin handles video and audio streams.
Version:    
Priority:    3
Location:    /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
      Disable
MIME types:    
MIME type    Description    File extensions
application/x-mplayer2    AVI video    
.avi    .wma    .wmv
video/x-ms-asf-plugin    ASF video    
.asf    .wmv
video/x-msvideo    AVI video    
.asf    .wmv
video/x-ms-asf    ASF video    
.asf
video/x-ms-wmv    Windows Media video    
.wmv
video/x-wmv    Windows Media video    
.wmv
video/x-ms-wvx    Windows Media video    
.wmv
video/x-ms-wm    Windows Media video    
.wmv
video/x-ms-wmp    Windows Media video    
.wmv
application/x-ms-wms    Windows Media video    
.wms
application/x-ms-wmp    Windows Media video    
.wmp
application/asx    Microsoft ASX playlist    
.asx
audio/x-ms-wma    Windows Media audio    
.wma
Disable

DivX® Web Player
DivX Web Player version 1.4.0.233
Name:    DivX® Web Player
Description:    DivX Web Player version 1.4.0.233
Version:    
Priority:    4
Location:    /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
      Disable
MIME types:    
MIME type    Description    File extensions
video/divx    AVI video    
.divx
Disable

QuickTime Plug-in 7.6.6
The Totem 2.30.2 plugin handles video and audio streams.
Name:    QuickTime Plug-in 7.6.6
Description:    The Totem 2.30.2 plugin handles video and audio streams.
Version:    
Priority:    5
Location:    /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
      Disable
MIME types:    
MIME type    Description    File extensions
video/quicktime    QuickTime video    
.mov
video/mp4    MPEG-4 video    
.mp4
image/x-macpaint    MacPaint Bitmap image    
.pntg
image/x-quicktime    Macintosh Quickdraw/PICT drawing    
.pict    .pict1    .pict2
video/x-m4v    MPEG-4 video    
.m4v
Disable
```

I see nothing there that even relates to flash.  

I also found that the thumbnails on YouTube display, but when I click to view the files, whether it is with Chrome, Chromium, or Firefox I cannot seem to view any flash videos what so ever...

---

### Post by moma on 2010-10-20
Hello,

Follow [this guide...]("http://www.futuredesktop.org/#step6") to setup Flash & Java in Ubuntu 10.10. Look for steps 6b and 6c. I prefer Chromium Browser over/to Chrome. See [Step 7a]("http://www.futuredesktop.org/#step7a").

---

### Post by stat30fbliss on 2010-10-20
> **moma said:**
> Hello,

Follow [this guide...]("http://www.futuredesktop.org/#step6") to setup Flash & Java in Ubuntu 10.10. Look for steps 6b and 6c. I prefer Chromium Browser over/to Chrome. See [Step 7a]("http://www.futuredesktop.org/#step7a").

That guide was very helpful!  Unfortunately, only the stats plugin for my wordpress blog work now.  I get a play button in the videos on YouTube now, but when I click play it streams blackness...

---

### Post by efflandt on 2010-10-20
Try **locate flashplayer.so** and **locate flashplayergc.so** (the Google Chrome version) and see if either of those comes up with anything.  If there is more than one, see of alternates are symlinks to the same file or if there is more than one actual file with same name and different size in different paths.  If you changed anything on your system lately you might try doing **sudo updatedb** (which runs from cron.daily)to make sure that the locate database is up to date first.

The only flashplayer on my system (which automatically works with Chromium) is the true 64-bit one I put there:

**locate flashplayer.so**
/usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by stat30fbliss on 2010-10-20
hmm I have **flashplugin-alternative.so** in that folder

---

### Post by ThePhysician on 2010-10-20
> **moma said:**
> Hello,

Follow [this guide...]("http://www.futuredesktop.org/#step6") to setup Flash & Java in Ubuntu 10.10. Look for steps 6b and 6c. I prefer Chromium Browser over/to Chrome. See [Step 7a]("http://www.futuredesktop.org/#step7a").

I prefer Chrome's extensions.

---

### Post by stat30fbliss on 2010-10-21
So I am getting some flash now.  My youtube widget in Screenlets worked fine, but I am still not getting any flash in any of my web browsers.  Some ads and my wordpress stats work in firefox, none in chrome, and no online videos work in either.

Help!

---

### Post by moma on 2010-10-22
Re-hello,

1) Try to get rid off all obsolete flashplayer.so and flashplayergc.so library files. Do as the user "efflandt" wrote in 
[http://ubuntuforums.org/showpost.php?p=10001993&postcount=12](http://ubuntuforums.org/showpost.php?p=10001993&postcount=12)

I simply repeat his commands here:
$ [COLOR="DarkGreen"]sudo updatedb[/COLOR] # this updates the file database
$ [COLOR="DarkGreen"]locate flashplayer[/COLOR]

Then sudo rm all flashplayer*.so files you find.

You are more likely to succeed when the base is clean.
----

2) Clean up your repositories. This is important if you upgraded from older Ubuntu to 10.10.
Remove all old, lucid based repos from the software sources.
[http://www.futuredesktop.org/maverick/images/picture-6aaa.png](http://www.futuredesktop.org/maverick/images/picture-6aaa.png) 
----

3) Update package index after clean up
$ [COLOR="DarkGreen"]sudo apt-get update [/COLOR]

----
3) Re-install a proper Flash-player. 
Do step 6a) and 6c) of [this...]("http://www.futuredesktop.org/#step6")
----

If all this fails, please do a re-installation. Stick to the guide FWIW.

---

