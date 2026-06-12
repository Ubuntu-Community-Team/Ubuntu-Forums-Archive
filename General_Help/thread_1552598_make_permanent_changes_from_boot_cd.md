---
title: "make permanent changes from boot cd"
date: 2010-08-13
forum: General Help
---

### Post by stad on 2010-08-13
I use Ubuntu 10.04 and after installing the driver for my onboard video card, I can no long boot into Ubuntu. I'm thinking that if I was somehow able to remove it, this might fix the problem. Is there a way to do this, possibly from the boot cd? Any help is much appreciated. I'm new to Linux and this was on the family's primary computer.

Thank you.

---

### Post by wojox on 2010-08-13
What video card and driver? You should be able to boot a Live-CD and uninstall it.

---

### Post by Jazzy_Jeff on 2010-08-13
I think he is asking how to use the boot cd to remove it.

---

### Post by linux18 on 2010-08-13
that kind of thing requires chrooting, give me a few minutes to gather some notes

EDIT: try booting into recovery mode and get to a root prompt

---

### Post by wojox on 2010-08-13
> **Jazzy_Jeff said:**
> I think he is asking how to use the boot cd to remove it.

Ah, good point.

Boot off your Live-CD, mount the partition and open your terminal, run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

