---
title: "ALSA in Virtual PC?"
date: 2006-05-04
forum: General Help
---

### Post by Video Toaster on 2006-05-04
I recently installed Kubuntu in a Virtual PC 2004 SP1 virtual machine.  It seems to be working OK for the most part.  However, sound is an issue.  When I tried using the ALSA "snd-sb16" kernel module for the emulated PnP Sound Blaster 16 card, I got a "cpu overload" error from aRts every time KDE played a system sound.  I've since fixed that by switching the the OSS "sb" kernel module; however, that means I don't have access to dmix and can only play one stream of audio.  While this is certainly better than nothing, I'd love to get ALSA working.  Anybody have any ideas?  Thanks!

(Interestingly enough, the reverse is true in Ubuntu - the"snd-sb16" module works perfectly and the "sb" module doesn't work at all.)

---

