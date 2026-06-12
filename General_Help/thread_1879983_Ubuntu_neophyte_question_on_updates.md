---
title: "Ubuntu neophyte question on updates"
date: 2011-11-12
forum: General Help
---

### Post by kydd on 2011-11-12
hello all, I'm fairly new to Ubuntu, although i used Xubuntu 10.4 before on a different computer.  

one thing i noticed was the amount of updates sent everyday. when i ran Ubuntu i was using a very old computer with only 40 gigabytes of hardrive- after a month a quarter of it was used up on updates alone. however, i ticked the install all updates option.

so my question is, do i need to install all these updates? most of the time the updates smooth out performance (or at least windows has convinced me that they have) and are well worth it.

also, is there a way to differentiate from updates i do need and updates that i don't? e.g. would a fairly important system update be titled something that would set it apart from a less important libre office update?

thanks a bunch, and i'm sorry if this question has been asked before, or if i'm in the wrong section.

---

### Post by ajgreeny on 2011-11-12
You can choose to install only the security updates if you wish, to save on disk space, but it is probably best, assuming you don't have a problem with download limits, to install every update offered, but make sure that the cache of packages is cleared every so often with the command ```
sudo apt-get clean
```
You can even set the system to delete all the packages immediately after installation, if you prefer in **Software sources**, to save you needing to remember that.

---

