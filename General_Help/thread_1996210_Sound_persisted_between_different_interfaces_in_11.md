---
title: "Sound persisted between different interfaces in 11.10 but not in 12.04?"
date: 2012-06-04
forum: General Help
---

### Post by Los Frijoles on 2012-06-04
I recently installed the pulseaudio equalizer from the webupd8 repository and I noticed something that used to work very well on Ubuntu 11.10 but doesn't work in 12.04 (the equalizer added an audio interface and this made me notice).

In Ubuntu 11.10 if I set the volume when my headphones weren't plugged in it would change the volume for the 'Analog Output' section on the output tab. Then, if I plugged in my headphones and set the volume when those were plugged in it would save the volume to the 'Headphones' section of the output tab. Whenever I switched between the two it would remember my volume settings and I really found that handy since I have to turn up the volume much higher for my speakers than my headphones and I don't appreciate audio blasting in my headphones when I plug them in before remembering to turn down the volume. In Ubuntu 12.04 this audio volume saving "feature" was removed.

The issue I am having now with it is that with the equalizer if I change the equalizer setting it changes the interface automagically to the "LADSPA Plugin Multiband EQ ....." interface and changes the volume to match my system volume (which is at about 40%). Since the sound goes program->equalizer->output interface and the equalizer is set to the same volume as the output you get only 40% of the original sound going to the output before it is attenuated for volume by that driver. What I would like to do is set the EQ volume to 100% and then have it stick that way rather than changing every time I change something and it gets re-selected by me changing some setting. Does anyone know how I can do this?

Thanks in advance for any help.

---

