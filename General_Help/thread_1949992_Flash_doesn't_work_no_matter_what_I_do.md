---
title: "Flash doesn't work no matter what I do"
date: 2012-03-31
forum: General Help
---

### Post by 0011235813 on 2012-03-31
Hey,
can anyone help me with this problem?
I have tried several different browsers (Firefox,Chrome,Rekonq,Arora) to play flash. None of them work! 
Now when I opened Firefox, it asked me to install Gnash when opening flash based sites like Kongregate or Adobe. I did this, but it still doesn't work. If it works, it works with glitches and is useless. I have tried installing the "Adobe Flash Plugin 10" thing in USC, but that doesn't solve the problem either, even with browser restart(s). I have tried uninstalling Gnash and Lightspark, but still no go. 
The only thing left was "Adobe Flash Plugin for Mozilla" which doesn't seem to want to install. It just tells me "package files failed to download, check your Internet connection" my Internet connection is working fine thank you! And I was able to install other software without any problems. 
Does anyone know how I can get Flash?
I'm using my old laptop, which I haven't touched in about a month. It works fine on my other laptop though.

---

### Post by josephmills on 2012-03-31
give this a shot 
open your terminal 
(Ctrl+alt+t)
```
sudo apt-get update && sudo apt-get --yes upgrade
```
then
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

```

then 

```
sudo apt-get install ubuntu-restricted-extras
```


Reboot and see if that works 
If not post back

---

### Post by lovinglinux on 2012-03-31
[Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by sdowney717 on 2012-03-31
Google Chrome comes with its own built-in flash version from Adobe.
Wonder why it wont work, it is the only flash that works for me.

What and how did you install chrome?
[https://www.google.com/chrome](https://www.google.com/chrome)

---

### Post by 0011235813 on 2012-04-01
@Josephmills I got an error when executing the second command ```
error: could not connect to proxy, bad port 
```   @lovinglinux When I went through the wizard, and got down to the point of executing the shell script, I was simply told that it could not &quot;create child process&quot;. Ubuntu restricted extras is already installed.   And I did install Chrome from the official site, but when I check about: plugin I can't find flash on there. Any ideas what could be wrong?  I can't seem to be able to insall the flash plugin for Mozilla thing in USC. I just get a 404 not found error. Is there any way to install it from an external repository or something of the sort?

---

### Post by 0011235813 on 2012-04-01
Update: Fixed! Apparantely, the issue has been solved using: ```
sudo apt-get install flashplugin-installer 
``` ! The issue seems to have been caused by an issue with USC and Synaptic that prevented the installation of Flash. But by using the terminal, I was able to bypass the issue.  Now, where can I have a rant about this forsaken plugin from Adobe?

---

### Post by beldofil on 2012-04-10
I have the same problem, I tried flash-aid and possibly everything else. I can download and install all plug-ins but they do nothing...

---

### Post by lovinglinux on 2012-04-10
> **beldofil said:**
> I have the same problem, I tried flash-aid and possibly everything else. I can download and install all plug-ins but they do nothing...

Please click th Flash-Aid Help menu, generate a report and post it here.


Also check [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by beldofil on 2012-04-11
The flash-aid report goes:

```
Ubuntu Architecture

Linux fil-CF-28PBJ12FE 2.6.38-13-generic #57-Ubuntu SMP Mon Mar 5 18:10:14 UTC 2012 i686 i686 i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

medibuntu.list

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install
Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
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
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
:$
1334057924000:1:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$
:$
1320797432000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.2)):$
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
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
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
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1300218695000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1300218695000:1:5:$
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
1300218695000:1:5:$
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
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1300218695000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$

[INVALID]

```

---

### Post by beldofil on 2012-04-11
[PLUGINS]
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
:$
1334057924000:1:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$
:$
1320797432000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.2)):$
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
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
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
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1300218695000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1300218695000:1:5:$
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
1300218695000:1:5:$
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
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1300218695000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$

[INVALID]

---

### Post by lovinglinux on 2012-04-11
> **beldofil said:**
> The flash-aid report goes:


Please post the results of each of these commands:

```
md5sum /usr/lib/flashplugin-installer/libflashplayer.so
md5sum /usr/lib/mozilla/plugins/libflashplayer.so
md5sum /usr/share/ubufox/plugins/libflashplayer.so
file /usr/share/ubufox/plugins/libflashplayer.so
```

---

### Post by beldofil on 2012-04-11
```
fil@fil-CF-28PBJ12FE:~$ md5sum /usr/lib/flashplugin-installer/libflashplayer.so
42d4aec7558dfd088061c07766c3ad93  /usr/lib/flashplugin-installer/libflashplayer.so
fil@fil-CF-28PBJ12FE:~$ md5sum /usr/lib/mozilla/plugins/libflashplayer.so
42d4aec7558dfd088061c07766c3ad93  /usr/lib/mozilla/plugins/libflashplayer.so
fil@fil-CF-28PBJ12FE:~$ md5sum /usr/share/ubufox/plugins/libflashplayer.so
42d4aec7558dfd088061c07766c3ad93  /usr/share/ubufox/plugins/libflashplayer.so
fil@fil-CF-28PBJ12FE:~$ file /usr/share/ubufox/plugins/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'

