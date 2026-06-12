---
title: "Cannot view files from HFS+ partitions (permissions issue)"
date: 2010-06-08
forum: General Help
---

### Post by chemicalrubber on 2010-06-08
I have a dual boot system with Lucid and Leopard. The files in the Documents folder and all the other user folders are unreadable from Lucid after mounting the HFS+ partition. The Users folder is accessible, then after going into my username folder most of the folders have an "X" in the bottom right corner and I can't open them. Except, the Public folder. What permission settings should I be using in this case?

---

### Post by TheStroj on 2010-06-08
Have you tried exploring those folders from terminal? If not, try making yourself root (run 'sudo su') and navigating to them ('cd where/ever/it/is').

---

