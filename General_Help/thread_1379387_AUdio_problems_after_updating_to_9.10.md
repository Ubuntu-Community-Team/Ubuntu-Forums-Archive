---
title: "AUdio problems after updating to 9.10"
date: 2010-01-12
forum: General Help
---

### Post by colobix on 2010-01-12
Hey. For some stupid reason I just had to upgrade from 9.04 to 9.10 when everything worked just fine. Now I can't hear any sound at all.
What do I do? Please help.

---

### Post by Mickser_52 on 2010-01-12
Have you tried checking the settings in System - Preferences - Sound?

---

### Post by colobix on 2010-01-12
Yup. THat was like the first thing I checked. and to see if anything was muted or anything like that.
It doesnt seem to find any audio device.
THe list is empty. You know, in the volumecontrols.
Maybe the new version doesnt have the driver or something. that's kinda weird because it's a very new audio card.

---

### Post by Mickser_52 on 2010-01-12
Beyond my experience I'm afraid. Administration - System test has audio tests but you may have tried that already

---

### Post by colobix on 2010-01-12
YUp. THe test found the audio device but when I did the sound test, nothing happend (no sound). THere is no device in the input list in volumecontrol either.

---

### Post by Woody1987 on 2010-01-12
Same thing happened to me, i installed linux-backports-modules-alsa-KERNEL_VERSION. Reboot, with luck this will fix it for you.

---

### Post by colobix on 2010-01-12
Well, alsa is the right sound card.
OK. I couldn't find a karnel version, but I searched for linux-backports-modules-alsa and found like 8 packages or something.
Sound I just install them all?

---

### Post by michy99 on 2010-01-12
Only install the one for your kernel. You can see which kernel you are running with```
uname -r
```

---

### Post by Woody1987 on 2010-01-12
which kernel are you currently using? type uname -r in a terminal. 

For example, im running 2.6.31-17-generic, so i would install linux-backports-modules-alsa-2.6.31-17-generic

---

### Post by colobix on 2010-01-12
OK so what karnel do I choose? Some karnels wouln't start the graphic, some of them doesnt let me go on the internet, so which one do I choose that will make it all work?
There's a list of atleast 10. they all end with numbers from 17 - 31 I think.

---

### Post by Woody1987 on 2010-01-12
did you install the alsa module mentioned above? if so load the latest kernel when you boot. If not, install it and reboot and let it automatically boot, dont mess with the boot menu.

---

### Post by michy99 on 2010-01-12
I think you missed the point. Enter this in a terminal:```
uname -r
```That tells you which kernel you have. Then install the linux-backports-modules-alsa that matches your kernel.

---

### Post by Woody1987 on 2010-01-12
actually, just run

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
``` 

it will automatically install the correct version.

---

