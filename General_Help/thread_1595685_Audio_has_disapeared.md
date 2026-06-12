---
title: "Audio has disapeared"
date: 2010-10-13
forum: General Help
---

### Post by mdmorash on 2010-10-13
I have just discovered that my audio is gone. Everything appears to be correct, but there is no sound at all...

---

### Post by happyhamster on 2010-10-13
Could you show the output of:
```

cat /proc/asound/cards

cat /proc/asound/modules
```
It will show if the hardware is recognized and which audio modules are in use.

You can run those commands in a terminal (Applications-->Accessories-->Terminal). BTW, to copy/paste in a terminal, highlight the text you want to copy, and paste by clicking the middle-mouse button (or use shift-ctrl-c and shift-ctrl-v). Good luck.

---

### Post by mdmorash on 2010-10-13
> **happyhamster said:**
> Could you show the output of:
```

cat /proc/asound/cards

cat /proc/asound/modules
```It will show if the hardware is recognized and which audio modules are in use.

You can run those commands in a terminal (Applications-->Accessories-->Terminal). BTW, to copy/paste in a terminal, highlight the text you want to copy, and paste by clicking the middle-mouse button (or use shift-ctrl-c and shift-ctrl-v). Good luck.

0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf6400000 irq 16

and 

0 snd_hda_intel

---

### Post by happyhamster on 2010-10-13
Ok, so hardware is recognized, and a module is loaded. Go to System-->Preferences-->Sound and take a look at the Hardware and Output options to see if everything is unmuted and the correct profiles are chosen, etc. 

Also, go to System-->Preferences-->Startup Applications to make sure the Pulseaudio options are ticked.

What ubuntu version are you using? Is this a laptop (and if so, which one)?

Could you also show the output of:
```

aplay -l

```
It will (usually) give a bit more info about the soundcard.

Good luck.

---

### Post by mdmorash on 2010-11-07
I fixed this by going into synaptic and "rolling back" the kernal. Everything started working again.

---

