---
title: "CPU frequency scaling unsupported"
date: 2009-08-15
forum: General Help
---

### Post by permant on 2009-08-15
Hi everyone:
I want to scaling CPU frequency ,but there is an error.


CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

so what can I do ??
thank you for your suggestion!

---

### Post by coldReactive on 2009-08-15
What is your processor brand (AMD, Intel) and model?

---

### Post by SoftwareExplorer on 2009-08-15
There's the possibility that Linux just plain doesn't support processor scaling with that CPU. For example, my old Intel P4 single thread processor doesn't support it, but my Intel C2Q one does an does my AMD Athlon X2. So it really depends on what processor you have, though it seems that newer processors are better supported in this aspect.

---

### Post by Finalfantasykid on 2009-08-16
If you do have a newer cpu, try going into your BIOS to see if scaling is enabled.

---

### Post by SoftwareExplorer on 2009-08-16
> **Finalfantasykid said:**
> If you do have a newer cpu, try going into your BIOS to see if scaling is enabled.
That's interesting, I never knew the BIOS had control over that, but it makes sense now that I think about it. What is the option usually called?

---

### Post by coldReactive on 2009-08-16
> **SoftwareExplorer said:**
> That's interesting, I never knew the BIOS had control over that, but it makes sense now that I think about it. What is the option usually called?

Frequency Scaling, CPU Scaling, CPU Frequency Scaling.

My BIOS has this setting too.

---

### Post by SoftwareExplorer on 2009-08-16
Two of my BIOS don't, one does. I guess I learn something new every day.

---

