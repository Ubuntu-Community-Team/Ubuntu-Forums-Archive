---
title: "Question about color depth"
date: 2012-05-11
forum: General Help
---

### Post by flyingfisch on 2012-05-11
I don't know if this is the right place to post, but I hope so! :D

I understand that I can get some of my 3D games to run faster if I change the color depth from 24-bit to 16-bit.

My question is, do I have to edit my xorg settings before and after I play the game every time? Or can I make some kind of file that does it auto-magically? Or should I just always use 16-bit and not go back to 24-bit?

I feel like I am bombarding the potential answerer with questions :D

Anyway, thanks in advance and if this thread should be somewhere else, please move it for me :)

---

### Post by CatKiller on 2012-05-11
Crikey, that takes me back. I shouldn't imagine that it will make any real difference.

---

### Post by flyingfisch on 2012-05-12
> **CatKiller said:**
> Crikey, that takes me back. I shouldn't imagine that it will make any real difference.


So it won't do anything?

---

### Post by CatKiller on 2012-05-12
> **flyingfisch said:**
> So it won't do anything?



When that technique was common, graphics processing was mostly done by the CPU and the completed frame was passed to the framebuffer for display. The PCI bus was shared and bandwidth and video memory were strictly limited. Reducing the amount of data that needed to be shuffled around by a third made a significant difference to performance.

These days, most graphics processing is done by the graphics card and there are all sorts of other processes going on at the same time. Which means there are all sorts of other performance constraints; I/O, AI, physics, scheduling for the OS, and so on. While reducing the colour depth will reduce the size of the numbers that need to be crunched, meaning that it takes less bandwidth to transfer textures from disk ultimately to the GPU, you've still got all those other things going on. And it might even make performance worse if you need to spend time converting the textures into a 16-bit colour space.

If your game is running well then you will not be able to notice a tiny improvement. If it's not running well then the tiny improvement isn't going to be enough to make it run well. Not worth the effort, in my opinion.

Although I could be wrong :-)

---

### Post by flyingfisch on 2012-06-21
Well, I have a pretty old graphics card (nvidia geforce 5200). Is that old enough where changing color depth would work?

---

