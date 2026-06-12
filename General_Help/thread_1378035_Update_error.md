---
title: "Update error"
date: 2010-01-10
forum: General Help
---

### Post by seamles on 2010-01-10
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/Release.gpg](http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/Release.gpg)  
Failed to fetch [http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/main/i18n/Translation-en_US.bz2](http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/main/i18n/Translation-en_US.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.

Please help!

---

### Post by vinnywright on 2010-01-10
looks like you have strange stuff in your /etc/apt/sources.list ?

what did you add those lines for?

VINNY

---

### Post by michy99 on 2010-01-11
That repository may be down temporarily. Disable it and everything should be fine. Try enabling it again in a day or two to see if it works. If not, it may be down for good.

vinnywright: The same reason anyone adds repositories. To get stuff that isn't in the Ubuntu repositories.

---

### Post by vinnywright on 2010-01-11
> **michy99 said:**
> 

vinnywright: The same reason anyone adds repositories. To get stuff that isn't in the Ubuntu repositories.

a ya I was wandering what it was.

VINNY

---

