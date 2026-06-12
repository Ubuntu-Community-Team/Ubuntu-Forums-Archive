---
title: "ALSA Mixer Settings"
date: 2010-09-26
forum: General Help
---

### Post by DOS Boot on 2010-09-26
I have a netbook which I'm setting up a Netbook Remix LiveUSB for, and the main issue is that when a microphone or other sound source is plugged into the mic jack, sound input will not immediately come through the speakers or headphones, but it can be recorded in Sound Recorder and played back.

In the Terminal, "amixer" is reporting the only mic option as "Front Mic Boost". Shouldn't there be an option just titled "Front Mic" with it's own option to mute and unmute? I think that may be the cause of the issue, because I think Front Mic is set to mute by default in ALSA Mixer, and since that option isn't showing up in the ALSA Mixer GUI or in the Terminal it's technically stuck on mute.

Does anyone know a way that I can add the Front Mic option to the ALSA mixer manually or through an update?

---

### Post by DOS Boot on 2010-09-27
The soundcard in the netbook is an HDA Intel with the Realtek ALC269 chip. It seems that ALSA Mixer may have some issues with these types of chips. 

Has anyone ever came across or fixed an ALSA Mixer issue like this? Would it be possible to manually add the "Front Mic" option to ALSA Mixer by editing it's configuration file or something along those lines?

---

### Post by DOS Boot on 2010-09-27
Is there a way to add new options to ALSAMixer either manually or through an update?

---

### Post by DOS Boot on 2010-10-14
Can sound options be manually added to ALSA Mixer by adding them to ALSA Mixer's configuration file?

---

