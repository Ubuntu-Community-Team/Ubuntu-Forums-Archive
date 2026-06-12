---
title: "Troubleshooting ALSA"
date: 2010-08-19
forum: General Help
---

### Post by EricJonsson on 2010-08-19
So I plugged in some fresh 5.1 speakers onto my HTPC system, and... Well, ALSA ain't making sense to me. Basically, I seem to be stuck with stereo audio.

```
eric@gimli:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
[U]surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers[/U]
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```So there's the "surround51"-device I should be using. Now, making sure that PulseAudio is disabled (that's a problem for later) I run the following:
```

eric@gimli:~$ speaker-test -t wav -D surround51 -c 6

speaker-test 1.0.22

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```If I set the number of channels to two, (-c 2) I get audio from Front Left and Front Right, ie. regular stereo. If I use the device "plug:surround51" with six channels, audio plays, but it silently ignores the center, subwoofer and both rear speakers.

Can anyone shed some light on this? What should I do to get full 5.1 audio working?

---

### Post by megacrypto on 2010-08-31
any luck with this ... i have the same problem .. 3-stack on mobo and what i found out that for some reason now the sound (surround) goes out all 3 plugs (i.e front from middle, rear from bottom, and LFE from top) it used to send all sound from the middle plug !!

this only happened after i upgraded to lucid

---

### Post by ganar on 2010-10-31
I'm having the same problem and am interested in knowing if you managed to solve it in Karmic ( or any other version)

---

### Post by EricJonsson on 2010-11-01
> **ganar said:**
> I'm having the same problem and am interested in knowing if you managed to solve it in Karmic ( or any other version)
Indeed I did. Better yet, I wrote down how. :)

[Here you go!]("http://www.acc.umu.se/%7Eericj/?q=node/32") Hope it works.

Edit: This was on a machine running Lucid.

---

