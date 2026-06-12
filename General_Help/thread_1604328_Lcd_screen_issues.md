---
title: "Lcd screen issues"
date: 2010-10-23
forum: General Help
---

### Post by antturley on 2010-10-23
Hi fellow linux users. This question isn't pertaining to linux. I didn't know where else to ask besides this place. I recently (15mins ago) a new lcd in my laptop. I installed everything with ease although when I power up my computer the screen is grey. I checked all the wires to the monitor and they seem secure. Any ideas? :confused:

---

### Post by efflandt on 2010-10-24
Was it a replacement laptop display, and if so what was wrong with the old one?  Maybe that did electrical damage that you were not aware of, or a plug is in backwards.

If it is an external display, Intel or ATI usually automatically switch to the external display at boot and X tries to bring both displays up in a resolution that it thinks both can handle (at least with default video).

But nVidia might stick to the internal display unless you specifically change that from System > Preferences > Monitors for default video or System > Administration > NVIDIA X Server Settings for proprietary video modules.  That can make it difficult to switch to an external display when a laptop screen is semi-broken or maybe impossible if the laptop screen does not work at all.  I had to do that on an old laptop where half the screen diagonally was blacked out and the other half was sluggish to refresh and pixelated.  I cannot see BIOS or grub, but at least X has been switched to external VGA.

---

