---
title: "alsa sound problems"
date: 2006-04-03
forum: General Help
---

### Post by Intangir on 2006-04-03
if i set my default sound card (in the gnome sound settings) to my SBLive i can't use the hardware string for the device in any alsa programs (and default doesnt work on .. poorly supported alsa programs like cedega)

cedega doesnt seem to work with any of the settings in ~/.asoundrc but it works with the hardware string alsa identifiers like 'hw:1,0'

on gentoo, i can share hw:1,0 (my SBLive! card) on both xmms's alsa plugin, and cedega, they both manage to play sound with that setting

but on ubuntu, with the SBLive set as my default, i can only use 'default' as alsa device on xmms, and cedega can't seem to use alsa at all! (it doesnt understand what 'default' means, and the 'hw:1,0' doesnt work on ubuntu with SBLive as my default soundcard)

SBLive supports more than one channel or whatever by default or hardware mixing? muxing? by default (not sure what its called, more than one application can use it, and it plays streams from them simultaniously) on windows and gentoo, but for ubuntu something fishy about the way its setting it up and using it isnt allowing that

maybe it has to do with esd?.. i dont know

anyone know how to set it up so its still sharable? and i can use it in cedega with the hardware string?

---

### Post by Intangir on 2006-04-03
btw i have 2 sound cards, SBLive comes up and the 2nd one on gentoo, and i dont know how to change the order, i tried both hw:0,0 and hw:1,0 on cedega on ubuntu just incase it was changing the order somehow, neither worked

and neither worked on xmms either, only 'default' works

---

### Post by kudu on 2006-04-03
Good questions I'd love answers to. ](*,)

---

