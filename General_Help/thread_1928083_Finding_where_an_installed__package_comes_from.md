---
title: "Finding where an installed  package comes from"
date: 2012-02-19
forum: General Help
---

### Post by ofnuts on 2012-02-19
Is there a way to determine from which repository a given package has been obtained for installation? Or if it was installed from a .deb downloaded directly?

---

### Post by oldos2er on 2012-02-19
In Synaptic use the Origin tab. Also ```
dpkg-query -W <package name>
```

---

### Post by 3Miro on 2012-02-19
Install the Synaptic Package Manager and from there you can view properties about each individual package. You can see the maintainer and from "section" you can see things like "non-free" or "multiverse" and so on.

---

### Post by ofnuts on 2012-02-19
> **oldos2er said:**
> In Synaptic use the Origin tab. Also ```
dpkg-query -W <package name>
```Thanks for the command. However $Origin is empty for many packages (gimp/gcc); $Section says graphics/devel for same.

---

### Post by ofnuts on 2012-02-19
> **3Miro said:**
> Install the Synaptic Package Manager and from there you can view properties about each individual package. You can see the maintainer and from "section" you can see things like "non-free" or "multiverse" and so on.
If Synaptic can display it, then either it is already on my system and I can find it without Synaptic, or Synaptic manages it directly and then it won't have the information for already installed packages?

---

### Post by oldos2er on 2012-02-19
Maybe ```
apt-cache policy <package>
``` ?

---

### Post by ofnuts on 2012-02-19
> **oldos2er said:**
> Maybe ```
apt-cache policy <package>
``` ?
Bingo!

---

### Post by oldos2er on 2012-02-19
Cool.

---

