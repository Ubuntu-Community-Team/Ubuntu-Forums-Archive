---
title: "Ubuntu command line install sound problems"
date: 2011-08-18
forum: General Help
---

### Post by iamauser on 2011-08-18
I have recently installed Ubuntu 11.04 from the alternative installation CD; the installation was just the command line system. On top of this I have installed xorg and awesome window manager. The only problem I am having is with sound; I am unable to hear sound played through both browser-based Flash and locally stored files.

Is there something that I have to do before I can use sound?

Edit: I have solved the original problem however I would like to know if I can remove pulseaudio as it seems that I am only using alsa.

---

### Post by nothingspecial on 2011-08-18
Do you have alsa-base and libasound2 installed?

---

### Post by iamauser on 2011-08-18
> **nothingspecial said:**
> Do you have alsa-base and libasound2 installed?

Yes, both are installed.

---

### Post by nothingspecial on 2011-08-18
What is your sound card recognised as?

---

### Post by iamauser on 2011-08-18
> **nothingspecial said:**
> What is your sound card recognised as?

Output of 'sudo aplay -l' is

```
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

This is in a ThinkPad R500 if it makes any difference.

---

### Post by iamauser on 2011-08-18
If I use 'sudo' I am able to manually change the volume using 'amixer' and so I am thinking that this is a permissions thing (I can't do this without running 'sudo'). How can I add myself to the audio group?

---

### Post by iamauser on 2011-08-18
(Sorry for the triple post)...

I have added myself to the audio group but I am still unable to alter anything without using 'sudo'. 

If I do 'sudo aplay /usr/share/sounds/alsa/Front_Center.wav' I get the sound, however if I attempt to do this (or adjust the volume) without 'sudo' I get "Invalid card number." from amixer (or just nothing if I use aplay).

---

### Post by iamauser on 2011-08-18
I have solved the problem of no sound now. It seemed that a restart, or equivalent action, was required to allow for the group changes to properly take effect. 

Can I remove pulseaudio as it seems that I am only using alsa?

---

### Post by nothingspecial on 2011-08-18
Sorry, my kids pestered me for a game of cricket :P

You do not need pulse, however I am unsure that, since it is installed, it will not break something if you remove it.

I doubt it.

---

