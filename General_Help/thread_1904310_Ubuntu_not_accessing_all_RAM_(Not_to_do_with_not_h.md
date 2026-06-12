---
title: "Ubuntu not accessing all RAM (Not to do with not having 32/64 bit)"
date: 2012-01-04
forum: General Help
---

### Post by Henkdroid on 2012-01-04
Hi, I have 1024MB of RAM installed (this shows up in the BIOS). When I'm using Ubuntu however only 977MB shows up. Why aren't the other 43MB of RAM not showing up?

---

### Post by 98cwitr on 2012-01-04
...

---

### Post by 2F4U on 2012-01-04
Any computer needs some amount of RAM for input/output buffering. If you have an integrated graphics card without its own memory, the card will use your regular RAM and the result is that this RAM is not available to the operating system.

---

### Post by Henkdroid on 2012-01-04
Thanks, that's probably it as I only have an Intel Mobile GM965/GL960.

---

### Post by 2F4U on 2012-01-04
The intel card is a so-called integrated graphics card and has no RAM of its own. So it will take some of the available RAM, which then cannot be used by the OS.

---

### Post by mcduck on 2012-01-04
Even without an integrated graphics card, Linux would never report all the physical RAM as available. And there's a good reason for this, the kernel itself is loaded into RAM at boot time, and that part of the memory of course won't ever be available for any other use...

If you check the information about installed physical RAM modules, by running "cat /proc/meminfo" for example, you'll see all the RAM detected. But reporting memory that you'll never be able to use as available wouldn't make much sense, would it? ;)

---

### Post by dcstar on 2012-01-05
> **Henkdroid said:**
> Hi, I have 1024MB of RAM installed (this shows up in the BIOS). When I'm using Ubuntu however only 977MB shows up. Why aren't the other 43MB of RAM not showing up?

Because on 80x86 hardware architecture other motherboard resources use the same Address Space that RAM also maps to and therefore those address blocks are unavailable for use as RAM.

Your motherboard probably maps a lot of those addresses above the physical RAM thus reducing the footprint, but there are still some that must exist within the first 4096MB to be compatible with 32-bit OSs.

---

