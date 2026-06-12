---
title: "Japanese input Firefox 4 mobile install"
date: 2011-05-09
forum: General Help
---

### Post by brntoki on 2011-05-09
I'm calling this a "mobile" install of Firefox 4 since I installed it in its own directory and am running it without installing it through synaptic. I decided to give this a go since, for some very frustrating reason, YouTube thumbnails will not show up anymore with a synaptic installed Firefox after the latest update. I tried several fixes but to no avail (this is not such an uncommon issue. Lowering max-connections, changing the dom settings in about:config, etc. didn't work).

In fact, for your info, after FF4 worked beautifully with Youtube, I decided to add the PPA and then install it through synaptic, figuring I'd get YouTube working properly, as well as be able to input Japanese like usual. Japanese input; check. YouTube; fail. For some reason, thumbnails will just not display properly anymore with a synaptic installed FF. Crazy!

Anyway, if someone could give me some pointers on how to go about getting my UIM-Anthy input working in an app installed in the "mobile" manner, I'd appreciate it.

Ubuntu 10.04, by the way.

Thanks!

---

### Post by lovinglinux on 2011-05-09
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

---

### Post by brntoki on 2011-05-09
Thanks! I have Flash-Aid and have tried it several times. I didn't realize there was a way to generate a report, though, so I'll give it a try and let you know. I'll have to do it later, though. Flash-Aid usually does get everything running nicely, however, and has been very helpful.

---

### Post by brntoki on 2011-05-09
Okay! So, ummm... It now magically works. YouTube is tubing, and Anthy is anthying. Thanks for your reply which caused me to retry the 3.16 FF, which worked, and then went up to 4.0.1, which also works. Why I don't yet know, but if I figure it out I'll post back. I'll refrain from marking this SOLVED for now for fear that the ride may be bumpy over the next couple of days and I may need to come back to this, and because I don't have a clue how it started to automagically work.

Thanks again, though.

B.

---

### Post by brntoki on 2011-05-09
Ha-ha-ha! Sure enough, it now automagically DOESN'T work! Here's the report:

[HTML]Ubuntu Architecture

Linux Live4Jesus 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-globalmenu				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

medibuntu.list
medibuntu.list.save
mozillateam-firefox-stable-lucid.list
mozillateam-firefox-stable-lucid.list.save
ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.save

Flash packages

Plugin locations

/home/brent/.mozilla/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

/usr/lib/mozilla/plugins/xxxflashplugin-alternative.sowhat

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
libvlcplugin.so:$
/usr/lib/mozilla/plugins/libvlcplugin.so:$
:$
1302784555000:1:1:$
Version 1.0.6 Goldeneye, copyright 1996-2007 The VideoLAN Team<br><a href="http://www.videolan.org/">http://www.videolan.org/</a>:$
VLC Multimedia Plug-in:$
36
0:audio/mpeg:MPEG audio:mp2,mp3,mpga,mpega:$
1:audio/x-mpeg:MPEG audio:mp2,mp3,mpga,mpega:$
2:video/mpeg:MPEG video:mpg,mpeg,mpe:$
3:video/x-mpeg:MPEG video:mpg,mpeg,mpe:$
4:video/mpeg-system:MPEG video:mpg,mpeg,mpe,vob:$
5:video/x-mpeg-system:MPEG video:mpg,mpeg,mpe,vob:$
6:audio/x-mpegurl:MPEG audio:m3u:$
7:video/mp4:MPEG-4 video:mp4,mpg4:$
8:audio/mp4:MPEG-4 audio:mp4,mpg4:$
9:audio/x-m4a:MPEG-4 audio:m4a:$
10:application/mpeg4-iod:MPEG-4 video:mp4,mpg4:$
11:application/mpeg4-muxcodetable:MPEG-4 video:mp4,mpg4:$
12:video/x-msvideo:AVI video:avi:$
13:video/quicktime:QuickTime video:mov,qt:$
14:application/x-ogg:Ogg stream:ogg:$
15:application/ogg:Ogg stream:ogg:$
16:application/x-vlc-plugin:VLC plug-in:vlc:$
17:video/x-ms-asf-plugin:Windows Media Video:asf,asx:$
18:video/x-ms-asf:Windows Media Video:asf,asx:$
19:application/x-mplayer2:Windows Media::$
20:video/x-ms-wmv:Windows Media:wmv:$
21:video/x-ms-wvx:Windows Media Video:wvx:$
22:audio/x-ms-wma:Windows Media Audio:wma:$
23:application/x-google-vlc-plugin:Google VLC plug-in::$
24:audio/wav:WAV audio:wav:$
25:audio/x-wav:WAV audio:wav:$
26:audio/3gpp:3GPP audio:3gp,3gpp:$
27:video/3gpp:3GPP video:3gp,3gpp:$
28:audio/3gpp2:3GPP2 audio:3g2,3gpp2:$
29:video/3gpp2:3GPP2 video:3g2,3gpp2:$
30:video/divx:DivX video:divx:$
31:video/flv:FLV video:flv:$
32:video/x-flv:FLV video:flv:$
33:video/x-matroska:Matroska video:mkv:$
34:audio/x-matroska:Matroska audio:mka:$
35:application/xspf+xml:Playlist xspf:xspf:$
npwrapper.nppdf.so:$
/usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so:$
:$
1300984376000:1:1:$
The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser. :$
Adobe Reader 9.4:$
5
0:application/pdf:Portable Document Format:pdf:$
1:application/vnd.fdf:Acrobat Forms Data Format:fdf:$
2:application/vnd.adobe.xfdf:XML Version of Acrobat Forms Data Format:xfdf:$
3:application/vnd.adobe.xdp+xml:Acrobat XML Data Package:xdp:$
4:application/vnd.adobe.xfd+xml:Adobe FormFlow99 Data File:xfd:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1298508273000:1:1:$
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.7 (6b20-1.9.7-0ubuntu1~10.04.1)) executes Java applets.:$
IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.7 (6b20-1.9.7-0ubuntu1~10.04.1)):$
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
1277465636000:1:1:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1274282974000:1:1:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime Movie:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1274282974000:1:1:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1274282974000:1:1:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
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
1274282974000:1:1:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.30.2):$
19
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
18:application/x-totem-plugin:Totem Multimedia plugin::$
npPicasa3.so:$
/opt/google/picasa/3.0/lib/npPicasa3.so:$
:$
1226106226000:1:1:$
Picasa plugin:$
Picasa:$
1
0:application/x-picasa-detect:3.0:pinstall:$
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
/home/brent/.mozilla/plugins/libflashplayer.so:$
1302666910000:$
[/HTML]

