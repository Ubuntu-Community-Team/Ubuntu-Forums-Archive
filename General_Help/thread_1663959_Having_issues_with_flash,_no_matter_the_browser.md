---
title: "Having issues with flash, no matter the browser"
date: 2011-01-10
forum: General Help
---

### Post by inameiname on 2011-01-10
For some reason, several websites that use flash cannot play videos. What is weirder, is testing this on more than just Firefox, just as with Opera, I get the same issue. It doesn't pop up a message at all, but remains a blank screen, and no video control buttons.

Another test I did was running Firefox through both '/home/(my username)/.mozilla' & '/root/.mozilla'. I deleted the two folders (I have a backup so no worries), and then did the following:

```

firefox

(it just runs through the terminal, creating a '.mozilla' folder in my home folder, and again, fails to play videos. Thus, I know it's not a firefox/opera addon)

sudo firefox

(it creates /home/(my username)/.mozilla folder, with lock on it for permissions since it was created with 'sudo', but still doesn't work to play videos)

```However, when I do the following, it does work. I don't understand why it does here, but not above:

```

gksu firefox

(it creates '/root/.mozilla', and DOES play all the flash videos. No blank screen where the video should be. It works)

```Does anyone know why a fresh folder in '/root/' works, but not in '/home/(my username)/'? Why would is suddenly stop working, and how can I fix it?

Also, I tried reinstalling flashplugin-installer, but that did nothing to change the issue.

Thanks in advance.

---

### Post by marl30 on 2011-01-10
Try this plugin to see if it helps:[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) (Flash-aid)

---

### Post by ghostborg on 2011-01-10
If you haven't tried Chrome(Google) yet it should have it built in already.
Chromium as far as I know does not since Flash is not open source.

---

### Post by lovinglinux on 2011-01-10
> **marl30 said:**
> Try this plugin to see if it helps:[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) (Flash-aid)

Most likely it will fix your problem. If not, then go to Flash-Aid Help tab, generate a report and post it here. Please let me know if you experience any difficulties with the extension, so I can improve it.

BTW, you should never run Firefox with sudo. Is a security risk and it messes with your user profile. To fix that, delete your ~/.mozilla folder or do this:

```
sudo chown -R $USER:$USER ~/.mozilla
```

