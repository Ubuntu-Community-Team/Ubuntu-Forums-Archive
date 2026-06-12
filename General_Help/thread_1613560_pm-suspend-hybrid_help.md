---
title: "pm-suspend-hybrid help"
date: 2010-11-04
forum: General Help
---

### Post by doobiest on 2010-11-04
Hi, I need some help with pm-suspend-hybrid.

The man page seems to contradict itself.

1st:

pm-suspend-hybrid
Hybrid-suspend is the process where the system does everything it needs to hibernate, suspends instead of shutting down. This means that your computer can wake up quicker than for normal hibernation if you do not run out of power, and you can resume even if you run out of power. s2both(8) is an hybrid-suspend implementation. 

*Pay attention to the wording, that it does everything that it needs to hibernate, but suspends instead of shuts down. If the computer runs out of power, nothing is lost as it's also been saved to disk, not just in ram.

However, further in the man page theres a section about PM_HIBERNATE_DELAY. which describes this is the number of seconds before the computer wakes up from suspend, and then chooses to hibernate.




So my question is which one is it, when doing pm-suspend-hybrid, does it save to disk and to ram, then suspend. Or does it just suspend, and after a timer wake up and hibernate?

From my testing, it's the second one, It will suspend, wake up on its own, then hibernate.

However what I want is the first option, where it saves both to ram and disk, so in the even of total power loss I can still recover my systems state.


Does anyone know how to get this to work, because out of the box it doesn't appear to function as I expected.

Thanks,

---

### Post by professorYaffle on 2011-01-29
I was looking into this whilst upgrading to maverick.

I noticed the man page for pm-action mentions that "s2both(8) is an hybrid-suspend implementation." apt-file told me that s2both is in a package called "uswsusp"

I installed uswsusp and tried pm-suspend-hybrid again. It was definitely now trying to do what it said on the tin. It spent a while paging stuff to disk and then went to sleep. Unfortunately when resuming from sleep (I haven't actually tried powering it off yet) X crashes - despite the fact that pm-suspend works fine for me normally.

---

