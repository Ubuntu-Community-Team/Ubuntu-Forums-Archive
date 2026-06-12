---
title: "How do you see what drivers your system is using?"
date: 2010-09-04
forum: General Help
---

### Post by RCXtest on 2010-09-04
In 10.04.

---

### Post by pbrane on 2010-09-04
type **lsmod** in a terminal.

---

### Post by RCXtest on 2010-09-04
Thanks.

Looking thru the generated list, I see an "ati_agp". Why would there be agp support on my system, I have no agp cards.

Anyway, I also seem to not have a video driver of any sort installed. How is my display working?

---

### Post by pbrane on 2010-09-05
do you see **fglrx** or **radeon** modules?
```

lsmod | grep "radeon\|fglrx"

```

ati_agp needs to be loaded before either of those two modules. I think the agp module supports system RAM use by the GPU. the maximum system RAM usable by the GPU is called the AGP Aperture.

---

### Post by RCXtest on 2010-09-05
No, neither of those modules.

Problem I am having is I cannot install a video driver. Since some recent update.

---

### Post by pbrane on 2010-09-06
you must be using a vesa or vga driver, gotta be running something to use your video card. I'm not familiar with the ATI/Radeon driver install. Can you post what you have done, any error messages and what card you have? Maybe some one has a solution.

---

