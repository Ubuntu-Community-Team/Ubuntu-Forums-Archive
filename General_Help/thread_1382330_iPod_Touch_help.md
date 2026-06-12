---
title: "iPod Touch help"
date: 2010-01-15
forum: General Help
---

### Post by HH8823WP on 2010-01-15
Is there a way to sync an ipod Touch 3G with Ubuntu?

---

### Post by warfacegod on 2010-01-15
I don't think that the Touches work with Ubuntu but you could try installing gtkpod from Synaptic.

---

### Post by baddog144 on 2010-01-15
No, not really. :(
I think it was possible with early firmwares, but these days you gotta have iTunes.

---

### Post by warfacegod on 2010-01-15
> **baddog144 said:**
> No, not really. :(
I think it was possible with early firmwares, but these days you gotta have iTunes.

...and iTunes doesn't run in Wine.

---

### Post by baddog144 on 2010-01-15
> **warfacegod said:**
> ...and iTunes doesn't run in Wine.

No. It doesn't. :(

---

### Post by jerome schatten on 2010-01-16
> **warfacegod said:**
> ...and iTunes doesn't run in Wine.

iTunes runs OK on a virtual XP machine from VirtualBox.
jerome

---

### Post by warfacegod on 2010-01-16
> **jerome schatten said:**
> iTunes runs OK on a virtual XP machine from VirtualBox.
jerome

Well enough to sync up a Touch? Sounds like a lot of hassle.

---

### Post by baddog144 on 2010-01-16
> **warfacegod said:**
> Well enough to sync up a Touch? Sounds like a lot of hassle.
Yeah, Virtualbox has pretty good USB support and everything, so if you have access to a Windows install CD, you should be good.

---

### Post by jerome schatten on 2010-01-16
> **warfacegod said:**
> Well enough to sync up a Touch? Sounds like a lot of hassle.

It's a one time hassle with lots of side benefits besides managing your ipod. Your virtual machines are completely isolated from the host -- an environment for testing distros and ideas without bringing down your system if you do something foolish. The virtual machines you create can just be plugged into other machines running VB -- very handy.

Anyway, everything I tried on the virtual XP machine worked as it does under a native XP machine.  Don't download the Ubuntu VB packages with apt, but rather, go to the VirtualBox website and download their version and the guest additions. 

jerome

---

