---
title: "Pulseaudio sound in vlc player"
date: 2012-05-31
forum: General Help
---

### Post by samwillc on 2012-05-31
Hi everyone,

I have read a few posts but none seem to be having the issue I am having. I have pulseaudio equalizer enabled and that works on mp3 and my other music, and also works fine on youtube. Turning the EQ off/on I can hear a clear difference between the sounds.

However, when using vlc player, I would like to also use the global EQ. When selecting:

Tools > preferences > audio > output module = pulseaudio audio output

...the sound on the videos is noisy/hissing/crackling and sounds terrible.

Selecting:

tools > preferences > audio > output module (ALSA audio output) > HDA ATI SB, ALC892 Analog Default Audio Device

...the sound is fine. However, I can't use the pulseaudio EQ. I tried turning EQ off/on whilst playing back a video and no sound changes at all.

Has anyone else had this? It seems really weird that the EQ works for everything else I use apart from vlc. I have tried pulse audio control (in software centre) and the volumes are all set normally at around 70% so nothing is over the top loud. Also, in alsa sound mixer, my levels are around 80%.

Maybe I am missing some setting in vlc. I have a logitech speakers and sub, which are just plugged into the headphones output jack in the back of the pc, so not using HDMI output for sound.

Thanks if anyone can help or point me in the right direction.

Sam.

---

### Post by roelforg on 2012-05-31
Set the output module to "Default", works fine for me.

---

### Post by samwillc on 2012-05-31
Hi,

Did that a minute ago. Bearing in mind pulseaudio EQ is ENABLED, so my system sound settings are using:

Play sound through:

Digital Output (S/PDIF)
Headphones
Analogue Output
LADSPA Plugin Multiband EQ on Built-in Audio Analogue Stereo <<-----SELECTED

Still no good even when choosing prefs > audio > 'default' in vlc. Strange when I disabled pulseaudio, and then re-enabled, the sound was ok and I could hear it was using the EQ.

Then, turned off vlc, opened again, loaded up another vid, and noise/crackling again.

Something is really not right with the pulseaudio EQ and vlc.

With it OFF and playing sound through default analogue output, no problems. With it ON, sounds awful. This is ONLY for vlc player though, nothing else.

Any other ideas?? Thanks.

Sam.

**edit 31/05/12** - found an easy solution for myself. The type of solution I usually employ when there is clearly a problem and yet it can't be recreated according to a lot of threads and it isn't worth spending a lot of my time on. Simply uninstalled vlc player, and instead, I'm using the built in ubuntu 12.04 movie player, works a charm, plays everything I throw at it, and sounds great through pulseaudio EQ! Win! :D.

---

