---
title: "Generic Graphics drivers"
date: 2010-08-25
forum: General Help
---

### Post by Nathan.Flow on 2010-08-25
Hello all, I'm looking for some suggestions, and options.
I'm trying to build a live cd, and would like to know what video drivers work with both ATI, and Nvdia.

My current live cd installs the nvdia drivers, but the system I'm using it on has an ATI card. I don't get it. I also can't figure out How I broke the run in safe graphics mode option, but it's no longer available. 

Thanks in advance.

---

### Post by dv3500ea on 2010-08-25
Don't include hardware drivers on the live CD (especially not the proprietary ones because that would be (probably) illegal).

Instead, install graphics drivers from System -> Administration -> Hardware Drivers on each installation.

---

### Post by Nathan.Flow on 2010-08-25
Some how it's getting them form the internet. I don't know what I or how I did that, but I'm trying to fix it. Do you know of a driver that works for both nvidia, and ati?

---

### Post by Mark Phelps on 2010-08-26
> **Nathan.Flow said:**
> So you know of a driver that works for both nvidia, and ati?

There's no such driver.  What you call the "generic" drivers are really the open-source drivers, and they are available through Synaptic.

---

