---
title: "try to run before I can walk &#8210; midi (and other things)"
date: 2011-09-03
forum: General Help
---

### Post by engine on 2011-09-03
**what I have**
10.04 LTS, including jack and alsa
a stack of midi files, generated from mup (my scoring package of choice)
a stack of instrument samples in .wav format

**what I'd like to do**
[LIST]
[*]play back the files, using midi commands to select voice from the samples
[*]use an external midi keyboard (I have a Korg microKontrol, among others) to record, again using the samples as voices
[/LIST]

**what I need**
patient, friendly information &#8210; I have the suspicion there will be a lot for me to learn/do to cross all these gaps

Thanks in advance!

---

### Post by CatKiller on 2011-09-03
Playing back MIDI files is pretty straightforward using a software synth like Timidity or FluidSynth. Recording a MIDI performance is not too bad using something like Rosegarden or Ardour. It might work out-of-the-box with JACK, or it might take a bit of trial-and-error with your routing.

That just leaves you playing back with your own voices. It's not something that I've tried and I'm not at my computer to look now, but there may well be something available. I know that the software synths let you load a sound font, and that Hydrogen (a simple drum sequencer) will let you use your own samples to be triggered, but I don't know for sure what there is to do exactly what you want.

---

