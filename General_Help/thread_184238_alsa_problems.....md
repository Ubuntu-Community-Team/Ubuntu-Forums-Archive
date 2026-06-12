---
title: "alsa problems...."
date: 2006-05-29
forum: General Help
---

### Post by dreadbrazen on 2006-05-29
So... did the synaptic update thing today.  It runs smoothly as always.  I reboot.

No sound.  None whatsoever.

So, I'm digging around, reinstalling alsa and what-have-you when I get this message from Synaptic:

E: ld10k1: subprocess post-installation script returned error exit status 1

ld10k1 is the wrapper for ALSA to talk to the emu10k(1/2) library.  For some reason, that package is broken.  I have tried reinstalling it.  Nothing seems to work.  The package is now broken (though it does not say so in synaptic) and will not reinstall.  Furthermore, there is no .deb on the ubuntu packages website.

Xine claims that it cannot initialize drivers.  There is no sound anywhere on my system.  Yesterday, I did attempt to install the newest version of OSS through the OpenSound website.  Don't know if that would screw anything up in ALSA, though...

ASUS AN7 Motherboard (nForce2)
AMD 2200XP+
ATI Radeon 9600 Pro (256mb DDR)
Creative Sound Blaster Audigy2 EX
1024mb DDR

Any ideas?

---

