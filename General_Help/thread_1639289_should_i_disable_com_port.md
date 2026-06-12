---
title: "should i disable com port"
date: 2010-12-06
forum: General Help
---

### Post by carolinason on 2010-12-06
would there be any functionality issues from disabling the com port on my pc? it's just a header on the motherboard and since i do not use it, i thought of disabling it.

my concern was that perhaps gnu/linux might need a com port for internal operating functionality, sort of like a loopback.

thanks

---

### Post by carolinason on 2010-12-18
wow!

---

### Post by dcstar on 2010-12-18
> **carolinason said:**
> would there be any functionality issues from disabling the com port on my pc? it's just a header on the motherboard and since i do not use it, i thought of disabling it.
........

There is no point disabling it unless **you** are somehow getting confused and trying to use it.

---

### Post by efflandt on 2010-12-18
There is no benefit in disabling a com (serial) port unless it conflicts with something you are trying to do on another serial port.  But there is also no harm in disabling it if you are not using it.

---

### Post by carolinason on 2010-12-24
no, i am not confused. my intent was to find out if there was more to a com port than mere irq's and system resources in the context of ubuntu.

thanks efflandt!

---

### Post by QLee on 2010-12-24
[QUOTE=carolinason]no, i am not confused. my intent was to find out if there was more to a com port than mere irq's and system resources in the context of ubuntu.

thanks efflandt![/QUOTE]

Well, there could be. It could be used to run a serial console or for some kind of process control through a serial interface but since you are probably referring to a default Ubuntu install, then you have your answer because you don't seem to be using it for anything. Most, if not all, new hardware no longer includes a serial interface that extends to the case. I'd just disable it in the BIOS if I didn't need it.

---

