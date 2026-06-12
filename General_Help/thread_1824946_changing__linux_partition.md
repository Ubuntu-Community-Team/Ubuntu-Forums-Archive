---
title: "changing  linux partition"
date: 2011-08-14
forum: General Help
---

### Post by harryliddic on 2011-08-14
My business requires a dual boot and I'm running out of space on the Wxp drive(500K). I want to put a Wxp partition on my linux drive. 30gb or so. I can't afford to lose files from either operating system. I tried Gparted no luck. Is there a way?

---

### Post by YesWeCan on 2011-08-14
What exactly isn't working?

You have a linux drive and you want to make 30GB of space on it to install a fresh WXP to?

So, you cannot change the size of a partition if you are also using that partition at the same time. Normally, you would boot from a live CD/USB and run GParted from there.

---

### Post by harryliddic on 2011-08-14
when I run Gparted it boots up in linux and for a while the partitons stands as I want them then it goes back to all linux

---

### Post by sanderd17 on 2011-08-14
Everything you want with partitions is possible with Gparted, but in most cases you need to run it from a live CD/USB (because you can't edit partitions that are in use).

We do need some more info about your current partition schema and what you want to achieve.

EDIT: just read your post. Did you hit the green V buton, the "apply" button?

---

### Post by YesWeCan on 2011-08-14
I found this guide quite good: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by SidebySide on 2011-08-15
> **harryliddic said:**
> tried Gparted no luck. Is there a way?
Use gparted on a live boot from your linux disk, again...

---

