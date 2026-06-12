---
title: "An error occured, please run Package Manager from the rightlcick menu?"
date: 2011-05-03
forum: General Help
---

### Post by DryTowels on 2011-05-03
So there's this circle with a white line across it, and it tells gives me this message Error: BrokenCount > 0 This usually means your installed packages have unmet dependencies. Any help on removing this? Also im still a beginner to Ubuntu so a step by step guide would be helpful.

---

### Post by DogMatix on 2011-05-03
Try running the Synaptic Package Manager

---

### Post by DryTowels on 2011-05-03
> **DogMatix said:**
> Try running the Synaptic Package Manager


Says something about 1 broken thing. What now?

---

### Post by DogMatix on 2011-05-04
You could try running

```
sudo apt-get install -f
```

in the terminal.


Were you trying to install something when this happened or was it after an upgrade/update?

---