(DON'T replace USER)

> **ghostborg said:**
> If you haven't tried Chrome(Google) yet it should have it built in already. Chromium as far as I know does not since Flash is not open source.

Sorry, but that is not a solution. Other applications besides the browser make use of flash, so replacing the browser is just a band-aid. Besides, only Chrome 32bit has the bundled plugin.

---

### Post by inameiname on 2011-01-10
Thanks for the suggestions. I'll try them and let you know.

Yeah, I just tried 'sudo firefox' for the heck of it. I just tried all sorts of the combinations to figure out why 'gksu firefox' worked, but not 'firefox' or 'sudo firefox' even. 

Oh, and the flash and the exact same flash videos don't work in Opera either, not just Firefox. So I'm sure Chrome/Chromium would be the same, unless it does indeed have a built-in version of something. 

Out of curiosity, why would a firefox addon be required when I didn't need it before? I didn't change a thing and even deleted and restored my '.mozilla' folder that I know worked with it before?

Also, with this plugin, do I just use once, and once it installs the appropriate packages and removes the unneeded ones, just uninstall it?

---

### Post by Aquix on 2011-01-10
It's only a plugin to fix flash install and configurations. When you got flash going, you can delete it. 

Another great addon from lovinglinux.:KS

---

### Post by inameiname on 2011-01-10
Thanks.

Sadly, I've installed it, and upon restart of firefox, it pops up this script in it's window:

```

#!/bin/bash

sudo apt-get --yes purge flashplugin-installer
sudo apt-get update
cd "/home/me/.mozilla/firefox/573gtz7t.default/extensions/flashaid@lovinglinux.megabyet.net/chrome/content/tmp" && rm -f *.tar.gz* && wget http://www.webgapps.org/downloads/flash/beta/flashplayer32 && tar xvf flashplayer32 && sudo chown root:root libflashplayer.so && sudo mv libflashplayer.so /usr/lib/mozilla/plugins/ && sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so && rm -f flashplayer32
sudo mkdir /etc/adobe
echo 'OverrideGPUValidation=true' | sudo tee /etc/adobe/mms.cfg

```

I do that, and restart, and it doesn't fix anything. Seems like it just removed the normal installation of flashplugin-installer, and installed the libflashplayer.so elsewhere.

I tried it again, and this time it was this script in the window:

```

#!/bin/bash

sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo apt-get update
cd "/home/me/.mozilla/firefox/573gtz7t.default/extensions/flashaid@lovinglinux.megabyet.net/chrome/content/tmp" && rm -f *.tar.gz* && wget http://www.webgapps.org/downloads/flash/beta/flashplayer32 && tar xvf flashplayer32 && sudo chown root:root libflashplayer.so && sudo mv libflashplayer.so /usr/lib/mozilla/plugins/ && sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so && rm -f flashplayer32
TWEAK=$(cat /etc/adobe/mms.cfg | grep 'OverrideGPUValidation=true')
if test -z "${TWEAK}";then
echo 'OverrideGPUValidation=true' | sudo tee -a /etc/adobe/mms.cfg
fi

```

Then restarted, and still doesn't work. :( Doh.

---

### Post by lovinglinux on 2011-01-10
> **inameiname said:**
> Oh, and the flash and the exact same flash videos don't work in Opera either, not just Firefox. So I'm sure Chrome/Chromium would be the same, unless it does indeed have a built-in version of something. 

The 32bit version has a bundled plugin, that is optimized by Google. However, mileage varies. I have seen complaints about Chrome plugin and installing the repository flash or using Flash-Aid solves the problem sometimes for Chrome too.

> **inameiname said:**
> Out of curiosity, why would a firefox addon be required when I didn't need it before? I didn't change a thing and even deleted and restored my '.mozilla' folder that I know worked with it before?

The add-on is not required. You can do what it does via command-line and via package manager. However, it is very convenient, because it addresses many common issues I have helped to fix over the years in the forum and allows to do that without typing any commands. The extension is basically a script launcher, that uses your system information to generate the best script to solve your flash problems and optimize it.

With the extension we don't need to try to figure out the source of your problem, which most likely will be one covered by the extension script.

I cannot determine why you need to fix flash now. Too many variables to consider and not enough information about your system. If you really want such info, then generate a report from the extension help tab before running the installation script. With that report I can probably tell the source of your problem.

> **inameiname said:**
> Also, with this plugin, do I just use once, and once it installs the appropriate packages and removes the unneeded ones, just uninstall it?

Well, uninstalling it won't hurt. However, by default the extension will install the latest beta flash from Adobe, depending on your Ubuntu version and architecture. This flash version is not updated by the package manager, but the extension includes an update check. So I would advice to keep it installed. It will check for flash updates once a day, unless you disable this feature in the preferences.

---

### Post by lovinglinux on 2011-01-10
> **inameiname said:**
> Then restarted, and still doesn't work. :( Doh.

Please, go to the extension Help tab, generate a report and post it here.

---

### Post by inameiname on 2011-01-10
Thanks for the info. I understand the addon clearly now. It looked like it was just a script-maker.

Per your request, here is the help report that was generated. It is indeed strange why it doesn't work anymore, and yet worked with 'gksu firefox'. That is what really baffles me:

```

Ubuntu Architecture

Linux Computer 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install
firefox-mozilla-build                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-3.6.13/firefox.sh'

Sources


Flash packages

Plugin locations


/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
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
libnpgtpo3dautoplugin.so:$
/opt/google/talkplugin/libnpgtpo3dautoplugin.so:$
:$
1292280850000:1:5:$
Google Talk Plugin Video Accelerator version:0.1.43.4:$
Google Talk Plugin Video Accelerator:$
1
0:application/vnd.gtpo3d.auto:O3D MIME::$
libnpgoogletalk.so:$
/opt/google/talkplugin/libnpgoogletalk.so:$
:$
1292280849000:1:5:$
Version: 1.7.1.0:$
Google Talk Plugin:$
1
0:application/googletalk:Google Talk Plugin:googletalk:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$
:$
1292049901000:1:5:$
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.2 (6b20-1.9.2-0ubuntu2)) executes Java applets.:$
IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.2 (6b20-1.9.2-0ubuntu2)):$
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
16:application/x-java-applet;jpi-version=1.6.0_20:IcedTea:class,jar:$
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
32:application/x-java-bean;jpi-version=1.6.0_20:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1290721763000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1289803589000:1:1:$
Shockwave Flash 10.2 d151:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
gecko-mediaplayer.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer.so:$
:$
1268180685000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 0.9.9.2<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
mplayerplug-in is now gecko-mediaplayer 0.9.9.2:$
43
0:audio/x-mpegurl:MPEG Playlist:m3u:$
1:video/mpeg:MPEG:mpg,mpeg:$
2:audio/mpeg:MPEG:mpg,mpeg:$
3:video/x-mpeg:MPEG:mpg,mpeg:$
4:video/x-mpeg2:MPEG2:mpv2,mp2ve:$
5:audio/mpeg:MPEG:mpg,mpeg:$
6:audio/x-mpeg:MPEG:mpg,mpeg:$
7:audio/mpeg2:MPEG audio:mp2:$
8:audio/x-mpeg2:MPEG audio:mp2:$
9:audio/mp4:MPEG 4 audio:mp4:$
10:audio/x-mp4:MPEG 4 audio:mp4:$
11:video/mp4:MPEG 4 Video:mp4:$
12:video/x-m4v:MPEG 4 Video:m4v:$
13:video/3gpp:MPEG 4 Video:mp4,3gp:$
14:audio/mpeg3:MPEG audio:mp3:$
15:audio/x-mpeg3:MPEG audio:mp3:$
16:audio/x-mpegurl:MPEG url:m3u:$
17:audio/mp3:MPEG audio:mp3:$
18:application/x-ogg:Ogg Vorbis Media:ogg,oga,ogm:$
19:application/ogg:Ogg Vorbis Media:ogg,oga,ogm:$
20:audio/x-ogg:Ogg Vorbis Audio:ogg,oga:$
21:audio/ogg:Ogg Vorbis Audio:ogg,oga:$
22:video/x-ogg:Ogg Vorbis Video:ogg,ogm:$
23:video/ogg:Ogg Vorbis Video:ogg,ogm:$
24:application/x-vlc-plugin:VLC plug-in:vlc:$
25:application/x-google-vlc-plugin:Google VLC plug-in::$
26:audio/flac:FLAC Audio:flac:$
27:audio/x-flac:FLAC Audio:flac:$
28:video/fli:FLI animation:fli,flc:$
29:video/x-fli:FLI animation:fli,flc:$
30:video/x-flv:Flash Video:flv:$
31:video/flv:Flash Video:flv:$
32:video/vnd.vivo:VivoActive:viv,vivo:$
33:audio/x-matroska:Matroska Audio:mka:$
34:video/x-matroska:Matroska Video:mkv:$
35:application/x-nsv-vp3-mp3:Nullsoft Streaming Video:nsv:$
36:audio/x-mod:Soundtracker:mod:$
37:audio/x-aiff:AIFF Audio:aif:$
38:audio/basic:Basic Audio File:au,snd:$
39:audio/x-basic:Basic Audio File:au,snd:$
40:audio/midi:MIDI Audio:mid,midi,kar:$
41:audio/x-scpls:Shoutcast Playlist:pls:$
42:video/x-mng:Multiple-Image Network Graphics:mng:$
gecko-mediaplayer-wmp.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so:$
:$
1268180685000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 0.9.9.2<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
Windows Media Player Plug-in:$
19
0:application/asx:Media Files:*:$
1:video/x-ms-asf-plugin:Media Files:*:$
2:video/x-msvideo:AVI:avi,*:$
3:video/msvideo:AVI:avi,*:$
4:application/x-mplayer2:Media Files:*:$
5:application/x-ms-wmv:Microsoft WMV video:wmv,*:$
6:video/x-ms-asf:Media Files:asf,asx,*:$
7:video/x-ms-asx:Media Files:asx,*:$
8:video/x-ms-wm:Media Files:wm,*:$
9:video/x-ms-wmv:Microsoft WMV video:wmv,*:$
10:audio/x-ms-wmv:Windows Media:wmv,*:$
11:video/x-ms-wmp:Windows Media:wmp,*:$
12:application/x-ms-wmp:Windows Media:wmp,*:$
13:video/x-ms-wvx:Windows Media:wvx,*:$
14:audio/x-ms-wax:Windows Media:wax,*:$
15:audio/x-ms-wma:Windows Media:wma,*:$
16:application/x-drm-v2:Windows Media:asx,*:$
17:audio/wav:Microsoft wave file:wav,*:$
18:audio/x-wav:Microsoft wave file:wav,*:$
gecko-mediaplayer-rm.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so:$
:$
1268180685000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 0.9.9.2<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
RealPlayer 9:$
7
0:audio/x-pn-realaudio:RealAudio:ram,rm:$
1:application/vnd.rn-realmedia:RealMedia:rm:$
2:application/vnd.rn-realaudio:RealAudio:ra,ram:$
3:video/vnd.rn-realvideo:RealVideo:rv:$
4:audio/x-realaudio:RealAudio:ra:$
5:audio/x-pn-realaudio-plugin:RealAudio:rpm:$
6:application/smil:SMIL:smil:$
gecko-mediaplayer-qt.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer-qt.so:$
:$
1268180685000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 0.9.9.2<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
QuickTime Plug-in 7.6.4:$
6
0:video/quicktime:Quicktime:mov:$
1:video/x-quicktime:Quicktime:mov:$
2:image/x-quicktime:Quicktime:mov:$
3:video/quicktime:Quicktime:mp4:$
4:video/quicktime:Quicktime - Session Description Protocol:sdp:$
5:application/x-quicktimeplayer:Quicktime:mov:$
gecko-mediaplayer-dvx.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer-dvx.so:$
:$
1268180685000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 0.9.9.2<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
DivX Browser Plug-In:$
2
0:video/divx:DivX Media Format:divx:$
1:video/vnd.divx:DivX Media Format:divx:$
libnullplugin.so:$
/opt/firefox/plugins/libnullplugin.so:$
1.0.0.15:$
1291385234000:1:5:$
The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.:$
Default Plugin:$
1
0:*:All types:.*:$

```


FYI, I just tried 'gksu firefox' to see if it was still working with those flash videos, even with the  change that the scripts asked and did, and YES, IT STILL WORKS.

---

### Post by lovinglinux on 2011-01-10
> **Aquix said:**
> It's only a plugin to fix flash install and configurations. When you got flash going, you can delete it. 

Another great addon from lovinglinux.:KS

Thanks ;)

