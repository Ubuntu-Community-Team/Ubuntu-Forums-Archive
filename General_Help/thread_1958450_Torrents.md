---
title: "Torrents"
date: 2012-04-14
forum: General Help
---

### Post by Exyl on 2012-04-14
Hey people, I've got a little problem, hope you can help me out on this. 
I'm in college and torrents are blocked here (IT IS NOT THAT 'HOW TO MAKE TORRENTS WORK' QUESTION, so please read on.), but there is some stuff that is only available on torrents and i prefer using torrents because it is almost impossible to download bigger files cuz the download interrupts due to disconnection. So I use VPN service for torrents. 
Torrents worked fine until a month ago or so but lately I'm getting very low speeds but at the same time resources tab shows massive incoming speeds, so what i'm asking for is, certainly not how to get massive speeds but where is this data going? Could it be some stuff that is being stored on my computer without my knowledge? I'm using Transmission and have tried Deluge, both are reporting the same.



[center][IMG]http://www3.picturepush.com/photo/a/8030916/640/8030916.png[/IMG][/center]




Transmission shows download speed 67 and System monitor shows 236, no other applications were running.

---

### Post by 0011235813 on 2012-04-14
Oh please, even with no applications running, there could still be several processes using the Internet. The 140 odd KB is very little in terms of data and could easily just be down to error on the system monitor or whatnot. The slow download speeds could be down to a slow connection, a slow VPN, or a bunch of other factors. The up-loader's connection might be slow, who knows? Torrents are unpredictable and unreliable, not to mention a privacy nightmare. 

Really, you're better of finding some download manager in the repositories and using that instead of torrents.

PS: Is your processor the 8150 Bulldozer, or some hyperthreaded I7?

---

### Post by Exyl on 2012-04-14
> **0011235813 said:**
> Oh please, even with no applications running, there could still be several processes using the Internet. The 140 odd KB is very little in terms of data and could easily just be down to error on the system monitor or whatnot. The slow download speeds could be down to a slow connection, a slow VPN, or a bunch of other factors. The up-loader's connection might be slow, who knows? Torrents are unpredictable and unreliable, not to mention a privacy nightmare. 

Really, you're better of finding some download manager in the repositories and using that instead of torrents.

PS: Is your processor the 8150 Bulldozer, or some hyperthreaded I7?


I'm pretty sure that no other applications are utilizing the internet, i've noticed this large gap is only when running torrents.

You mentioned that hyperthreaded i7 might have something to do with this, that might be the case, i have an i7, but still could you please give me an idea about what hyperthreading has to do with this?

And thanks for replying.

---

### Post by 0011235813 on 2012-04-14
> **Exyl said:**
> I'm pretty sure that no other applications are utilizing the internet, i've noticed this large gap is only when running torrents.

You mentioned that hyperthreaded i7 might have something to do with this, that might be the case, i have an i7, but still could you please give me an idea about what hyperthreading has to do with this?

And thanks for replying.

OK well that could still mean errors, it doesn't matter anyway since the 140KB is very little and shouldn't affect download speeds by that much. I would suggest you use a program like multiget in the repos instead of torrents and see how that compares.

And the last bit was just my curiosity, no hyperthreading has nothing to do this, I was just wondering whether you bought the AMD octacore or whether the system was incorrectly identifying the hyperthreaded quad core as being eight cores. Technically speaking, hyperthreading would result in the system having access to eight (logical) cores, but since the cores aren't "real" merely virtual, I find it quite misleading. You can look up on [hyperthreading]("https://en.wikipedia.org/wiki/Hyper-threading"). To put it short, hyperthreading improves the performance of lightly threaded apps like web browsers by reducing pipelining strains.

---

### Post by JRV on 2012-04-14
Run top while running transmission to see if you have any background tasks that are slowing it down.  
```
top
```

---

