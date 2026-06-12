---
title: "Local &amp; Obsolete packages in symaptic"
date: 2009-09-25
forum: General Help
---

### Post by sports fan Matt on 2009-09-25
Are they uninstalled packages, installed?  Are they safe to uninstall?  Im not sure what these packages actually mean.

---

### Post by CatKiller on 2009-09-25
They are installed packages that aren't in the current repository index. They might have been installed locally (from .deb files) or from a repository that you no longer have in your sources.list, or they may have been removed from the repository because they are obsolete. Whether you want to uninstall them or not really depends on whether you use them or not.

---

### Post by Ron W on 2010-03-04
Hello

I'm very interested in what you say because I have a long list of files like the following list mentioned in the Synaptic Package Manager's 'Installed (local or obsolete):

linux-headers-2.6.24-18
linux-headers-2.6.24-18-generic
linux-image-2.6.24-18-generic

with the last two digits ranging from 14 to 23.

I currently have Kernel Linux 2.6.24-26-generic loaded (according to System->Administration->System Monitor) [I'm using 8.04 LTS].

I'm hesitating in removing them because I  assume that the Synaptic Package Manager would remove these when doing the upgrades. My suspicion is that these are still needed for later versions and removing them would cause a few problems to say the least.

Am I safe to either 'Remove' or 'Completely Remove'?

Thanks

Ron

---

