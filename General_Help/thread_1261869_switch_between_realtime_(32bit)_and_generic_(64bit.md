---
title: "switch between realtime (32bit) and generic (64bit) kernel?"
date: 2009-09-09
forum: General Help
---

### Post by rymdmyr on 2009-09-09
I've got a laptop running with a dual core CPU and I'd like to use Ubuntu Studio (with a realtime kernel) and Ubuntu (generic) kernel.
Is it generally possible (and safe) to have the realtime kernel (32bit) and the generic kernel (64bit) installed at the same time and just decide when GRUB comes up in which one to work for the next session? 

The reason is: Openoffice3 does not work with rt kernels and some audio softwares as supercollider or puredata are lousy on generic kernels (and not supported with 64bit).

It would be convenient to have both, a dual boot within one installation, so to say.

Any experiences or ideas on this?
Thanks!

---

### Post by ronparent on 2009-09-09
My quick take on it is you cannot install a 32bit and 64bit on the same partition. It will work fine with each in its own partition - they can share the same swap. Although they could share the same data drives, I don't think they could share a /home partition. With these provisoes a dual boot is doable.

---

