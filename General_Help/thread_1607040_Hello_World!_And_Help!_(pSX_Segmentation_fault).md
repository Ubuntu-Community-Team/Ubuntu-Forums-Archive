---
title: "Hello World! And Help! (pSX Segmentation fault)"
date: 2010-10-27
forum: General Help
---

### Post by Hatsune Miku on 2010-10-27
Hello Everyone i am a newbie to this world you call Linux! I am migrating from Mac OS X, Reasons for? Meh i wanted something harder and i like free things :D :P. But free things come with a price it seems. pSX is having problems with sound, the error i am having occuring is as follows below

```
(pSX:2685): Gtk-WARNING **: Loading IM context type 'ibus' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

I forgot to tell you! I am running on a x86_64 system with kernel 2.6.35-22 generic with NVIDIA Card/Drivers! Also running GNOME 2.32.0

Any ideas guise? :popcorn:

Miku~Samaba.

---

### Post by searchfgold6789 on 2010-10-27
Well "Segmentation Fault" for me is usually fixed by reinstalling something.
I just don't know what it could be in your case. Sound card drivers?
It would help us to know what exactly you are trying to do. Boot from the live CD in the PSX emulator? Run a command?

 - search
(sorry I don't know much about PSX)

---

### Post by Hatsune Miku on 2010-10-27
> **searchfgold6789 said:**
> Well "Segmentation Fault" for me is usually fixed by reinstalling something.
I just don't know what it could be in your case. Sound card drivers?
It would help us to know what exactly you are trying to do. Boot from the live CD in the PSX emulator? Run a command?

 - search
(sorry I don't know much about PSX)

its alright :P PSX is a PS1 emulator, A lot of people have been having problems with PSX giving a segment fault. I tried the fix people have come up with which is shutdown pulse audio while the emulator runs. But for me pulse Audio WILL NOT DIE!!!! (xD) or the fix is just not working.

BUMP!

---

### Post by Hatsune Miku on 2010-10-27
Bump

---

### Post by Silent Warrior on 2010-10-27
Dude, no reason to bump a thread because you don't get a reply for one hour... On the other hand, I, for one, have no idea how to sort this out.

As an extreme measure, you could install a bunch of ALSA-packages (or double-check that a bunch of ALSA-packages are installed :) ) and then uninstall PulseAudio. It sounds like that's what the fix is about - though you might be better off getting your information from the pSX-community. Likely the binary wasn't compiled with PA-support in mind.

---

### Post by Hatsune Miku on 2010-11-27
> **Silent Warrior said:**
> Dude, no reason to bump a thread because you don't get a reply for one hour... On the other hand, I, for one, have no idea how to sort this out.

As an extreme measure, you could install a bunch of ALSA-packages (or double-check that a bunch of ALSA-packages are installed :) ) and then uninstall PulseAudio. It sounds like that's what the fix is about - though you might be better off getting your information from the pSX-community. Likely the binary wasn't compiled with PA-support in mind.

Sorry i have been gone for so long! Anyway the problem is coming from Pulse Audio according to some googling i have been doing :) So i do not think ALSA packages would do anything :c Anyone got any other clue?

---

### Post by oleink on 2010-11-27
> **Hatsune Miku said:**
> Sorry i have been gone for so long! Anyway the problem is coming from Pulse Audio according to some googling i have been doing :) So i do not think ALSA packages would do anything :c Anyone got any other clue?

Hi and welcome to the forums.  This may not be helpful, but as the 2nd poster said this is usually fixed through reinstalling something.  Try reinstalling pulse (or updating) and reinstalling PSX

PS nice profile pic

---

### Post by kistina on 2010-11-29
> **Hatsune Miku said:**
> Sorry i have been gone for so long! Anyway the problem is coming from Pulse Audio according to some googling i have been doing :) So i do not think ALSA packages would do anything :c Anyone got any other clue?

I did as the other person suggested and it worked.  Pulse Audio and ALSA are both sound servers, they do the same thing, if you have one you don't need the other, so installing ALSA packages(if you don't already have them) and then uninstalling Pulse Audio should work.  But you most likely need to change settings in some of your audio programs after getting rid of Pulse.  Also hi everyone, since this is my first post I think.

---

### Post by Hatsune Miku on 2011-01-05
> **kistina said:**
> I did as the other person suggested and it worked.  Pulse Audio and ALSA are both sound servers, they do the same thing, if you have one you don't need the other, so installing ALSA packages(if you don't already have them) and then uninstalling Pulse Audio should work.  But you most likely need to change settings in some of your audio programs after getting rid of Pulse.  Also hi everyone, since this is my first post I think.

YAY :D! I was also thinking the same thing at a point. I installed Arch Linux and found it had the same problem when i used Pulse Audio and not ALSA, Hmm odd if you ask me O:! Would a mod please sticky this for future help on this problem? Thank you! :)

With love
     Hatsune Miku <3

---

