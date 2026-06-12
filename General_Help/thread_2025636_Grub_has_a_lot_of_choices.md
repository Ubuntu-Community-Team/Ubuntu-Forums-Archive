---
title: "Grub has a lot of choices"
date: 2012-07-14
forum: General Help
---

### Post by robtygart on 2012-07-14
I installed Ubuntu along side of Kubuntu, when Grub loads it has a lot of choices, but most are the same and take you into Kubuntu, and recovery mode for each one.  

Shouldn't there just be one set for each Ubuntu and Kubuntu?

---

### Post by ajgreeny on 2012-07-14
This old chestnut of a question is because each time a new numbered kernel is added in the normal update process it is added to the grub menu.

You probably therefore have several numbered kernels ending with the most recent, 3.2.0-26.  If you want to remove some of them it is easily done with grub-customiser, or by first installing **synaptic** (package manager) and then searching for all packages with the unwanted number string in their name and removing them.

I advise you to keep the most recent 3.2.0-26 and the one prior to that 3.2.0-25, as a fallback, just in case.

---

