---
title: "x86 to utilize 8gb of ram?"
date: 2011-07-14
forum: General Help
---

### Post by MtnDew on 2011-07-14
I know in Windows that if you install the x86 version, it can't utilize more than four gigabytes of ram, is that true for Ubuntu/Linux? I have 8GB of ram and I want to make sure it is all utilized.   Linux Ubuntu-Aphex 2.6.35-30-generic-pae #54-Ubuntu SMP Tue Jun 7 20:28:33 UTC 2011 i686 GNU/Linux

---

### Post by Seq on 2011-07-14
> **MtnDew said:**
> I know in Windows that if you install the x86 version, it can't utilize more than four gigabytes of ram, is that true for Ubuntu/Linux? I have 8GB of ram and I want to make sure it is all utilized.   Linux Ubuntu-Aphex 2.6.35-30-generic-pae #54-Ubuntu SMP Tue Jun 7 20:28:33 UTC 2011 i686 GNU/Linux

The "pae" bit in your kernel name above seems to indicate you have a PAE kernel. Assuming your hardware supports it you will have access to that memory. If you're running the live CD try `free -m` in a terminal and see.

Although is there any reason you would not want to use the 64-bit build?

---

### Post by mastablasta on 2011-07-14
Ubuntu can address more RAM in 32 bit by using PAE kernel.

however why not just install 64 bit OS (AMD64)? as a bonus it will work faster

---

### Post by seawolf167 on 2011-07-14
I would highly suggest using the x86_64 version over using PAE. But if you want to, you can read how to enable PAE from [this link]("https://help.ubuntu.com/community/EnablingPAE").

---

