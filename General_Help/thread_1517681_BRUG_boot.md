---
title: "BRUG boot"
date: 2010-06-25
forum: General Help
---

### Post by cap10Ibraim on 2010-06-25
I edited the following entries in the burg file 
GRUB_DEFAULT=6
GRUB_TIMEOUT=5
and saved the file but the next time I booted nothing changed ?!

---

### Post by tom.swartz07 on 2010-06-25
> **cap10Ibraim said:**
> I edited the following entries in the burg file 
GRUB_DEFAULT=6
GRUB_TIMEOUT=5
and saved the file but the next time I booted nothing changed ?!

You probs didnt update it. ```
sudo update-burg
``` and try it again

---

### Post by MedianMajik on 2010-06-25
Could you please give more details of what you are trying to do and how your system is laid out

---

### Post by KeyserSoze93 on 2010-06-25
BURG? Do you mean BURG, BRUG or GRUB. I assume you mean GRUB, because your config file says GRUB.

Just checking...

---

### Post by cap10Ibraim on 2010-06-25
> **tom.swartz07 said:**
> You probs didnt update it. ```
sudo update-burg
``` and try it again
Thanks that solved the problem
> **KeyserSoze93 said:**
> BURG? Do you mean BURG, BRUG or GRUB. I assume you mean GRUB, because your config file says GRUB.

Just checking...
It's BRUG

---

