---
title: "How to dim laptop screen brightness"
date: 2011-11-13
forum: General Help
---

### Post by sir_jct on 2011-11-13
Hello Friends,

I am using an acer 5750 64bit+ 4gb ram+ i2310 and have just installed ubuntu 11.10 via wubi.

My laptop screen is too bright for my eyes and am totally helpless and dimming it.

Fn + dim button on laptop does not make much of a difference.

I have scoured google for command line to no avail.
Could somebody please help me.
Many thanks
Jay

---

### Post by iridemybike on 2011-11-13
If you go to "System Settings"(either through Dash or it may be in your taskbar to the left) and then go to "screen" and in the little window that pops up there will be a slider to set the brightness wherever you want.

---

### Post by sir_jct on 2011-11-13
> **iridemybike said:**
> If you go to "System Settings"(either through Dash or it may be in your taskbar to the left) and then go to "screen" and in the little window that pops up there will be a slider to set the brightness wherever you want.

Hello Iridemybike,

Moving the screen brightness slider does NOT have an effect on brightness

---

### Post by bcbc on 2011-11-14
It seems you have an intel graphics card so check this out: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

That link has background the bug as well as patches for 11.04 and 10.10. Since you are using 11.10 it should work,:
> However, some Oneiric users may still need to add the boot parameter "acpi_backlight=vendor"

---

