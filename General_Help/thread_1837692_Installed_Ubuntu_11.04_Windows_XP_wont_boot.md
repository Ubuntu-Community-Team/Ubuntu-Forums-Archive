---
title: "Installed Ubuntu 11.04 Windows XP wont boot"
date: 2011-09-02
forum: General Help
---

### Post by shadowsnake on 2011-09-02
Hello folks

Im enjoying ubuntu, but have had trouble booting Windows XP from the boot menu

Can anyone suggest any user friendly, preferably not too technical solutions?

Much appreciated

---

### Post by raja.genupula on 2011-09-02
we need some information .
1 do you have any idea at which partition you have installed your windows ?
2 what is the out put of ```
sudo os-prober
``` ?
3 . are you seeing any entry of windows in your grub.cfg file at /boot/grub location 
```
sudo gedit /boot/grub/grub.cfg
```

---

