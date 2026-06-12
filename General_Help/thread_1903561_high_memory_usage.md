---
title: "high memory usage"
date: 2012-01-02
forum: General Help
---

### Post by hodad on 2012-01-02
Freezing up my pc. I usually run four workspaces, each with an instance of Firefox.  I have a fairly new motherboard, but minimal memory.  I've just ordered 4GB of DDR2 memory, but need some help until it arrives in about a week.  I'm looking for some good tutorials/advice on tweaking memory (handling cache, buffers, etc).

Gigabyte GA-MA785GM-US2H
AMD Phenom 9750 Quad Core
740.5 GB memory
250 GB primary HD
10 GB secondary HD

Screenshot attached.  After screenshot, I closed everything (2 instances of Firefox) but system manager, and it was still using 99.9% of swap memory, and 60% "memory" (and my understanding of how they work is fuzzy). 

Thanks in advance!

---

### Post by hodad on 2012-01-02
Oopps!  Screenshot attached...

---

### Post by LinuxFan999 on 2012-01-02
Which version of Ubuntu are you using?

---

### Post by Bobhuber on 2012-01-02
First of all your showing less than 1/gig of total available memory 740/meg with the graphics using the rest of the 1/gig (I'm guessing). Ubuntu should run fine on that assuming you have a large enough swap.If you have 4/gig ordered plan on setting up a 2/gig swap partition or swap file (depending on the version of Ubuntu).
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Read the WHOLE page. Some stuff on the bottom about swappiness that can dramatically speed up your system.

---

### Post by hodad on 2012-01-02
Thanks for responses:
Using 10.10 

Will check out the link on swapping.

---

### Post by hodad on 2012-01-03
After reading the article on swap files, I took another look at my screenshot, and noticed that I had only about 4MB of swap for about 750 MB of ram.  I also realized that (serendipitously) I had a an old 10GB drive that was actually installed, but not being used.  I read that it's good to have the swap partition set on a separate drive (if possible), so that's what I did.

I set up the swap to be about  8 of the 10 GB of the old drive (so it's essentially a "swap drive" now).  I used 8GB since I hope to install 4GB of new memory when it arrives in the mail.

A new screenshot shows that swap usage went from 99.9% down to zero; but that zero will probably rise as I use the pc for a while during the day.

I think that increasing the swap size from 4MB to 8GB did the trick!  Will post again if I run into any problems today, but I think that problem is solved.

Thanks for your help!

---

