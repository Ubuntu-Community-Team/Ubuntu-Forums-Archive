---
title: "Firefox keeps freezing"
date: 2010-05-01
forum: General Help
---

### Post by bigpilot on 2010-05-01
I've just upgraded to Kubuntu 10.04 and I've noticed that the new FireFox 3.6.3 keeps freezing up, using 100% CPU and lots of disk activity for seconds at a time for apparently no reason at all. The OS itself doesn't freeze up, it's Firefox only, but it's still annoying since I surf the web a lot. I see a lot of maxing out of my dual-core CPU's with System Monitor and I don't like it. 

Is anyone else having these problems?

Note that I kept all my original scripts during updating when the installer asked me to choose.

---

### Post by bigpilot on 2010-05-01
Doing some research myself I figured out that Firefox is not the problem, but a Desktop Search program called 'Virtuoso'.

I switched it off by going to System Settings -> Advanced -> Desktop Search and then unchecking the 'Enable Nepomuk Semantic Desktop' checkbox and pressing 'Apply'.

CPU is now down to a couple percent and no more disk thrashing.

---

### Post by duncanmc on 2010-05-18
Thank you very much. My firefox was stalling and freezing. Disabling virtuoso fixed the problem.

---

