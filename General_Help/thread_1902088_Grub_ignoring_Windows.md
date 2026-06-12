---
title: "Grub ignoring Windows"
date: 2011-12-29
forum: General Help
---

### Post by Hovercat on 2011-12-29
I had some problems with Windows and Ubuntu earlier today, but I've gotten that figured out, except that grub detects Windows 7 when running "update-grub", but it doesn't show up in the boot loader. I tried adding Windows 7 manually in /etc/grub.d/40_custom, but that doesn't show up in the boot loader, however, it is in grub.cfg. The only way to boot into windows is for me to open up command line in grub and type

```
set root=(hd0,1)
chainloader +1
boot
```

---

### Post by Mark Phelps on 2011-12-30
Don't know what "not showing up in the boot loader" means ...

You said the entry is in grub.cfg, so does a menu appear when you boot?

Is there a Windows Loader entry in that menu?

What happens when you select that menu entry?

These are all very different kinds of problems.

---

### Post by Rubi1200 on 2011-12-30
Best thing would be to post the results of the boot info script so we can see what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

