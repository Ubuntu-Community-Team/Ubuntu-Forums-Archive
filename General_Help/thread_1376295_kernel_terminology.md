---
title: "kernel terminology?"
date: 2010-01-09
forum: General Help
---

### Post by mahela007 on 2010-01-09
What does the 'generic' tag mean in the kernels that are installed by Ubuntu?

---

### Post by lykwydchykyn on 2010-01-09
> **mahela007 said:**
> What does the 'generic' tag mean in the kernels that are installed by Ubuntu?

Once upon a time, they used to ship separate kernels for i386, i686, k7, and a few other variants of 32 bit intel/amd processors.  Eventually they just rolled all these up into one generic kernel that works with all 32 bit x86 processors.  Hence generic.

Hope that wasn't too techie.

---

### Post by mahela007 on 2010-01-09
Nope... very good answer. Errmm so did they have to sacrifice anything for this simplicity?

---

### Post by lykwydchykyn on 2010-01-09
> **mahela007 said:**
> Nope... very good answer. Errmm so did they have to sacrifice anything for this simplicity?

I can't say for sure, but I've heard that the optimizations that used to be compiled in are now automatically detected at runtime.  I think with modern processors a lot of these things become moot.

---

### Post by NoaHall on 2010-01-09
> **lykwydchykyn said:**
> I can't say for sure, but I've heard that the optimizations that used to be compiled in are now automatically detected at runtime.  I think with modern processors a lot of these things become moot.

The difference between a own complied kernel and a generic one is very small. It might make your system about 2% faster for a lot of hard work.

---

### Post by falconindy on 2010-01-09
> ** lykwydchykyn]I think with modern processors a lot of these things become moot.[/QUOTE]
[QUOTE=NoaHall said:**
> The difference between a own complied kernel and a generic one is very small. It might make your system about 2% faster for a lot of hard work.
I disagree. Look into Con Kolivas's patchset (BFS scheduler). His work centers around desktop interactivity and low latency. x264 encoding times are often used as benchmark for showing the benefits of using his CPU scheduler over the default.

Also, fwiw, my kernel (pre-BFS) used to compile in about 7 minutes. With BFS, I shave about a minute off that time.

edit: using a 3.16ghz C2D with 2gb of RAM.

---

### Post by lykwydchykyn on 2010-01-10
> **falconindy said:**
> I disagree. Look into Con Kolivas's patchset (BFS scheduler). His work centers around desktop interactivity and low latency. x264 encoding times are often used as benchmark for showing the benefits of using his CPU scheduler over the default.

Also, fwiw, my kernel (pre-BFS) used to compile in about 7 minutes. With BFS, I shave about a minute off that time.

edit: using a 3.16ghz C2D with 2gb of RAM.

While all that may be true, it has nothing to do with the processor-specific kernels formerly offered by Ubuntu which my remarks referred to.  Unless I'm mistaken, Ubuntu never offered a BFS-enabled kernel.

---

