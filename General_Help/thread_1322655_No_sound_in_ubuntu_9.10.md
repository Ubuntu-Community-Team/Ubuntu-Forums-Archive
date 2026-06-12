---
title: "No sound in ubuntu 9.10"
date: 2009-11-11
forum: General Help
---

### Post by Davestom on 2009-11-11
Hey Everyone, had same topic in 9.04 - but the fix from there doesnt help at all this time.

**aplay -l**
> aplay: device_list:223: no soundcards found...


**lspci | grep audio**
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

**_What I have done till now?_**
[LIST]
[*]Installing drivers from ALSA
[*]Installing OSS (with crash at end)
[*]Trying to configure alsa-base conf, to activate my model (options snd-hda-intel model=medion)
[*]Installing diverse images (making update from other software sources)
[/LIST]

So my conclusion is, "What now?!" Anyone knows what to do?! 

*It can be mentioned that pulseaudio sees sound coming out, but there is no sound going through the speakers. *

---

### Post by VMOS on 2009-11-11
if pulseaudio sees the sound, have you checked alsamixer and kmix to make sure there is nothing muted?

---

### Post by 824957q on 2009-11-11
I have the same problem but i have pulse audio and riptide and i don't know what to do!

---

