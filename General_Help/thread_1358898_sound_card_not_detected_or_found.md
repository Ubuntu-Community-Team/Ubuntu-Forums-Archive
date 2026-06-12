---
title: "sound card not detected or found"
date: 2009-12-18
forum: General Help
---

### Post by muse3332 on 2009-12-18
hi im running ubuntu 9.10 karmic koala and no one has replied to my posts they have but they just give up when were half way through so plz have a heart help me with my no sound please i know you probally have better things to do but ive been trying to find the solution to this problem forever!! plz dont foward me to a diffrent forum cuz evryone has a difrrent solutin plz plz plz!!! my sound xcard is not detected i put in aplay and it said no soundcards found i did 3 clean installs sop plzzzz  :confused::confused::confused::confused::confused::confused:

---

### Post by kostkon on 2009-12-18
Give in a terminal:
```
lspci | grep Audio
```
and post the output here.

One thing you could try is to install the following package:
```
linux-backports-modules-alsa-karmic-generic
```
and then reboot.

---

