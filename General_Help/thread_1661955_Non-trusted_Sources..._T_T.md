---
title: "Non-trusted Sources... T_T"
date: 2011-01-07
forum: General Help
---

### Post by whoisatlas on 2011-01-07
Whenever I try to either update, or install new software to Ubuntu 10.10, I get this error...

Requires Installation of Untrusted Packages
The action would require the installation of packages from not authenticated sources.

What the heck is this crap, and how do I fix it?

Thanks!

---

### Post by endotherm on 2011-01-07
you have at some point most likely, added an unauthenticated PPA repository, and installed software from it. now there is an update to that software published, so your system wants to install the update, but it requires packages from the unauthenticated repo. 

do you have any PPAs showing in System->Administration ->SoftwareSources -> Other Software? one of these entires is likely the culprit. 

I stopped using AWN a few years ago, because the PPA from which it was available, was unauthenticated, and it updated very often.

---

### Post by whoisatlas on 2011-01-07
Hrmmm, I love how when I go to check and see if it will work, it works. Thanks for your help anyhow! :D

---

