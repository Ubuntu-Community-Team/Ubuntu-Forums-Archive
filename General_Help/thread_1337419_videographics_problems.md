---
title: "video/graphics problems?"
date: 2009-11-25
forum: General Help
---

### Post by MichaelBurns on 2009-11-25
I think that there might be a problem with the video "card", more specifically xubuntu's control of it.  That is a very unqualified guess, based on several problems that I have now experienced on this computer in the last week that all have one thing in common:  I lose the display just before the login screen, and the occurance is always associated with the monitor making a clicking noise.  Sometimes the screen just goes blank.  Sometimes either part or all of the display gets jumbled with pixels of random colors (but in some kind of a pattern).

I don't know how to read the output of lshw well, but I'm guessing that the video card is integrated into the mobo.

Any suggestions?  The computer is pretty outdated (several years old, but I don't know exactly).  Do I need to fix/replace the video driver (e.g. because it is incompatible with my video hardware)?  Preferably I'm looking for a solution that doesn't require any new hardware, because that might compel the computer owner to simply buy a new computer, but then it would have MS Windows, and I will have failed in this arduous week-long role as wannabe computer admin migrating several people to xubuntu.  There is one exception:  I might get away with suggesting a new monitor; this one is a CRT dinosaur, and the phosphor is even burnt.

---

### Post by cariboo on 2009-11-25
What graphics adapter does your computer have, as that would go a long way in helping you solve the problem.

From your description, it sounds like the horizontal sync and vertical refresh rates aren't set properly.

---

### Post by MichaelBurns on 2009-12-02
Cariboo, thanks for your reply, and sorry that I haven't gotten back to you.  I haven't had access to that computer since I read your post, so I don't know how to answer you question.

Regarding the horizontal sync and vertical refresh, I don't understand why you think that might be the problem, primarily because the problem is intermittant, and secondarily because the jumbled pixels don't move.  (I'm drawing here on my naive understanding of how a CRT works.)  Maybe you can explain it to me?

BTW, my mom obtained (temporary) possession of an hd tv soon after I started this thread, and I hooked up the computer to it through the VGA input.  I experienced the same problem; however, and this could just be my imagination, it may be less frequent now.  I don't know if this information is helpful.

---

### Post by MichaelBurns on 2009-12-25
> **cariboo907 said:**
> What graphics adapter does your computer have, ...How do I find out?

from lshw output:
```

        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0

```

---

