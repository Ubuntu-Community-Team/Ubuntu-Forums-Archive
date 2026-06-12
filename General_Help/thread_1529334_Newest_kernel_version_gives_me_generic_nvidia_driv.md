---
title: "Newest kernel version gives me generic nvidia drivers"
date: 2010-07-12
forum: General Help
---

### Post by Zeemvel on 2010-07-12
If I boot up Ubuntu with the newest configuration, it runs in very low graphics resolution and gives a window saying it runs in very low graphics configuration because "no usable configuration could be found for any of the screens".

This happens when I boot up with the newest configuration, kernel version "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic".

If I take the second-newest version, kernel version "Ubuntu 10.04 LTS, kernel 2.6.32-22-generic", then it works.

How can I fix the nvidia drivers for the newest version?

Thanks.

---

### Post by efflandt on 2010-07-12
Which nVidia drivers are you running, and did you install them using Hardware Drivers, Synaptic package manager, or some other way?  If you installed some other way, maybe they do not update automatically.

I am using 195 drivers and I did see that low graphics mode once, but I think it was when I had a typo in /etc/default/grub (GRUB_SAVE**D**DEFAULT=true should have been GRUB_SAVEDEFAULT=true).

```
uname -srm
Linux 2.6.32-23-generic x86_64

lsmod | grep nvidia
nvidia              10832442  38
```

---

### Post by Zeemvel on 2010-08-02
Hello,

I don't know how I installed the NVidia drivers.

In the meantime a new Ubuntu upgrade added a kernel version 2.6.32-24. But I still have to select 2.6.32-22 in the startup screen, because now both the 2.6.32-23 and the 2.6.32-24 give me the low graphics message and a too low resolution to work with.

If I type the commands you showed, I get:

uname -srm
Linux 2.6.32-22-generic i686

lsmod | grep nvidia
nvidia              10216432  28
agpgart                31724  1 nvidia

Note that in  "uname -srm" it shows the 22, because there's no point to me in booting to the 23 and 24 version, the resolution is too low to do anything useful. I guess if Ubuntu updates the kernel 3 more times, I'll be screwed because version 22 will then disappear at the bottom of the bootup screen and I won't be able to select it anymore...

So, knowing that I don't know myself how the NVidia drivers got installed on my Ubuntu, what exact steps can I perform to be able to choose the newest kernel version (24) in the bootup screen AND have proper NVidia graphics?

Thanks!

---

