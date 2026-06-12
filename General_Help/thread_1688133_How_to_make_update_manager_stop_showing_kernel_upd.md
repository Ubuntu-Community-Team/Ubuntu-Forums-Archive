---
title: "How to make update manager stop showing kernel updates?"
date: 2011-02-15
forum: General Help
---

### Post by dewdrop_world on 2011-02-15
Is there any way to stop the Ubuntu update manager from asking me to update the generic kernels?


I'm using kernel 2.6.33-29-realtime. I never boot into the generic kernel -- therefore, security updates for the generic kernel are not relevant for me. All they do is fill up my GRUB menu.


(Or, is my assumption wrong -- if I update the generic kernel, will that push some fixes into the realtime kernel also? I think not, but computers are strange places.)


Thanks.
James

---

### Post by dcstar on 2011-02-15
> **dewdrop_world said:**
> Is there any way to stop the Ubuntu update manager from asking me to update the generic kernels?
.........

Remove them from your system.

---

### Post by kellemes on 2011-02-15
Is this what you're looking for?
[http://newbiedoc.sourceforge.net/system/kernel-pkg.html#HOLD-KERNEL-PKG]("http://newbiedoc.sourceforge.net/system/kernel-pkg.html#HOLD-KERNEL-PKG")

---

