---
title: "system locks up on restart"
date: 2011-02-02
forum: General Help
---

### Post by garyed on 2011-02-02
I just installed Ubuntu 10.04 on my old Toshiba Satellite laptop.
I'm dual booting with another Linux distro - ZenMini Everything works O.K. running Ubuntu but I can't restart the system with out it locking up. I have to power down completely from Ubuntu. I don't have any problem restarting with ZenMini so its obviously an Ubuntu problem. 
Anyone have any ideas?

---

### Post by garyed on 2011-02-05
Bbbbbbbbump

---

### Post by dino99 on 2011-02-05
into synaptic check that the tosh packages are installed

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by garyed on 2011-02-06
> **dino99 said:**
> into synaptic check that the tosh packages are installed

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

Thanks for the tip.
I had one of the two packages already installed so I installed the other one too.
It didn't help though.

---

