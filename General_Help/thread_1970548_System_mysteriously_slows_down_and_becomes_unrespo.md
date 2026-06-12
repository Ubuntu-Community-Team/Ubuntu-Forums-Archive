---
title: "System mysteriously slows down and becomes unresponsive"
date: 2012-05-01
forum: General Help
---

### Post by hypersoar on 2012-05-01
Very often, my system will slow down. The mouse becomes very sluggish, video playback is choppy if it's in full screen or if I move the mouse, and everything is generally unresponsive. Sometimes things become almost unusably slow.

I notice no pattern for when this happens. There are no particular applications running, and it can happen right after boot or some time after. Once it starts, it may go away after some indeterminate period of time. CPU usage does not change when it happens. This has been a problem for the last three releases, including Precise, and it persisted after a clean wipe/reinstall (it wasn't always a problem on this laptop). It has not been a problem at all in Windows. I'm running a Dell Studio 1555 with integrated graphics (Intel GMA 4500, I think). I usually use a bluetooth mouse, but the slowdown happens with or without it.

So, I'm completely stumped. I'd really appreciate some help isolating the cause.

---

### Post by 2F4U on 2012-05-01
Is the machine getting hot? The CPU may scale down due to the danger of overheating.

---

### Post by hypersoar on 2012-05-01
No, it isn't getting hot. With the way this comes and goes, I don't think it's an overheating issue. 

However, I did just remember/notice again that kworker appears to be working unsually hard, with two processes up at ~6% CPU usage each.

Edit: Yeah, those kworker processes correlate perfectly with the slowdown.

---

