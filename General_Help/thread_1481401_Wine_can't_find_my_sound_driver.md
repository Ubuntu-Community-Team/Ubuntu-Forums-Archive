---
title: "Wine can't find my sound driver"
date: 2010-05-12
forum: General Help
---

### Post by Ishayu on 2010-05-12
So... I'm pretty new to Linux as you can see by my postcount, and I have a problem and I don't know where to take it honestly.

I installed Wine 1.1.44. Everthing was nice and dandy. However, after a few days the sound just stopped working in Wine. :(

As of this posting I am listening to music on Youtube and I just played World of Goo (Humble Indie Bundle <3) and it had sound working just fine.

However, Wine cannot find any devices at all. ALSA is completely empty, OSS has a bunch of empty AUX devices. JACK has empyt input and output devices, and NAS has a single empty wave out device.
Testing sound returns an error: "Audio test failed!"
The sound preferences dialog tells me I have an Internal Audio Analog Stereo Duplex card... which tells me just about nothing really.

Could a nice soul help me through the debugging process of this one and eventually, hopefully, find a fix?

Thanks! :)

---

### Post by Ishayu on 2010-05-12
It works now.

Apparently the new Linux kernel broke Wine+PulseAudio, so I switched back to the old one.

Last time I tried Linux, which was 3 years ago, a similar thing happened and at that time I didn't even know about kernels and stuff like that so I just gave up. Not this time though. :P
They broke all existing NVIDIA driver installers, you see.

Can someone tell those kernel maintainers to stop completely breaking everything? (Or, optionally, could Canonical stop updating the kernel 3 days after they release a new version? It's really quite dumb, to be honest. Well, both problems are)

/complain

---

