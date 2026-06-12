---
title: "Synaptic Package Manager broken =["
date: 2011-12-29
forum: General Help
---

### Post by xfearxnxloathing on 2011-12-29
> E: The package indicator-displex needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

O_o what do i do to fix this?

---

### Post by samigina on 2011-12-29
Try with:

> sudo dpkg --remove --force-depends --force-remove-reinstreq indicator-displex

If it fails remove all files beginning with your package name from /var/lib/dpkg/info/ and the try again.

---

### Post by xfearxnxloathing on 2011-12-29
> **samigina said:**
> Try with:



If it fails remove all files beginning with your package name from /var/lib/dpkg/info/ and the try again.

how do i know the package name?  i think skype is what is broken.

---

### Post by samigina on 2011-12-29
> E: The package **indicator-displex** needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Reading the error message tell us that "indicator-displex" is the package with problems.

---

### Post by xfearxnxloathing on 2011-12-29
> **samigina said:**
> Reading the error message tell us that "indicator-displex" is the package with problems.

oh ok, sry haha 

well this fixed my problem, thank you all for the help!! =D

---

