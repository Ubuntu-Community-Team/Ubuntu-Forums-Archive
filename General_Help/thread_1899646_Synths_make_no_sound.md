---
title: "Synths make no sound"
date: 2011-12-24
forum: General Help
---

### Post by disnominal on 2011-12-24
Hello!!
I have just installed a variety of synths (some through the software center and others which I compiled); unfortunately, none of them produce sound.
I am unsure as to what the issue is; however I am aware that my computer can play youtube. Also, I noticed that after installing jack, jack2, and libjack-dev (all out of my ignorance as to which one was actually the correct dependency), ubuntu does not make the sound effect it used to when I would change the volume using my keyboard, which I find to be strange.

Anyways, I appreciate any and all help;
Thank you so much in advance!

---

### Post by guyver_dio on 2011-12-24
So youtube plays sound, have you opened any local songs or videos to see if they play sound?

What exactly do you mean by synths? Are they synth programs or synthesized audio files?

My first thought was that those synths/synth programs are midi based? If so, you may need to install something like timidity (which can be installed through the software center). After it's installed you need to go into the settings or preferences of the program and under playback settings you'll see somewhere that something like midi-0 is selected. You should be able to drop this down and see something like timidity-0 can be select. Select the timidity one and hopefully it should produce sound.

---

### Post by disnominal on 2011-12-25
Hello guyver_dio!
Yes, I have opened local sources of sound and they do work.
By synths, I mean synth programs, and they are not midi based, so I do not think the timidity approach will work, though I appreciate your efforts greatly!
Any other ideas? :-)

---

