---
title: "Memory Cache?"
date: 2009-06-27
forum: General Help
---

### Post by Mercedes300 on 2009-06-27
Hi, 

Just curios, what is the memory cache used for? Htop says that the memory is full (used by programs, buffer, and cache) even when I first boot.

I found an [article]("http://www.scottklarr.com/topic/134/linux-how-to-clear-the-cache-from-memory/") about clearing the cache with the command ```
sync; echo 3 > /proc/sys/vm/drop_caches
``` as root.

Does this have any adverse effects on you system, or damage anything? I guess I'm just in the need for some schooling on this.

Thanks,

Manny.

edit: added link to article.

---

### Post by t4thfavor on 2009-06-28
You definatey want to keep the cache. Its where the kernel puts stuff it thinks you or it might want to use soon. If running programs need that cache space, the kernel gives it to them in such a short amount of time you will never notice. Let it be, and be happy its there.

---

