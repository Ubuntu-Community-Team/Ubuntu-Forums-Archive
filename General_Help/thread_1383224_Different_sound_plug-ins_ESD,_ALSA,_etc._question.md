---
title: "Different sound plug-ins ESD, ALSA, etc. question"
date: 2010-01-17
forum: General Help
---

### Post by BeingLostMayVary on 2010-01-17
Ok I was wondering is there a way to allow certain programs to use certain sound plug-ins? I have firefox which uses the ALSA, but I&#12288;have another program KeyHoleTV  that uses ALSA as well. The catch is that KeyHoleTV won't work while firefox is running. So is there a way to which I&#12288;can get a ESD plugin for KeyHoleTV and use ALSA for firefox? Thanks for any help.

---

### Post by BeingLostMayVary on 2010-01-17
What if I downloaded gsstreamer0.10esd from Synaptic? Would that possibly make it work?

---

### Post by lidex on 2010-01-17
Your pulse audio server may need some tweaking. You should be able to get multiple streams with it unless the program you refer to just won't work with it. Either way this should help:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")

---

