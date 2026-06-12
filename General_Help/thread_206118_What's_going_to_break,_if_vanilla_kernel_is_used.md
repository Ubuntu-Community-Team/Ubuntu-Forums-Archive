---
title: "What's going to break, if vanilla kernel is used?"
date: 2006-06-29
forum: General Help
---

### Post by A.Skwar on 2006-06-29
Hello!

As suspend/resume doesn't work with the kernel shipped with Dapper, I'd like to try using the suspend2 kernel patch from [http://suspend2.net/](http://suspend2.net/). But the patch cannot be applied cleanly against the Ubuntu sources.

Because of that, I'd like to use a vanilla kernel. But the Ubuntu patches are there for a reason, I'd suppose. Is this reason documented somewhere? Or, put differently, what do the Ubuntu patches add to the vanilla kernel and what's not going to work anymore after using a vanilla kernel?

Thanks,

Alexander

---

### Post by thasheep on 2006-06-29
The ubuntu patches seem to fall mostly into two categories. Firstly, they tweak performance so that the computer reacts faster to user interaction (but I don't think this is the case with the server kernels). Secondly, a lot of patches are applied to support hardware that wasn't supported by the 2.6.15 vanilla kernel. Most of these patches are backported from more recent kernels.

Currently, I'm running linux 2.6.17 with con kolivas's (mostly performance) patches and the only difference I've noticed is that my computer runs faster. These are the basis for most distros' performance tweaks. See [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

---

