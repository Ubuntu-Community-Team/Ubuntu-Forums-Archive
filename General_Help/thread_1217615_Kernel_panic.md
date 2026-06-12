---
title: "Kernel panic"
date: 2009-07-19
forum: General Help
---

### Post by Brunno Silva on 2009-07-19
Hi,

I found some threads about this problem, but none helped me. One day, when I turned on my computer, it stopped the boot process and never got to Ubuntu. I don't know why it happened, but since then the boot process ends with this message:

Boot from (hd0,0) ext4   078c9be5-e9d2-4beb-b886-ecea270e960a
Starting up ...
[    1,324318] Kernel panic - not syncing: VFS: Unable to mount root fs on unknow-block(0,0)

What should I do?

Brunno Silva

---

### Post by alphacrucis2 on 2009-07-19
> **Brunno Silva said:**
> Hi,

I found some threads about this problem, but none helped me. One day, when I turned on my computer, it stopped the boot process and never got to Ubuntu. I don't know why it happened, but since then the boot process ends with this message:

Boot from (hd0,0) ext4   078c9be5-e9d2-4beb-b886-ecea270e960a
Starting up ...
[    1,324318] Kernel panic - not syncing: VFS: Unable to mount root fs on unknow-block(0,0)

What should I do?

Brunno Silva

If you have the install CD. Boot from that and check the condition of the hd0 disk drive. You might be able to use fsck to repair.

---

### Post by Brunno Silva on 2009-07-19
Alphacrucis2,

Thanks for the quick answer. How should I check its condition? What exactly I'll look for? I can access all its file from the CD.

Brunno Silva

---

