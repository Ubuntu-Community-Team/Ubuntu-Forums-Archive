---
title: "Problem with DVD buring"
date: 2009-11-23
forum: General Help
---

### Post by Warthaug on 2009-11-23
I recently upgraded my wife's computer to 9.10; 32-bit.  Brasero will burn disks fine, but us extremely slow in doing so.  I prefer k3b, so I installed it - and it cannot even detect the DVD recorder; whether or not there is a blank DVD in it.

My Wife's computer dates to before we met, so I have few details.  Its an Acer brand, dual-core system with ~1GB ram.  The DVD burner itself is LG, although I have no idea what model it is.

Any idea what is going on, and how to go about fixing it?

thanx

Bryan

---

### Post by hwttdz on 2009-11-23
Have you run k3bsetup?

---

### Post by Walialu on 2009-11-23
Confirmed!

Same happened to me after updating, so I switched to gnomebaker.

```
sudo apt-get install gnomebaker
```

works like a charm :D

---

### Post by Warthaug on 2009-11-23
> **hwttdz said:**
> Have you run k3bsetup?

No, I did not.  Running it fixed the problem.

Thanx!

Bryan

---

