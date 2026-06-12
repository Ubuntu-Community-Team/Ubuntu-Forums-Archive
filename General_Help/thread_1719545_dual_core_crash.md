---
title: "dual core crash"
date: 2011-04-01
forum: General Help
---

### Post by dominoy2k1 on 2011-04-01
hello everyone. new user of ubuntu. liking it so far. i am having a small problem. i am running gigabyte GA-M68M-S2P and AMD sempron 2.7. the problem is when i try to run dual core. it will boot and run for 2mins then it crashes. single core runs perfect. any help will be appreciated.

---

### Post by cbowman57 on 2011-04-02
Not sure what version you are running but the first thing I would do is check for an updated bios.

---

### Post by 3rdalbum on 2011-04-02
How on earth do you change it from dual to single?

Sounds like a faulty CPU.

---

### Post by iponeverything on 2011-04-02
> **3rdalbum said:**
> How on earth do you change it from dual to single?

Sounds like a faulty CPU.

just use a non-smp kernel.

---

### Post by cbowman57 on 2011-04-02
Or pass nosmp to the kernel IIRC.

---

### Post by iponeverything on 2011-04-02
> **cbowman57 said:**
> Or pass nosmp to the kernel IIRC.

good to know. I didn't know about passing this at boot.

---

### Post by cbowman57 on 2011-04-02
It's also handy sometimes for single core processors that have a difficult time auto-detecting cores, I think there is also an smp=[number of cores] option as well.

---

