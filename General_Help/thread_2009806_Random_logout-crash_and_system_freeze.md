---
title: "Random logout-crash and system freeze"
date: 2012-06-24
forum: General Help
---

### Post by ricardisimo on 2012-06-24
I had posted elsewhere about this, and it was suggested that I should start a new thread. The long and the short of it is that I will randomly get logged out of my account (more common) or the entire system will freeze up (less common) including - sometimes yes, sometimes no - the mouse pointer. Might be two (or three) separate issues, I know.

I'd like to know how to trace the problem. The only constant thus far has been network activity; I've always been opening a web page, or my son is playing an online game, or at a bare minimum in the middle of a download. Most often it seems to be while a webpage is loading. Is this even possible, or is it just my imagination?

---

### Post by ricardisimo on 2012-07-03
Subscribed to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/594408"). But I would still appreciate any help I can get from folks here. Where can I find useful reports as to what the hell just happened immediately after a crash? Thanks.

---

### Post by snowygrouch on 2012-07-07
Yes this is completely unbeliavable,

Supermicro x7dw-n MB
Nvidia Quadro FX3700    (tried several drivers)
OCZ SSD
XEON QUAD X5420s

For me it happens usually when watching web browser videos online, but
has also occured doing completely unrelated stuff. BAM....back to login screen
all work lost. 

Been through all the suggested solutions on forums.

Best suggestion I had so far was to get a subscription to Canonical for 100 euros....wow
great. So I saved some money by using Linux, now I have wasted about 25hours of time and its suggested that I buy a support package. Brilliant....

I installed Linux in order to use opensource engineering programs like OpenFOAM, how exactly am I supposed to use an operating system
that crashes sometimes several times within the space of 30minuites ?

---

### Post by ricardisimo on 2012-07-10
Well, in all fairness, this is quite new for me, and I've been on Ubuntu for almost a decade. Normally my system has been the model of stability. Still, the lack of responses here or in Launchpad is disconcerting, to say the least.

---

### Post by tlfcbb on 2012-08-04
I am also having this problem.  Does anyone have any idea if it has been solved yet.  So frustrating.

---

### Post by tlfcbb on 2012-08-07
Bump.  This problem has been reported on several forums so there must be a lot of people having it.  Does anyone have a solution.  Should I go back to 11.10?  Should I reinstall 12.04 (would this do any good)?  At the moment my computer is useless to work on as it randomly logs me out and my work is lost.  I would also say that I cannot watch a full video on you tube through any browser, firefox, chrome or opera.  I have a NIVIDIA card with the recommended driver installed.  Please, any help would be very much appreciated.

---

### Post by ricardisimo on 2012-08-09
So far the only things close to solutions that have come up in the bug reports and subsequent conversation are:
[LIST]
[*]Running Kubuntu desktop instead of any Unity or Gnome variant;
[*]uninstalling the proprietary nvidia driver, running nouveau instead;
[*]downgrading to 11.10;
[*]Going out and buying an ATI graphics card and being done with it once and for all.
[/LIST]
Many of these are not options for me, so I'm just trying to wait it out, and thanking my lucky stars that the computer I use for my livelihood is already ATI, not nVidia.

---

### Post by tlfcbb on 2012-08-09
Thanks for that Ricardisimo.  I tried removing the drivers but this led to so many other problems, computer frezzing, blank screen etc that I had to reinstall the drivers.  The other options are not suitable for me.

I have logged into unity 2D and so far have had no problems so hopefully this is the answer.  It is not an ideal solution as it means you loose all the functions of 3D but I would rather have a fully functioning computer running 2D.

Lets hope they can get this problem sorted out soon.

---

### Post by richardhwinter on 2012-09-24
I had a similar issue after upgrading to 12.04: After closing the lid the system was frozen with only the option of a hard shutdown via power button.
I went back to first Nividia driver in the list (173) and this worked for me. But the performace is dissatisfiying (slow refresh of the screen).

I came here to ask for a better solution but it looks like there is none so far.

---

### Post by shreepads on 2012-09-24
> **ricardisimo said:**
> So far the only things close to solutions that have come up in the bug reports and subsequent conversation are:
[LIST]
[*]Running Kubuntu desktop instead of any Unity or Gnome variant;
[*]uninstalling the proprietary nvidia driver, running nouveau instead;
[*]downgrading to 11.10;
[*]Going out and buying an ATI graphics card and being done with it once and for all.
[/LIST]
Many of these are not options for me, so I'm just trying to wait it out, and thanking my lucky stars that the computer I use for my livelihood is already ATI, not nVidia.

Have you tried
- Latest proprietary NVidia driver (304.xx series)
- Calculating your system power usage vs rated power capacity of the PSU in the system

---

### Post by richardhwinter on 2012-10-03
Just for the record:
In my case (lenovo R61, Ubuntu 12.04) going back to the nouveau driver was the best solution: No more crashes, reasonable performance.

---

### Post by Ron on 2012-10-06
I am not a ubuntu user, but for any funny-business with linux behaving badly, a good thing to try is adding "noapic" to the kernel boot parameters in grub.

---

