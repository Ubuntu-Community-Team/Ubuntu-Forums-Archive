---
title: "Want my pc to work faster, help!"
date: 2009-09-28
forum: General Help
---

### Post by arnab_das on 2009-09-28
I want my pc to work faster when it comes to converting videos etc, looks like most conversion programmes take ages to convert videos.

Should a RAM upgrade suffice or does it require a processor upgrade?

---

### Post by pawhtiobo on 2009-09-28
Hi :)
 
What kind of CPU and amount of RAM do you have?
 
see ya...

---

### Post by arnab_das on 2009-09-28
> **pawhtiobo said:**
> Hi :)
 
What kind of CPU and amount of RAM do you have?
 
see ya...

currently i have AMD Sempron 3200+ and 1GB RAM, have an MSI K9MMV motherboard.

---

### Post by philinux on 2009-09-28
Add the app "CPU frequency scaling monitor".

Once added left click it and choose performance. See if it makes things faster.

---

### Post by Vaphell on 2009-09-28
video transformations are math heavy so the raw power of CPU is what counts, plenty of RAM helps too.
Your hardware looks dated, adding RAM would help a little, but i wouldn't expect miracles

---

### Post by CrusaderAD on 2009-09-28
A new motherboard and processor is probably what you need. I hear the quad core intels are the fastest right now, but I could be wrong. More RAM probably won't make much of a difference.

---

### Post by arnab_das on 2009-09-28
> **philinux said:**
> Add the app "CPU frequency scaling monitor".

Once added left click it and choose performance. See if it makes things faster.

i tried that but apparently my sempron doesnt allow that :(

---

### Post by arnab_das on 2009-09-28
> **Vaphell said:**
> video transformations are math heavy so the raw power of CPU is what counts, plenty of RAM helps too.
Your hardware looks dated, adding RAM would help a little, but i wouldn't expect miracles

it is indeed dated. but am getting a new laptop soon so dont really want to spend too much on my pc configuration right now. i thought a ram upgrade would suffice.

---

### Post by Giblet5 on 2009-09-28
Agreed on the CPU-intensive math comments.

Do you have an nvidia graphics card? Check out nvidia's Cuda project: it uses your GPU's graphics pipelines to speed up transcoding, transforms, and tons of other stuff.

Two cores = quick
Four cores = almost twice as quick
24 graphics pipes = much much MUCH quicker

---

### Post by Giblet5 on 2009-09-28
> **arnab_das said:**
> it is indeed dated. but am getting a new laptop soon so dont really want to spend too much on my pc configuration right now. i thought a ram upgrade would suffice.

No laptop is going to (noticeably) beat your old desktop on media transcoding.

An old Q6600 quad-core desktop will easily tromp the fastest Alienware laptop made right now (P9600 dual core, I think), and then there's the issue of laptop disk performance.

Media transcoding is slow. Pros dedicate large systems to the task and they still have to practice yoga.

---

### Post by pawhtiobo on 2009-09-28
Hi :)
 
I have a smillar PC at home, Sempron 3000+ with a MSI Board also , not much can be done, i just done a little overclock (2400 Mhz) and added some decent RAM (2 GB OCZ ETX), tweaked a little the BIOS and the SO...i got maybe 15-20% preformance gain, but with the risks that the overclocking give you...if i where you i would save the money for the laptop....
 
see ya...

---

### Post by 3rdalbum on 2009-09-28
The Semprons are quite slow for video encoding.

They support 64-bit, or at least mine does, so you might get a speed-up by going to 64-bit Ubuntu if you haven't already. Upping the RAM won't hurt but I don't think it will help much either.

If you're encoding to H.264 format you will definitely want to get a new CPU with lots of cores, because x264 can work across multiple threads. If you're encoding to something else you might want to look at a fast dual-core instead, like the Intel Core 2 Duo E8400 (3GHz). The Sempron 3200s use the old 939 socket, I believe, so you'd pretty much be up for a motherboard upgrade anyway.

Laptops are definitely **not** the answer if you want good video encoding performance. If you want a laptop, go right ahead; but don't expect it to be more than a couple of percent faster than your Sempron.

---

