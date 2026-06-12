---
title: "New application versions...???"
date: 2010-02-12
forum: General Help
---

### Post by robertcoulson on 2010-02-12
Hi
Can anyone tell me how to find out if there are newer version of applications to download in Ubuntu 9.10...???
I downloaded the newest version of OpenOffice ok.
Bob

---

### Post by x33a on 2010-02-12
Well If there are newer versions available in the repositories, then a simple update would install them.

```
sudo apt-get update && sudo apt-get upgrade
```

For other applications which aren't the latest version in the official repositories, you can try the ppa or manually download and compile the software.

---

### Post by robertcoulson on 2010-02-12
OK x33a...Done this...Does this mean any updates are done...???...Sorry for this stupid question.
Bob

---

### Post by x33a on 2010-02-12
Yes, as i said, if the updates are available through the official repos, then they should be installed after the above steps.

but if, for example, package X updates to a higher version, but the official repos contain the previous version, then the higher version won't be installed, unless you manually add a ppa containing the higher version, or manually download and compile the higher version of the package.

---

### Post by robertcoulson on 2010-02-12
OK...I will leave it as that...PPA and compiling are above me...Thanks very much.
Bob

---

