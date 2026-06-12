---
title: "Problem with blank screen during boot"
date: 2012-01-23
forum: General Help
---

### Post by d3ngar on 2012-01-23
Hi,

It seems the last Kernel Update shot something with my Dell laptop monitor, as the whole screen just simply doesn't work...

During boot, after the BIOS sequence, the screen just turns black. A bit of green smear and lines appear (which I assume is the GRUB menu). This disappears and the boot sequence continues. At the end, the other monitor (dual screen) is kicking in and the log-in is displayed.

After the log-in I can see the other monitor in the display-settings, but when I try to enable it, it's just black.

I think something went very wrong here with the last update.

Any suggestions?

---

### Post by d3ngar on 2012-01-27
This was a very weird error!

As you probably can appreciate: the kernel isn't loaded before GRUB, but somehow I was affected by something relating to 3.0.0-15!

The only way for me to solve this was to boot via Live CD / USB / using my other attached monitor and forcing a different kernel to boot. I didn't have any problems thereafter!

---

