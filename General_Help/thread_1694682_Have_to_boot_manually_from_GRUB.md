---
title: "Have to boot manually from GRUB"
date: 2011-02-24
forum: General Help
---

### Post by a_l_a_n on 2011-02-24
My grub broke ages ago. Since then turning on my machine yields a grub prompt and I must type

> set root=(hd0,1)
> chainloader +1
> boot

I have tolerated this situation because

a) I'm lazy
b) It makes me feel like a mad h4X0r and I long for some mere mortal to witness me starting my machine this way and be hugely impressed (but this hasn't happened once in the last year)

Enough I have had!

What's wrong? How do I fix?

---

### Post by wiggly81 on 2011-02-24
try this
 ```
sudo update-grub
```
it should rebuild the grub.cfg

---

### Post by drs305 on 2011-02-24
Please download and run the boot info script from the following site. Post the RESULTS.txt contents and we can take a look at your boot files and decide what steps you need to take.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

