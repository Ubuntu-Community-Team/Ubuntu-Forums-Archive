---
title: "Sound problem with asus motherboard"
date: 2009-10-02
forum: General Help
---

### Post by capaman on 2009-10-02
I installed 9.04 and have not been able to get the sound working.  I have an Asus CG5270 mainboard with onboard sound, and could find no documentation anywhere telling me what kind of sound card I have.

With the command "aplay -l" I get...

[B]card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]

With the command "lspci -v" I get...

[B]01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 82f3
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at fe9fc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>[/B]

With the command "cat /proc/asound/card0/codec#* | grep Codec" I get...

**Codec: Realtek ALC887**

I am still not sure what alsa sound driver module I should use to get the the sound working as all the information seems to be conflicting.  Any help appreciated, thanks.

---

### Post by ucoder on 2009-10-07
Hi!

Are you getting any sound? Speakers? Headphones?

I too have an ASUS motherboard with the same sound chip, Realtek ALC887, I get sound from speakers just fine, but nothing from headphones.

I've been trying to understand this for the past couple of hours, but no real progress.

If I open up alsamixer from the terminal, I can see the headphones column "flat" and I can't adjust it. Other columns move correctly.

The only thing I learned was that the Realtek ALC887 is NOT mentioned in ALSA documention HD-Audio-Models.txt so I guess it's just not supported properly.

I would also like to hear if someone has got this working :)

---

### Post by philinux on 2009-10-07
I've got an asus motherboard and checking in codec#0 it says Realtek ALC883. Got no problems with sound here using pulse or alsa or autodetect.

---

### Post by ucoder on 2009-10-08
That's because it's listed in HD-Audio-Models.txt and the Realtek ALC887 is not :)

Apparently there are quite a few variations of the AL88* chip, but not all of them are supported by ALSA.

---

### Post by ucoder on 2009-10-08
Uh oh! I just got this working, simply by switching from digital to analog output in the sound preferences!

It's a little cumbersome of course, having to do that by hand, but at least I get sound from headphones now :)

I have my computer hooked to my stereos via optical s/pdif -cable and that's why I keep it on digital output normally.

---

