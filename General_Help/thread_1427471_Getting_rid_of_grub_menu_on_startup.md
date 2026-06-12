---
title: "Getting rid of grub menu on startup"
date: 2010-03-11
forum: General Help
---

### Post by sincerelyydavid on 2010-03-11
how can i get rid of that grub menu that lets you choose between 4 different boot options on startup? i only have ubuntu on my laptop and want to boot automatically into it.

---

### Post by 73ckn797 on 2010-03-11
If you are running 9.10 you can install "startupmanager" from Synaptic and change the Boot Options for the time out when the grub menu displays. This is the easy graphical way.

---

### Post by Alabamaschalk on 2010-03-11
Hi!
Try startupmanager (universe). In this you will find a boot options tab in which you can define the timeout and the default boot options.

---

### Post by Alabamaschalk on 2010-03-11
Damn, too late

---

### Post by sincerelyydavid on 2010-03-11
lol. but the grub menu never appeared before. do you guys know what might have caused it to suddenly appear?

---

### Post by 73ckn797 on 2010-03-11
> **sincerelyydavid said:**
> lol. but the grub menu never appeared before. do you guys know what might have caused it to suddenly appear?

A kernel update would add the new choice along with the old one. It would then rewrite grub in the process.

---

### Post by sincerelyydavid on 2010-03-11
how do i update my kernel, with the update manager? because startup manager's not working. i set the timeout to 0, but when i boot, it stays on the grub menu screen, and i can't boot into ubuntu without clicking enter.

---

### Post by 73ckn797 on 2010-03-11
> **sincerelyydavid said:**
> how do i update my kernel, with the update manager? because startup manager's not working. i set the timeout to 0, but when i boot, it stays on the grub menu screen, and i can't boot into ubuntu without clicking enter.

Kernel updates are a part of the regular update process. Current kernel is 2.6.31-20.

What version of Ubuntu are you using?

---

### Post by sincerelyydavid on 2010-03-12
9.10

---

### Post by derande on 2010-03-12
i've had the same problem with startup manager. only solution i have is that it took me something like 3-4 times setting the boot timeout to zero until it actually took.

keep trying and cross yr fingers.

---

