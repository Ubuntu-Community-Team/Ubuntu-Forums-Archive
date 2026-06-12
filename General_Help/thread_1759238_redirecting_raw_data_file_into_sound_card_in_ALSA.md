---
title: "redirecting raw data file into sound card in ALSA?"
date: 2011-05-15
forum: General Help
---

### Post by LanguidLegend on 2011-05-15
I have an exercise for my class that I'm stumped on:
[INDENT][COLOR="DimGray"]Redirect mouse device into a file.

sudo cat /dev/input/mice > rawmouse.data
Move the mouse a bit and then type CONTROL-C.

Note that on some distro's you'll need to sudo to bypass device files' restricted permissions.

Now, cat that file to the sound card.

cat rawmouse.data > /dev/dsp
Sounds horrible, doesn't it?

So that's how we make sound, by throwing bytes at the sound card.[/COLOR][/INDENT]
However, based on some research, I've found out the /dev/dsp is based on OSS, whereas Ubuntu now uses ALSA (Advanced Linux Sound Architecture) which has a different setup, which doesn't include /dev/dsp.

So my question is this: Is there a way to write data to the sound card (the way the example does) with ALSA?

---

