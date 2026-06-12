---
title: "Can I install an older kernel?"
date: 2010-01-06
forum: General Help
---

### Post by Bluesplayer on 2010-01-06
Hi

I want to move my ununtu server hard drive to an older machine though it is more powerful.  I am getting an error stating that I need to use a suitable kernel for the machine - it recognises it as i386.  Can I install this older kernel without losing data so that it can be booted eventually with the older computer?

Regards

---

### Post by spiderbatdad on 2010-01-06
I would have to say no. It sounds as if the kernel is significantly older. The file system has changed dramatically. Binary compatibilities among many system programs and the hardware has also changed. You will have to back up your data elsewhere prior to a fresh installation of the new operating system.

---

### Post by jocko on 2010-01-06
I really doubt it is asking for an OLDER kernel.
You don't say what computers you have, but I'm guessing the newer computer have a 64 bit cpu, and you have 64 bit ubuntu installed on it, while the older computer is 32 bit.
In that case, a different kernel will not help. You need to install the 32 bit version of ubuntu.

---

