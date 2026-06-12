---
title: "alsa, oss, pulse (how to switch?)"
date: 2010-07-08
forum: General Help
---

### Post by Cool Javelin on 2010-07-08
I have been reading a lot about using different audio output methods, among them are alsa (the one my mpd defaulted to,) pulseaudio, and oss4.

First off, what are these things? Are they a top level interface to my sound hardware? or a low level driver for it?

Can I use just any one I want?

How does it (they) know what kind of sound card I have in my machine? Do they care? Are all sound cards enough alike that there is no difference?

If I want to try to use Pulse vs. alsa, what steps must I go through to archive that? (download drivers, install codecs, replace my sound card?)

Thanks for helping a dimbulb here,
Mark.

---

### Post by lidex on 2010-07-08
alsa is the more recent sound base for linux. I believe it's supposed to replace oss. Pulseaudio is a sound-server that sits atop alsa, so those two work together. To use oss (or alsa alone) you need to remove pulse.
OSS4
[https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")
ALSA
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")
MPD on Pulseaudio
[http://mpd.wikia.com/wiki/PulseAudio]("http://mpd.wikia.com/wiki/PulseAudio#For_Distros_where_PulseAudio_output_is_broken")
Pulseaudio
[http://pulseaudio.org/]("http://pulseaudio.org/")

---

### Post by kerry_s on 2010-07-08
to select:
```
gstreamer-properties
```

---

### Post by Cool Javelin on 2010-07-10
Thanks lidex:

My alsa device wasn't working, and your links helped me to understand more about the methods and to change to oss4.

Mark.

---

