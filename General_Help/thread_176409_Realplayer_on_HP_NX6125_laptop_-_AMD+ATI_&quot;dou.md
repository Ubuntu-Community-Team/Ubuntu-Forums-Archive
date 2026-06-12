---
title: "Realplayer on HP NX6125 laptop - AMD+ATI &quot;double speed time&quot; acting up or what?"
date: 2006-05-14
forum: General Help
---

### Post by the0b0rm on 2006-05-14
Hi,

I have a HP NX6125 laptop, and can't seem to get realplayer to play clips properly.

The symptoms are as follows: Realplayer starts by buffering, then it plays ~ one second of video and audio properly, then audio starts dropping intermittently and video stalls (shows a still image, and then two seconds later another). **Occasionally** (say once a minute), video starts to run for one or two seconds, at (apparently) double speed. In the mean time realplayer frequently re-starts buffering again, claiming "congestion"

I'm pretty certain this is not (RealPlayer10Gold) software related, that the install was done properly, and I'm also certain that i'ts not DSL bandwith related; I get a stable 10 Mb/s downstream, and my humble Apple 600MHz PPC plays streams flawlessly.

My *hypothesis* is that it's related to a (documented) bug in the chipset (ATI) used in this laptop, which makes the system clock run about twice as fast, and the rest of the system *incredibly* slow, unless I boot the kernel with the "noapic" option.

I've tried various other (combinations) of kernel options (nolapic, acpi=off, noapictimer, disable_timer_input_1 etc... suggested in other forum threads, but to no avail.

Can someone confirm that the RealPlayer problem is indeed related to the "double speed time" issue?

Better still, does anyone have a suggestion of how to resolve this issue?

with kind regards,

Theo

---

### Post by the0b0rm on 2006-05-16
bump (shameless)

---

