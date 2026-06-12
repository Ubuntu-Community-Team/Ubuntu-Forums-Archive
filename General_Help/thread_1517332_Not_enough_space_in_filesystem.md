---
title: "Not enough space in filesystem?"
date: 2010-06-24
forum: General Help
---

### Post by TheAnomalyCoder on 2010-06-24
I was happily browsing my new Linux Ubuntu Distribution, and a warning message popped up stating that there's about 145 megs in FIle System. Anyone have any idea how to solve this problem other than removing files? :KS

---

### Post by mörgæs on 2010-06-26
Hi, welcome to the forum.


145 MB free? That is critical. You should not let your disk get so full on any operative system. 


You can try removing cached packages with

```
sudo apt-get clean
```After that, please post the output of ```
df
```

---

### Post by TheAnomalyCoder on 2010-06-26
> **mörgæs said:**
> Hi, welcome to the forum.


145 MB free? That is critical. You should not let your disk get so full on any operative system. 


You can try removing cached packages with

```
sudo apt-get clean
```After that, please post the output of ```
df
```
Thanks for the suggestion, but I was dual booting with windows and I didn't except it to fill up so fast. I removed windows today and replaced it with Ubuntu.

---

