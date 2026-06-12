---
title: "Sound stutter problem in VBA"
date: 2011-01-07
forum: General Help
---

### Post by shatanas on 2011-01-07
I've installed VisualBoyAdvance via the Synaptic Package Manager, but  whenever I load a game the sound is jagged and cut, although the  emulation works at normal speed.

I had a similar problem with Spotify running under Wine which, when  adjusted to the settings specified on the website could not play  anything, popping up a message "Spotify cannot play music, there is a  problem with your sound card".

I don't know what I've fiddled with, but I launched it again and right  now it's playing beautifully smooth music (spotify) whereas the VBA is  still in the wrong.

Help?

---

### Post by mauricio.dev on 2011-01-27
Hey, I think it solved when turning Options-> Frameskip -> Throttle -> 100%
Tell us if it works for you too.
I tested on ubuntu maverick with pulseaudio sound (and libsdl1.2debian-pulseaudio)
I also achieved good results by installing libsdl1.2debian-esd (this disables the pulseaudio version)
But as my sound control started getting buggy I've reinstalled the pulseaudio and tested some more.

---

