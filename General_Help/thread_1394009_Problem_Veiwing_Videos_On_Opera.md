---
title: "Problem Veiwing Videos On Opera"
date: 2010-01-30
forum: General Help
---

### Post by iandizion713 on 2010-01-30
hello all im pretty new to Ubuntu..but love it a lot. Im having problems veiwing videos and stuff on the internet with Opera, it seems to freeze and skip a lot when i try to watch sports highlights and stuff. I have Opera 10.10 and my Ubuntu is 9.10 (karmic) kernel linux 2.6.31-17-generic, GNOME 2.28.1 i have no gstreamer software installed...not sure if any of this helps. i have tried to search forum for similar problems..sorry if i did not search hard enough..so much on there.

---

### Post by iandizion713 on 2010-01-31
finally fixed it...i was having problems with pulseaudio i guess.
i fixed by this

Got Alsa
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer

Removed PulseAudio
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio

---

