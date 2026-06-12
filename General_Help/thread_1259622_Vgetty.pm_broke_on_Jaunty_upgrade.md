---
title: "Vgetty.pm broke on Jaunty upgrade"
date: 2009-09-06
forum: General Help
---

### Post by bbell2000 on 2009-09-06
For several years, I've been using mgetty/vgetty with VOCP to serve as an answering machine for three modems.

It looks like the jaunty upgrade upgraded my Perl from 5.8 to 5.10 and Vgetty.pm is now broken.  VOCP accepts the voice message, but refuses to forward the message via email.  As best as I can tell, it's because Vgetty.pm is crashing with the following error:

        (in cleanup) Can't call method "print" on an undefined value at /usr/local/share/perl/5.10.0/Modem/Vgetty.pm line 95 during global destruction.

I found a few references to other people having the same issue, but no resolution.

Any ideas as to how I can correct the error?

---

