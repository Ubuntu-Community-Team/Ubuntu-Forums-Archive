---
title: "dtmfdial cannot access sound device"
date: 2010-11-02
forum: General Help
---

### Post by rlong on 2010-11-02
Hey folks,

I'm running 10.10 x64 with pulseaudio working but no matter what sound device I specify with sudo dtmfdial's --output-dev option, I get the following:
```
ioctl(SNDCTL_DSP_CHANNELS): Inappropriate ioctl for device

```

My audio devices are:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
```

I have tried specifying devices such as:
```
/dev/dsp
/dev/snd/hwC0D0
/dev/snd/hwC1D0
/dev/snd/pcmC0D0c
/dev/snd/pcmC0D0p
/dev/snd/pcmC0D1p
/dev/snd/pcmC1D3p

```

I've been searching for a couple hours and have yet to find a solution to this issue. I've also tried strace but couldn't make heads or tails of the output. Any help appreciated. Thanks!

R

---

### Post by Mercedes300 on 2012-02-09
I'm having the same problem.

I'd love to see a solution. :)

Anyone?

-John

---

### Post by dcstar on 2012-02-09
> **rlong said:**
> Hey folks,

I'm running 10.10 x64 with pulseaudio working but no matter what sound device I specify with **sudo** dtmfdial's --output-dev option, I get the following:
........

When you are in a user session you should probably not use sudo, Pulseaudio runs in user mode.

I have just installed this package and got that error on the first run, but subsequent runs plays the tones through my speakers. If you wait for a timeout of about 12 seconds after the system plays a sound to expire then it seems to work.

---

