---
title: "LTSP display modules"
date: 2010-09-12
forum: General Help
---

### Post by diablo2nd on 2010-09-12
Hi.
So i have a server successfully running LTSP and clients successfully using it. However, in the beginning i had an issue with flipped text/screen and managed to find an answer to that. the answer was to not use proprietary drivers. This is not really a solution though, as now my big powerfull server doesn't do anything cool. like Compiz, or games.

So the Nvidia driver was accidentally enabled again, and clients are still fine...

What i would like to do now is set up a display module for the clients to use. My clients are hp t5700 and as best as i can tell they use ATI chipset. 

So far i have chrooted into the environment and installed fgrlx and then in lts.conf set XServer=ati, and tried xserver=fglrx the client either dosnt boot or dosnt change from standard.

I just need to set a higher resoultion on the client, and have the nvidia drivers on the server

---

