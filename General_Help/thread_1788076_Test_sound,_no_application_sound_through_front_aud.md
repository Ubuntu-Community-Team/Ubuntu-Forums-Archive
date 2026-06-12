---
title: "Test sound, no application sound through front audio socket - 10.04"
date: 2011-06-22
forum: General Help
---

### Post by Bucky Ball on 2011-06-22
Hi all,

Strange one. Just upgraded my mother-in-law's computer from 8.04 to 10.04 via the update manager. All seems to be working beautifully except ...

* When I run gstreamer-properties and do an output test I get a test sound through the headphones plugged into the front audio socket of the machine using the 'Analogue Headphones' setting in Sound Preferences. (This rules out dead headphones.)

* When I try to play audio through any app I get no sound through the headphones, but if I change the setting to 'Analogue Output' in Sound Preferences I get audio loud and clear through the speakers which are plugged into the audio socket at the rear of the machine.

Any idea what is happening? If I could figure how the gstreamer-properties test is getting audio to the front socket I guess I'd be getting somewhere. I only have the rest of the day to fix this then I drive 750Kms home so hoping there might be some suggestions out there.

Tnx in advance ...

---

### Post by Bucky Ball on 2011-06-22
Incidentally, everything is setup for VT1708B chip. That is what the gstreamer output test is using and also what alsamixer is looking at.

Also in PulseAudio Volume Control, under Playback, I have two 'Alsa Plug-in [mplayer]: alsa playback' permanently. They seem to be doing nothing. When I actually open Gnome Mplayer and play something, a new one pops up. This can play through rear connected speakers but not front connected headphones.

What gives?

---

### Post by Bucky Ball on 2011-06-22
To put this all a little more succinctly:

gstreamer-properties will use front panel headphone socket for output test, applications will not use front panel headphone socket for audio output. ;)

---

