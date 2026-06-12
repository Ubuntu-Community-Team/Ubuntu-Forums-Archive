---
title: "Linux 2.6.17 Released"
date: 2006-06-19
forum: General Help
---

### Post by FizDev on 2006-06-19
Hey! The Linux Kernel 2.6.17 has just been released. 
> "After almost three months, Linux 2.6.17 has been released. The changes include support for Sun Niagara CPUs, a new I/O mechanism called 'splice' which can improve the performance greatly for some applications, a scheduler domain optimized for multicore machines, driver for the widely used broadcom 43xx wifi chip (Apple's Airport Extreme and such), iptables support for the H.323 protocol, CCID2 support for DCCP, softmac layer for the wireless stack, block queue IO tracing, and many other changes listed at the changelog"
[http://linux.slashdot.org/linux/06/06/19/0138242.shtml](http://linux.slashdot.org/linux/06/06/19/0138242.shtml)

Does anyone know when will it be available in the repositories?

---

### Post by Shay Stephens on 2006-06-19
We are using 2.6.15 right now, so I would think it's a 6month window before we see the new kernel.  But that is just speculation.

---

### Post by gabrielsaldana on 2006-06-19
The new features sound great, specially the broadcom support. We could forget about the fwcutter tool.

Why wait 6 months? Cant we just compile the new kernel sources?

---

### Post by RAOF on 2006-06-19
[QUOTE=FizDev]...
Does anyone know when will it be available in the repositories?[/QUOTE]
Yep:  Never, for Dapper.  Strictly security/bug fixes only for Dapper since it's release.  The possiblity to break setups is just too great with big, complicated things like the kernel.

---

### Post by Shay Stephens on 2006-06-19
[QUOTE=RAOF]Yep:  Never, for Dapper.  Strictly security/bug fixes only for Dapper since it's release.  The possiblity to break setups is just too great with big, complicated things like the kernel.[/QUOTE]
I'm thinking it will show up in edgy.

---

### Post by mat1t on 2006-06-19
2.6.17 has been in edgy since the beginning. I think it was using a release candidate. I should think it will be updated to full release once it's come downstream and has been tested.

---

### Post by funkenstein on 2006-06-19
as gabriel said, you can just compile the new kernel yourself, which is what I'm going to do soonly :D

---

