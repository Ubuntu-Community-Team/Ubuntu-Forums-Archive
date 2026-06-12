---
title: "HP Media Smart Server, no connection"
date: 2010-03-23
forum: General Help
---

### Post by kdsn on 2010-03-23
Hello Guru's, I'm new to Linux, and have thrown myself head first into it.

I have an HP Media Smart Server, can not remember which model, but it is not possible to connect a monitor.

Now I have taken the HD out and installed Linux 9.10 server on it and it worked fine until I put the disk back into the HP.

it looks like it boots up nicely, but I can not connect, I think there is a problem with IP / network card, I think it is a SIS190-SIS191 from what I've read on the web.

I am a lost noob, so please be gentle

---

### Post by dcstar on 2010-03-24
> **kdsn said:**
> Hello Guru's, I'm new to Linux, and have thrown myself head first into it.

I have an HP Media Smart Server, can not remember which model, but it is not possible to connect a monitor.

Now I have taken the HD out and installed Linux 9.10 server on it and it worked fine until I put the disk back into the HP.

it looks like it boots up nicely, but I can not connect, I think there is a problem with IP / network card, I think it is a SIS190-SIS191 from what I've read on the web.

I am a lost noob, so please be gentle

If you installed Ubuntu on one set of hardware then there is no guarantee that a system will run when moved to different hardware.

Systems **must** be installed on the same hardware they are to run on to guarantee that all configuration is done correctly.

---

### Post by sandyd on 2010-03-24
you unfortunately cannot use ubuntu on that computer. there was an earlier post about this (im too lazy to dig it up, but I remember it cause I posted in it). the driver for that particular network card is not included in ubuntu. you will have to download it from the sis site. however, the drivers you get from there are extremely outdated, and seem to only work for RPM / RedHat-based distros. however, you might want to email or call them !nd ask them about the drivers to comfirm that they dont have newer drivers hidden somewhere.

---

