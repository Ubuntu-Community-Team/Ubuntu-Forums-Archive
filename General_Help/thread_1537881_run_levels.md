---
title: "run levels"
date: 2010-07-24
forum: General Help
---

### Post by viralmeme on 2010-07-24
I would like to run a script before X starts, where would it go in the RC levels ?

Lubuntu Lucid ..

---

### Post by prodigy_ on 2010-07-24
2-5. BTW, why don't you just use rc.local for that?

---

### Post by viralmeme on 2010-07-24
> **prodigy_ said:**
> 2-5. BTW, why don't you just use rc.local for that?
Doesn't rc.local run after X ?

---

### Post by prodigy_ on 2010-07-24
AFAIK rc.local is executed before X.

---

### Post by viralmeme on 2010-07-24
> **prodigy_ said:**
> AFAIK rc.local is executed before X.
Ah, so .. I'll give it a try ..

---

### Post by sisco311 on 2010-07-24
> **prodigy_ said:**
> AFAIK rc.local is executed before X.

nope, rc.local is executed at the end of any multi-user runlevel.

@OP. 

Ubuntu uses Upstart, runleveles are still emulated, but Upstart is event based and asynchronous. 

lxdm is tarted by an Upstart job (etc/init/lxdm.conf). 

Could you please elaborate what are you trying to accomplish?

---

### Post by viralmeme on 2010-07-27
> **sisco311 said:**
> Could you please elaborate what are you trying to accomplish?
I am using a portable Lubuntu on a USB device, I want to create a script that will (when running the USB on my home computer) mount two partitions from the local system, as /archive and /tmp.

---

