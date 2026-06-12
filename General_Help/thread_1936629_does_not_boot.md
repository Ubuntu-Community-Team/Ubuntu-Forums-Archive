---
title: "does not boot"
date: 2012-03-06
forum: General Help
---

### Post by fireball69696 on 2012-03-06
hi to all

here is my problem, i installed ubuntu 10.04 on my laptop (doual boot with win7). i had to backport a new kernel (3.0.0-15-general) because i had driver problems (lan, touchpad, graphics that i noticed at first). it worked all fine until there was a disk check, from then on it's all going downwords. after i select the kernel in the boot it list it wont load.
 
the 2.6.32-38-general kernel is still working (and maybe it will have the same problem)

its the acer aspire 7750g laptop i'm talking about.

the only thing i could find for this is to boot the live cd and enter in terminal

$ sudo -s
$ fsck /dev/sdxx

(sda6 at my laptop)

this only worked for two boot-ing, but it wont work any more eather.

pls, help needed quick

---

