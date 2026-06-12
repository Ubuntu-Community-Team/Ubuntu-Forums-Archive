---
title: "No Sound"
date: 2010-06-29
forum: General Help
---

### Post by vois2009 on 2010-06-29
Hi,

No sound came out from the audio play, please advise where can i reinstall the the audio driver.

Previously everything is working fine till today.

Anyone can advise. Thanks.

---

### Post by lidex on 2010-06-29
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by vois2009 on 2010-06-29
Whe I go to Application/accessories/terminal it show:  ken@ken-desktop : ~ $

My PC is Dell.

---

