---
title: "All of my audio has echo and crackle!"
date: 2011-07-26
forum: General Help
---

### Post by mrlofi on 2011-07-26
I'm not sure what's going on, but I tested with multiple speakers and found that I'm dealing with a software issue.

As the topic says, I have major distortion and an echo behind it. (Yes, I checked the sound level settings.)

Upon the advice of another thread, I tried removing

# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
 by

gksudo gedit /etc/modprobe.d/alsa-base.conf
which did nothing.

I just put this computer together (MSI A75MA-G55 motherboard w/integrated Realtek HD Audio, running Ubuntu 10.04) and need to have it ready to go tomorrow. I tried installing the drivers through WINE, but ran into a wall (alert window saying "No driver was supported in this driver package"). 

Any suggestions?

---

### Post by noah++ on 2011-07-26
Which programs have you tried playing audio from? Have you tried using various sound servers in them -- PulseAudio instead of ALSA, for instance?

---

### Post by 3602 on 2011-07-26
This might not be the case, but you wouldn't happen to have a microphone (either connected or embedded), would you?

---

### Post by mrlofi on 2011-07-26
There's no microphone and I muted the input to make sure no sound was cycling. Banshee, Rhythmbox, and the system alert sounds are all having the same problem.
The sound card is the one integrated into the motherboard I mentioned above (Realtek ALC887). I'll give PulseAudio a shot.

---

### Post by Calredon on 2011-07-28
mrlofi, i have exact the same problem, running kubuntu 11.04 with the A75MA-G55, and the A8 3850.

The crackling sound occurs in all tested programs, system sounds, wine, games, vlc ......

I tried the linux driver from realtek.com, but this didn´t work because they don´t support the ALC887.

For today im too tired to try much more, but at this moment i´m downloading
kubuntu 11.10 Ocelot daily, maybe this will work better.

I will give feedback.

Cal

---

### Post by SlugSlug on 2011-07-28
I always get rubbish sound from pulse

a 

sudo apt-get remove pulsaudio && sudo apt-get install alsa  

fixes it for me

this will display a warning about removing ubuntu desktop -- its ok :)

---

### Post by Calredon on 2011-07-28
Oh, i forgot that - i already tried to remove, purge and reinstall pulseaudio and alsa :D

It didn´t work.

Cal

---

### Post by mrlofi on 2011-07-28
I ended up going to my neighborhood PC parts store and getting a Soundblaster Live for fifteen bucks. Plugged it in, switched sound settings to use it instead of the integrated card, and the problem was fixed. I tried using drivers from multiple sites to no avail; so the issue may just be that the ALC887 and Ubuntu don't get along very well. I hope changing to ALSA fixes your issue so you don't have to shell out any cash.

---

### Post by NERDMAN! on 2011-07-28
yeah i'd say its just not getting along with ubuntu. stick with the soundblaster. even their el cheapies are better than realtek onboards anyway.

> **SlugSlug said:**
> I always get rubbish sound from pulse

slugslug i would have to say its just a config issue there, my laptop defaulted to pulse on install and ive never had an issue with it.

---

### Post by SlugSlug on 2011-07-29
> **NERDMAN! said:**
> yeah i'd say its just not getting along with ubuntu. stick with the soundblaster. even their el cheapies are better than realtek onboards anyway.


slugslug i would have to say its just a config issue there, my laptop defaulted to pulse on install and ive never had an issue with it.



I dnt think it is, I've spent days trying to get it to work. fore eg turning vol up/down = loud crackle & 5.1 dnt work (sub vol edits main vol at same time & balance also edits vol)

---

### Post by Calredon on 2011-07-29
Hi,

after removing pulseaudio the sound works correct, so it seems not to be an general problem with linux supporting this mainboard, but a pulseaudio problem.

Unfortunately after this i managed it to destroy my whole alsa configuration, so now i have to rebuild alsa.

---

### Post by Calredon on 2011-07-30
Hi there,

i was able to resolve the Problem by following this [Guide]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"). After the reboot in Step 4 the Sound was working.

---

