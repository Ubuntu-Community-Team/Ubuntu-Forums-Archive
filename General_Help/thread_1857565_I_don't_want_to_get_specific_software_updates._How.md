---
title: "I don't want to get specific software updates. How to set it?"
date: 2011-10-10
forum: General Help
---

### Post by vikash_chandola on 2011-10-10
I don't want to get updates for libre office. I use it very rarely. It's updates are also bigger than other updates. so what i should do to stop my ubuntu to stop taking Libre office updates.

---

### Post by TeoBigusGeekus on 2011-10-10
I think you can freeze the package in synaptic.

---

### Post by matt_symes on 2011-10-10
Hi

You need to pin the package (apt) or lock the version (synaptic).

What version of Ubuntu are you using ?

Kind regards

---

### Post by JRV on 2011-10-10
Search for it in synaptic.
Select it, then click on package and check the "Lock Version" box.

---

### Post by dcstar on 2011-10-11
> **JRV said:**
> Search for it in synaptic.
Select it, then click on package and check the "Lock Version" box.

And be aware that apt-upgrade does **not **respect Synaptic pinning, they use different databases.

---

