---
title: "upgrading Lucid to 2.6.35 kernel"
date: 2010-10-07
forum: General Help
---

### Post by Chris1274 on 2010-10-07
Hi everyone,

I'd like to install the 2.6.35 kernel while keeping Lucid (just not in the mood right now to get used to a new release). Can someone point me to a tutorial on how to go about this? Or maybe even provide such a tutorial, if it's not too much trouble? Thanks in advance.

Chris

---

### Post by anishman on 2010-10-07
**The following was what I used to install the latest kernel on Lucid.**

I did it to get the latest intel driver for my laptop.

***You can simply just install the kernel for your own needs:***  
[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

:)

---

### Post by Rob2687 on 2010-10-07
There's no need to use the xorg-edgers PPA just for the kernel in that repository. The backported Maverick kernel is available here. [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

---

### Post by Chris1274 on 2010-10-07
So, once I add that ppa to my sources, all I have to do is run an update and upgrade and that will install the new kernel?

---

