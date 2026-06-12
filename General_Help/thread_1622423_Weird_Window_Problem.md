---
title: "Weird Window Problem"
date: 2010-11-15
forum: General Help
---

### Post by NoSuchDevice on 2010-11-15
Hey guys I got this weird problem. Sometimes when I login and open up a window or something I don't see the Close/Minimize or Maximize buttons and I can't move the window What's wrong? 

Thanks

---

### Post by Lancro on 2010-11-15
Press alt + space, does the window menu opens?

---

### Post by solitaire on 2010-11-15
This happen to me every other Reboot/Startup on my laptop.

I have to log out then log back in to get the Window title bar back...

slightly annoying, I'll see if "alt+space" does anything next time it happens...

---

### Post by sikander3786 on 2010-11-15
Unfortunately, it is a known problem with compiz but luckily there are many workarounds.

You can install fusion-icon and add it to your startup applications. It will sit in your system tray and you can right click and reload window manager whenever it happens to correct the problem.

Another one is that you can press Alt + F2 and type

```
compiz --replace
```

And hopefully, that will also correct the problem.

If you want to switch your window manager to metacity, you can either use fusion-icon or type,

```
metacity --replace
```

---

