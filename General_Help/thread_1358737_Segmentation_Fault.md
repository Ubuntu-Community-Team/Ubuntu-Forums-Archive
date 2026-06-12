---
title: "Segmentation Fault?"
date: 2009-12-18
forum: General Help
---

### Post by Pnkmaggt on 2009-12-18
I am having trouble starting my synpatic package manager i keep getting this

pnkmaggt@L1f3bl00d-1:~$ sudo synaptic package manager
[sudo] password for pnkmaggt: 
Segmentation fault


any thoughts?

Sorry - forgot to say - Running Ubuntu 9.1 on a Dell Latitude D820.

---

### Post by 3Miro on 2009-12-18
Try 

```

gksudo synaptic

```

sudo is for console apps only, you should use gksudo for graphical ones.

---

### Post by Pnkmaggt on 2009-12-18
now my terminal doesn't even say anything is wrong is just closes the package manager before anything even comes up.

---

### Post by RMXH on 2009-12-18
Hi. Have you updated your system recently? If so, check that all updates have finished successfully as incomplete updates to the system may cause this error.

---

### Post by Pnkmaggt on 2009-12-18
ok so I updated my system as far as i could go and gave it the old reboot and now it works - ty

---

