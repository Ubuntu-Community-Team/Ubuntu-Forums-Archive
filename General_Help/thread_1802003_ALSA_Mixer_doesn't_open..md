---
title: "ALSA Mixer doesn't open."
date: 2011-07-11
forum: General Help
---

### Post by ssreddy555 on 2011-07-11
After installing from Synaptic, ALSA Mixer doesn't open.

I have re installed but it still doesn't open.

Any suggestion how to go about it?

---

### Post by mali2297 on 2011-07-13
What happens if you run
```

alsamixer

```
in the terminal? Any error message?

---

### Post by ssreddy555 on 2011-07-14
Presently away from home. Will post as soon as I come back in 5 days.

Thanks for the reply.

---

### Post by ssreddy555 on 2011-07-17
This is what it shows:

cannot load mixer controls: Invalid argument

---

### Post by mali2297 on 2011-07-17
What does *aplay -l* say? 

What kind of sound card do you have? 

Is it just alsamixer that does not work or do you lack sound completely? 

When did the problem occur? Already from the first install of Ubuntu or later?

---

### Post by ssreddy555 on 2011-07-17
This is the output of the command:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My sound output is alright. It's only ALSA Mixer that's not opening - I need these controls to make the mic work in Skype by unmuting some controls.It's not working right now.

It's so from the time the OS is installed.

---

### Post by mali2297 on 2011-07-17
Strange. You could try running *sudo alsamixer*.

An Internet search lead me to this bug report: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/613248](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/613248), but I am not certain that it is relevant.

---

