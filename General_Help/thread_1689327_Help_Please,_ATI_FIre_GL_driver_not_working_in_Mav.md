---
title: "Help Please, ATI FIre GL driver not working in Maverick, screen very unstable"
date: 2011-02-16
forum: General Help
---

### Post by maddbaron on 2011-02-16
Was having an xorg problem earlier now resolved but now the screen is extremely unstable and bouncing. I checked my ATI Fire GL driver and it is installed and working fine.

Is there a CLI I can enter and see the issue or perhaps 10.10 and my drivers are conflicting?

EDIT: I see in synaptic I have nvidia drivers and something called a nouveau display driver. Can I remove those since I run an ATI card?

---

### Post by maddbaron on 2011-02-16
bump

If I disable my fire gl driver in safe mode then reactivate it in my regular session will that fix the current issue? 

anyone know?

---

### Post by tgalati4 on 2011-02-16
There are several log files to check:

/var/log/Xorg.0.log
.xession-errors          (in your home directory)

Also check dmesg to see if you are actually having video hardware problems:

dmesg | more  (spacebar to page forward, q to quit)

As a general rule, don't remove anything from a base Linux system unless:

1.  You know what you are doing.
2.  You don't know what you are doing and you don't care.
3.  Acknowledge the fact that if you break it you get to keep both pieces.

---

### Post by maddbaron on 2011-02-16
> **tgalati4 said:**
> There are several log files to check:

/var/log/Xorg.0.log
.xession-errors          (in your home directory)

Also check dmesg to see if you are actually having video hardware problems:

dmesg | more  (spacebar to page forward, q to quit)

As a general rule, don't remove anything from a base Linux system unless:

1.  You know what you are doing.
2.  You don't know what you are doing and you don't care.
3.  Acknowledge the fact that if you break it you get to keep both pieces.


I stopped the stuttering, removed the drivers. soon as i put them back & reboot the stuttering returns. So I took them off

I'm @ my wits end

I ran dmesg and I have no clue what I'm looking for. 

this is all very befuddling

ATI drivers aren't working. But the original problem has been solved if a mode reads this please merge with my thread in the video area.

---

