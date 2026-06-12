---
title: "Video problem with last version skype 2.2.0.35"
date: 2012-02-05
forum: General Help
---

### Post by honeybear on 2012-02-05
Hi, Please find the issue of the video of the other person to who I am talking with. After 1-2 min, the video of my friend got completely not fine/ok. Please find screenshot.

Would you know how to cure this issue? thanks

---

### Post by imachavel on 2012-02-05
I never really used Skype with Linux. 

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) Troubleshooting

recompile the source file in c?

weird guide. Every other guide for Linux is made for programmers. video problems, usually = drivers, pix elation resolution settings, or perhaps even other software issues. It is a video loading format problem for sure. I wouldn't know. I use Skype with windows. Any other issues concurrently happening?

---

### Post by honeybear on 2012-02-05
to recompile the source? really ?

there is no source. it is non-free app

---

### Post by imachavel on 2012-02-05
non free app huh? well it may not be LOCATED in source. anyway forget the re compiling. Give me a second, maybe I'll have another idea. One sec

Ok so basically, in practical thinking, skype is something you log in on a server, as your account is there, but the application runs on your computer, so the video format thing might be a decoding problem? Are you having problems loading any other video format at all? Give that a thought. I just don't know

---

### Post by TeoBigusGeekus on 2012-02-05
Is it persistent? Skype does this from time to time...

---

### Post by imachavel on 2012-02-05
well unless the driver uninstalled itself(which sounds like a windows error, not a linux one, if that's even possible)

then it'd be a decoder issue.


1. Picture is Present but Faulty
If your webcam is not one of the latest models and you get at least some picture (garbled, green-screen or static) then your drivers are installed. However, you may need additional configuration in order to use your webcam.

Reason: The developers decided to change the way the drivers and cameras work: old drivers (before Ubuntu 8.10) had the code to decode the data received from the webcam, the new drivers (since 8.10) don't. instead they assume decoding it always done somewhere else. The applications which use the older assumptions have to be provided with the additional (compatibility and decoding) library.

An example of the procedure needed to adjust launching one typical application with the described problem follows.

1.1. Skype
This information might be for the old versions of Skype and obsolete in 2010 and later

Go to main menu, System, Preferences, Menus: Applications, Internet, Items: Skype, Properties, and replace the Command with


bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

---

### Post by imachavel on 2012-02-05
> **TeoBigusGeekus said:**
> Is it persistent? Skype does this from time to time...

how would one go about trouble shooting ubuntu decoder issues?

---

### Post by TeoBigusGeekus on 2012-02-05
Since skype is closed source, not much can be done here I'm afraid...

---

### Post by imachavel on 2012-02-05
well perhaps using a different decoder might help. Maybe not, but try this:

To record both video and audio using FFmpeg, first make sure it is installed:
sudo apt-get install ffmpeg
Run ffmpeg with arguments such as these:
ffmpeg -f oss -i /dev/dsp -f video4linux2 -s 320x240 -i /dev/video0 out.mpg

if not then well what can you do. Use those commands in terminal I assume?

---

### Post by TeoBigusGeekus on 2012-02-05
ffmpeg can record video and audio, but it couldn't transmit it over the internet.

@op: Try jitsi or [this]("https://imo.im/") site.

---

### Post by honeybear on 2012-02-05
> **TeoBigusGeekus said:**
> Is it persistent? Skype does this from time to time...

This skype video issue happens after 1-2 minutes of video talk.

This box has a well-working mplayer and vlc.

It is likely due to skype and not v4l2. skype does sthg wrong


ffmpeg is already installed and work well.

I try: bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' ... lets pray

---

### Post by honeybear on 2012-02-05
```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```
is not helping. 

I installed skype on another computer (same version) and 
```
skype
``` works.

Both computers are installed with the same packages and fresh installed.

Try to understand sthg ... so weird.

So I still have the same fuzzy video


edit: the weird thing. It does only that when I call on internet with all my friends. If I try in intranet the video works both side.

So skype + internet does not like the v4l1 or v4l2 ...

```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```
is not helping.

---

### Post by honeybear on 2012-02-06
I have tried evrthg and nothing work

Maybe there is a solution that works with linux, osx, and MS win?

```

$ apt-cache search voip
ekiga-dbg - H.323 and SIP compatible VoIP client - debug symbols
ekiga - H.323 and SIP compatible VoIP client
gsutil - configure and manage Grandstream BudgeTone 100 VOIP and GX2000 phones
libh323-1.21.0 - H.323 aka VoIP library
libh323-dbg - H.323 aka VoIP library development debug files
libh323plus-dev - H.323 aka VoIP library development files
ihu - Qt VoIP softphone with an own, encrypted protocol
iprelay - User-space bandwidth shaping TCP proxy daemon
kphone - Voice over IP (VoIP) phone application
libexosip2-4 - eXtended OSIP library
libnetsds-perl - Service Delivery Suite framework
mumble-11x - Low latency VoIP client (1.1.x)
mumble-dbg - Low latency VoIP client (debugging symbols)
mumble-server-web - Web scripts for mumble-server
mumble-server - Low latency VoIP server
mumble - Low latency VoIP client
mz - versatile packet creation and network traffic generation tool
libspeex-ocaml-dev - OCaml interface to the speex library
libspeex-ocaml - OCaml interface to the speex library
libopal-dbg - OPAL library debug symbols
libopal-dev - OPAL library header files
libopal-doc - OPAL library documentation files
libopal3.6.8 - Open Phone Abstraction Library - successor of OpenH323
simpleopal - Simple example from the OPAL project
openam - H.323 answering machine
libopenh323-1.18.0-develop - H.323 aka VoIP library
libopenh323-1.18.0 - H.323 aka VoIP library
libopenh323-dbg - H.323 aka VoIP library development debug files
libopenh323-dev - H.323 aka VoIP library development files
libopenh323-doc - H.323 aka VoIP library documentation files
simph323 - Simple example from the OpenH323 project
sflphone-daemon - SIP and IAX2 compatible VoIP phone - core daemon
sflphone-data - SIP and IAX2 compatible VoIP phone - common data
sflphone-gnome - SIP and IAX2 compatible VoIP phone - GNOME client
sip-tester - a performance testing tool for the SIP protocol
libsofia-sip-ua-dev - Sofia-SIP library development files
libsofia-sip-ua-glib-dev - Sofia-SIP library glib/gobject interface development files
libsofia-sip-ua-glib3 - Sofia-SIP library glib/gobject interfaces runtime
libsofia-sip-ua0 - Sofia-SIP library runtime
sofia-sip-bin - Sofia-SIP library utilities
sofia-sip-doc - Sofia-SIP library library documentation
libspeex-dev - The Speex codec library development files
libspeex1 - The Speex codec runtime library
libspeexdsp-dev - The Speex extended library development files
libspeexdsp1 - The Speex extended runtime library
speex-doc - Documentation for speex
speex - The Speex codec command line tools
twinkle - Voice over Internet Protocol (VoIP) SIP Phone
yate-qt4 - YATE-based universal telephony client
asterisk-prompt-es - Spanish prompts for the Asterisk PBX



```

---

