---
title: "Quick Question..."
date: 2006-03-28
forum: General Help
---

### Post by Sublime10 on 2006-03-28
I just installed a new kernel. Now when I boot my computer, on the grub menu it shows 2 instances of Ubuntu, one for each kernel. Can I delete the old kernel from the mbr without harming anything?

-Thanks

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=Sublime10]I just installed a new kernel. Now when I boot my computer, on the grub menu it shows 2 instances of Ubuntu, one for each kernel. Can I delete the old kernel from the mbr without harming anything?

-Thanks[/QUOTE]
I wouldn't recommend it. If one kernel ever fails you can use the old kernel to boot ubuntu and fix the problem. However, if you want, go ahead-it's safe to remove the old entry but once again, I WOULD NOT recommend doing so.

---

### Post by taurus on 2006-03-28
If the new kernel is booting fine for you, you can certainly remove the old kernel from GRUB menu by editing /boot/grub/menu.lst...
```

sudo gedit /boot/grub/menu.lst

```

---

### Post by Sublime10 on 2006-03-28
Ok thanks.

---

### Post by engla on 2006-03-28
Hey, remove the old kernel with synaptic. That should remove the grub entry too and everything in an automated way.

I'd keep one old version though, but if you made sure it boots then there should be no problem.

---

