---
title: "Multimonitor support with catalyst/fglrx? Still as crappy as back then?"
date: 2012-03-18
forum: General Help
---

### Post by wecali on 2012-03-18
Hi,

i'm thinking about buying a new pc. I'd like to build up a multimonitor system with four and more 19" TFTs attached. I am currently considering to build this pc with cheap AMD graphic cards. (2x PCIe 16x).
 
The question is, can someone tell me from experience how well the multimonitor support with AMD graphic cards currently works on ubuntu?

I remember a time when nearly everyone strongly discouraged the use of ATI graphic cards for linux systems because of the extraordinarily bad driver support for those cards. 

Has the situation changed for ubuntu in 2012? 

Best regards,

Wecali

---

### Post by BlueHorseDemon on 2012-03-18
Well I'm running two monitors on a HD5770 and its a pretty tragic experience.  Catalyst control center won't save any settings at all unless you open it from the terminal, and even then weird things happen when you reboot (the settings have to be reapplied generally).  There is no way to set your primary monitor without using xrandr, but due to the aforementioned issues with the dual monitor settings being wrecked on startup, running a xrandr script at startup doesnt seem to actually do anything.

It's bad.

---

