---
title: "Something eat resourses"
date: 2010-08-10
forum: General Help
---

### Post by peaceprayer on 2010-08-10
Subject is all - something eat resources in my Ubuntu.

gnome-system-monitor usually shows me, that for about 400-900mb of memory is used (with only Firefox, Deluge, Deadbeef and usual stuff running) and moreover - both cores of processor is working pretty hard too : ~ 25-60 % for both. 

seems strange to me.

tell me please - how can i check what is so hungry in my Ubuntu?

p.s.: got built in video-card and auido card. does it makes sence?
p.p.s.: couple of days ago decided to turn off pulseaudio stuff (got a problem - only one user on one PC could use sound) and changed it to ALSA.

---

### Post by Spice Weasel on 2010-08-10
GNOME in general is a bit of a hog, but try just going on to the processes tab and use the little title things to organise the processes by amount of CPU/RAM used. That should give you a vague idea of what's using the most juice on your system.

---

### Post by howefield on 2010-08-10
And if you want something a little less vague, try running top or htop from a terminal.

---

### Post by quinnten83 on 2010-08-10
> **peaceprayer said:**
> Subject is all - something eat resources in my Ubuntu.

gnome-system-monitor usually shows me, that for about 400-900mb of memory is used (with only Firefox, Deluge, Deadbeef and usual stuff running) and moreover - both cores of processor is working pretty hard too : ~ 25-60 % for both. 

seems strange to me.

tell me please - how can i check what is so hungry in my Ubuntu?

p.s.: got built in video-card and auido card. does it makes sence?
p.p.s.: couple of days ago decided to turn off pulseaudio stuff (got a problem - only one user on one PC could use sound) and changed it to ALSA.

try with the top command?
```
top
```

---

### Post by peaceprayer on 2010-08-10
i tried htop and top commands, and the strange thing it usually looked like:
the sum of all process % equals ~ 10, but overall % sometimes jumps to 50% or something and holds like this for a several seconds.

also the problem is not only when Ubuntu working it seems to work slower now, but even the time it need to start increased. 

how can i get info what processes take what resources from the very start till the moment i'll see the desktop?

thank you for answers, guys!

---

