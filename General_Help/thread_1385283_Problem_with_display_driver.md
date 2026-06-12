---
title: "Problem with display driver"
date: 2010-01-19
forum: General Help
---

### Post by aryan4444 on 2010-01-19
i have nvidia graphics card 256 mb.
installed its software by going to SYSTEM->ADMINISTRATION->HARDWARE DRIVERS

since then display is not working after booting up..
but i can get to the recovery console.. tty.

how can i restore my graphics.
and why is the nvidia graphic driver not working??
pls help.

---

### Post by JiuJitsu500 on 2010-01-19
One odd thing I found on three computers, all three with ATI cards was that the driver (perhaps something else?) couldn't recognize a full 4GB of RAM, and had to be boot in safe graphics mode every time. Once, after not having any trouble on any Nvidia cards untiol this point, I tried the same thing after not getting into normal graphics mode... I removed 2GB of RAM and it worked like a charm.

But, I don't know how much RAM you have, this is only what worked for me on 4 laptops (don't tell the owners ;) ). I found it in the launchpad bug site and tried it and they all are very happy. The bug I guess won't read above 2GB of RAM on a small group of cards, and the drivers will only work with that or less. I haven't found a workaround yet, but I am still looking.

---