But now that I look at it, I think I may know what's going on. Let me get back to you again, shortly.

---

### Post by brntoki on 2011-05-09
No dice! :(

---

### Post by brntoki on 2011-05-10
Tried a completely fresh install, renamed the .mozilla folder in order to create a new profile from scratch, as well as the .macromedia, only plugin was Flash-Aid, and no way in heck will it work. Go back to the mobile install, and it works flawlessly, but no Japanese input. I think I'd rather work from that angle; getting Japanese input to work with a mobile install rather than playing with this any more. It makes no sense whatsoever.

---

### Post by lovinglinux on 2011-05-10
> **brntoki said:**
> Tried a completely fresh install, renamed the .mozilla folder in order to create a new profile from scratch, as well as the .macromedia, only plugin was Flash-Aid, and no way in heck will it work. Go back to the mobile install, and it works flawlessly, but no Japanese input. I think I'd rather work from that angle; getting Japanese input to work with a mobile install rather than playing with this any more. It makes no sense whatsoever.

What is the architecture of the mobile browser?

The problem could be that you are installing flash from the 64bit browser using Flash-Aid and then trying to view flash with a 32bit "mobile" browser. Make sure all your browsers are 64bit, then run Flash-Aid again.

---

### Post by brntoki on 2011-05-10
> **lovinglinux said:**
> What is the architecture of the mobile browser?

The problem could be that you are installing flash from the 64bit browser using Flash-Aid and then trying to view flash with a 32bit "mobile" browser. Make sure all your browsers are 64bit, then run Flash-Aid again.

Well, I'm a little confused. When I did the fresh install of Firefox I also got a fresh copy of Flash-Aid through the Add-On function in Firefox, thinking that may be better than relying on the copy I already had. It seemed to work at first, but then it didn't. I'll try again, however.

How can I check to see if my browser is 64bit or not? I looked in troubleshooting information in the Help section, but it didn't clear things up for me.

Thanks for your help. I'll report back after I try again.

---

### Post by lovinglinux on 2011-05-10
> **brntoki said:**
> Well, I'm a little confused. When I did the fresh install of Firefox I also got a fresh copy of Flash-Aid through the Add-On function in Firefox, thinking that may be better than relying on the copy I already had. It seemed to work at first, but then it didn't. I'll try again, however.

You are doing it right. 

I just want to make sure that to install the "mobile" browser, you have downloaded a Firefox version with the same architecture, because if you don't, it won't be able to use the plugins properly.

> **brntoki said:**
> How can I check to see if my browser is 64bit or not? I looked in troubleshooting information in the Help section, but it didn't clear things up for me.

Type **about[noparse]:[/noparse]support** in the address bar and look for the **User Agent** data.

To make sure things are properly set, launch Firefox from your system (the one installed via Synaptic), type **about[noparse]:[/noparse]support** and make sure it has x86_64 in the User Agent string. Then run Flash-Aid to re-install flash. This will install Flash 64bit. Restart Firefox and make sure flash is working properly.

Now, launch the "mobile" version, type **about[noparse]:[/noparse]support** and make sure it has x86_64 in the User Agent string. If not, download the 64bit version of Firefox from the [aurora repositories]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-aurora/"), install it and launch it. Test flash.

Please report what works and what not. Please specify browser version and if the browser is installed via synpatic or "mobile".

---

### Post by brntoki on 2011-05-10
Okay. I've done a complete removal and reinstall of Firefox 4.0.1 again, whacking my old profile and only importing my bookmarks and passwords, and installed a fresh Flash-Aid. This is, of course, a synaptic install.

User Agent: Mozilla/5.0 (X11; Linux x86_64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1     

I've run Flash-Aid a couple of times and thumbnails still won't show, at least on YouTube. Flash will play, but thumbnails will only display intermittently. Max-connections and all other settings are at their defaults.

---

### Post by brntoki on 2011-05-10
Thumbnails at other popular sites are working properly. Only YouTube is buggy.

---

### Post by lovinglinux on 2011-05-10
I am not sure what exactly is going on, but I do have some clues.

I suspect the problem is that the thumbnails are the last thing loaded by the page javascript. I guess there is something being loaded before them that doesn't really complete and keeps the browser busy. That same problem happened to me when developing one of my extensions and I had to add a delay to it, to let the thumbnails load before the extension activation.

Is just I guess, but lets try some things. Forget about re-installing Flash. You are good to go already on that department.

First go to the Security tab of Firefox Preferences and disable the options "Block reported attack sites" and "Block reported web forgeries". Clear your cache and test YouTube.

If that doesn't help, install [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/"), add the Easy List subscriptions and test again.

If that doesn't help, install [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") extension and test again.

If that doesn't help, get my [FlashVideoReplacer]("http://www.webgapps.org/addons/flashvideoreplacer") extension. If it doesn't work, set a delay in the extension preferences to something like 600.

---

### Post by brntoki on 2011-05-11
Hey! I really, really appreciate your help. Please know that.

Now, this is just too weird. Right now, for some unknown reason, thumbs are displaying beautifully on YouTube. I suspect it will revert back to its funkiness, however, and when it does I'll then start trying your further suggestions.

Again, thanks a whole lot for your help. I'll report back with an update after I see how things go.

B.

---

### Post by lovinglinux on 2011-05-11
> **brntoki said:**
> Hey! I really, really appreciate your help. Please know that.

Now, this is just too weird. Right now, for some unknown reason, thumbs are displaying beautifully on YouTube. I suspect it will revert back to its funkiness, however, and when it does I'll then start trying your further suggestions.

Again, thanks a whole lot for your help. I'll report back with an update after I see how things go.

B.

You are welcome.

---

### Post by brntoki on 2011-05-15
Well! Whad'ya know? I played and played with this thing and couldn't get anything to work, and then changed the proxy settings in FF. The thumbs appeared for a while, and then quit again. From there I decided to change my DNS settings to OpenDNS (something I had used a long time ago), and it works perfectly now.

Also, however, there does seem to be something with FF4 because I ran 3.??? in WinXP on my virtual machine and it worked fine. Then I upgraded to FF4 and it was the same thing. I downloaded Chromium (for Ubuntu, not windows) and it didn't work either. Neither did Epiphany. The problem, therefore, seems to be deeper than just FF4. Somehow there is a conflict with FF4, my normal DHCP settings (auto), and YouTube.

---

### Post by brntoki on 2011-05-16
OK. Further update: It seems that the images loading from i.ytimg.com, i1.ytimg.com, i2.ytimg.com, etc., etc., were not able to be accessed. I played around and found that I'd get a 404 error if I pasted a URL for a YTube video preview image.

For example: [http://i2.ytimg.com/vi/A8_mN_7jMYc/default.jpg](http://i2.ytimg.com/vi/A8_mN_7jMYc/default.jpg)

If I paste that into my browser now, it will show the image. Before I changed my DNS to OpenDNS servers, I would get a 404 error. But the funny thing is that nothing changed, except the upgrade to FF4. Again, it worked in WinXP with FF3.16.xx, but after going to FF4 it stopped working.

---

