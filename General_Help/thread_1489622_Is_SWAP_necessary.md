---
title: "Is SWAP necessary?"
date: 2010-05-21
forum: General Help
---

### Post by bigseb on 2010-05-21
If I understand things corrctly then the swap partition fulfills the same function as the page file in Windows. I always turned my page file off as I have more than enough RAM. So... can I delete the SWAP partition? 

Maybe this is a silly question... dunno... would be interested to know.

---

### Post by frostschutz on 2010-05-21
The swap partition may also be used for suspend on disk, but otherwise, if you don't want swap you don't need it - if the kernel runs out of memory it will just start killing processes then.

---

### Post by obscurant1st on 2010-05-21
If you have enough RAM there is no need for swap partition. Actually swap is needed if you are running any applications which may run out of memory with your current RAM configuration, then additional memory will be taken from SWAP partition. If you dont hv a swap partition, you system may suddenly restart of shutdown. Sometimes the app is simply killed automatically.

---

### Post by Detonate on 2010-05-21
I always have a swap partition, even though with my configuration, my system never uses it.  It's just small amount of disk space and does not affect performance in any way if it is not being used.  But it's there if ever needed.  You may want to adjust your swappiness settings.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Bobhuber on 2010-05-21
> **bigseb said:**
> If I understand things corrctly then the swap partition fulfills the same function as the page file in Windows. I always turned my page file off as I have more than enough RAM. So... can I delete the SWAP partition? 

Maybe this is a silly question... dunno... would be interested to know.
Read This
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

