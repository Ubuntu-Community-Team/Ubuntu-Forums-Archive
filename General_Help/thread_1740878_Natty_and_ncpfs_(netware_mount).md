---
title: "Natty and ncpfs (netware mount)"
date: 2011-04-27
forum: General Help
---

### Post by lykwydchykyn on 2011-04-27
*(Posting this here since Natty is released tomorrow and the Natty testing forum will probably close soon.  Hope that's ok.)*

I may be the only person trying to mount Netware shares in 2011 on Natty Narwal, but in case I'm not I've run up into a nasty bug and I thought I'd see if anyone else was seeing this.

When I mount a netware share in Natty, open a BASH shell, and cd into the mountpoint, any kind of tab completion will completely crash the ncpfs connection.  BASH crashes, the mountpoint becomes inaccessible, can't be unmounted, the ncpmount process can't be killed, and even trying to list the contents of the folder containing the mountpoints either takes a loooooooooong time or never finishes.

I found [this bug](https://bugs.launchpad.net/bugs/762344) report and added some information to it, but I just wanted to see if any other ncpfs users could try this out and offer a workaround or at least contribute to the bug report.

Thanks for any input.

---

### Post by lodder on 2011-05-12
this helped me: [https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/773211](https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/773211)

---

### Post by lykwydchykyn on 2011-05-12
I'll give it a shot, I suppose.  Thanks.

---

### Post by lykwydchykyn on 2011-05-12
> **lodder said:**
> this helped me: [https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/773211](https://bugs.launchpad.net/ubuntu/+source/ncpfs/+bug/773211)

This worked!  Yay!  Just when I thought ncpfs was headed for death by bit-rot (again).  

Thanks for the help.

---

### Post by pennstatebadboy on 2011-05-16
I'm running into the same problem.

What worked for you? Just using an old kernel? Or did you need to change your file manager and/or ncpfs version as well?

---

### Post by lykwydchykyn on 2011-05-16
I upgraded to the 2.6.39 kernel from kernel-ppa.  That solved it.  Apparently it's a bug in the 2.6.38 kernel.

I didn't have to change or upgrade anything else.

---

