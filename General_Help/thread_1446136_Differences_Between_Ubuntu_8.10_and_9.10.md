---
title: "Differences Between Ubuntu 8.10 and 9.10"
date: 2010-04-03
forum: General Help
---

### Post by AP0ll0UK on 2010-04-03
Evening All

Seen as my ATI driver doesn't support Ubuntu 9.10 and neither does LinuxMCE [my two biggest bug bears at the moment] I am considering downgrading to Ubuntu 8.10.

I just wondered if there were any major differences or if I am likely to see any major issues because of things that were fixed or added to 9.10 that weren't available in 8.10.

Many Thanks.

---

### Post by zvacet on 2010-04-04
Jaunty will get to the end of life on April.It means it will not be supported after that.Maybe you can find driver on Ati web site.

---

### Post by quadproc on 2010-04-04
> **AP0ll0UK said:**
> Evening All

Seen as my ATI driver doesn't support Ubuntu 9.10 and neither does LinuxMCE [my two biggest bug bears at the moment] I am considering downgrading to Ubuntu 8.10.

I just wondered if there were any major differences or if I am likely to see any major issues because of things that were fixed or added to 9.10 that weren't available in 8.10.

Many Thanks.
There is a really big difference between Ubuntu 8.10 and 9.04 (and later): X windows changed from version 1.5 to 1.6.  The change in X is huge and is completely incompatible with drivers which worked for version 1.5.  Unfortunately, you may be forced to either upgrade your graphics hardware or to stick with the version 8.10.

One of the problems with staying on an older release is that there won't be any support for it at some point.  Another set of problems is security related - older versions have a number of unfixed security problems.

Something else that I know of is that changing users does not work correctly on 8.10: the user change partially corrupts the display and makes it hard to tell what is happening.  There is still a problem related to this in 9.04 but I think that it has a chance of getting fixed at some point, perhaps in 10.something. Edit: change user works in 9.10.

quadproc

---

