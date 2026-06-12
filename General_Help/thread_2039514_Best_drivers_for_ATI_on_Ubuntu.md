---
title: "Best drivers for ATI on Ubuntu?"
date: 2012-08-09
forum: General Help
---

### Post by Hungry Man on 2012-08-09
I don't know much about the drivers on Ubuntu. I don't want the closed source ATI drivers - they have an annoying overflow that would prevent them from booting on my kernel.

I don't actually know which ones I'm running know... but I'd like to.

I think there's radeon and then some other one.

---

### Post by 2F4U on 2012-08-09
If you don't have the proprietary ATI drivers installed (restricted drivers utility) you are most likely running the open source ATI driver. To be sure, you can look into /var/log/Xorg.0.log (this is the log file for the X server). This file contains a huge amount information.

---

### Post by Hungry Man on 2012-08-09
That file isn't super clear. I think based on that I'm using Radeon...

---

### Post by QIII on 2012-08-09
Post the results of 

```
lspci -nnk | grep -iA2 vga
```

At the end it will tell you what the kernel is using.

---

### Post by mastablasta on 2012-08-09
what version of ubuntu? what version of graphics card?

---

### Post by QIII on 2012-08-09
> **mastablasta said:**
> what version of ubuntu? what version of graphics card?

What kernel, too?

---

### Post by Hungry Man on 2012-08-09
Ubuntu 12.04 and I have an ATI Mobility 5650.

---

### Post by Hungry Man on 2012-08-09
> **QIII said:**
> What kernel, too?

3.5. Custom patched/ compiled.

---

### Post by QIII on 2012-08-09
There's a lot of patching going on right now to get the Catalyst 12.6 driver working with Quantal in testing right now.

I'm not bothering.  I'm waiting until the final Beta or the RC, which is when Canonical and AMD do their secret hand shake and high five to get the October ATI driver into the repo before it is released to the public.

That makes Phoronix grumble every time!

---

### Post by Hungry Man on 2012-08-09
That's all well and good but I can't use the closed source driver and I don't really want to use 12.10 yet.

I'm glad to hear that that's happening though.

---

### Post by QIII on 2012-08-09
> **Hungry Man said:**
> ... I don't really want to use 12.10 yet.

Oh, no.  Sorry.  Wasn't suggesting that.  

I have dedicated machines for all that horsing around.

---

