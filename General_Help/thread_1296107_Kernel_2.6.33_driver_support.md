---
title: "Kernel 2.6.33 driver support"
date: 2009-10-20
forum: General Help
---

### Post by spinoza666 on 2009-10-20
Hi,

with Karmic we will be moving to kernel 2.6.31. I'm considering buying a soundcard which support is included in 2.6.33. Does anyone have any inkling how long I would have to wait until Ubuntu moves to 2.6.33?

-Atle

---

### Post by P4man on 2009-10-20
I could be wrong but isnt karmic gonna stay on 2.6.31xx ?
There might be backprts, but I guess you'll have to wait for 10.04 for proper support. What sound card could you possibly want that you'd consider buying one knowing its not supported now and only hoping it will be properly supported at some point?

---

### Post by sgosnell on 2009-10-20
You can get the latest kernels [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  You can just download the kernel and install it with gdebi.  You don't have to wait for an upgrade for your distro, the kernel is independent, and easily installed or removed.

---

### Post by Claus7 on 2009-10-20
Hello,

correct me if I'm wrong, yet I think that the update of the kernels in a stable release is slower than those of the alpha and beta versions. 

I also think that 10.04 should be a good bet for the kernel in question.

Could I ask if the installation of the new kernel works decently even if it is not officially supported? Has anyone checked how stable these are with ubuntu?

Regards!

---

### Post by sgosnell on 2009-10-20
They're on the Ubuntu kernel site.  They may not work well on certain hardware with certain versions of Ubuntu installed, though.  I'm currently running the .30 kernel on Jaunty, but the .31 kernel won't boot.  There is a .32 release candidate there, but I haven't tried it on my laptop yet.  It's not hard to install a kernel and leave the other one(s) intact, and if your computer has problems with the new one, just boot from the old one and then uninstall the one you have problems with.  I never remove a working kernel until I'm absolutely positive I don't need it any longer.  I still have the .28 kernel on my machine, although I haven't booted it in months, just in case.

---

### Post by spinoza666 on 2009-10-20
Well to answer the first question, I'm planning to get the Asus Xonar Essence. The pci-express version will be included in 2.6.30, while the pci version will be included in 2.6.33. My one and only pci-express port is occupied.

I'm into Hi-fi and this seems to be a very good card, so that's basically why. In addition I prefer to use only hardware which is supported in the kernel, so that's why I'm considering waiting.

But if I have to wait for too long I might as well look for another card, or install the newest kernel or alsa package. The newest alsa version seems the most reasonable option of the latter two, but then again, running the newest kernel might be interesting as well. Maybe too interesting:)

Maybe any of you have any advice to what could be a good replacement for the Asus card? Something that's got excellent sound quality, but is well supported in Ubuntu now?

---

### Post by P4man on 2009-10-20
Is there really an audible difference between various "decent" cards? I wonder... sure some may have features you may want (sound processing, perhaps Dolby trueHD for blu-rays that you cant play on ubuntu anyway ;p), but when playing back music -even through a highend amplifier and speaker, Im curious if anyone could tell my age old Audigy1 from any other new uber card. Im willing to bet no one can.

Maybe you have a genuine use for highend audio cards features, but Im willing to bet most ppl buy them like they buy monster cables. Unless you got a *really* good amp and speaker set, I bet even onboard audio would be indistinguishable.

---

### Post by spinoza666 on 2009-10-21
Well I absolutley agree that quite a few audiophiles take it too far, and hear differences when they are inaudible to the human ear, but still there is something to be said for getting quality equipment if you value sound quality. I do not spend excessive amounts, but rather try to find a good balance between cost and differences in sound quality that you can actually detect.

When it comes to soundcards for hifi use, there are differences among them. Nevertheless, playing music from your pc is not the best option, as you will get somewhat reduced sound quality regardless of what card you use, compared to a cd player that is. There are a lot of reasons for this, most of it has to do with static interference from the cpu and other components. Other issues are the quality of the DAC, or what type of connectors are available. I can definitely hear the difference between music coming from my computer, and music from my cd player, but then again, I listen intently.

I guess this conversation has drifted away from its origin, but thanks for your replies, they have bee most helpful.

Cheers

---

