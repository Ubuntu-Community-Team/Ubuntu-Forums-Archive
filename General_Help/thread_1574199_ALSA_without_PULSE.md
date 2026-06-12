---
title: "ALSA without PULSE???"
date: 2010-09-13
forum: General Help
---

### Post by Vigh on 2010-09-13
Hi I was just wondering if there was a way to use ALSA without PULSE, PULSE AUDIO is causing my Skype to crash continually. I entered the following command into terminal-

sudo apt-get remove --purge pulse-audio

now my system has no sound at all, soundcards are detected in aplay -l, but unfortunately when i go to sound properties it just says waiting for sound system to respond

---

### Post by kerry_s on 2010-09-13
you only needed to remove "gstreamer0.10-pulseaudio" it's borked & crashes everything.

so put pulseaudio back & remove gstreamer0.10-pulseaudio

---

### Post by manwhore on 2010-09-19
You were right kerry! this worked for me. I removed the gstreamer0.10-pulseaudio put pulseaudio back and now I'm back in business

---

