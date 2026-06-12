---
title: "Question about Kernel"
date: 2006-02-27
forum: General Help
---

### Post by BrejoSacor on 2006-02-27
Hey, I just updated, well installed the 686-smp kernel...
  I had been running 386, and it was fine, but after a reboot, the 686-smp kernel system was just running really slow and just terrible.  Is there anyway to just remove that one all together.  So that my old kernel is the only one that shows up in GRUB.

Thanks. Jon

---

### Post by rjwood on 2006-02-27
if you installed it via synaptic you only need to uncheck it in synaptic.

---

### Post by nixclusive on 2006-02-27
You you have an SMP machine? That Symmetric Multuple Processor...

SMP support on uniprocessor machines can cause slower performance. Uninstall it right away, if you are not sure.

---

### Post by BrejoSacor on 2006-02-27
thanks, i think that worked, although i did install via apt-get.

---

### Post by Ramses de Norre on 2006-02-27
Do you have a dual core processor or hyper threading? Because that's the only situation you will need an smp kernel in I think.
Otherwise, try the normal 686 kernel.

---

### Post by BrejoSacor on 2006-02-27
yea, i have a P4 HT 3.2 gHz processor, so can i use the smp kernel? but when i had that one, it was real slow, almost like I had no RAM!!!  maybe it just wasn't confgured right...

---

### Post by Ramses de Norre on 2006-02-27
I haven't got it myself so I don't know what to expect, but it should be faster..
Maybe you have to configure something but that would surprise me..
You could try reinstalling it maybe:-k

---

### Post by BrejoSacor on 2006-02-27
yea, thanks for all the help guys.  I think i will just stick to old trusty (386).

Jon

---

