---
title: "NVidia MediaShield Raid 1 - Rebuild?"
date: 2010-02-08
forum: General Help
---

### Post by contecarli on 2010-02-08
One problem solved, the next one arises.

I've got a Zotac GeForce 9300 - ITX Mainboard with Nvidia Raid (MediaShield) and 2x320GB in RAID 1. I had to replace one hard disc and need to rebuild the raid, but I can't find a way to do this under Ubuntu (I don't use windows on that pc).

I've already set the array to rebuild in the MediaShield menu, which comes up while booting. Everything I found up until now tells me to start the MediaShield application in Windows, which I don't have here.

How can I rebuild the raid array?

Edit:
I came across the dmraid tool, but I just got an error when trying to rebuild:

```

$ sudo dmraid -R nvidia_beccfcac
Volume "nvidia_beccfcac" is not in rebuild state (current: 16)
Rebuild: cannot rebuild from current state!

```

---

