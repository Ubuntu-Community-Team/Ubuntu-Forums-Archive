---
title: "Soundcard question"
date: 2010-08-31
forum: General Help
---

### Post by btown1987 on 2010-08-31
Ok so im a little new to linux. I have an EVGA P55 FTW mobo with a realtek HD Audio soundcard on it. There are a mic and headphone minijack on the front of the case. In windows I can split the card and make the front headphone slot into its own recognized output. This allows me to output things like TeamSpeak to only my headphones and not my speakers.

ok now fast forward to my linux x86 install. I have teamspeak 3 installed and want to do the same thing, force TS to output through the front jack only. I have tried all of the outputs that teamspeak has registered in its settings and all of them just output to regular speakers.

I am using the default ALSA driver/ configuration that the system setup when i installed it.

Any ideas on how I can do this? Remember im still new to this so please allow for my deer in headlights stare as you try to explain complex ideas :)

Thank you.

---

### Post by ptptaylor on 2010-08-31
This might not be of any use, as I don't know how to make it applications specific.
But to get it to output through your front connector it will be a setting (if you're using linux) in the sound icon (top right) preferences ---output ---then connector. Choose it as you wish. If you change it, I am worried that it will mean all the audio gets put through the front instead of just the teamspeak as you wish.

---

### Post by btown1987 on 2010-08-31
after a little more investigating i have found that i cant choose a different connector in the sound properties. I can for my mic, but not for my output. I compiled + installed the realtek hd audio driver, but it hasn't helped. Im going to poke around some more in the alsa-base.conf

---

### Post by btown1987 on 2010-08-31
Some more to report...

Alsa mixer shows that my sound card is ALC 889 which is correct. Its and 8 channel card. However the sound porperties shows it as internal audio 1 output / 1 input which is incorrect.

---

### Post by btown1987 on 2010-08-31
Ok got it now, it turns out that all i had to do was edit /etc/asound.conf to set the default card as card 0 from /proc/asound/cards which is the correct card.

---

