---
title: "saying I have only 25gb on a 200gb partition"
date: 2010-07-30
forum: General Help
---

### Post by pagey94 on 2010-07-30
I open Home from 'places', and at the bottom it says i have (now) 15gb free... but my partition is 200gb and even when i first installed ubuntu, it was 25gb, and im sure that this is something to do with ubuntu, because there is NOTHING else on this drive

---

### Post by ajgreeny on 2010-07-30
Have a look with **Applications ->Accessories ->Disk Usage Analyser** and see if you can figure out which folder is using all your space in home

---

### Post by anglican on 2010-07-30
> **pagey94 said:**
> I open Home from 'places', and at the bottom it says i have (now) 15gb free... but my partition is 200gb and even when i first installed ubuntu, it was 25gb, and im sure that this is something to do with ubuntu, because there is NOTHING else on this driveWhat does:
```
sudo parted -l
```
have to say about your disk(s)?

H

---

