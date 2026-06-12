---
title: "Lubuntu 12.04 upgrade, serious problem, Intel Mac Mini"
date: 2012-04-29
forum: General Help
---

### Post by cogitordi on 2012-04-29
I had Lubuntu 11.10 running well on an Intel Mac Mini. The upgrade to 12.04 has resulted in unstable boot behaviour, including long boot times that are like system hangs, and video corruption. 

Are these problems the reason why there is an Intel Mac variant of Lubuntu for AMD64?

---

### Post by cogitordi on 2012-04-29
This explains the problem:

[http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image](http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image)

However, I had no such problem with Ubuntu 11.10. 

If you are an Intel Mac user thinking of upgrading, expect trouble.

---

### Post by cogitordi on 2012-05-04
Correction: the problem appears to be the LightDM setting a video mode that my monitor does not support. 

My system works if I do not use the proprietary NVidia driver. However, the "Nouveau" driver does not seem to support 1280x1024 without some fiddling.

goto fiddling; //warning, may never return

---

