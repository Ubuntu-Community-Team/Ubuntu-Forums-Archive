---
title: "No swap partition?"
date: 2011-02-14
forum: General Help
---

### Post by sr_guy on 2011-02-14
My motherboard supports up to 8GB DDR2. I currently have 4GB installed. If I maxed out my RAM, and installed 10.10 without a swap partition, I've heard this would increase speeds significantly. Would it? 

This particular rig runs multiple servers including an Asterisk PBX with FreePBX, XBMC, and Boxee. XBMC and Boxee do not run at the same time, only one at a time. Would it be safe to run with 8GB ram, and no swap partition?

Running FreePBX/asterisk, XBMC, playing videos or youtube, and every other background processes, free shows on average 50% free.

Opinions?

---

### Post by asmoore82 on 2011-02-14
Extra RAM is always nice.

But if you aren't already experiencing massive swap usage,
lack of swap will have no effect on performance at all.

If you run a linux server with no swap at all, and if that day comes when
it is out of RAM, it is free to crash and you aren't allowed to complain :-({|=.

My laptop has 8GB of RAM ~ I only run 512 MB of swap.
I never use any swap, I cannot hibernate and I'm happy with it =D>.

---

### Post by mr_luksom on 2011-02-15
Swap doesn't degrade performance when its not used.

Even when it is being used, I'll take a slowdown any day over a crash, which is what will happen if you run out of ram.

Give it at least a gig of swap - if you don't need it, then good for you.

---

### Post by Grenage on 2011-02-15
A system won't generally crash if you run out of RAM - it swaps things out.  If you have plenty of RAM (4GB+), you can probably get away without having one at all; if you have so much hard drive space that you don't care, a swap won't do any harm.

On a laptop, I usually have a swap partition slightly larger than my RAM total - hibernation requires that RAM data is written to the drive.

---

