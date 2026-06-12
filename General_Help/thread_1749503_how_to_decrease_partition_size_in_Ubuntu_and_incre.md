---
title: "how to decrease partition size in Ubuntu and increase it in XP?"
date: 2011-05-04
forum: General Help
---

### Post by 666pluto on 2011-05-04
currently, I have on internal HDD 160GB in size. 20GB are for windows XP partition and the rest is assigned for ubuntu partition(s?). i want to make it now more equal in size, but how can i do that? I'm using ubuntu 11.04...

---

### Post by 666pluto on 2011-05-06
anyone?

---

### Post by imigueldiaz on 2011-05-06
> **666pluto said:**
> anyone?

Try to use gparted, but **be very careful, or you can loose your data**

Search any guide on internet before to use it ;)

Best

---

### Post by Sidewinder1 on 2011-05-06
If you're going to resize the windows partition in gparted or any other partition tool, *before* performing that operation, make sure you defragment the NTFS partition, at least twice. Be advised that depending on how much data is there it could take a long time to defrag. Also make back-ups of your important data (pictures, movies, music, etc.) prior to doing any of the above.

HTH,
Side

---

