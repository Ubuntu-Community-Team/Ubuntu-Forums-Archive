---
title: "no sound"
date: 2010-03-13
forum: General Help
---

### Post by adling11 on 2010-03-13
hi every body
at first i had install kubuntu and the sound was very good but after  i install the gnome desktop  i have no sound in gnome and only i can listen to mp3 music in kde coz i installed mp3 fluendo codec 
what i have to do 
and thank you

---

### Post by sixthwheel on 2010-03-13
Go to System/Preferences/ Sound, and take a look around.

---

### Post by adling11 on 2010-03-13
what i've to look for exactly

---

### Post by subedistra7 on 2010-03-13
> **adling11 said:**
> what i've to look for exactly

check if pcm is at 0%. if it is, drag it to max.

---

### Post by rawlins02 on 2010-03-13
I just fixed a sound problem I'd been having after installing 9.10 Karmic Koala. I'd been unable to get sound for several web sites/applications. I tested sound as follows.

> aplay /usr/share/sounds/alsa/Front_Center.wav

Heard the voice say 'Front Center'. Check. Then started RythmBox Music Player under Applications -> Sound and Video.  Started a radio station and heard music. Check. So concluded that some things were working, but not all apps. Then went to Synaptic and removed pulseaudio sound server.  Presto! Several web applications I've tested now produce sound.

Can't say if that's your problem. But worth a try. You can always reinstall pulseaudio.

---

