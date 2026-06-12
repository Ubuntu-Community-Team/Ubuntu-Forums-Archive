---
title: "a list of .debs installed with dpkg?"
date: 2006-04-24
forum: General Help
---

### Post by jms830 on 2006-04-24
is there any way to get a list of .deb files that i have installed with dpkg (not ones installed using apt-get)? Because I think I want to remove some of them that I installed early on in my ubuntu experience.

---

### Post by garba on 2006-04-24
apt-get is just a fronted to dpkg, it's dpkg which takes care of actually decompressing the packages and setting them up (i.e. running the setup scripts)... all apt does is keeping in sync with a central repository, resolving dependencies, and calling dpkg multiple times... hope this helps clarify it a little for you ;)

---

### Post by Hairy_Palms on 2006-04-24
in synaptic, thiers a section called "local or obsolete" that shows only debs installed with dpkg or from obsolete repositorys.

---

### Post by adamkane on 2006-04-24
synaptic -> status -> install (local or obsolete)

---

