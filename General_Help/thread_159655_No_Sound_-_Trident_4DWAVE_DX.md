---
title: "No Sound - Trident 4DWAVE DX"
date: 2006-04-13
forum: General Help
---

### Post by cchat on 2006-04-13
I have recently installed Breezy and have no sound.  I am using a Trident 4DWAVE DX soundcard.   I went to system>preferences>sound and there was no card listed.  "Enable sound server startup" and "Sounds for events" were selected.

Device Manager recognizes that there is a card, but shows "Device type:" and "Capabilities:" as "unknown"

Sound card is not listed in /etc/modules file

I also went to the alsa-project website for the trident 4dwave dx card and discovered that "soundcore" is installed as a module using the "modinfo soundcore" command, but could not understand anything else on that site which appeared to be about recompiling the kernel.  

Anyone have a clue as to where I can go next?](*,)

---

