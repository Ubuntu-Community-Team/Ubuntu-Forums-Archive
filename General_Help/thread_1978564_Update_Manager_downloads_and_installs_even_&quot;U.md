---
title: "Update Manager downloads and installs even &quot;UNSELECTED&quot; updates"
date: 2012-05-12
forum: General Help
---

### Post by kanishkdudeja on 2012-05-12
Even if i dont select some of the updates in update manager, still when i click on "install", it downloads and installs them.

How can this be resolved? This is really buggy.

---

### Post by carl4926 on 2012-05-12
They may be being pulled in by dependency?

---

### Post by kanishkdudeja on 2012-05-12
Doesnt look like it. I unselected all the Libre Office Updates. And the rest for the updates dont depend on libre office packages. Still, all Libre Office updates got downloaded and installed. 

This is not the first time im seeing such behaviour. It happens quite a lot.

---

### Post by carl4926 on 2012-05-12
I'll take note of this next time and see

---

### Post by kanishkdudeja on 2012-05-12
Thanks :)

---

### Post by kanishkdudeja on 2012-05-18
Bump.

---

### Post by Frogs Hair on 2012-05-18
You can lock versions of packages from the synaptic package manager . Select the package and choose lock version from the package tab. I haven't had problems with unselected packages, but it may be due to needed dependencies as mentioned. I upgrade all packages unless I receive a partial upgrade which can happen if using PPAS or proposed updates.

---

