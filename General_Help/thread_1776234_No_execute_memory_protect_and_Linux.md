---
title: "No execute memory protect and Linux"
date: 2011-06-05
forum: General Help
---

### Post by vehemoth on 2011-06-05
Do you need this BIOS setting enabled, does it have any advantages or disadvantages to it. My understanding is that it is to provent malware, but on a linux only system does iit hinder more than help?

---

### Post by wolfen69 on 2011-06-05
Since there is little to no malware for linux to begin with, I would just leave it alone and not worry about it. And even if there were viruses for linux, it is considerably more difficult for linux to actually get a virus.

---

### Post by papibe on 2011-06-05
It will be better (more safe) to activate that BIOS option, since Ubuntu (and I believe all distros using a recent kernel) can fully utilize those features.

I think when off, Linux do a partial emulation to behave as that option is enabled (at least on the pae kernel). More info [here]("https://wiki.ubuntu.com/Security/CPUFeatures").

I have run servers with both the setting on and off, with no significant difference. But I'm talking about Home servers here, so not in the line of fire, if you know what I mean.

Hope it helps.

---

