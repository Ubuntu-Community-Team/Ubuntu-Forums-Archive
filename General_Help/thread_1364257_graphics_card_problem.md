---
title: "graphics card problem"
date: 2009-12-25
forum: General Help
---

### Post by nitishsuvarna on 2009-12-25
HI i m newbee in linux world & 2de i installed linux ubuntu 9.10.My prooblem is that it does not recognise my gpu.it is nvidia 8600gts 512mb/128bit.In hardware drivers,it shows nothing & in software package,all softwares are installed.PLZ HELP ME

---

### Post by bruno9779 on 2009-12-25
have you updated your system?

```
sudo apt-get update && sudo apt-get upgrade
```

the right drivers should be the 185nvidia. If it does not appear in hardware drivers you could try installing it through synaptic

If all this fails you can install the driver as supplied by Nvidia, but it is a PITA for a newbie, so post back and I'll tell you then

---

### Post by nitishsuvarna on 2009-12-25
i have ntered ur code in terminal system is updating i will reply soon

---

### Post by nitishsuvarna on 2009-12-25
thank u bruno for ur help.Now my system is working properly with gpu.TNX A LOT.

---

