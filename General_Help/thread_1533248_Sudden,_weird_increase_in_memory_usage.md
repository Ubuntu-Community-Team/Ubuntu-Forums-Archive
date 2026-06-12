---
title: "Sudden, weird increase in memory usage"
date: 2010-07-17
forum: General Help
---

### Post by Jopj on 2010-07-17
Hi, I have a mini-ITX pc running Ubuntu 10.04 that I use as a home server. I originally installed 256 MB of memory to it and later had 512 MB for a short while. The system used about 230 mb actively in both cases with SETI running, the rest was cache. When I installed 1 GB of memory, the system suddenly started using more than 580 MB just sitting there, and more than 700 while running SETI. Why this sudden extra memory usage? I'd think that the extra memory would just be used for cache as it was in the previous cases.
The problem I have is that I can't find out what is using the memory. Htop's numbers don't quite add up: [http://www.imagebam.com/image/af9be489014144](http://www.imagebam.com/image/af9be489014144). How can a headless machine use so much more memory than a fully fledged desktop system which uses around 350 MB, most of which is for GNOME?
I'm not that knowledgeable about linux and probably am missing something really simple, so any help is appreciated!

---

### Post by Ocxic on 2010-07-17
The system will attempt to utilize ALL of your memory/or at least all that it needs, and is expected behavior. 
Your system is just able to cache more data then was able to before, and has adjusted itself to make better usage of the increase in memory.

I have 8GB of RAM and after a few hours of using my computer, it gets maxed out(currently 70% programs, 30% cache). it's all normal.

---

### Post by Jopj on 2010-07-17
OK, thanks!
I didn't think of that as the memory usage remained exactly same eith 512 and 256 MB of memory, I thought that the cache was serving that duty.
Still, why don't Htop's numbers add up, is it only measuring the memory *actually* used?

---

### Post by Ocxic on 2010-07-18
yes "htop" will only show how much memory is currently being used by application/programs, it does not care about what is in cache.

---