---

### Post by lovinglinux on 2011-01-10
> **inameiname said:**
> Per your request, here is the help report that was generated. It is indeed strange why it doesn't work anymore, and yet worked with 'gksu firefox'. That is what really baffles me:

FYI, I just tried 'gksu firefox' to see if it was still working with those flash videos, even with the  change that the scripts asked and did, and YES, IT STILL WORKS.

Your report shows me that you are all set. Firefox is detecting the version installed by Flash-Aid and you don't have any additional plugin that might have caused conflicts.

The fact that you can run the plugin via gksudo, indicates that the problem most likely resides in your profile, because when you use gksudo, Firefox uses the root profile.

However, the fact that Opera doesn't work as well, indicates the problem lies somewhere else. So I would start by deleting the ~/.macromedia folder. Make a backup first, since it is responsible for storing flash cookies, for example from flash games scores.

When you restart Firefox after deleting that folder, go to the add-on manager and check if Flash is listed in the plugins.

Also make sure you don't have any blocking script like NoScript or Flahblock enabled.

Check if Opera works. Type **opera[noparse]:[/noparse]plugins** in the address bar and make sure the flash version listed there is:

```
Description: Shockwave Flash 10.2 d161
```

---

### Post by lovinglinux on 2011-01-10
It seems that you have Firefox 4 or something else installed manually or via Ubuntuzilla. It also seems that you don't have a plugin folder there.

