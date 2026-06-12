---
title: "System crawls when using cd drive"
date: 2006-02-05
forum: General Help
---

### Post by gmcauley on 2006-02-05
I am seeing an unbearable slow down in my system when:

1) I copy file from a cd to my hardrive, and
2) when I am burning a cd

As soon as these operations are finished, everything is fine.

Any help would be greatly appreciated.

---

### Post by krusbjorn on 2006-02-05
Same here. It's because those actions eat your CPU for breakfast. Try K3b for burning if you havent already. It goes alot easier on my CPU than the other burning applications.

---

### Post by gmcauley on 2006-02-05
Thank you for your reply.

So you are saying this is *normal* behavior? Beacase when I say unbearable, I mean unbearable.  When I am copying/burning, my mouse pointer crawls so slowly that I can barely control the mouse.  Moving windows around is similar.  While the operations are going on, I can not really do anything else.

I have a AMD64 3800+ cpu, and am using K3b - so I was thinking that maybe I need to somehow configure the cd drive differently??

---

### Post by krusbjorn on 2006-02-05
Nah, I'm just saying that I havent bothered to search for how to make it stop ;). It could have something to do with not having DMA enable for your CD drive, but I'm not sure. I'm sure someone else who reads this will what is wrong and how to fix it.

---

### Post by GeneralZod on 2006-02-06
[QUOTE=krusbjorn]Nah, I'm just saying that I havent bothered to search for how to make it stop ;). It could have something to do with not having DMA enable for your CD drive, but I'm not sure. I'm sure someone else who reads this will what is wrong and how to fix it.[/QUOTE]

Yep; it's almost certainly dma related.  Read this, and pay special attention to the fact that the drive letter of your drive may differ from that given in the example (in this example, the drive is /dev/hd*c*) :

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

