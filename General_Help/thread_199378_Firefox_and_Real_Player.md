---
title: "Firefox and Real Player"
date: 2006-06-18
forum: General Help
---

### Post by v4169sgr on 2006-06-18
Currently I am not able to use the Real Player plugin in Firefox. If anyone can help by telling me where I need to start looking, that would be great!

On a clean install on new hardware, I've run Automatix to obtain Real Player 10, and have later supplemented this with a dowload of the same from [www.real.com/linux](www.real.com/linux). I've configured Real Player to use RTSP HTTP only, as earlier I was getting errors about 'bad link'.

At the moment the window where the video is supposed to be playing is simply blank [white], and there is no sound. Earlier, during my attempts to configure Real Player, I was obtaining sound, but no video; I don't seem to be able to do this any more.

Here is the contents of /usr/lib/mozilla/plugins [the contents of /usr/lib/mozilla-firefox/plugins link to this]:

```
total 1020
 16 -rw-r--r-- 1 root root  15148 2005-12-27 18:18 libflash-mozplugin.so
  4 -rw-r--r-- 1 root root    981 2006-01-01 09:16 mplayerplug-in.xpt
  4 -rw-r--r-- 1 root root    981 2006-01-01 09:16 mplayerplug-in-wmp.xpt
  4 -rw-r--r-- 1 root root    981 2006-01-01 09:16 mplayerplug-in-qt.xpt
  4 -rw-r--r-- 1 root root    981 2006-01-01 09:16 mplayerplug-in-gmp.xpt
244 -rw-r--r-- 1 root root 244860 2006-01-01 09:16 mplayerplug-in-wmp.so
244 -rw-r--r-- 1 root root 245660 2006-01-01 09:16 mplayerplug-in.so
244 -rw-r--r-- 1 root root 244540 2006-01-01 09:16 mplayerplug-in-qt.so
244 -rw-r--r-- 1 root root 244412 2006-01-01 09:16 mplayerplug-in-gmp.so
  4 drwxr-xr-x 3 root root   4096 2006-06-17 21:03 ..
  0 lrwxrwxrwx 1 root root     39 2006-06-17 21:28 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
  0 lrwxrwxrwx 1 root root     50 2006-06-18 10:37 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
  4 drwxr-xr-x 2 root root   4096 2006-06-18 21:26 mplayer_safe
  8 -rwxr-xr-x 1 root root   5086 2006-06-18 22:49 nphelix.xpt
 64 -rwxr-xr-x 1 root root  57457 2006-06-18 22:49 nphelix.so
  4 drwxr-xr-x 3 root root   4096 2006-06-18 21:41 .

```

and here are the plugins I've moved out of the way:

```
  4 -rw-r--r-- 1 root root    871 2004-11-01 14:29 kaffeineplugin.la
180 -rw-r--r-- 1 root root 177638 2004-11-01 14:29 kaffeineplugin.a
 16 -rw-r--r-- 1 root root  13872 2004-11-01 14:29 kaffeineplugin.so
  4 -rw-r--r-- 1 root root    981 2006-01-01 09:16 mplayerplug-in-rm.xpt
244 -rw-r--r-- 1 root root 244572 2006-01-01 09:16 mplayerplug-in-rm.so
  4 drwxr-xr-x 2 root root   4096 2006-06-18 21:26 .
  4 drwxr-xr-x 3 root root   4096 2006-06-18 21:41 ..

```

Here is the contents of "about : plugins" [spaces added for clarity]

```
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.581 built with gcc 3.2.0 on Feb 1 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
Google VLC multimedia plugin 1.0

    File name: mplayerplug-in-gmp.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/x-google-vlc-plugin 	Google Video 		Yes
QuickTime Plug-in 6.0

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.17

    File name: mplayerplug-in.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
Shockwave Flash

    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/futuresplash 	Future Splash 	spl 	Yes
Java(TM) Plug-in 1.5.0_06-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_06

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_06 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_06 	Java 		Yes
```

---

### Post by v4169sgr on 2006-06-18
Should mention that I have been using news.bbc.co.uk to test and have recently started experiencing sound issues too.

---

### Post by v4169sgr on 2006-06-18
Careful experimentation has revealed that:

* Realplay when fed a URL with a RAM file from the BBC site plays both pictures and sound:

* Videos from the BBC Sports site play sound but no video, but videos from the BBC news site play no sound or video.

Can anyone help please?

---

