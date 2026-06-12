---
title: "Earphone compatibility"
date: 2009-10-16
forum: General Help
---

### Post by banerjeerupak on 2009-10-16
I'm using ubuntu 9.04. At times, even with the ear phones plugged in, the sound comes from the speakers. This is especially a problem at my workplace, where i can play my music only through my headphones. Please help as to how to solve this issue. 

:guitar:

---

### Post by dandnsmith on 2009-10-16
So, what sort of connection do you use for (a)speakers (b)headphones
and what sort of soundcard/chip do you have?

I plug my headphones into a socket in one speaker, which automatically switches off the speakers (by a physical, built-in switch).

---

### Post by banerjeerupak on 2009-10-16
I'm using a laptop. As soon as i plug in a earphone it used to stop playing the sound on my speakers. But that is no longer the case now. It keeps playing the sound through both my speakers as well as my earphone. I'm using a standard audio jack for my earphones. And i've no external speakers attached, just the basic ones that come with the laptop.

---

### Post by dandnsmith on 2009-10-18
So know you have to do 2 things (at least)
1) work out what, if anything, has occurred as far as software installation/configuration since it stopped working (or are you saying that it is still OK for some applications?)

2) check what sound manager you're actually using (and there aren't 2 of them) and what the settings are. I'm not on 9.04, so don't know what the defaults are.

---

### Post by budde on 2009-11-01
I've got a similar problem.

It appears that if I boot my computer with my headphones in, sound will only come from headphones. If I boot my computer without headphones, the sound will come from the laptops internal speakers, and if I now plug in my headphones I will have sound in both the speakers and the headphones.

I've found that a simple ```
sudo alsa force-reload
``` will work the same as rebooting the computer. That means that when I want to use my headphones I just plug them in and do a *sudo alsa force-reload* and it will transfer the sound into my headphones only. If I then want to use the laptop speakers again I just unplug the headphones and *sudo alsa force-reload* again.

I've noticed that most applications don't take too kindly on alsa being taken away from them, so I always close any application playing sound (VLC, Rhythmbox etc.) before the reload in order to prevent crashes.

This problem is new to me in 9.10 as in 9.04 I could just mute my speakers in the Sound - Preferences dialogue, but that option is gone now.

Not the best solution in the world, but it works. Hope this can help you!

---

