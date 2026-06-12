---
title: "How do you hear mic with bluetooth headset???"
date: 2010-09-22
forum: General Help
---

### Post by demonic_crow on 2010-09-22
What I want to do is hook up a mic to my computer and have the sound play through my bluetooth headset.  Can this be done?  I cant seem to figure out at all.  It play fine through the computer speakers but nothing in BT.  Thanks for all the help.

P.S.  I have Ubuntu 10.04

---

### Post by demonic_crow on 2010-09-22
any thoughts?

---

### Post by kostkon on 2010-09-22
The *PulseAudio Volume Control* utility will be useful.

---

### Post by demonic_crow on 2010-09-23
> The *PulseAudio Volume Control* utility will be useful. 	

What do you mean??? 

I have: 
hardware to BT
output to BT 
input connector Analog Microphone and sound input to BT

But when I go to applications it says nothing is playing it.

I can't hear anything even with the computer speakers unless I run Jack Control.  Still BT won't run under it cause it seem like I still need an app so the BT can connect to it to hear the sound.

---

### Post by demonic_crow on 2010-09-23
When I do choose the Sound input to my BT I notice it tried to take sound from it instead of the mic thats plug into the computer.

---

### Post by efflandt on 2010-09-23
I noticed that when I plug in the dongle for my wireless Plantronics headset and use Sound Preferences to select the headset microphone for input, that shows a graph of sound from the microphone.  It works with Sound Recorder, but does NOT directly pass through to speakers or headphones (depending which is selected).

Not sure what application might be able to pass microphone to speakers, but there does not seem to be any such application installed by default.  That might tend to produce feedback (high pitched squeal) unless the app had something to prevent that.

---

### Post by demonic_crow on 2010-09-23
Well I have my guitar plug up to my computer and into my microphone plug-in.  Im using Jack control with Rakarrack and I can here it perfect through the speakers.  Just have to make sure you connect the right stuff in Jack Control.  Now what I want to do is use my BT headset to listen to my guitar without having to have a headset plug into the computer.  I just can't figure out how to do that for some odd reason.  I don't want to use the microphone on my BT headset but use the guitar.  Maybe this will enlighten some peoples as in what I'm doing.  Sorry if I been a bit confusing.

---

### Post by transmogrifox on 2010-09-23
The BT headset will look like a different audio interface to jack.  Jack needs to be used for input/output on the same interface, so it will either want mic on computer to computer speaker output (same sound card), or mic + speaker from BT device.  It is not friendly toward computer mic to BT headset configuration.

I hope not to discourage you from trying, but just want you to be aware this isn't an arrangement that is designed to work at this point...just so you have an expectation it will be easy.  Being able to do that will require a hack that involves re-sampling as an intermediate step between the two interfaces.

Some people have talked about running two instances of jackd connected to the different audio interfaces then using some kind of jack app to bridge them.  I don't know the names of apps to do that, but in reading forums & blogs I have gathered there is some kind of a hacked-up solution that works for some people with varying results.

Any time I have attempted to start jack with different in/out interfaces it fails to launch.

Pulseaudio might be able to help you.  I am not familiar with Pulseaudio, so I don't know how well it has been playing with jack recently, but maybe it can your bridge in between interfaces ;)... something like mic-in->jack->pulseaudio->bluetooth ...?

Sorry I can't be more help, but then those are some ideas to research.

---

