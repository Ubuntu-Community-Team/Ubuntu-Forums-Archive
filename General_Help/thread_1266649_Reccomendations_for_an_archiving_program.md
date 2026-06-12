---
title: "Reccomendations for an archiving program?"
date: 2009-09-14
forum: General Help
---

### Post by Vunutus on 2009-09-14
I've been using Ark since my switch to KDE, and am rather disappointed in it (and other linux archival programs). Specifically, it falls flat on its face when dealing with large (500MB plus) RAR archives, and doesn't seem to handle multi-part archives at all.

Does anyone have any recommendations for me? I used to use WinRAR back in my Windows days and it seemed to handle virtually any archiving scenario with no problem.

---

### Post by Vunutus on 2009-09-16
Bump

---

### Post by Ms_Angel_D on 2009-09-16
you can install winrar in wine....

---

### Post by Vunutus on 2009-09-16
But I'm looking for a Linux program, not a way to run a Windows program :P

---

### Post by Ms_Angel_D on 2009-09-16
the only program that I know which makes multi-part rar files is winrar

---

### Post by Vunutus on 2009-09-29
So nobody knows of a Linux program that has better support for RARs? WinRAR is really a pain to use since running it in Wine doesn't give drag and drop compatibility so I have to use the clunky dialogs.

---

### Post by FunkyRes on 2009-09-29
What are you trying to do?

If you are trying to create archives, use tar.
You can split tar archives up using a program called split. You can rejoin them using cat.

split is command line but works extremely well.

If you are looking to open rar archives, there is a linux unrar. I think it is in multiverse.

---

