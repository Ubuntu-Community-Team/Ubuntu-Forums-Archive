---
title: "automatic old kernel remover?"
date: 2009-09-15
forum: General Help
---

### Post by hockeyhead019 on 2009-09-15
hey guys,

well clearly as the title states i was looking for something which automatically removes the kernels as they upgrade... for example I have 8 or so of em on my boot up screen and its just annoying... i know that i could get rid of them in synaptic but i was curious as to if there was a program which would remove them except for ones you pick or the latest two version etc...

-Jim

---

### Post by KiLaHuRtZ on 2009-09-15
Look at, and perhaps modify, '/boot/grub/menu.lst' at this specific point.

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
[COLOR="Green"]#[/COLOR] howmany=[COLOR="Red"]all[/COLOR]
```

Leave the leading '[COLOR="Green"]#[/COLOR]' in place as this is not a commented out line.

After which do the following to update GRUB.

```
sudo update-grub
```

I would suggest keeping all your old kernels installed just as a failsafe.  They will no longer show in the GRUB loader, however they are still installed in case you ever need them.  And they don't take up too much space in relation to today's hard drives.

---

### Post by hockeyhead019 on 2009-09-15
ok so if i do leave all of them installed as a fail safe and something goes wrong with whatever one i can select from the grub menu, my question now is how would i access the older versions?

nevermind i figured out that i can just leave 2 or 3 in there so that if something goes wrong i can just boot one of the other two

---

### Post by KiLaHuRtZ on 2009-09-16
Even if a kernel does not exist in the menu, you can still boot it by manually typing it at the GRUB prompt.

---

