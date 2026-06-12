---
title: "Flash player problem"
date: 2011-04-08
forum: General Help
---

### Post by Eudis21 on 2011-04-08
When I play videos or flash games. The videos speeds up and skips annoyingly, in flash games the sound is messed up. 

I've tried uninstalling my flash/updating flash/installing a older version. Any help will be appreciated.

Also whats the command to display my hardware information for anyone willing to help, I'm a total noob, but willing to learn.

Currently running Ubuntu 10.10 Maverick. Browsers used Chromium/ Google Chrome ( For its flash plugin ), and firefox.

---

### Post by flipper T on 2011-04-08
try flashaid extension in firefox

there is something similar in chrome too

---

### Post by Eudis21 on 2011-04-08
Forgot to mention I tried that.

---

### Post by flipper T on 2011-04-08
oh

---

### Post by Sef on 2011-04-09
> I've tried uninstalling my flash/updating flash/installing a older version. 

How have you installed and uninstalled it?

> Also whats the command to display my hardware information for anyone willing to help,

sudo lshw

---

### Post by Eudis21 on 2011-04-09
Yes, I've tried that.
I have a new update on this problem. ANY video I watch is time-skipped/accelerated I tried watching an .avi and the same thing happened.
I believe is my graphics card, maybe a driver problem. Heres the graphics card specs.
Btw this is a quiet old machine. 

*-display:0
                description: VGA compatible controller
                product: Radeon RV250 If [Radeon 9000]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz

[ description: Mini Tower Computer
    product: Dimension 4550
    vendor: Dell Computer Corporation
    serial: 5YPZN21]

---

### Post by Eudis21 on 2011-04-09
bump

---

### Post by lovinglinux on 2011-04-09
> **Eudis21 said:**
> bump

Please go to Flash-Aid help tab, generate a report and paste the contents of the *firefox-report.txt* file created on your desktop.

Is probably a pulseaudio issue. See [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by Eudis21 on 2011-04-09
Ubuntu Architecture

Linux Tai 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

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
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.16/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list

Flash packages

flashplugin-installer				deinstall
Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


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
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$
:$
1298473629000:1:5:$
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.7 (6b20-1.9.7-0ubuntu1)) executes Java applets.:$
IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.7 (6b20-1.9.7-0ubuntu1)):$
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
1295949257000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1285633033000:1:5:$
The <a href="[http://www.gnome.org/projects/totem/](http://www.gnome.org/projects/totem/)">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
The <a href="[http://www.gnome.org/projects/totem/](http://www.gnome.org/projects/totem/)">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
The <a href="[http://www.gnome.org/projects/totem/](http://www.gnome.org/projects/totem/)">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
1298684914000:1:5:$
Shockwave Flash 11.0 d0:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

---

### Post by lovinglinux on 2011-04-09
> **Eudis21 said:**
> Ubuntu Architecture

Linux Tai 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux...

Your report is okay.However, it seems you have installed the experimental Flash 11.0 after using Flash-Aid. I haven't tested that version yet. Flash-Aid install 10.3 d180.

See [http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions)

Perform the steps in the issue "No sound in flash but sound works elsewhere".

---

### Post by Eudis21 on 2011-04-09
Hmm, I attempted that now and got stuck at change default sound card, it won't open up.

---

### Post by lovinglinux on 2011-04-09
> **Eudis21 said:**
> Hmm, I attempted that now and got stuck at change default sound card, it won't open up.

Delete the files you have changed and reboot.

---

### Post by Eudis21 on 2011-04-09
> **lovinglinux said:**
> Delete the files you have changed and reboot.
Still can't access default sound card in System > Preferences > Default sound card.

---

### Post by lovinglinux on 2011-04-09
> **Eudis21 said:**
> Still can't access default sound card in System > Preferences > Default sound card.

Install pavucontrol and check if you can configure your cards with it. I am not on gnome right now, but pavucontrol always worked for me.

```
sudo apt-get install pavucontrol
```

Also check [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

