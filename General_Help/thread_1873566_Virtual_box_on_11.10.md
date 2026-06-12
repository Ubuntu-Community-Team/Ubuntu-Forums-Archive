---
title: "Virtual box on 11.10"
date: 2011-11-01
forum: General Help
---

### Post by amiacamal on 2011-11-01
My virtual box doesnt seem to do anything. I installed from the website but cant seem to create any vm's. 
I'v been stuck on this screen for an hour now... i told it to make an xp vm, using 1 gb ram and 10gb space.

---

### Post by tartalo on 2011-11-01
Any reason why you don't use the virtualbox in the repositories? That works for me.

---

### Post by thatguruguy on 2011-11-01
> **tartalo said:**
> Any reason why you don't use the virtualbox in the repositories? That works for me.

I don't think that the virtualbox in the repositories fully supports USB.

To the OP: are you sure you have enough disk space?  I'm using virtualbox without issue on my 11.10 install.

---

### Post by CerberusCommand on 2011-11-01
Oracle's virtual box has recently been having problems with installing windows, it dumped on me on several occasions, both from the website download and from the repository download. It maybe a random server issue since it didn't happen earlier this year with ubuntu v11.04. Unfortunately the only solution which I can think of is emailing the developers at [https://forums.virtualbox.org](https://forums.virtualbox.org)  or wait for other users to come up with a solution.

---

### Post by haqking on 2011-11-01
make sure you have the latest vbox 4.1.4 from oracle here [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

and the extensions pack

then try again.

Once this is done If you have USB issues make sure you are in the vboxusers group with

```
sudo usermod -a -G vboxusers username 
```

and create a USB filter

---

