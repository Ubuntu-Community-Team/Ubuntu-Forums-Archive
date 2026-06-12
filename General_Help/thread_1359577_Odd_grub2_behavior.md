---
title: "Odd grub2 behavior"
date: 2009-12-19
forum: General Help
---

### Post by bowens44 on 2009-12-19
I think I did something that messed up grub2 in karmic. It's nothing major. When I boot into the latest kernel I see a black screen for 23 or 30 seconds before I see the screen with ubuntu and the animated bar just before login. I don't see the black screen with the white ubuntu symbol.

I tried t install splashy and this is where the trouble may have started. I have since uninstalled splashy. I I did an update-grub.

This is somehow related to the kernel. If I boot into the previous kernel everything functions normally.

any idea how I can get everything back to the defaults when booting into the latest kernel?  I suspect that splashy did something that is causing this behaviour.

thanks

---

### Post by drs305 on 2009-12-19
You can open /boot/grub/grub.cfg for inspection. Compare both menu entries for the kernels in question. If they are exactly the same except for the kernel number then it probably isn't something that Grub 2 is going to fix. You can look especially at the "linux" lines to see if one has options the other doesn't.

```

gksu gedit /boot/grub/grub.cfg /etc/default/grub

```

If you find different options, open /etc/default/grub and look at the two GRUB_CMDLINE... lines.

---

### Post by Leppie on 2009-12-19
could you post your /boot/grub/grub.cfg?

---

