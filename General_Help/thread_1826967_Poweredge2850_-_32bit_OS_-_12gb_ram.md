---
title: "Poweredge2850 - 32bit OS - 12gb ram"
date: 2011-08-17
forum: General Help
---

### Post by Sternfan on 2011-08-17
Hi all,

I have a pe2850 that I installed the 32-bit version of Ubuntu.  It had 4gb ram, and I would like to upgrade to 12gb.  So, when I add 8gb ram to it, will the 32bit ubuntu see all the 12gb?  Or, do I need to reinstall with the 64-bit?

Thanks,
Rob

---

### Post by Wim Sturkenboom on 2011-08-17
You need the PAE kernel for 32 bits to support more than 3GB RAM; should be in the repositories.

---

### Post by Sternfan on 2011-08-17
Thanks for the prompt reply.  If I installed it with 4gb ram, shouldn't it already have the PAE Kernel?  How can I check?

Rob

---

### Post by dino99 on 2011-08-17
> **Sternfan said:**
> Thanks for the prompt reply.  If I installed it with 4gb ram, shouldn't it already have the PAE Kernel?  How can I check?

Rob

2 things to do:
- activate PAE into the bios
- install kernel generic PAE instead of simple generic (headers & image)

then all the ram will be used.

---

### Post by Sternfan on 2011-08-17
I am now thinking of taking the plunge and just putting a 64-bit version on the pe2850.  Anybody have any issues with this?

Thanks,
Rob

---

### Post by oldos2er on 2011-08-17
> **Sternfan said:**
> I am now thinking of taking the plunge and just putting a 64-bit version on the pe2850.  Anybody have any issues with this?

With that much RAM, I don't know why you'd want to run anything other than a 64-bit OS. What processor does the system have?

---

### Post by Slim Odds on 2011-08-17
64 bit all the way!

---

### Post by pqwoerituytrueiwoq on 2011-08-17
+1 64bit
just use flash aid (ff addon) to get flash working

---

### Post by Sternfan on 2011-08-17
The server has dual 2.8s with hyperthreading.  Looks like I am going to redo the whole server.

Rob

---

