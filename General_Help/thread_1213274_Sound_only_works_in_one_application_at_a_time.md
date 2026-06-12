---
title: "Sound only works in one application at a time"
date: 2009-07-14
forum: General Help
---

### Post by itsjareds on 2009-07-14
Hi, I'm using Ubuntu Jaunty, and I can only seem to get one application to use sound at a time. Whenever I open a flash music player on one tab of Firefox, then a Java game with music in another, I don't get any sound in the Java game. If I open the Java game first, the flash music player doesn't produce sound.

I've followed several long tutorials such as this one and I still can't get it working. Can anyone help? It's the last major issue I have with Ubuntu!

Thanks,
Jared

---

### Post by itsjareds on 2009-07-14
bump

---

### Post by sedawk on 2009-07-14
I have seen applications that seem to try to get exclusive access
which doesn't work if another app already plays audio
(e.g. avidemux always comes up with that kind of message).

What happens if you play two youtube (music) videos in parallel?
Do you hear both or only the first one started?

---

### Post by itsjareds on 2009-07-14
Yes, all flash application sounds will work if I'm just playing the flash music player.

edit: Woops, i forgot to add the link to the tutorial I used.
[URL="http://ubuntuforums.org/showthread.php?t=789578"]
http://ubuntuforums.org/showthread.php?t=789578[/URL]

I changed all of my sound preferences to PulseAudio (same problem with ALSA). I viewed the PulseAudio volume controller and I see that there's an audio stream "ALSA Plugin [firefox-3.5]". It only shows for the flash app. When I run only the java applet with sound, there isn't any sound that shows up on the volume controller but I can hear it.

---

### Post by itsjareds on 2009-07-15
bump?

---

### Post by brunovianna on 2010-06-10
I'm using lucid in a hp pavillion dv6. I only solved this after following the pulse audio "perfect setup" instructions: [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

here is my /etc/asound.conf file:

```
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
}
```

---

### Post by willix on 2010-06-14
I had sound issues with Karmic running on my HP Pavilion dv7. In short I could play sound either from firefox flash plugin, or from another app (rythmbox, mplayer,...) but not both. If a sound had been played from firefox, I could not listen to music from rythmbox. I had to kill firefox in order to listen to my music again.

I solved this by following the instructions in this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) (which adds the libs and tools in the PerfectSetup) and then adding the /etc/asound.conf file as described by brunovianna.

I'm now able to swith from one to the other without having to stop anything.

Cheese

---