### Post by bruce89 on 2006-06-18
Not sure if this helps - [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29#head-7d2f38dce9f1934882f207ab2f4042f72033bf70](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29#head-7d2f38dce9f1934882f207ab2f4042f72033bf70)

---

### Post by v4169sgr on 2006-06-18
Thanks for the reply, but that isn't going to help, as the nphelix.so file is already present, and dpkg will refuse to over-write it [even if it is moved away].

Does anyone think this has anythign to do with RPM extensions but not RAM or RM extensions being mapped to the plugin?

---

### Post by v4169sgr on 2006-06-18
I can also open RealPlayer from within FireFox by following a link to download a RAM file and choosing 'Open Application', which works. However I am still not ablr to use the Real Player plugin.

It is probably also worth mentioning that, in order, I tried:
* Easy Ubuntu, which messed up requiring a apt-get -f install or two and a reboot to fix;
* Automatix;
* [www.realplayer.com/linux](www.realplayer.com/linux) download into a home directory, and a sudo install into /usr.

---

### Post by v4169sgr on 2006-06-18
I've had some limited success with the MediaPlayerConnectivity [0.63] FireFox extension, but would still like to open streaming video embedded within the browser.

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=v4169sgr]I've had some limited success with the MediaPlayerConnectivity [0.63] FireFox extension, but would still like to open streaming video embedded within the browser.[/QUOTE]

Not sure what stage you are at, but for me, videos work fine (sound and pictures on BBC sport) using the mplayer plugin (I chose WMV). BBC Radio works as well with Real Player plugin.

---

### Post by v4169sgr on 2006-06-19
[QUOTE=reclusivemonkey]Not sure what stage you are at, but for me, videos work fine (sound and pictures on BBC sport) using the mplayer plugin (I chose WMV). BBC Radio works as well with Real Player plugin.[/QUOTE]

Thank you sincerely for this valuable advice. I moved the nphelix files aay from the /usr/lib/mozilla/plugins directory, restored the mplayer real media plugins, restarted firefox, and I now get pictures and sound again.

One oddity is that sometimes in BBC News I get *two* video subwindows in the pop up, one full size and one about 1/5 height, and *two* sound tracks both of which play a little out of phase in relation to each other. Has anyone seen this?

Incidentally I should say that under certain conditions [unfortunately very rare] the nphelix plugin would play nice and do its job. But it looks like mplayer is much nicer. Why is this such a hassle with dapper and firefox v1.5? I did not have this problem with SuSe 9.1 and firefox 1.0.7 ...

---

### Post by reclusivemonkey on 2006-06-19
[QUOTE=v4169sgr]
One oddity is that sometimes in BBC News I get *two* video subwindows in the pop up, one full size and one about 1/5 height, and *two* sound tracks both of which play a little out of phase in relation to each other. Has anyone seen this?
[/QUOTE]

Yeah I had that problem at some point. I can't quite remember what I did to fix it unfortunately :-S. I am trialing Ubuntu having come from Slack and I am afraid to say Slack is calling me back...

---

### Post by v4169sgr on 2006-06-20
I'm afraid to say that I found a quick, simple and effective solution to this problem.

I downloaded firefox 1.5.0.4 as a tarball from the official website, unpacked under /usr/local, copied over all the relevant plugins from /usr/lib/mozilla/plugins, and RealPlayer plugin worked straight away right out of the box.

:( 

Why? Because it looks like the 6.06 firefox 1.5 package needs some work.

C'mon Ubuntu, let's get it together!:cool:

---

### Post by JoWilly on 2006-06-20
[quote=v4169sgr]I'm afraid to say that I found a quick, simple and effective solution to this problem.

I downloaded firefox 1.5.0.4 as a tarball from the official website, unpacked under /usr/local, copied over all the relevant plugins from /usr/lib/mozilla/plugins, and RealPlayer plugin worked straight away right out of the box.

:( 

Why? Because it looks like the 6.06 firefox 1.5 package needs some work.

C'mon Ubuntu, let's get it together!:cool:[/quote] 
Hmmm ? The ubuntu firefox was updated to 1.5.0.4 a few days ago through the ubuntu updater; are you sure you were still running 1.5 ?

If you are experiencing the same plroblem with the 1.5.0.4 ubuntu firefox don't forget to post a bug report (search first) on launchpad, so the developers will know about it.

---

### Post by JoWilly on 2006-06-20
[quote=reclusivemonkey]Yeah I had that problem at some point. I can't quite remember what I did to fix it unfortunately :-S. I am trialing Ubuntu having come from Slack and I am afraid to say Slack is calling me back...[/quote] 
After your post I went to take a look at slackware.

The main news page states that the latest release features kernel 2.4.31 with an option of 2.6.13 in testing, kde 3.4.2..... old versions.

So what's better in slackware ? (have never tried it and am eager to know more about it)

---

