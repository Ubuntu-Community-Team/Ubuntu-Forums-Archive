---
title: "How to switch kernels at startup? (10.04)"
date: 2010-05-05
forum: General Help
---

### Post by g-raf on 2010-05-05
I was using Jaunty before installing Lucid - at the beginning of a restart I could hit ESC and choose if I want to load the generic kernel or the realtime kernel. In Lucid, it seems there is no such option. How can I load my linux-rt kernel?

---

### Post by dcstar on 2010-05-05
> **g-raf said:**
> I was using Jaunty before installing Lucid - at the beginning of a restart I could hit ESC and choose if I want to load the generic kernel or the realtime kernel. In Lucid, it seems there is no such option. How can I load my linux-rt kernel?

If you read the Grub2 HOWTOs it says hold the Shift key down to get the menu, or how you change the config to always display the menu.

---

### Post by dino99 on 2010-05-05
> **g-raf said:**
> I was using Jaunty before installing Lucid - at the beginning of a restart I could hit ESC and choose if I want to load the generic kernel or the realtime kernel. In Lucid, it seems there is no such option. How can I load my linux-rt kernel?

the rt kernel is outdated now

---

### Post by g-raf on 2010-05-05
> **dcstar said:**
> If you read the Grub2 HOWTOs it says hold the Shift key down to get the menu, or how you change the config to always display the menu.

Thank a lot. This worked perfectly. My mistake for not checking the new grub how to before posting this thread.

---

### Post by g-raf on 2010-05-05
> **dino99 said:**
> the rt kernel is outdated now

Really? What do you mean by "outdated"? Is there something that works better for low latency audio production?

---

