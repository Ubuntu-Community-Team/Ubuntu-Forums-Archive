---
title: "Update error"
date: 2011-08-13
forum: General Help
---

### Post by JCM_Pico on 2011-08-13
hi there, 

today when I tried to update my system, this message appeared. 

```
E: /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb:  trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package  xul-ext-ubufox 0 
```

I can't understand the effect of this on the system or how can I fix it.
can anybody give some help?

---

### Post by wojox on 2011-08-13
Open synaptic, marked xul-ext-ubufox for removal, ubufox for upgrade and apply changes.

---

### Post by hakermania on 2011-08-13
EDIT: Apparently [wojox]("http://ubuntuforums.org/member.php?u=802919") solution is much better
_***As I understand it***_, there are 2 DEB packages which install the same file.
Your update downloaded the ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb package and tried to install it. It detected that the package tried to overwrite a file installed by the xul-ext-ubufox package.

If being on your position, I would try to find the xul-ext-ubufox DEB package in /var/cache/apt/archives/, copy it to my Desktop, extracting it, finding the file ubufox.js inside the extracted folder, calculating its md5sum and compare it with the md5sum of the file /etc/xul-ext/ubufox.js, if they are the same, then there's no problem.
If not, I don't know, it may be.

---

### Post by JCM_Pico on 2011-08-13
will follow [wojox]("http://ubuntuforums.org/member.php?u=802919") solution... thanks

---

### Post by wojox on 2011-08-13
> **JCM_Pico said:**
> will follow [wojox]("http://ubuntuforums.org/member.php?u=802919") solution... thanks

If it works (fingers crossed), post back and please mark as solved. :p

---

