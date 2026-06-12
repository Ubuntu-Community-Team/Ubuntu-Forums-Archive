---
title: "64 bit server version not recognizing 4G of memory"
date: 2010-05-06
forum: General Help
---

### Post by mdolian on 2010-05-06
I have an Acer Aspire Revo with 4G of memory.  I installed the 64 bit server version on it but for some reason Ubuntu only sees 3G.  The bios recognizes all 4G so the motherboard definitely supports it.  Should 4G work out of the box on the 64 bit Ubuntu versions or do I have to do something to enable it?

Linux ambernet 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux

Thanks

---

### Post by howefield on 2010-05-06
This comes up fairly regularly, and often the cause is that the motherboard/chipset does not support 4 gig of memory. I know - crazy, ect ect.

Have you checked yours out ?

---

### Post by mdolian on 2010-05-06
I thought if the bios shows 4G, then the motherboard supports it?  Is that not the case?

---

### Post by LowSky on 2010-05-06
Are you using onboard video? If yes it maybe using the 1GB missing.

---

### Post by howefield on 2010-05-06
> **mdolian said:**
> Is that not the case?

Nope, it's not always the case. It is possible to have the BIOS see all your memory, but the chipset not.

I don't know about your specific model, just throwing it in there for you to check.

---

### Post by dino99 on 2010-05-06
try the "pae" kernel to see if its make differences or an other server kernel than yours

---

### Post by howefield on 2010-05-06
You don't seem to be alone.

[http://www.revouser.com/forum/viewtopic.php?f=8&t=359](http://www.revouser.com/forum/viewtopic.php?f=8&t=359)

---

### Post by mdolian on 2010-05-06
> **howefield said:**
> You don't seem to be alone.

[http://www.revouser.com/forum/viewtopic.php?f=8&t=359](http://www.revouser.com/forum/viewtopic.php?f=8&t=359)

interesting, thanks for the link

---

### Post by Slim Odds on 2010-05-06
> **dino99 said:**
> try the "pae" kernel to see if its make differences or an other server kernel than yours

You don't need a PAE kernel with 64 bit (indeed, there is no such thing).

The issue is always the hardware..... i.e., a motherboard the supports "memory hole mapping" and is properly configured to enable that (they sometimes call it something else).

Even with a 64 bit OS, there is a need to allow some hardware to live in the lower 4G address space. This means that some of the RAM memory must be moved up above the 4G address. There are tons and tons of posts that talk about this so I'm not going to say any more (feel free to find those).

---

### Post by RTrev on 2010-05-06
I have both 64-bit Ubuntu and 32-bit Lubuntu installed on a 4G machine.  The 32-bit sees 3.6G, and the 64-bit sees 3.9G.

My video card has half a gig on-board, so it's not stealing much of my main memory.  Perhaps that's the issue in your case.. something is taking that memory.  I don't think it's the fault of the OS, given that I've been running this setup for years and 64-bit Ubuntu has always seen 3.9G of my 4G.

Hope someone can help you diagnose precisely what's going on.

---

