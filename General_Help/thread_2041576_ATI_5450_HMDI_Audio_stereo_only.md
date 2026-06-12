---
title: "ATI 5450 HMDI Audio stereo only"
date: 2012-08-12
forum: General Help
---

### Post by 000zero on 2012-08-12
Hello all, I am having an issue where my HDMI audio for my ATI 5450 is stereo only.  I know this card can support 5.1 out.  I just installed 12.04 and went the Additional Drivers route to install the ATI proprietary drivers.  I am not sure how I can get 5.1 out from my PC, any suggestions?

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5450
OpenGL version string: 4.2.11627 Compatibility Profile Context

```

If anyone has any suggestions please let me know. thank you

---

### Post by 000zero on 2012-08-13
I have tried installing the 32 bit version of Ubuntu and still not working correctly via the Additional Drivers install.  Also, something to note is that when I try to install the Post-release-updates version it totally fails. I have been searching for more than a day of how to get past this, no one seems to have the same issue I am having. I am going to try installing manually and see what that does, but last time I tried that it failed to install.

any advice is welcome, otherwise its back to Vista :frown:. I don't want to but my HTPC has been down for a month already and I would like to get it going again.

---

