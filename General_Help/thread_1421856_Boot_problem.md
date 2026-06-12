---
title: "Boot problem"
date: 2010-03-04
forum: General Help
---

### Post by SiegHard on 2010-03-04
Hello few days ago i got problem which slows my boot to linux.
Before loading Ubuntu logo in console i see fast flash with words:
"Warning: unable to find a suitable fs in /proc/mount, is it mounted?
Use --subdomainfs to override." What should i do? To fix that warning?

---

### Post by bluelamp999 on 2010-03-04
Have you installed a different kernel other than the standard one?

I got this message when I installed a more recent kernel (non Ubuntu) than the current Karmic one. I was trying to use the xorg-edgers ATI drivers which require a .32 (I think) kernel.

Apparently it's something to do with AppArmor...

Edit: I got rid of the message by reinstalling the current kernel from Synaptic.

---

### Post by SiegHard on 2010-03-04
> **bluelamp999 said:**
> Have you installed a different kernel other than the standard one?

I got this message when I installed a more recent kernel (non Ubuntu) than the current Karmic one. I was trying to use the xorg-edgers ATI drivers which require a .32 (I think) kernel.

Apparently it's something to do with AppArmor...

Edit: I got rid of the message by reinstalling the current kernel from Synaptic.
Yes i using different kernel ;/ So it's impossible somehow to slove?

---

### Post by bluelamp999 on 2010-03-05
I just installed the current Ubuntu kernel from Synaptic...

For Karmic at the moment this is ```
linux-image-2.6.31-20-generic
```

This worked for me, your mileage may vary...

---