```

---

### Post by callmemahavir on 2012-04-11
Goto ...

[http://www.mozilla.org/en-US/plugincheck/](http://www.mozilla.org/en-US/plugincheck/)

Also Try ...

Firefox menu -> Tools -> Add-ons

---

### Post by beldofil on 2012-04-11
> **callmemahavir said:**
> Goto ...

[http://www.mozilla.org/en-US/plugincheck/](http://www.mozilla.org/en-US/plugincheck/)

Also Try ...

Firefox menu -> Tools -> Add-ons

Thanks for your help but the problem is that I have done all this and it doesn't want to work, that's why I'm here.

---

### Post by lovinglinux on 2012-04-11
> **beldofil said:**
> ```
fil@fil-CF-28PBJ12FE:~$ md5sum /usr/lib/flashplugin-installer/libflashplayer.so
42d4aec7558dfd088061c07766c3ad93  /usr/lib/flashplugin-installer/libflashplayer.so
fil@fil-CF-28PBJ12FE:~$ md5sum /usr/lib/mozilla/plugins/libflashplayer.so
42d4aec7558dfd088061c07766c3ad93  /usr/lib/mozilla/plugins/libflashplayer.so
fil@fil-CF-28PBJ12FE:~$ md5sum /usr/share/ubufox/plugins/libflashplayer.so
42d4aec7558dfd088061c07766c3ad93  /usr/share/ubufox/plugins/libflashplayer.so
fil@fil-CF-28PBJ12FE:~$ file /usr/share/ubufox/plugins/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'

```

I don't see anything wrong in your report.

Have you tried to disable hardware acceleration in flash?

Have you tried to clean up the browser cache and cookies? 

Have you tried a different browser to see if the problem is exclusive to Firefox?

Do you use an ad blocking or script blocking extension?

Also, please try to downgrade flash, just for testing, and let me know if it works or not. After downgrading and testing, delete the downloaded flash file, so we can start over from the same point. This way we can exclude the issues caused by version 11.2.202.228. See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by beldofil on 2012-04-12
> **lovinglinux said:**
> I don't see anything wrong in your report.

Have you tried to disable hardware acceleration in flash?

Have you tried to clean up the browser cache and cookies? 

Have you tried a different browser to see if the problem is exclusive to Firefox?

Do you use an ad blocking or script blocking extension?

Also, please try to downgrade flash, just for testing, and let me know if it works or not. After downgrading and testing, delete the downloaded flash file, so we can start over from the same point. This way we can exclude the issues caused by version 11.2.202.228. See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

I disabled hardware acceleration-no results
I cleaned the cache and cookies-no results
I tried chromium but flash crashes as soon as the page loads
I am using an ad block extension in chromium but weather it is or of makes no difference.

And finally I downgraded flash and it works!! however when following your tutorial from the other post I could not find ~/.mozilla/plugins/ so I put mine in ~/.mozilla/extensions/, it did nothing so I just copied the link to flash-aid and eureka, it works!

---

### Post by lovinglinux on 2012-04-12
> **beldofil said:**
> I disabled hardware acceleration-no results
I cleaned the cache and cookies-no results
I tried chromium but flash crashes as soon as the page loads
I am using an ad block extension in chromium but weather it is or of makes no difference.

And finally I downgraded flash and it works!! however when following your tutorial from the other post I could not find ~/.mozilla/plugins/ so I put mine in ~/.mozilla/extensions/, it did nothing so I just copied the link to flash-aid and eureka, it works!

Don't forget to use NoScript, because of the risks of using an old flash version.

---

### Post by philinux on 2012-04-12
> **lovinglinux said:**
> Don't forget to use NoScript, because of the risks of using an old flash version.

Is there a bug report for the latest flash not working?

[edit] Ah found one. [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/975693](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/975693)

---

### Post by claracc on 2012-04-12
> Is there a bug report for the latest flash not working?

[edit] Ah found one. [https://bugs.launchpad.net/ubuntu/+s...ee/+bug/975693](https://bugs.launchpad.net/ubuntu/+s...ee/+bug/975693)

This bug is for ubuntu 12.04.

I have encountered the problem in lubuntu 11.04 with epiphany browser and midori, new flash player plugin makes them crash. Chromium simply states it has missed the flash player plugin.

In my ubuntu 10.04 laptop with firefox 11, new flash player works well.

As I have read that adobe will not support linux anymore, I understood it was not sense to report a bug.

---

### Post by philinux on 2012-04-12
> **claracc said:**
> This bug is for ubuntu 12.04.

I have encountered the problem in lubuntu 11.04 with epiphany browser and midori, new flash player plugin makes them crash. Chromium simply states it has missed the flash player plugin.

In my ubuntu 10.04 laptop with firefox 11, new flash player works well.

As I have read that adobe will not support linux anymore, I understood it was not sense to report a bug.

Indeed. I just booted into 12.04. It's using 11,2,202,228 flash with no problem.

---

