---
title: "An update ago (Flash/youtube)"
date: 2011-01-11
forum: General Help
---

### Post by Chasey on 2011-01-11
Using 10.10 everything worked great out of the box. After about 10 updates flash video from youtube.com ceased to work but the audio does. Pandora also politely informed me that adobe flash plug-in crashed. 

I'm not sure if it's flash to be Frank I went to adobe's site and tested the shockwave player and that little video/art did work! Also tried some stuff I've found in another post ```
 sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y

```This did not resolve the problem. Anybody else come across this? Thanks in advanced for any thoughts.

---

### Post by lovinglinux on 2011-01-11
[http://ubuntuforums.org/showthread.php?p=10337838](http://ubuntuforums.org/showthread.php?p=10337838)

---

### Post by Chasey on 2011-01-11
> **lovinglinux said:**
> [http://ubuntuforums.org/showthread.php?p=10337838](http://ubuntuforums.org/showthread.php?p=10337838)

Thanks lovinglinux I read and followed all the steps you provided but still only audio is working for these videos  :(

---

### Post by lovinglinux on 2011-01-11
> **Chasey said:**
> Thanks lovinglinux I read and followed all the steps you provided but still only audio is working for these videos  :(

Disable Compiz and see if it shows the video. Also, if you are using Flash-Aid, go to the Help tab, generate a report and post here.

---

### Post by Chasey on 2011-01-11
OK I disabled compiz... I think. System > Preferences > Appearance > Visual Effects > None (correct)

No video...

Here is the flash-aid report
Ubuntu Architecture

Linux Chaseyub 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.13/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

erik-b-andersen-rgba-gtk-maverick.list
erik-b-anderson-rgba-gtk-maverick.list
erik-b-anderson-rgba-gtk-maverick.list.save
tualatrix-ppa-maverick.list

Flash packages

Plugin locations


/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
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
Version:0.11:$

[PLUGINS]
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1289327780000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1285633033000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1285633033000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1285633033000:1:5:$
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
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1285633033000:1:5:$
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
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1289803589000:1:5:$
Shockwave Flash 10.2 d151:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$

*********************************************************

Thanks for your help with this mate!

1:application/futuresplash:FutureSplash Player:spl:$

---

### Post by lovinglinux on 2011-01-11
Your report shows everything is setup properly.

Try to start Firefox via terminal using the following command:

```
env XLIB_SKIP_ARGB_VISUALS=1 firefox
```

Let me know if the problem persists with that.

Also try to create a new Firefox profile and check if the problem persists.

---

### Post by Chasey on 2011-01-11
This is something weird... I tried some other sites with video like  justin.tv (I think it uses flash player) Anyways it's working! Youtube,  google videos and ted.com still only gives me audio and a gray area where  the video should play.

---

### Post by pqwoerituytrueiwoq on 2011-01-11
just to be sure the video is loading in flash and not html5
do you get the flash context menu when right-clicking on the gray spot?

---

### Post by Chasey on 2011-01-11
> **pqwoerituytrueiwoq said:**
> just to be sure the video is loading in flash and not html5
do you get the flash context menu when right-clicking on the gray spot?

Yes it is. 

Lovinglinux I launched Firefox with a new profile with the terminal there was no noticeable change.     

#-o

---

### Post by Chasey on 2011-01-11
OK I keep finding really bazaar stuff as I keep looking into it... Get this... Youtube videos will play on Facebook! I'm am really really stumped now. 

Thanks for your responses. I really do appreciate them.

---

### Post by lovinglinux on 2011-01-12
> **Chasey said:**
> OK I keep finding really bazaar stuff as I keep looking into it... Get this... Youtube videos will play on Facebook! I'm am really really stumped now. 

Thanks for your responses. I really do appreciate them.

I suspect it could be a cookie issue. Delete your cookies, the cache and the  /.macromedia folder (make a backup if you want to preserve games scores).

Also try [http://www.youtube-nocookie.com]("http://www.youtube-nocookie.com").

---

### Post by Chasey on 2011-01-12
> **lovinglinux said:**
> I suspect it could be a cookie issue. Delete your cookies, the cache and the  /.macromedia folder (make a backup if you want to preserve games scores).

Also try [http://www.youtube-nocookie.com](http://www.youtube-nocookie.com).


I've ran this ```
sudo /etc/init.d/nscd restart 
```and removed /.macromedia. Still nothing... Could there be something else that would be keeping video from playing only from youtube?

---

### Post by lovinglinux on 2011-01-12
> **Chasey said:**
> I've ran this ```
sudo /etc/init.d/nscd restart 
```and removed /.macromedia. Still nothing... Could there be something else that would be keeping video from playing only from youtube?

Since you can play embedded YouTube videos, but not on YouTube site is really weird. Usually is the other way, because of cookies.

Check if you are allowing cookies from Youtube.

---

### Post by Chasey on 2011-01-13
It is the strangest thing and once again I just want to thank you guys for your help. 

Still stuck BTW but this is what I've tried so far...

It seems obvious to me that the problem is with firefox so I tried to remove it via terminal and it's plug-ins and profile.

I'm starting to think I'm smart... Re-install and nothing... It's the same.

I've installed Chromium and video's will play in youtube. 

What am I doing wrong with firefox!? I'm a huge fan and have defended it for years! If one of you guys can point getting back to brand new firefox I would be ever so grateful.

---

### Post by lovinglinux on 2011-01-13
> **Chasey said:**
> It is the strangest thing and once again I just want to thank you guys for your help. 

Still stuck BTW but this is what I've tried so far...

It seems obvious to me that the problem is with firefox so I tried to remove it via terminal and it's plug-ins and profile.

I'm starting to think I'm smart... Re-install and nothing... It's the same.

I've installed Chromium and video's will play in youtube. 

What am I doing wrong with firefox!? I'm a huge fan and have defended it for years! If one of you guys can point getting back to brand new firefox I would be ever so grateful.

Try Firefox 4.

---

### Post by Chasey on 2011-01-17
> **lovinglinux said:**
> Try Firefox 4.

I've been working so I couldn't respond... I did install firefox 4 but the problem persist. (Head/desk)

---

### Post by lovinglinux on 2011-01-17
Have you tried to create a new Ubuntu user, just for testing?

---

### Post by Chasey on 2011-01-17
I didn't think about that but when I did same same audio no video :/

---

### Post by Chasey on 2011-01-17
Remember it was after a update before that it had worked. Kind of a side questions; Where can I view log files for system changes? Would that help to look at these?

---

### Post by Chasey on 2011-01-17
Remember it was after a update before that it had worked. Kind of a side questions; Where can I view log files for system changes? Would that help to look at these?

---

### Post by Chasey on 2011-01-17
Remember it was after a update before that it had worked. Kind of a side questions; Where can I view log files for system changes? Would that help to look at these?

---

### Post by Chasey on 2011-01-17
Remember it was after a update before that it had worked. Kind of a side questions; Where can I view log files for system changes? Would that help to look at these?

---

### Post by BbUiDgZ on 2011-01-17
try this.

```
mv ~/.mozilla ~/.mozilla-bk
```

then try firefox again
```
firefox http://youtube.com
```

if that still fails then move your mozilla folder back
```
mv ~/.mozilla-bk ~/.mozilla
```

---

### Post by Chasey on 2011-01-17
> **BbUiDgZ said:**
> try this.

```
mv ~/.mozilla ~/.mozilla-bk
```

then try firefox again
```
firefox http://youtube.com
```

if that still fails then move your mozilla folder back
```
mv ~/.mozilla-bk ~/.mozilla
```

Negative  ](*,)

---

### Post by theDaveTheRave on 2011-01-17
here's a thought, don't know if it will work.

do you run an apache server?

if you do, what about creating your own web page, and have an  [<iframe>]("http://www.w3.org/TR/html4/present/frames.html") that simply imports stuff from youtube - ie the whole page.

just to see if that will make the youtube stuff work.

when I'm not feeling so tired I could write a quick page for you, if others think it is an interesting test that is... (sorry 2 year old twins leave me feeling tired a lot !)

David

---

### Post by Chasey on 2011-01-17
> **theDaveTheRave said:**
> here's a thought, don't know if it will work.

do you run an apache server?

if you do, what about creating your own web page, and have an  [<iframe>]("http://www.w3.org/TR/html4/present/frames.html") that simply imports stuff from youtube - ie the whole page.

just to see if that will make the youtube stuff work.

when I'm not feeling so tired I could write a quick page for you, if others think it is an interesting test that is... (sorry 2 year old twins leave me feeling tired a lot !)


David

I bet it would work... Like I said in another post youtube videos do work when embedded on Facebook. That site is Apache/PHP based right? 

I don't run an apache server :( Not really at that level yet. Doesn't it come installed on ubuntu? You just have to set it up if I'm not mistaken right?

It would be a good test but it's not really practical for what I really want... To get to brass tax I'm trying to watch these Professor Messer videos [http://www.professormesser.com/microsoft-70-680/free-microsoft-70-680-training](http://www.professormesser.com/microsoft-70-680/free-microsoft-70-680-training) (Don't laugh) These videos are from youtube but when embedded on this site they don't work there either. Videos from youtube only seem to work when embedded on facebook.

---

### Post by theDaveTheRave on 2011-01-18
I couldn't say how facebook is powered.

But, it is 'video only' that is embeded. I'm suggesting showing the whole of the facebook site through a frame (not just the video), I will need to play a bit to see if this is possible.

I get the feeling that youtube has become so ubiquitous that people say that it is 'embeded youtube' when in actual fact it is just using the same back end technology as youtube do - or more precisely simply pointing to their video server (whatever that may be).

Also there are site out there that allow you to do this sort of thing already, for those unfortunate enough to have highly restrictive internet usage problems, maybe you should hunt them down also, and see if you can see the video's through them...

David

---

### Post by Chasey on 2011-01-19
I don't have restrictive internet.

---

### Post by surewhynot on 2011-03-09
I have a quick test for you to do. Try to click on the "Channel" that the youtube video was uploaded to. :) Let me know if you can watch the video from there.

~Jace Lansing

---

### Post by Zikona on 2011-03-14
Experiencing same thing here since last update. I think it was a chrome update. Hope we get a solution soon

I have already reinstalled Chrome with flashplugin64-installer without any success. Whats interesting is that the symptoms indicated in this thread would start for me once I move my mouse pointer across the youtube page. Strange it sounds but this is true. Seems that youtube's code page perhaps is creating this issue. When I do move my mouse pointer across the side for youtube preview videos while the original video is playing or across main video, Page would freeze for couple seconds (1--20 secs)withe the sound in the background and video would continue to play.

Oh, also my 4 core cpu spikes up across but I am not sure if this was happening before whenever flash was in use.

---

### Post by Zikona on 2011-03-14
Fix number 3 from [http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html) resolved my issue.

---

