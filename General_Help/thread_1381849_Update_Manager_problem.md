---
title: "Update Manager problem"
date: 2010-01-15
forum: General Help
---

### Post by OctaFish on 2010-01-15
Every time I do an upgrade, i get the following message:

[FONT="Courier New"]W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_non-free_binary-i386_Packages)[/FONT]


the upgrade seems to go ok, but afterwards it informs me that system was last updated 40 od days ago.

any help appreciated, preferably step by step idiot proof....

---

### Post by drs305 on 2010-01-15
It appears you have two identical entries for medibuntu. You will want to remove one of the two duplicate lines and you can do it via Synaptic.

Open Synaptic or Software Sources, Settings, Repositories, Third Party/Other Software tab. See if you have identical entries. If so, untick one of them. You may have two identical sets (free and nonfree) - in this case untick one of each.

After you have made the changes, on the main Synaptic menu press "Reload".

---

