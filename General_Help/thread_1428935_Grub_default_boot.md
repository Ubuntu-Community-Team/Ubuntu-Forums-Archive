---
title: "Grub default boot"
date: 2010-03-13
forum: General Help
---

### Post by need more pyton on 2010-03-13
hello fellow ubuntu users!  I am trying to change to boot order in grub, but I keep running into the same problem.  every help article I find instructs me to go to /boot/grub/menu
however that file doesnt exist on my computer. in my /boot/grub directory file names go from memrw.mod to minicmd.com with nothing in between.  I am using an up to date release of Karmic Koala. if someone could tell me what file i should be using i think i could probably take care of the rest but full directions would be appreciated.
thanks

---

### Post by synapsys on 2010-03-13
Those instructions are for grub legacy. Karmic Koala uses grub2. You can install the startup manager and change the default os there.

```
sudo apt-get install startup-manager
```

---

### Post by Barriehie on 2010-03-13
You might find this thread helpful; I'm using legacy grub so can't give detailed instructions.
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub)

---

