---
title: "Upgrading packets: Downloading but not installing just yet"
date: 2010-01-25
forum: General Help
---

### Post by justinstrack on 2010-01-25
If I were to download items from the Synaptic Packet Manager, download only not install, how would I then install them later? Where will the files be located?

---

### Post by 3rdalbum on 2010-01-25
/var/cache/apt/archives is where they are located.

By default, Synaptic and apt-get will use archived packages if they are available, rather than downloading them again from the web. So just doing 'sudo apt-get install' or installing them in Synaptic will do the trick.

---

### Post by justinstrack on 2010-01-25
O Okay thanks, How would I execute the package?

---

