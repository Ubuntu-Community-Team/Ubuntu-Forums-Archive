---
title: "another sound issue - only a &quot;pop&quot; from speakers/headphones"
date: 2010-11-17
forum: General Help
---

### Post by miguelastico on 2010-11-17
Hi everybody. I am almost ashamed to write another post on sound problems, but I don't know where else to turn.
I am using ubuntu server 64 bit, fresh installation, and the sound doesn't work.
This is my second installation, I had to re-install after some problems with grub (I have another post about that) and before that the sound worked flawlessly.

I basically tried every solution I found on line, so writing here is my last resort.

Basically the sound doesn't work, it just gives me a "pop" in the headphones from time to time, and when I mute/unmute the volume.
I read that this could be caused by the energy saving preferences of the audio card, and there was a solution that didn't work.
Strange thing, if I turn on the microphone (that I don't have) I hear static in the headphone, and if I look at "pavucontrol" while playing a sound file, I see the sound meter going up and down as if the sound was played.

I really tried everything, and what puzzles me is that everything seems to be ok, aplay -l shows my card, alsamixer too, and so on.
I really don't know what to try else.

---

### Post by miguelastico on 2011-02-10
I have an update just in case someone had the same problem.
After some reinstall, manipulations, I could manage to get back the sound, by accident though.
After a couple of months, by ANOTHER accident I deleted some GRUB configuration files. As a result the system didn't boot, so I followed a how to for re-installing grub with a live cd.
When I rebooted I was without audio again.
At this point I think GRUB is somewhat linked with the problem.
How can I know what in GRUB is causing my audio system not to work?

---

