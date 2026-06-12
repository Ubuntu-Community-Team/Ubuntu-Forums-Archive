---
title: "Will increasing swappiness increase  the speed ?"
date: 2010-07-04
forum: General Help
---

### Post by kimikrishna on 2010-07-04
If i increase swappiness using this : [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

will it increase the speed of my ubuntu ?

---

### Post by davidmohammed on 2010-07-04
marginally - however the real answer is the machine that you are running on - what are the specifications i.e. processor, ram, graphics card?

---

### Post by philinux on 2010-07-04
> **kimikrishna said:**
> If i increase swappiness using this : [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

will it increase the speed of my ubuntu ?

You mean reduce swappiness.

---

### Post by Mr Nemo on 2010-07-04
Do you want to change the swappiness or the actual swap space?

---

### Post by Revolutionary101 on 2010-07-04
You will see an increase in speed if you decrease swappiness, if you have a computer that is using a high % of its RAM. My computer has 1 GB of RAM installed and it would see a huge difference in speed by decreasing the swappiness. The more RAM you have the less it has to access the swap partition, so by decreasing the priority of using your swap on a computer with 4 GB+ RAM installed, you wouldn't see much of a performance change.

It all depends on how much RAM you have installed.

---

### Post by kimikrishna on 2010-07-04
I have 1 Gb ram, And dual core processor with 3 Ghz frequency.

---

### Post by v1ad on 2010-07-04
this is nice to know, i have 6 gigs of ram so i set it to 10.

and kimikrishna leave it at default. u need the swap, if you only have 1 gb of ram.

---

### Post by philinux on 2010-07-04
> **kimikrishna said:**
> I have 1 Gb ram, And dual core processor with 3 Ghz frequency.

Run this in a terminal and post back the result. Please use the code tags. Apps>access

```
free -m
```

---

### Post by kimikrishna on 2010-07-04
```
 total       used       free     shared    buffers     cached
Mem:           992        896         95          0        160        412
-/+ buffers/cache:        323        668
Swap:         1623          0       1623

```

ONly a browser was running when i ran free -m.

---

