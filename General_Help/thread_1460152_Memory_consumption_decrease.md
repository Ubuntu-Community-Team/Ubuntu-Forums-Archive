---
title: "Memory consumption decrease"
date: 2010-04-22
forum: General Help
---

### Post by isra.navarro on 2010-04-22
Hi, i just recently installed Ubuntu 10.04 beta 2 on my laptop computer, i noticed that my memory comsumption after a fresh boot was around 250mb and noticed, if i hibernate the computer > shutdown and fresh boot my memory usage dropped down as 90 mb staying on around 133mb , but if i only reboot or shutdown without passing thru hibernate first the memory usage keeps increasing without any apps open just gui. in both cases the swap usage is 0mb

---

### Post by thomasaaron on 2010-04-22
It could be a memory leak in Lucid that hasn't been fixed yet. xorg and pulseaudio have traditionally been the most problematic in this regard.

If you go to a terminal and run...
```

top
```

...it will show you what is consuming your memory. Also, try letting it sit for a while to see if the memory usage continues to grow. If it doesn't, it's probably not a leak.

---

