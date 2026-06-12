---
title: "Cannot record audio line in from sound card"
date: 2009-09-17
forum: General Help
---

### Post by cbraxton on 2009-09-17
On my old Ubuntu 6.06 Dapper system it was trivial to get audio input working to digitize old records and tapes, in fact all I had to do was bring the audio to the sound card's line input and it would play through the speakers and be available for recording in Audacity or Gramofile.

On my 9.04 Jaunty setup, I just can't get this working. Line input just seems to go nowhere. In Audacity if the "monitor input" function is used on the input meter you can see there is audio in there somewhere, but you can't hear it through the speakers and Audacity does not record it.

Hardware is Asus M4A78T-E motherboard built-in audio. (Shows up as "ATI SB VT1708S.") My sound preferences are set to "Autodetect" for sound playback and that seems to work as media files play OK. Sound capture is set to "Pulseaudio Sound Server." (Changing this to the other available settings does not seem to have any effect.) Default Mixer Tracks is set to "HDA ATI SB." (Once again, changing this seems to have no effect.) Input levels are cranked up and not muted.

Audacity is set to "ALSA: Pulse" for playback and recording. Once again, changing these appears to have no effect.

There are an awful lot of settings here and it is not really clear how they affect each other. How can I get this to work and get back the recording functionality I had in Ubuntu 6.06?

---

