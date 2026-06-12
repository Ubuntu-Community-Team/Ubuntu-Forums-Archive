---
title: "Time won't stay."
date: 2010-06-10
forum: General Help
---

### Post by Thatguyi445 on 2010-06-10
Everytime I boot up my computer the clock is 3 hours behind. I have Ubuntu 10.04 LTS and had it on another computer and never had this problem before.

---

### Post by KeyserSoze93 on 2010-06-10
Set the clock right and then run:

```

sudo hwclock --systohc

```

This should set the BIOS clock to the OS time, which should then allow the system to pick the correct time back up when it boots.

---

### Post by Thatguyi445 on 2010-06-10
Thank you.

---

### Post by AstroLlama on 2010-06-21
Simple question, simple answer. The perfect thread. (too bad I ruined it)

---

