---
title: "Ubuntu keeps hanging"
date: 2012-06-13
forum: General Help
---

### Post by digitig on 2012-06-13
I've done a new clean install of Ubuntu 12.04, and I'm finding that it works fine to begin with but after a while slows down to an unusable crawl (minutes to respond to a mouse move). This happens within about 20 minutes at worst, a couple of hours at best. I've not been able to link the slow-down to any specific program, and I've tried starting in Gnome Classic (no effects) to rule out possible Unity video driver issues. Somebody on /, suggested I try killing udevd: it's hard to tell if that has helped, but it certainly hasn't fixed it. Can anybody suggest what I might try next? I'm effectively a Linux newbie, by the way, because although I've been trying Linux for decades I've never managed to get a satisfactory installation so I've never really learned how to drive it properly.

---

### Post by digitig on 2012-06-14
Ok, somebody elsewhere pointed me to System Monitor (did I mention I was a newbie) and I discovered that the swap file was growing until it maxed out. I increased the swap size (a *lot*), and now it levels out well clear of the top. The system seems to be stable now.

---

### Post by gnorb on 2012-06-14
Been looking on swap size lately. Can you advice the size of RAM and swap you have or just paste in the result of when you run the command free in the terminal?

---

### Post by naknak987 on 2012-06-14
I've always used 1 gig for my swap size. Never had any problems. My system also have 300mb of ram.

---

