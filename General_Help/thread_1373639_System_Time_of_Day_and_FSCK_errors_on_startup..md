---
title: "System Time of Day and FSCK errors on startup."
date: 2010-01-06
forum: General Help
---

### Post by Crowchild on 2010-01-06
I've been having some trouble lately in that every 1 out of 3 (or so) times I boot, I get an error saying that my system time-of-day is not set. I am given a few options that usually lead me to the suggestion that I need to do a FSCK... which I do. And reboot. On reboot I am given a list of the linux kernels to boot (which doesn't happen in my normal boot sequence) anyone that I choose takes be through the same set of error and the suggestion to do a FSCK. Again, I am told to reboot and this time it boots properly.

Does anyone know what may be going on or where I can find a activity log so to I can give you more indepth data on what is going on here. Like I said it's not happening every time so I can't quite reproduce this error on demand.

Thanks.

---

### Post by dcstar on 2010-01-06
> **Crowchild said:**
> I've been having some trouble lately in that every 1 out of 3 (or so) times I boot, I get an error saying that my system time-of-day is not set. I am given a few options that usually lead me to the suggestion that I need to do a FSCK... which I do. And reboot. On reboot I am given a list of the linux kernels to boot (which doesn't happen in my normal boot sequence) anyone that I choose takes be through the same set of error and the suggestion to do a FSCK. Again, I am told to reboot and this time it boots properly.

Does anyone know what may be going on or where I can find a activity log so to I can give you more indepth data on what is going on here. Like I said it's not happening every time so I can't quite reproduce this error on demand.

Thanks.

Has the CMOS battery on your motherboard died?

---

### Post by Crowchild on 2010-01-06
Yeah, that seems to be the problem... do you know if there is a way to recharge it or does it need to be replaced?

---

### Post by philinux on 2010-01-06
> **Crowchild said:**
> Yeah, that seems to be the problem... do you know if there is a way to recharge it or does it need to be replaced?

It needs replacing.

---

