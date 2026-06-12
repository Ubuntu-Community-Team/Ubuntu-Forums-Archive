---
title: "in continuous long runs of OS I have to restart Ubuntu due to no sound"
date: 2010-03-19
forum: General Help
---

### Post by Miki800 on 2010-03-19
I am running Ubuntu 9.10

from time to time if I desire sound in videos, youtubes or whatever.

I must restart Ubuntu to have sound back because in time it will just not work.

what do I mean - I run vlc, and I have no sound
so I searched a bit over the internet and figures I have to restart the 'sound server' to fix that

so I tried this line:
sudo /etc/init.d/alsasound restart

sometimes it works, sometimes it destroys my sound for good.


also - when it destroys my sound for good ( and I have no choice but to restart to solve this again )
when I click on the 'Sound Output' Gnome panel gadget I see this:

[[IMG]http://img684.imageshack.us/img684/552/whatiseei.jpg[/IMG]](http://img684.imageshack.us/i/whatiseei.jpg/)

which is not what I usually have.


for the record - I use google chrome and I have lots of youtubes and other flashes tabs opened in the background.

and whenever I have to restart the sound server they all show they crashed.


in windows this has never happened to me but I'd like to stay in Ubuntu without having to restart it so much.
In windows I almost never restart.


please assist me, thank you so much.

---

### Post by Ozymandias_117 on 2010-03-19
Next time it happens, can you run ```
sudo lshw | grep -i audio
```in a terminal and post the results please.

---

### Post by tgalati4 on 2010-03-19
Try restarting pulseaudio in a terminal:

pulseaudio -k

---

### Post by Miki800 on 2010-03-20
great, thanks.
next time it happens I'll try and do what you guys say

but why does this keep happening?
[its ok, you don't have to answer, its open source I know... I'm just ejecting frustration]

---

### Post by tgalati4 on 2010-03-20
Sometimes flash video, skype, and other closed-source programs leave the sound framework in an unknown state.  When the sound daemon get's messed up, no other application can produce sound.  So you have to kill the old sound daemon (pulseaudio -k) and it then allows other applications to use the sound hardware again.  It's a pain, but over time it will get better.

Keep a log book of what applications cause repeated problems then file a bug against those applications.

---

### Post by pbarnett on 2010-03-20
Thanks enormously - this has been bugging me since Hardy :-)

---

