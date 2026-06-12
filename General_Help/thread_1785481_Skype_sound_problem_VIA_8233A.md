---
title: "Skype sound problem VIA 8233A"
date: 2011-06-18
forum: General Help
---

### Post by boxcorner on 2011-06-18
Hello

I am running Ubuntu 10.10
I have installed Skype (Beta) Version 2.2.0.25
video is working but sound quality is bad
I am using a Labtec AM-22 mic 

I have installed ALSA Mixer, which shows:
VIA 8233A with Realtek ALC650D

I don't know how to configure ALSA Mixer, but I have enabled everything labelled Mic, and I have cranked everything up.

Also, System > Preferences > Sound > Input volume = maximum

When I test call in Skype, the sound level is very low, and there is a lot of background noise.

Could someone please tell me what I need to do to improve sound quality?  
Also, where do I need to go to find instructions on how to configure ALSA Mixer?

Thanks in advance.

Addendum
========

Having played around with ALSA Mixer, the following settings seem produce the optimum result:

(settings left to right)

Master Mono Playback OFF
Playback ON Sync ON (this needs to be ON to hear the other person)
Center ON (this needs to be ON to hear the other person)
LFE ON (this needs to be ON to hear the other person)
Surround Shared ON
Surround Playback ON Sync ON (this needs to be ON to hear the other person)
Beep ON
Phone OFF
Mic Mic1 OFF
Mic Playback OFF
Line OFF Sync OFF
CD OFF Sync OFF
Video OFF
Aux OFF
PCM ON Sync ON (this needs to be ON to hear the other person)
Capture ON Mic Mic Sync ON (this needs to be ON for the other person to hear you)

(everything else to the right OFF)

NB - USB Camera: USB Mixer Mic Capture OFF Auto Gain Control OFF

however the sound quality is still poor and there is still a lot of background noise.

---

