---
title: "Ubuntu crashes: where to start looking?"
date: 2011-03-16
forum: General Help
---

### Post by efolia on 2011-03-16
[LEFT]A few days ago I installed Maverick (10.10) on a build using an EVGA 730a MB running on an AMD Athlon II X3 450. It runs on twin displays using the NVidea driver and the MB's video card. I am not that familiar with Linux (though i've been working with and on computers for the last two decades). It took me two days to figure out that I could not use my KVM switch's USB because it was preventing the CPU from using all but the first core. So now that the machine is by itself and using its 3 cores, it keeps crashing randomly: The displays turn into some random colors (different for both) and the machine has to be resetted via hardware. The crashes seem totally random, as they can occur anywhere from within 30 seconds of boot to hours into a session, so I suspect it is due to some hardware/driver problem. It also crashes whether I do something or not: it seems totally random. It never crashed when it was using only one core. I looked through the logs and could not find where the crash occurs: it does not seem to leave any message behind, so I'm at lost as to what the source of this problem could be. So the question is: which log file should I look into? Or maybe any idea what I should be looking for?
[/LEFT]
 
Thanks

---

### Post by efolia on 2011-03-17
If that helps someone, disabling the CPU Cool and Quiet feature in the BIOS did the trick. It could be that the MB manufacturer's bios didn't quite support AMD's CnQ feature correctly, or even some OS incompatibility with this particular processor. Either way it worked.

---

