---
title: "Ubuntu but Kubuntu Boot Screen"
date: 2011-04-10
forum: General Help
---

### Post by PsyclonJohn on 2011-04-10
Okay, so this isn't much of a problem at all, but more of a curiosity question. 

So, the other day I installed KDE Desktop Environment, and every time I turn my computer on it says I'm running Kubuntu 10.10. (Just wanted to try Kubuntu out)

Is there a way to make that say Ubuntu 10.10 again, if not, it's fine. 

Thanks,

John

---

### Post by Yellow Pasque on 2011-04-10
```
sudo update-alternatives --config default.plymouth
```
..or just remove plymouth-theme-kubuntu-logo and/or plymouth-theme-kubuntu-text

---

### Post by PsyclonJohn on 2011-04-13
Okay, so I ran the command and selected the number 2 for Ubuntu (as 0 and 1 were for Kubuntu) and I still have the Kubuntu screen in the beginning.

---

### Post by Yellow Pasque on 2011-04-13
Hmm. Maybe you need to run this before it takes effect:
```
sudo update-initramfs -u -k all
```

---

