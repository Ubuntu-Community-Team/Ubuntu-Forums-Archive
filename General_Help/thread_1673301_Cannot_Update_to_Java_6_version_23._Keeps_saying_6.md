---
title: "Cannot Update to Java 6 version 23. Keeps saying 6.22 is latest version."
date: 2011-01-22
forum: General Help
---

### Post by BestUsername2222 on 2011-01-22
Wtf?
I tried apt-get update then apt-get install sun-java6-jre
Still says 6.22 is latest version even though I went to the Java website and it says 6 version 23 is the latest.
Help!

---

### Post by howefield on 2011-01-22
6.22 is latest version as far as the repositories are concerned. Application version numbers are fixed through the life of each Ubuntu release, except for security fixes/updates. 

6.23 contains no security fixes/updates so is unlikely to be placed in the repositories. You would need to download and install manually if you wanted it.

---

### Post by BestUsername2222 on 2011-01-22
> **howefield said:**
> 6.22 is latest version as far as the repositories are concerned. Application version numbers are fixed through the life of each Ubuntu release, except for security fixes/updates. 

6.23 contains no security fixes/updates so is unlikely to be placed in the repositories. You would need to download and install manually if you wanted it.

All four Java downloads for Linux on the java website don't work when I try to install them.

---

### Post by howefield on 2011-01-22
Remove your current java installation and follow the instructions here.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

