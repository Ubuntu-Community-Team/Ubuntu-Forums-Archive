---
title: "HDD Health Check"
date: 2009-11-07
forum: General Help
---

### Post by Vigh on 2009-11-07
Hi is there a way I can check the health of my HDD in Ubuntu? It seems to be a bit noisier than usual.

---

### Post by kkady32 on 2009-11-07
can try smartmounttools and smart-notifier,u findet in synaptic,but u must see when in BIOS u have S.M.A.R.T enabled.
or in Sistem>Administration>Disk Utility

---

### Post by P4man on 2009-11-07
If you're using Karmic, then go system > administration > disk utility
Make sure S.M.A.R.T. is enabled in the BIOS. That program is known to have a bug, if you see an error about a negative or extremely high relocated sector count, you can safely ignore it.

---

