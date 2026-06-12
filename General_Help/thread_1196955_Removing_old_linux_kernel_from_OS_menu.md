---
title: "Removing old linux kernel from OS menu"
date: 2009-06-25
forum: General Help
---

### Post by johan34 on 2009-06-25
Hi. Im quite good with Ubuntu now and have installed it on a partition so I have an OS choices menu in the beginning. It would usually show Ubuntu generic, Ubuntu recovery, Ubuntu memtest and then XP. But after an update it now has ubuntu generic 2.6 and ubuntu generic 2.4. How can i remove the old one?

---

### Post by Sub101 on 2009-06-25
If you install startupmanager which is in Synaptic then you can use it to set the number of old kernels you want to show in Grub.

It is generally suggested that you keep at least one older kernel in the boot menu, as a new kernel update may not be as compatible as the previous one.

---

### Post by johan34 on 2009-06-25
Do you think 2.6 is compatible enough or should I still keep 2.4

---

### Post by DeMus on 2009-06-25
> **johan34 said:**
> Do you think 2.6 is compatible enough or should I still keep 2.4

Since there are many versions already from 2.6 (the latest is 2.6.30) you can safely throw away 2.4.
Which 2.6 do you have at the moment?

---

### Post by johan34 on 2009-06-25
I have 2.6.28-13 on Jaunty

---

### Post by Sub101 on 2009-06-25
If the kernel you are using now is the newest one then you should be fine. 

If it works fine then you should be ok.

---

### Post by jmszr on 2009-06-25
johan34,

It's good to keep a "back-up" kernel. When you want to remove a kernel go to the Synaptic Package Manager and search for "linux-image" and remove applicable kernel.

---

### Post by johan34 on 2009-06-25
Thanx alot!

---

### Post by hyperdude111 on 2009-06-25
It is good to keep a backup kernel, the newest for jaunty 26.xx.xx.13 fails to boot on my system. Thankfully 26.xx.xx.11 still works so I use that.

---

### Post by DeMus on 2009-06-25
> **hyperdude111 said:**
> It is good to keep a backup kernel, the newest for jaunty 26.xx.xx.13 fails to boot on my system. Thankfully 26.xx.xx.11 still works so I use that.

I use 2.6.30 already and it is wonderful.

---

