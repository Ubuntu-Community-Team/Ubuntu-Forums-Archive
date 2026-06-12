---
title: "swap slowing the system?"
date: 2011-07-02
forum: General Help
---

### Post by rng on 2011-07-02
From system monitor I noticed that swap starts getting used when RAM fills up by more than 50%. This slows the system due to frequent disk writing. Effectively the system is using only 50% of RAM available. 

Since I hardly need to hibernate the system, can I delete swap partition and/or disable swap by swapoff command? Will ubuntu work all right after that (if I ensure that I have adequate RAM for my programs)?

---

### Post by wolfen69 on 2011-07-02
Go [here]("https://help.ubuntu.com/community/SwapFaq") for info on swap. Go to the section on swappiness. You can change it to swap less.

---

### Post by rng on 2011-07-02
Thanks for the link. It confirms what I suspected: 

"The default setting in Ubuntu is swappiness=60. Reducing the default value of swappiness will probably improve overall performance for a typical Ubuntu desktop installation. A value of swappiness=10 is recommended, but feel free to experiment."

I will reduce the swappiness value and see.

---

