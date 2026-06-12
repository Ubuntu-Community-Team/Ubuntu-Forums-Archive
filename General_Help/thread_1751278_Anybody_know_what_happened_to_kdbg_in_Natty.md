---
title: "Anybody know what happened to kdbg in Natty?"
date: 2011-05-06
forum: General Help
---

### Post by Tricity on 2011-05-06
Hey everybody,

I just installed 11.04 and found that the debugger gui, kdbg, is no longer in the repositories. I have all repos enabled except backports. I also tried to find any information about the fate of kdbg, whether it is just not yet packaged for 11.04, or whether it is discontinued, but to no avail.

Does anybody know about kdbg's fate? :confused:

If it is being discontinued, I'll probably roll my own .deb package and post it somewhere - kdbg is too good to drop, I think.

And while we are at it, does anybody know what happened to Piklab?

Thanks - any hint appreciated.

---

### Post by burito on 2011-05-08
According to Launchpad kdbg is "deleted". No further info.

I would certainly like a proper answer, as this as ended my ability to use Ubuntu for software development.

---

### Post by burito on 2011-05-08
Thanks to tensorpudding in the IRC channel, I have found out this...

It seems Qt3 is verboten in 11.04, which KDbg not being the most actively developed program hadn't migrated to by the time the feature freeze kicked in. KDbg has since switched to Qt4, and there are builds available for Oneiric, as well as backports for Natty.

[https://launchpad.net/~yofel/+archive/backports/+build/2491855](https://launchpad.net/~yofel/+archive/backports/+build/2491855)

---

### Post by RootsLINUX on 2011-05-11
I was also disappointed to find kdbg nowhere to be found in Natty. I hope it gets added back because its the only debugger in Linux I have actually enjoyed using. (I tried to love you ddd, I really did).

---

### Post by oldos2er on 2011-05-11
kdbg is available in the backports PPA [https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

---

### Post by RootsLINUX on 2011-05-12
> **oldos2er said:**
> kdbg is available in the backports PPA [https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

Thanks! Got it installed now. :D

---

