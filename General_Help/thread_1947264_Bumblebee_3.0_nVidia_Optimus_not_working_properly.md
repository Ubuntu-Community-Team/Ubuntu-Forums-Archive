---
title: "Bumblebee 3.0 nVidia Optimus not working properly"
date: 2012-03-26
forum: General Help
---

### Post by baby_panda on 2012-03-26
Hi, I have an nVidia Optimus-enabled Dell laptop with Ubuntu 11.10 Oneiric. I installed Bumblebee 3.0 Tumbleweed. When I use optirun the first time after I log in, it works fine. But when I use optirun once more, it  displays this:

[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please

[ERROR]Aborting because fallback start is disabled.

After getting this message, when I type:
 
sudo restart bumblebeed

and use optirun again, it works. Please, can anybody tell me what's wrong here?

---

### Post by Lekensteyn on 2012-04-30
It sounds like you've installed a mismatching nvidia driver. Can you add your /var/log/Xorg.8.log and the tail of your kernel log (/var/log/kern.log)?

---

### Post by baby_panda on 2012-05-02
> **Lekensteyn said:**
> It sounds like you've installed a mismatching nvidia driver. Can you add your /var/log/Xorg.8.log and the tail of your kernel log (/var/log/kern.log)?

Hi, I've attached the 2 log files. The nVidia driver (nvidia-current) was installed from the Ubuntu  11.10 repositories.

P.S.: Thank you very much for replying. I had almost given up hope in the Ubuntu forums. :)

---

### Post by Lekensteyn on 2012-05-03
Try upgrading to Precise for updated drivers.

Problematic messages and context:
```
vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=none,decodes=none:owns=none
NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
NVRM: RmInitAdapter failed! (0x26:0xffffffff:1077)
NVRM: rm_init_adapter(0) failed
vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
NVRM: RmInitAdapter failed! (0x26:0xffffffff:1077)
NVRM: rm_init_adapter(0) failed
```

---

