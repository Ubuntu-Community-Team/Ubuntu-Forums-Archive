---
title: "Kmix will only show my mic channels"
date: 2010-04-30
forum: General Help
---

### Post by 16777216 on 2010-04-30
Kmix will not show any audio channels except the front mic and front mic boost.

When trying to add the other channels back nothing is shown in the channel setup dialog.

ALSA mixer works fine in this regard.

Also, I can't set my sound hardware to anything other than 6 or 8 channel audio though I only have stereo speakers and this is true no matter which mixer is used.

Lucid, Kernel 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686

Driver: 3.8.1a-980706 (ALSA v 1.0.22.1 emulation code)

Hardware info: HDA NVidia at 0xfe020000 irq 20

Audio devices: Realtek ALC1200 Analog (DUPLEX)

I guess no one knows anything about this one.

---

### Post by janaka on 2012-08-14
Install "Gnome ALSA mixer".  Then open it up and make sure audio device you expect the sound to come out of is un-muted.  While ago there was an issue where volumes below 50% didn't work either; so if you encounter this, just increase the volume above 50%.
From my experience, Kmix issues are usually caused for Intel sound chipsets.  I have this with my 12.04.

---

