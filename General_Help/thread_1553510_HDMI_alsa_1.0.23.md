---
title: "HDMI alsa 1.0.23"
date: 2010-08-15
forum: General Help
---

### Post by bprins on 2010-08-15
Hi,

I'm still struggling getting HDMI sound on ubuntu 10.04.

I've got the following aplay -l output

```

bas@ubuntu-lt:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

After connecting the HDMI cable to the TV I only get video, but no sound.

Testing via:
- aplay -D plughw:0,0 Noise.wav => sound on laptop
- aplay -D plughw:1,3 Noise.wav => no sound on TV (sound on TV is not muted)

Also, I've checked what alsamixer knows about the HDMI device. 
- alsamixer -> F6 -> select nvidia device:
Then I see "S/PDIF" (which I unmute). Shouldn't it state something like "HDMI"? 

It's not the same is it? [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) gives an overview on the differences between S/PDIF and HDMI. 

Is that the rootcause of my HDMI issues?

Looking forward to your experiences etc.

Thanks.

Bas

---

