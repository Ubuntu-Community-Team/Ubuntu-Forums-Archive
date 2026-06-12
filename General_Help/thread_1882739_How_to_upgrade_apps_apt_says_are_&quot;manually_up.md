---
title: "How to upgrade apps apt says are &quot;manually upgradeable&quot;?"
date: 2011-11-17
forum: General Help
---

### Post by KeithLM on 2011-11-17
I'm running 11.10 right now and if I run apt-show-versions I see that there are a few apps that are listed as being manually upgradeable. What does this mean and how do I do it?  Here's an example:
```

libgdata-common/oneiric *manually* upgradeable from 0.9.1-0ubuntu2 to 0.10.1-1~oneiric1
libgdata13/oneiric *manually* upgradeable from 0.9.1-0ubuntu2 to 0.10.1-1~oneiric1

```

apt-get install and --reinstall do nothing with these.  -f is meaningless too.

---

### Post by raja.genupula on 2011-11-17
look for them in synaptic and install from there.

---

### Post by KeithLM on 2011-11-17
I'd really like to handle this from the command line if at all possible.

---

### Post by raja.genupula on 2011-11-18
```
sudo apt-get install --reinstall <app name>
```

it will make the upgrades to specific packages . 
all the best

---

### Post by KeithLM on 2011-11-18
As I said, that didn't work.  It just reinstalls the existing version.

---

