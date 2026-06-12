---
title: "No Sound Tried it ALL"
date: 2009-08-09
forum: General Help
---

### Post by Deten on 2009-08-09
Ubuntu 9.04 amd_64
Fresh install

Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3628
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at da100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


I tried installing alsa 1.0.20, I tried verifying that nothing was muted, I tried tweaking settings in System->Preferences->Sound, I broke things and reinstalled a fresh installation.

I tried every tweak I fan on this forum, adding irq*** thing to the mod alsa file config thing.  

I am completely out of ideas, what can I do to get sound working... any drastic idea is acceptable!

---

### Post by coldReactive on 2009-08-09
You even did this?

[http://www.xappsoftware.com/wordpress/2009/05/05/82801i-ich9-family-hd-audio-controller-on-ubuntu-904/](http://www.xappsoftware.com/wordpress/2009/05/05/82801i-ich9-family-hd-audio-controller-on-ubuntu-904/)

---

### Post by Deten on 2009-08-09
I did try it, but it was a set of 3, two other things...

Let me try it though on the fresh install...

---

### Post by Deten on 2009-08-09
alsa-base is a completely empty file, and after looking, I noticed it doesnt exist.

There is an alsa-base.conf, is that what you meant?

---

### Post by Deten on 2009-08-09
No that didnt help, still no sound at either startup NOR during use

---

### Post by Deten on 2009-08-09
Heres more information, I am not sure what the difference is between the Intel 82801I and this:

deten@deten-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
deten@deten-laptop:~$ 

What is this STAC92xx?

---

### Post by coldReactive on 2009-08-09
> **Deten said:**
> What is this STAC92xx?

That's your main sound controller/device.

[http://www.google.com/#hl=en&q=STAC92xx+ubuntu](http://www.google.com/#hl=en&q=STAC92xx+ubuntu)

Also, are you using HDMI for sound? If so, then it would be ATI's fault.

---

### Post by Deten on 2009-08-09
Also here is the alsa info script:
[http://www.alsa-project.org/db/?f=0a99c27a7a1f7ea878446c1b44d98c28655357b0](http://www.alsa-project.org/db/?f=0a99c27a7a1f7ea878446c1b44d98c28655357b0)

I noticed:

!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


Should Esound daemon be running?

---

### Post by Deten on 2009-08-09
Please please any help would be so nice!

---

### Post by Deten on 2009-08-11
Still No Sound, any help would be nice.

---

### Post by Deten on 2009-08-23
Thanks anyways, I think im gonna try linux mint and see if I have better luck.

---

