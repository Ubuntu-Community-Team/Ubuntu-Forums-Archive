---
title: "Lost sound after upgrade"
date: 2009-11-16
forum: General Help
---

### Post by wersdaluv on 2009-11-16
I made a clean karmic 32 install. I've been on karmic 64 since it was released, and decided to replace it with the 32 bit version. In the fresh install, I installed some packages and did an upgrade. After that, I rebooted. After rebooting, I can't play any kind of sound anymore. Before I did that, I was even playing music. 

I'm on an intel 82801H.

Any idea?

---

### Post by lloyd_b on 2009-11-16
> **wersdaluv said:**
> I made a clean karmic 32 install. I've been on karmic 64 since it was released, and decided to replace it with the 32 bit version. In the fresh install, I installed some packages and did an upgrade. After that, I rebooted. After rebooting, I can't play any kind of sound anymore. Before I did that, I was even playing music. 

I'm on an intel 82801H.

Any idea?

In a terminal window, run the following and post the results:```
aplay -l
```This will show you which audio devices are available to Alsa.

I had a similar problem (Intel 82801EB/ER), which was solved by adding the following to the end of "/etc/modprobe.d/alsa-base":```
options snd-intel8x0 ac97_quirk=3
```but this will only help if you actually have the AC97 hardware (the 82801 chip does NOT actually provide the sound - it's just "glue" for the actual sound hardware).

You can verify if you have AC97 hardware by looking at the "multimedia" entry from running 'lswh' in a terminal window.

Lloyd B.

---

### Post by wersdaluv on 2009-11-16
> **lloyd_b said:**
> In a terminal window, run the following and post the results:```
aplay -l
```This will show you which audio devices are available to Alsa.

I had a similar problem (Intel 82801EB/ER), which was solved by adding the following to the end of "/etc/modprobe.d/alsa-base":```
options snd-intel8x0 ac97_quirk=3
```but this will only help if you actually have the AC97 hardware (the 82801 chip does NOT actually provide the sound - it's just "glue" for the actual sound hardware).

You can verify if you have AC97 hardware by looking at the "multimedia" entry from running 'lswh' in a terminal window.

Lloyd B.
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

_____________________

I'll check your fix as soon as I can! Thanks a lot! :)

---

### Post by wersdaluv on 2009-11-17
> **wersdaluv said:**
> :~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

_____________________

I'll check your fix as soon as I can! Thanks a lot! :)
It din't make a difference :(

---

### Post by wersdaluv on 2009-11-17
On the "Sound Preferences" dialog, in the Hardware and Input tabs, no device is listed. In the Output tab the only device is "Dummy Output"

There's the problem. Any idea why I have this and how to fix it? :)

---

