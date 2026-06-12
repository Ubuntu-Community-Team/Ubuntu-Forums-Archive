---
title: "streaming audio video problems"
date: 2006-05-21
forum: General Help
---

### Post by shredfitz on 2006-05-21
Cannot get sound with real player streams.  No audio streaming or otherwise with totem.  Have tried running streams in mplayer, through the firefox plugin.  No sound with VLC for any kinds of files.

My biggest gripe thus far with ubuntu 5.10 (the first and only one that I have tried)  is that I can get streaming video and audio from one out of ten streams if I am lucky.

I have a usb soundcard ? Could this be an issue ?  I can play audio files and I get sound from video files that I have on disk.  No audio when streaming though.   No audio or video when i try to watch highlights at [http://www.nba.com/pistons/index_main.html](http://www.nba.com/pistons/index_main.html)

I have an install here that has been tinkered with much .  I did use automatix to install some of the non free and win codecs.  Firefox plugins , mplayer ect.

Love LInux but I also love streaming video.  I get no audio from youtube or google video.  But at google video I can download the video and when I play it back I can hear it.

---

### Post by Sef on 2006-05-21
Did you install the codecs?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")


For Youtube, alsa-oss needs to be installed.  From the terminal

sudo apt-get update

sudo apt-get install alsa-oss

---

### Post by shredfitz on 2006-05-21
I have the alsa-oss installed, I have the codecs installed.  I still am without streaming video sucess. No youtube or sound from most streaming video.

---

