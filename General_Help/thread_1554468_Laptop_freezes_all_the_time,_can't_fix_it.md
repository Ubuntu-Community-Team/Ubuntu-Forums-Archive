---
title: "Laptop freezes all the time, can't fix it"
date: 2010-08-16
forum: General Help
---

### Post by J-E-N-O-V-A on 2010-08-16
I'm dual-booting Vista and Ubuntu. Ubuntu freezes all the time, like every 5 mins so I don't ever use it. I just do a new installation every now and then to see if it fixes itself but it doesn't. It says that the battery has a low capacity, could this be the cause?

Strangely, it only freezes in Vista when I take out the charger, about at the same frequency as in Ubuntu.

Does anyone know what the problem could be and how I could identify it if it is a hardware issue?

---

### Post by wojox on 2010-08-16
It freezes as in you can't use the mouse or keyboard?

---

### Post by Quackers on 2010-08-16
What laptop do you have?

---

### Post by J-E-N-O-V-A on 2010-08-16
> **Quackers said:**
> What laptop do you have?
Asus X50SL.
> **wojox said:**
> It freezes as in you can't use the mouse or keyboard?
Yes.

---

### Post by wojox on 2010-08-16
Look in */var/log/messages* and you may see the problem. What graphics card/chip are you using?

```
lspci | grep VGA
```

---

