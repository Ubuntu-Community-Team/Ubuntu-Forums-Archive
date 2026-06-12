---
title: "libc6 dependency gone?"
date: 2012-03-21
forum: General Help
---

### Post by clacroix12 on 2012-03-21
Hey all,

Working on a practically new install of ubbuntu 11.10 here. I was installing some applications and updates when i started getting the following whenever i tried running apt-get install.

```

The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5)
 libc6-dev : Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is to be installed
```
I tried to install the missing dependencies but it told me that the packages couldn't be found. Any help on this would be fantastic since I really can't use apt-get at all until i figure this out.

Thanks in advance!

---

### Post by nothingspecial on 2012-03-23
*Thread moved to **General Help**.*

---

### Post by kurt18947 on 2012-03-23
I don't know if it'll help but can you install Synaptic perhaps via Ubuntu software center?  I've had some luck with Synaptic fixing problems like yours. In Synaptic:  Edit -> fix broken packages.  Then try running update all packages in Synaptic.

---

