---
title: "After &quot;rm -rf&quot; directories, i could still &quot;locate&quot; them"
date: 2010-06-24
forum: General Help
---

### Post by hanat on 2010-06-24
I was removing some directories, and later if i try "locate" command, i could still able to find it. i wonder it anyone has experienced this, whats happening?

---

### Post by John Bean on 2010-06-24
I bet you can't "find" them though ;-)

Clue: "locate" uses a cache, "find" doesn't.

---

### Post by 98cwitr on 2010-06-24
clear your cache

---

### Post by hanat on 2010-06-24
i have reboot my computer, and i could still "locate" them.

---

### Post by hanat on 2010-06-24
Yes, i could not "find" them.
Why could "locate" still find them even if i reboot my computer

---

### Post by John Bean on 2010-06-24
> **hanat said:**
> i have reboot my computer, and i could still "locate" them.

Rebooting doesn't clear the cache.

---

### Post by mcphargus on 2010-06-24
I'm pretty sure `sudo updatedb` will update the cache.

---

### Post by hanat on 2010-06-24
> **mcphargus said:**
> I'm pretty sure `sudo updatedb` will update the cache.
cool!
now I can continue!

---

