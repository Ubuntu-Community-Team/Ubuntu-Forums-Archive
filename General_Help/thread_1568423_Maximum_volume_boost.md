---
title: "Maximum volume boost"
date: 2010-09-05
forum: General Help
---

### Post by J V on 2010-09-05
My system barely makes any noise with the speakers, alsa, pulse and totem set to 100%...

It's about 6 times too weak.

I need a maximum volume boost, something along the lines of modprobe?

Edit: Please help, this is unusable...

---

### Post by J V on 2010-09-05
Bump - This is a huge problem and all other requests for help on this matter were given up on...

---

### Post by linux18 on 2010-09-05
install aumix, then run it drom the command line 
I believe it has 10,000% gain

---

### Post by J V on 2010-09-05
It doesn't have any at all... All it's doing here is the same as alsamixer, the same as sound prefs, the same as the volume shortcuts...

Unless theres some hidden function I know nothing about?

For example: Current status is...

Volume control 0 to 100

Want it to be 0 to 600

That way it will just be a general all round sound beefing up...

---

### Post by J V on 2010-09-06
Bump: Don't want to have to sift through ALSA source and figure out how to recompile it with tweak...

---

### Post by cottfcfan on 2010-09-06
Just been reading this, may help.

[http://ubuntuforums.org/showthread.php?t=1569067](http://ubuntuforums.org/showthread.php?t=1569067)

---

### Post by J V on 2010-09-06
Alsa is working as advertised, the problem is that the max volume is too low... I also can't do anything with asound.conf as my particular chip has no models available in the documentation.

I would need to know where in alsa I could change the source to triple the volume: Something which is hard to find...

---

### Post by jmfal on 2010-09-06
Hi JV

You can try the pulseaudio equalizer from psyke83 ppa

my volume was acceptible but not real loud, added p/a eq made it painfully loud.

14band eq w/pre amp, settings are very touchy, you don`t need to move slider alot to change volume

I found it by searching multimedia/video section>using search this forum>pulseaudio equalizer>thread by jrounds>reply by psyke83

hope this solves your problem

---

### Post by J V on 2010-09-06
Bingo! thanks jmfal ;P

---

