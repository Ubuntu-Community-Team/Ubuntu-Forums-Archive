---
title: "Problems with Synaptic Package Manager"
date: 2009-12-14
forum: General Help
---

### Post by fcheh on 2009-12-14
1. The following shows up when I open Package Manger how do I correct problem?

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


2. Also no sound from internal speakers but headphone work.
3. Cant play real videos from AEBN website?

---

### Post by PseudoLemon on 2009-12-14
1. Do what it says for the package manager
2. Driver problem? There've been numerous posts about this
3. There are... alternatives...

---

### Post by Yvan300 on 2009-12-14
1. Open a terminal and copy and paste the following and hit enter

```
sudo dpkg --configure -a
```

2. According to which version of ubuntu you are using, you can right click the volume icon and choose different sound drivers. Keep choosing until you find one that works with your speaker. Also the system volume is sometimes divided into pcm and master. At times either one may be muted and will need to be turned up.

3. Did you install ubuntu-restricted extras and if so which browser are you using. Some sites require a window plugin to be installed which make them incompatible with linux.

---