Try this:

```
sudo mkdir /opt/firefox/plugins
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
```

---

### Post by inameiname on 2011-01-10
Okay, firstly, I have in Opera:Plugins:

```

Description: Shockwave Flash 10.2 d151
not
Description: Shockwave Flash 10.2 d161

```I also do not have a  ~/.macromedia folder.

The only plugin with 'flash' in it that I have according to Firefox is Shockwave Flash. I hope that's the appropriate one that should show up.

Finally, I do use Ubuntuzilla. Usually it downloads the latest version, and then a little later Ubuntu's main repos have it updated as well. It doesn't seem to hurt keeping it, so I just leave it.

Oh, and my Firefox version is 3.6.13.

Anyway, I'll try your most recent reply and get back with you.


UPDATE:

Alas, 

sudo mkdir /opt/firefox/plugins
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins

...didn't fix anything. It actually said /opt/firefox/plugins already existed.

---

### Post by inameiname on 2011-01-10
If I cannot figure this out, I may just restore my computer from a Remastersys backup image I made a week ago. That way I'll see if the issue persists, or is fixed. Worse case scenario I guess. Of course, if it is still an issue, that is weird as it wasn't when I made it.

---

### Post by TechWiz2100 on 2011-01-10
I think the error you are having is related to Compiz
[http://ubuntuforums.org/showthread.php?t=1658439]("http://ubuntuforums.org/showthread.php?t=1658439")

Check out that link and see if any of it fixes your problem.

---

### Post by lovinglinux on 2011-01-10
> **inameiname said:**
> ```

Description: Shockwave Flash 10.2 d151
not
Description: Shockwave Flash 10.2 d161

```


Your version is correct. I did a typo. Is d151 not d161.

> **inameiname said:**
> 
UPDATE:

Alas, 

sudo mkdir /opt/firefox/plugins
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins

...didn't fix anything. It actually said /opt/firefox/plugins already existed.

Ok then. No problem there.

Can you post a link to a web site that flash doesn't work for you? Does it work on YouTube?

---

### Post by lovinglinux on 2011-01-10
> **TechWiz2100 said:**
> I think the error you are having is related to Compiz
[http://ubuntuforums.org/showthread.php?t=1658439]("http://ubuntuforums.org/showthread.php?t=1658439")

Check out that link and see if any of it fixes your problem.

Indeed could be Compiz, since it doesn't play well with flash.

---

### Post by inameiname on 2011-01-10
Compiz...hmmmm...interesting. I never thought of that. Not sure why it'd screw up only some flash.

Anyway, I looked at that link you gave, and tried:

```

env XLIB_SKIP_ARGB_VISUALS=1 firefox

...and it does load a whole new Firefox, but is doesn't fix things.

```


YouTube does seem to work with any and all links I gave. Anyway, as mentioned, it's only on some sites.

No worries. Thanks for your help. I was planning on redoing anyway. I'll see if that changes things. If not, oh well. 

Thanks!

---

### Post by lovinglinux on 2011-01-10
> **inameiname said:**
> Compiz...hmmmm...interesting. I never thought of that. Not sure why it'd screw up only some flash.

Anyway, I looked at that link you gave, and tried:

```

env XLIB_SKIP_ARGB_VISUALS=1 firefox

...and it does load a whole new Firefox, but is doesn't fix things.

```


YouTube does seem to work with any and all links I gave. Anyway, as mentioned, it's only on some sites.

No worries. Thanks for your help. I was planning on redoing anyway. I'll see if that changes things. If not, oh well. 

Thanks!

Please let me know if you need further assistance.

---

### Post by inameiname on 2011-01-10
Sure. I'm always needing help in some shape or form. :P

---

### Post by inameiname on 2011-01-10
So I redid my computer from a Remastersys backup, and what do you know, it works. All the video I've tried to stream seems to work. I don't get it, but whatever. 

It's a shame I couldn't figure out for sure just what the culprit was so as to prevent it if it ever happens again, but oh well.

Thanks again to those who tried to help.

---

