---
title: "ESD blocks some audio?"
date: 2006-05-22
forum: General Help
---

### Post by SB-X on 2006-05-22
Certain games I've gotten from the repositories (Toppler, lbreakout2, Frozen Bubble) don't have any audio output, but from what I've gathered on the forum, this is because ESD is tying up the sound hardware. The games make sounds when ESD isn't running.
Why is it that I can type "killall esd" and then "(esd&)" and it allows them to produce sounds, even while it's running? (yet the one that starts with the session prevents that)

---

### Post by nanotube on 2006-05-23
to run these games with proper sound, pipe them through "esddsp". this command will make programs that do not use esd use it anyway. so, instead of starting lbreakout2 just by itself, start it wiht command
```
esddsp lbreakout2
```
then you will get sound. (of course, you can edit your menu shortcuts to add esddsp, so you dont have to start it from the terminal every time.) (and btw, lbreakout2 is a cool game! :) )
for more info, you can "man esddsp" :)

---

### Post by SB-X on 2006-05-23
I don't have that command.
> $ **apt-file search -i esddsp**
esound-clients: usr/bin/esddsp
esound-clients: usr/share/man/man1/esddsp.1.gz
libesd-alsa0: usr/lib/esound/libesddsp.so.0
libesd-alsa0: usr/lib/esound/libesddsp.so.0.2.36
libesd0: usr/lib/esound/libesddsp.so.0
libesd0: usr/lib/esound/libesddsp.so.0.2.36
So I installed esound-clients. I don't have libesd0, should I install that?

It looks like I don't need esddsp unless ESD apps are making sounds at the same time. ESD apps only hog the audio device briefly after they play a sound, then after several seconds other apps can use it.
But that still doesn't explain why they weren't working before, until I restarted ESD. Any idea why that is? (maybe some app wasn't releasing the hardware until ESD was killed?)

---

### Post by SB-X on 2006-05-24
It's working so far, though I'll need to enable hardware mixing to get simultaneous sounds. I can figure out what ESD is doing later on my own.
Thanks.

---

