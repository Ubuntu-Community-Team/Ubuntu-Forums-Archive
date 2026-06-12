---
title: "Routing all sound through S/PDIF"
date: 2009-11-21
forum: General Help
---

### Post by yonkiman on 2009-11-21
I'm running 64 bit Unbuntu 9.10. 

Some of my apps (Hulu) send sound out to my analog output
Some of my apps (MythTV) send sound to my S/PDIF output
Some of my apps (Banshee, VLC) have gone silent (no sound on any output)

A week or two everything was going out the SPDIF port.  I'm not sure what happened - I installed the recommended Synaptic updates and a youtube player called minitube (that may be the prime suspect). 

MythTV audio settings:
[INDENT]Output device: ALSA:digital
Passthrough Output Device: ALSA:iec958:{AES0 0x02}
Max Audio Channels: Stereo (no sound if I pick 5.1)
Upmix: Passive
Enable AC3 to SPDIF passthrough: Checked
Enable DTS to SPDIF passthrough: Checked
Aggressive Sound Card Buffering: Not checked
Use Internal Volume Controls: Not checked[/INDENT]

Do I need to go into every single application and try to force SPDIF, or can I make the default audio path SPDIF (which it seemed to be until a few days ago)?

My goals:
[LIST]All audio out on SPDIF (I don't care if it's also on the analog outputs or not)[/LIST]
[LIST]When the source is digital (i.e. basically all the time), no processing (resampling, scaling, etc.) anywhere in the stream.[/LIST] 

aplay -L output is below in case it's helpful (there seem to be an awful lot of items in it!??!!).

```
:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
```

---

### Post by yonkiman on 2009-11-28
Found the problem.  Opened System/Preferences/Sound, clicked on the Hardware tab.  The relevant device was set to "Analog Stereo Input".  So I thought it only had to do with the inputs, whereas my problem was with the output.  So I never selected the device, then clicked on the Profile settings below.  When I did, I chose "Digital Stereo (IEC958) Output + Analog Stereo Input" and voila!  Happiness.  Hope this helps someone else.

---

