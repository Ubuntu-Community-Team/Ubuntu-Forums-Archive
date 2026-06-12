---
title: "Unable to open Synaptic Package manager"
date: 2010-05-31
forum: General Help
---

### Post by nitts5841 on 2010-05-31
Hi 

I am unable to open my newly installed ubuntu 9.10 (karmic-koala) asv it is showing some error message which is as follows: 

 E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/bisigi-ppa-karmic.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

If anyone has a remedy for this, i will open my Synaptic Package manager.

With regards,

NITTS5841

---

### Post by cogier on 2010-05-31
Can you get to **System>Administration>Software Sources**? Click on the **Other** tab and if there is a line there with **bisigi** in it either try and fix the problem or delete it. From what I can see it refers to themes so should not be too critical.

---

### Post by nitts5841 on 2010-05-31
Hi 
But still its not working as per the instructions directed by you.
And i didn't find any line with **bisigi** in it.
So please help me so thatmy synaptic package manager may work properly.

With Regards,
NITTS5841

---

### Post by oldos2er on 2010-05-31
Can you copy and paste the output from ```
cat /etc/apt/sources.list.d/bisigi-ppa-karmic.list
```

---

### Post by nitts5841 on 2010-06-01
Where should i copy that output.
and wats this code actually significe.

with regards,
NITTS5841

---

### Post by dino99 on 2010-06-01
> **nitts5841 said:**
> Where should i copy that output.[COLOR="Red"]from a terminal: apps terminal[/COLOR]
and wats this code actually significe.

with regards,
NITTS5841

open a terminal

---

