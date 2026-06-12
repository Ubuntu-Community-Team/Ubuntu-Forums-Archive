---
title: "question on hardware sensors monitor"
date: 2010-05-09
forum: General Help
---

### Post by doll99hk on 2010-05-09
i have added the hardware sensors monitor to the panel and enabled....but i can only enabled my hardisk temp(i.e. hddtemp)...but there is no option of cpu.....how can i enable my cpu temp??

---

### Post by dcstar on 2010-05-10
> **doll99hk said:**
> i have added the hardware sensors monitor to the panel and enabled....but i can only enabled my hardisk temp(i.e. hddtemp)...but there is no option of cpu.....how can i enable my cpu temp??

```
man sensors
```

---

### Post by dino99 on 2010-05-10
sensors-detect

---

### Post by doll99hk on 2010-05-10
> **dino99 said:**
> sensors-detect

i have type sudo sensors-detect in the terminal and answer 'yes' for all the questions but i still can't enable my cpu temp sensor....

---

### Post by Dilutu on 2010-05-10
The only way for me to get my sensors working was to add GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax" to  etc/default/grub
Th.

---

### Post by XCan on 2010-05-10
Which CPU do you have? Maybe you're unlucky enough that sensors does not support it?

---

