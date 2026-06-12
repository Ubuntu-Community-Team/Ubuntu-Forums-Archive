---
title: "cant load x, loops over and over?"
date: 2010-02-04
forum: General Help
---

### Post by ulao on 2010-02-04
I just did an install and after loading X is close and start X again, in a loop?

So I dropped to another session and looked at xorg.conf, its set up for what looks like auto detection. ( Identifier "Default Screen"  Monitor "Configured Monitor"  )I tried to put in the refresh rate but do to the fact its not set up right X failed to load. I put the xorg.conf back and rebooted, not X tried to load then exists with
saw signal 11. Server aborting
ddxSigGiveUp: Closing log
ddxSigGiveUp: re-raising 11
connection to X server lost

I get this just after the desktop loads completely 

Tried sudo dpkg-reconfigure xserver-xorg but  I get no installed. I may try to install it?
any ideas?

---

