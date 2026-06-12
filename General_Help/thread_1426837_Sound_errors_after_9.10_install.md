---
title: "Sound errors after 9.10 install?"
date: 2010-03-10
forum: General Help
---

### Post by blazini on 2010-03-10
I just did a clean install to 9.10 from 9.04. Sound seems to work just fine, but whenever I open up a video file I get this error in the corner:

Phonon:KDE's Multimedia Library

The audio playback device SiS Sl7012 with AD1986 (SiS Sl7012) does not work. Falling back to playing/recording through the PulseAudio sound server

Whats the best way to go about getting rid of this?

---

### Post by Scunizi on 2010-03-10
I had the same issue with gforce motherboard HDMI audio.  In the box that pops up you should have an option to tell it not to remind you about that again.  Other than that I hope the sound actually works.  If not open the mixer or sound options and play with the settings.

---

### Post by blazini on 2010-03-10
Actually I just realised it's just Kaffeine that's doing it. I've always used Kaffeine with Ubuntu in the past and never had the problem.

---

### Post by sandyd on 2010-03-10
Go to Menu -> Computer -> System Settings -> Multimedia

Click on pulseaudio press the up button until its at the top.
do this for all of the audio outputs.

---

