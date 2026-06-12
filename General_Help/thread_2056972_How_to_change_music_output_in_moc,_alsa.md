---
title: "How to change music output in moc, alsa"
date: 2012-09-12
forum: General Help
---

### Post by BeniaminK on 2012-09-12
Hello,
I've been using [moc]("http://moc.daper.net/") for a while on a laptop and it is great, but then I wanted to plug in USB radio as an output, rhythmbox and other players detected new output device, but moc has output hardcoded in ~/.moc/config, where is stated:

```
# Sound driver - OSS, ALSA, JACK, SNDIO (on OpenBSD) or null (only for
# debugging).
# You can enter more than one driver as a colon-separated list.  The first
# working driver will be used.
SoundDriver             = JACK:ALSA:OSS

# Jack output settings.
JackOutLeft             = "alsa_pcm:playback_1"
JackOutRight            = "alsa_pcm:playback_2"

# OSS output device.
OSSDevice               = /dev/dsp

# OSS Mixer device.
OSSMixerDevice          = /dev/mixer

# OSS Mixer channel: pcm or master.
OSSMixerChannel         = pcm

# Second OSS Mixer channel: pcm or master.
OSSMixerChannel2        = master

# ALSA mixer device.
AlsaMixer               = PCM

# Second ALSA mixer device.
AlsaMixer2              = Master

# ALSA output device.
AlsaDevice              = default
```

And I have no idea, what to change. Some tutorial on devices and some additional help is needed.

I suppose, I have to change something in alsa, but neither in moc nor in alsamixer, I do not know how to check, where is my usb device and what to change.

---

