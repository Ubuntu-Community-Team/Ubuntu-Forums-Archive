---
title: "Compiz issues"
date: 2011-03-20
forum: General Help
---

### Post by xondak on 2011-03-20
Last week I did a system update which caused Compiz to stop functioning completely. I really need Compiz to work so I decided to reinstall Ubuntu anyway.

I successfully reinstalled Ubuntu and everything worked fine. After I did a system update, Compiz stopped functioning and NVIDIA X Server Settings appeared in the system menu. I have integrated Intel graphics so I find it weird that NVIDIA's X server drivers would be installed...

Anyone have any idea what's wrong??

---

### Post by mikewhatever on 2011-03-20
If you don't have an Nvidia card, but may have an Nvidia driver installed, that may be a problem. Have you tried removing it?
Check what Nvidia related packages are installed with the following command:
```
dpkg -l | grep nvidia
```

Note, there is no need to remove everything that comes up, for example, *modaliases packages are ok.

---

### Post by xondak on 2011-03-20
Thank you so much! I thought I had removed all the NVIDIA drivers, but I missed one. This has fixed my issue. :D

---

