---
title: "Choose output device"
date: 2011-01-08
forum: General Help
---

### Post by neon401 on 2011-01-08
Hello

Is there any way to select which output device a program uses? I notice many Ubuntu programs lack the choice to choose where the sound is outputted, for example Rhythmbox and Exaile.

I have 3 sound outputs (Internal, PCI, HDMI) connected and I'd like to for example use the PCI card as default audio device but play music from Rhythmbox through the internal motherboard output.

Thanks in advance

---

### Post by kostkon on 2011-01-08
Yes, you can with the *PulseAudio Volume Control* utility. Just install it using the software centre.

Then, to use it just start your application and then open the volume control utility. In the *Playback* tab you'll see its audio stream and next to it the devices drop-down menu that it will allow you to set the output device for this application.

The good thing is that pulseaudio will remember your choice so you'll only need to do this once.

---

### Post by neon401 on 2011-01-08
> **kostkon said:**
> Yes, you can with the *PulseAudio Volume Control* utility. Just install it using the software centre.

Then, to use it just start your application and then open the volume control utility. In the *Playback* tab you'll see its audio stream and next to it the devices drop-down menu that it will allow you to set the output device for this application.

The good thing is that pulseaudio will remember your choice so you'll only need to do this once.
Thank you so much!

---

