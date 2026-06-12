---
title: "Grandfatherclock unable to paly audio file while I listen to MP3 on my PC"
date: 2010-04-08
forum: General Help
---

### Post by skao on 2010-04-08
Hi

Currently I am using grandfatherclock to remind me the time while I work ( I schedule few tasks in cron). This work very well, but as soon as I start listen to MP3 on my PC the grandfatherclock (or I sould said SOX as the audio file is "pipe" through SOX) stop working, I found out that SOX said the audio device (/dev/dsp) is busy, so it will not play the audio file.

So is there a way to force SOX to play the audio file even when the audio device (/dev/dsp) is busy?

Or is there any other command line program I can use to just play a simple audio file said every hour even the audio device is busy, so I can use cron to schedule it.

Thanks for your help

---

### Post by tgalati4 on 2010-04-08
Depending on what version of Linux you are using, there are several things to consider:

pulseaudio is a sound server framework that allows multiple applications to send sound and mix them to the speakers.  This allows you to set sound levels for system beeps, notification bubbles, and various music players.

ALSA is the sound driver framework that talks to the hardware using kernel modules (essentially drivers).  Sound goes through the pulseaudio framework to ALSA for playback.

OSS is an older sound framework with it's own modules.  Usually applications that talk directly to /dev/dsp are using either OSS or ALSA (such as SOX).  I believe pulseaudio talks to /dev/audio.  

man pulseaudio

for more information.

It's quite possible that grandfatherclock uses either ALSA or OSS instead of going though pulseaudio.

There may be some workarounds, for instance aoss is a wrapper that makes OSS applications appear to be ALSA apps.

Try:

aoss grandfatherclock

Otherwise, you will have to search to figure out how to get grandfatherclock to send audio through pulseaudio.

---

### Post by skao on 2010-04-08
Hi tgalati

aoss grandfatherclock did not work either.

So I need to find out how to use pulseaudio to play the sound.

Thanks for your help

Stephen

---

### Post by skao on 2010-04-08
Hi everyone

Got this problem solved.

we don't need to use pulseaudio, as grandfathercolck use sox to do the play back for better sound quality, just need to change one lin in t rc file for grandfathercolock /etc/grandfatherclockrc to use alsa instead of the default ossdps.

The line is PLAY_COMMAND:sox -v %g %f -t ossdsp %a or something like that
to

sox -v %g %f -t alsa

Also make sure the lock file LCK..dsp is deleted otherwise it will not work. This file is created by grandfatherclock use man grandfatherclock for more detail.

Regards,
Stephen

---

### Post by tgalati4 on 2010-04-09
I'm glad that you got it solved.

---

