---
title: "splash"
date: 2011-11-07
forum: General Help
---

### Post by Gwaro on 2011-11-07
My system takes 13 seconds to show the splash screen when booting. Before that is just a black blank screen. Is this how it is supposed to be?

---

### Post by Gremlinzzz on 2011-11-07
I would say yeah thats it:popcorn:

---

### Post by mcduck on 2011-11-07
No, not really, but that happens quite commonly with certain graphics cards and drivers. The graphics driver takes too long to initiate, so Linux just continues booting and then tries enabling the graphics again at later stage of the boot process when the driver and card are both ready.

Note that this behavior doesn't actually slow down the boot, more of the opposite. But if you'd prefer the boot process to wait until the graphics card is ready so you'll see the boot splash from the very beginning, it's pretty simply to fix. Just open a terminal and run the following commands:

```
echo "FRAMEBUFFER=y" | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

---

### Post by Gwaro on 2011-11-07
Thank you all

---

