---
title: "Wifi disconnecting all the time on laptop"
date: 2012-03-19
forum: General Help
---

### Post by jesushero on 2012-03-19
I am using a Toshiba Satellite laptop with Ubuntu 10.04. The wifi worked on its own as soon as I installed. With most wifi networks, it works perfect. With one that I need to use a lot, it keeps on disconnecting every few minutes, and then is unable to connect again until the wifi card gets a hard reset (radio killswitch). I thought it must have been a problem with the router, until today when this friend brought his older, Windows XP laptop next to mine, and on his system, the wifi connected immediately and never disconnected. 

So obviously the problem is on my system, either the software side or the hardware side. Which is most likely and how do I solve it? Why would this only be a problem with one specific network?

---

### Post by Mark Phelps on 2012-03-19
> **jesushero said:**
> So obviously the problem is on my system, either the software side or the hardware side. 
Most probably, the hardware -- the WiFi chip in your laptop.

> Why would this only be a problem with one specific network? It wouldn't -- but it could be a problem with one laptop. Not all WiFi chips are the same, and they don't use the same drivers -- which is why one laptop might work very well, and another laptop (using the same wireless network) might work very poorly.

I even have a problem at home where an "older" laptop, using a "G" connection works great, while a newer one, using an "N" connection, gets a poor signal and has disconnects.  And, yes, I have my wireless router setup to handle both G and N.

---

### Post by jesushero on 2012-03-19
Hmmm.. Makes sense.. But is there anything I can do about it? Or do I just live with it?

---

### Post by Mark Phelps on 2012-03-20
> **jesushero said:**
> Hmmm.. Makes sense.. But is there anything I can do about it? Or do I just live with it?

If you're willing to experiment ...

In Linux, drivers are bound to the kernel such that newer kernel versions, when included in distros, often come paired with newer drivers versions.

That said, I would download and burn a CD of Ubuntu 11.10 and a bootable USB of 12.04 -- and try each of them.  See if the wireless then works in either, and if it stops disconnecting.

---

### Post by coldjeanz on 2012-03-20
Mine does the same thing however it ONLY does it at my house. I use a wired connection at home so it doesn't really bother me however it will keep saying my wireless network has been disconnected and it will keep popping up until I turn off the little switch on the side of my computer to disable the wifi. But if I'm using it at school (the wifi) it doesn't have this problem.

Not sure if we have the same problem though.

---

### Post by jesushero on 2012-03-21
> **Mark Phelps said:**
> If you're willing to experiment ...

In Linux, drivers are bound to the kernel such that newer kernel versions, when included in distros, often come paired with newer drivers versions.

That said, I would download and burn a CD of Ubuntu 11.10 and a bootable USB of 12.04 -- and try each of them.  See if the wireless then works in either, and if it stops disconnecting.


Thanks, hadn't though of that! So, if newer kernels/drivers fix it, would this be considered a Kernel bug on 10.04?

---

### Post by Mark Phelps on 2012-03-21
> **jesushero said:**
> Thanks, hadn't though of that! So, if newer kernels/drivers fix it, would this be considered a Kernel bug on 10.04?

NO, because it would be a driver problem, not a kernel problem.

It's just that the drivers run in kernel space, so they have to be "bound" to the kernel.

---

