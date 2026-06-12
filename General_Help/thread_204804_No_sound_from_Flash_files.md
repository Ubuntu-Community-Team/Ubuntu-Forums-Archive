---
title: "No sound from Flash files"
date: 2006-06-27
forum: General Help
---

### Post by BlacKsheep88 on 2006-06-27
I have the Flash plugin for Firefox installed, and the videos will play, but they have no sound. Is there a command to change the settings to where I can enable sound?

---

### Post by Dr. Nick on 2006-06-27
try this

[http://ubuntuforums.org/showthread.php?t=204022](http://ubuntuforums.org/showthread.php?t=204022)

---

### Post by tubo on 2006-06-27
i solved the sound issue in firefox differently. i start my firefox with an alsa wrapper, which also works for me:

aoss firefox &

thats all, i have sound in Flash videos.

best
Emanuel

---

### Post by BlacKsheep88 on 2006-06-27
[QUOTE=tubo]i solved the sound issue in firefox differently. i start my firefox with an alsa wrapper, which also works for me:

aoss firefox &

thats all, i have sound in Flash videos.

best
Emanuel[/QUOTE]
What is an alsa wrapper and how do I apply it?

---

### Post by keithjr on 2006-06-27
None of the posted solutions have helped me so far, and I don't forsee any will, but let us know if any solutions come to you

<edit> Nevermind!  the link posted above did work (just run each of the non-commented commands in the first post one line at a time), just don't forget to change the firefox rc file:

```

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

sudo nano /etc/firefox/firefoxrc

```

and in firefoxrc:

FIREFOX_DSP="esd"

This worked for me.  FINALLY!

I think the key is that the first symlink created allows firefox to finally access my second sound device, my sound blaster card, instead of my crappy onboard sound.

---

### Post by tubo on 2006-06-28
[QUOTE=BlacKsheep88]What is an alsa wrapper and how do I apply it?[/QUOTE]

emanuel@foobar:~#sudo apt-cache show alsa-oss
...snip....
Description: ALSA wrapper for OSS applications
 This package contains a program loader, aoss, which wraps
 applications written for OSS in a compatibility library,
 thus allowing them to work with ALSA.
 .
 There are two ways of getting an application to work with
 ALSA if the application was written for OSS. The first way
 is to load the special ALSA drivers that emulate the OSS
 kernel interface; these allow the application to open
 /dev/dsp0 and other OSS device files. The second way is
 to wrap the application in the libaoss library provided
 in this package; the wrapper causes the application to
 access native ALSA device files such as /dev/snd/pcmC0D0c
 instead of OSS device files.
 .
 Use of the alsa-oss library is recommended over the use of
 OSS-emulation drivers if you want to use ALSA's PCM plugin
 layer.
 .
....snip....

to install simply

emanuel@foobar:~#sudo apt-get install alsa-oss

then start Firefox with:

emanuel@foobar:~#aoss firefox &

works for me and seems easy. I modified the Desktop shortcut as well and never had sound issues again.

Emanuel

---

### Post by Ramses de Norre on 2006-06-28
Or edit /etc/firefox/firefoxrc and set FIREFOX_DSP= to aoss, looks nicer to me but does the same ;)

---

