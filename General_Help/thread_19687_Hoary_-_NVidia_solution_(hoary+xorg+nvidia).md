---
title: "Hoary - NVidia solution (hoary+xorg+nvidia)"
date: 2005-03-13
forum: General Help
---

### Post by pedroac on 2005-03-13
I had a problem with my **NVIDIA GeForce4 MX 440** when upgraded Ubuntu to Hoary version, and solved it (after reading the Spanish "How To" - but I'm not spanish, I'm portuguese ... )!

 After installing nvidia packages, type:
```
sudo dpkg-reconfigure xserver-xorg
``` 

 Choose the **"nvidia"** driver (reject "nv" option), and accept the defaults ... except when it's asked to *select the X.Org server modules that should be loaded by default.* : **disable GlCore and dri** module.   [-o< 

 Restart X (Ctrl+Alt+F4), and everything went right!  :grin:

---

