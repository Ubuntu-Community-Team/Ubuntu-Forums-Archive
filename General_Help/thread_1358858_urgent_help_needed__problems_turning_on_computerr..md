---
title: "urgent help needed : problems turning on computerr....grub help ? PLEASE"
date: 2009-12-18
forum: General Help
---

### Post by insaniac09 on 2009-12-18
i have a hp computer dual booted with windows xp and ubuntu 9.04....before evertime i would start my computer it would boot with grub and then give me the option to pick either windows xp or ubuntu...but now I'm not sure what happened but when i turn on my computer the screen just keeps saying GRUB GRUB GRUB GRUB GRUB continuously and i cant use my computer ...its driving me INSANE and i have a few files on my xp that i need ...Does anybody know how to fix this ! please help :confused:

---

### Post by bodhi.zazen on 2009-12-18
hard to tell.

I would boot a live CD and examine your system.

Unmount all the partitions and check them with fsck

```
fsck /dev/sda1
```

and on ...

---

