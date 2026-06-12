---
title: "Need help getting sound"
date: 2011-12-08
forum: General Help
---

### Post by jras20 on 2011-12-08
I need help getting sound on a Dell netbook,  I see the icon but no audio comes out of the speakers.  The service tag is 3r16qj1.  Thanks for any help!

---

### Post by lechien73 on 2011-12-08
What version of Ubuntu are you using? If you go to the Sound control panel applet, you can check and, if necessary, change the output device. Maybe it's automatically picked up a different output.

---

### Post by jras20 on 2011-12-08
> **lechien73 said:**
> What version of Ubuntu are you using? If you go to the Sound control panel applet, you can check and, if necessary, change the output device. Maybe it's automatically picked up a different output.

10.04 I tried all the sound outputs and still no luck.

---

### Post by lechien73 on 2011-12-08
Ok, please could you post the output of:

```
aplay -l
```

Have you checked to see if headphones work?

---

### Post by jras20 on 2011-12-08
> **lechien73 said:**
> Ok, please could you post the output of:

```
aplay -l
```

Have you checked to see if headphones work?


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Headphones does not work either

---

### Post by lechien73 on 2011-12-08
I think it could be an alsa problem. I'm just taking a look to see what version was pre-installed with 10.04, and how we can upgrade it.

This link might help you: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

