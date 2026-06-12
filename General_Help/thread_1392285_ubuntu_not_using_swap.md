---
title: "ubuntu not using swap"
date: 2010-01-27
forum: General Help
---

### Post by pavel989 on 2010-01-27
hi everyone.

I got like a gig of ram on this netbook here, running karmic. But apperently it uses no swap at all. its mounted correctly and all that. however,is it possible that its not using the swap space because the swap space in a logical partition?

---

### Post by t4thfavor on 2010-01-27
Remove all but 256MB of ram, and then load firefox, and a few other apps, that will start your swap, until then be happy you don't have to use it. Linux rarely does if you have adequate memory, which you appear to have.

---

### Post by ramjet_1953 on 2010-01-27
When you have a reasonable amount of RAM the swapfile is almost never used.

However, if you want to use hibernate on you laptop, you will need around twice your RAM size in swapfile size.

To familiarize yourself with this, follow the link below and have a good read.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Regards,
Roger :D

---

